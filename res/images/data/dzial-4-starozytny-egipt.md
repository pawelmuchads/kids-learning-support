# Kapsuła Czasu – Dział 4: Starożytny Egipt

Specyfikacja pytań i odpowiedzi do dopisania na stronę `kapsula-czasu-historia.html`.
Źródło: podręcznik do historii, dział 4 „Starożytny Egipt”, s. 22–23 i 26–27. Strony 24–25 nie zostały dostarczone (patrz sekcja 7).

---

## 0. Instrukcja dla modelu, który dokończy stronę

### Kontekst
`kapsula-czasu-historia.html` to jednoplikowa strona (HTML + CSS + JS, bez bibliotek, tylko Google Fonts) z pytaniami do powtórki z historii dla ucznia szkoły podstawowej. Treść jest w tablicy `DZIALY` w skrypcie. Jest tam dział 1, a być może także działy 2, 3 i 6 (osobne pliki MD o tej samej strukturze).

### Zadanie
1. Dopisz do `DZIALY` nowy dział według sekcji 1–6 tego pliku. Działy w tablicy i w zakładkach ustaw według `nr` (1, 2, 3, 4, 6…).
2. **Jeśli strona obsługuje jeden dział** (skrypt wybiera `DZIALY.filter(...)[0]`, a zakładki nic nie robią), wprowadź najpierw zmiany z listy niżej. **Jeśli już obsługuje kilka działów**, dodaj tylko to, czego brakuje: typ `zrodlo` i neutralny komunikat wyniku w `kolejnosc` (punkty 5 i 6).
3. **Nie zmieniaj istniejących działów** ani wyglądu strony.

### Zasady merytoryczne (ważne)
- Treść pytań, odpowiedzi i ciekawostek została sprawdzona z podręcznikiem i ze źródłami wiedzy ogólnej. **Nie dopisuj nowych faktów, dat ani liczb** i nie „poprawiaj” treści.
- **Nie przepisuj na stronę tekstu źródłowego Herodota z s. 22** (polskie tłumaczenie jest chronione prawem autorskim). Pytanie P18 odsyła do podręcznika, a odpowiedź streszcza tekst własnymi słowami.
- Zwroty „Egipcjanie uważali”, „wierzyli” dotyczą wierzeń starożytnych Egipcjan. Zostaw je w tej formie.
- Polskie cudzysłowy „ ”, półpauza – w zakresach dat, formy neutralne płciowo.
- Nie odtwarzaj map, ilustracji ani postaci z podręcznika (prawa autorskie). Pytania o mapę i ilustracje odsyłają do stron podręcznika.

### Konwersja treści z tego pliku do pól JS
- `**tekst**` → `<b>tekst</b>`, `*tekst*` → `<i>tekst</i>`.
- Lista `-` → `<ul><li>…</li></ul>`, lista numerowana → `<ol><li>…</li></ol>`.
- Akapity → `<p>…</p>`.
- Linie „Źródło: …” są tylko do weryfikacji – **nie renderuj ich**.

### Zmiany w kodzie (jeśli jeszcze ich nie ma)
1. **Przełączanie działów.** Funkcja `render(dzId)` buduje `ALL`, `BY`, `TOTAL`, `#main`, `#chips` i stopkę dla wybranego działu i jest wywoływana po kliknięciu zakładki. Aktywny dział zapamiętaj w `location.hash` (np. `#d4`) i odtwórz go przy wczytaniu strony. Domyślnie otwiera się dział 1.
2. **Etykiety zakładek** z numerem z podręcznika: „Dział 4 Starożytny Egipt”.
3. **Postęp per dział.** Pasek, ranga, klepsydra, chipy i licznik dotyczą aktywnego działu. `uid` ma prefiks `dz.id` (np. `d4-5`). Zostaw klucz `localStorage` `kapsula-czasu-v1`.
4. **Rangi i komunikaty maskotki per dział:** opcjonalne pola `rangi` i `start` w obiekcie działu (wartości w sekcji 6). Toast końcowy: „🏆 Cały dział opanowany! Zostajesz: ” + nazwa najwyższej rangi.
5. **Typy w `TYPY`** (dodaj brakujące):
   - `pojecie: '📖 Wyjaśnij pojęcie'`, `obraz: '🖼️ Praca z ilustracją'`, `mapa: '🗺️ Praca z mapą'`, `zrodlo: '📜 Tekst źródłowy'` – renderują się jak zwykłe pytanie (`q`, opcjonalne `body`, `odp`, `extra`).
   - `sortuj: '🗂️ Przyporządkuj'` – w tym dziale nieużywany; jeśli go nie ma, nie musisz go dodawać.
6. **Typ `kolejnosc`:**
   - Opcjonalne pole `hint` (dla P21: „Klikaj wydarzenia od najdawniejszego do najpóźniejszego.”, dla P24: „Klikaj od szczytu piramidy w dół.”).
   - Placeholder `.oseq:empty::before` neutralny: „Klikaj po kolei, a pojawi się tutaj twoja kolejność”.
   - **Komunikat wyniku musi być neutralny.** Obecnie jest na sztywno „Daty na właściwym miejscu”, a w P24 elementami są grupy społeczne. Zmień go na „Na właściwym miejscu: x z n”.
7. Przy zmianie działu: wyłącz filtr „Tylko do powtórki”, przewiń na górę, przelicz pasek i maskotkę.
8. **Ściągawka:** sekcja 5. Oś czasu jak w dziale 1 (`.tl`), resztę jako karty `.rules`.

### Kryteria gotowości
- Brak błędów w konsoli; strona działa po otwarciu z dysku (`file://`).
- Wszystkie zakładki działają, postęp każdego działu liczy się osobno i przetrwa odświeżenie strony.
- Dział 4 ma 27 pytań w 8 kategoriach, numerowane od 1. Pasek chipów przewija się poziomo, jeśli się nie mieści.
- Dopasowania, obie kolejności i „prawda/fałsz” liczą wynik zgodnie z kluczami z tego pliku.
- Układ działa na telefonie (szerokość 390 px).

---

## 1. Metadane działu

| pole | wartość |
|---|---|
| `id` | `'d4'` |
| `nr` | `4` |
| `tytul` | `'Starożytny Egipt'` |
| `zakres` | `'podręcznik s. 22–27'` |

---

## 2. Kategorie

| # | `id` | `ikona` | `nazwa` | `krotko` | `opis` | `c` | `soft` | `dark` |
|---|---|---|---|---|---|---|---|---|
| 1 | `d4-slowa` | 🗣️ | Wyjaśnij własnymi słowami | Słowami | Opowiedz pełnymi zdaniami, o co chodzi. | `#FF6B5B` | `#FFE7E2` | `#C4382A` |
| 2 | `d4-pojecia` | 📖 | Słowniczek pojęć | Pojęcia | Krótko i konkretnie: co znaczy to słowo? | `#7C5CFF` | `#EDE9FF` | `#5536D6` |
| 3 | `d4-spoleczenstwo` | 👑 | Faraon i jego poddani | Faraon | Kto rządził, kto słuchał i kto co robił. | `#F59E0B` | `#FFEFCC` | `#9A5B00` |
| 4 | `d4-pismo` | ✍️ | Pismo egipskie | Pismo | Hieroglify, pisarze i papirus. | `#14A39F` | `#DBF3F1` | `#0A736F` |
| 5 | `d4-zrodla` | 📜 | Źródło, mapa i ilustracja | Źródła | Przeczytaj, popatrz i wyciągnij wnioski. | `#8B5E3C` | `#F4E9DF` | `#6B4226` |
| 6 | `d4-daty` | 📅 | Daty i oś czasu | Daty | Ustaw wydarzenia w kolejności i policz lata. | `#3B82F6` | `#E1EBFF` | `#1E5CC8` |
| 7 | `d4-pary` | 🔗 | Dopasuj i ułóż | Dopasuj | Piramida społeczna i pojęcia w parach. | `#E8579B` | `#FCE4EF` | `#AD2966` |
| 8 | `d4-pf` | ⚖️ | Prawda czy fałsz? | Prawda / fałsz | Zdecyduj przy każdym zdaniu. A zdania fałszywe popraw! | `#16A063` | `#DFF5E9` | `#11774A` |

---

## 3. Schemat pól pytania

| `typ` | pola |
|---|---|
| `opis`, `pojecie`, `krotka`, `policz`, `wymien`, `obraz`, `mapa`, `zrodlo` | `q`, opcjonalnie `body`, `odp`, `extra` |
| `kolejnosc` | `q`, `elementy` (kolejność wyświetlania), `kolejnosc` (indeksy w poprawnej kolejności), `odp`, `extra`, opcjonalnie `hint` |
| `dopasuj` | `q`, `lewa`, `prawa`, `klucz` (litera dla każdej pozycji z `lewa`), `extra`; odpowiedź generuje się sama |
| `pf` | `q`, `zdania: [{t, p, fix}]` (`p` = `true` dla prawdy), `extra` |

---

## 4. Pytania

### Kategoria 1: `d4-slowa` – Wyjaśnij własnymi słowami

#### P1 · `opis`
**Pytanie:** Z jakiego powodu Egipt nazwano darem Nilu?

**Odpowiedź:**
W Egipcie **deszcz prawie nie pada**. Gdyby nie Nil, kraj byłby jedną wielką pustynią. Co roku **w lipcu zaczynał się wylew Nilu**, podobny do łagodnej powodzi: woda powoli przybierała, aż zalała pola, i **opadała dopiero we wrześniu**. Zostawał po niej **muł, który użyźniał pola**. Dlatego już w starożytności nazwano Egipt **darem Nilu**.

**Zabłyśnij na lekcji:**
Sami Egipcjanie nazywali swój kraj **Kemet**, czyli „Czarna Ziemia”, od ciemnego, żyznego mułu.

Coroczne wylewy Nilu skończyły się dopiero w XX w., gdy zbudowano wielką tamę w Asuanie, ukończoną w 1970 r.

Źródło: s. 22, s. 27 („To, co najważniejsze”)

---

#### P2 · `opis`
**Pytanie:** Dlaczego Egipcjanie zbudowali system nawadniający?

**Odpowiedź:**
Bo **wkrótce po wylewie ziemia zaczynała wysychać**. Egipcjanie wykopali więc **tysiące kanałów i niewielkich zbiorników wodnych**, z których nawadniali pola. Musieli je **ciągle pogłębiać**, bo inaczej zasypałby je piasek pustyni.

**Zabłyśnij na lekcji:**
Do czerpania wody z kanałów Egipcjanie używali **żurawia**: długiej tyczki z wiadrem na jednym końcu i ciężarem na drugim, która działa jak huśtawka. Podobne żurawie przy studniach można jeszcze zobaczyć na starych polskich wsiach.

Źródło: s. 22

---

#### P3 · `opis`
**Pytanie:** Kiedy i dlaczego Egipt stał się państwem?

**Odpowiedź:**
**Ok. 3100 r. p.n.e.** Budową i utrzymaniem systemu nawadniającego **ktoś musiał kierować**, dlatego Egipcjanie utworzyli państwo. Podlegali władzy **faraona**, czyli króla.

**Zabłyśnij na lekcji:**
Wcześniej istniały dwa królestwa: **Górny Egipt** na południu i **Dolny Egipt** na północy, w delcie Nilu. Dlatego faraonowie nosili podwójną koronę: białą Górnego i czerwoną Dolnego Egiptu.

Według tradycji pierwszym faraonem zjednoczonego Egiptu był Menes. Wielu uczonych utożsamia go z władcą o imieniu Narmer.

Źródło: s. 22

---

#### P4 · `opis`
**Pytanie:** Omów organizację państwa egipskiego: kto rządził i komu wydawał polecenia?

**Odpowiedź:**
Egipt był **monarchią**, a rządził nim **faraon**. Faraon **wydawał polecenia kapłanom, urzędnikom i oficerom**, a oni **przekazywali je chłopom, rzemieślnikom i żołnierzom**.

**Najwyższym urzędnikiem był wezyr**, który rządził państwem w imieniu faraona. Urzędnicy zarządzali prowincjami, dbali o kanały nawadniające i zaopatrzenie dla armii.

Faraon i jego urzędnicy **organizowali pracę mieszkańców, zapewniali im bezpieczeństwo i rozsądzali spory**. W zamian Egipcjanie składali faraonowi **daniny**.

**Zabłyśnij na lekcji:**
Egipt był podzielony na ok. 40 prowincji, które Grecy nazywali **nomami**. Każdą zarządzał urzędnik wyznaczony przez faraona.

Źródło: s. 22–23, s. 26–27 (polecenie A)

---

#### P5 · `opis`
**Pytanie:** Porównaj położenie urzędników i chłopów w starożytnym Egipcie.

**Odpowiedź:**
- **Urzędnicy** byli **wykształceni** (umieli czytać, pisać i rachować). Zarządzali prowincjami, dbali o kanały i zaopatrzenie dla armii. Byli **zamożni**, bo jako wynagrodzenie dostawali **ziemię i żywność**. Przekazywali polecenia faraona innym, więc **w piramidzie społecznej stali wysoko**.
- **Chłopi** stanowili **ogromną większość** mieszkańców. Uprawiali **ziemię należącą do faraona** i **oddawali większość plonów jako daninę**. W czasie wylewu Nilu musieli **pracować przy budowie** grobowców, świątyń i magazynów. **W piramidzie społecznej byli nisko**, niżej stali tylko niewolnicy.

**Zabłyśnij na lekcji:**
Zachował się egipski tekst nazywany „Satyrą na zawody”. Ojciec zachęca w nim syna do nauki na pisarza: opisuje, jak ciężko pracują rolnicy i rzemieślnicy, a pisarz ma czyste ręce i nikt nim nie pomiata.

Źródło: s. 26–27 (polecenie C)

---

### Kategoria 2: `d4-pojecia` – Słowniczek pojęć

#### P6 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: państwo, ustrój, monarchia.

**Odpowiedź:**
- **Państwo** – organizacja społeczeństwa, które **zamieszkuje jakieś terytorium, ma swoje prawa i podlega czyjejś władzy**.
- **Ustrój** – **sposób zorganizowania władzy** w państwie.
- **Monarchia** – **państwo rządzone przez koronowanego władcę**. Starożytny Egipt miał ustrój monarchiczny, bo rządził nim faraon.

**Zabłyśnij na lekcji:**
„Monarchia” pochodzi z greki: *monos* – jeden, *archein* – rządzić, czyli „władza jednego”. Polska przez wieki też była monarchią, rządzoną przez książąt i królów. Monarchiami są do dziś np. Wielka Brytania, Hiszpania i Szwecja, ale tamtejsi władcy mają znacznie mniej władzy niż faraon.

Źródło: s. 22–23

---

#### P7 · `pojecie`
**Pytanie:** Czym była danina? Czym zastąpiono daniny i kiedy?

**Odpowiedź:**
- **Danina** – to, co Egipcjanie składali faraonowi **w zbożu, zwierzętach, wyrobach rzemieślniczych itp.** Faraon przeznaczał daniny na utrzymanie siebie, swoich urzędników i żołnierzy.
- Gdy **na Bliskim Wschodzie wynaleziono pieniądze (VII w. p.n.e.)**, daniny zastąpiono **podatkami**.

**Zabłyśnij na lekcji:**
Pierwsze monety bito w **Lidii**, krainie na terenie dzisiejszej Turcji, z elektronu, czyli naturalnej mieszanki złota i srebra.

Podatki płacimy do dziś: część ceny prawie każdej rzeczy kupionej w sklepie to podatek.

Źródło: s. 23

---

#### P8 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: wezyr, prowincja, najemnik.

**Odpowiedź:**
- **Wezyr** – **najwyższy urzędnik**; rządził państwem **w imieniu faraona**, który przekazywał mu swoje polecenia.
- **Prowincja** – (tu) **część państwa, którą rządzi urzędnik wyznaczony przez władcę**.
- **Najemnik** – **żołnierz walczący w obcym wojsku za pieniądze**.

**Zabłyśnij na lekcji:**
Słowo „wezyr” przyszło do nas z języka arabskiego i tureckiego. Tak nazywano m.in. ministrów sułtana tureckiego. Egipski tytuł brzmiał inaczej, ale historycy używają słowa „wezyr”, bo dobrze oddaje tę funkcję.

Źródło: s. 26 (opisy i objaśnienia z gwiazdką)

---

### Kategoria 3: `d4-spoleczenstwo` – Faraon i jego poddani

#### P9 · `wymien`
**Pytanie:** Przedstaw uprawnienia faraona.

**Odpowiedź:**
- Sprawował **nieograniczoną władzę**.
- Miał **prawo życia i śmierci** nad wszystkimi mieszkańcami Egiptu. Nawet jeśli kazał zabić niewinnego człowieka, nie ponosił za to kary.
- **Do niego należała cała ziemia** w państwie, a chłopi ją tylko uprawiali.
- Był **najwyższym dowódcą wojskowym, najwyższym sędzią i najwyższym kapłanem**.
- **Wydawał polecenia** kapłanom, urzędnikom i oficerom.
- Otrzymywał **daniny** od Egipcjan.

**Zabłyśnij na lekcji:**
Słowo „faraon” pochodzi od egipskiego określenia „wielki dom”, czyli pałac. Znakami władzy faraona były m.in. korona, laska w kształcie pasterskiego haka i cep.

Źródło: s. 23, s. 26–27

---

#### P10 · `wymien`
**Pytanie:** Omów główne zadania faraona i jego urzędników. Co Egipcjanie dawali w zamian?

**Odpowiedź:**
Faraon i jego urzędnicy:
1. **organizowali pracę** mieszkańców państwa,
2. **zapewniali im bezpieczeństwo**,
3. **rozsądzali spory** między nimi.

W zamian Egipcjanie **składali faraonowi daniny** w zbożu, zwierzętach, wyrobach rzemieślniczych itp.

**Zabłyśnij na lekcji:**
Nad Nilem stawiano tzw. **nilometry**, czyli schody lub studnie ze znakami do mierzenia poziomu wody. Na ich podstawie urzędnicy przewidywali, jakie będą plony, i ustalali, ile trzeba oddać.

Źródło: s. 23

---

#### P11 · `krotka`
**Pytanie:** Za kogo Egipcjanie uważali faraona? Dlaczego nie wiemy, czy bóg słońca nazywał się Ra, czy Re?

**Odpowiedź:**
Egipcjanie uważali faraona za **syna boga słońca Ra (albo Re)**. Wierzyli, że **po śmierci faraon sam staje się bogiem**.

Nie wiemy, jak brzmiało imię boga, bo **Egipcjanie nie zapisywali samogłosek**.

**Zabłyśnij na lekcji:**
Boga Ra przedstawiano z głową sokoła i tarczą słońca nad głową. Ponieważ faraon miał po śmierci stać się bogiem, budowano dla niego wspaniałe grobowce, np. piramidy w Gizie. Znajdziesz je na mapie na s. 23.

Źródło: s. 23 (tekst i dymek postaci)

---

#### P12 · `krotka`
**Pytanie:** Omów rolę kapłanów w państwie egipskim.

**Odpowiedź:**
- Zajmowali się **nauką, zwłaszcza astronomią i medycyną**.
- Przy świątyniach prowadzili **szkoły dla przyszłych urzędników**.
- Byli **bardzo zamożni** i **nieraz wywierali wpływ na rządy państwem**, czyli faraon musiał postąpić tak, jak oni chcieli.

**Zabłyśnij na lekcji:**
Obserwując niebo, Egipcjanie stworzyli kalendarz z 365 dniami: 12 miesięcy po 30 dni i 5 dni dodatkowych. Pojawienie się o świcie gwiazdy Syriusz zapowiadało, że wkrótce zacznie się wylew Nilu.

Źródło: s. 26

---

#### P13 · `krotka`
**Pytanie:** Co należało do obowiązków chłopów?

**Odpowiedź:**
- **Uprawiali ziemię należącą do faraona**.
- **Większość plonów odnosili do magazynów jako daninę**.
- **W czasie wylewu Nilu** musieli **pracować przy budowie grobowców, świątyń lub magazynów**.
- Mogli też zostać **żołnierzami**.

**Zabłyśnij na lekcji:**
Dlaczego przy budowach pracowano właśnie w czasie wylewu? Bo pola były wtedy zalane i chłopi i tak nie mogli na nich pracować.

Archeolodzy odkryli obok piramid w Gizie osadę robotników. Wynika z niej, że piramidy budowali głównie zwykli pracownicy, którym dawano jedzenie, a nie tłumy niewolników, jak dawniej sądzono.

Źródło: s. 26

---

#### P14 · `wymien`
**Pytanie:** Kto wchodził w skład społeczeństwa starożytnego Egiptu i jakie miał obowiązki?

**Odpowiedź:**
Społeczeństwo Egiptu można przedstawić jako **piramidę**: im wyżej ktoś się znajdował, tym więcej ludzi musiało wypełniać jego polecenia.
1. **Faraon** – król, najwyższy dowódca wojskowy, sędzia i kapłan; wydawał polecenia.
2. **Wezyr** – najwyższy urzędnik; rządził państwem w imieniu faraona.
3. **Kapłani** – zajmowali się nauką (astronomią, medycyną), prowadzili szkoły przy świątyniach.
4. **Urzędnicy** (m.in. pisarze) – zarządzali prowincjami, dbali o kanały i zaopatrzenie dla armii.
5. **Rzemieślnicy** – wytwarzali narzędzia i przedmioty codziennego użytku.
6. **Żołnierze** – chłopi, rzemieślnicy i cudzoziemscy najemnicy; walczyli w wojnach faraona.
7. **Chłopi** – uprawiali ziemię faraona, oddawali daninę, w czasie wylewu budowali grobowce, świątynie i magazyny.
8. **Niewolnicy** – jeńcy wojenni lub osoby kupione na targu; należeli do swego pana i nie mieli żadnych praw.

**Zabłyśnij na lekcji:**
Uwaga, pułapka! Niewolnicy są na samym dole piramidy, bo nie mieli żadnych praw, ale było ich **niewielu**. Najliczniejszą grupą byli **chłopi**, którzy stanowili ogromną większość Egipcjan.

Źródło: s. 26–27 (polecenie B, „To, co najważniejsze”)

---

### Kategoria 4: `d4-pismo` – Pismo egipskie

#### P15 · `krotka`
**Pytanie:** Czym się zajmowali egipscy pisarze?

**Odpowiedź:**
Pisarze byli **urzędnikami**. **Sporządzali dokumenty państwowe** i **zapisywali informacje potrzebne do rządzenia państwem**, np. ile zboża zebrano do magazynów albo jaką zapłatę otrzymali robotnicy.

**Zabłyśnij na lekcji:**
Nauka na pisarza trwała wiele lat. Papirus był drogi, więc uczniowie ćwiczyli pisanie na skorupach naczyń i płaskich kawałkach wapienia.

Źródło: s. 27

---

#### P16 · `krotka`
**Pytanie:** Na jakich materiałach i w jaki sposób pisali Egipcjanie?

**Odpowiedź:**
- **Hieroglify wykuwali** w skałach, na kamiennych ścianach, posągach i obeliskach.
- Na co dzień pisarze używali uproszczonego **pisma kapłańskiego**. Pisali je **pędzelkiem na papirusie**, czyli materiale podobnym do papieru. Robiono go **z łodyg trzciny papirusowej**, która rosła nad Nilem.

**Zabłyśnij na lekcji:**
Od słowa „papirus” pochodzi nasze słowo „papier”. Papirus robiono tak: cienkie paski łodygi układano w dwóch warstwach na krzyż, prasowano i suszono. Pisano czarnym tuszem z sadzy, a ważniejsze fragmenty czerwonym.

Źródło: s. 27

---

#### P17 · `krotka`
**Pytanie:** Kiedy powstało pismo egipskie? Skąd pochodzi nazwa „hieroglify” i ile było znaków?

**Odpowiedź:**
Pismo egipskie powstało **ok. 3000 r. p.n.e.** Starożytni Grecy nazwali je **hieroglifami, czyli „świętymi znakami”**, bo zetknęli się z nimi **w świątyniach Egiptu**. Pismo hieroglificzne liczyło **ok. 800 znaków** i było trudne, dlatego na co dzień używano uproszczonego **pisma kapłańskiego**.

**Zabłyśnij na lekcji:**
Przez wieki nikt nie umiał czytać hieroglifów. Pomógł **Kamień z Rosetty**, znaleziony w 1799 r., na którym ten sam tekst wyryto trzema rodzajami pisma, w tym hieroglifami i po grecku. Dzięki niemu w 1822 r. Francuz **Jean-François Champollion** odczytał hieroglify.

Źródło: s. 27

---

### Kategoria 5: `d4-zrodla` – Źródło, mapa i ilustracja

#### P18 · `zrodlo`
**Pytanie:** Przeczytaj tekst źródłowy z podręcznika (s. 22): fragment „Dziejów” greckiego historyka Herodota z V w. p.n.e. Dlaczego, według Herodota, Egipcjanie mniej pracują przy uprawie roli niż mieszkańcy innych krajów?

**body:** Podręcznik, s. 22: ramka „Tekst źródłowy”

**Odpowiedź:**
Bo **nie muszą orać pługiem, kopać ani wykonywać innych ciężkich prac** przed siewem, które muszą wykonywać ludzie w innych krajach. W Egipcie **rzeka sama wylewa, nawadnia pola, a potem opada**. Wtedy wystarczy obsiać pole.

**Zabłyśnij na lekcji:**
Herodota nazywa się „ojcem historii”. Sam podróżował po Egipcie i opisywał to, co zobaczył.

Pamiętaj jednak, że źródło trzeba czytać krytycznie. Herodot trochę przesadził: Egipcjanie musieli kopać i ciągle pogłębiać tysiące kanałów (s. 22), więc ich praca wcale nie była łatwa.

Źródło: s. 22 (tekst źródłowy i pytanie pod nim)

---

#### P19 · `mapa`
**Pytanie:** Spójrz na mapę „Starożytny Egipt” (s. 23). Nad jakimi morzami leży Egipt? Gdzie znajdowały się tereny uprawne?

**body:** Podręcznik, s. 23: mapa „Starożytny Egipt”

**Odpowiedź:**
- Egipt leży nad **Morzem Śródziemnym** (od północy) i nad **Morzem Czerwonym** (od wschodu).
- **Tereny uprawne** to **wąski pas wzdłuż Nilu** i jego **delta** przy ujściu do Morza Śródziemnego. Resztę kraju zajmują **pustynie** z nielicznymi oazami.

**Zabłyśnij na lekcji:**
Nil płynie z południa na północ, dlatego południe nazywano Górnym Egiptem (bo „w górę rzeki”), a północ Dolnym Egiptem. Nil jest jedną z najdłuższych rzek świata (ok. 6650 km). Delta to nazwa od greckiej litery Δ, do której podobny jest kształt ujścia rzeki.

Źródło: s. 22–23 (tekst i mapa)

---

#### P20 · `obraz`
**Pytanie:** Przyjrzyj się malowidłu na s. 23. Kogo przedstawia i co się na nim dzieje? Z którego wieku pochodzi?

**body:** Podręcznik, s. 23: malowidło z faraonem na rydwanie

**Odpowiedź:**
Przedstawia **faraona Ramzesa II**, który **na rydwanie prowadzi Egipcjan do ataku na nieprzyjacielską twierdzę**. To kopia malowidła ściennego **z XIII w. p.n.e.** Malowidło pokazuje, że faraon był **najwyższym dowódcą wojskowym**.

**Zabłyśnij na lekcji:**
Na egipskich malowidłach faraon jest dużo większy od innych postaci. Tak Egipcjanie pokazywali, kto jest najważniejszy.

Ramzes II panował ok. 66 lat i kazał zbudować m.in. świątynie w **Abu Simbel** (zaznaczone na mapie). W latach 60. XX w. przeniesiono je w całości wyżej, żeby nie zalała ich woda ze sztucznego jeziora przy nowej tamie.

Źródło: s. 23 (podpis pod malowidłem, mapa)

---

### Kategoria 6: `d4-daty` – Daty i oś czasu

#### P21 · `kolejnosc`
**Pytanie:** Ułóż wydarzenia w kolejności, od najdawniejszego do najpóźniejszego. Przydadzą się też daty z działu 3!

**hint:** Klikaj wydarzenia od najdawniejszego do najpóźniejszego.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `Egipcjanie tworzą państwo`
- 1: `Ramzes II prowadzi wojska do ataku na twierdzę`
- 2: `Sumerowie wynajdują pismo`
- 3: `Egipt zostaje przyłączony do Rzymu`
- 4: `Powstaje pismo egipskie`
- 5: `Na Bliskim Wschodzie wynaleziono pieniądze`
- 6: `Upadek cywilizacji Sumerów`

**kolejnosc:** `[2, 0, 4, 6, 1, 5, 3]`

**Odpowiedź:**
Sumerowie wynajdują pismo (ok. 3500 r. p.n.e.) → Egipcjanie tworzą państwo (ok. 3100 r. p.n.e.) → powstaje pismo egipskie (ok. 3000 r. p.n.e.) → upadek cywilizacji Sumerów (ok. 2000 r. p.n.e.) → Ramzes II na malowidle (XIII w. p.n.e.) → wynalezienie pieniędzy (VII w. p.n.e.) → Egipt częścią Rzymu (30 r. p.n.e.)

**Zabłyśnij na lekcji:**
Państwo egipskie istniało przez cały ten czas, od drugiego wydarzenia aż do ostatniego. Widziało upadek Sumerów i wynalezienie pieniędzy!

Źródło: s. 22–23, s. 27; daty Sumerów z działu 3 (s. 17–19)

---

#### P22 · `policz`
**Pytanie:** W którym wieku i w którym tysiącleciu to było? Uważaj na zera!

**body (chipy):**
- ok. 3100 r. p.n.e. (powstanie państwa)
- ok. 3000 r. p.n.e. (powstanie pisma)
- 30 r. p.n.e. (przyłączenie do Rzymu)

**Odpowiedź:**
- ok. 3100 r. p.n.e. → 31 + 1 = 32 → **XXXII w. p.n.e.**; 3 + 1 = 4 → **IV tysiąclecie p.n.e.**
- ok. 3000 r. p.n.e. → trzy zera, więc nie dodajemy 1 → **XXX w. p.n.e.** i **III tysiąclecie p.n.e.**
- 30 r. p.n.e. → 0 + 1 = 1 → **I w. p.n.e.** i **I tysiąclecie p.n.e.**

**Zabłyśnij na lekcji:**
Powstanie państwa i powstanie pisma dzieli tylko ok. 100 lat, a należą do różnych tysiącleci! To jak z sylwestrem: kilka minut różnicy, a już inny rok.

Źródło: s. 22, s. 27; reguły liczenia z działu 1

---

#### P23 · `policz`
**Pytanie:** Policz: a) Ile lat przetrwało starożytne państwo egipskie (od ok. 3100 do 30 r. p.n.e.)? b) O ile lat pismo egipskie (ok. 3000 r. p.n.e.) jest młodsze od pisma Sumerów (ok. 3500 r. p.n.e.)? c) Ile lat minęło od przyłączenia Egiptu do Rzymu do 2026 r.?

**Odpowiedź:**
- a) 3100 − 30 = **ok. 3070 lat**, czyli **ponad 3 tysiące lat**, tak jak podaje podręcznik.
- b) 3500 − 3000 = **ok. 500 lat**.
- c) 30 + 2026 − 1 = **2055 lat**. Odejmujemy 1, bo nie było roku 0.

**Zabłyśnij na lekcji:**
Ostatnią władczynią Egiptu była słynna **Kleopatra**. Po jej śmierci w 30 r. p.n.e. Egipt zajęli Rzymianie. Wielką piramidę w Gizie zbudowano ok. 2560 r. p.n.e., czyli ok. 2530 lat przed śmiercią Kleopatry. Kleopatra żyła więc bliżej naszych czasów niż czasów budowy piramidy!

Źródło: s. 22–23, s. 27; data pisma Sumerów z działu 3 (s. 19)

---

### Kategoria 7: `d4-pary` – Dopasuj i ułóż

#### P24 · `kolejnosc`
**Pytanie:** Ułóż grupy społeczne starożytnego Egiptu od szczytu piramidy w dół.

**hint:** Klikaj od szczytu piramidy w dół.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `chłopi`
- 1: `wezyr`
- 2: `rzemieślnicy`
- 3: `niewolnicy`
- 4: `faraon`
- 5: `urzędnicy`
- 6: `żołnierze`
- 7: `kapłani`

**kolejnosc:** `[4, 1, 7, 5, 2, 6, 0, 3]`

**Odpowiedź:**
**faraon → wezyr → kapłani → urzędnicy (m.in. pisarze) → rzemieślnicy → żołnierze → chłopi → niewolnicy**

**Zabłyśnij na lekcji:**
Im wyżej ktoś stał w piramidzie, tym więcej ludzi musiało wypełniać jego polecenia. Na szczycie jest jedna osoba, faraon, a niżej coraz więcej ludzi. Wyjątkiem są niewolnicy: stoją najniżej, bo nie mieli żadnych praw, ale było ich niewielu.

Źródło: s. 26, s. 27 („To, co najważniejsze” – kolejność grup)

---

#### P25 · `dopasuj`
**Pytanie:** Dopasuj grupę społeczną do jej opisu.

**lewa:**
1. `wezyr`
2. `kapłani`
3. `urzędnicy`
4. `żołnierze`
5. `chłopi`
6. `niewolnicy`

**prawa** (w tej kolejności):
- **A** – `Uprawiali ziemię faraona i oddawali większość plonów jako daninę; w czasie wylewu budowali grobowce i świątynie`
- **B** – `Jeńcy wojenni lub osoby kupione na targu; należeli do swego pana i nie mieli żadnych praw`
- **C** – `Najwyższy urzędnik; rządził państwem w imieniu faraona`
- **D** – `Walczyli w wojnach faraona; byli wśród nich także cudzoziemscy najemnicy`
- **E** – `Zajmowali się nauką, zwłaszcza astronomią i medycyną; prowadzili szkoły przy świątyniach`
- **F** – `Ludzie wykształceni; zarządzali prowincjami, dbali o kanały i zaopatrzenie dla armii`

**klucz:** 1–C, 2–E, 3–F, 4–D, 5–A, 6–B → `['C','E','F','D','A','B']`

**Zabłyśnij na lekcji:**
W zadaniu brakuje jednej grupy: **rzemieślników**. Wytwarzali narzędzia i przedmioty codziennego użytku.

Źródło: s. 26

---

#### P26 · `dopasuj`
**Pytanie:** Dopasuj pojęcie do znaczenia.

**lewa:**
1. `hieroglify`
2. `pismo kapłańskie`
3. `papirus`
4. `obelisk`
5. `pisarz`

**prawa** (w tej kolejności):
- **A** – `Pomnik w formie wysokiego słupa`
- **B** – `Materiał podobny do papieru, robiony z łodyg trzciny rosnącej nad Nilem`
- **C** – `Urzędnik, który sporządzał dokumenty i zapisywał informacje potrzebne do rządzenia państwem`
- **D** – `„Święte znaki” – pismo, które Egipcjanie wykuwali m.in. w kamieniu`
- **E** – `Uproszczone znaki, którymi pisarze pisali na co dzień pędzelkiem na papirusie`

**klucz:** 1–D, 2–E, 3–B, 4–A, 5–C → `['D','E','B','A','C']`

**Zabłyśnij na lekcji:**
Egipskie obeliski można dziś zobaczyć nie tylko w Egipcie, lecz także m.in. w Rzymie, Paryżu, Londynie i Nowym Jorku. Przywieziono je tam w różnych czasach jako cenne zabytki.

Źródło: s. 27 (tekst i objaśnienie z gwiazdką)

---

### Kategoria 8: `d4-pf` – Prawda czy fałsz?

#### P27 · `pf`
**Pytanie:** Które zdania są prawdziwe, a które fałszywe?

**zdania:**

| lit. | `t` (zdanie) | `p` | `fix` (wyjaśnienie po odsłonięciu) |
|---|---|---|---|
| a | Egipt leży w północno-wschodniej Afryce. | `true` | *(puste)* |
| b | Wylew Nilu był gwałtowną, niszczycielską powodzią. | `false` | Przypominał **łagodną powódź**: woda powoli przybierała od lipca, opadała we wrześniu i zostawiała **żyzny muł**. |
| c | Faraon był najwyższym dowódcą wojskowym, najwyższym sędzią i najwyższym kapłanem. | `true` | *(puste)* |
| d | Chłopi byli właścicielami ziemi, którą uprawiali. | `false` | **Cała ziemia należała do faraona**, a chłopi ją tylko uprawiali. |
| e | Niewolników było w Egipcie bardzo dużo. | `false` | Niewolników było **niewielu**. Najliczniejsi byli chłopi. |
| f | Pismo hieroglificzne liczyło ok. 800 znaków. | `true` | *(puste)* |
| g | Kapłani nieraz wywierali wpływ na rządy państwem. | `true` | *(puste)* |
| h | Egipt stał się częścią Rzymu w 30 r. n.e. | `false` | Stało się to w **30 r. p.n.e.** |

**Zabłyśnij na lekcji:**
Wielka piramida w Gizie przez ok. 3800 lat była najwyższą budowlą zbudowaną przez ludzi. To jedyny z siedmiu cudów świata starożytnego, który przetrwał do dziś.

Źródło: s. 22–23, s. 26–27

---

## 5. Ściągawka (pole `sciagawka`)

**Oś czasu** (segmenty od lewej):
1. **ok. 3100 p.n.e.** – powstanie państwa egipskiego
2. **ok. 3000 p.n.e.** – powstanie pisma egipskiego
3. **XIII w. p.n.e.** – faraon Ramzes II
4. **VII w. p.n.e.** – wynalezienie pieniędzy na Bliskim Wschodzie; daniny zastąpione podatkami
5. **30 p.n.e.** – Egipt częścią Rzymu

**Karty:**
- **🌊 Dar Nilu** – wylewy Nilu (od lipca do września) nawadniały ziemię i nanosiły żyzny muł. Po wylewie: system nawadniający z kanałów i zbiorników.
- **👑 Faraon** – syn boga słońca Ra (według wierzeń Egipcjan); prawo życia i śmierci; cała ziemia jego; najwyższy dowódca, sędzia i kapłan.
- **🏛️ Państwo** – monarchia. Faraon i urzędnicy: organizowali pracę, zapewniali bezpieczeństwo, rozsądzali spory. W zamian daniny.
- **🔺 Piramida społeczna** – faraon → wezyr → kapłani → urzędnicy (m.in. pisarze) → rzemieślnicy → żołnierze → chłopi → niewolnicy.
- **✍️ Pismo** – hieroglify (ok. 800 „świętych znaków”, wykuwane w kamieniu) i uproszczone pismo kapłańskie (pędzelkiem na papirusie).

---

## 6. Rangi i komunikaty maskotki dla działu 4 (pola `rangi`, `start`)

Rangi „wspinają się” po piramidzie społecznej, z pominięciem niewolników.

**start:** `Witaj nad Nilem! Zaczynasz u podnóża piramidy, a każde pytanie, które umiesz, wyniesie Cię wyżej. I przesypie trochę mojego piasku!`

| `od` | `e` | `n` | `msg` |
|---|---|---|---|
| 0 | 🌾 | Chłop znad Nilu | Pierwsze pole obsiane! Piasek zaczął się sypać. ⏳ |
| 0.25 | 🔨 | Rzemieślnik | Brawo! Awans: zostajesz Rzemieślnikiem. |
| 0.5 | ✍️ | Pisarz | Ponad połowa! Zostajesz Pisarzem. Pędzelek w dłoń! |
| 0.75 | 📜 | Wezyr | Wezyr! Już tylko jeden stopień do szczytu piramidy… |
| 1 | 👑 | Faraon wiedzy | FARAON WIEDZY! Szczyt piramidy zdobyty, cały dział opanowany! 🏆 |

---

## 7. Weryfikacja merytoryczna (do wiadomości, nie renderować)

**Co sprawdzono**
- Każda odpowiedź jest zgodna z tekstem s. 22–23 i 26–27 (strony podano przy pytaniach). Obejmują one wszystkie pytania 1–9 z czerwonych ramek, pytanie do tekstu źródłowego, pytanie do mapy oraz polecenia A, B i C. Tabela „To, co najważniejsze” jest w całości w P1, P4, P9, P10, P14, P16–P17 i w ściągawce.
- Rachunki: 3100 − 30 = 3070; 3500 − 3000 = 500; 30 + 2026 − 1 = 2055; 2560 − 30 = 2530; 3100 p.n.e. → XXXII w. p.n.e. i IV tysiąclecie p.n.e.; 3000 p.n.e. → XXX w. p.n.e. i III tysiąclecie p.n.e.; 30 p.n.e. → I w. p.n.e. i I tysiąclecie p.n.e.
- Klucze dopasowań i obie kolejności (P21, P24) sprawdzone pozycja po pozycji. Kolejność grup w P24 pochodzi z „To, co najważniejsze” na s. 27.
- Ciekawostki („Zabłyśnij na lekcji”) wykraczają poza podręcznik i zostały sprawdzone z wiedzą ogólną.

**Uwagi**
1. **Strony 24–25** nie zostały dostarczone. Numeracja pytań w podręczniku przechodzi z 4 (s. 23) do 5 (s. 26), więc na s. 24–25 prawdopodobnie nie ma pytań w ramkach, a „To, co najważniejsze” nie odwołuje się do żadnej treści spoza s. 22–23 i 26–27. Jeśli na tych stronach jest tekst (np. o piramidach lub wierzeniach), nie jest on tu uwzględniony.
2. **Tekst źródłowy Herodota** nie jest przepisany ani w tym pliku, ani na stronie, bo polskie tłumaczenie jest chronione prawem autorskim. Odpowiedź P18 jest własnym streszczeniem.
3. **Pieniądze i podatki.** Podręcznik upraszcza: pierwsze monety powstały w VII w. p.n.e. w Lidii, ale w samym Egipcie upowszechniły się znacznie później. Odpowiedź P7 trzyma się podręcznika.
4. **„Ok. 800 znaków”** to przybliżona liczba hieroglifów z klasycznego okresu (później było ich znacznie więcej). Zostaje wersja z podręcznika.
5. **Piramidy** pojawiają się na tych stronach tylko w legendzie mapy, dlatego mówią o nich wyłącznie ciekawostki (P11, P13, P23, P27). Nie ma o nich pytań.
