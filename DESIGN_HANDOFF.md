# Handoff: Senior Lane — strona zapisowa (lead-gen landing page)

> Język interfejsu: **polski (PL)**. Wersję EN przygotować osobno — cała treść poniżej jest finalna i nie należy jej zastępować placeholderami.

## Overview
Jednoekranowa strona docelowa (landing page) dla programu **Senior Lane · Konsorcjum Bonam Curam**. Jedyny cel: **zebranie zapisów (leadów)** od dorosłych dzieci seniorów i samych seniorów — kontakt + region + orientacyjny zakres potrzeb.

Model usługi (kontekst, nie do umieszczania dosłownie): zbieramy grupę zainteresowanych seniorów w regionie, wynajmujemy budynek blisko tej grupy, tworzymy kameralne mieszkania z opieką — stały czynsz od miejsca + usługi à la carte. Działalność **not-for-profit** (zysk → cele statutowe).

## About the Design Files
Plik w tym pakiecie (`Senior Lane.dc.html`) to **referencja projektowa stworzona w HTML** — prototyp pokazujący docelowy wygląd i zachowanie, **nie** kod produkcyjny do skopiowania 1:1. Plik jest „Design Component" (autorski format streamujący, oparty o `support.js` i style inline) — **nie przenoś go żywcem**.

Zadanie: **odtworzyć ten projekt w docelowym środowisku** (najpewniej React/Next.js + standardowy CSS / Tailwind / styled-components — wybierz zgodnie z konwencjami repo; jeśli repo nie istnieje, zaproponuj framework). Formularz jest poglądowy (pokazuje potwierdzenie) — podłącz do backendu lub usługi formularzy.

## Fidelity
**High-fidelity (hifi).** Finalne kolory, typografia, odstępy, treść i interakcje. Odtwórz UI pixel-perfect, używając bibliotek i wzorców istniejących w repo.

---

## Design Tokens

### Kolory
| Rola | Hex |
|---|---|
| Granat (kotwica, nagłówki, sekcja „Co dostajesz", stopka) | `#162640` |
| Granat jaśniejszy (panele na granacie) | `#1f3556` |
| Granat ciemny (tło stopki) | `#101d33` |
| Złoto (akcent, CTA, ścieżka, eyebrow) | `#b9942f` |
| Złoto hover (CTA) | `#a8852a` |
| Złoto miękkie (akcenty na granacie, numery kroków) | `#cdab52` |
| Krem (tło główne) | `#f6f1e7` |
| Krem cieplejszy (sekcje „Dlaczego" i „FAQ") | `#fbf7ee` |
| Papier (karty, formularz) | `#fcfaf4` / karty `#fffdf8` |
| Atrament (tekst główny) | `#2c3447` |
| Atrament — lead/akapity wzmocnione | `#3c4658` |
| Atrament miękki (tekst drugorzędny) | `#56607a` |
| Szałwia (znaczniki „w cenie", dot zaufania) | `#6f8064` (jasny wariant `#9fb18f`) |
| Linia (obramowania, dzielniki) | `#e3dccb` / `#e8e0cd` / `#ece4d1` |
| Tekst na granacie | `#eef1f6` / wtórny `#b3bccd` / `#9aa6bd` |
| Błąd walidacji | `#b4402f` |

### Typografia
- **Display / nagłówki:** `Fraunces` (serif), wagi 400–600; kursywa do akcentu (słowa „blisko domu" w H1 — kolor złoto, italic).
- **Body / UI:** `Source Sans 3`, wagi 400–700.
- Google Fonts: `Fraunces:ital,opsz,wght@0,9..144,400;0,9..144,500;0,9..144,600;1,9..144,400;1,9..144,500` + `Source+Sans+3:wght@400;500;600;700`.
- **Bazowy stopień pisma: 18px** (celowo większy — starszy odbiorca), line-height ~1.62.
- H1 hero: `clamp(2.6rem, 7vw, 5rem)`, weight 400, line-height 1.04, letter-spacing -.015em.
- H2 sekcji: `clamp(1.9rem, 4vw, 2.8rem)`, weight 500, line-height 1.1, letter-spacing -.01em.
- Eyebrow (nadtytuł): wersaliki, `letter-spacing .18em`, `font-size .78–.82rem`, weight 700, kolor złoto (`#b9942f`) — na granacie złoto miękkie (`#cdab52`).
- Lead: `clamp(1.1rem, 2vw, 1.32rem)`.

### Odstępy / promienie / cienie
- Padding sekcji: `clamp(64px,9vw,116px) 24px` (pionowo zmienny, poziomo 24px); szersze sekcje `clamp(64px,9vw,120px)`.
- Maksymalna szerokość kontenera treści: `1180px` (sekcje wąskie: 1100 / 1080 / 820 / 780).
- Promienie: karty `16px`, większe panele/formularz `18–20px`, pigułki/CTA/chipsy `999px`, pola input `10px`.
- Cienie: karty `0 1px 2px rgba(22,38,64,.04)`; uniesione `0 8px 28px rgba(22,38,64,.14)`; CTA `0 10px 24px rgba(185,148,47,.3)`; formularz `0 24px 60px rgba(0,0,0,.28)`.
- Akcent CTA / pasy sekcji: złota linia `3px solid #b9942f`.

---

## Screens / Views
Strona jednoekranowa, sekcje w kolejności. Sticky header nad wszystkim.

### 1. Header (sticky)
- Layout: `max-width:1180px`, flex space-between, `padding:12px 24px`, tło `rgba(246,241,231,.85)` + `backdrop-filter:blur(12px)`, dolna linia `1px solid #e3dccb`, `z-index:50`.
- Lewa: **logo** (`assets/logo-konsorcjum.png`, 50×50) + dwuwierszowy lockup — „**Senior Lane**" (Fraunces 1.3rem, granat) nad „KONSORCJUM BONAM CURAM" (Source Sans 3, .68rem, wersaliki, letter-spacing .13em, `#56607a`).
- Środek: **nav** (`Dlaczego` `#dlaczego`, `Jak to działa` `#jak`, `Oferta` `#oferta`, `FAQ` `#faq`) — weight 600, `#3c4658`, hover → złoto, `white-space:nowrap`. **Ukryte < 768px.**
- Prawa: CTA „Zapisz się" → `#zapis` (pigułka złota).

### 2. Hero (`#top`)
- Sekcja `min-height:clamp(600px,84vh,820px)`, flex column wyśrodkowane pionowo, `text-align:left`.
- Tło: szkic seniorów (`assets/hero-seniors.png`) — `background-position:right bottom`, `background-size:auto min(620px,92%)`, `opacity:.5`, `mix-blend-mode:multiply`; **odsłonięta prawa strona sceny**.
- Nakładki dla czytelności tekstu: gradient poziomy (krem 0% → przezroczysty ~68% → lekki krem 100%) + delikatny gradient pionowy góra/dół.
- Treść (lewa kolumna, `z-index:2`, w kontenerze 1180):
  - Eyebrow: „Lokale z opieką w najbliższej okolicy"
  - H1: „Opieka *blisko domu*" — słowa „blisko domu" italic, złoto. `max-width:640px`.
  - Lead (`#3c4658`, `max-width:540px`): „Zbieramy grupę seniorów w Twojej okolicy, znajdujemy budynek niedaleko i tworzymy w nim kameralne mieszkania z opieką. Twój bliski zostaje tam, gdzie ma rodzinę i swoje miejsca."
  - Plakietka zaufania (pigułka, kropka szałwia): „Prowadzimy działalność not-for-profit"
  - CTA: „Zapisz się — bez zobowiązań" (złoty, `#zapis`) + „Zobacz, jak to działa" (obrys, `#jak`)
  - Mikrotekst: „Zapis jest bezpłatny i do niczego nie zobowiązuje."

### 3. Dlaczego Senior Lane (`#dlaczego`, tło `#fbf7ee`)
- Intro **dwukolumnowe** (grid auto-fit minmax(300px,1fr), align center): lewa = eyebrow „Dlaczego Senior Lane" + H2 „**Opieka w Twojej okolicy**" + lead „Nie wybieramy najbliższego wolnego miejsca w przypadkowym mieście. Najpierw słuchamy rodzin, a potem budujemy ofertę tam, gdzie te rodziny są."; prawa = zdjęcie `assets/life-walk.png` (rounded 18px, `object-position:center 18%`, wys. `clamp(260px,34vh,380px)`).
- Siatka 6 kart (grid auto-fit minmax(290px,1fr), gap 22px). Karta: `#fffdf8`, border `1px #e8e0cd`, radius 16, padding 30, krótka kreska-akcent 34×3px (naprzemiennie złoto/szałwia), H3 Fraunces 1.32rem, akapit `#56607a`.
  1. **Blisko domu** — „Lokalizację otwieramy tam, gdzie mieszka grupa zainteresowanych rodzin. Senior zostaje w swoim regionie — blisko bliskich i znajomych miejsc."
  2. **Działalność not-for-profit** — „Senior Lane prowadzimy w formule not-for-profit. Wypracowany zysk przeznaczamy na cele statutowe Fundacji DivideYou."
  3. **Niezależność, nie zamknięcie** — „To mieszkania z usługami opiekuńczymi, a nie zamknięta placówka. Senior zachowuje samodzielność i dokupuje wsparcie wtedy, gdy go potrzebuje."
  4. **Bezpieczeństwo zawsze w cenie** — „Całodobowa obecność personelu i system przywoławczy są w stałym czynszu. To podstawa, a nie usługa dodatkowa."
  5. **Zero ryzyka na starcie** — „Zapis nic nie kosztuje. Kaucję rezerwacyjną zwracamy w całości, jeśli lokalizacja w Twojej okolicy ostatecznie nie ruszy."
  6. **Ludzie z tego samego regionu** — „Mieszkańcy pochodzą z jednej okolicy — łatwiej o wspólny język, odwiedziny rodziny i poczucie wspólnoty."

### 4. Jak to działa (`#jak`, tło `#f6f1e7`) — sekcja sygnaturowa
- Intro wyśrodkowane: eyebrow „Jak to działa", H2 „Sześć kroków do miejsca blisko domu", lead „Idziemy odwrotnie niż klasyczne domy opieki: najpierw zbieramy ludzi, dopiero potem dobieramy budynek pod konkretną grupę."
- **Złota „ścieżka" (lane)**: SVG z wijącą się złotą linią (stroke `#b9942f`, width 3) biegnącą pionowo środkiem między 6 numerowanymi krokami. **Rysuje się przy przewijaniu** (animacja `stroke-dashoffset` zależna od pozycji sekcji w viewport). To jedyny „odważny" akcent strony.
  - Implementacja referencyjna: ścieżka generowana w JS na podstawie wysokości kontenera kroków (6 segmentów, naprzemienne krzywe Béziera, amplituda ~22px), `strokeDasharray = pathLength`, `strokeDashoffset` interpolowany od `len`→`0` wraz z postępem scrolla. Patrz klasa logiki w pliku (`buildPath` / `updateLane`).
  - **Desktop:** grid 3-kolumnowy `1fr 88px 1fr` — karty naprzemiennie lewo/prawo, okrągłe odznaki numerów (54px) w kolumnie środkowej na linii. **< 768px:** kolaps do `56px 1fr`, SVG ukryty, w zamian prosta pionowa złota linia (`[data-how-line]`), karty po prawej.
  - Odznaki: granat `#162640` + cyfra złoto `#cdab52`, border `3px #f6f1e7`; krok 6 wyróżniony — tło złoto, cyfra biała.
- 6 kroków (numeracja to realna sekwencja):
  1. **Zapisujesz się — bez zobowiązań** — „Zostawiasz kontakt i wskazujesz swój region. To wszystko, czego potrzebujemy na start."
  2. **Zbieramy grupę w Twojej okolicy** — „Łączymy rodziny z tego samego regionu. Gdy zbierze się wystarczająca grupa — uruchamiamy lokalizację."
  3. **Znajdujemy budynek blisko Was** — „Wybieramy i wynajmujemy odpowiedni obiekt w okolicy grupy, żeby dojazd rodziny był krótki."
  4. **Rezerwujesz miejsce** — „Podpisujesz list intencyjny i wpłacasz zwrotną kaucję. Jeśli lokalizacja nie ruszy — kaucja wraca w całości."
  5. **Urządzamy pokój i usługi** — „Przygotowujemy pokój oraz pakiet usług pod konkretne potrzeby Twojego bliskiego."
  6. **Wprowadzenie** — „Senior zamieszkuje blisko domu, z opieką i bezpieczeństwem na wyciągnięcie ręki."

### 5. Co dostajesz / Oferta (`#oferta`, tło granat `#162640`)
- Intro **dwukolumnowe**: lewa = zdjęcie `assets/life-tablet.png` (rounded 18px); prawa = eyebrow „Co dostajesz" (złoto miękkie) + H2 (biały) „Przejrzysty podział: stały czynsz i usługi na życzenie" + lead (`#b3bccd`) „Bezpieczeństwo i dach nad głową są zawsze w cenie. Resztę dobierasz wtedy, gdy jest potrzebna — i tyle, ile potrzeba."
- Dwa panele (grid auto-fit minmax(300px,1fr), gap 24): tło `#1f3556`, border `1px #2c456b`, radius 18.
  - **W stałym czynszu** — znacznik „w cenie" (pigułka szałwia), znaki `✓` szałwia:
    - Umeblowany pokój 1- lub 2-osobowy, media i ogrzewanie
    - Całodobowa obecność personelu i system przywoławczy
    - Dostęp do części wspólnych: jadalnia, salon, ogród
    - Podstawowy nadzór i wsparcie organizacyjne
    - Sprzątanie przestrzeni wspólnych
  - **Dokupujesz wg potrzeb** — znacznik „à la carte" (pigułka złota), znaki `+` złoto:
    - Posiłki — pełny pakiet, częściowy lub pojedyncze
    - Sprzątanie pokoju w wybranej częstotliwości
    - Pranie i prasowanie
    - Pomoc osobista — higiena, ubieranie
    - Rehabilitacja i fizjoterapia
    - Zakupy, dostawa leków, asysta na wizyty lekarskie
    - Transport
- Nota pod panelami (`#9aa6bd`): „Konkretne stawki podajemy dla danej lokalizacji — zależą od budynku i regionu. Pokazujemy je w całości, bez ukrytych kosztów."

### 6. Działalność not-for-profit + kto za tym stoi (tło `#f6f1e7`)
- Grid dwukolumnowy (auto-fit minmax(320px,1fr), gap 44, align start).
- Lewa: zdjęcie `assets/life-bench-summer.png` (rounded 16) → eyebrow „Działalność not-for-profit" → **cytat** (Fraunces, italic, lewa krawędź `4px #b9942f`, `clamp(1.4rem,2.8vw,2rem)`): „Senior Lane to działalność not-for-profit. Wypracowany zysk w całości przeznaczamy na cele statutowe."
- Prawa: karta `#fffdf8` „**Kto za tym stoi**" + „Program prowadzi Konsorcjum Senior Lane Bonam Curam w formule not-for-profit." Dwa wiersze ról (etykieta-badge + nazwa + opis), rozdzielone górną linią:
  - **Lider** (badge granat) — **Fundacja DivideYou** — „Organizacja prowadząca program"
  - **Operator** (badge złoto) — **Konsorcjum Bonam Curam** — „Operator opieki senioralnej"

### 7. FAQ (`#faq`, tło `#fbf7ee`)
- `max-width:820px`, H2 wyśrodkowany „To, o co rodziny pytają najpierw".
- Akordeon w karcie `#fffdf8`, radius 16. Każdy item: przycisk pełnej szerokości (pytanie weight 700 + ikona `+`), panel `max-height` animowany. **Single-open** (otwarcie zamyka pozostałe). Ikona obraca się `rotate(45deg)` (+ → ×).
- Pytania/odpowiedzi:
  1. **Co, jeśli w mojej okolicy nie uzbiera się grupa?** — „Nie uruchamiamy wtedy lokalizacji, a wpłaconą kaucję rezerwacyjną zwracamy w całości. Sam zapis nie zobowiązuje Cię do niczego i jest bezpłatny."
  2. **Czy to zamknięta placówka albo dom opieki?** — „Nie. To mieszkania z usługami opiekuńczymi. Senior zachowuje samodzielność, a wsparcie dokupuje wtedy i w takim zakresie, w jakim jest potrzebne."
  3. **Czy mój bliski będzie bezpieczny?** — „Tak. Całodobowa obecność personelu oraz system przywoławczy są zawsze w cenie podstawowej — nie są usługą dodatkową, którą trzeba dokupować."
  4. **Ile to kosztuje?** — „Płaci się stały czynsz od miejsca oraz za usługi, z których faktycznie się korzysta. Konkretne stawki podajemy dla danej lokalizacji, bo zależą od budynku i regionu."
  5. **Czy muszę od razu płacić?** — „Nie. Zapis jest bezpłatny i niezobowiązujący. Zwrotną kaucję wpłaca się dopiero przy rezerwacji konkretnego miejsca w uruchamianej lokalizacji."
  6. **Kto prowadzi program?** — „Konsorcjum Senior Lane Bonam Curam: Fundacja DivideYou jako lider oraz Bonam Curam PSA jako operator opieki. Prowadzimy działalność not-for-profit."

### 8. Formularz zapisu (`#zapis`, tło granat) — punkt konwersji
- Karta `#fcfaf4`, `max-width:780px`, radius 20, mocny cień. Nagłówek (biały, wyśrodkowany) „Zapisz się — bez zobowiązań" + lead (`#b3bccd`) „Zostaw kontakt i wskaż swój region. Odezwiemy się, gdy w Twojej okolicy uzbieramy grupę — albo wcześniej, jeśli będziemy mieli pytania."
- **Dane kontaktowe:** Imię i nazwisko *(wymagane)* · Telefon · E-mail · Miasto / region *(wymagane)*. Segment „Zgłaszam dla": rodzica / bliskiej osoby · siebie · jeszcze nie wiem.
- **Zakres oczekiwanych usług** (podpis: „Orientacyjnie — pomaga nam dobrać budynek i ofertę. Nic nie jest wiążące."):
  - Typ pokoju: 1-osobowy · 2-osobowy · bez preferencji
  - Samodzielność: samodzielny/-a · potrzebuje częściowego wsparcia · potrzebuje stałej pomocy · jeszcze nie wiem
  - Zakres posiłków: pełny — 3 posiłki dziennie · częściowy · bez posiłków · jeszcze nie wiem
  - Usługi dodatkowe (chipsy, **wielokrotny wybór**): Sprzątanie pokoju · Pranie i prasowanie · Pomoc osobista · Rehabilitacja · Zakupy i leki · Transport
  - Uwagi (opcjonalne, textarea)
- **Zgoda (wymagana):** „Wyrażam zgodę na kontakt w sprawie programu Senior Lane. Administratorem danych jest Fundacja DivideYou; dane wykorzystamy wyłącznie w tym celu."
- **Przycisk:** „Zapisz się — bez zobowiązań".
- **Po wysłaniu** (zamiana formularza na panel sukcesu): kółko `✓` szałwia, „**Dziękujemy za zgłoszenie**", „Zapisaliśmy Twój region. Odezwiemy się, gdy w Twojej okolicy zbierze się grupa — lub wcześniej, jeśli będziemy mieli pytania."

### 9. Stopka (tło `#101d33`)
- Lewa: logo-lockup (Senior Lane + kropka złota + KONSORCJUM BONAM CURAM) + „Program prowadzony w formule not-for-profit przez Fundację DivideYou (lider) i Bonam Curam PSA (operator opieki)."
- Prawa: „Kontakt" + `p.nykiel@divideyou.com` (link, złoto).
- Dół (małe, `#71809a`): „© 2026 Konsorcjum Senior Lane Bonam Curam. Mieszkania z usługami opiekuńczymi. Treść informacyjna — nie stanowi oferty w rozumieniu Kodeksu cywilnego."

---

## Interactions & Behavior
- **Reveal przy scrollu:** elementy z `[data-reveal]` pojawiają się (fade + translateY 24px→0) gdy wchodzą w kadr (IntersectionObserver odpala jednorazową animację `@keyframes slreveal .8s`). **Treść jest domyślnie widoczna** — animacja to progressive enhancement (brak JS/IO ⇒ wszystko widać; ważne dla SSR/eksportu/PDF). Nie chowaj treści za JS.
- **Lane (Jak to działa):** rysowanie konturu sterowane scrollem (zob. wyżej). Przy `prefers-reduced-motion` — pokazać od razu narysowaną.
- **Chipsy usług:** toggle, stan zaznaczony = granat tło / biały tekst (`aria-pressed`).
- **Segmenty (radio):** pojedynczy wybór w grupie, zaznaczony = granat.
- **FAQ:** akordeon single-open, animacja `max-height`, ikona `+`→`×` (rotate 45°).
- **Walidacja przed wysłaniem:** wymagane Imię, Miasto, Zgoda — przy braku: czerwony komunikat pod polem + czerwone obramowanie. Po sukcesie: ukryj formularz, pokaż panel potwierdzenia (bez przeładowania).
- **Nawigacja kotwicowa:** `scroll-behavior:smooth` + `scroll-margin-top:78–80px` na sekcjach (kompensacja sticky headera).
- **Hover:** CTA złoto → `#a8852a`; linki nav → złoto; obrys CTA → border granat.
- **A11y:** widoczny focus klawiatury, kontrast, bazowo 18px; respektować `prefers-reduced-motion`.

## State Management
Stan minimalny, możliwy w pełni lokalnie w komponencie:
- `faqOpen` — indeks otwartego pytania (lub null), single-open.
- `selectedChips` — zbiór zaznaczonych usług dodatkowych.
- wybory segmentów: `forWho`, `roomType`, `independence`, `meals`.
- pola formularza: `name`, `phone`, `email`, `city`, `notes`, `consent`.
- `submitted` — przełącza widok na panel potwierdzenia.
- **Data fetching:** brak na froncie poza wysyłką formularza — całe zgłoszenie (kontakt + zakres usług) wyślij jako **jedno** żądanie do backendu/usługi formularzy. Administrator danych: **Fundacja DivideYou** (RODO).

## Responsive behavior
- Pełna responsywność do mobile (jedna kolumna, większe pola dotykowe, hit-targety ≥44px).
- Nav chowane < 768px (rozważ menu hamburger w implementacji produkcyjnej — w prototypie pominięte).
- Siatki kart/paneli/kolumn używają `repeat(auto-fit, minmax(...))` — zwijają się same.
- Sekcja „Jak to działa" przełącza się z układu 3-kolumnowego (lane środkiem) na lewy pasek linii < 768px.

## Assets
W folderze `assets/`:
- `logo-konsorcjum.png` — logo „Konsorcjum na rzecz Seniora · Bonam Curam" (złote serce w okręgu, PNG z przezroczystością, 500×500). Dostarczone przez klienta.
- `hero-seniors.png` — szkic (line-art) spacerujących seniorów; tło hero. Dostarczone przez klienta.
- `life-walk.png`, `life-tablet.png`, `life-bench-summer.png`, `life-bench-autumn.png` — ogólne, lifestyle'owe zdjęcia seniorów (~1132×754) używane jako contained insety w sekcjach. **Nie pokazują konkretnej placówki** (świadomie — lokalizacje będą różne). `life-bench-autumn.png` aktualnie nieużywane w layoucie — zapas. Dostarczone przez klienta; w produkcji podmień na docelowe licencjonowane materiały.

## Czego unikać (krytyczne dla treści)
- **Nie** sugerować braku zysku: zakaz „non-profit", „nie zarabiamy", „opłaty pokrywają tylko koszty", „bez marży". Poprawny przekaz: *działalność not-for-profit; zysk → cele statutowe Fundacji DivideYou*. **Nie** definiować pojęcia „not-for-profit".
- **Nie** pokazywać zdjęć konkretnej placówki ani konkretnych kwot (zależą od lokalizacji).
- Ton: ciepły, godny, ludzki — nie kliniczny, nie korporacyjny.
- Disclaimer „nie stanowi oferty w rozumieniu KC" zostaje w stopce.

## Files
- `Senior Lane.dc.html` — referencyjny prototyp (Design Component; style inline, logika w klasie `Component`). Otwórz w przeglądarce, aby zobaczyć docelowy wygląd i zachowanie. Logika reveal/lane/FAQ/chipsy/formularz znajduje się w bloku klasy logiki na końcu pliku.
- `assets/` — zasoby wymienione wyżej.
