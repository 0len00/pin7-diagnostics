# Pin7 Diagnostics

Tasuta Androidi diagnostikaäpp VAG-grupi autodele. APK on allalaaditav **Releases** lehelt — konto, registreerimine ega litsents ei ole vajalik.

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

## Probleemid

Kui ühendus ei tööta, saada logi (äpis „Logi“ vaade → salvesta) koos auto mudeli, aasta ja mootorikoodiga Issue'sse.
