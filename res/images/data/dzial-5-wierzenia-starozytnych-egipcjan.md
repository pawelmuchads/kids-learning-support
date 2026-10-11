# Kapsuła Czasu – Dział 5: Wierzenia starożytnych Egipcjan

Specyfikacja pytań i odpowiedzi do dopisania na stronę `kapsula-czasu-historia.html`.
Źródło: podręcznik do historii, dział 5 „Wierzenia starożytnych Egipcjan”, s. 28–29 i 32–33. Strony 30–31 nie zostały dostarczone (patrz sekcja 7).

---

## 0. Instrukcja dla modelu, który dokończy stronę

### Kontekst
`kapsula-czasu-historia.html` to jednoplikowa strona (HTML + CSS + JS, bez bibliotek, tylko Google Fonts) z pytaniami do powtórki z historii dla ucznia szkoły podstawowej. Treść jest w tablicy `DZIALY` w skrypcie. Jest tam dział 1, a być może także działy 2, 3, 4 i 6 (osobne pliki MD o tej samej strukturze).

### Zadanie
1. Dopisz do `DZIALY` nowy dział według sekcji 1–6 tego pliku. Działy w tablicy i w zakładkach ustaw według `nr` (1, 2, 3, 4, 5, 6…).
2. **Jeśli strona obsługuje jeden dział** (skrypt wybiera `DZIALY.filter(...)[0]`, a zakładki nic nie robią), wprowadź najpierw zmiany z listy niżej. **Jeśli już obsługuje kilka działów**, dodaj tylko to, czego brakuje (typy `zrodlo` i `obraz`, neutralny komunikat wyniku w `kolejnosc`).
3. **Nie zmieniaj istniejących działów** ani wyglądu strony.

### Zasady merytoryczne (ważne)
- Treść pytań, odpowiedzi i ciekawostek została sprawdzona z podręcznikiem i ze źródłami wiedzy ogólnej. **Nie dopisuj nowych faktów, dat ani liczb** i nie „poprawiaj” treści.
- **Nie przepisuj na stronę tekstu źródłowego z Księgi Umarłych z s. 32** (polskie tłumaczenie jest chronione prawem autorskim). Pytanie P17 odsyła do podręcznika, a odpowiedź streszcza tekst własnymi słowami.
- Wszystko, co dotyczy bogów, sądu Ozyrysa i krainy umarłych, to **wierzenia starożytnych Egipcjan**. Zostaw zwroty „Egipcjanie wierzyli”, „według Egipcjan”.
- **Nie używaj sformułowania „najwyższa kamienna budowla na Ziemi”** o piramidzie Cheopsa (patrz sekcja 7). Na stronie podawaj tylko jej wysokość (138 m) i ciekawostkę w brzmieniu z P12.
- Polskie cudzysłowy „ ”, półpauza – w zakresach dat, formy neutralne płciowo.
- Nie odtwarzaj ilustracji ani postaci z podręcznika (prawa autorskie). Pytania o ilustracje odsyłają do stron podręcznika.

### Konwersja treści z tego pliku do pól JS
- `**tekst**` → `<b>tekst</b>`, `*tekst*` → `<i>tekst</i>`.
- Lista `-` → `<ul><li>…</li></ul>`, lista numerowana → `<ol><li>…</li></ol>`.
- Akapity → `<p>…</p>`.
- Linie „Źródło: …” są tylko do weryfikacji – **nie renderuj ich**.

### Zmiany w kodzie (jeśli jeszcze ich nie ma)
1. **Przełączanie działów.** Funkcja `render(dzId)` buduje `ALL`, `BY`, `TOTAL`, `#main`, `#chips` i stopkę dla wybranego działu i jest wywoływana po kliknięciu zakładki. Aktywny dział zapamiętaj w `location.hash` (np. `#d5`) i odtwórz go przy wczytaniu strony. Domyślnie otwiera się dział 1.
2. **Etykiety zakładek** z numerem z podręcznika: „Dział 5 Wierzenia starożytnych Egipcjan”. Jeśli tytuł się nie mieści, użyj pola `krotkiTytul: 'Wierzenia Egipcjan'` (tylko na zakładce).
3. **Postęp per dział.** Pasek, ranga, klepsydra, chipy i licznik dotyczą aktywnego działu. `uid` ma prefiks `dz.id` (np. `d5-5`). Zostaw klucz `localStorage` `kapsula-czasu-v1`.
4. **Rangi i komunikaty maskotki per dział:** opcjonalne pola `rangi` i `start` w obiekcie działu (wartości w sekcji 6). Toast końcowy: „🏆 Cały dział opanowany! Zostajesz: ” + nazwa najwyższej rangi.
5. **Typy w `TYPY`** (dodaj brakujące): `pojecie: '📖 Wyjaśnij pojęcie'`, `obraz: '🖼️ Praca z ilustracją'`, `zrodlo: '📜 Tekst źródłowy'`. Renderują się jak zwykłe pytanie (`q`, opcjonalne `body`, `odp`, `extra`).
6. **Typ `kolejnosc`:**
   - Opcjonalne pole `hint` (dla P20: „Klikaj wydarzenia od najdawniejszego do najpóźniejszego.”, dla P25: „Klikaj kolejne etapy sądu, od początku do końca.”).
   - Placeholder `.oseq:empty::before` neutralny: „Klikaj po kolei, a pojawi się tutaj twoja kolejność”.
   - Komunikat wyniku neutralny: „Na właściwym miejscu: x z n” (nie „Daty na właściwym miejscu”).
7. Przy zmianie działu: wyłącz filtr „Tylko do powtórki”, przewiń na górę, przelicz pasek i maskotkę.
8. **Ściągawka:** sekcja 5. Oś czasu jak w dziale 1 (`.tl`), resztę jako karty `.rules`.

### Kryteria gotowości
- Brak błędów w konsoli; strona działa po otwarciu z dysku (`file://`).
- Wszystkie zakładki działają, postęp każdego działu liczy się osobno i przetrwa odświeżenie strony.
- Dział 5 ma 26 pytań w 7 kategoriach, numerowane od 1.
- Dopasowania, obie kolejności i „prawda/fałsz” liczą wynik zgodnie z kluczami z tego pliku.
- Układ działa na telefonie (szerokość 390 px).

---

## 1. Metadane działu

| pole | wartość |
|---|---|
| `id` | `'d5'` |
| `nr` | `5` |
| `tytul` | `'Wierzenia starożytnych Egipcjan'` |
| `krotkiTytul` | `'Wierzenia Egipcjan'` |
| `zakres` | `'podręcznik s. 28–33'` |

---

## 2. Kategorie

| # | `id` | `ikona` | `nazwa` | `krotko` | `opis` | `c` | `soft` | `dark` |
|---|---|---|---|---|---|---|---|---|
| 1 | `d5-slowa` | 🗣️ | Wyjaśnij własnymi słowami | Słowami | Opowiedz pełnymi zdaniami, o co chodzi. | `#FF6B5B` | `#FFE7E2` | `#C4382A` |
| 2 | `d5-bogowie` | ☀️ | Bogowie Egiptu | Bogowie | W kogo i jak wierzyli Egipcjanie. | `#F59E0B` | `#FFEFCC` | `#9A5B00` |
| 3 | `d5-groby` | 🔺 | Piramidy, grobowce i mumie | Piramidy | „Domy wieczności” i sposoby na życie wieczne. | `#14A39F` | `#DBF3F1` | `#0A736F` |
| 4 | `d5-zrodla` | 📜 | Źródło i ilustracja | Źródła | Przeczytaj, popatrz i wyciągnij wnioski. | `#8B5E3C` | `#F4E9DF` | `#6B4226` |
| 5 | `d5-daty` | 📅 | Daty i oś czasu | Daty | Ustaw wydarzenia w kolejności i policz lata. | `#3B82F6` | `#E1EBFF` | `#1E5CC8` |
| 6 | `d5-pary` | 🔗 | Dopasuj i ułóż | Dopasuj | Bogowie w parach i przebieg sądu Ozyrysa. | `#E8579B` | `#FCE4EF` | `#AD2966` |
| 7 | `d5-pf` | ⚖️ | Prawda czy fałsz? | Prawda / fałsz | Zdecyduj przy każdym zdaniu. A zdania fałszywe popraw! | `#16A063` | `#DFF5E9` | `#11774A` |

---

## 3. Schemat pól pytania

| `typ` | pola |
|---|---|
| `opis`, `pojecie`, `krotka`, `policz`, `wymien`, `obraz`, `zrodlo` | `q`, opcjonalnie `body`, `odp`, `extra` |
| `kolejnosc` | `q`, `elementy` (kolejność wyświetlania), `kolejnosc` (indeksy w poprawnej kolejności), `odp`, `extra`, opcjonalnie `hint` |
| `dopasuj` | `q`, `lewa`, `prawa`, `klucz` (litera dla każdej pozycji z `lewa`), `extra`; odpowiedź generuje się sama |
| `pf` | `q`, `zdania: [{t, p, fix}]` (`p` = `true` dla prawdy), `extra` |

---

## 4. Pytania

### Kategoria 1: `d5-slowa` – Wyjaśnij własnymi słowami

#### P1 · `opis`
**Pytanie:** W jaki sposób Ozyrys został władcą krainy umarłych?

**Odpowiedź:**
Według Egipcjan Ozyrysa **zabił i poćwiartował jego zły brat Set**. Siostra Ozyrysa, **Izyda, pozbierała jego szczątki**, a **Anubis je skleił**. Tak powstała **pierwsza mumia**. Inni bogowie **przywrócili Ozyrysa do życia** i odtąd **władał on krainą umarłych**.

**Zabłyśnij na lekcji:**
Według mitu Izyda była nie tylko siostrą, lecz także żoną Ozyrysa. Ich syn **Horus** pokonał później Seta. Na ilustracji z sądu Ozyrysa (s. 33) to właśnie Horus prowadzi zmarłego przed tron swojego ojca.

Źródło: s. 29

---

#### P2 · `opis`
**Pytanie:** Co robili Egipcjanie, żeby zapewnić sobie przychylność bogów?

**Odpowiedź:**
**Wznosili bogom kamienne świątynie** i **składali ofiary**: żywność, wyroby rzemieślnicze oraz kosztowności. Wierzyli, że zadowolone bóstwa spowodują np. **obfity wylew Nilu**.

**Zabłyśnij na lekcji:**
Największy zespół świątyń starożytnego Egiptu to **Karnak** w Tebach (Teby znajdziesz na mapie w dziale 4). Budowano go i rozbudowywano przez ok. 2000 lat.

Źródło: s. 29

---

#### P3 · `opis`
**Pytanie:** Wyjaśnij, przed kim i jak faraonowie próbowali zabezpieczyć swoje groby.

**Odpowiedź:**
Przed **złodziejami**, których kusiły skarby w grobowcach. Faraonowie kazali **budować piramidy** albo **kuć grobowce w niedostępnych skałach**. W piramidzie Cheopsa **komorę grobową ukryto wewnątrz budowli**, a **wejście zawalono kamieniami**.

Na próżno: złodzieje obrabowali wszystkie znane piramidy i grobowce **z wyjątkiem jednego**, grobowca Tutanchamona.

**Zabłyśnij na lekcji:**
Grobowce w skałach kuto m.in. w **Dolinie Królów** koło Teb (zaznaczonej na mapie w dziale 4). Tam w 1922 r. znaleziono grób Tutanchamona.

Źródło: s. 29

---

#### P4 · `opis`
**Pytanie:** Co robili Egipcjanie, żeby zapewnić swoim zmarłym życie wieczne?

**Odpowiedź:**
1. **Dbali, by ciało nie uległo rozkładowi**: balsamowali ciała i sporządzali mumie, wkładali je do trumien i sarkofagów, budowali piramidy (np. Cheopsa) i kuli w skałach grobowce.
2. **Pomagali duszy przejść sąd Ozyrysa**: wkładali do grobów tzw. **Księgę Umarłych** z tekstami mów i modlitw.
3. W grobowcach faraonów umieszczali **przedmioty potrzebne na tamtym świecie**: łoża pokryte złotem, rydwany, tron, ubrania, klejnoty.

**Zabłyśnij na lekcji:**
Egipcjanie mumifikowali nie tylko ludzi, lecz także zwierzęta, np. koty, krokodyle i ibisy (ptaki boga Tota). Archeolodzy znaleźli miliony takich zwierzęcych mumii.

Źródło: s. 29, s. 32–33 (polecenie A, „To, co najważniejsze”)

---

#### P5 · `opis`
**Pytanie:** Wyjaśnij, jak, według Egipcjan, przebiegał sąd Ozyrysa.

**Odpowiedź:**
Egipcjanie wierzyli, że **dusza każdego zmarłego staje przed sądem Ozyrysa**. Ilustracja z Księgi Umarłych pisarza Hunefera (s. 33) pokazuje przebieg sądu:
1. **Anubis** prowadzi zmarłego na sąd.
2. Zmarły **opowiada o swoim życiu 14 bogom**, którzy wraz z Ozyrysem wydadzą wyrok.
3. Na **wadze** waży się **serce zmarłego**, a na drugiej szali leży **strusie pióro**. Serce lżejsze od pióra nie jest obciążone grzechami.
4. Serca cięższe od pióra pożera **Ammit, „Pożeraczka Zmarłych”**.
5. **Tot** zapisuje wynik sądu na papirusie.
6. **Horus** prowadzi zmarłego przed tron **Ozyrysa**, a Ozyrys przyjmuje go do krainy umarłych.

W zależności od wyroku dusza trafiała do **szczęśliwej krainy umarłych** albo **przestawała istnieć lub cierpiała wieczne męki**.

**Zabłyśnij na lekcji:**
Pióro było znakiem **Maat**, bogini prawdy i porządku świata.

Dlaczego ważono serce, a nie mózg? Egipcjanie uważali serce za siedzibę myśli i uczuć. Mózg podczas balsamowania usuwano i wyrzucano, a serce zostawiano w ciele, bo było potrzebne na sądzie.

Źródło: s. 32–33 (polecenie B, podpisy do ilustracji)

---

#### P6 · `opis`
**Pytanie:** Wytłumacz, po co Egipcjanie wkładali do grobów tzw. Księgi Umarłych.

**Odpowiedź:**
Żeby **pomogły zmarłemu podczas sądu Ozyrysa**. Księga Umarłych zawierała **spisane na papirusie teksty mów i modlitw**, które zmarły miał wygłosić przed Ozyrysem i innymi bogami. Były w niej też **ilustracje** przedstawiające ziemskie życie zmarłego oraz sąd Ozyrysa. Np. rodzina pisarza Hunefera włożyła mu taką księgę do grobu.

**Zabłyśnij na lekcji:**
Nazwę „Księga Umarłych” nadali jej dopiero nowożytni uczeni. Sami Egipcjanie nazywali te teksty mniej więcej „Księgą wychodzenia za dnia”. Papirus Hunefera można dziś oglądać w Muzeum Brytyjskim w Londynie.

Źródło: s. 32

---

### Kategoria 2: `d5-bogowie` – Bogowie Egiptu

#### P7 · `pojecie`
**Pytanie:** Co to jest politeizm?

**Odpowiedź:**
**Politeizm**, czyli **wielobóstwo**, to **wiara w wielu bogów**. Wyznawali go starożytni Egipcjanie.

**Zabłyśnij na lekcji:**
Przeciwieństwem politeizmu jest **monoteizm**, czyli wiara w jednego Boga. Poznasz go w dziale 6, o starożytnym Izraelu.

Źródło: s. 28, s. 33 („To, co najważniejsze”)

---

#### P8 · `wymien`
**Pytanie:** Podaj imiona i cechy pięciu bóstw Egiptu przedstawionych w podręczniku. Jak wyglądali egipscy bogowie?

**Odpowiedź:**
Egipscy bogowie mieli **kształty zwierząt, ludzi albo ludzi z głowami zwierząt**.
- **Ra** – bóg słońca, **najważniejszy z bogów, stwórca świata**. Codziennie wraz ze słońcem żeglował łodzią po niebie. Przedstawiany jako mężczyzna z głową sokoła, na której jest tarcza słoneczna.
- **Tot** (albo Thot) – patron mądrości, **bóg pisarzy i uczonych**. Przedstawiany jako mężczyzna z głową ibisa.
- **Anubis** – **bóg zmarłych i opiekun grobów**. Mężczyzna z głową szakala.
- **Ozyrys** – **sędzia umarłych i władca ich krainy**, bóg życia po śmierci. Mężczyzna owinięty bandażami jak mumia.
- **Izyda** – **opiekunka rodzin, bogini magii, uzdrowicielka chorych**; pomagała rodzącym kobietom. Często przedstawiana z tronem na głowie.

**Zabłyśnij na lekcji:**
Wygląd bogów nie był przypadkowy. Ibis, ptak Tota, ma długi, zakrzywiony dziób, trochę jak przyrząd do pisania. Szakale kręciły się przy cmentarzach na pustyni, dlatego szakal stał się zwierzęciem boga zmarłych.

Źródło: s. 28

---

#### P9 · `pojecie`
**Pytanie:** Co trzymali w dłoniach egipscy bogowie i co to oznaczało?

**Odpowiedź:**
- W **lewej dłoni** trzymali **krzyż ankh**, który oznaczał **życie i nieśmiertelność**.
- W **prawej dłoni** trzymali **berło uas**, czyli **oznakę boskiej władzy**.

**Zabłyśnij na lekcji:**
Ankh ma kształt krzyża z pętlą u góry. Był też znakiem pisma oznaczającym „życie”. Znajdziesz go nawet w imieniu faraona Tut-**ankh**-amona.

Źródło: s. 28 (opis Tota)

---

#### P10 · `krotka`
**Pytanie:** Za kogo uchodził każdy faraon? Dlaczego faraonowie nosili sztuczne brody?

**Odpowiedź:**
Każdy faraon **uchodził za syna boga słońca Ra**. Egipcjanie wierzyli, że **po śmierci faraon staje się bogiem**.

Egipcjanie golili brody, ale faraonowie **nosili sztuczne brody na znak swojej władzy i mocy**. Nosiła ją nawet **kobieta, gdy była faraonem**.

**Zabłyśnij na lekcji:**
Kobietą-faraonem była np. **Hatszepsut** (XV w. p.n.e.). Na wielu posągach przedstawiono ją ze sztuczną brodą, tak jak faraonów mężczyzn.

Źródło: s. 29 (tekst i dymek postaci)

---

### Kategoria 3: `d5-groby` – Piramidy, grobowce i mumie

#### P11 · `krotka`
**Pytanie:** Gdzie Egipcjanie grzebali zmarłych? Po co faraonowie budowali sobie grobowce już za życia i co w nich umieszczano?

**Odpowiedź:**
Egipcjanie grzebali zmarłych **na pustyni**, którą uważali za **królestwo demonów i śmierci**. Faraonowie budowali sobie już za życia **„domy wieczności”**, czyli grobowce. Miały one:
- **ukazać potęgę władcy**,
- **pomieścić przedmioty potrzebne mu na tamtym świecie**: łoża pokryte złotem, rydwany, tron, ubrania, klejnoty…

**Zabłyśnij na lekcji:**
Pustynia miała też praktyczne zalety: nie zabierała cennej ziemi uprawnej nad Nilem, a suchy, gorący piasek dobrze chronił ciała. Najstarsze egipskie mumie powstały w sposób naturalny, po prostu wysuszone w piasku.

Źródło: s. 29

---

#### P12 · `krotka`
**Pytanie:** Kiedy powstała piramida Cheopsa? Jaka jest wysoka i z ilu bloków ją zbudowano? Gdzie ukryto komorę grobową?

**Odpowiedź:**
- Powstała **w XXVI w. p.n.e.**
- Jej szczyt wznosi się na wysokość **138 metrów**.
- Do budowy zużyto **2 300 000 kamiennych bloków**.
- **Komorę grobową ukryto wewnątrz budowli**, a wejście zawalono kamieniami. Złodzieje i tak ją obrabowali.

**Zabłyśnij na lekcji:**
138 metrów to mniej więcej tyle, co 46-piętrowy wieżowiec! Dawniej piramida była jeszcze wyższa (ok. 146 m), ale straciła wierzchołek i gładką okładzinę z białego wapienia. Przez ok. 3800 lat była najwyższą budowlą zbudowaną przez ludzi.

Obok niej stoją dwie inne wielkie piramidy: Chefrena i Mykerinosa (zdjęcie na s. 29).

Źródło: s. 29

---

#### P13 · `krotka`
**Pytanie:** Co wyjątkowego odkryli archeolodzy w 1922 r.? Z czego wykonano maskę Tutanchamona?

**Odpowiedź:**
W **1922 r.** archeolodzy odkryli **grobowiec faraona Tutanchamona**. Był to jedyny znany grobowiec, którego nie obrabowali złodzieje. Znaleziono w nim **mnóstwo złota i kosztowności**, świadczących o bogactwie władcy starożytnego Egiptu.

Maskę Tutanchamona (XIV w. p.n.e.) wykonano **ze złota i kamieni szlachetnych**.

**Zabłyśnij na lekcji:**
Grobowiec odkrył Brytyjczyk **Howard Carter**. Sama maska waży ok. 10 kg. Tutanchamon został faraonem jako dziecko, w wieku ok. 9 lat, a zmarł młodo, mając ok. 19 lat.

Gazety pisały potem o „klątwie faraona”, która miała dotknąć odkrywców. To tylko legenda: sam Carter żył jeszcze 17 lat.

Źródło: s. 29 (tekst i podpis pod maską)

---

#### P14 · `krotka`
**Pytanie:** Pod jakimi warunkami, według egipskich wierzeń, dusza mogła trafić do krainy umarłych?

**Odpowiedź:**
Kraina umarłych była **miejscem wiecznego szczęścia**. Dusza mogła się tam dostać, jeśli:
1. **pomyślnie przeszła sąd Ozyrysa**,
2. **ciało zmarłego nie uległo rozkładowi**.

**Zabłyśnij na lekcji:**
Sposób na zapamiętanie: każdy warunek ma swoje „narzędzie”. Na ciało – **mumia**, na sąd – **Księga Umarłych**.

Źródło: s. 32, s. 33 („To, co najważniejsze”)

---

#### P15 · `wymien`
**Pytanie:** Wyjaśnij, jak Egipcjanie sporządzali mumie.

**Odpowiedź:**
1. **Usuwali wnętrzności** zmarłego.
2. **Suszyli ciało**.
3. **Bandażowali** je.
4. **Pokrywali żywicą**.
5. Mumię wkładali do **drewnianej trumny w kształcie człowieka**.
6. Trumnę zamykali w **sarkofagu**, czyli kamiennej skrzyni w kształcie trumny.

**Zabłyśnij na lekcji:**
Ciało suszono specjalną solą, zwaną natronem, przez ok. 40 dni, a całe balsamowanie trwało ok. 70 dni. Serce zostawiano w ciele, bo zmarły potrzebował go na sądzie Ozyrysa.

Źródło: s. 32 (tekst i objaśnienie z gwiazdką)

---

#### P16 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: mumia, balsamowanie, sarkofag.

**Odpowiedź:**
- **Mumia** – **ciało zmarłego zabezpieczone przed rozkładem**.
- **Balsamowanie** – **zabezpieczanie ciała przed rozkładem**.
- **Sarkofag** – **kamienna skrzynia w kształcie trumny**.

**Zabłyśnij na lekcji:**
Słowo „sarkofag” pochodzi z greki i znaczy dosłownie „zjadający ciało”. Słowo „mumia” wywodzi się z języka perskiego i arabskiego, od nazwy smoły, bo ciemne mumie kojarzyły się ludziom ze smołą.

Źródło: s. 29, s. 32

---

### Kategoria 4: `d5-zrodla` – Źródło i ilustracja

#### P17 · `zrodlo`
**Pytanie:** Przeczytaj tekst źródłowy z Księgi Umarłych (s. 32). Co zmarły mówił o sobie przed bogami? Czy nasza ocena dobra i zła jest podobna do egipskiej? Uzasadnij odpowiedź.

**body:** Podręcznik, s. 32: ramka „Tekst źródłowy”

**Odpowiedź:**
Zmarły zapewniał, że **nie krzywdził ludzi**: nie doprowadzał biednych do nędzy, nie był przyczyną głodu ani płaczu, nie zabijał i nie kazał zabijać, nikomu nie zadawał cierpienia i nie oczerniał sługi przed jego przełożonym. Zapewniał też, że **nie robił nic, czego nie lubią bogowie**, i nie umniejszał ofiar w świątyniach. Na koniec kilka razy powtarzał, że **jest czysty**.

**Czy to podobne do naszej oceny?** W dużej części **tak**: także my uważamy za złe zabijanie, zadawanie cierpienia, krzywdzenie biednych i obmawianie innych. **Różnica:** część zasad dotyczy obowiązków wobec egipskich bogów i zmarłych, np. ofiar w świątyniach czy placków dla dusz zmarłych.

To pytanie otwarte, więc liczy się dobre uzasadnienie.

**Zabłyśnij na lekcji:**
Tę część Księgi Umarłych nazywa się „wyznaniem negatywnym”, bo zmarły wylicza, czego **nie** robił. Podobne zasady, np. „nie zabijaj”, znajdziesz w Dekalogu (dział 6).

Źródło: s. 32 (tekst źródłowy i pytanie pod nim)

---

#### P18 · `obraz`
**Pytanie:** Przyjrzyj się ilustracji z Księgi Umarłych Hunefera (s. 33). Wymień bogów uczestniczących w sądzie Ozyrysa.

**body:** Podręcznik, s. 33: ilustracja sądu Ozyrysa z ponumerowanymi scenami

**Odpowiedź:**
- **Ozyrys** – siedzi na tronie i przyjmuje zmarłego do krainy umarłych,
- **14 bogów** – słuchają opowieści zmarłego i wraz z Ozyrysem wydają wyrok,
- **Anubis** – prowadzi zmarłego na sąd,
- **Tot** – zapisuje wynik sądu,
- **Horus** – prowadzi zmarłego przed tron Ozyrysa,
- **Izyda i Neftyda** – stoją za Ozyrysem.

Przy wadze czeka też **Ammit, „Pożeraczka Zmarłych”**.

**Zabłyśnij na lekcji:**
Ammit przedstawiano jako potwora złożonego z trzech groźnych zwierząt: miała głowę krokodyla, przód ciała lwa i tył hipopotama.

Źródło: s. 33 (podpisy 1–7 pod ilustracją)

---

#### P19 · `obraz`
**Pytanie:** Na ilustracji sądu Ozyrysa (s. 33) jest waga, oznaczona numerem 3. Co leżało na jej szalach i co oznaczał wynik ważenia?

**body:** Podręcznik, s. 33: ilustracja sądu Ozyrysa

**Odpowiedź:**
Na **lewej szali** leżało **serce Hunefera**, a na **prawej – strusie pióro**. Serce **lżejsze od pióra** oznaczało, że **nie jest obciążone grzechami**, więc zmarły mógł trafić do krainy umarłych. Serca **cięższe od pióra** pożerała **Ammit, „Pożeraczka Zmarłych”**. Wynik zapisywał **Tot**.

**Zabłyśnij na lekcji:**
W polszczyźnie też łączymy serce z ciężarem: mówimy „z lekkim sercem”, gdy niczym się nie martwimy, i „ciężko na sercu”, gdy coś nas gnębi.

Źródło: s. 33 (podpisy 3–5 pod ilustracją)

---

### Kategoria 5: `d5-daty` – Daty i oś czasu

#### P20 · `kolejnosc`
**Pytanie:** Ułóż wydarzenia w kolejności, od najdawniejszego do najpóźniejszego. Przydadzą się daty z działów 3 i 4!

**hint:** Klikaj wydarzenia od najdawniejszego do najpóźniejszego.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `Odkrycie grobowca Tutanchamona`
- 1: `Budowa piramidy Cheopsa`
- 2: `Egipt zostaje przyłączony do Rzymu`
- 3: `Sumerowie wynajdują pismo`
- 4: `Panowanie Tutanchamona`
- 5: `Powstanie państwa egipskiego`

**kolejnosc:** `[3, 5, 1, 4, 2, 0]`

**Odpowiedź:**
Sumerowie wynajdują pismo (ok. 3500 r. p.n.e.) → powstanie państwa egipskiego (ok. 3100 r. p.n.e.) → budowa piramidy Cheopsa (XXVI w. p.n.e.) → panowanie Tutanchamona (XIV w. p.n.e.) → Egipt częścią Rzymu (30 r. p.n.e.) → odkrycie grobowca Tutanchamona (1922 r.)

**Zabłyśnij na lekcji:**
Między pochowaniem Tutanchamona a odkryciem jego grobowca minęło ponad 3000 lat, a skarby przez cały ten czas czekały pod ziemią!

Źródło: s. 28–29; data pisma Sumerów z działu 3 (s. 19)

---

#### P21 · `policz`
**Pytanie:** Jakie lata obejmują te okresy? a) XXVI w. p.n.e., kiedy zbudowano piramidę Cheopsa; b) XIV w. p.n.e., z którego pochodzi maska Tutanchamona; c) I tysiąclecie p.n.e., z którego pochodzi mumia w drewnianej trumnie (s. 32). d) Do którego wieku należy rok 1922?

**Odpowiedź:**
- a) XXVI w. p.n.e. = lata **2600–2501 p.n.e.**
- b) XIV w. p.n.e. = lata **1400–1301 p.n.e.**
- c) I tysiąclecie p.n.e. = lata **1000–1 p.n.e.**
- d) 1922 → 19 + 1 = 20 → **XX w.**

**Zabłyśnij na lekcji:**
Przed naszą erą wiek „zaczyna się” od większej liczby: XXVI w. p.n.e. zaczął się w 2600 r. p.n.e., a skończył w 2501 r. p.n.e. To znów „odliczanie rakiety” z działu 1.

Źródło: s. 29, s. 32 (podpisy); reguły liczenia z działu 1

---

#### P22 · `policz`
**Pytanie:** Policz: a) Ile mniej więcej lat dzieli budowę piramidy Cheopsa (XXVI w. p.n.e.) od czasów Tutanchamona (XIV w. p.n.e.)? b) Ile lat minęło od odkrycia grobowca Tutanchamona (1922 r.) do 2026 r.? c) Ile co najmniej lat temu zbudowano piramidę Cheopsa?

**Odpowiedź:**
- a) 26 − 14 = 12 wieków, czyli **ok. 1200 lat**.
- b) 2026 − 1922 = **104 lata**.
- c) Najpóźniejszy rok XXVI w. p.n.e. to 2501 r. p.n.e.: 2501 + 2026 − 1 = 4526, czyli **ponad 4500 lat temu**. Odejmujemy 1, bo nie było roku 0.

**Zabłyśnij na lekcji:**
Dla Tutanchamona piramida Cheopsa była już bardzo starym zabytkiem, starszym niż dla nas czasy przed chrztem Polski (966 r.)!

Źródło: s. 29; reguły liczenia z działu 1

---

### Kategoria 6: `d5-pary` – Dopasuj i ułóż

#### P23 · `dopasuj`
**Pytanie:** Dopasuj bóstwo do jego roli.

**lewa:**
1. `Ra`
2. `Tot`
3. `Anubis`
4. `Ozyrys`
5. `Izyda`
6. `Set`

**prawa** (w tej kolejności):
- **A** – `Opiekunka rodzin, bogini magii, uzdrowicielka chorych`
- **B** – `Zły brat Ozyrysa, który go zabił i poćwiartował`
- **C** – `Bóg słońca, najważniejszy z bogów, stwórca świata`
- **D** – `Sędzia umarłych i władca ich krainy`
- **E** – `Patron mądrości, bóg pisarzy i uczonych`
- **F** – `Bóg zmarłych i opiekun grobów`

**klucz:** 1–C, 2–E, 3–F, 4–D, 5–A, 6–B → `['C','E','F','D','A','B']`

**Zabłyśnij na lekcji:**
Set był bogiem pustyni, burz i chaosu. Egipcjanie widzieli w nim przeciwieństwo Ozyrysa, który kojarzył się z życiem i urodzajem.

Źródło: s. 28–29

---

#### P24 · `dopasuj`
**Pytanie:** Dopasuj bóstwo do tego, jak je przedstawiano.

**lewa:**
1. `Ra`
2. `Tot`
3. `Anubis`
4. `Ozyrys`
5. `Izyda`

**prawa** (w tej kolejności):
- **A** – `Mężczyzna owinięty bandażami jak mumia`
- **B** – `Mężczyzna z głową szakala`
- **C** – `Kobieta z tronem na głowie`
- **D** – `Mężczyzna z głową sokoła, na której jest tarcza słoneczna`
- **E** – `Mężczyzna z głową ptaka ibisa`

**klucz:** 1–D, 2–E, 3–B, 4–A, 5–C → `['D','E','B','A','C']`

**Zabłyśnij na lekcji:**
Imię Izydy po egipsku prawdopodobnie oznaczało „tron”, dlatego przedstawiano ją z tronem na głowie.

Źródło: s. 28

---

#### P25 · `kolejnosc`
**Pytanie:** Ułóż etapy sądu Ozyrysa we właściwej kolejności. Pomoże Ci ilustracja na s. 33.

**hint:** Klikaj kolejne etapy sądu, od początku do końca.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `Tot zapisuje wynik sądu`
- 1: `Ozyrys przyjmuje zmarłego do krainy umarłych`
- 2: `Anubis prowadzi zmarłego na sąd`
- 3: `Horus prowadzi zmarłego przed tron Ozyrysa`
- 4: `Serce zmarłego zostaje zważone ze strusim piórem`

**kolejnosc:** `[2, 4, 0, 3, 1]`

**Odpowiedź:**
**Anubis prowadzi zmarłego na sąd → serce zmarłego zostaje zważone ze strusim piórem → Tot zapisuje wynik sądu → Horus prowadzi zmarłego przed tron Ozyrysa → Ozyrys przyjmuje zmarłego do krainy umarłych**

**Zabłyśnij na lekcji:**
Ilustrację w podręczniku czyta się od lewej do prawej, a numery 2, 3, 5, 6 i 7 idą w tej samej kolejności co etapy sądu.

Źródło: s. 33 (podpisy 2, 3, 5, 6, 7)

---

### Kategoria 7: `d5-pf` – Prawda czy fałsz?

#### P26 · `pf`
**Pytanie:** Które zdania są prawdziwe, a które fałszywe?

**zdania:**

| lit. | `t` (zdanie) | `p` | `fix` (wyjaśnienie po odsłonięciu) |
|---|---|---|---|
| a | Starożytni Egipcjanie wyznawali politeizm. | `true` | *(puste)* |
| b | Anubisa przedstawiano jako mężczyznę z głową sokoła. | `false` | Anubis miał **głowę szakala**. Głowę sokoła miał Ra. |
| c | Według Egipcjan Ozyrysa zabił jego zły brat Set. | `true` | *(puste)* |
| d | Sztuczną brodę nosiła nawet kobieta, gdy była faraonem. | `true` | *(puste)* |
| e | Dusza mogła trafić do krainy umarłych tylko wtedy, gdy ciało zmarłego uległo rozkładowi. | `false` | Było odwrotnie: ciało **nie mogło ulec rozkładowi**, dlatego Egipcjanie robili mumie. |
| f | W czasie sądu Ozyrysa serce zmarłego ważono ze strusim piórem. | `true` | *(puste)* |
| g | Piramidę Cheopsa zbudowano w XIV w. p.n.e. | `false` | Zbudowano ją w **XXVI w. p.n.e.** XIV w. p.n.e. to czasy Tutanchamona. |
| h | Egipcjanie grzebali zmarłych na żyznych polach nad Nilem. | `false` | Grzebali ich **na pustyni**, którą uważali za królestwo demonów i śmierci. |

**Zabłyśnij na lekcji:**
Piramida Cheopsa to jedyny z siedmiu cudów świata starożytnego, który przetrwał do dziś.

Źródło: s. 28–29, s. 32–33

---

## 5. Ściągawka (pole `sciagawka`)

**Oś czasu** (segmenty od lewej):
1. **ok. 3100 p.n.e.** – powstanie państwa egipskiego
2. **XXVI w. p.n.e.** – piramida Cheopsa
3. **XIV w. p.n.e.** – Tutanchamon
4. **30 p.n.e.** – Egipt częścią Rzymu
5. **1922** – odkrycie grobowca Tutanchamona

**Karty:**
- **☀️ Bogowie** (politeizm = wielobóstwo):
  - Ra – słońce, najważniejszy, stwórca świata (głowa sokoła),
  - Tot – mądrość, pisarze (głowa ibisa),
  - Anubis – zmarli i groby (głowa szakala),
  - Ozyrys – sędzia i władca umarłych (bandaże jak mumia),
  - Izyda – rodziny, magia, leczenie (tron na głowie),
  - Set – zły brat Ozyrysa.
- **🗝️ Dwa warunki krainy umarłych** – 1) ciało nie może ulec rozkładowi → mumie, piramidy, grobowce w skałach; 2) dusza musi przejść sąd Ozyrysa → Księga Umarłych.
- **🧻 Mumia krok po kroku** – wnętrzności → suszenie → bandaże → żywica → drewniana trumna → sarkofag.
- **⚖️ Sąd Ozyrysa** – Anubis prowadzi → serce na wadze z piórem → Tot zapisuje → Horus prowadzi → Ozyrys przyjmuje (serca cięższe od pióra pożera Ammit).
- **🔺 Piramida Cheopsa** – XXVI w. p.n.e., 138 m, 2,3 mln bloków.

---

## 6. Rangi i komunikaty maskotki dla działu 5 (pola `rangi`, `start`)

**start:** `Witaj w Egipcie! Zostaniesz archeologiem: odkryjesz bogów, piramidy i tajemnice sądu Ozyrysa. Za każde pytanie, które umiesz, przesypie się trochę mojego piasku!`

| `od` | `e` | `n` | `msg` |
|---|---|---|---|
| 0 | 🔍 | Młody archeolog | Pierwsze znalezisko! Piasek zaczął się sypać. ⏳ |
| 0.25 | 🗺️ | Tropiciel z Doliny Królów | Brawo! Zostajesz Tropicielem z Doliny Królów. |
| 0.5 | 🔺 | Badacz piramid | Ponad połowa! Badacz piramid w akcji. |
| 0.75 | 📜 | Znawca Księgi Umarłych | Znawca Księgi Umarłych! Jeszcze kilka pytań do tytułu Mistrza… |
| 1 | 🏆 | Mistrz egiptologii | MISTRZ EGIPTOLOGII! Cały piasek przesypany, cały dział opanowany! 🏆 |

---

## 7. Weryfikacja merytoryczna (do wiadomości, nie renderować)

**Co sprawdzono**
- Każda odpowiedź jest zgodna z tekstem s. 28–29 i 32–33 (strony podano przy pytaniach). Obejmują one wszystkie pytania 1–8 z czerwonych ramek, pytanie do tekstu źródłowego oraz polecenia A i B. Tabela „To, co najważniejsze” jest w całości w P4, P7, P8, P14 i w ściągawce.
- Rachunki: XXVI w. p.n.e. = 2600–2501; XIV w. p.n.e. = 1400–1301; I tysiąclecie p.n.e. = 1000–1; 1922 → XX w.; 26 − 14 = 12 wieków; 2026 − 1922 = 104; 2501 + 2026 − 1 = 4526; 1200 lat przed 2026 r. to ok. 826 r., czyli przed 966 r.; 138 m / 3 m na piętro ≈ 46 pięter; od XIV w. p.n.e. do 1922 r. minęło ponad 3000 lat.
- Klucze dopasowań i obie kolejności (P20, P25) sprawdzone pozycja po pozycji. Kolejność w P25 odpowiada numeracji 2 → 3 → 5 → 6 → 7 w podpisach do ilustracji.
- Ciekawostki („Zabłyśnij na lekcji”) wykraczają poza podręcznik i zostały sprawdzone z wiedzą ogólną.

**Uwagi do treści podręcznika**
1. **„Najwyższa kamienna budowla na Ziemi”.** Podręcznik tak opisuje piramidę Cheopsa (s. 29), ale to dziś nieprawda: kilka kamiennych katedr jest wyższych, np. katedra w Ulm (ok. 162 m) i katedra w Kolonii (ok. 157 m). Dlatego żadne pytanie ani odpowiedź nie powtarza tego sformułowania. Ciekawostka w P12 mówi poprawnie, że piramida przez ok. 3800 lat była najwyższą budowlą zbudowaną przez ludzi (zgodnie z działem 4).
2. **Grobowiec Tutanchamona** „jako jedyny nieobrabowany”. Złodzieje weszli do niego jeszcze w starożytności, ale grób ponownie zamknięto i niemal wszystkie skarby przetrwały. Odpowiedź P13 trzyma się podręcznika, a ciekawostka mu nie przeczy.
3. **Data papirusu Hunefera.** Podręcznik podaje XIV w. p.n.e., a Muzeum Brytyjskie datuje go na ok. 1275 r. p.n.e. (XIII w.). Dlatego żadne pytanie nie dotyczy wieku tego papirusu.
4. **Ważenie serca.** Podręcznik pisze, że serce Hunefera jest „lżejsze od pióra”. W wielu opracowaniach mowa o równowadze serca i pióra. Zostaje wersja z podręcznika.
5. **Tekst źródłowy z Księgi Umarłych** nie jest przepisany ani w tym pliku, ani na stronie. Odpowiedź P17 to własne streszczenie.
6. **Strony 30–31** nie zostały dostarczone. Numeracja pytań przechodzi z 4 (s. 29) do 5 (s. 32), a „To, co najważniejsze” nie odwołuje się do innych treści, więc to prawdopodobnie ilustracje. Ich ewentualna treść nie jest tu uwzględniona.
