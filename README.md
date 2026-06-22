# Senior Lane — strona zapisowa

Landing page programu **Senior Lane · Konsorcjum Bonam Curam** — mieszkania z usługami
opiekuńczymi blisko domu. Jedyny cel strony: zbieranie zapisów (leadów).

Działalność prowadzona w formule **not-for-profit** przez Fundację DivideYou (lider)
i Bonam Curam PSA (operator opieki).

## Stos technologiczny

Statyczna strona — czysty **HTML + CSS + vanilla JS**, bez kroku budowania.
Odtworzona 1:1 z projektu (`DESIGN_HANDOFF.md`), z którego pochodzą wszystkie
tokeny projektowe, treść i interakcje.

```
index.html              # cała strona (sekcje, style inline, logika w <script>)
assets/                 # logo, tło hero, zdjęcia lifestyle
.github/workflows/      # automatyczny deploy na GitHub Pages
DESIGN_HANDOFF.md        # oryginalny brief projektowy (referencja)
```

## Lokalne uruchomienie

Wystarczy otworzyć `index.html` w przeglądarce, albo:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Publikacja

Każdy push na gałąź `main` automatycznie publikuje stronę na **GitHub Pages**
(workflow `.github/workflows/deploy-pages.yml`). Adres pojawia się w zakładce
**Settings → Pages** oraz w podsumowaniu uruchomienia w **Actions**.

## Uwagi

- Formularz zapisu jest poglądowy — po walidacji pokazuje panel potwierdzenia.
  Aby zbierać zgłoszenia, podłącz go do backendu lub usługi formularzy
  (administrator danych: Fundacja DivideYou).
- Zdjęcia lifestyle są materiałem zastępczym — w produkcji podmień na docelowe,
  licencjonowane materiały.
