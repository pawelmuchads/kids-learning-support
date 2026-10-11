# Kapsuła Czasu – Dział 6: Starożytny Izrael

Specyfikacja pytań i odpowiedzi do dopisania na stronę `kapsula-czasu-historia.html`.
Źródło: podręcznik do historii, dział 6 „Starożytny Izrael”, s. 34–37.

---

## 0. Instrukcja dla modelu, który dokończy stronę

### Kontekst
`kapsula-czasu-historia.html` to jednoplikowa strona (HTML + CSS + JS, bez bibliotek, tylko Google Fonts) z pytaniami do powtórki z historii dla ucznia szkoły podstawowej. Treść jest w tablicy `DZIALY` w skrypcie. Obecnie jest w niej dział 1 „Czas w historii” oraz zablokowany placeholder `{ id:'d2', nr:2, tytul:'Następny dział', locked:true }`.

### Zadanie
1. Dopisz do `DZIALY` nowy dział według sekcji 1–5 tego pliku. Placeholder `d2` zastąp tym działem (opcjonalnie dodaj na końcu nowy placeholder `locked:true` „Kolejny dział”).
2. Wprowadź zmiany w kodzie opisane niżej, żeby strona obsługiwała więcej niż jeden dział.
3. **Nie zmieniaj działu 1** ani wyglądu strony.

### Zasady merytoryczne (ważne)
- Treść pytań, odpowiedzi i ciekawostek została sprawdzona z podręcznikiem i ze źródłami wiedzy ogólnej. **Nie dopisuj nowych faktów, dat ani liczb** i nie „poprawiaj” treści.
- Zachowaj zwroty „według Biblii”, „wierzą”, „według judaizmu”. Strona opisuje wierzenia neutralnie i nie może ich podawać jako faktów naukowych ani ich oceniać.
- Zachowaj pisownię: **żydzi** (wyznawcy judaizmu) małą literą, **Żydzi** (naród) wielką. To rozróżnienie jest celowe (pytanie P10).
- Polskie cudzysłowy „ ”, półpauza – w zakresach dat, formy neutralne płciowo (bez „umiałeś/umiałaś”).
- Nie odtwarzaj na stronie mapy, ilustracji ani postaci z podręcznika (prawa autorskie). Pytania o mapę odsyłają do mapy na s. 36.

### Konwersja treści z tego pliku do pól JS
- `**tekst**` → `<b>tekst</b>`, `*tekst*` → `<i>tekst</i>`.
- Lista `-` → `<ul><li>…</li></ul>`, lista numerowana → `<ol><li>…</li></ol>`.
- Akapity → `<p>…</p>` (tak jak w dziale 1).
- Linie „Źródło: …” są tylko do weryfikacji – **nie renderuj ich**.

### Wymagane zmiany w kodzie
1. **Przełączanie działów.** Obecnie skrypt wybiera tylko pierwszy odblokowany dział (`var dz=DZIALY.filter(...)[0]`) i raz buduje `ALL`, `BY`, `TOTAL`, `#main`, `#chips` i stopkę. Przenieś to do funkcji `render(dzId)`, wywoływanej po kliknięciu zakładki. Aktywny dział zapamiętaj w `location.hash` (np. `#d6`) i odtwórz go przy wczytaniu strony. Domyślnie otwiera się dział 1.
2. **Etykiety zakładek** używają numeru z podręcznika: „Dział 1 Czas w historii”, „Dział 6 Starożytny Izrael”.
3. **Postęp per dział.** Pasek, ranga, klepsydra, chipy i licznik dotyczą aktywnego działu. `uid` pytań już ma prefiks `dz.id` (np. `d6-3`), więc zostaw klucz `localStorage` `kapsula-czasu-v1` – postęp działu 1 nie zginie.
4. **Rangi i komunikaty maskotki per dział.** `RANGI`, `START` oraz tekst toastu przy ukończeniu działu („Zostajesz Mistrzem Chronologii!” w `setMark`) są teraz na sztywno pod dział 1. Dodaj do obiektu działu opcjonalne pola `rangi` i `start` (dział 1 dostaje obecne wartości, dział 6 – wartości z sekcji 6). Toast końcowy: „🏆 Cały dział opanowany! Zostajesz: ” + nazwa najwyższej rangi.
5. **Nowe typy pytań** w `TYPY`: `pojecie: '📖 Wyjaśnij pojęcie'` oraz `mapa: '🗺️ Praca z mapą'`. Renderują się jak zwykłe pytanie (pytanie, opcjonalne `body`, odpowiedź).
6. **Podpowiedź w pytaniu `kolejnosc`.** Teraz tekst jest na sztywno: „Klikaj daty od najdawniejszej…”. W P16 elementami są wydarzenia, więc dodaj opcjonalne pole `hint` (dla P16: „Klikaj wydarzenia od najdawniejszego do najpóźniejszego.”) i podmień placeholder `.oseq:empty::before` na neutralny: „Klikaj po kolei, a pojawi się tutaj twoja kolejność”.
7. Przy zmianie działu: zamknij filtr „Tylko do powtórki”, przewiń na górę, przelicz pasek i maskotkę.
8. **Ściągawka:** sekcja 5. Oś czasu zbuduj jak w dziale 1 (`.tl` z kolorowymi segmentami), resztę jako `.rules`.

### Kryteria gotowości
- Brak błędów w konsoli; strona działa po otwarciu z dysku (`file://`).
- Obie zakładki działają, postęp każdego działu liczy się osobno i przetrwa odświeżenie strony.
- Dział 6 ma 24 pytania w 7 kategoriach, numerowane od 1.
- Dopasowania i „prawda/fałsz” liczą wynik zgodnie z kluczami z tego pliku.
- Układ działa na telefonie (szerokość 390 px).

---

## 1. Metadane działu

| pole | wartość |
|---|---|
| `id` | `'d6'` |
| `nr` | `6` |
| `tytul` | `'Starożytny Izrael'` |
| `zakres` | `'podręcznik s. 34–37'` |

---

## 2. Kategorie

| # | `id` | `ikona` | `nazwa` | `krotko` | `opis` | `c` | `soft` | `dark` |
|---|---|---|---|---|---|---|---|---|
| 1 | `d6-slowa` | 🗣️ | Wyjaśnij własnymi słowami | Słowami | Opowiedz pełnymi zdaniami, o co chodzi. | `#FF6B5B` | `#FFE7E2` | `#C4382A` |
| 2 | `d6-pojecia` | 📖 | Słowniczek pojęć | Pojęcia | Krótko i konkretnie: co znaczy to słowo? | `#7C5CFF` | `#EDE9FF` | `#5536D6` |
| 3 | `d6-ludzie` | 👑 | Kto to był? | Kto to był? | Postacie, które trzeba znać z tego działu. | `#F59E0B` | `#FFEFCC` | `#9A5B00` |
| 4 | `d6-daty` | 📅 | Daty i oś czasu | Daty | Ustaw wydarzenia w kolejności i policz lata. | `#3B82F6` | `#E1EBFF` | `#1E5CC8` |
| 5 | `d6-pary` | 🔗 | Dopasuj w pary | Dopasuj | Połącz daty, ludzi i symbole z opisami. | `#E8579B` | `#FCE4EF` | `#AD2966` |
| 6 | `d6-mapa` | 🗺️ | Praca z mapą | Mapa | Otwórz podręcznik na s. 36 i spójrz na mapę. | `#14A39F` | `#DBF3F1` | `#0A736F` |
| 7 | `d6-pf` | ⚖️ | Prawda czy fałsz? | Prawda / fałsz | Zdecyduj przy każdym zdaniu. A zdania fałszywe popraw! | `#16A063` | `#DFF5E9` | `#11774A` |

---

## 3. Schemat pól pytania (taki sam jak w dziale 1)

| `typ` | pola |
|---|---|
| `opis`, `pojecie`, `krotka`, `policz`, `mapa` | `q`, opcjonalnie `body`, `odp`, `extra` |
| `kolejnosc` | `q`, `elementy` (kolejność wyświetlania), `kolejnosc` (indeksy w poprawnej kolejności), `odp`, `extra`, opcjonalnie `hint` |
| `dopasuj` | `q`, `lewa`, `prawa`, `klucz` (litera dla każdej pozycji z `lewa`), `extra`; odpowiedź generuje się sama |
| `pf` | `q`, `zdania: [{t, p, fix}]` (`p` = `true` dla prawdy), `extra` |

„Chipy” w `body` renderuj jak w dziale 1: `<ul class="dates"><li>…</li></ul>`.

---

## 4. Pytania

### Kategoria 1: `d6-slowa` – Wyjaśnij własnymi słowami

#### P1 · `opis`
**Pytanie:** Czym jest Biblia?

**Odpowiedź:**
Biblia to **święta księga żydów i chrześcijan**. Wierzą oni, że powstała **pod natchnieniem Boga**, czyli że jej autorzy napisali to, co Stwórca chciał powiedzieć ludziom. Składa się z **kilkudziesięciu części nazywanych księgami** (np. Księga Rodzaju). Jest dziełem **religijnym, a nie naukowym**.

**Zabłyśnij na lekcji:**
Słowo „Biblia” pochodzi z greki i znaczy po prostu „książki”, w liczbie mnogiej! Greckie słowo wiąże się z nazwą fenickiego miasta Byblos, przez które sprowadzano papirus, czyli materiał do pisania. Z tego samego źródła pochodzi słowo „biblioteka”.

Biblia to rzeczywiście cała biblioteka: Biblia katolicka liczy 73 księgi.

Źródło: s. 34, s. 37 („To, co najważniejsze”)

---

#### P2 · `opis`
**Pytanie:** Jakie są różnice między Biblią hebrajską a Biblią chrześcijańską?

**Odpowiedź:**
- **Biblia hebrajska** (żydowska) była pisana prawdopodobnie **od XIII do II w. p.n.e.** Chrześcijanie nazywają ją **Starym Testamentem**.
- **Biblia chrześcijańska** obejmuje Stary Testament oraz **Nowy Testament**, który powstał **w I w. n.e.** i opowiada o życiu i nauce Jezusa Chrystusa.
- Dla chrześcijan Nowy Testament jest częścią Biblii, a **dla żydów – nie**.

**Zabłyśnij na lekcji:**
Żydzi nazywają swoją Biblię **Tanach**. To skrót od nazw jej trzech części: **T**ora (Pouczenie), **N**ewiim (Prorocy) i **K**etuwim (Pisma). Biblię hebrajską spisano głównie po hebrajsku, a Nowy Testament – po grecku.

Policz: od XIII do II w. p.n.e. to ponad tysiąc lat spisywania ksiąg!

Źródło: s. 35, s. 37

---

#### P3 · `opis`
**Pytanie:** Dlaczego historycy ostrożnie podchodzą do informacji zawartych w Biblii? Co odpowie historyk na pytanie, czy istniał Abraham?

**Odpowiedź:**
Bo Biblia jest dziełem **religijnym, a nie naukowym**. Jej autorzy opisali np. **rozmowy Abrahama z Bogiem**. Nauka nie zajmuje się takimi informacjami, bo są one **przedmiotem wiary**: albo ktoś w nie wierzy, albo nie. Jednocześnie księgi historyczne Biblii są znakomitym źródłem historycznym, więc historycy z nich korzystają, ale ostrożnie.

Na pytanie o Abrahama historyk odpowie: **na pewno istniało plemię, z którego powstał naród żydowski, i być może żył biblijny Abraham**. Pewności jednak nie mamy i prawdopodobnie nie będziemy mieli nigdy.

**Zabłyśnij na lekcji:**
Historycy porównują opisy z Biblii z innymi źródłami, np. ze znaleziskami archeologów. W 1947 r. pasterz z plemienia Beduinów, szukając zagubionej kozy, natrafił w jaskiniach nad Morzem Martwym na gliniane dzbany ze starymi zwojami.

Te **zwoje znad Morza Martwego** mają ponad 2000 lat i należą do najstarszych znanych odpisów ksiąg Biblii hebrajskiej.

Źródło: s. 35

---

#### P4 · `opis`
**Pytanie:** Co nazywamy tzw. niewolą babilońską? Dlaczego mówimy „tak zwaną”?

**Odpowiedź:**
W początkach VI w. p.n.e. Babilończycy opanowali królestwo Judy. Gdy Żydzi zbuntowali się przeciwko ich rządom, Babilończycy **zdobyli Jerozolimę i zniszczyli świątynię (586 r. p.n.e.)**. Król Babilonii kazał **przesiedlić kilkanaście tysięcy Żydów na wschód**. Ten czas nazywamy tzw. **niewolą babilońską**.

Mówimy „tak zwaną”, bo Żydzi byli **przesiedleńcami, a nie niewolnikami**. Niektórzy zajmowali nawet wysokie stanowiska w państwie babilońskim.

Niewola skończyła się po kilkudziesięciu latach: w **539 r. p.n.e.** Persowie podbili Babilonię, a ich król pozwolił Żydom wrócić do Palestyny.

**Zabłyśnij na lekcji:**
Królem Babilonii, który kazał zniszczyć świątynię jerozolimską, był **Nabuchodonozor II**. Za jego panowania zbudowano w Babilonie **Bramę Isztar**, ozdobioną niebieskimi glazurowanymi cegłami z wizerunkami zwierząt. Jej rekonstrukcja stoi dziś w muzeum w Berlinie.

Źródło: s. 36

---

#### P5 · `opis`
**Pytanie:** Czym różni się monoteizm od politeizmu? Co wyznawali Izraelici?

**Odpowiedź:**
- **Monoteizm**, czyli jedynobóstwo, to wiara w **jednego Boga**.
- **Politeizm**, czyli wielobóstwo, to wiara w **wielu bogów**.

Izraelici, w przeciwieństwie do innych starożytnych ludów, wierzyli w jednego Boga, **Jahwe**, czyli wyznawali **monoteizm**. Inne ludy starożytne, np. Sumerowie czy Egipcjanie, czciły wielu bogów.

**Zabłyśnij na lekcji:**
Obie nazwy pochodzą z greki: *monos* – jeden, *polys* – wiele, *theos* – bóg.

Religie, które wywodzą się z judaizmu, czyli chrześcijaństwo i islam, też są monoteistyczne.

Źródło: s. 37 (pojęcie politeizmu przypomina ramka na s. 34)

---

#### P6 · `opis`
**Pytanie:** Co mówi judaizm o Bogu i o narodzie wybranym?

**Odpowiedź:**
- Bóg jest jeden (**Jahwe**), **nie ma początku ani końca**, **stworzył świat i człowieka**.
- Okazuje ludziom **miłosierdzie**, ale jest „**Bogiem zazdrosnym**”: człowiek ma Go kochać „z całego serca, z całej duszy, ze wszystkich sił”.
- Izraelici są **narodem wybranym**, bo **za ich pośrednictwem Bóg da się poznać całemu światu**.

**Zabłyśnij na lekcji:**
Słowa o kochaniu Boga „z całego serca” są częścią modlitwy **Szema Israel** („Słuchaj, Izraelu”), jednej z najważniejszych modlitw w judaizmie.

Imię Boga zapisywano czterema literami (JHWH). Pobożni żydzi z szacunku go nie wymawiają i mówią zamiast niego np. „Adonaj”, czyli „Pan”.

Źródło: s. 37

---

#### P7 · `opis`
**Pytanie:** Omów dzieje narodu wybranego od czasów Abrahama do końca tzw. niewoli babilońskiej.

**Odpowiedź:**
1. Według Biblii plemię koczowniczych pasterzy, którym przewodził **Abraham**, na polecenie Boga wyruszyło **z Mezopotamii do Ziemi Obiecanej** (Palestyny).
2. Potomkowie Abrahama dali początek **narodowi wybranemu** – Izraelitom, których później nazwano Żydami.
3. **Na przełomie XI i X w. p.n.e.** Izraelici utworzyli w Palestynie **królestwo Izraela**. Do rozkwitu doprowadzili je królowie **Dawid** (ok. 1010 – ok. 970 p.n.e.) i jego syn **Salomon** (ok. 970 – ok. 931 p.n.e.), który zbudował świątynię w Jerozolimie.
4. Po śmierci Salomona królestwo **podzieliło się na dwa słabe i skłócone państwa**. Jednym z nich była **Juda** ze stolicą w Jerozolimie.
5. W początkach VI w. p.n.e. Judę opanowali **Babilończycy**. Po buncie Żydów zdobyli Jerozolimę i zniszczyli świątynię (**586 r. p.n.e.**), a kilkanaście tysięcy Żydów przesiedlono na wschód. Zaczęła się **tzw. niewola babilońska**.
6. W **539 r. p.n.e.** Persowie podbili Babilonię. Ich król **pozwolił Żydom wrócić do Palestyny**, która stała się częścią Persji. Żydzi odbudowali świątynię i wierzyli, że własne państwo przywróci im Mesjasz.

**Zabłyśnij na lekcji:**
Sposób na zapamiętanie: sześć słów-kluczy po kolei, czyli **wędrówka → naród → królestwo → podział → niewola → powrót**. Do każdego dopowiedz jedno zdanie, a w pracy pisemnej dodaj daty: ok. 1010, ok. 931, 586 i 539 p.n.e.

Źródło: s. 35–37 (polecenie A w „Pytaniach i poleceniach”)

---

### Kategoria 2: `d6-pojecia` – Słowniczek pojęć

#### P8 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: Ziemia Obiecana, Palestyna, Izrael.

**Odpowiedź:**
- **Ziemia Obiecana** – według Biblii kraj, do którego na polecenie Boga wyruszyło z Mezopotamii plemię Abrahama. Leżał tam, gdzie dziś znajduje się państwo Izrael.
- **Palestyna** – starożytna nazwa kraju potomków Abrahama.
- **Izrael** – druga starożytna nazwa tego kraju, od imienia jednego z wnuków Abrahama. Tak nazywało się też królestwo utworzone przez Izraelitów na przełomie XI i X w. p.n.e. Dziś to nazwa państwa.

**Zabłyśnij na lekcji:**
Tym wnukiem Abrahama był **Jakub**, syn Izaaka. Według Biblii otrzymał on od Boga imię Izrael.

Nazwa **Palestyna** pochodzi od **Filistynów**, ludu, który mieszkał na wybrzeżu. Filistynem był biblijny olbrzym Goliat, którego pokonał młody Dawid.

Źródło: s. 35

---

#### P9 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: judaizm, Dekalog, Tora.

**Odpowiedź:**
- **Judaizm** – religia żydowska. Jest **monoteistyczna** i **istnieje do dziś**. Wywodzą się z niej chrześcijaństwo i islam.
- **Dekalog** – **dziesięcioro przykazań** zawartych w Biblii. Według Biblii otrzymał je Mojżesz od samego Boga, wyryte na kamiennych tablicach. Określa **główne zasady postępowania** wyznawców judaizmu.
- **Tora** – **pięć pierwszych ksiąg Biblii**. Zawiera liczne nakazy i zakazy uzupełniające Dekalog, a także opisy stworzenia świata i dzieje Abrahama oraz jego potomków. Dla wyznawców judaizmu to **najważniejsza część Biblii**.

**Zabłyśnij na lekcji:**
„Dekalog” to po grecku „dziesięć słów” (*deka* – dziesięć, *logos* – słowo). Według tradycji żydowskiej Tora zawiera aż **613 nakazów i zakazów**.

Zwój Tory przepisuje się ręcznie, piórem. Podczas czytania wodzi się po tekście wskaźnikiem w kształcie małej dłoni (nazywa się **jad**), żeby nie dotykać pergaminu palcami.

Źródło: s. 37

---

#### P10 · `pojecie`
**Pytanie:** Słowo „Żydzi” ma dwa znaczenia. Jakie? Kiedy piszemy je wielką, a kiedy małą literą?

**Odpowiedź:**
1. **żydzi** (małą literą) – **wyznawcy judaizmu**, tak jak chrześcijanie, muzułmanie czy wyznawcy innych religii.
2. **Żydzi** (wielką literą) – **członkowie narodu żydowskiego**, tak jak np. Polacy. W przeszłości nazywano ich też **Izraelitami** lub **Hebrajczykami**.

**Zabłyśnij na lekcji:**
To ogólna zasada polskiej pisowni: nazwy narodów piszemy wielką literą (Polak, Żyd, Egipcjanin), a nazwy wyznawców religii małą (katolik, żyd, muzułmanin).

Język hebrajski jest używany do dziś. To urzędowy język państwa Izrael, a pisze się w nim od prawej do lewej.

Źródło: s. 34 (ramka „Żydzi”)

---

#### P11 · `pojecie`
**Pytanie:** Kim byli koczownicy? Czym różnili się od ludów osiadłych? Podaj przykład jednych i drugich.

**Odpowiedź:**
- **Koczownicy** nie mieli stałych siedzib. Na Bliskim Wschodzie były to **plemiona pasterzy**, które wędrowały z miejsca na miejsce **w poszukiwaniu pastwisk dla bydła**. Przykład: **plemię Abrahama**.
- **Ludy osiadłe** mieszkały na stałe w jednym miejscu. Przykład: **Sumerowie**.

Koczownicy nieraz szukali schronienia przed głodem lub suszą w zamożnym Egipcie.

**Zabłyśnij na lekcji:**
Na egipskim malowidle w podręczniku łatwo odróżnić obie grupy. Egipcjanie noszą proste białe spódniczki, a przybysze mają kolorowe, wzorzyste stroje i prowadzą ze sobą osły.

Koczownicy żyją do dziś, np. część Beduinów na pustyniach Bliskiego Wschodu.

Źródło: s. 34

---

#### P12 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: Mesjasz, synagoga.

**Odpowiedź:**
- **Mesjasz** – według wierzeń Żydów **człowiek posłany przez Boga**. Po powrocie z niewoli babilońskiej Żydzi wierzyli, że Mesjasz **przywróci im własne państwo**.
- **Synagoga** – **żydowski dom modlitwy**. Każda synagoga ma ręcznie spisany zwój Tory.

**Zabłyśnij na lekcji:**
Hebrajskie słowo „mesjasz” znaczy „namaszczony”. Po grecku to samo słowo brzmi „Christos”, stąd tytuł Chrystus. Chrześcijanie wierzą, że Mesjaszem był Jezus, a wyznawcy judaizmu wciąż na Mesjasza czekają.

„Synagoga” to po grecku „zgromadzenie”.

Źródło: s. 36, s. 37 (podpis pod zwojem Tory)

---

### Kategoria 3: `d6-ludzie` – Kto to był?

#### P13 · `opis`
**Pytanie:** Kim byli i czego dokonali Dawid oraz Salomon?

**Odpowiedź:**
**Dawid** (panował ok. 1010 – ok. 970 p.n.e.) i jego syn **Salomon** (ok. 970 – ok. 931 p.n.e.) to **królowie Izraela**, którzy **doprowadzili królestwo do rozkwitu**. Salomon **wybudował wspaniałą świątynię w stolicy państwa, Jerozolimie**. Po jego śmierci królestwo podzieliło się na dwa państwa.

**Zabłyśnij na lekcji:**
Według Biblii Dawid jako młody pasterz pokonał olbrzyma Goliata kamieniem wystrzelonym z procy.

Salomon słynął z mądrości. Stąd powiedzenie „**salomonowy wyrok**”, czyli mądry i sprawiedliwy, oraz przysłowie „**z pustego i Salomon nie naleje**”.

Źródło: s. 35

---

#### P14 · `opis`
**Pytanie:** Kim był Abraham i dokąd – według Biblii – wyruszyło jego plemię?

**Odpowiedź:**
Abraham to postać **znana nam tylko z Biblii**: przywódca **plemienia koczowniczych pasterzy**. Według Biblii na polecenie Boga jego plemię wyruszyło **z Mezopotamii do Ziemi Obiecanej**, tam, gdzie dziś leży państwo Izrael. Jego potomkowie dali początek **narodowi wybranemu**, czyli Izraelitom.

**Zabłyśnij na lekcji:**
Według Biblii Abraham pochodził z miasta **Ur** w Mezopotamii, jednego z miast Sumerów.

Na rycinie w podręczniku aniołowie zapowiadają, że Abraham i Sara mimo starości będą mieli syna. Był nim **Izaak**. Jego imię kojarzy się ze śmiechem, bo według Biblii Sara roześmiała się, słysząc tę zapowiedź.

Abraham jest ważną postacią dla trzech religii: judaizmu, chrześcijaństwa i islamu.

Źródło: s. 34–35

---

#### P15 · `krotka`
**Pytanie:** Kto i kiedy zniszczył świątynię jerozolimską? Kto pozwolił Żydom wrócić do Palestyny?

**Odpowiedź:**
- Świątynię zniszczyli **Babilończycy w 586 r. p.n.e.**, po zdobyciu Jerozolimy. Rozkaz wydał król Babilonii **Nabuchodonozor**.
- Wrócić do Palestyny pozwolił Żydom **król Persów**, wkrótce po tym, jak **Persowie podbili Babilonię w 539 r. p.n.e.** Żydzi odbudowali wtedy świątynię.

**Zabłyśnij na lekcji:**
Tym perskim królem był **Cyrus Wielki**. Odbudowana świątynia przetrwała do 70 r. n.e., kiedy zburzyli ją Rzymianie.

Do dziś zachował się fragment muru, który otaczał wzgórze świątynne. To **Ściana Płaczu** (Mur Zachodni) w Jerozolimie, najważniejsze miejsce modlitwy Żydów. Wierni wkładają w szczeliny między kamieniami karteczki z modlitwami.

Źródło: s. 36 (imię króla z dymka postaci na s. 36)

---

### Kategoria 4: `d6-daty` – Daty i oś czasu

#### P16 · `kolejnosc`
**Pytanie:** Ułóż wydarzenia w kolejności, od najdawniejszego do najpóźniejszego.

**hint:** Klikaj wydarzenia od najdawniejszego do najpóźniejszego.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `Persowie podbijają Babilonię`
- 1: `Plemię Abrahama wyrusza z Mezopotamii do Ziemi Obiecanej`
- 2: `Babilończycy zdobywają Jerozolimę i niszczą świątynię`
- 3: `Początek panowania króla Dawida`
- 4: `Rzymianie łupią Jerozolimę i zabierają menorę ze świątyni`
- 5: `Podział Izraela na dwa państwa`
- 6: `Salomon buduje świątynię w Jerozolimie`

**kolejnosc:** `[1, 3, 6, 5, 2, 0, 4]`

**Odpowiedź:**
Wyprawa plemienia Abrahama → początek panowania Dawida (ok. 1010 p.n.e.) → Salomon buduje świątynię (X w. p.n.e.) → podział Izraela (ok. 931 p.n.e.) → Babilończycy niszczą świątynię (586 p.n.e.) → Persowie podbijają Babilonię (539 p.n.e.) → Rzymianie łupią Jerozolimę (70 n.e.)

**Zabłyśnij na lekcji:**
Wyprawa Abrahama nie ma daty. Historycy nie wiedzą, kiedy (ani czy) żył Abraham. Według Biblii jego plemię wyruszyło do Ziemi Obiecanej na długo przed czasami królów.

Źródło: s. 34–36, podpis pod menorą na s. 35

---

#### P17 · `policz`
**Pytanie:** W którym wieku to było? Zapisz wiek cyframi rzymskimi.

**body (chipy):**
- ok. 1010 r. p.n.e.
- ok. 931 r. p.n.e.
- 586 r. p.n.e.
- 539 r. p.n.e.
- 70 r. n.e.

**Odpowiedź:**
- ok. 1010 r. p.n.e. → 10 + 1 = 11 → **XI w. p.n.e.** (początek panowania Dawida)
- ok. 931 r. p.n.e. → 9 + 1 = 10 → **X w. p.n.e.** (podział Izraela)
- 586 r. p.n.e. → 5 + 1 = 6 → **VI w. p.n.e.** (zniszczenie świątyni)
- 539 r. p.n.e. → 5 + 1 = 6 → **VI w. p.n.e.** (podbój Babilonii przez Persów)
- 70 r. n.e. → 0 + 1 = 1 → **I w. n.e.** (Rzymianie łupią Jerozolimę)

**Zabłyśnij na lekcji:**
Teraz widać, skąd w podręczniku zwrot „na przełomie XI i X w. p.n.e.”: Dawid zaczął panować ok. 1010 r. p.n.e. (XI w.), a Salomon ok. 970 r. p.n.e. (X w.).

Zdobycie Jerozolimy i upadek Babilonii wypadają w tym samym VI wieku p.n.e., więc tzw. niewola babilońska zaczęła się i skończyła w jednym stuleciu.

Źródło: s. 34 (oś czasu), s. 35; reguła liczenia wieków z działu 1

---

#### P18 · `policz`
**Pytanie:** Policz: a) Ile lat minęło od zdobycia Jerozolimy przez Babilończyków (586 r. p.n.e.) do podboju Babilonii przez Persów (539 r. p.n.e.)? b) Ile lat mniej więcej panował Dawid, a ile Salomon?

**Odpowiedź:**
- a) 586 − 539 = **47 lat**. Zgadza się to z podręcznikiem: państwo babilońskie przetrwało jeszcze „kilkadziesiąt lat”.
- b) Dawid: 1010 − 970 = **ok. 40 lat**. Salomon: 970 − 931 = **ok. 39 lat**.

**Zabłyśnij na lekcji:**
Gdy obie daty są p.n.e., odejmujemy mniejszą liczbę od większej. Lata przed naszą erą „odliczamy w dół”, jak przed startem rakiety. Według Biblii obaj królowie panowali po 40 lat.

Zadanie dla mistrzów: od zniszczenia świątyni (586 r. p.n.e.) do zburzenia odbudowanej świątyni przez Rzymian (70 r. n.e.) minęło 586 + 70 − 1 = **655 lat**. Odejmujemy 1, bo nie było roku 0.

Źródło: s. 35–36

---

### Kategoria 5: `d6-pary` – Dopasuj w pary

#### P19 · `dopasuj`
**Pytanie:** Dopasuj datę do wydarzenia.

**lewa:**
1. `ok. 1010 r. p.n.e.`
2. `ok. 931 r. p.n.e.`
3. `586 r. p.n.e.`
4. `539 r. p.n.e.`
5. `70 r. n.e.`

**prawa** (w tej kolejności):
- **A** – `Persowie podbijają Babilonię`
- **B** – `Rzymianie łupią Jerozolimę i zabierają menorę ze świątyni`
- **C** – `Początek panowania króla Dawida`
- **D** – `Babilończycy zdobywają Jerozolimę i niszczą świątynię`
- **E** – `Podział Izraela na dwa państwa`

**klucz:** 1–C, 2–E, 3–D, 4–A, 5–B → `['C','E','D','A','B']`

**Zabłyśnij na lekcji:**
Skrót „ok.” (około) przy dacie oznacza, że historycy nie znają jej dokładnie. Im dawniejsze wydarzenie, tym częściej spotkasz przy nim to „ok.”.

Źródło: s. 34 (oś czasu), s. 35 (podpis pod menorą)

---

#### P20 · `dopasuj`
**Pytanie:** Dopasuj postać do opisu.

**lewa:**
1. `Abraham`
2. `Dawid`
3. `Salomon`
4. `Mojżesz`
5. `Nabuchodonozor`

**prawa** (w tej kolejności):
- **A** – `Syn Dawida; zbudował wspaniałą świątynię w Jerozolimie`
- **B** – `Król Babilonii, który kazał zniszczyć świątynię jerozolimską`
- **C** – `Według Biblii praojciec narodu wybranego; jego plemię wyruszyło z Mezopotamii do Ziemi Obiecanej`
- **D** – `Według Biblii otrzymał od Boga Dekalog wyryty na kamiennych tablicach`
- **E** – `Król Izraela panujący ok. 1010 – ok. 970 p.n.e.; ojciec Salomona`

**klucz:** 1–C, 2–E, 3–A, 4–D, 5–B → `['C','E','A','D','B']`

**Zabłyśnij na lekcji:**
Według Biblii Mojżesz wyprowadził Izraelitów z niewoli w Egipcie, a Dekalog otrzymał na górze Synaj. Tradycyjnie utożsamia się ją z górą na Półwyspie Synaj, który widać na mapie na s. 36.

Źródło: s. 34–37

---

#### P21 · `dopasuj`
**Pytanie:** Dopasuj symbol lub przedmiot do opisu.

**lewa:**
1. `Gwiazda Dawida`
2. `Menora`
3. `Zwój Tory`
4. `Kamienne tablice`

**prawa** (w tej kolejności):
- **A** – `Siedmioramienny złoty świecznik używany w religii żydowskiej; stał w świątyni jerozolimskiej`
- **B** – `Spisany ręcznie na pergaminie z jagnięcej skóry; ma go każda synagoga`
- **C** – `Według Biblii wyryto na nich Dekalog, który otrzymał Mojżesz`
- **D** – `Symbol religii żydowskiej i dzisiejszego państwa Izrael; jako symbol powstał dopiero w średniowieczu`

**klucz:** 1–D, 2–A, 3–B, 4–C → `['D','A','B','C']`

**Zabłyśnij na lekcji:**
Gwiazda Dawida (po hebrajsku *Magen Dawid*, czyli „tarcza Dawida”) jest na fladze Izraela, a menora w godle tego państwa.

Na łuku triumfalnym Tytusa w Rzymie do dziś widać płaskorzeźbę rzymskich żołnierzy niosących menorę zabraną ze świątyni w 70 r. n.e. Nie myl menory z **chanukiją**, czyli świecznikiem z dziewięcioma ramionami, który zapala się podczas święta Chanuka.

Źródło: s. 35 (podpisy), s. 37 (zwój Tory, Dekalog)

---

### Kategoria 6: `d6-mapa` – Praca z mapą

#### P22 · `mapa`
**Pytanie:** Spójrz na mapę „Palestyna w X–IX w. p.n.e.” w podręczniku. Które miasto było stolicą Izraela w czasach Dawida i Salomona? Na jakie dwa państwa podzielił się Izrael po śmierci Salomona i które z nich miało stolicę w Jerozolimie?

**body:** Podręcznik, s. 36: mapa „Palestyna w X–IX w. p.n.e.”

**Odpowiedź:**
- Stolicą była **Jerozolima**.
- Po śmierci Salomona powstały dwa słabe i skłócone państwa: **królestwo Izraela** na północy (zachowało nazwę zjednoczonego państwa) i **królestwo Judy** na południu. Stolicą Judy była **Jerozolima**.

**Zabłyśnij na lekcji:**
Stolicą północnego królestwa Izraela stała się później **Samaria**, którą też widać na mapie.

Słowo „Żyd” pochodzi (przez łacinę) od nazwy Judy.

Źródło: s. 35–36 (tekst i mapa)

---

#### P23 · `mapa`
**Pytanie:** Nad jakim morzem leżała Palestyna? Jak nazywa się rzeka, która przez nią płynie, i dokąd ta rzeka wpada?

**body:** Podręcznik, s. 36: mapa „Palestyna w X–IX w. p.n.e.”

**Odpowiedź:**
- Palestyna leżała nad **Morzem Śródziemnym** (od zachodu).
- Przez Palestynę płynie rzeka **Jordan**, z **Jeziora Genezaret** do **Morza Martwego**.

**Zabłyśnij na lekcji:**
Morze Martwe to w rzeczywistości bardzo słone jezioro. Jest tak słone, że można się na nim unosić jak na materacu, a ryby nie mogą w nim żyć. Jego brzeg leży ponad 400 m poniżej poziomu morza i jest najniżej położonym miejscem na lądzie na Ziemi.

Źródło: s. 36 (mapa)

---

### Kategoria 7: `d6-pf` – Prawda czy fałsz?

#### P24 · `pf`
**Pytanie:** Które zdania są prawdziwe, a które fałszywe?

**zdania:**

| lit. | `t` (zdanie) | `p` | `fix` (wyjaśnienie po odsłonięciu) |
|---|---|---|---|
| a | Nowy Testament jest częścią Biblii zarówno dla chrześcijan, jak i dla żydów. | `false` | Tylko dla chrześcijan; **dla żydów Nowy Testament nie jest częścią Biblii**. |
| b | Biblia hebrajska była pisana prawdopodobnie od XIII do II w. p.n.e. | `true` | *(puste)* |
| c | W czasie tzw. niewoli babilońskiej Żydzi byli niewolnikami. | `false` | Byli **przesiedleńcami**; niektórzy zajmowali nawet wysokie stanowiska w państwie babilońskim. |
| d | Z judaizmu wywodzą się chrześcijaństwo i islam. | `true` | *(puste)* |
| e | Gwiazda Dawida powstała w czasach króla Dawida. | `false` | Jej nazwa nawiązuje do Dawida, ale jako symbol powstała **dopiero w średniowieczu**. |
| f | Tora to pięć pierwszych ksiąg Biblii. | `true` | *(puste)* |
| g | Izraelici, podobnie jak Egipcjanie, czcili wielu bogów. | `false` | Izraelici wierzyli w **jednego Boga, Jahwe** (monoteizm). |
| h | Persja to dzisiejszy Iran. | `true` | *(puste)* |

**Zabłyśnij na lekcji:**
Nazwą „Persja” posługiwano się w Europie aż do 1935 r. Wtedy władze tego kraju poprosiły inne państwa, by używały nazwy **Iran**.

Źródło: s. 35–37

---

## 5. Ściągawka (pole `sciagawka`)

**Oś czasu** (segmenty od lewej):
1. **ok. 1010 p.n.e.** – początek panowania Dawida
2. **ok. 970 p.n.e.** – początek panowania Salomona, budowa świątyni w Jerozolimie
3. **ok. 931 p.n.e.** – podział na królestwo Izraela i królestwo Judy
4. **586 p.n.e.** – Babilończycy niszczą świątynię, początek tzw. niewoli babilońskiej
5. **539 p.n.e.** – Persowie podbijają Babilonię, Żydzi wracają do Palestyny

Pod osią podpis: „Wszystkie daty: przed naszą erą”.

**Karty z regułami:**
- **📜 Biblia ma dwie części.** Biblia hebrajska (= Stary Testament), pisana prawdopodobnie od XIII do II w. p.n.e. Nowy Testament – I w. n.e., część Biblii tylko dla chrześcijan.
- **✡️ Judaizm w trzech punktach.** Monoteizm, czyli jeden Bóg, Jahwe. Główne zasady postępowania określa Dekalog. Szczegółowe nakazy i zakazy podaje Tora (pięć pierwszych ksiąg Biblii).
- **✍️ Żyd czy żyd?** Żyd – członek narodu (jak Polak). żyd – wyznawca judaizmu (jak katolik).
- **🕎 Symbole.** Gwiazda Dawida (symbol od średniowiecza), menora (siedmioramienny świecznik), zwój Tory (w każdej synagodze).

---

## 6. Rangi i komunikaty maskotki dla działu 6 (pola `rangi`, `start`)

**start:** `Witaj w starożytnym Izraelu! Ruszamy szlakiem koczowników z Mezopotamii. Za każde pytanie, które umiesz, przesypie się trochę mojego piasku!`

| `od` | `e` | `n` | `msg` |
|---|---|---|---|
| 0 | 🐪 | Wędrowiec z Mezopotamii | Pierwsze kroki na szlaku za nami! Piasek zaczął się sypać. ⏳ |
| 0.25 | 🗺️ | Odkrywca Ziemi Obiecanej | Brawo! Zostajesz Odkrywcą Ziemi Obiecanej. |
| 0.5 | 📜 | Badacz zwojów | Ponad połowa za Tobą! Badacz zwojów w akcji. |
| 0.75 | 👑 | Kronikarz królów | Kronikarz królów! Jeszcze kilka pytań do tytułu Mistrza… |
| 1 | 🏆 | Mistrz starożytnego Izraela | MISTRZ STAROŻYTNEGO IZRAELA! Cały piasek przesypany, cały dział opanowany! 🏆 |

---

## 7. Weryfikacja merytoryczna (do wiadomości, nie renderować)

**Co sprawdzono**
- Każda odpowiedź jest zgodna z tekstem s. 34–37 (strony podano przy pytaniach). Obejmują one wszystkie pytania 1–8 z czerwonych ramek oraz polecenia A i B z „Pytań i poleceń”.
- Rachunki: 586 − 539 = 47; 1010 − 970 = 40; 970 − 931 = 39; 586 + 70 − 1 = 655 (bez roku 0). Wieki: 1010 p.n.e. → XI, 931 p.n.e. → X, 586 i 539 p.n.e. → VI, 70 n.e. → I.
- Klucze dopasowań i kolejność w P16 sprawdzone pozycja po pozycji.
- Ciekawostki („Zabłyśnij na lekcji”) wykraczają poza podręcznik i zostały sprawdzone z wiedzą ogólną. Fakty religijne podano jako wierzenia lub tradycję („według Biblii”, „według tradycji”).

**Uwagi do treści podręcznika**
1. **Menora.** Podręcznik pisze, że „pierwsza menora” zaginęła po złupieniu Jerozolimy przez Rzymian w 70 r. n.e. Ściśle biorąc, Rzymianie zabrali menorę z drugiej, odbudowanej świątyni, a pierwsza świątynia została zniszczona przez Babilończyków w 586 r. p.n.e. Dlatego w pytaniach nie ma słowa „pierwsza”: piszemy, że Rzymianie zabrali menorę ze świątyni. Nie wracaj do sformułowania z podręcznika.
2. **586 r. p.n.e.** Część historyków podaje 587 r. p.n.e. Na stronie zostaje data z podręcznika (586).
3. **Stary Testament = Biblia hebrajska.** To uproszczenie podręcznika: w Biblii katolickiej Stary Testament ma kilka ksiąg więcej. Pytania trzymają się wersji podręcznika i tego nie rozwijają.
4. Ramka „przypomnij” na s. 34 odsyła do pojęcia „Bliski Wschód” z wcześniejszych działów. Nie ma o nim pytania, bo podręcznik nie definiuje go na s. 34–37.
