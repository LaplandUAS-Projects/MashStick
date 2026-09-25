# Tektelic Kiwi Soil Monitoring System

Tektelic Kiwi Soil Monitoring System on Node-RED-pohjainen ratkaisu maaperäolosuhteiden jatkuvaan seurantaan. Järjestelmä vastaanottaa Tektelic Kiwi -maaperäanturin mittausdataa LoRaWAN-verkon kautta, käsittelee tiedot Node-RED:ssä, tallentaa ne Google Sheetsiin ja mahdollistaa visualisoinnin Google Looker Studiossa.

Ratkaisu soveltuu erityisesti:

- Maatalouteen
- Tutkimuskäyttöön
- Kasvihuoneisiin
- Ympäristöseurantaan
- IoT-pohjaisiin mittausjärjestelmiin

---

## Järjestelmän toimintaperiaate

Tektelic Kiwi -anturi mittaa maaperän olosuhteita ja lähettää mittaustiedot LoRaWAN-verkon kautta Netmore-palveluun.

Netmore välittää anturin lähettämät tiedot HTTPS-webhookina Node-RED-palvelimelle, jossa viestit dekoodataan ja muunnetaan helposti käsiteltävään muotoon.

Tämän jälkeen Node-RED lähettää tiedot Google Apps Script -rajapinnan kautta Google Sheetsiin. Google Looker Studio käyttää Sheets-taulukkoa tietolähteenä ja muodostaa siitä reaaliaikaiset raportit ja dashboardit.

## Arkkitehtuuri

```text
Tektelic Kiwi
      │
      ▼
Netmore LoRaWAN
      │
 HTTPS Webhook
      ▼
Node-RED
      │
Payload Decoder
      │
      ▼
Google Apps Script
      │
      ▼
Google Sheets
      │
      ▼
Looker Studio Dashboard
```

## Kerättävät tiedot

- Mittausaika
- Maaperän lämpötila
- Maaperän kosteuden jännitys (Watermark / kPa)
- Anturin paristotaso
- MCU-lämpötila

## Projektin sisältö

```text
.
├── tektelic_to_google_sheets.json
├── appsScript.js
├── README.md
└── INSTALL.md
```

## Ominaisuudet

- HTTPS webhook -vastaanotto
- Netmore LoRaWAN -integraatio
- Tektelic Kiwi payload decoder
- Google Sheets -tallennus
- Reaaliaikainen dashboardointi Looker Studiossa

## Käyttöönotto

Katso tarkemmat ohjeet tiedostosta INSTALL.md.

## Lisenssi

MIT License

## Tekijä

Petri Martikainen
