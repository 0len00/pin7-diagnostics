# Pin7 Diagnostics

Tasuta Androidi diagnostikaäpp VAG-grupi autodele. APK on allalaaditav **Releases** lehelt — konto, registreerimine ega litsents ei ole vajalik.

## Tähelepanu: rakendus on arendusjärgus

Rakenduses **võib olla vigu ja kõik ei pruugi veel korralikult töötada**. Osa funktsioone on testimata või töötab ainult teatud moodulite/autodega:

- KWP2000 / KW2027 (ABS-moodulid) tugi on uuem ja vähem testitud kui KWP1281
- vigane lugemine võib anda tühja tulemuse või katkestada ühenduse — proovi siis uuesti
- mõõteplokid, adaptsioon ja põhiline seadistus sõltuvad mooduli toest ja võivad osaliselt mitte töötada

Kui midagi ei tööta, on see oodatud tagasiside, mitte garanteeritud funktsioon. Palun saada logi (vt „Probleemid“ allpool).

## Funktsioonid

- **KWP1281** (vanemad VAG-moodulid): veakoodide lugemine ja kustutamine, mõõteplokid, adaptsioon, põhiline seadistus
- **KWP2000 / KW2027** (nt ABS-moodulid): veakoodide lugemine ja kustutamine, ident, sessioonid
- **VDO kell** (aadress 17) ja mootoriplokk (aadress 01)
- Logi kuvamine ja salvestamine seadmes

## Nõuded

- Android 8.0 (API 26) või uuem, USB OTG tugi
- USB-ODB2 kaabel FTDI (FT232) või CH340 kiibiga
- Ühendus toimub K-liini (KWP1281) või KWP2000 kaudu — CAN-only autod ei ole toetatud

## Paigaldamine

1. Ava [Releases](../../releases) ja laadi alla uusim `pin7diagnostics-*.apk`
2. Luba telefonis „Paigalda tundmatutest allikatest“ (nt Seaded → Rakendused → Spetsiaalne juurdepääs)
3. Ava APK ja paigalda
4. Ühenda kaabel, anna äpile USB-luba ja vajuta „Ühenda”

Uuendused paigalduvad eelmise versiooni peale (sama allkirjavõti), andmeid ei kaotata.

## Versioonid

| Versioon | versionCode | Fail | MD5 |
|---|---|---|---|
| 1.36 | 37 | `pin7diagnostics-1.36.apk` | `e24fec0ed45e9a5f9221126ce2724993` |

## Märkused

- Äpp on tasuta ja ilma reklaamideta; ostmist ega sisselogimist pole.
- Diagnostika tegemine on omal vastutusel. Ära kirjuta moodulitesse muudatusi, kui ei tea, mida need teevad.
- Siin repos on ainult levitatav APK. Lähtekoodi siin ei avaldata.

## Engine ja tänud

Diagnostikaengine põhineb **gmenounos**'e projektil [kw1281test](https://github.com/gmenounos/kw1281test) — tema on selle KWP1281/KWP2000 engine autor ja omanik. Suur tänu talle töö eest, millele see rakendus toetub.

## Probleemid

Kui ühendus ei tööta, saada logi (äpis „Logi“ vaade → salvesta) koos auto mudeli, aasta ja mootorikoodiga Issue'sse.
