# Datenschutzerklärung — BabiBo

BabiBo wird von Le Phuong Trung entwickelt.

_Zuletzt aktualisiert: 17. November 2026_

BabiBo ist eine App für persönliche Finanzen für das iPhone. Es ist keine
iPad-App. Die Personen, die sie veröffentlichen, betreiben keinen Dienst, der
dein Hauptbuch empfängt. Es gibt kein BabiBo-Konto, keine Auswertung, keine
Absturzberichte, keine Werbe-ID und kein SDK eines Dritten, das von sich aus
Daten sendet.

Einige Funktionen senden Daten vom Gerät, an ein Unternehmen, das du wählst,
oder an eine Site, die die Funktion erreichen muss. Diese Seite sagt, was das
Gerät verlässt, wie, warum, wer es empfängt (einschließlich des
KI-Anbieters), wie lange es aufbewahrt wird und wie du es stoppst oder
löschst.

## Was auf dem Gerät bleibt

Alles, was das Hauptbuch kennt — Konten, Salden, Buchungen, Kategorien,
Budgets, Bestände, Belegfotos und Namen, die bereits von einem Beleg gelernt
wurden — liegt in einer Datenbankdatei im eigenen Container der App auf deinem
Gerät.

Diese Datei ist in der Sicherung des Geräts enthalten. Wenn iCloud Backup
eingeschaltet ist, reist eine verschlüsselte Kopie mit dem Rest des Telefons.
Diese Kopie liegt zwischen dir und Apple. Wir können sie nicht lesen.

Du kannst die Datei jederzeit unter **Einstellungen → Daten** exportieren und
sie auf einem anderen Gerät in BabiBo importieren. Eine wiederhergestellte
Kopie trägt die Banksitzung nicht: Der Signaturschlüssel bleibt auf dem
Telefon, das ihn erzeugt hat, und du verbindest die Bank auf dem neuen Telefon
erneut.

Die App zu löschen löscht diese Datei. Dazu gehören ein gespeicherter
Gemini-API-Schlüssel, bereits gelernte Produktnamen, gespeicherte Preise und
zwischengespeicherte Logos.

Wir verwenden diese Daten nicht für Werbung oder Tracking, und wir erhalten
nie eine Kopie.

## Deine Bank, über Enable Banking

Optional, auf iPhone, Mac und einem Server, den du selbst betreibst. Es wird
nichts gesendet, bis du deine eigene Anwendung bei Enable Banking registrierst
und eine Bank verbindest.

**Was.** Salden, Auszüge (die Buchungen) und die Kontokennungen, die die Bank
zurückgibt, einschließlich einer IBAN, wenn die Bank eine sendet.

**Wie.** Die App fragt Enable Banking, das deine Bank fragt, und schreibt die
Antwort in die lokale Datei. Die Anwendungskennung und der private Schlüssel
bleiben auf deinem Gerät. Auf dem iPhone bittet die App iOS, sobald eine Bank
verbunden ist, sie am Morgen zu wecken — sie zielt auf 07:15 und überspringt
den Abruf, wenn eine Synchronisierung in den letzten sechs Stunden bereits
gelungen ist — und lädt die Auszüge erneut. iOS kann diese Uhrzeit ignorieren.
Der Abruf läuft nur, solange die Hintergrundaktualisierung für BabiBo
eingeschaltet ist.

**Warum.** Um das Hauptbuch zu füllen. Wenn du Mitteilungen erlaubt hast,
veröffentlicht das Telefon auch eine Zusammenfassung, wenn neue Buchungen
eingetroffen sind. Diese Mitteilung entsteht auf dem Gerät. Sie wird nicht an
uns gesendet.

**Wer.** Enable Banking und deine Bank. Nicht wir. Was sie mit den Daten tun,
folgt ihren Bedingungen und der Einwilligung, die du bei der Registrierung und
bei der Freigabe der Bank gibst.

**Wie lange, und wie aufhören.** Die Kopie in der App bleibt, bis du das Konto
löschst. Ein Konto zu löschen löscht seine Buchungen und, wenn es das letzte
Konto dieser Verbindung ist, die Verbindung, sodass der morgendliche Abruf
nichts mehr zu fragen hat. Enable Banking und die Bank behalten, was ihre
eigenen Bedingungen verlangen. Wir können ihre Kopie nicht löschen. Widerrufe
die Einwilligung bei deiner Bank oder in der Enable-Banking-Anwendung, die du
registriert hast.

## Google Gemini

Optional, und nur auf dem iPhone. Es geht keine Anfrage hinaus, bis du einen
Schlüssel unter **Einstellungen → Kassenbons** speicherst.

**Was.** Die abgekürzten Artikelnamen auf einem Beleg und der Name des
Händlers. Nicht das Foto, nicht die Beträge, nicht die Daten und nicht der
Rest des Hauptbuchs. Eine weitere Anfrage kann bereits auf dem Telefon
gespeicherte Kategoriebegriffe senden — Wörter wie „Hähnchen“, ohne Händler,
Betrag oder Datum — damit sie in eine feste Liste von Produktfamilien
eingeordnet werden.

**Wie.** Du erstellst einen Schlüssel bei
[Google AI Studio](https://aistudio.google.com) und speicherst ihn in den
Einstellungen. Die App ruft dann die Gemini-API von Google auf
(`generativelanguage.googleapis.com`), mit diesem Schlüssel. Eine Bezeichnung,
die einmal beantwortet wurde, bleibt auf dem Telefon und wird nicht erneut
gesendet.

**Warum.** Um eine Kassenabkürzung in einen Produktnamen und eine Kategorie zu
verwandeln, die in die lokale Datei zurückgeschrieben werden.

**Wer.** Google, nach den Gemini-API-Bedingungen, die für den von dir
erstellten Schlüssel gelten. Wir erhalten den Text nicht. Google ist der
KI-Anbieter dieser Funktion.

**Wie lange, und wie aufhören.** Google behält, was diese Bedingungen sagen.
Wir legen diese Frist nicht fest, und wir haben keine Kopie auf einem Server
von uns. Die Lesung bleibt in der lokalen Datenbank, bis du die App löschst.
**Einstellungen → Kassenbons → Retirer** löscht den Schlüssel vom Telefon und
stoppt weitere Anfragen. Die Taste heißt Retirer. Das löscht keine bereits auf
dem Telefon gespeicherten Lesungen und nicht das, was Google bereits erhalten
hat. Lösche oder erneuere den Schlüssel auch in Google AI Studio, wenn Google
ihn nicht mehr annehmen soll.

## Yahoo Finance

**Was.** Ein Tickersymbol, zum Beispiel `CW8.PA`. Wenn du ein Wertpapier
suchst, der Text, den du eingegeben hast. Nicht die Menge, nicht der Wert und
nicht der Kontoname.

**Wie.**

- Auf dem iPhone fragt eine Aktualisierung des Hauptbuchs Yahoo nach einem
  Preis für jeden Bestand, der ein Symbol hat. Ein Symbol zu speichern fragt
  sofort. Das Suchfeld fragt, wenn du suchst. Die App tut das nicht beim
  morgendlichen Abruf im Hintergrund.
- Auf dem Mac und auf einem Server, den du betreibst, wird Yahoo nur verwendet,
  wenn du den Kursanbieter auf Yahoo stellst. Die Voreinstellung ist aus, und
  diese Versionen stellen dann keine Kursanfrage.

Die Anfrage geht an `query1.finance.yahoo.com`. Es gibt keinen API-Schlüssel.
Die Verbindung trägt auch die Netzwerkadresse und einen User-Agent, wie jede
HTTPS-Anfrage. Die App fügt keinen Namen und keine Kontokennung hinzu.

**Warum.** Um einen Preis zu zeigen und, auf dem iPhone, die Notierung zu
finden, die zu dem passt, was du eingegeben hast.

**Wer.** Yahoo. Nicht wir.

**Wie lange, und wie aufhören.** Preise werden in die lokale Datei geschrieben
und bleiben, bis du die App löschst. Yahoo behält seine eigenen Protokolle nach
seiner Datenschutzerklärung. Wir haben kein Yahoo-Konto, mit dem sie gelöscht
werden könnten. Lösche auf dem iPhone den Bestand, um weitere Preisanfragen
dafür zu stoppen, und suche nicht, wenn der Text nicht gesendet werden soll.
Stelle auf dem Mac und auf deinem Server den Kursanbieter zurück auf `none`.

## Websites der Händler

Nur iPhone. Standardmäßig an.

**Was.** Kein Feld aus dem Hauptbuch wird an die Anfrage gehängt. Die App lädt
`https://` plus die Domain des Händlers und danach das Symbol, das diese Seite
nennt. Die Anfrage sieht aus wie ein Browser, der diese Adresse abruft: die
Adresse selbst, die Netzwerkadresse des Telefons und ein Browser-User-Agent.
Cookies werden weder gespeichert noch gesendet.

**Wie.** Solange **Einstellungen → Kategorien und Händler → Händlerlogos**
eingeschaltet ist und ein Händler eine bekannte Site oder eine von dir
eingegebene Site hat. Das Bild wird angefordert, wenn es zum ersten Mal
gebraucht wird.

**Warum.** Um das Symbol dieses Händlers zu zeichnen. Nichts weiter.

**Wer.** Die Website dieses Händlers und wer sie betreibt. Kein Logo-Dienst,
und nicht wir.

**Wie lange, und wie aufhören.** Das Bild bleibt im Cache der App, bis iOS
Caches leert oder du die App löschst. Eine Site ohne verwendbares Symbol wird
sieben Tage lang nicht erneut gefragt. Die Protokolle der Site gehören der
Site; wir können sie nicht löschen. Schalte **Händlerlogos** aus, um neue
Anfragen zu stoppen.

## Dein eigener Server

Optional. Wenn du BabiBo auf einen Server richtest, den du betreibst, liest
und schreibt die App das Hauptbuch dort. Diese Maschine gehört dir. Entferne
die Serveradresse in den Einstellungen, um aufzuhören. Lösche, was der Server
auf dieser Maschine gespeichert hat.

## Face ID

Wenn du die App-Sperre einschaltest, bittet BabiBo iOS, dich zu prüfen. iOS
antwortet mit ja oder nein. Deine biometrischen Daten erreichen die App nie
und werden an niemanden gesendet.

## Kinder

BabiBo richtet sich nicht an Kinder.

## Änderungen

Jede Änderung dieser Erklärung wird auf
<https://github.com/LePhuongTrung/babobi-PRIVACY> festgehalten, wo die
Geschichte öffentlich ist.

Diese Seite ist Deutsch. Dieselbe Erklärung auf Englisch ist PRIVACY.md im
Stammverzeichnis. Die anderen Sprachen der App liegen in einem Ordner mit dem
Sprachcode.

## Kontakt

Es gibt kein BabiBo-Konto zu löschen, weil wir keines führen. Die App zu
löschen löscht die lokale Datei. Für Daten, die ein Empfänger bereits hat,
gilt der Weg im Abschnitt dieses Empfängers oben.

Fragen: <bububaba.support@lephuongtrung.id.vn>
