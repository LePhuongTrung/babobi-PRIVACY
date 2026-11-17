# Política de privadesa — BabiBo

BabiBo està desenvolupat per Le Phuong Trung.

_Darrera actualització: 17 de novembre de 2026_

BabiBo és una app de finances personals per a iPhone. No és una app per a
iPad. Qui la publica no opera cap servei que rebi el teu llibre major. No hi
ha cap compte de BabiBo, ni analítica, ni informes de fallades, ni
identificador de publicitat, ni cap SDK de tercers que enviï dades pel seu
compte.

Algunes funcions sí que envien dades fora del dispositiu, cap a una empresa
que tu tries o cap a un lloc que la funció ha d'assolir. Aquesta pàgina diu
què surt, com, per què, qui ho rep (inclòs el proveïdor d'IA), quant de temps
es conserva i com ho atures o ho esborres.

## Què es queda al dispositiu

Tot el que el llibre major coneix — comptes, saldos, moviments, categories,
pressupostos, posicions, fotos de tiquets i noms ja apresos d'un tiquet — es
guarda en un fitxer de base de dades dins el contenidor de l'app al teu
dispositiu.

Aquest fitxer entra a la còpia de seguretat del dispositiu. Si tens iCloud
Backup activat, una còpia xifrada viatja amb la resta del telèfon. Aquesta
còpia és entre tu i Apple. Nosaltres no la podem llegir.

Pots exportar el fitxer en qualsevol moment des de **Configuració → Dades** i
importar-lo a BabiBo en un altre dispositiu. Una còpia restaurada no porta la
sessió del banc: la clau de signatura es queda al telèfon que la va crear, i
tornes a connectar el banc al telèfon nou.

Eliminar l'app elimina aquest fitxer. Això inclou una clau d'API de Gemini
desada, els noms de productes ja apresos, els preus desats i els logotips en
memòria cau.

No fem servir aquestes dades per a publicitat ni seguiment, i no en rebem mai
una còpia.

## El teu banc, a través d'Enable Banking

Opcional, a l'iPhone, al Mac i a un servidor que allotges tu. No s'envia res
fins que registres la teva pròpia aplicació a Enable Banking i connectes un
banc.

**Què.** Saldos, extractes (els moviments) i els identificadors de compte que
retorna el banc, inclòs un IBAN quan el banc n'envia un.

**Com.** L'app pregunta a Enable Banking, que pregunta al teu banc, i escriu
la resposta al fitxer local. L'identificador de l'aplicació i la clau privada
es queden al teu dispositiu. A l'iPhone, un cop connectat un banc, l'app demana
a iOS que la desperti al matí — apunta a les 07:15, i omet la baixada si una
sincronització ja ha reeixit en les darreres sis hores — i torna a baixar els
extractes. iOS pot ignorar aquesta hora. La baixada només s'executa mentre
l'actualització en segon pla està activada per a BabiBo.

**Per què.** Per omplir el llibre major. Si has permès les notificacions, el
telèfon també publica un resum quan arriben moviments nous. Aquesta
notificació es crea al dispositiu. No se'ns envia.

**Qui.** Enable Banking i el teu banc. No nosaltres. Què en fan, de les dades,
segueix les seves condicions i el consentiment que dones en registrar-te i en
aprovar el banc.

**Quant de temps, i com aturar-ho.** La còpia a l'app roman fins que elimines
el compte. Eliminar un compte n'elimina els moviments i, quan és el darrer
compte d'aquella connexió, elimina la connexió, de manera que la baixada del
matí ja no té res a demanar. Enable Banking i el banc conserven el que exigeixen
les seves condicions. Nosaltres no podem esborrar la seva còpia. Revoca el
consentiment al teu banc, o a l'aplicació d'Enable Banking que vas registrar.

## Google Gemini

Opcional, i només a l'iPhone. No es fa cap petició fins que deses una clau a
**Configuració → Tiquets de compra**.

**Què.** Els noms abreujats dels articles impresos en un tiquet, i el nom del
comerç. No la foto, no els imports, no les dates i no la resta del llibre
major. Una petició més pot enviar paraules de categoria ja desades al telèfon
— paraules com « pollastre », sense comerç, import ni data — per arxivar-les
en una llista fixa de famílies de productes.

**Com.** Crees una clau a
[Google AI Studio](https://aistudio.google.com) i la deses a Configuració.
L'app crida llavors l'API Gemini de Google
(`generativelanguage.googleapis.com`) amb aquesta clau. Una etiqueta ja
resposta una vegada es queda al telèfon i no es torna a enviar.

**Per què.** Per convertir una abreviatura de caixa en un nom de producte i
una categoria, que es tornen a escriure al fitxer local.

**Qui.** Google, segons les condicions de l'API Gemini que s'apliquen a la clau
que vas crear. Nosaltres no rebem el text. Google és el proveïdor d'IA
d'aquesta funció.

**Quant de temps, i com aturar-ho.** Google conserva el que diuen aquestes
condicions. Nosaltres no fixem aquest termini i no tenim cap còpia en un
servidor nostre. La lectura roman a la base de dades local fins que elimines
l'app. **Configuració → Tiquets de compra → Retirer** esborra la clau del
telèfon i atura les peticions següents. El botó es diu Retirer. No esborra les
lectures ja desades al telèfon, i no esborra el que Google ja ha rebut.
Esborra o rota la clau també a Google AI Studio si vols que Google deixi
d'acceptar-la.

## Yahoo Finance

**Què.** Un símbol de cotització, com `CW8.PA`. Quan cerques un valor, el text
que vas escriure. No la quantitat, no el valor i no el nom del compte.

**Com.**

- A l'iPhone, una actualització del llibre major demana a Yahoo un preu per
  cada posició que té un símbol. Desar un símbol pregunta de seguida. El camp
  de cerca pregunta quan cerques. L'app no ho fa a la baixada en segon pla del
  matí.
- Al Mac, i en un servidor que tu allotges, Yahoo només es fa servir si poses
  el proveïdor de preus a Yahoo. L'ajust per defecte està desactivat, i
  aquestes versions no fan llavors cap petició de cotització.

La petició va a `query1.finance.yahoo.com`. No hi ha clau d'API. La connexió
també porta l'adreça de xarxa i un user agent, com qualsevol petició HTTPS.
L'app no afegeix cap nom ni cap identificador de compte.

**Per què.** Per mostrar un preu i, a l'iPhone, per trobar la cotització que
coincideix amb el que vas escriure.

**Qui.** Yahoo. No nosaltres.

**Quant de temps, i com aturar-ho.** Els preus s'escriuen al fitxer local i hi
romanen fins que elimines l'app. Yahoo conserva els seus propis registres
segons la seva política de privadesa. No tenim cap compte de Yahoo amb què
esborrar-los. A l'iPhone, elimina la posició per aturar més peticions de preu
sobre ella, i no cerquis si no vols que s'enviï el text. Al Mac i al teu
servidor, torna a posar el proveïdor de preus a `none`.

## Llocs dels comerços

Només iPhone. Activat per defecte.

**Què.** Cap camp del llibre major s'adjunta a la petició. L'app carrega
`https://` més el domini del comerç, i després la icona que aquella pàgina
anomena. La petició sembla un navegador que demana aquella adreça: la mateixa
adreça, l'adreça de xarxa del telèfon i un user agent de navegador. Les
galetes no es desen ni s'envien.

**Com.** Mentre **Configuració → Categories i comerços → Logotips dels
comerços** està activat, i un comerç té un lloc conegut o un lloc que vas
escriure. La imatge es demana la primera vegada que cal.

**Per què.** Per dibuixar la icona d'aquell comerç. Res més.

**Qui.** El lloc d'aquell comerç, i qui l'allotja. No un servei de logotips, i
no nosaltres.

**Quant de temps, i com aturar-ho.** La imatge roman a la memòria cau de l'app
fins que iOS esborra les memòries cau o elimines l'app. Un lloc sense una icona
utilitzable no es torna a demanar durant set dies. Els registres del lloc són
seus; nosaltres no els podem esborrar. Desactiva **Logotips dels comerços**
per aturar les peticions noves.

## Un servidor teu

Opcional. Si apuntes BabiBo a un servidor que operes tu, l'app hi llegeix i hi
escriu el llibre major. Aquella màquina és teva. Treu l'adreça del servidor a
Configuració per aturar-ho. Esborra el que el servidor va desar en aquella
màquina.

## Face ID

Si actives el bloqueig de l'app, BabiBo demana a iOS que et verifiqui. iOS
respon sí o no. Les teves dades biomètriques no arriben mai a l'app, i no
s'envien a ningú.

## Menors

BabiBo no s'adreça a menors.

## Canvis

Qualsevol canvi d'aquesta política es registra a
<https://github.com/LePhuongTrung/babobi-PRIVACY>, on l'historial és públic.

Aquesta pàgina és en català. La mateixa política en anglès és PRIVACY.md a
l'arrel. Les altres llengües de l'app són en una carpeta amb el codi de la
llengua.

## Contacte

No hi ha cap compte de BabiBo per esborrar, perquè nosaltres no en guardem
cap. Eliminar l'app elimina el fitxer local. Per a les dades que un destinatari
ja té, fes servir el camí indicat a la secció d'aquell destinatari.

Preguntes: <bububaba.support@lephuongtrung.id.vn>
