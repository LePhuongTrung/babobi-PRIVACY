# BabiBo

Personal finance that stays on your iPhone.

Developed by Le Phuong Trung. The iPhone app is for iPhone only. It is not an iPad app.

BabiBo keeps a budget, a net worth, and the transactions behind them in one ledger file on the phone. There is no BabiBo account to create, no BabiBo server, and no advertising.

## What it does

- A year of net worth: current accounts, savings, holdings, and loans.
- A monthly plan. You assign what comes in. The app follows what goes out and shows what is left.
- Every transaction filed by hand, or by rules that remember how you filed it before.
- Spending by category, by month, and by day, including subscriptions it finds on its own.
- A home-screen widget that shows how much is left.
- Face ID when you open the app, if you turn it on.
- A demo with invented accounts. Erase it from Settings.

Bank sync is optional. It uses your own Enable Banking application (PSD2). You can also enter rows by hand, or import the CSV and OFX files your bank already gives you.

## Your data

The ledger stays in a file on the phone. BabiBo does not run a service that receives it.

Some features do send a narrow request: to your bank if you connect one, to Google Gemini if you save a key, to Yahoo Finance for a price or a ticker search, to a merchant's site for its logo, and to a server of your own if you point the app at one.

What leaves, who receives it, and how to stop it is in the [privacy policy](PRIVACY.md).

## The code

BabiBo is free software under the AGPL-3.0.

https://github.com/LePhuongTrung/BabiBo-swift

## Contact

https://github.com/LePhuongTrung/babobi-PRIVACY/issues
