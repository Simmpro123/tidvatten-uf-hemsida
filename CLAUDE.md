# Tidvatten UF – hemsida

Hemsidan för Tidvatten UF (UF-företag, Ekonomiprogrammet åk 3). En enda statisk sida: `index.html` + bilder i `assets/`.

- GitHub-repo: https://github.com/Simmpro123/tidvatten-uf-hemsida (konto Simmpro123), publiceras med GitHub Pages från `main` (roten).
- **Huvudsida: https://tidvattenuf.se** (köpt hos STRATO 2026-10-14) = GitHub Pages med egen domän (filen `CNAME`). DNS hos STRATO: A-poster `@` → 185.199.108.153 / .109.153 / .110.153 / .111.153, CNAME `www` → `simmpro123.github.io`.
- Gamla adressen https://tidvatten.netlify.app – Netlify-sajt `tidvatten`, id `3caa8058-9d69-4f20-9bf8-15653a281116`. Gratisplanen har 300 krediter/mån och varje produktionsdeploy kostar 15 (max ~20/mån) – i oktober 2026 tog de slut. Deploya inte dit vid varje ändring längre.
- Netlify CLI: kör med `$env:PATH = "C:\Program Files\nodejs;$env:APPDATA\npm;$env:PATH"` först. Inloggad på användarens konto.
- Git: `C:\Program Files\Git\cmd\git.exe` · GitHub CLI: `C:\Program Files\GitHub CLI\gh.exe` (finns inte i PATH).

## 3D-boken (överst till höger)
- Omslagen är riktiga foton av den tryckta boken: `assets/book-front.jpg` och `assets/book-back.jpg` (800×1046, perspektivkorrigerade från mobilfoton så att de är platta, proportion 1 : 1.3077 = samma som `--h`; nuvarande foton "Nya bilder (framsida/baksida).jpg" i Downloads\UF bilder, 2026-10-15). Förminskade versioner: `book-front-340/510.jpg` i köpkortet (`.book-card-art`) och `book-back-500/750.jpg` under Om boken (`.page-card`).
- Boken är klammerhäftad, därför är ryggen tunn (`--d` = 3,5 % av bredden) och `.face.spine` är bara en färgtoning i omslagets blå.
- Bokfakta i köpkortet (`.book-details`): författare, illustratör, utgåva, ISBN 978-91-535-1773-3, språk, vikt 134 g, förlag – i den ordning Nathalie skrev dem.

## Betalning
- Swish: nummer i `SWISH_NUMBER`. Beställningsmejl via EmailJS (mallar i användarens EmailJS-konto).
- Kort: Stripe **live**-konto `acct_1UDMsN6QRMIxLUuS` ("Tidvatten"). Fyra betalningslänkar i `STRIPE_LINKS` (1–4 böcker, frakt-produkt 49 kr ingår). Bokpris `price_1UQiqj6QRMIxLUuSD4jMdLGz` (179 kr, sedan 2026-10-15), fraktpris `price_1UOaRb6QRMIxLUuS5R8lnc3P` (49 kr). Länkarna tar 228/407/586/765 kr. De gamla 159 kr-länkarna (`plink_1UOaRl…`, `…RwD…`, `…S66…`, `…SGd…`, 208–685 kr) är fortfarande aktiva eftersom tidvatten.netlify.app använder dem – avaktivera dem när Netlify-adressen pekar om till tidvattenuf.se.
- Ändras priset måste nya Stripe-länkar skapas (Stripe CLI: `%LOCALAPPDATA%\Microsoft\WinGet\Packages\Stripe.StripeCli_Microsoft.Winget.Source_8wekyb3d8bbwe\stripe.exe`, inloggad, använd `--live`) och `BOOK_PRICE`/`SHIPPING` uppdateras.
- `client_reference_id` får bara vara A–Z/0–9, därför görs å/ä/ö om i referensen.

## Arbetsflöde
Efter varje ändring av sidan:
1. Commit med ett kort meddelande på svenska och `git push` till `origin main`. Det publicerar sidan på tidvattenuf.se automatiskt (GitHub Pages, ca 1 min). Verifiera att live-`index.html` matchar lokalt.
2. Netlify (gamla adressen) uppdateras inte längre vid varje ändring. Planen när krediterna fylls på i november: en sista deploy med `_redirects` (`/* https://tidvattenuf.se/:splat 301!`) så att gamla länkar skickas till nya domänen. Deploy-kommando: kopiera **bara** `index.html` + `assets/` (+ ev. `_redirects`) till en tom mapp och kör `netlify deploy --prod --dir <mappen> --site 3caa8058-9d69-4f20-9bf8-15653a281116`.

Snäckan i loggan (`assets/logo-mark.png`) är hämtad från tidvatten.netlify.app – byt inte ut den.

Lägg aldrig in hemliga nycklar (t.ex. Stripe `sk_...`) i koden – repot är offentligt. Publika nycklar (Stripe `pk_...`, EmailJS public key) är okej.
