# Kapsuła Czasu – Dział 2: Od myśliwych do rolników

Specyfikacja pytań i odpowiedzi do dopisania na stronę `kapsula-czasu-historia.html`.
Źródło: podręcznik do historii, dział 2 „Od myśliwych do rolników”, s. 11 i 14–16. Strony 12–13 nie zostały dostarczone (patrz sekcja 7).

---

## 0. Instrukcja dla modelu, który dokończy stronę

### Kontekst
`kapsula-czasu-historia.html` to jednoplikowa strona (HTML + CSS + JS, bez bibliotek, tylko Google Fonts) z pytaniami do powtórki z historii dla ucznia szkoły podstawowej. Treść jest w tablicy `DZIALY` w skrypcie. Jest tam dział 1 „Czas w historii”, a być może także dział 6 „Starożytny Izrael” (osobny plik MD z tą samą strukturą).

### Zadanie
1. Dopisz do `DZIALY` nowy dział według sekcji 1–6 tego pliku. Działy w tablicy i w zakładkach ustaw według `nr` (1, 2, 6…).
2. **Jeśli strona obsługuje jeden dział** (skrypt wybiera `DZIALY.filter(...)[0]`, a zakładki nic nie robią), wprowadź najpierw zmiany z listy niżej. **Jeśli już obsługuje kilka działów**, dodaj tylko nowy typ `sortuj` (zmiana 5) oraz brakujące typy i pola.
3. **Nie zmieniaj istniejących działów** ani wyglądu strony.

### Zasady merytoryczne (ważne)
- Treść pytań, odpowiedzi i ciekawostek została sprawdzona z podręcznikiem i ze źródłami wiedzy ogólnej. **Nie dopisuj nowych faktów, dat ani liczb** i nie „poprawiaj” treści.
- Zachowaj liczby z podręcznika, nawet jeśli znasz nowsze ustalenia (patrz sekcja 7). Tam, gdzie nauka poszła dalej, wspomina o tym wyłącznie ciekawostka w P26.
- Polskie cudzysłowy „ ”, półpauza – w zakresach dat, formy neutralne płciowo (bez „umiałeś/umiałaś”).
- Nie odtwarzaj ilustracji ani postaci z podręcznika (prawa autorskie). Pytanie P19 odsyła do rysunku na s. 15.

### Konwersja treści z tego pliku do pól JS
- `**tekst**` → `<b>tekst</b>`, `*tekst*` → `<i>tekst</i>`.
- Lista `-` → `<ul><li>…</li></ul>`, lista numerowana → `<ol><li>…</li></ol>`.
- Akapity → `<p>…</p>`.
- Linie „Źródło: …” są tylko do weryfikacji – **nie renderuj ich**.

### Zmiany w kodzie (jeśli jeszcze ich nie ma)
1. **Przełączanie działów.** Funkcja `render(dzId)` buduje `ALL`, `BY`, `TOTAL`, `#main`, `#chips` i stopkę dla wybranego działu i jest wywoływana po kliknięciu zakładki. Aktywny dział zapamiętaj w `location.hash` (np. `#d2`) i odtwórz go przy wczytaniu strony. Domyślnie otwiera się dział 1.
2. **Etykiety zakładek** z numerem z podręcznika: „Dział 2 Od myśliwych do rolników”.
3. **Postęp per dział.** Pasek, ranga, klepsydra, chipy i licznik dotyczą aktywnego działu. `uid` ma prefiks `dz.id` (np. `d2-5`). Zostaw klucz `localStorage` `kapsula-czasu-v1`.
4. **Rangi i komunikaty maskotki per dział:** opcjonalne pola `rangi` i `start` w obiekcie działu (wartości dla działu 2 są w sekcji 6). Toast końcowy: „🏆 Cały dział opanowany! Zostajesz: ” + nazwa najwyższej rangi (zamiast stałego tekstu o chronologii).
5. **Nowe typy w `TYPY`:**
   - `pojecie: '📖 Wyjaśnij pojęcie'`, `obraz: '🖼️ Praca z ilustracją'` – renderują się jak zwykłe pytanie (`q`, opcjonalne `body`, `odp`, `extra`).
   - `sortuj: '🗂️ Paleolit czy neolit?'` – **nowy mechanizm**, uogólnienie typu `pf`. Pola: `q`, `kategorie` (np. `['Paleolit','Neolit']`), `elementy: [{t, k}]` (`k` = indeks w `kategorie`), `extra`.
     - Przy każdym elemencie są przyciski z pełnymi nazwami kategorii. Na wąskim ekranie przyciski idą pod tekst.
     - Podpowiedź: „Przy każdej cesze kliknij „Paleolit” albo „Neolit”.”
     - Po odsłonięciu odpowiedzi elementy dostają klasy `right`/`wrong`, a wynik ma postać „Dobrze przyporządkowane: x z n”.
     - Odpowiedź generuje się sama: dla każdej kategorii nagłówek i lista jej elementów.
6. **Podpowiedź w `kolejnosc`:** opcjonalne pole `hint` (dla P20: „Klikaj wydarzenia od najdawniejszego do najpóźniejszego.”), a placeholder `.oseq:empty::before` neutralny: „Klikaj po kolei, a pojawi się tutaj twoja kolejność”.
7. Przy zmianie działu: wyłącz filtr „Tylko do powtórki”, przewiń na górę, przelicz pasek i maskotkę.
8. **Ściągawka:** sekcja 5. Oś czasu jak w dziale 1 (`.tl`), porównanie paleolit/neolit jako dwie kolumny `.rules`.

### Kryteria gotowości
- Brak błędów w konsoli; strona działa po otwarciu z dysku (`file://`).
- Wszystkie zakładki działają, postęp każdego działu liczy się osobno i przetrwa odświeżenie strony.
- Dział 2 ma 26 pytań w 7 kategoriach, numerowane od 1.
- Dopasowania, `sortuj` i „prawda/fałsz” liczą wynik zgodnie z kluczami z tego pliku.
- Układ działa na telefonie (szerokość 390 px).

---

## 1. Metadane działu

| pole | wartość |
|---|---|
| `id` | `'d2'` |
| `nr` | `2` |
| `tytul` | `'Od myśliwych do rolników'` |
| `zakres` | `'podręcznik s. 11–16'` |

---

## 2. Kategorie

| # | `id` | `ikona` | `nazwa` | `krotko` | `opis` | `c` | `soft` | `dark` |
|---|---|---|---|---|---|---|---|---|
| 1 | `d2-slowa` | 🗣️ | Wyjaśnij własnymi słowami | Słowami | Opowiedz pełnymi zdaniami, o co chodzi. | `#FF6B5B` | `#FFE7E2` | `#C4382A` |
| 2 | `d2-pojecia` | 📖 | Słowniczek pojęć | Pojęcia | Krótko i konkretnie: co znaczy to słowo? | `#7C5CFF` | `#EDE9FF` | `#5536D6` |
| 3 | `d2-paleolit` | 🦣 | Życie w paleolicie | Paleolit | Jak żyli myśliwi i zbieracze? | `#F59E0B` | `#FFEFCC` | `#9A5B00` |
| 4 | `d2-neolit` | 🌾 | Życie w neolicie | Neolit | Jak żyli pierwsi rolnicy? | `#14A39F` | `#DBF3F1` | `#0A736F` |
| 5 | `d2-daty` | 📅 | Daty i oś czasu | Daty | Ustaw wydarzenia w kolejności i policz lata. | `#3B82F6` | `#E1EBFF` | `#1E5CC8` |
| 6 | `d2-pary` | 🔗 | Dopasuj i przyporządkuj | Dopasuj | Połącz pojęcia z opisami i rozdziel cechy epok. | `#E8579B` | `#FCE4EF` | `#AD2966` |
| 7 | `d2-pf` | ⚖️ | Prawda czy fałsz? | Prawda / fałsz | Zdecyduj przy każdym zdaniu. A zdania fałszywe popraw! | `#16A063` | `#DFF5E9` | `#11774A` |

---

## 3. Schemat pól pytania

| `typ` | pola |
|---|---|
| `opis`, `pojecie`, `krotka`, `policz`, `wymien`, `obraz` | `q`, opcjonalnie `body`, `odp`, `extra` |
| `kolejnosc` | `q`, `elementy` (kolejność wyświetlania), `kolejnosc` (indeksy w poprawnej kolejności), `odp`, `extra`, opcjonalnie `hint` |
| `dopasuj` | `q`, `lewa`, `prawa`, `klucz` (litera dla każdej pozycji z `lewa`), `extra`; odpowiedź generuje się sama |
| `sortuj` | `q`, `kategorie`, `elementy: [{t, k}]`, `extra`; odpowiedź generuje się sama |
| `pf` | `q`, `zdania: [{t, p, fix}]` (`p` = `true` dla prawdy), `extra` |

„Chipy” w `body` renderuj jak w dziale 1: `<ul class="dates"><li>…</li></ul>`.

---

## 4. Pytania

### Kategoria 1: `d2-slowa` – Wyjaśnij własnymi słowami

#### P1 · `opis`
**Pytanie:** Czym różnił się klimat Europy sprzed 40 tysięcy lat od dzisiejszego klimatu?

**Odpowiedź:**
Ok. 40 tysięcy lat temu na Ziemi trwał **okres ochłodzenia**:
- średnia temperatura lipca na południu Europy wynosiła tylko **+5°C**,
- północną część Europy pokrywał **lądolód**, którego grubość dochodziła do **3 km**,
- na południu ciągnęła się **tundra**: rosły tam tylko trawy, krzewy i pojedyncze drzewa, a **lasów nie było**.

Dziś klimat Europy jest **dużo cieplejszy**: lądolodu nie ma, rosną lasy.

**Zabłyśnij na lekcji:**
Dziś średnia temperatura lipca w Polsce to ok. 18–20°C, a na południu Europy, np. w Rzymie, ok. 25°C. Lądolód o grubości 3 km to tyle, co ponad 12 Pałaców Kultury i Nauki postawionych jeden na drugim!

W czasie tego zlodowacenia lądolód dotarł też na północ dzisiejszej Polski. Zostawił po sobie jeziora na pojezierzach i wielkie **głazy narzutowe** przywleczone ze Skandynawii.

Źródło: s. 11

---

#### P2 · `opis`
**Pytanie:** Dlaczego ludzie starszej epoki kamiennej prowadzili koczowniczy tryb życia?

**Odpowiedź:**
Bo w zimnym klimacie:
- **nie mogli uprawiać ziemi**, ponieważ przez większą część roku była zmarznięta,
- **nie mogli budować drewnianych domów**, bo brakowało im budulca (lasy nie rosły).

Dlatego zajmowali się **myślistwem i zbieractwem** i **wędrowali w poszukiwaniu żywności**, zamiast budować trwałe domy.

**Zabłyśnij na lekcji:**
„Koczować” to przebywać gdzieś tylko na jakiś czas, bez stałego domu. Koczownicy żyli nie tylko w epoce kamiennej. W dziale 6 poznasz koczowniczych pasterzy z Bliskiego Wschodu, którzy wędrowali w poszukiwaniu pastwisk dla bydła.

Źródło: s. 11

---

#### P3 · `opis`
**Pytanie:** Gdzie i dlaczego ok. 10 tysięcy lat temu zmieniły się warunki życia ludzi?

**Odpowiedź:**
**Gdzie:** najpierw na **Bliskim Wschodzie**, a potem w Europie.

**Dlaczego:** bo zmienił się klimat. Już ok. 20 tysięcy lat temu zaczął się ocieplać: lądolód cofnął się na północ, zaczęły padać obfite deszcze, wyrosły gęste lasy, wysokie trawy i **dzikie zboża**. Ok. 10 tysięcy lat temu nastał **okres ciepły**, w którym żyjemy do dziś. Wtedy mieszkańcy Bliskiego Wschodu jako pierwsi w dziejach **zaczęli uprawiać ziemię i hodować zwierzęta**.

**Zabłyśnij na lekcji:**
Obszar, na którym powstały pierwsze uprawy, nazywa się **Żyznym Półksiężycem**. To łukowaty pas urodzajnych ziem od Mezopotamii przez Syrię po Palestynę. Pierwszymi uprawianymi zbożami były pszenica i jęczmień.

Źródło: s. 14

---

#### P4 · `opis`
**Pytanie:** Z jakiego powodu mieszkańcy Bliskiego Wschodu zaczęli prowadzić osiadły tryb życia?

**Odpowiedź:**
Bo **zajęli się rolnictwem**. Uprawiali pola, a pól **trzeba było doglądać**, więc nie mogli już wędrować z miejsca na miejsce. Zamieszkali w **trwałych domach** z drewna albo z gliny zmieszanej z trzciną. W cieplejszym klimacie rosły już lasy, więc mieli z czego budować.

**Zabłyśnij na lekcji:**
Zboże rośnie kilka miesięcy. Od siewu do żniw trzeba pilnować pola, np. przed dzikimi zwierzętami. A zebrane ziarno można przechowywać na później w glinianych naczyniach. Dlatego rolnicy zostawali w jednym miejscu.

Źródło: s. 15

---

#### P5 · `opis`
**Pytanie:** Które gałęzie rzemiosła rozwinęły się jako pierwsze – i dlaczego właśnie one?

**Odpowiedź:**
- **Garncarstwo.** Ludziom nie wystarczały już naczynia ze skóry czy drewna, więc zaczęli wytwarzać **gliniane wazy, misy i dzbany**. Przechowywali w nich ziarno i napoje, a także gotowali posiłki.
- **Tkactwo.** W cieplejszym klimacie potrzebne były **bardziej przewiewne stroje z wełny i lnu** zamiast ubrań szytych ze skór.

**Zabłyśnij na lekcji:**
Z łodyg lnu robi się nici, a wełnę dawały udomowione owce, więc hodowla i tkactwo szły w parze.

Gliniane naczynia są dla archeologów tak ważne, że całe dawne społeczności nazywa się od wzorów na garnkach. Na ziemiach polskich żyli np. rolnicy z tzw. **kultury ceramiki wstęgowej rytej**.

Źródło: s. 16

---

#### P6 · `wymien`
**Pytanie:** Przedstaw skutki rewolucji neolitycznej.

**Odpowiedź:**
1. **Osiadły tryb życia** – ludzie nie wędrowali już, bo musieli doglądać pól. Budowali trwałe domy z drewna albo z gliny zmieszanej z trzciną.
2. **Udoskonalenie kamiennych narzędzi** – ludzie nauczyli się je wygładzać, przewiercać i osadzać na trzonkach. Zaczęli też wytwarzać narzędzia rolnicze.
3. **Udomowienie kóz, owiec, bydła i świń** – zwierzęta dawały mięso, skóry, mleko i wełnę.
4. **Możliwość wyżywienia większej liczby ludzi dzięki rolnictwu** – na Bliskim Wschodzie przybywało ludzi, powstawały coraz ludniejsze wsie i osady.
5. **Powstanie pierwszych gałęzi rzemiosła**: garncarstwa i tkactwa.

**Zabłyśnij na lekcji:**
Skutki rewolucji neolitycznej odczuwamy do dziś. Chleb, mleko, wełniany sweter, gliniany kubek – to wszystko ma swój początek właśnie wtedy.

Źródło: s. 15–16 (polecenie A, „To, co najważniejsze”)

---

#### P7 · `opis`
**Pytanie:** Omów różnice między koczowniczym a osiadłym trybem życia.

**Odpowiedź:**
- **Koczowniczy tryb życia** (paleolit): ludzie **wędrowali w poszukiwaniu żywności** i nie budowali trwałych domów. Mieszkali w **jaskiniach albo namiotach** z kości mamuta okrytych skórami. Żyli z **myślistwa i zbieractwa**.
- **Osiadły tryb życia** (neolit): ludzie **mieszkali na stałe w jednym miejscu**, bo musieli doglądać pól. Budowali **trwałe domy** z drewna lub gliny zmieszanej z trzciną. Żyli z **rolnictwa**, czyli uprawy ziemi i hodowli zwierząt. Powstawały coraz ludniejsze **wsie i osady**.

**Zabłyśnij na lekcji:**
Sposób na dobrą odpowiedź: porównuj po kolei te same rzeczy – gdzie ludzie mieszkali, z czego żyli, czy się przemieszczali.

Możesz dodać jeszcze jedną różnicę: koczownik wszystko, co miał, nosił ze sobą, więc nie mógł mieć ciężkich rzeczy. Rolnik mógł gromadzić zapasy w ciężkich glinianych naczyniach.

Źródło: s. 11, 15–16 (polecenie B, „To, co najważniejsze”)

---

### Kategoria 2: `d2-pojecia` – Słowniczek pojęć

#### P8 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: lądolód, tundra, Bliski Wschód.

**Odpowiedź:**
- **Lądolód** – ogromna i bardzo gruba pokrywa lodowa. W Europie sprzed 40 tysięcy lat jego grubość dochodziła do 3 km.
- **Tundra** – obszar porośnięty jedynie trawami, krzewami i pojedynczymi drzewami.
- **Bliski Wschód** – południowo-zachodnia Azja i północno-wschodnia Afryka.

**Zabłyśnij na lekcji:**
Lądolody istnieją do dziś: pokrywają Antarktydę i Grenlandię. Tundra też: znajdziesz ją na dalekiej północy, np. w północnej Skandynawii i na Syberii, gdzie żyją renifery.

Do Bliskiego Wschodu należą m.in. Mezopotamia, Egipt i Palestyna. Poznasz je w kolejnych działach.

Źródło: s. 11

---

#### P9 · `pojecie`
**Pytanie:** Wyjaśnij pojęcia: myślistwo, zbieractwo, rolnictwo.

**Odpowiedź:**
- **Myślistwo** – zdobywanie pożywienia przez polowanie na dzikie zwierzęta.
- **Zbieractwo** – zbieranie tego, co daje przyroda: owoców, nasion, jadalnych korzeni, ptasich jaj.
- **Rolnictwo** – **uprawa ziemi i hodowla zwierząt**.

**Zabłyśnij na lekcji:**
Myśliwy i zbieracz biorą to, co przyroda sama daje. Rolnik sam sprawia, że rośnie zboże i rodzą się zwierzęta, dlatego może gromadzić zapasy.

Źródło: s. 11, s. 14

---

#### P10 · `pojecie`
**Pytanie:** Co nazywamy rewolucją neolityczną?

**Odpowiedź:**
**Rewolucja neolityczna** to **przejście ludzi od myślistwa i zbieractwa do rolnictwa**, czyli do uprawy ziemi i hodowli zwierząt. Zaczęła się na **Bliskim Wschodzie** ok. 10 tysięcy lat temu.

**Zabłyśnij na lekcji:**
„Rewolucja” to wielka, przełomowa zmiana. Ta rewolucja nie była nagłym przewrotem, bo trwała tysiące lat. Zmieniła jednak życie ludzi tak bardzo jak mało co w dziejach.

Źródło: s. 14–16

---

#### P11 · `pojecie`
**Pytanie:** Wyjaśnij, skąd pochodzi nazwa: młodsza epoka kamienna.

**Odpowiedź:**
- **„Kamienna”**, bo ludzie nadal robili narzędzia **z kamienia**, tylko ulepszone: wygładzane, przewiercane i osadzane na trzonkach.
- **„Młodsza”**, bo ta epoka **nastała po starszej epoce kamiennej**, czyli po paleolicie.

Naukowa nazwa młodszej epoki kamiennej to **neolit**.

**Zabłyśnij na lekcji:**
Nazwy pochodzą z greki: *neos* – nowy, *palaios* – stary, *lithos* – kamień.

Po epokach kamiennych przyszły czasy, w których ludzie robili narzędzia z metali: najpierw z miedzi i brązu, potem z żelaza.

Źródło: s. 11, s. 14–15

---

### Kategoria 3: `d2-paleolit` – Życie w paleolicie

#### P12 · `krotka`
**Pytanie:** Ile osób liczyła gromada ludzi paleolitu? Dlaczego właśnie tyle?

**Odpowiedź:**
Gromada liczyła **20–30 osób**. **Mniejsza** nie dałaby rady upolować dużego zwierzęcia, np. mamuta. W **większej** nie starczyłoby jedzenia dla wszystkich.

**Zabłyśnij na lekcji:**
Mamut włochaty był wielkości słonia, miał gęste futro i zakrzywione ciosy. Myśliwi zapędzali go np. do dołu-pułapki (rysunek na s. 11).

Ostatnie mamuty żyły jeszcze ok. 4000 lat temu na Wyspie Wrangla w Arktyce, gdy w Egipcie stały już piramidy!

Źródło: s. 14

---

#### P13 · `krotka`
**Pytanie:** Jakiej broni i jakich narzędzi używali myśliwi paleolitu?

**Odpowiedź:**
- **toporków i oszczepów z krzemiennymi ostrzami**,
- **pięściaków** – do rąbania, cięcia i kopania, ale też jako broni,
- **harpunów** do połowu ryb,
- **łuku**, który ludzie wynaleźli kilkanaście tysięcy lat temu; ułatwił polowanie na szybkie zwierzęta, np. renifery.

Broń i narzędzia robiono z **krzemienia**.

**Zabłyśnij na lekcji:**
Pięściak trzymało się w dłoni, stąd nazwa (od „pięści”).

Na ziemiach polskich, w **Krzemionkach** koło Ostrowca Świętokrzyskiego, zachowały się kopalnie krzemienia pasiastego. Ludzie wydobywali go tam już ok. 5000 lat temu, w neolicie. Dziś kopalnie są na liście światowego dziedzictwa UNESCO.

Źródło: s. 14

---

#### P14 · `krotka`
**Pytanie:** Co jedli ludzie starszej epoki kamiennej?

**Odpowiedź:**
- **mięso upolowanych zwierząt**: mamutów, niedźwiedzi, byków, koni i reniferów, pieczone nad ogniskiem,
- **ryby**,
- to, co zebrały kobiety i dzieci: **owoce, nasiona, jadalne korzenie i ptasie jaja**.

**Zabłyśnij na lekcji:**
Byki, na które polowano, to dzikie tury, przodkowie dzisiejszego bydła. Ostatni tur na świecie padł w Polsce, w Puszczy Jaktorowskiej, w 1627 r.

Źródło: s. 14

---

#### P15 · `krotka`
**Pytanie:** W jaki sposób ludzie paleolitu rozpalali ogień?

**Odpowiedź:**
Uderzali **krzemieniem w kamień zwany pirytem**. Z pirytu sypały się **iskry**, które podpalały np. **wiązkę suchej trawy**.

**Zabłyśnij na lekcji:**
Nazwa „piryt” pochodzi od greckiego słowa oznaczającego ogień. Bywa nazywany „złotem głupców”, bo błyszczy jak złoto.

Znacznie później żył Ötzi, człowiek sprzed ponad 5000 lat, którego ciało znaleziono w 1991 r. w lodowcu w Alpach. Miał przy sobie **hubkę**, czyli grzyb, który łatwo zajmuje się od iskry.

Źródło: s. 14

---

#### P16 · `krotka`
**Pytanie:** Gdzie mieszkali ludzie paleolitu? Dlaczego nie budowali drewnianych domów?

**Odpowiedź:**
Mieszkali **w jaskiniach** albo **w namiotach z kości mamuta okrytych zwierzęcymi skórami**. Drewnianych domów nie budowali, bo **brakowało budulca**, ponieważ lasy wtedy nie rosły. Poza tym wędrowali w poszukiwaniu żywności, więc nie budowali trwałych domów.

**Zabłyśnij na lekcji:**
Archeolodzy odkryli na terenie dzisiejszej Ukrainy szczątki chat z kości mamutów sprzed ok. 15 tysięcy lat. Na jedną taką chatę zużyto kości wielu mamutów.

Źródło: s. 11

---

### Kategoria 4: `d2-neolit` – Życie w neolicie

#### P17 · `krotka`
**Pytanie:** Jak ludzie neolitu udoskonalili kamienne narzędzia? W jaki sposób przewiercano kamienne ostrze?

**Odpowiedź:**
Ludzie nauczyli się narzędzia **wygładzać, przewiercać i osadzać na trzonkach**. Zaczęli też robić **narzędzia rolnicze**. Lepsze narzędzia były potrzebne do **karczowania lasów i pracy w polu**.

Ostrze przewiercano tak: **„wiertarką” był kij**, a pomocnik **sypał do otworu piasek, który zwiększał tarcie**.

**Zabłyśnij na lekcji:**
Była też prostsza siekiera, z ostrzem osadzonym w wydrążonym trzonku. Łatwiej ją było zrobić, ale była **mniej trwała** od siekiery z otworem wywierconym w ostrzu (podpis na s. 16). Wywiercenie otworu w kamieniu mogło trwać wiele godzin.

Źródło: s. 14–16 (tekst i podpisy pod ilustracjami)

---

#### P18 · `krotka`
**Pytanie:** Jakie zwierzęta udomowili ludzie neolitu i co od nich mieli? Jakie zwierzę udomowiono już wcześniej, w paleolicie?

**Odpowiedź:**
Ludzie neolitu udomowili **kozy, owce, bydło i świnie**. Zwierzęta hodowlane dawały **mięso i skóry**, a także **mleko i wełnę**.

Już w starszej epoce kamiennej ludzie udomowili **psa**.

**Zabłyśnij na lekcji:**
Udomowić zwierzę to przyzwyczaić je do życia przy człowieku i je hodować. Wiele zwierząt domowych ma dzikich przodków: pies pochodzi od wilka, krowa od tura, świnia od dzika, a owca od muflona.

Źródło: s. 14 (dymek postaci), s. 15

---

#### P19 · `obraz`
**Pytanie:** Przyjrzyj się rysunkowi neolitycznej wsi. Jakie prace wykonują na nim ludzie?

**body:** Podręcznik, s. 15: rysunek „Neolityczna wieś”

**Odpowiedź:**
- Jedna kobieta **tka na krośnie**: przeplata poziomą nić przez pionowe nici obciążone ciężarkami, żeby były napięte.
- Druga kobieta **miele ziarna**: rozciera je kamieniem na mąkę, z której upiecze chleb lub placki.
- Mężczyzna na drabinie **naprawia dach** wiązkami słomy.

**Zabłyśnij na lekcji:**
Na tym jednym rysunku widać prawie wszystkie skutki rewolucji neolitycznej: trwałe domy, hodowlę zwierząt (świnie, stado zwierząt w tle), rolnictwo (mąka z ziarna), tkactwo i gliniane naczynia.

Źródło: s. 15 (podpis pod rysunkiem)

---

### Kategoria 5: `d2-daty` – Daty i oś czasu

#### P20 · `kolejnosc`
**Pytanie:** Ułóż wydarzenia w kolejności, od najdawniejszego do najpóźniejszego.

**hint:** Klikaj wydarzenia od najdawniejszego do najpóźniejszego.

**elementy** (kolejność wyświetlania, indeksy od 0):
- 0: `Początek ocieplania się klimatu`
- 1: `Pojawienie się człowieka rozumnego`
- 2: `Początek młodszej epoki kamiennej na Bliskim Wschodzie`
- 3: `Ludzie rozumni przybywają do Europy`
- 4: `Koniec młodszej epoki kamiennej na Bliskim Wschodzie`

**kolejnosc:** `[1, 3, 0, 2, 4]`

**Odpowiedź:**
Pojawienie się człowieka rozumnego (ok. 198 tys. p.n.e.) → ludzie rozumni przybywają do Europy (ok. 38 tys. p.n.e.) → początek ocieplania się klimatu (ok. 18 tys. p.n.e.) → początek młodszej epoki kamiennej na Bliskim Wschodzie (ok. 8000 p.n.e.) → jej koniec (ok. 2500 p.n.e.)

**Zabłyśnij na lekcji:**
Oś czasu w podręczniku nie jest narysowana w skali. Gdyby 1 cm oznaczał 1000 lat, odcinek od pojawienia się człowieka rozumnego do początku neolitu miałby prawie 2 metry, a cały neolit na Bliskim Wschodzie zająłby tylko 5,5 cm!

Źródło: s. 11 (oś czasu), s. 15

---

#### P21 · `policz`
**Pytanie:** W tekście podręcznika jest „ok. 200 tysięcy lat temu”, a na osi czasu „ok. 198 tys. p.n.e.”. Skąd ta różnica? Zamień na daty p.n.e.: ok. 40 tysięcy lat temu, ok. 20 tysięcy lat temu, ok. 10 tysięcy lat temu.

**body (chipy):**
- ok. 40 tys. lat temu
- ok. 20 tys. lat temu
- ok. 10 tys. lat temu

**Odpowiedź:**
„Lat temu” liczymy **od dziś**, a „p.n.e.” **od początku naszej ery**. Od początku naszej ery minęło ok. 2000 lat, więc **odejmujemy ok. 2000**: 200 000 − 2000 = 198 000, czyli **ok. 198 tys. p.n.e.**

- ok. 40 tys. lat temu → **ok. 38 tys. p.n.e.** (przybycie ludzi rozumnych do Europy)
- ok. 20 tys. lat temu → **ok. 18 tys. p.n.e.** (początek ocieplania się klimatu)
- ok. 10 tys. lat temu → **ok. 8000 p.n.e.** (początek młodszej epoki kamiennej na Bliskim Wschodzie)

**Zabłyśnij na lekcji:**
Dokładnie w 2026 r. trzeba by odjąć 2026 lat. Przy tak dawnych i przybliżonych datach (z „ok.”) wystarczy jednak zaokrąglić do 2000.

Naukowcy często zapisują takie daty skrótem **BP** (z angielskiego *before present*, „przed teraźniejszością”). Umownie liczy się je od 1950 r.

Źródło: s. 11 (tekst i oś czasu), s. 14

---

#### P22 · `policz`
**Pytanie:** Policz: a) Ile lat trwała młodsza epoka kamienna na Bliskim Wschodzie? b) Ile lat minęło od pojawienia się człowieka rozumnego (ok. 198 tys. p.n.e.) do początku rolnictwa na Bliskim Wschodzie (ok. 8000 p.n.e.)?

**Odpowiedź:**
- a) Od ok. 8000 do ok. 2500 p.n.e.: 8000 − 2500 = **ok. 5500 lat**.
- b) 198 000 − 8000 = **ok. 190 000 lat**.

**Zabłyśnij na lekcji:**
190 tysięcy z ok. 200 tysięcy lat to aż **95%**! Przez prawie całe swoje dzieje ludzie rozumni byli myśliwymi i zbieraczami.

Gdyby dzieje człowieka rozumnego zmieścić w jednej dobie, rolnictwo pojawiłoby się dopiero ok. 22:50.

Źródło: s. 11 (oś czasu), s. 15

---

### Kategoria 6: `d2-pary` – Dopasuj i przyporządkuj

#### P23 · `dopasuj`
**Pytanie:** Dopasuj nazwę do opisu.

**lewa:**
1. `krzemień`
2. `piryt`
3. `pięściak`
4. `harpun`
5. `łuk`

**prawa** (w tej kolejności):
- **A** – `Broń wynaleziona kilkanaście tysięcy lat temu; ułatwiła polowanie na szybkie zwierzęta, np. renifery`
- **B** – `Twarda skała, którą można łupać na kawałki o bardzo ostrych krawędziach`
- **C** – `Oszczep z zadziorami na ostrzu i liną do przyciągnięcia zdobyczy`
- **D** – `Kamień, z którego po uderzeniu krzemieniem sypały się iskry`
- **E** – `Krzemienne narzędzie do rąbania, cięcia i kopania, używane też jako broń`

**klucz:** 1–B, 2–D, 3–E, 4–C, 5–A → `['B','D','E','C','A']`

**Zabłyśnij na lekcji:**
Krzemień był dla ludzi epoki kamiennej tym, czym dla nas stal: najlepszym materiałem na ostrza. Przy łupaniu powstają krawędzie tak ostre, że można nimi kroić skórę i mięso.

Źródło: s. 14 (tekst i podpisy)

---

#### P24 · `dopasuj`
**Pytanie:** Dopasuj pojęcie do znaczenia.

**lewa:**
1. `rolnictwo`
2. `garncarstwo`
3. `tkactwo`
4. `karczowanie`
5. `rzemiosło`

**prawa** (w tej kolejności):
- **A** – `Usuwanie drzew z korzeniami`
- **B** – `Wykonywanie przedmiotów codziennego użytku za pomocą prostych narzędzi`
- **C** – `Uprawa ziemi i hodowla zwierząt`
- **D** – `Wytwarzanie glinianych waz, mis i dzbanów`
- **E** – `Wytwarzanie na krośnie tkanin, np. z wełny i lnu`

**klucz:** 1–C, 2–D, 3–E, 4–A, 5–B → `['C','D','E','A','B']`

**Zabłyśnij na lekcji:**
Pierwsi garncarze lepili naczynia ręcznie. Koło garncarskie, na którym naczynie obraca się podczas lepienia, wynaleziono znacznie później, w Mezopotamii.

Źródło: s. 14–16 (tekst i objaśnienia z gwiazdką)

---

#### P25 · `sortuj`
**Pytanie:** Paleolit czy neolit? Przyporządkuj każdą cechę do właściwej epoki.

**kategorie:** `['Paleolit', 'Neolit']` (indeks 0 = Paleolit, 1 = Neolit)

**elementy** (w tej kolejności wyświetlania):

| # | `t` | `k` |
|---|---|---|
| 1 | Uprawa ziemi i hodowla zwierząt | 1 (Neolit) |
| 2 | Jaskinie i namioty z kości mamuta okryte skórami | 0 (Paleolit) |
| 3 | Ubrania tkane z wełny i lnu | 1 (Neolit) |
| 4 | Koczowniczy, czyli wędrowny tryb życia | 0 (Paleolit) |
| 5 | Narzędzia z kamienia wygładzanego i przewiercanego, osadzone na trzonkach | 1 (Neolit) |
| 6 | Myślistwo i zbieractwo | 0 (Paleolit) |
| 7 | Trwałe domy z drewna lub gliny zmieszanej z trzciną | 1 (Neolit) |
| 8 | Ubrania szyte ze skór | 0 (Paleolit) |
| 9 | Osiadły tryb życia | 1 (Neolit) |
| 10 | Narzędzia z kamienia obłupywanego, by nadać mu kształt | 0 (Paleolit) |
| 11 | Gliniane wazy, misy i dzbany | 1 (Neolit) |
| 12 | Polowanie na mamuty | 0 (Paleolit) |

**Zabłyśnij na lekcji:**
Zapamiętaj pary przeciwieństw: **wędrówka ↔ osiadłość, jaskinia ↔ dom, polowanie ↔ pole, skóra ↔ tkanina, obłupywanie ↔ wygładzanie**.

Źródło: s. 16 („To, co najważniejsze”), s. 11, s. 14

---

### Kategoria 7: `d2-pf` – Prawda czy fałsz?

#### P26 · `pf`
**Pytanie:** Które zdania są prawdziwe, a które fałszywe?

**zdania:**

| lit. | `t` (zdanie) | `p` | `fix` (wyjaśnienie po odsłonięciu) |
|---|---|---|---|
| a | Człowiek rozumny pojawił się na Ziemi ok. 200 tysięcy lat temu. | `true` | Tak podaje podręcznik. Zajrzyj też do ciekawostki poniżej. |
| b | Ok. 40 tysięcy lat temu Europę porastały gęste lasy. | `false` | Trwał okres ochłodzenia: północ pokrywał **lądolód**, a na południu ciągnęła się **tundra** bez lasów. |
| c | Gromada ludzi paleolitu liczyła 20–30 osób. | `true` | *(puste)* |
| d | Już w starszej epoce kamiennej ludzie udomowili psa. | `true` | *(puste)* |
| e | Rolnictwo to tylko uprawa ziemi. | `false` | Rolnictwo to uprawa ziemi **i hodowla zwierząt**. |
| f | Młodsza epoka kamienna zaczęła się w tym samym czasie na całym świecie. | `false` | Na Bliskim Wschodzie zaczęła się ok. 8000 r. p.n.e., a w innych częściach świata **znacznie później**. |
| g | Mieszkańcy Bliskiego Wschodu jako pierwsi w dziejach zaczęli uprawiać ziemię. | `true` | *(puste)* |
| h | Siekiera z ostrzem osadzonym w wydrążonym trzonku była trwalsza od siekiery z otworem wywierconym w ostrzu. | `false` | Była **łatwiejsza do wykonania, ale mniej trwała**. |

**Zabłyśnij na lekcji:**
Nauka ciągle się rozwija! W 2017 r. ogłoszono odkrycie w Maroku kości, które wielu naukowców uznaje za szczątki ludzi rozumnych sprzed ok. 300 tysięcy lat. Dlatego w nowszych książkach możesz spotkać inną liczbę niż w podręczniku. Na sprawdzianie podaj tę z podręcznika.

Źródło: s. 11, 14–16

---

## 5. Ściągawka (pole `sciagawka`)

**Oś czasu** (segmenty od lewej):
1. **ok. 198 tys. p.n.e.** – pojawienie się człowieka rozumnego
2. **ok. 38 tys. p.n.e.** – ludzie rozumni przybywają do Europy
3. **ok. 18 tys. p.n.e.** – początek ocieplania się klimatu
4. **ok. 8000 – ok. 2500 p.n.e.** – młodsza epoka kamienna (neolit) na Bliskim Wschodzie

Pod osią podpis: „lat temu” − ok. 2000 = „p.n.e.” (np. 40 tys. lat temu ≈ 38 tys. p.n.e.).

**Porównanie (dwie kolumny):**

| | Paleolit (starsza epoka kamienna) | Neolit (młodsza epoka kamienna) |
|---|---|---|
| Tryb życia | koczowniczy, czyli wędrowny | osiadły |
| Schronienie | jaskinie, namioty z kości i ze skór | trwałe domy z drewna lub gliny zmieszanej z trzciną |
| Główne zajęcia | myślistwo i zbieractwo | rolnictwo: uprawa ziemi i hodowla zwierząt |
| Narzędzia | z kamienia obłupywanego | z kamienia wygładzanego, przewiercanego, osadzanego na trzonku |
| Ubrania | szyte ze skór | tkane z wełny i lnu |

**Karta: 🌾 Rewolucja neolityczna** – przejście od myślistwa i zbieractwa do rolnictwa. Skutki:
1. osiadły tryb życia,
2. udoskonalenie kamiennych narzędzi,
3. udomowienie kóz, owiec, bydła i świń,
4. wyżywienie większej liczby ludzi,
5. pierwsze rzemiosła: garncarstwo i tkactwo.

---

## 6. Rangi i komunikaty maskotki dla działu 2 (pola `rangi`, `start`)

**start:** `Witaj w epoce kamiennej! Zaczynamy od myśliwych, a skończymy na rolnikach. Za każde pytanie, które umiesz, przesypie się trochę mojego piasku!`

| `od` | `e` | `n` | `msg` |
|---|---|---|---|
| 0 | 🔥 | Strażnik ogniska | Iskra skrzesana! Piasek zaczął się sypać. ⏳ |
| 0.25 | 🏹 | Łowca mamutów | Brawo! Zostajesz Łowcą Mamutów. |
| 0.5 | 🌾 | Pierwszy rolnik | Ponad połowa za Tobą! Czas na pierwsze żniwa. |
| 0.75 | 🏺 | Mistrz garncarski | Mistrz garncarski! Jeszcze kilka pytań do tytułu Mistrza… |
| 1 | 🏆 | Mistrz epoki kamiennej | MISTRZ EPOKI KAMIENNEJ! Cały piasek przesypany, cały dział opanowany! 🏆 |

---

## 7. Weryfikacja merytoryczna (do wiadomości, nie renderować)

**Co sprawdzono**
- Każda odpowiedź jest zgodna z tekstem s. 11 i 14–16 (strony podano przy pytaniach). Obejmują one wszystkie pytania 1–10 z czerwonych ramek oraz polecenia A i B z „Pytań i poleceń”. Tabela „To, co najważniejsze” jest w całości w P6, P7 i P25.
- Rachunki: 200 000 − 2000 = 198 000; 40/20/10 tys. lat temu → 38/18/8 tys. p.n.e. (zgodne z osią czasu na s. 11); 8000 − 2500 = 5500; 198 000 − 8000 = 190 000; 190/200 = 95%; 10/200 doby = 72 min, czyli ok. 22:50; 3000 m / 237 m (wysokość PKiN) ≈ 12,7; skala osi: 190 000 lat = 190 cm, 5500 lat = 5,5 cm.
- Klucze dopasowań, kolejność w P20 i przyporządkowania w P25 sprawdzone pozycja po pozycji.
- Ciekawostki („Zabłyśnij na lekcji”) wykraczają poza podręcznik i zostały sprawdzone z wiedzą ogólną.

**Uwagi do treści podręcznika**
1. **Najstarsze kości człowieka rozumnego.** Podręcznik podaje 200 tysięcy lat. Znalezisko z Dżebel Irhud w Maroku (ogłoszone w 2017 r.) jest datowane na ok. 300 tysięcy lat i często uznawane za szczątki wczesnych ludzi rozumnych. Odpowiedzi trzymają się podręcznika; nowsze ustalenia pojawiają się tylko w ciekawostce do P26.
2. **Łuk.** Podręcznik: „kilkanaście tysięcy lat temu”. Niektóre nowsze badania wskazują na znacznie starsze groty strzał (nawet ponad 50 tysięcy lat), ale sprawa jest dyskutowana. Na stronie zostaje wersja z podręcznika, bez komentarza.
3. **Koniec młodszej epoki kamiennej.** W dziale 1 (oś epok na s. 9) młodsza epoka kamienna kończy się ok. 3500 r. p.n.e., razem z początkiem historii. W dziale 2 (s. 11 i 15) neolit na Bliskim Wschodzie trwa do ok. 2500 r. p.n.e. Pytania działu 2 używają dat 8000–2500 p.n.e. i nie zestawiają ich z działem 1. Nie dodawaj pytań, które łączą te dwie daty.
4. **Strony 12–13** nie zostały dostarczone. Numeracja pytań w podręczniku przechodzi z 2 (s. 11) do 3 (s. 14), więc na s. 12–13 prawdopodobnie nie ma pytań w ramkach, ale ich ewentualna treść nie jest tu uwzględniona.
5. „+5°C w lipcu na południu Europy” i „lądolód do 3 km” to dane z podręcznika, zostawione bez zmian.
