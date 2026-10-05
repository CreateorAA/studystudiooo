# Study Studio voor Netlify

## Online zetten

1. Pak `Study-Studio-Netlify.zip` uit.
2. Log in op je Netlify-account en open https://app.netlify.com/drop .
3. Sleep de uitgepakte projectmap naar Netlify. Kies de map waarin `netlify.toml`, `package.json` en `index.html` staan. Je kunt op Netlify Drop ook de ZIP kiezen.
4. Laat Netlify het project bouwen. De instellingen staan al in `netlify.toml`: build `npm run build`, publicatiemap `dist`, functies `netlify/functions`.
5. Open je nieuwe Netlify-link en voeg je eerste lesstof toe.

Belangrijk: upload het volledige project terwijl je bent ingelogd. Alleen `dist` uploaden plaatst de vormgeving online, maar installeert de opslagserver en AI-tutor niet. Bij een nieuwe upload op een bestaande site: gebruik de volledige projectmap en controleer dat Netlify een build uitvoert. Als het account de bronmap niet automatisch bouwt, gebruik een Git-import of `netlify deploy --build` vanuit deze map.

## Uploaden van lesstof

- PDF, Word (.docx), TXT en Markdown, maximaal 10 MB per document.
- Een PDF wordt in de browser gelezen, inclusief de meegeleverde PDF-worker. Er is geen externe PDF-server nodig.
- Controleer de gelezen tekst voordat je opslaat. Gescande documenten zonder tekstlaag vereisen geplakte tekst.
- Maximaal 60.000 tekens per les en maximaal 150 PDF-pagina's. Verdeel lange boeken in hoofdstukken.
- Alleen de gelezen lesinhoud en de bestandsnaam worden verstuurd, niet het volledige document. Daardoor blijven verzoeken onder de Netlify-limiet voor serverfuncties.
- Netlify Blobs bewaart de lesinhoud, vragen en voortgang. Een beveiligde browsercookie bepaalt jouw studieruimte. Gebruik dezelfde browser om je lessen terug te vinden. Dit is geen accountlogin en synchroniseert niet automatisch met andere browsers/apparaten. Verwijder je de cookie, dan verlies je toegang tot deze studieruimte.
- De oorspronkelijke documenten en bestaande lessen op de ChatGPT-site worden niet meegenomen. Voeg ze op Netlify opnieuw toe.

## AI-tutor en oefentoetsen

De app gebruikt de server-side Netlify AI Gateway via `OPENAI_API_KEY` en `OPENAI_BASE_URL`. Op de huidige credit-based Netlify-plannen (inclusief Free) levert Netlify deze automatisch na een productiepublicatie, tenzij AI Features zijn uitgezet of je eigen providerinstellingen hebt ingevuld. Voeg voor deze automatische route GEEN lege of voorbeeldwaarden toe aan je Netlify environment variables.

AI-gebruik wordt verrekend met de credits van je Netlify-team. De app begrenst AI-verzoeken tot 40 per dag per netwerkadres. Je bestaande lesstof en toetsen blijven daarna beschikbaar. Bij een uitgezette of ontbrekende AI Gateway toont de app een duidelijke melding en blijft uploaden mogelijk.

Eigen OpenAI-account gebruiken kan ook: voeg in Netlify onder Environment variables `OPENAI_API_KEY` toe met scope Functions, en eventueel `OPENAI_BASE_URL=https://api.openai.com/v1`. Laat de sleutel alleen op de server staan. Voeg hem nooit toe aan frontendbestanden of aan een VITE_-variabele. Het model is standaard `gpt-4.1-mini`; aanpassen kan via `OPENAI_MODEL`. Publiceer opnieuw als Netlify dit na een wijziging vraagt.

## Controle

Na het publiceren:
1. Voeg een kort hoofdstuk toe en controleer dat de tekst gelezen wordt.
2. Sla op en vernieuw de pagina: je les moet terugkomen.
3. Maak een oefentoets (met AI Gateway actief).
4. Beantwoord een vraag en controleer de uitleg.
5. Open Noor en stel een vraag over je eigen lesstof.

De ZIP is lokaal gebouwd en gecontroleerd. Er is nog geen publicatie in jouw Netlify-account uitgevoerd; die kan pas daar worden bevestigd.

## Voor ontwikkelaars

`npm ci` installeert de vastgelegde dependencies. `npm run build` controleert TypeScript, bouwt Vite en kopieert de PDF-worker. `npm test` controleert opslag, toegang per browser, uploadvalidatie, broncontrole van vragen, herhaalplanning, tutorcontext en de AI-limiet. De AI-tests gebruiken een simulatie; ze verbruiken geen betaalde AI-credits.

## Bronnen

- Netlify Drop: https://docs.netlify.com/manage/projects/add-new-project/
- Netlify Blobs: https://docs.netlify.com/build/data-and-storage/netlify-blobs/
- Netlify AI Gateway: https://docs.netlify.com/build/ai-gateway/overview/
