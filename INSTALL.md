# Installation Guide

## 1. Vaatimukset

### Laitteisto

- Tektelic Kiwi Soil Sensor
- LoRaWAN-yhteys (Netmore)
- Node-RED-palvelin

### Ohjelmistot

- Node.js
- Node-RED
- Google Sheets
- Google Apps Script
- Google Looker Studio

## 2. Node-RED-palvelimen valmistelu

Asenna Node-RED haluamallesi alustalle ja varmista että palvelin on saavutettavissa internetistä HTTPS-yhteydellä.

Suositeltavia ratkaisuja:

- Kiinteä IP-osoite
- DuckDNS
- No-IP

## 3. Node-RED-projektin tuonti

Tuo tiedosto:

```text
tektelic_to_google_sheets.json
```

Node-REDiin valinnalla:

```text
Menu -> Import
```

## 4. Luo Google Sheets

Luo uusi Google Sheets -taulukko historiatiedoille.

## 5. Luo Apps Script

Google Sheets:

```text
Extensions -> Apps Script
```

Korvaa oletuskoodi tiedoston:

```text
appsScript.js
```

sisällöllä.

## 6. Julkaise Web App

```text
Deploy -> New Deployment
```

Valitse Web App ja käyttöoikeudeksi Anyone.

Kopioi muodostunut URL.

## 7. Päivitä Node-RED

Liitä Apps Script URL HTTP Request -solmuun ja deployaa flow.

## 8. Määritä Netmore

Luo Netmore-portaaliin HTTPS-webhook:

```text
https://oma-palvelin.fi/tektelic
```

Method: POST

Content-Type: application/json

## 9. Testaus

Tarkista että mittausdata siirtyy:

1. Netmore
2. Node-RED
3. Google Apps Script
4. Google Sheets
5. Looker Studio

## 10. Dashboard

Luo Looker Studioon raportti käyttäen Google Sheets -taulukkoa tietolähteenä.

Suositellut mittarit:

- Maaperän lämpötila
- Maaperän kosteus (kPa)
- Paristotaso
- MCU-lämpötila
- Viimeisin mittaus
