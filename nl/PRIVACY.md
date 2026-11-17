# Privacybeleid — BabiBo

BabiBo is ontwikkeld door Le Phuong Trung.

_Laatst bijgewerkt: 17 november 2026_

BabiBo is een app voor persoonlijke financiën voor iPhone. Het is geen
iPad-app. De mensen die de app publiceren, draaien geen dienst die uw grootboek
ontvangt. Er is geen BabiBo-account, geen statistiek, geen crashrapportage,
geen advertentie-id, en geen SDK van een derde die zelf gegevens verstuurt.

Sommige functies sturen wel gegevens van het apparaat, naar een bedrijf dat u
kiest of naar een site die de functie moet bereiken. Deze pagina zegt wat
vertrekt, hoe, waarom, wie het ontvangt (inclusief de AI-aanbieder), hoe lang
het wordt bewaard, en hoe u het stopt of verwijdert.

## Wat op het apparaat blijft

Alles wat het grootboek kent — rekeningen, saldi, transacties, categorieën,
budgetten, posities, bonfoto's en namen die al van een bon zijn geleerd —
staat in één databasebestand in de eigen container van de app op uw apparaat.

Dat bestand zit in de back-up van het apparaat. Als iCloud Backup aanstaat,
reist een versleutelde kopie mee met de rest van de telefoon. Die kopie is
tussen u en Apple. Wij kunnen hem niet lezen.

U kunt het bestand op elk moment exporteren via **Instellingen → Gegevens**,
en het importeren in BabiBo op een ander apparaat. Een herstelde kopie draagt
de banksessie niet: de ondertekeningssleutel blijft op de telefoon die hem
heeft gemaakt, en u verbindt de bank opnieuw op de nieuwe telefoon.

De app verwijderen verwijdert dit bestand. Dat omvat een opgeslagen
Gemini-API-sleutel, de al geleerde productnamen, opgeslagen prijzen en
gecachte logo's.

Wij gebruiken deze gegevens niet voor reclame of tracking, en wij ontvangen
er nooit een kopie van.

## Uw bank, via Enable Banking

Optioneel, op iPhone, Mac en een server die u zelf host. Er wordt niets
verstuurd totdat u uw eigen applicatie bij Enable Banking registreert en een
bank koppelt.

**Wat.** Saldi, afschriften (de transacties) en de rekening-id's die de bank
terugstuurt, inclusief een IBAN wanneer de bank die meestuurt.

**Hoe.** De app vraagt Enable Banking, die uw bank vraagt, en schrijft het
antwoord in het lokale bestand. Het applicatie-id en de privésleutel blijven
op uw apparaat. Op iPhone, zodra een bank is gekoppeld, vraagt de app iOS om
haar 's ochtends te wekken — ze mikt op 07:15, en ze slaat de download over
als een synchronisatie in de laatste zes uur al is gelukt — en downloadt de
afschriften opnieuw. iOS kan dat tijdstip negeren. De download draait alleen
terwijl Background App Refresh voor BabiBo aanstaat.

**Waarom.** Om het grootboek te vullen. Als u meldingen hebt toegestaan,
plaatst de telefoon ook één samenvatting wanneer er nieuwe transacties zijn.
Die melding wordt op het apparaat gemaakt. Hij wordt niet naar ons gestuurd.

**Wie.** Enable Banking en uw bank. Niet wij. Wat zij met de gegevens doen,
volgt hun voorwaarden en de toestemming die u geeft bij het registreren en
bij het goedkeuren van de bank.

**Hoe lang, en hoe te stoppen.** De kopie in de app blijft tot u de rekening
verwijdert. Een rekening verwijderen verwijdert haar transacties en, wanneer
het de laatste rekening van die koppeling is, verwijdert de koppeling, zodat
de ochtenddownload niets meer te vragen heeft. Enable Banking en de bank
bewaren wat hun eigen voorwaarden eisen. Wij kunnen hun kopie niet
verwijderen. Trek de toestemming in bij uw bank, of in de Enable
Banking-applicatie die u hebt geregistreerd.

## Google Gemini

Optioneel, en alleen op iPhone. Er gaat geen verzoek uit totdat u een sleutel
opslaat onder **Instellingen → Kassabonnen**.

**Wat.** De verkorte artikelnamen die op een bon staan, en de naam van de
winkel. Niet de foto, niet de bedragen, niet de datums, en niet de rest van
het grootboek. Een volgend verzoek kan categoriewoorden sturen die al op de
telefoon staan — woorden zoals « kip », zonder winkel, bedrag of datum — zodat
ze in een vaste lijst van productfamilies kunnen worden geplaatst.

**Hoe.** U maakt een sleutel op
[Google AI Studio](https://aistudio.google.com) en slaat hem op in
Instellingen. De app roept daarna de Gemini-API van Google aan
(`generativelanguage.googleapis.com`) met die sleutel. Een label dat één keer
is beantwoord, blijft op de telefoon en wordt niet opnieuw gestuurd.

**Waarom.** Om een kassa-afkorting om te zetten in een productnaam en een
categorie, die terug in het lokale bestand worden geschreven.

**Wie.** Google, onder de Gemini-API-voorwaarden die gelden voor de sleutel
die u hebt gemaakt. Wij ontvangen de tekst niet. Google is de AI-aanbieder
van deze functie.

**Hoe lang, en hoe te stoppen.** Google bewaart wat die voorwaarden zeggen.
Wij stellen die termijn niet vast, en wij hebben geen kopie op een server van
ons. De lezing blijft in de lokale database tot u de app verwijdert.
**Instellingen → Kassabonnen → Retirer** verwijdert de sleutel van de
telefoon en stopt verdere verzoeken. De knop heet Retirer. Dit wist geen
lezingen die al op de telefoon staan, en het wist niet wat Google al heeft
ontvangen. Verwijder of vernieuw de sleutel ook in Google AI Studio als u
wilt dat Google hem niet meer aanvaardt.

## Yahoo Finance

**Wat.** Een tickersymbool, zoals `CW8.PA`. Wanneer u een effect zoekt, de
tekst die u hebt getypt. Niet het aantal, niet de waarde, en niet de
rekeningnaam.

**Hoe.**

- Op iPhone vraagt een verversing van het grootboek Yahoo om een koers voor
  elke positie die een symbool heeft. Een symbool opslaan vraagt meteen. Het
  zoekveld vraagt wanneer u zoekt. De app doet dit niet in de
  achtergronddownload van de ochtend.
- Op Mac, en op een server die u host, wordt Yahoo alleen gebruikt als u de
  koersaanbieder op Yahoo zet. De standaard staat uit, en die versies doen dan
  geen koersverzoek.

Het verzoek gaat naar `query1.finance.yahoo.com`. Er is geen API-sleutel. De
verbinding draagt ook het netwerkadres en een user agent, zoals elk
HTTPS-verzoek. De app voegt geen naam en geen rekening-id toe.

**Waarom.** Om een koers te tonen en, op iPhone, om de notering te vinden die
bij wat u typte past.

**Wie.** Yahoo. Niet wij.

**Hoe lang, en hoe te stoppen.** Koersen worden in het lokale bestand
geschreven en blijven tot u de app verwijdert. Yahoo bewaart zijn eigen logs
onder zijn privacybeleid. Wij hebben geen Yahoo-account waarmee die logs
kunnen worden verwijderd. Verwijder op iPhone de positie om verdere
koersverzoeken ervoor te stoppen, en zoek niet als u niet wilt dat de tekst
wordt verstuurd. Zet op Mac en op uw server de koersaanbieder terug op
`none`.

## Websites van winkels

Alleen iPhone. Standaard aan.

**Wat.** Geen veld uit het grootboek wordt aan het verzoek gehangen. De app
laadt `https://` plus het domein van de winkel, en daarna het pictogram dat
die pagina noemt. Het verzoek lijkt op een browser die dat adres opvraagt: het
adres zelf, het netwerkadres van de telefoon, en een browser-user-agent.
Cookies worden niet opgeslagen en niet verstuurd.

**Hoe.** Zolang **Instellingen → Categorieën en handelaren → Logo's van
winkels** aanstaat, en een winkel een bekende site heeft of een site die u
hebt getypt. De afbeelding wordt de eerste keer opgevraagd dat ze nodig is.

**Waarom.** Om het pictogram van die winkel te tekenen. Verder niets.

**Wie.** De website van die winkel, en wie haar host. Geen logodienst, en niet
wij.

**Hoe lang, en hoe te stoppen.** De afbeelding blijft in de cache van de app
tot iOS caches wist of u de app verwijdert. Een site zonder bruikbaar
pictogram wordt zeven dagen niet opnieuw gevraagd. De logs van de site zijn
van de site; wij kunnen ze niet verwijderen. Zet **Logo's van winkels** uit
om nieuwe verzoeken te stoppen.

## Uw eigen server

Optioneel. Als u BabiBo naar een server wijst die u zelf draait, leest en
schrijft de app het grootboek daar. Die machine is van u. Verwijder het
serveradres in Instellingen om te stoppen. Verwijder wat de server op die
machine heeft opgeslagen.

## Face ID

Als u het app-slot aanzet, vraagt BabiBo iOS om u te verifiëren. iOS antwoordt
ja of nee. Uw biometrie bereikt de app nooit, en wordt aan niemand gestuurd.

## Kinderen

BabiBo is niet op kinderen gericht.

## Wijzigingen

Elke wijziging van dit beleid wordt vastgelegd op
<https://github.com/LePhuongTrung/babobi-PRIVACY>, waar de geschiedenis openbaar
is.

Deze pagina is Nederlands. Hetzelfde beleid in het Engels is PRIVACY.md in de
hoofdmap. De andere talen van de app staan in een map met de taalcode.

## Contact

Er is geen BabiBo-account om te verwijderen, omdat wij er geen bewaren. De app
verwijderen verwijdert het lokale bestand. Voor gegevens die een ontvanger al
heeft, gebruikt u het pad in het onderdeel van die ontvanger hierboven.

Vragen: <bububaba.support@lephuongtrung.id.vn>
