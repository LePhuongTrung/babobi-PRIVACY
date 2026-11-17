# Politique de confidentialité — BabiBo

BabiBo est développé par Le Phuong Trung.

_Dernière mise à jour : 17 novembre 2026_

BabiBo est une application de finances personnelles pour iPhone. Ce n'est pas
une application pour iPad. Les personnes qui la publient n'exploitent pas de
service qui reçoit votre grand livre. Il n'y a pas de compte BabiBo, pas
d'analyse d'usage, pas de rapport de plantage, pas d'identifiant publicitaire,
et pas de SDK tiers qui envoie des données de lui-même.

Certaines fonctions envoient des données hors de l'appareil, vers une société
que vous choisissez ou vers un site que la fonction doit joindre. Cette page
dit ce qui part, comment, pourquoi, qui le reçoit (y compris le fournisseur
d'IA), combien de temps c'est conservé, et comment vous l'arrêtez ou
l'effacez.

## Ce qui reste sur l'appareil

Tout ce que le grand livre connaît — comptes, soldes, opérations, catégories,
budgets, titres détenus, photos de tickets, et noms déjà appris d'un ticket —
est stocké dans un fichier de base de données, dans le conteneur de
l'application sur votre appareil.

Ce fichier est inclus dans la sauvegarde de l'appareil. Si iCloud Backup est
activé, une copie chiffrée part avec le reste du téléphone. Cette copie est
entre vous et Apple. Nous ne pouvons pas la lire.

Vous pouvez exporter le fichier à tout moment depuis **Réglages → Données**,
et l'importer dans BabiBo sur un autre appareil. Une copie restaurée ne porte
pas la session bancaire : la clé de signature reste sur le téléphone qui l'a
créée, et vous reconnectez la banque sur le nouveau téléphone.

Supprimer l'application supprime ce fichier. Cela comprend une clé d'API
Gemini enregistrée, les noms de produits déjà appris, les prix enregistrés et
les logos en cache.

Nous n'utilisons aucune de ces données pour la publicité ou le suivi, et nous
n'en recevons jamais de copie.

## Votre banque, via Enable Banking

Facultatif, sur iPhone, Mac, et un serveur que vous hébergez. Rien n'est
envoyé tant que vous n'avez pas enregistré votre propre application auprès
d'Enable Banking et connecté une banque.

**Quoi.** Les soldes, les relevés (les opérations), et les identifiants de
compte que la banque renvoie, y compris un IBAN lorsque la banque en envoie
un.

**Comment.** L'application interroge Enable Banking, qui interroge votre
banque, puis écrit la réponse dans le fichier local. L'identifiant
d'application et la clé privée restent sur votre appareil. Sur iPhone, une
fois une banque connectée, l'application demande à iOS de la réveiller le
matin — elle vise 07:15, et elle saute le téléchargement si une
synchronisation a déjà réussi dans les six dernières heures — puis télécharge
à nouveau les relevés. iOS peut ignorer cette heure. Le téléchargement ne
s'exécute que si l'actualisation en arrière-plan est activée pour BabiBo.

**Pourquoi.** Pour remplir le grand livre. Si vous avez autorisé les
notifications, le téléphone publie aussi un résumé lorsque de nouvelles
opérations sont arrivées. Cette notification est créée sur l'appareil. Elle
ne nous est pas envoyée.

**Qui.** Enable Banking et votre banque. Pas nous. Ce qu'ils font des données
suit leurs conditions et le consentement que vous donnez lorsque vous vous
inscrivez et lorsque vous approuvez la banque.

**Combien de temps, et comment arrêter.** La copie dans l'application reste
jusqu'à ce que vous supprimiez le compte. Supprimer un compte supprime ses
opérations et, lorsqu'il s'agit du dernier compte de cette connexion, supprime
la connexion, de sorte que le téléchargement du matin n'a plus rien à
demander. Enable Banking et la banque conservent ce que leurs propres
conditions exigent. Nous ne pouvons pas supprimer leur copie. Révoquez le
consentement dans votre banque, ou dans l'application Enable Banking que vous
avez enregistrée.

## Google Gemini

Facultatif, et seulement sur iPhone. Aucune requête n'est faite tant que vous
n'avez pas enregistré une clé dans **Réglages → Tickets de caisse**.

**Quoi.** Les noms d'articles abrégés imprimés sur un ticket, et le nom du
commerçant. Pas la photo, pas les montants, pas les dates, et pas le reste du
grand livre. Une requête supplémentaire peut envoyer des mots de catégorie
déjà stockés sur le téléphone — des mots comme « poulet », sans commerçant,
montant ni date — afin de les ranger dans une liste fixe de familles de
produits.

**Comment.** Vous créez une clé sur
[Google AI Studio](https://aistudio.google.com) et vous l'enregistrez dans
Réglages. L'application appelle alors l'API Gemini de Google
(`generativelanguage.googleapis.com`) avec cette clé. Un libellé déjà répondu
une fois est conservé sur le téléphone et n'est pas renvoyé.

**Pourquoi.** Pour transformer une abréviation de caisse en nom de produit et
en catégorie, qui sont réécrits dans le fichier local.

**Qui.** Google, selon les conditions de l'API Gemini qui s'appliquent à la
clé que vous avez créée. Nous ne recevons pas le texte. Google est le
fournisseur d'IA de cette fonction.

**Combien de temps, et comment arrêter.** Google conserve ce que ces
conditions prévoient. Nous ne fixons pas cette durée, et nous n'avons pas de
copie sur un serveur à nous. La lecture reste dans la base locale jusqu'à ce
que vous supprimiez l'application. **Réglages → Tickets de caisse → Retirer**
supprime la clé du téléphone et arrête les requêtes suivantes. Cela n'efface
pas les lectures déjà stockées sur le téléphone, et cela n'efface pas ce que
Google a déjà reçu. Supprimez ou renouvelez aussi la clé dans Google AI Studio
si vous voulez que Google cesse de l'accepter.

## Yahoo Finance

**Quoi.** Un symbole de titre, par exemple `CW8.PA`. Lorsque vous cherchez un
titre, le texte que vous avez saisi. Pas la quantité, pas la valeur, et pas le
nom du compte.

**Comment.**

- Sur iPhone, une actualisation du grand livre demande à Yahoo un cours pour
  chaque titre qui a un symbole. Enregistrer un symbole interroge tout de
  suite. Le champ de recherche interroge lorsque vous cherchez. L'application
  ne le fait pas pendant le téléchargement du matin en arrière-plan.
- Sur Mac, et sur un serveur que vous hébergez, Yahoo n'est utilisé que si
  vous réglez le fournisseur de cours sur Yahoo. Le réglage par défaut est
  désactivé, et ces versions ne font alors aucune demande de cours.

La requête va vers `query1.finance.yahoo.com`. Il n'y a pas de clé d'API. La
connexion porte aussi l'adresse réseau et un user agent, comme toute requête
HTTPS. L'application n'ajoute ni nom ni identifiant de compte.

**Pourquoi.** Pour afficher un cours et, sur iPhone, pour trouver la cotation
qui correspond à ce que vous avez saisi.

**Qui.** Yahoo. Pas nous.

**Combien de temps, et comment arrêter.** Les cours sont écrits dans le
fichier local et y restent jusqu'à ce que vous supprimiez l'application. Yahoo
conserve ses propres journaux selon sa politique de confidentialité. Nous
n'avons pas de compte Yahoo qui pourrait les supprimer. Sur iPhone, supprimez
le titre pour arrêter les demandes de cours qui le concernent, et ne cherchez
pas si vous ne voulez pas que le texte soit envoyé. Sur Mac et sur votre
serveur, remettez le fournisseur de cours sur `none`.

## Sites des commerçants

iPhone seulement. Activé par défaut.

**Quoi.** Aucun champ du grand livre n'est joint à la requête. L'application
charge `https://` plus le domaine du commerçant, puis l'icône que cette page
nomme. La requête ressemble à un navigateur qui demande cette adresse :
l'adresse elle-même, l'adresse réseau du téléphone, et un user agent de
navigateur. Les cookies ne sont ni stockés ni envoyés.

**Comment.** Tant que **Réglages → Catégories et marchands → Logos des
marchands** est activé, et qu'un commerçant a un site connu ou un site que
vous avez saisi. L'image est demandée la première fois qu'elle est nécessaire.

**Pourquoi.** Pour dessiner l'icône de ce commerçant. Rien d'autre.

**Qui.** Le site de ce commerçant, et celui qui l'héberge. Pas un service de
logos, et pas nous.

**Combien de temps, et comment arrêter.** L'image reste dans le cache de
l'application jusqu'à ce qu'iOS efface les caches ou que vous supprimiez
l'application. Un site sans icône utilisable n'est pas redemandé pendant sept
jours. Les journaux du site lui appartiennent ; nous ne pouvons pas les
supprimer. Désactivez **Logos des marchands** pour arrêter les nouvelles
requêtes.

## Votre propre serveur

Facultatif. Si vous pointez BabiBo vers un serveur que vous exploitez,
l'application y lit et y écrit le grand livre. Cette machine est la vôtre.
Retirez l'adresse du serveur dans Réglages pour arrêter. Supprimez ce que le
serveur a stocké sur cette machine.

## Face ID

Si vous activez le verrou de l'application, BabiBo demande à iOS de vous
vérifier. iOS répond oui ou non. Vos données biométriques n'entrent jamais
dans l'application, et elles ne sont envoyées à personne.

## Enfants

BabiBo ne s'adresse pas aux enfants.

## Modifications

Toute modification de cette politique est enregistrée sur
<https://github.com/LePhuongTrung/babobi-PRIVACY>, où son historique est
public.

Cette page est en français. La même politique en anglais est PRIVACY.md à la
racine. Les autres langues de l'application sont dans un dossier au code de la
langue.

## Contact

Il n'y a pas de compte BabiBo à supprimer, parce que nous n'en détenons pas.
Supprimer l'application supprime le fichier local. Pour des données qu'un
destinataire a déjà, suivez le chemin indiqué dans la section de ce
destinataire.

Questions : <bububaba.support@lephuongtrung.id.vn>
