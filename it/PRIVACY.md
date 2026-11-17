# Informativa sulla privacy — BabiBo

BabiBo è sviluppato da Le Phuong Trung.

_Ultimo aggiornamento: 17 novembre 2026_

BabiBo è un'app di finanza personale per iPhone. Non è un'app per iPad. Chi la
pubblica non gestisce un servizio che riceve il tuo libro mastro. Non c'è un
account BabiBo, non ci sono statistiche, non c'è segnalazione degli arresti
anomali, non c'è un identificatore pubblicitario e non c'è un SDK di terzi che
invii dati da solo.

Alcune funzioni inviano dati fuori dal dispositivo, verso una società che
scegli tu o verso un sito che la funzione deve raggiungere. Questa pagina dice
che cosa esce, come, perché, chi lo riceve (compreso il fornitore di IA), per
quanto tempo viene conservato e come lo interrompi o lo cancelli.

## Che cosa resta sul dispositivo

Tutto ciò che il libro mastro conosce — conti, saldi, movimenti, categorie,
budget, titoli detenuti, foto degli scontrini e nomi già imparati da uno
scontrino — è conservato in un file di database dentro il contenitore
dell'app sul tuo dispositivo.

Quel file è incluso nel backup del dispositivo. Se iCloud Backup è attivo, una
copia cifrata viaggia con il resto del telefono. Quella copia è tra te e
Apple. Noi non possiamo leggerla.

Puoi esportare il file in qualsiasi momento da **Impostazioni → Dati** e
importarlo in BabiBo su un altro dispositivo. Una copia ripristinata non porta
la sessione della banca: la chiave di firma resta sul telefono che l'ha
creata, e ricolleghi la banca sul telefono nuovo.

Eliminare l'app elimina questo file. Ciò include una chiave API Gemini
salvata, i nomi dei prodotti già imparati, i prezzi salvati e i loghi in
cache.

Non usiamo questi dati per pubblicità o tracciamento, e non ne riceviamo mai
una copia.

## La tua banca, tramite Enable Banking

Facoltativo, su iPhone, Mac e un server che ospiti tu. Non viene inviato nulla
finché non registri una tua applicazione presso Enable Banking e colleghi una
banca.

**Che cosa.** Saldi, estratti (i movimenti) e gli identificatori di conto che
la banca restituisce, compreso un IBAN quando la banca ne invia uno.

**Come.** L'app chiede a Enable Banking, che chiede alla tua banca, e scrive
la risposta nel file locale. L'id dell'applicazione e la chiave privata
restano sul tuo dispositivo. Su iPhone, una volta collegata una banca, l'app
chiede a iOS di svegliarla al mattino — punta alle 07:15 e salta lo scaricamento
se una sincronizzazione è già riuscita nelle ultime sei ore — e scarica di
nuovo gli estratti. iOS può ignorare quell'orario. Lo scaricamento avviene
solo mentre l'aggiornamento delle app in background è attivo per BabiBo.

**Perché.** Per riempire il libro mastro. Se hai consentito le notifiche, il
telefono pubblica anche un riepilogo quando arrivano nuovi movimenti. Quella
notifica è creata sul dispositivo. Non viene inviata a noi.

**Chi.** Enable Banking e la tua banca. Non noi. Che cosa ne fanno dei dati
segue le loro condizioni e il consenso che dai quando ti registri e quando
approvi la banca.

**Per quanto tempo, e come fermarlo.** La copia nell'app resta finché non
elimini il conto. Eliminare un conto elimina i suoi movimenti e, quando è
l'ultimo conto di quella connessione, elimina la connessione, così lo
scaricamento del mattino non ha più nulla da chiedere. Enable Banking e la
banca conservano ciò che le loro condizioni richiedono. Non possiamo cancellare
la loro copia. Revoca il consenso nella tua banca, o nell'applicazione Enable
Banking che hai registrato.

## Google Gemini

Facoltativo, e solo su iPhone. Nessuna richiesta parte finché non salvi una
chiave in **Impostazioni → Scontrini**.

**Che cosa.** I nomi abbreviati degli articoli stampati su uno scontrino e il
nome dell'esercente. Non la foto, non gli importi, non le date e non il resto
del libro mastro. Un'ulteriore richiesta può inviare parole di categoria già
memorizzate sul telefono — parole come « pollo », senza esercente, importo o
data — per archiviarle in un elenco fisso di famiglie di prodotti.

**Come.** Crei una chiave su
[Google AI Studio](https://aistudio.google.com) e la salvi in Impostazioni.
L'app chiama poi l'API Gemini di Google
(`generativelanguage.googleapis.com`) con quella chiave. Un'etichetta a cui
è già stata data risposta una volta resta sul telefono e non viene inviata di
nuovo.

**Perché.** Per trasformare un'abbreviazione di cassa in un nome di prodotto e
in una categoria, che vengono riscritti nel file locale.

**Chi.** Google, secondo le condizioni dell'API Gemini che si applicano alla
chiave che hai creato. Noi non riceviamo il testo. Google è il fornitore di
IA di questa funzione.

**Per quanto tempo, e come fermarlo.** Google conserva ciò che quelle
condizioni prevedono. Non fissiamo noi quel periodo e non abbiamo una copia su
un server nostro. La lettura resta nel database locale finché non elimini
l'app. **Impostazioni → Scontrini → Retirer** elimina la chiave dal telefono
e interrompe le richieste successive. Il pulsante è etichettato Retirer. Non
cancella le letture già memorizzate sul telefono e non cancella ciò che Google
ha già ricevuto. Elimina o ruota la chiave anche in Google AI Studio se vuoi
che Google smetta di accettarla.

## Yahoo Finance

**Che cosa.** Un simbolo di titolo, per esempio `CW8.PA`. Quando cerchi un
titolo, il testo che hai digitato. Non la quantità, non il valore e non il
nome del conto.

**Come.**

- Su iPhone, un aggiornamento del libro mastro chiede a Yahoo un prezzo per
  ogni posizione che ha un simbolo. Salvare un simbolo chiede subito. Il campo
  di ricerca chiede quando cerchi. L'app non lo fa nello scaricamento in
  background del mattino.
- Su Mac, e su un server che ospiti tu, Yahoo si usa solo se imposti il
  fornitore di prezzi su Yahoo. L'impostazione predefinita è disattivata, e
  quelle versioni non fanno allora alcuna richiesta di quotazione.

La richiesta va a `query1.finance.yahoo.com`. Non c'è una chiave API. La
connessione porta anche l'indirizzo di rete e uno user agent, come ogni
richiesta HTTPS. L'app non aggiunge un nome né un id di conto.

**Perché.** Per mostrare un prezzo e, su iPhone, per trovare la quotazione che
corrisponde a ciò che hai digitato.

**Chi.** Yahoo. Non noi.

**Per quanto tempo, e come fermarlo.** I prezzi vengono scritti nel file
locale e restano finché non elimini l'app. Yahoo conserva i propri registri
secondo la sua informativa sulla privacy. Non abbiamo un account Yahoo con cui
cancellarli. Su iPhone, elimina la posizione per fermare le ulteriori
richieste di prezzo per essa, e non cercare se non vuoi che il testo venga
inviato. Su Mac e sul tuo server, riporta il fornitore di prezzi su `none`.

## Siti degli esercenti

Solo iPhone. Attivo per impostazione predefinita.

**Che cosa.** Nessun campo del libro mastro è allegato alla richiesta. L'app
carica `https://` più il dominio dell'esercente, poi l'icona che quella pagina
indica. La richiesta assomiglia a un browser che chiede quell'indirizzo:
l'indirizzo stesso, l'indirizzo di rete del telefono e uno user agent da
browser. I cookie non vengono né memorizzati né inviati.

**Come.** Mentre **Impostazioni → Categorie ed esercenti → Loghi degli
esercenti** è attivo, e un esercente ha un sito noto o un sito che hai
digitato. L'immagine viene richiesta la prima volta che serve.

**Perché.** Per disegnare l'icona di quell'esercente. Nient'altro.

**Chi.** Il sito di quell'esercente, e chi lo ospita. Non un servizio di loghi,
e non noi.

**Per quanto tempo, e come fermarlo.** L'immagine resta nella cache dell'app
finché iOS non svuota le cache o tu non elimini l'app. Un sito senza un'icona
utilizzabile non viene richiesto di nuovo per sette giorni. I registri del
sito sono suoi; non possiamo cancellarli. Disattiva **Loghi degli esercenti**
per fermare le nuove richieste.

## Un tuo server

Facoltativo. Se punti BabiBo a un server che gestisci tu, l'app legge e
scrive lì il libro mastro. Quella macchina è tua. Rimuovi l'indirizzo del
server in Impostazioni per fermarti. Cancella ciò che il server ha memorizzato
su quella macchina.

## Face ID

Se attivi il blocco dell'app, BabiBo chiede a iOS di verificarti. iOS risponde
sì o no. I tuoi dati biometrici non raggiungono mai l'app e non vengono inviati
a nessuno.

## Minori

BabiBo non è rivolto ai minori.

## Modifiche

Ogni modifica di questa informativa viene registrata su
<https://github.com/LePhuongTrung/babobi-PRIVACY>, dove la cronologia è
pubblica.

Questa pagina è in italiano. La stessa informativa in inglese è PRIVACY.md
nella cartella principale. Le altre lingue dell'app stanno in una cartella con
il codice della lingua.

## Contatto

Non c'è un account BabiBo da eliminare, perché non ne conserviamo uno.
Eliminare l'app elimina il file locale. Per i dati che un destinatario ha già,
usa il percorso indicato nella sezione di quel destinatario.

Domande: <bububaba.support@lephuongtrung.id.vn>
