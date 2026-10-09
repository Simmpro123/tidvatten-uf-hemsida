# Tidvatten UF – hemsida

Hemsidan för Tidvatten UF (UF-företag, Ekonomiprogrammet åk 3). En enda statisk sida: `index.html` + bilder i `assets/`.

- GitHub-repo: `tidvatten-uf-hemsida`, publiceras med GitHub Pages från `main` (roten).
- Git: `C:\Program Files\Git\cmd\git.exe` · GitHub CLI: `C:\Program Files\GitHub CLI\gh.exe` (finns inte i PATH).

## Arbetsflöde
Efter varje ändring av sidan: commit med ett kort meddelande på svenska som beskriver ändringen, och `git push` till `origin main`. Då uppdateras den publicerade sidan automatiskt inom någon minut.

Lägg aldrig in hemliga nycklar (t.ex. Stripe `sk_...`) i koden – repot är offentligt. Publika nycklar (Stripe `pk_...`, EmailJS public key) är okej.
