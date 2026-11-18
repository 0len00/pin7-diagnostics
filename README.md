# Pin7 Diagnostics

Free diagnostic app for VAG-group cars on Android. The APK is available on the **Releases** page — no account, registration or licence required.

## ⚠️ Work in progress

The app **may contain bugs and not everything may work properly yet**. Some features are untested or only work with certain modules/cars:

- KWP2000 / KW2027 (ABS modules) support is newer and less tested than KWP1281
- a failed read can return an empty result or drop the connection — just try again
- measuring blocks, adaptation and basic settings depend on module support and may only partly work

If something does not work, that is expected feedback rather than a guaranteed feature. Please send a log (see "Issues" below).

## Features

- **KWP1281** (older VAG modules): read and clear fault codes, measuring blocks, adaptation, basic settings
- **KWP2000 / KW2027** (e.g. ABS modules): read and clear fault codes, identification, sessions — fault-code reading now works on an MK60 ABS controller (clearing still needs confirmation on a real car)
- **VDO cluster** (address 17) and engine module (address 01)
- On-device log view and log export

## Languages

The app interface is available in **English, Estonian and Russian**.

## Requirements

- Android 8.0 (API 26) or newer, with USB OTG support
- USB OBD2 cable with an FTDI (FT232) or CH340 chip
- Communication runs over the K-line (KWP1281) or KWP2000 — CAN-only cars are not supported

## Installation

1. Open [Releases](../../releases) and download the latest `pin7diagnostics-*.apk`
2. Allow installing from unknown sources on the phone (e.g. Settings → Apps → Special app access)
3. Open the APK and install
4. Connect the cable, grant USB permission to the app and tap "Connect"

Updates install over the previous version (same signing key) and keep your data.

## Versions

| Version | versionCode | File | MD5 | Notes |
|---|---|---|---|---|
| 1.36 | 37 | `pin7diagnostics-1.36.apk` | `e24fec0ed45e9a5f9221126ce2724993` | stable free build |
| 1.37 | 38 | `pin7diagnostics-1.37-test.apk` | `7368e72c16f349bf4312dd000aeb0a43` | test build, pre-release |
| 1.41 | 42 | `pin7diagnostics-1.41-test.apk` | `219b4fc9d49ee03924b7d0dc5c9d2967` | test build, pre-release — KWP2000 fault-code reading works on MK60 ABS |
| 1.42 | 43 | `pin7diagnostics-1.42-test.apk` | `cba91886a219fb954c9dddfa375b0fc8` | test build, pre-release — fault-code meanings reviewed, 5 corrected and 30 added (ABS/ESP, engine, airbag) |
| 1.43 | 44 | `pin7diagnostics-1.43.apk` | `b2ecdb64e68cae3391b96ab326a48299` | stable free build — KWP2000 ABS/ESP (address discovery, session, fault codes read/clear), 5 fault-code meanings corrected and 30 added, connection holds on clear (confirmed in the car) |

## Notes

- The app is free and ad-free; there is nothing to buy and no sign-in.
- Diagnostics are at your own risk. Do not write changes into modules unless you know what they do.
- This repository only hosts the distributed APK. The source code is not published here.

## KWP2000 addressing: wakeup address vs header target

On a K-line module the 5-baud wakeup address and the address the same module expects in the
ISO 14230 frame header are two different things. For most VAG controllers they are the same
byte (ABS = `0x03`), which is why a fixed address usually works -- but not for all of them.
The MK60 ABS/ESP controller this app was tested against wakes at `0x03` and then ignores every
request addressed to `0x03`: its frames must carry target `0x28`. (EDC16 engine ECUs behave the
same way, with `0x01` -> `0x10`.) A request to the wrong header address is dropped silently --
the link stays up and the wakeup handshake succeeds, but every following request simply gets no
reply, which looks like "the connection works but the module does not answer".

Because that mapping belongs to the controller family and cannot be derived from the VAG module
number, the app does not hardcode it. Before opening a diagnostic session it probes the
candidates (`0x03`, `0x28`, `0x10`, `0x01`, `0x04`, `0x26`, `0x29`, `0x33`) with a harmless
`1A 9B` (readEcuIdentification) request, which needs no prior session, and keeps the first
address that answers. Supporting another KWP2000 controller normally means adding one candidate
address, not a new code path.

## Engine and credits

The diagnostic engine is based on **gmenounos**' project [kw1281test](https://github.com/gmenounos/kw1281test) — he is the author and owner of that KWP1281/KWP2000 engine. Many thanks for the work this app builds on.

## Issues

If the connection does not work, send a log (in the app: "Log" view → save) together with the car model, year and engine code as a GitHub Issue.
