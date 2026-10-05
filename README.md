# Study Studio

## Deze map uploaden naar GitHub

1. Maak een nieuwe repository op GitHub.
2. Kies **Add file → Upload files**.
3. Open deze map op je computer. Selecteer de inhoud van de map en sleep die naar GitHub.
4. Kies **Commit changes**.

De inhoud hoort direct in de hoofdmap van de repository: index.html, package.json, src en de andere bestanden. Upload geen node_modules, API-sleutels of .env-bestand. Die zitten niet in deze uploadmap.

## Wat zit erin?

- De kant-en-klare index.html met bijbehorende assets.
- De volledige broncode van de app met het uploadstartscherm.
- PDF- en Word-documentlezers, oefentoetsen, stampen en de tutorinterface.
- Serverfuncties en instellingen van de eerder voorbereide Netlify-versie.
- Vastgelegde dependencies en tests.

## Code opslaan versus de app online zetten

Uploaden naar GitHub slaat de code op. Het schakelt geen server of AI in. GitHub Pages kan alleen het statische deel tonen; de opslag van lesstof en de AI-tutor hebben een backend nodig. De serverfuncties in deze map zijn momenteel voor Netlify. Een andere hostingprovider vereist een passende backendaanpassing; alleen GitHub-uploaden maakt die functies niet actief.

## Lokaal bouwen

Node.js 22.13 of hoger is nodig.

```sh
npm ci
npm run build
npm test
```

De technische toelichting op de huidige serverfuncties staat in LEES-MIJ.md. Er zitten geen geheime API-sleutels of geüploade gebruikersdocumenten in dit pakket.
