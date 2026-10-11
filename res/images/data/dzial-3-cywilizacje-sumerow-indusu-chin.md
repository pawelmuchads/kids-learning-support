# Kapsuła Czasu – Dział 3: Cywilizacje Sumerów, doliny Indusu i Chin

Specyfikacja pytań i odpowiedzi do dopisania na stronę `kapsula-czasu-historia.html`.
Źródło: podręcznik do historii, dział 3 „Cywilizacje Sumerów, doliny Indusu i Chin”, s. 17–21 (komplet stron).

---

## 0. Instrukcja dla modelu, który dokończy stronę

### Kontekst
`kapsula-czasu-historia.html` to jednoplikowa strona (HTML + CSS + JS, bez bibliotek, tylko Google Fonts) z pytaniami do powtórki z historii dla ucznia szkoły podstawowej. Treść jest w tablicy `DZIALY` w skrypcie. Jest tam dział 1, a być może także działy 2 i 6 (osobne pliki MD o tej samej strukturze).

### Zadanie
1. Dopisz do `DZIALY` nowy dział według sekcji 1–6 tego pliku. Działy w tablicy i w zakładkach ustaw według `nr` (1, 2, 3, 6…).
2. **Jeśli strona obsługuje jeden dział** (skrypt wybiera `DZIALY.filter(...)[0]`, a zakładki nic nie robią), wprowadź najpierw zmiany z listy niżej. **Jeśli już obsługuje kilka działów**, sprawdź tylko punkt 5: typ `sortuj` musi działać dla **trzech** kategorii.
3. **Nie zmieniaj istniejących działów** ani wyglądu strony.

### Zasady merytoryczne (ważne)
- Treść pytań, odpowiedzi i ciekawostek została sprawdzona z podręcznikiem i ze źródłami wiedzy ogólnej. **Nie dopisuj nowych faktów, dat ani liczb** i nie „poprawiaj” treści.
- Zachowaj odpowiedzi zgodne z podręcznikiem, nawet jeśli znasz nowsze ustalenia (patrz sekcja 7).
- Polskie cudzysłowy „ ”, półpauza – w zakresach dat, formy neutralne płciowo.
- Nie odtwarzaj map, ilustracji ani postaci z podręcznika (prawa autorskie). Pytania o mapę i ilustrację odsyłają do stron podręcznika.

### Konwersja treści z tego pliku do pól JS
- `**tekst**` → `<b>tekst</b>`, `*tekst*` → `<i>tekst</i>`.
- Lista `-` → `<ul><li>…</li></ul>`, lista numerowana → `<ol><li>…</li></ol>`.
- Akapity → `<p>…</p>`.
- Linie „Źródło: …” są tylko do weryfikacji – **nie renderuj ich**.

### Zmiany w kodzie (jeśli jeszcze ich nie ma)
1. **Przełączanie działów.** Funkcja `render(dzId)` buduje `ALL`, `BY`, `TOTAL`, `#main`, `#chips` i stopkę dla wybranego działu i jest wywoływana po kliknięciu zakładki. Aktywny dział zapamiętaj w `location.hash` (np. `#d3`) i odtwórz go przy wczytaniu strony. Domyślnie otwiera się dział 1.
2. **Etykiety zakładek** z numerem z podręcznika: „Dział 3 Cywilizacje Sumerów, doliny Indusu i Chin”. Jeśli tytuł jest za długi na zakładkę, użyj pola `krotkiTytul: 'Sumerowie, Indus, Chiny'` (tylko na zakładce; pełny tytuł zostaje w nagłówku działu).
3. **Postęp per dział.** Pasek, ranga, klepsydra, chipy i licznik dotyczą aktywnego działu. `uid` ma prefiks `dz.id` (np. `d3-5`). Zostaw klucz `localStorage` `kapsula-czasu-v1`.
4. **Rangi i komunikaty maskotki per dział:** opcjonalne pola `rangi` i `start` w obiekcie działu (wartości w sekcji 6). Toast końcowy: „🏆 Cały dział opanowany! Zostajesz: ” + nazwa najwyższej rangi.
5. **Typy w `TYPY`** (dodaj brakujące):
   - `pojecie: '📖 Wyjaśnij pojęcie'`, `obraz: '🖼️ Praca z ilustracją'`, `mapa: '🗺️ Praca z mapą'` – renderują się jak zwykłe pytanie.
   - `sortuj: '🗂️ Przyporządkuj'` – uogólnienie typu `pf`. Pola: `q`, `kategorie` (lista nazw, **2 lub więcej**; tu 3), `elementy: [{t, k}]` (`k` = indeks w `kategorie`), `extra`, opcjonalnie `hint`.
     - Przy każdym elemencie są przyciski z nazwami kategorii. Na wąskim ekranie przyciski idą pod tekst i mogą się zawijać.
     - Po odsłonięciu odpowiedzi elementy dostają klasy `right`/`wrong`, a wynik ma postać „Dobrze przyporządkowane: x z n”.
     - Odpowiedź generuje się sama: dla każdej kategorii nagłówek i lista jej elementów.
     - Jeśli dział 2 dodał wcześniej `sortuj` z etykietą „🗂️ Paleolit czy neolit?”, zmień etykietę typu na ogólną „🗂️ Przyporządkuj” – tytuł zadania jest i tak w `q`.
6. **Podpowiedź w `kolejnosc`:** opcjonalne pole `hint` (dla P21: „Klikaj wydarzenia od najdawniejszego do najpóźniejszego.”), a placeholder `.oseq:empty::before` neutralny: „Klikaj po kolei, a pojawi się tutaj twoja kolejność”.
7. Przy zmianie działu: wyłącz filtr „Tylko do powtórki”, przewiń na górę, przelicz pasek i maskotkę.
8. **Ściągawka:** sekcja 5. Oś czasu jak w dziale 1 (`.tl`), porównanie cywilizacji jako trzy karty `.rules`.

### Kryteria gotowości
- Brak błędów w konsoli; strona działa po otwarciu z dysku (`file://`).
- Wszystkie zakładki działają, postęp każdego działu liczy się osobno i przetrwa odświeżenie strony.
- Dział 3 ma 27 pytań w 7 kategoriach, numerowane od 1.
- Dopasowania, `sortuj` (3 kategorie) i „prawda/fałsz” liczą wynik zgodnie z kluczami z tego pliku.
- Układ działa na telefonie (szerokość 390 px).

---

## 1. Metadane działu

| pole | wartość |
|---|---|
| `id` | `'d3'` |
| `nr` | `3` |
| `tytul` | `'Cywilizacje Sumerów, doliny Indusu i Chin'` |
| `krotkiTytul` | `'Sumerowie, Indus, Chiny'` |
| `zakres` | `'podręcznik s. 17–21'` |

---

## 2. Kategorie

| # | `id` | `ikona` | `nazwa` | `krotko` | `opis` | `c` | `soft` | `dark` |
|---|---|---|---|---|---|---|---|---|
| 1 | `d3-slowa` | 🗣️ | Wyjaśnij własnymi słowami | Słowami | Opowiedz pełnymi zdaniami, o co chodzi. | `#FF6B5B` | `#FFE7E2` | `#C4382A` |
| 2 | `d3-pojecia` | 📖 | Słowniczek pojęć | Pojęcia | Krótko i konkretnie: co znaczy to słowo? | `#7C5CFF` | `#EDE9FF` | `#5536D6` |
| 3 | `d3-sumer` | 🏺 | Sumerowie | Sumerowie | Pierwsza cywilizacja świata z bliska. | `#F59E0B` | `#FFEFCC` | `#9A5B00` |
| 4 | `d3-indus-chiny` | 🌏 | Dolina Indusu i Chiny | Indus i Chiny | Dwie wielkie cywilizacje Azji. | `#14A39F` | `#DBF3F1` | `#0A736F` |
| 5 | `d3-daty` | 📅 | Daty i oś czasu | Daty | Ustaw wydarzenia w kolejności i policz lata. | `#3B82F6` | `#E1EBFF` | `#1E5CC8` |
| 6 | `d3-pary` | 🔗 | Dopasuj i przyporządkuj | Dopasuj | Połącz rzeki, pojęcia i osiągnięcia z cywilizacjami. | `#E8579B` | `#FCE4EF` | `#AD2966` |
| 7 | `d3-pf` | ⚖️ | Prawda czy fałsz? | Prawda / fałsz | Zdecyduj przy każdym zdaniu. A zdania fałszywe popraw! | `#16A063` | `#DFF5E9` | `#11774A` |

---

## 3. Schemat pól pytania

| `typ` | pola |
|---|---|
| `opis`, `pojecie`, `krotka`, `policz`, `wymien`, `obraz`, `mapa` | `q`, opcjonalnie `body`, `odp`, `extra` |
| `kolejnosc` | `q`, `elementy` (kolejność wyświetlania), `kolejnosc` (indeksy w poprawnej kolejności), `odp`, `extra`, opcjonalnie `hint` |
| `dopasuj` | `q`, `lewa`, `prawa`, `klucz` (litera dla każdej pozycji z `lewa`), `extra`; odpowiedź generuje się sama |
| `sortuj` | `q`, `kategorie`, `elementy: [{t, k}]`, `extra`; odpowiedź generuje się sama |
| `pf` | `q`, `zdania: [{t, p, fix}]` (`p` = `true` dla prawdy), `extra` |

---

## 4. Pytania

### Kategoria 1: `d3-slowa` – Wyjaśnij własnymi słowami

#### P1 · `opis`
**Pytanie:** W jaki sposób powstały pierwsze społeczeństwa?

**Odpowiedź:**
Neolityczni rolnicy mieszkali we wsiach i w osadach. Z czasem stawały się one **coraz większe**, a ich mieszkańcy **nawiązywali ze sobą kontakty**.

Ludzie żyjący na jakimś obszarze nieraz **zgadzali się, by ktoś nimi kierował**. Inaczej mieszkańcy jednej wsi mogliby np. tak wykopać kanał nawadniający swoje pola, że **zabrakłoby wody dla drugiej wsi**. W ten sposób powstały pierwsze społeczeństwa.

**Zabłyśnij na lekcji:**
Przykład z kanałem pokazuje, po co ludziom władza: ktoś musi rozstrzygać spory i planować wspólne prace.

W słynnym zbiorze praw króla Hammurabiego z Babilonu (XVIII w. p.n.e.) są przepisy o tym, kto ma zapłacić, gdy przez jego zaniedbanie woda zaleje pole sąsiada.

Źródło: s. 17

---

#### P2 · `opis`
**Pytanie:** Dlaczego Sumerowie zbudowali system nawadniający i co im to dało?

**Odpowiedź:**
Bo w Mezopotamii **deszcz padał bardzo rzadko**. Sumerowie wykopali **tysiące kanałów**, którymi doprowadzali wodę do swoich pól. Dzięki nawadnianiu mieli **6 razy większe plony** niż inne ludy i wytwarzali **nadwyżkę pożywienia**.

**Zabłyśnij na lekcji:**
Nawadnianie miało też wadę. Woda parowała z pól i zostawiała w ziemi sól, więc z czasem część pól Mezopotamii stała się mniej urodzajna. Rolnicy zaczęli wtedy częściej siać jęczmień, który lepiej znosi zasoloną glebę niż pszenica.

Źródło: s. 18

---

#### P3 · `opis`
**Pytanie:** Co się zmieniło w Mezopotamii, gdy Sumerowie zaczęli wytwarzać nadwyżkę pożywienia? Jakie to miało znaczenie dla ich cywilizacji?

**Odpowiedź:**
Nadwyżka pożywienia to więcej jedzenia, niż ludzie potrzebowali. Dzięki niej:
1. **Podział pracy.** Niektórzy Sumerowie mogli zrezygnować z rolnictwa i zająć się tylko rzemiosłem, np. wyrobem narzędzi. Tak dokonał się pierwszy podział pracy: między rolników i rzemieślników.
2. **Pierwsze miasta.** Rzemieślnicy osiedlali się blisko siebie, bo w jednym miejscu łatwiej mogli kupić surowce i sprzedać swoje wyroby. Wsie przekształcały się w miasta.
3. **Miasta-państwa.** Większe miasta stały się miastami-państwami, którymi rządzili królowie.

**Zabłyśnij na lekcji:**
Rzemieślnik nie uprawiał pola, więc jedzenie musiał od rolnika kupić albo wymienić, np. na narzędzia czy naczynia. Gdyby rolnicy nie mieli nadwyżki, nie mieliby czego oddać, a rzemieślnik nie miałby z czego żyć.

Źródło: s. 18–19, s. 21 (polecenie B, „To, co najważniejsze”)

---

#### P4 · `opis`
**Pytanie:** Czym się różni społeczeństwo od cywilizacji?

**Odpowiedź:**
- **Społeczeństwo** to duża grupa ludzi, którzy mieszkają na dużym terenie, podlegają tej samej władzy, czują łączność między sobą i dostrzegają różnice między swoim społeczeństwem a innymi.
- **Cywilizacja** to **poziom rozwoju** społeczeństwa: takiego, które mieszka w osadach albo miastach, zna rolnictwo i rzemiosło oraz **używa pisma**.

Czyli każda cywilizacja to społeczeństwo, ale nie każde społeczeństwo osiągnęło poziom cywilizacji, np. jeśli nie używa pisma.

**Zabłyśnij na lekcji:**
Łatwy sposób na zapamiętanie: społeczeństwo to ludzie, a cywilizacja to poziom, na który ci ludzie się wspięli. Wspięli się, gdy mają osady lub miasta, rolnictwo z rzemiosłem i pismo.

Źródło: s. 17, s. 21 (polecenie A)

---

#### P5 · `wymien`
**Pytanie:** Przedstaw wspólne cechy najstarszych cywilizacji świata.

**Odpowiedź:**
1. Powstały **nad rzekami nawadniającymi pola**: Tygrysem i Eufratem, Nilem, Indusem i Huang-ho.
2. Utworzyły je społeczeństwa, które wytwarzały **nadwyżkę pożywienia**, czyli miały go więcej, niż potrzebowały.

Poza tym, jak każda cywilizacja, ich mieszkańcy żyli w osadach albo miastach, znali rolnictwo i rzemiosło oraz używali pisma.

**Zabłyśnij na lekcji:**
Dlatego najstarsze cywilizacje nazywa się często **cywilizacjami rzecznymi**. Rzeki dawały wodę do nawadniania, a podczas wylewów użyźniały pola mułem.

Źródło: s. 18 (tekst), s. 21 (mapa, polecenie C)

---

#### P6 · `opis`
**Pytanie:** Jak powstały pierwsze miasta? Czym miasto różni się od wsi?

**Odpowiedź:**
Rzemieślnicy **osiedlali się blisko siebie**, bo w jednym miejscu **łatwiej mogli kupić surowce i sprzedać swoje wyroby**. Tak powstały pierwsze miasta.

Miasto różni się od wsi tym, że jego mieszkańcy utrzymują się przede wszystkim **z rzemiosła i usług** (np. medycznych, prawnych), **a nie z rolnictwa**.

**Zabłyśnij na lekcji:**
Jednym z najstarszych wielkich miast świata był sumeryjski **Uruk**, w którym ok. 3000 r. p.n.e. mieszkało kilkadziesiąt tysięcy ludzi. Na mapie na s. 21 widać inne miasto Sumerów, **Ur**. Według Biblii stamtąd pochodził Abraham (dział 6).

Źródło: s. 18

---

### Kategoria 2: `d3-pojecia` – Słowniczek pojęć

#### P7 · `pojecie`
**Pytanie:** Co to jest społeczeństwo? Wymień jego cztery cechy.

**Odpowiedź:**
Społeczeństwo to **duża grupa ludzi**, którzy:
1. **mieszkają na dużym terenie** (np. w Egipcie),
2. **podlegają tej samej władzy** (np. królowi),
3. **czują łączność między sobą** (np. mówią tym samym językiem, podobnie pracują i spędzają czas wolny),
4. **dostrzegają różnice** między swoim społeczeństwem a innymi.

**Zabłyśnij na lekcji:**
Te cechy pasują też do nas: mieszkamy w Polsce, podlegamy tej samej władzy, mówimy po polsku i wiemy, czym różnimy się np. od naszych sąsiadów.

Źródło: s. 17

---

#### P8 · `pojecie`
**Pytanie:** Wyjaśnij pojęcie: cywilizacja.

**Odpowiedź:**
Cywilizacja to **poziom rozwoju społeczeństwa**, które:
1. **mieszka w osadach albo miastach**,
2. **zna rolnictwo i rzemiosło**,
3. **używa pisma**.

**Zabłyśnij na lekcji:**
Słowo „cywilizacja” pochodzi od łacińskiego *civis*, czyli obywatel, mieszkaniec miasta. Z cech cywilizacji najważniejsze dla historyków jest pismo, bo od jego wynalezienia zaczyna się historia (dział 1).

Źródło: s. 17, s. 21

---

#### P9 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: Mezopotamia, Żyzny Półksiężyc.

**Odpowiedź:**
- **Mezopotamia**, inaczej **Międzyrzecze**, to kraina na Bliskim Wschodzie leżąca **między dwiema rzekami: Tygrysem i Eufratem** (a także wokół nich).
- **Żyzny Półksiężyc** to **obszary uprawne w kształcie półksiężyca**, które ciągną się **od Mezopotamii do Palestyny**. Powstało tam i upadło wiele starożytnych cywilizacji.

**Zabłyśnij na lekcji:**
„Mezopotamia” to po grecku „kraj między rzekami” (*mesos* – środkowy, *potamos* – rzeka). Polska nazwa „Międzyrzecze” znaczy dokładnie to samo. Dziś większa część Mezopotamii leży w Iraku (zdjęcie Eufratu na s. 17).

Źródło: s. 17–18

---

#### P10 · `pojecie`
**Pytanie:** Wytłumacz, czym były miasta-państwa. Kto nimi rządził?

**Odpowiedź:**
Miasta-państwa to **starożytne państewka, które obejmowały miasto wraz z okolicą**. Stawały się nimi większe miasta Sumerów. Sumeryjskimi miastami-państwami **rządzili królowie**.

**Zabłyśnij na lekcji:**
Sumeryjskimi miastami-państwami były np. Ur, Uruk i Lagasz. Król Eannatum, którego żołnierzy widać na płaskorzeźbie na s. 18, rządził Lagaszem. Miasta-państwa często walczyły między sobą, np. o pola i wodę przy granicy.

Źródło: s. 19

---

### Kategoria 3: `d3-sumer` – Sumerowie

#### P11 · `wymien`
**Pytanie:** Przedstaw główne osiągnięcia Sumerów.

**Odpowiedź:**
Sumerowie jako pierwsi w dziejach:
1. **ok. 3500 r. p.n.e. wynaleźli pismo** – wraz z tym wynalazkiem skończyła się prehistoria, a zaczęła się historia,
2. **zbudowali koło i pierwsze wozy**,
3. **wynaleźli szkło** (choć nie znali szyb),
4. **uzyskali brąz** (ok. 2500 r. p.n.e.).

Do ich osiągnięć należą też **system nawadniający pola** (dzięki niemu mieli nadwyżkę pożywienia) i **utworzenie miast-państw**.

**Zabłyśnij na lekcji:**
Koło pojawiło się mniej więcej w tym samym czasie w kilku miejscach świata. Jedno z najstarszych znanych przedstawień wozu na kołach znaleziono w Polsce, na glinianym dzbanie z Bronocic (ok. 3500 r. p.n.e.).

Źródło: s. 19, s. 21 („To, co najważniejsze”)

---

#### P12 · `krotka`
**Pytanie:** Jak pisali Sumerowie? Jak nazywamy ich pismo?

**Odpowiedź:**
Sumerowie **nie znali papieru**. Znaki pisma **ryli trzciną na tabliczkach z miękkiej gliny**, a potem **wypalali tabliczki**, żeby glina stwardniała. Ich pismo nazywamy **pismem klinowym**.

**Zabłyśnij na lekcji:**
Znaki miały kształt małych klinów, bo zaostrzoną trzcinę wciskano w glinę ukośnie. Tabliczka na s. 19 opisuje kupno ziemi przez niejakiego Tuppsikkę, więc to coś jak dzisiejszy dokument u notariusza!

Pismem klinowym przez prawie 3000 lat pisały też inne ludy Bliskiego Wschodu, np. Babilończycy i Persowie.

Źródło: s. 19 (dymek postaci, podpis pod tabliczką)

---

#### P13 · `krotka`
**Pytanie:** Co to jest brąz? Kiedy Sumerowie go uzyskali i do czego służył?

**Odpowiedź:**
Brąz to **stop miedzi z cyną**. Sumerowie uzyskali go **ok. 2500 r. p.n.e.** Nadawał się do **wyrobu narzędzi i broni**. Wynalazek brązu **zakończył młodszą epokę kamienną**.

**Zabłyśnij na lekcji:**
Stop to mieszanina metali stopionych razem. Brąz jest twardszy od samej miedzi. Z brązu do dziś odlewa się dzwony i pomniki, a medal za trzecie miejsce to „brązowy medal”.

Źródło: s. 19

---

#### P14 · `obraz`
**Pytanie:** Przyjrzyj się płaskorzeźbie z XXV w. p.n.e. Jak byli ubrani i uzbrojeni żołnierze sumeryjskiego króla Eannatuma?

**body:** Podręcznik, s. 18: płaskorzeźba z żołnierzami króla Eannatuma

**Odpowiedź:**
Żołnierze byli ubrani w **spódniczki z owczej skóry**, na głowach mieli **miedziane hełmy**, a w rękach **włócznie i topory**.

**Zabłyśnij na lekcji:**
Płaskorzeźba to rzeźba, która tylko trochę wystaje z płaskiej powierzchni. Ta pochodzi z tzw. **Steli Sępów**, która upamiętnia zwycięstwo Lagaszu nad sąsiednim miastem-państwem Umma. Można ją oglądać w Luwrze w Paryżu.

Źródło: s. 18 (podpis pod płaskorzeźbą)

---

#### P15 · `krotka`
**Pytanie:** Kiedy upadła cywilizacja Sumerów i co po niej zostało?

**Odpowiedź:**
**Ok. 2000 r. p.n.e.** cywilizację Sumerów **zniszczyły inne ludy**. Jej **osiągnięcia zostały jednak wykorzystane przez następne cywilizacje**.

**Zabłyśnij na lekcji:**
Język sumeryjski przestał być używany na co dzień, ale jeszcze bardzo długo uczono się go w szkołach pisarzy. Było to trochę tak, jak w średniowiecznej Europie uczono się łaciny.

Źródło: s. 19

---

### Kategoria 4: `d3-indus-chiny` – Dolina Indusu i Chiny

#### P16 · `krotka`
**Pytanie:** Gdzie i kiedy powstała cywilizacja doliny Indusu? Wymień dzisiejsze państwa, na których terenie się rozwijała.

**Odpowiedź:**
Powstała **w drugiej połowie IV tysiąclecia p.n.e.** w dolinie rzeki **Indus**, na terenie dzisiejszych **Indii i Pakistanu**. Największą świetność osiągnęła w latach **ok. 2500 – ok. 1800 p.n.e.** Potem zniszczyły ją inne ludy.

**Zabłyśnij na lekcji:**
Od rzeki Indus pochodzi nazwa całych Indii. Dziś większa część doliny Indusu leży w Pakistanie. Na mapie na s. 21 widać dwa wielkie miasta tej cywilizacji: Harappę i Mohendżo Daro.

Źródło: s. 19–20

---

#### P17 · `krotka`
**Pytanie:** Czym się odznaczała cywilizacja doliny Indusu?

**Odpowiedź:**
- Mieszkańcy zajmowali się **rolnictwem, rzemiosłem i handlem** (także z Mezopotamią).
- Budowali **domy z wypalanych cegieł**.
- Mieli **prywatne łazienki i rury kanalizacyjne**, którymi spływały nieczystości.
- Wytwarzali **narzędzia z brązu**.
- Znali **pismo, którego uczonym nie udało się jeszcze odczytać**.

Jednym z największych miast było **Mohendżo Daro**, w którym ludzie mieszkali przez ponad 600 lat.

**Zabłyśnij na lekcji:**
Znamy kilkaset różnych znaków pisma doliny Indusu, ale zachowane napisy są bardzo krótkie. To jeden z powodów, dla których nikt ich jeszcze nie odczytał. Może kiedyś zrobisz to Ty?

Źródło: s. 19–20

---

#### P18 · `krotka`
**Pytanie:** Gdzie i kiedy powstała cywilizacja chińska? Czym zajmowali się najdawniejsi Chińczycy?

**Odpowiedź:**
Powstała **ok. 1700 r. p.n.e.** nad rzeką **Huang-ho, czyli Żółtą Rzeką**. Najdawniejsi Chińczycy zajmowali się **rolnictwem i rzemiosłem**: wytwarzali piękne **przedmioty z brązu** oraz **wyroby ceramiczne, które nie miały sobie równych na świecie**. Wynaleźli też **pismo obrazkowe**.

**Zabłyśnij na lekcji:**
Żółta Rzeka zawdzięcza nazwę żółtemu mułowi, który niesie jej woda. Jej powodzie bywały tak groźne, że nazywano ją „smutkiem Chin”.

Znacznie później Chińczycy wynaleźli porcelanę. Po angielsku porcelanę nazywa się po prostu *china*!

Źródło: s. 20

---

#### P19 · `krotka`
**Pytanie:** Przedstaw elementy starożytnej cywilizacji chińskiej, które przetrwały do dziś.

**Odpowiedź:**
- **Pismo**, które przeszło wiele zmian, ale **nadal jest używane**.
- **Język chiński**.
- **Państwo chińskie**: Chiny zostały zjednoczone **w III w. p.n.e.** i od tego czasu wciąż istnieje państwo chińskie, więc jest ono **najstarszym państwem świata**.

**Zabłyśnij na lekcji:**
Żeby swobodnie czytać chińską gazetę, trzeba znać ok. 3000 znaków. Językiem chińskim jako ojczystym mówi więcej ludzi niż jakimkolwiek innym językiem na świecie.

Źródło: s. 20

---

#### P20 · `krotka`
**Pytanie:** Do czego służył Wielki Mur Chiński? Kiedy go budowano i jaką ma długość?

**Odpowiedź:**
Bronił **północnej granicy Chin**. Chińczycy zbudowali go **w III w. p.n.e.**, a potem **aż do XVII w.** powiększali go i przebudowywali. Łączna długość wszystkich umocnień to **ponad 20 tysięcy kilometrów**.

**Zabłyśnij na lekcji:**
20 tysięcy kilometrów to ponad połowa obwodu Ziemi (ok. 40 tysięcy km)!

Popularny mit głosi, że Wielki Mur widać gołym okiem z Księżyca. To nieprawda, bo mur jest na to o wiele za wąski.

Źródło: s. 20 (podpis pod zdjęciem)

---

### Kategoria 5: `d3-daty` – Daty i oś czasu

#### P21 · `kolejnosc`
**Pytanie:** Ułóż wydarzenia w kolejności, od najdawniejszego do najpóźniejszego.

**hint:** Klikaj wydarzenia od najdawniejszego do najpóźniejszego.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `Sumerowie uzyskują brąz`
- 1: `Powstaje cywilizacja chińska`
- 2: `Sumerowie osiedlają się w Mezopotamii`
- 3: `Chiny zostają zjednoczone`
- 4: `Upadek cywilizacji Sumerów`
- 5: `Sumerowie wynajdują pismo`
- 6: `Koniec świetności cywilizacji doliny Indusu`

**kolejnosc:** `[2, 5, 0, 4, 6, 1, 3]`

**Odpowiedź:**
Sumerowie osiedlają się w Mezopotamii (po 4000 r. p.n.e.) → wynajdują pismo (ok. 3500 r. p.n.e.) → uzyskują brąz (ok. 2500 r. p.n.e.) → upadek cywilizacji Sumerów (ok. 2000 r. p.n.e.) → koniec świetności cywilizacji doliny Indusu (ok. 1800 r. p.n.e.) → powstaje cywilizacja chińska (ok. 1700 r. p.n.e.) → Chiny zostają zjednoczone (III w. p.n.e.)

**Zabłyśnij na lekcji:**
Zauważ: gdy powstawała cywilizacja chińska, Sumerów już od ok. 300 lat nie było! Najstarsze cywilizacje nie istniały wszystkie jednocześnie.

Źródło: s. 17 (oś czasu), s. 19–20

---

#### P22 · `policz`
**Pytanie:** Liczymy tysiąclecia i wieki p.n.e. a) Jakie lata obejmuje IV tysiąclecie p.n.e., a jakie jego druga połowa, kiedy powstała cywilizacja doliny Indusu? b) Tabliczka z pismem klinowym pochodzi z XXIV–XXII w. p.n.e. Jakie to lata i które to tysiąclecie?

**Odpowiedź:**
- a) IV tysiąclecie p.n.e. to lata **4000–3001 p.n.e.** Jego druga połowa to lata **3500–3001 p.n.e.** Przed naszą erą pierwsza połowa jest tą wcześniejszą (4000–3501 p.n.e.), tak samo jak przy wiekach.
- b) XXIV w. p.n.e. to lata 2400–2301 p.n.e., a XXII w. p.n.e. to lata 2200–2101 p.n.e. Tabliczka pochodzi więc z lat **2400–2101 p.n.e.**, czyli z **III tysiąclecia p.n.e.** (3000–2001 p.n.e.).

**Zabłyśnij na lekcji:**
Tysiąclecia liczymy jak wieki, tylko skreślamy trzy ostatnie cyfry i dodajemy 1. Na przykład 1700 r. p.n.e. → 1 + 1 = **II tysiąclecie p.n.e.** Wyjątek jak przy wiekach: rok 3000 p.n.e. należy do III tysiąclecia, bo kończy się trzema zerami.

W dziale 1 była tabliczka Sumerów z III tysiąclecia p.n.e., czyli z tego samego czasu!

Źródło: s. 19 (tekst i podpis pod tabliczką); reguły liczenia z działu 1

---

#### P23 · `policz`
**Pytanie:** Policz: a) Ile lat mniej więcej istniała cywilizacja Sumerów, od ok. 4000 do ok. 2000 r. p.n.e.? b) Ile lat trwała świetność cywilizacji doliny Indusu? c) Ile lat temu Sumerowie wynaleźli pismo, jeśli liczymy do 2026 r.?

**Odpowiedź:**
- a) 4000 − 2000 = **ok. 2000 lat**.
- b) 2500 − 1800 = **ok. 700 lat**.
- c) 3500 + 2026 − 1 = 5525, czyli **ok. 5500 lat temu**. Odejmujemy 1, bo nie było roku 0.

**Zabłyśnij na lekcji:**
Cywilizacja Sumerów trwała ok. 2000 lat, czyli mniej więcej tyle, ile minęło od początku naszej ery do dziś!

Źródło: s. 17–19, s. 21 („To, co najważniejsze”)

---

### Kategoria 6: `d3-pary` – Dopasuj i przyporządkuj

#### P24 · `dopasuj`
**Pytanie:** Dopasuj cywilizację do rzeki, nad którą powstała. Sprawdź na mapie „Najstarsze cywilizacje świata” (s. 21).

**lewa:**
1. `Cywilizacja Sumerów`
2. `Cywilizacja Egiptu`
3. `Cywilizacja doliny Indusu`
4. `Cywilizacja chińska`

**prawa** (w tej kolejności):
- **A** – `Huang-ho (Żółta Rzeka)`
- **B** – `Nil`
- **C** – `Tygrys i Eufrat`
- **D** – `Indus`

**klucz:** 1–C, 2–B, 3–D, 4–A → `['C','B','D','A']`

**Zabłyśnij na lekcji:**
O cywilizacji Egiptu dowiesz się więcej w kolejnym dziale. Na razie zapamiętaj, że i ona powstała nad wielką rzeką, a każda z najstarszych cywilizacji miała swoją rzekę.

Źródło: s. 17–21 (tekst i mapa)

---

#### P25 · `sortuj`
**Pytanie:** Która to cywilizacja? Przyporządkuj każdą cechę do właściwej cywilizacji.

**hint:** Przy każdej cesze wybierz cywilizację.

**kategorie:** `['Sumerowie', 'Dolina Indusu', 'Chiny']` (indeks 0 = Sumerowie, 1 = Dolina Indusu, 2 = Chiny)

**elementy** (w tej kolejności wyświetlania):

| # | `t` | `k` |
|---|---|---|
| 1 | Prywatne łazienki i rury kanalizacyjne | 1 (Dolina Indusu) |
| 2 | Pismo klinowe ryte trzciną na glinianych tabliczkach | 0 (Sumerowie) |
| 3 | Pismo obrazkowe, które po wielu zmianach jest używane do dziś | 2 (Chiny) |
| 4 | Pismo, którego uczeni wciąż nie potrafią odczytać | 1 (Dolina Indusu) |
| 5 | Tysiące kanałów nawadniających pola | 0 (Sumerowie) |
| 6 | Wielki Mur | 2 (Chiny) |
| 7 | Miasto Mohendżo Daro | 1 (Dolina Indusu) |
| 8 | Pierwsze wozy na kołach | 0 (Sumerowie) |
| 9 | Cywilizacja nad Żółtą Rzeką | 2 (Chiny) |
| 10 | Wynalezienie szkła | 0 (Sumerowie) |
| 11 | Handel z Mezopotamią | 1 (Dolina Indusu) |
| 12 | Ceramika, która nie miała sobie równych na świecie | 2 (Chiny) |

**Zabłyśnij na lekcji:**
Przedmioty z brązu wytwarzano we wszystkich trzech cywilizacjach, dlatego nie ma ich na tej liście. Do sprawdzianu najlepiej zapamiętać to, co wyróżnia każdą z nich.

Źródło: s. 18–21

---

#### P26 · `dopasuj`
**Pytanie:** Dopasuj pojęcie do znaczenia.

**lewa:**
1. `nadwyżka pożywienia`
2. `podział pracy`
3. `miasto`
4. `miasto-państwo`
5. `Żyzny Półksiężyc`

**prawa** (w tej kolejności):
- **A** – `Starożytne państewko obejmujące miasto wraz z okolicą`
- **B** – `Obszary uprawne w kształcie półksiężyca, od Mezopotamii do Palestyny`
- **C** – `Więcej pożywienia, niż ludzie potrzebują`
- **D** – `Osada, której mieszkańcy utrzymują się głównie z rzemiosła i usług, a nie z rolnictwa`
- **E** – `Sytuacja, w której jedni zajmują się rolnictwem, a inni rzemiosłem`

**klucz:** 1–C, 2–E, 3–D, 4–A, 5–B → `['C','E','D','A','B']`

**Zabłyśnij na lekcji:**
Podział pracy trwa do dziś i jest coraz drobniejszy: piekarz, lekarz, kierowca, programistka… Nikt nie robi wszystkiego sam, i to właśnie zaczęło się u Sumerów.

Źródło: s. 18–19

---

### Kategoria 7: `d3-pf` – Prawda czy fałsz?

#### P27 · `pf`
**Pytanie:** Które zdania są prawdziwe, a które fałszywe?

**zdania:**

| lit. | `t` (zdanie) | `p` | `fix` (wyjaśnienie po odsłonięciu) |
|---|---|---|---|
| a | Mezopotamia leży między Tygrysem a Eufratem. | `true` | *(puste)* |
| b | Sumerowie pisali atramentem na papierze. | `false` | Nie znali papieru: **ryli znaki trzciną na tabliczkach z miękkiej gliny**, a potem je wypalali. |
| c | Brąz to stop miedzi z cyną. | `true` | *(puste)* |
| d | Sumerowie wynaleźli szkło i robili z niego szyby w oknach. | `false` | Wynaleźli szkło, ale **nie znali szyb**. |
| e | Uczeni odczytali już pismo cywilizacji doliny Indusu. | `false` | **Nie udało się go jeszcze odczytać**. |
| f | Cywilizacja chińska powstała nad rzeką Huang-ho, czyli Żółtą Rzeką. | `true` | *(puste)* |
| g | Każde społeczeństwo jest cywilizacją. | `false` | Cywilizacja to **poziom rozwoju** społeczeństwa, które mieszka w osadach albo miastach, zna rolnictwo i rzemiosło oraz **używa pisma**. |
| h | Państwo chińskie istnieje od III w. p.n.e., dlatego nazywa się je najstarszym państwem świata. | `true` | *(puste)* |

**Zabłyśnij na lekcji:**
Chińczycy nazywają swój kraj *Zhongguo*, co znaczy „Państwo Środka”.

Źródło: s. 17–20

---

## 5. Ściągawka (pole `sciagawka`)

**Oś czasu** (segmenty od lewej):
1. **po 4000 p.n.e.** – Sumerowie osiedlają się w Mezopotamii
2. **ok. 3500 p.n.e.** – Sumerowie wynajdują pismo, koniec prehistorii
3. **ok. 2500 – ok. 1800 p.n.e.** – świetność cywilizacji doliny Indusu
4. **ok. 2000 p.n.e.** – upadek cywilizacji Sumerów
5. **ok. 1700 p.n.e.** – początki cywilizacji chińskiej

**Karty z definicjami:**
- **👥 Społeczeństwo** – duża grupa ludzi: wspólny teren, wspólna władza, poczucie łączności, dostrzeganie różnic wobec innych.
- **🏛️ Cywilizacja** – poziom rozwoju społeczeństwa: osady lub miasta + rolnictwo i rzemiosło + pismo.
- **🌊 Wspólne cechy najstarszych cywilizacji** – powstały nad rzekami nawadniającymi pola i wytwarzały nadwyżkę pożywienia.

**Trzy karty cywilizacji:**

| | Sumerowie | Dolina Indusu | Chiny |
|---|---|---|---|
| Kiedy | od początku IV tysiąclecia do ok. 2000 p.n.e. | świetność ok. 2500 – ok. 1800 p.n.e. | od ok. 1700 p.n.e.; państwo zjednoczone od III w. p.n.e. |
| Gdzie | Mezopotamia (Tygrys i Eufrat) | dzisiejsze Indie i Pakistan (Indus) | nad Huang-ho (Żółtą Rzeką) |
| Najważniejsze | nawadnianie i nadwyżka pożywienia → podział pracy → miasta → miasta-państwa; pismo klinowe, koło i wozy, szkło, brąz | domy z wypalanych cegieł, łazienki i kanalizacja, brąz, nieodczytane pismo | brąz, ceramika, pismo obrazkowe używane do dziś |

---

## 6. Rangi i komunikaty maskotki dla działu 3 (pola `rangi`, `start`)

**start:** `Witaj w Mezopotamii! Zaczynamy od pierwszych miast, a skończymy nad Żółtą Rzeką. Za każde pytanie, które umiesz, przesypie się trochę mojego piasku!`

| `od` | `e` | `n` | `msg` |
|---|---|---|---|
| 0 | 🌾 | Rolnik znad Eufratu | Pierwsze pole nawodnione! Piasek zaczął się sypać. ⏳ |
| 0.25 | 🌊 | Budowniczy kanałów | Brawo! Zostajesz Budowniczym Kanałów. |
| 0.5 | 📜 | Pisarz glinianych tabliczek | Ponad połowa za Tobą! Trzcina w dłoń i piszemy dalej. |
| 0.75 | 👑 | Król miasta-państwa | Król miasta-państwa! Jeszcze kilka pytań do tytułu Mistrza… |
| 1 | 🏆 | Mistrz pierwszych cywilizacji | MISTRZ PIERWSZYCH CYWILIZACJI! Cały piasek przesypany, cały dział opanowany! 🏆 |

---

## 7. Weryfikacja merytoryczna (do wiadomości, nie renderować)

**Co sprawdzono**
- Każda odpowiedź jest zgodna z tekstem s. 17–21 (strony podano przy pytaniach). Obejmują one wszystkie pytania 1–10 z czerwonych ramek oraz polecenia A, B i C z „Pytań i poleceń”. Polecenie z mapy na s. 21 (rzeki) jest w P24 i P5. Tabela „To, co najważniejsze” jest w całości w P11, P16–P19 i w ściągawce.
- Rachunki: 4000 − 2000 = 2000; 2500 − 1800 = 700; 3500 + 2026 − 1 = 5525; zakresy: IV tysiąclecie p.n.e. 4000–3001, jego druga połowa 3500–3001, XXIV w. p.n.e. 2400–2301, XXII w. p.n.e. 2200–2101, III tysiąclecie p.n.e. 3000–2001; 1700 r. p.n.e. → II tysiąclecie p.n.e.; ok. 2000 − ok. 1700 = ok. 300 lat między upadkiem Sumerów a początkiem cywilizacji chińskiej.
- Klucze dopasowań, kolejność w P21 i przyporządkowania w P25 sprawdzone pozycja po pozycji.
- Ciekawostki („Zabłyśnij na lekcji”) wykraczają poza podręcznik i zostały sprawdzone z wiedzą ogólną.

**Uwagi do treści podręcznika**
1. **Upadek cywilizacji doliny Indusu.** Podręcznik: „zniszczyły ją inne ludy”. Współczesne badania wskazują raczej na zmiany klimatu i zmiany biegu rzek, a sprawa jest dyskutowana. Odpowiedzi trzymają się podręcznika, bez komentarza na stronie.
2. **Koło.** Podręcznik: Sumerowie „jako pierwsi w dziejach” zbudowali koło. Najstarsze ślady koła pochodzą z podobnego czasu z kilku miejsc (Mezopotamia, Europa). Ciekawostka w P11 mówi o tym ostrożnie (dzban z Bronocic), a odpowiedź zostaje zgodna z podręcznikiem.
3. **„Najstarsze państwo świata”** (Chiny) to uproszczenie podręcznika, bo w dziejach Chin były okresy rozbicia. Zdanie h w P27 i odpowiedź P19 trzymają się podręcznika.
4. **Koniec młodszej epoki kamiennej.** Dział 3 (s. 19) i dział 2 (s. 15) zgodnie łączą go z brązem ok. 2500 r. p.n.e. Oś epok w dziale 1 (s. 9) kończy młodszą epokę kamienną ok. 3500 r. p.n.e., razem z początkiem historii. Celowo nie ma tu pytania „prawda/fałsz” o tym, co zakończyło młodszą epokę kamienną. Nie dodawaj pytań, które zestawiają te daty.
5. **Egipt** jest na mapie i w definicji pierwszych cywilizacji, ale opisuje go kolejny dział. Tu pojawia się tylko w dopasowaniu cywilizacji do rzeki (P24).
