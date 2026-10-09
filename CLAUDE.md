# Tidvatten UF – hemsida

Hemsidan för Tidvatten UF (UF-företag, Ekonomiprogrammet åk 3). En enda statisk sida: `index.html` + bilder i `assets/`.

- GitHub-repo: https://github.com/Simmpro123/tidvatten-uf-hemsida (konto Simmpro123), publiceras med GitHub Pages från `main` (roten).
- **Huvudsida (den som delas): https://tidvatten.netlify.app** – Netlify-sajt `tidvatten`, id `3caa8058-9d69-4f20-9bf8-15653a281116`.
- Kopia på GitHub Pages: https://simmpro123.github.io/tidvatten-uf-hemsida/
- Netlify CLI: kör med `$env:PATH = "C:\Program Files\nodejs;$env:APPDATA\npm;$env:PATH"` först. Inloggad på användarens konto.
- Git: `C:\Program Files\Git\cmd\git.exe` · GitHub CLI: `C:\Program Files\GitHub CLI\gh.exe` (finns inte i PATH).

## Betalning
- Swish: nummer i `SWISH_NUMBER`. Beställningsmejl via EmailJS (mallar i användarens EmailJS-konto).
- Kort: Stripe **live**-konto `acct_1UDMsN6QRMIxLUuS` ("Tidvatten"). Fyra betalningslänkar i `STRIPE_LINKS` (1–4 böcker, frakt-produkt 49 kr ingår). Bokpris `price_1UMXPU6QRMIxLUuSdEEMOgL9` (159 kr), fraktpris `price_1UOaRb6QRMIxLUuS5R8lnc3P`.
- Ändras priset måste nya Stripe-länkar skapas (Stripe CLI: `%LOCALAPPDATA%\Microsoft\WinGet\Packages\Stripe.StripeCli_Microsoft.Winget.Source_8wekyb3d8bbwe\stripe.exe`, inloggad, använd `--live`) och `BOOK_PRICE`/`SHIPPING` uppdateras.
- `client_reference_id` får bara vara A–Z/0–9, därför görs å/ä/ö om i referensen.

## Arbetsflöde
Efter varje ändring av sidan:
1. Commit med ett kort meddelande på svenska och `git push` till `origin main` (uppdaterar GitHub Pages automatiskt).
2. Deploya till Netlify: kopiera **bara** `index.html` + `assets/` till en tom mapp i scratchpad (inte CLAUDE.md eller .git) och kör `netlify deploy --prod --dir <mappen> --site 3caa8058-9d69-4f20-9bf8-15653a281116 --message "<samma som commit>"`.

Snäckan i loggan (`assets/logo-mark.png`) är hämtad från tidvatten.netlify.app – byt inte ut den.

Lägg aldrig in hemliga nycklar (t.ex. Stripe `sk_...`) i koden – repot är offentligt. Publika nycklar (Stripe `pk_...`, EmailJS public key) är okej.
