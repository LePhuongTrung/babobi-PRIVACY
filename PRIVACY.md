# Privacy Policy — BabiBo

BabiBo is developed by Le Phuong Trung.

_Last updated: 18 November 2026_

BabiBo is a personal finance app for iPhone. It is not an iPad app. The people
who publish it do not run a service that receives your ledger. There is no
BabiBo account, no analytics, no crash reporting, no advertising identifier,
and no third-party SDK that phones home.

Some features do send data off the device, to a company you choose or to a site
the feature has to reach. This page says what leaves, how, why, who receives it
(including the AI provider), how long it is kept, and how you stop it or delete
it.

## What stays on the device

Everything the ledger knows — accounts, balances, transactions, categories,
budgets, holdings, receipt photos, and names already learned from a receipt —
is stored in one database file inside the app's own container on your device.

That file is included in your device backup. If you have iCloud Backup turned
on, an encrypted copy travels with the rest of your phone. That copy is between
you and Apple. We cannot read it.

You can export the file at any time from **Settings → Data**, and import it
into BabiBo on another device. A restored copy does not carry the bank
session: the signing key stays on the phone that created it, and you connect
the bank again on the new phone.

Deleting the app deletes this file. That includes a saved Gemini API key, the
product names already learned, saved prices, and cached logos.

We do not use any of this data for advertising or tracking, and we never
receive a copy of it.

## Your bank, through Enable Banking

Optional, on iPhone, Mac, and a server you host. Nothing is sent until you
register your own application with Enable Banking and connect a bank.

**What.** Balances, statements (the transactions), and the account identifiers
the bank returns, including an IBAN when the bank sends one.

**How.** The app asks Enable Banking, which asks your bank, and writes the
answer into the local file. The application id and the private key stay on
your device. On iPhone, once a bank is connected, the app asks iOS to wake it
in the morning — it aims for 07:15, and it skips the pull if a sync already
succeeded in the last six hours — and downloads the statements again. iOS may
ignore that time. The pull runs only while Background App Refresh is on for
BabiBo.

**Why.** To fill the ledger. If you allowed notifications, the phone also
posts one summary when new transactions arrived. That notification is created
on the device. It is not sent to us.

**Who.** Enable Banking and your bank. Not us. What they do with the data
follows their terms and the consent you give them when you register and when
you approve the bank.

**How long, and how to stop.** The copy in the app stays until you delete the
account. Deleting an account deletes its transactions and, when it is the last
account on that connection, deletes the connection, so the morning pull has
nothing left to ask. Enable Banking and the bank keep what their own terms
require. We cannot delete their copy. Revoke the consent in your bank, or in
the Enable Banking application you registered.

## Google Gemini

Optional, and iPhone only. No request is made until you save a key under
**Settings → Receipts**.

**What.** The abbreviated item names printed on a receipt, and the merchant's
name. Not the photo, not the amounts, not the dates, and not the rest of the
ledger. One further request can send category words already stored on the
phone — words such as "chicken", with no merchant, amount, or date — so they
can be filed into a fixed list of product families.

**How.** You create a key at [Google AI Studio](https://aistudio.google.com)
and save it in Settings. The app then calls Google's Gemini API
(`generativelanguage.googleapis.com`) with that key. A label that was answered
once is kept on the phone and is not sent again.

**Why.** To turn a till abbreviation into a product name and a category, which
are written back into the local file.

**Who.** Google, under the Gemini API terms that apply to the key you created.
We do not receive the text. Google is the AI provider for this feature.

**How long, and how to stop.** Google keeps what those terms say. We do not
set that period, and we have no copy on a server of ours. The reading stays in
the local database until you delete the app. **Settings → Receipts →
Retirer** deletes the key from the phone and stops further requests. The
button is labeled Retirer. It does not erase readings already stored on the
phone, and it does not erase what Google already received. Delete or rotate
the key in Google AI Studio as well if you want Google to stop accepting it.

## Yahoo Finance

**What.** A ticker symbol, such as `CW8.PA`. When you search for a security,
the text you typed. Not the quantity, not the value, and not the account name.

**How.**

- On iPhone, a refresh of the ledger asks Yahoo for a price for every holding
  that has a symbol. Saving a symbol asks immediately. The search field asks
  when you search. The app does not do this in the morning background pull.
- On Mac, and on a server you host, Yahoo is used only if you set the price
  provider to Yahoo. The default is off, and those builds then make no quote
  request.

The request goes to `query1.finance.yahoo.com`. There is no API key. The
connection also carries the network address and a user agent, as any HTTPS
request does. The app adds no name and no account id.

**Why.** To show a price, and, on iPhone, to find the listing that matches
what you typed.

**Who.** Yahoo. Not us.

**How long, and how to stop.** Prices are written into the local file and stay
until you delete the app. Yahoo keeps its own logs under its privacy policy.
We have no Yahoo account that could delete them. On iPhone, delete the holding
to stop further price requests for it, and do not search if you do not want
the text sent. On Mac and on your server, set the price provider back to
`none`.

## Merchant websites

iPhone only. On by default.

**What.** No field from the ledger is attached to the request. The app loads
`https://` plus the merchant's domain, then the icon that page names. The
request looks like a browser asking for that address: the address itself, the
phone's network address, and a browser user agent. Cookies are neither stored
nor sent.

**How.** While **Settings → Categories and merchants → Merchant logos** is
on, and a merchant has a known site or a site you typed. The image is
requested the first time it is needed.

**Why.** To draw that merchant's icon. Nothing else.

**Who.** That merchant's website, and whoever hosts it. Not a logo service,
and not us.

**How long, and how to stop.** The image sits in the app's cache until iOS
clears caches or you delete the app. A site that had no usable icon is not
asked again for seven days. The site's logs are its own; we cannot delete
them. Turn **Merchant logos** off to stop new requests.

## Your own server

Optional. If you point BabiBo at a server you run, the app reads and writes
the ledger there. That machine is yours. Remove the server address in Settings
to stop. Delete what the server stored on that machine.

## Face ID

If you turn on the app lock, BabiBo asks iOS to verify you. iOS answers yes or
no. Your biometrics never reach the app, and they are not sent to anyone.

## Children

BabiBo is not directed at children.

## Changes

Any change to this policy is committed to
<https://github.com/LePhuongTrung/babobi-PRIVACY>, where its history is public.

This page is English. The same policy in the app's other languages is in this
repository, one folder per language: vi, fr, nl, it, es, ca, de, pt, and tr.

## Contact

There is no BabiBo account to delete, because we do not hold one. Deleting the
app deletes the local file. For data a recipient already has, use the path in
that recipient's section above.

Questions: <babibo.support@lephuongtrung.id.vn>
