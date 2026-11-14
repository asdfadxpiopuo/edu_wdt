# Wstęp do telekomunikacji — najważniejsze informacje

Poniżej znajdziesz uporządkowane streszczenie całego załączonego PDF-a. Numery w nawiasach odnoszą się do **stron pliku PDF**, a nie numeracji slajdów.

## 1. Czym jest telekomunikacja?

**Telekomunikacja** to przekazywanie informacji na odległość za pomocą sygnałów.

Najprostszy system telekomunikacyjny składa się z:

1. **Nadawcy** — źródła informacji.
2. **Wiadomości** — np. tekstu, dźwięku lub obrazu.
3. **Kodowania** — sposobu przedstawienia informacji.
4. **Nadajnika** — urządzenia wytwarzającego sygnał.
5. **Medium i kanału transmisyjnego** — drogi, którą sygnał dociera do celu, np. światłowodu lub przestrzeni.
6. **Odbiornika i odbiorcy** — urządzenia odbierającego sygnał i osoby lub systemu korzystającego z informacji.

Podczas transmisji sygnał może być osłabiany i zakłócany, więc odbiornik musi odtworzyć wiadomość mimo niedoskonałości kanału. *(s. 3–5, 58)*

### Historia w skrócie

Rozwój telekomunikacji prowadził od telegrafu optycznego, przez telegraf elektryczny i telefon, do radia, telewizji, łączności satelitarnej oraz sieci cyfrowych. Ważnym krokiem było powstanie **ARPANET-u** w 1969 r. i rozwój transmisji pakietowej, na której opiera się współczesny Internet. *(s. 15–52)*

---

## 2. Informacja, bity i kodowanie

### System binarny

**Bit** przyjmuje jedną z dwóch wartości: `0` albo `1`. Dane cyfrowe — liczby, tekst, obrazy i dźwięk — są przedstawiane jako ciągi bitów.

Przykład:

`1000011₂ = 64 + 2 + 1 = 67₁₀`

Jeżeli mamy **N możliwych symboli** i każdemu chcemy przypisać kod o tej samej długości, potrzebujemy co najmniej:

$$
n=\lceil\log_2 N\rceil
$$

bitów na symbol. Na przykład dla 17 symboli potrzeba 5 bitów, bo 4 bity dają tylko 16 różnych kombinacji. *(s. 60–64)*

### Przykłady kodowania

- **ASCII** — standard kodowania znaków; podstawowy ASCII ma 7 bitów.
- **UTF-8** — kodowanie tekstu wykorzystujące od 1 do 4 bajtów na znak.
- **RGB** — reprezentacja koloru za pomocą składowych czerwonej, zielonej i niebieskiej; często po 8 bitów na każdą składową. *(s. 65)*

---

## 3. Kompresja i entropia

### Kompresja bezstratna

Kompresja bezstratna zmniejsza ilość danych tak, aby po dekompresji dało się odzyskać **dokładnie oryginalną informację**.

Jedna z metod to **kodowanie Huffmana**:

- częściej występujące symbole dostają krótsze kody;
- rzadsze symbole dostają dłuższe kody;
- w rezultacie średnia liczba bitów na symbol może być mniejsza niż przy kodach o stałej długości.

Kodowanie Huffmana wykorzystuje drzewo binarne. Przykład z wykładu pokazuje, jak zakodować wyniki rzutów kostką średnio przy użyciu **2 bitów na symbol**. *(s. 69–73, 77–79)*

### Entropia Shannona

**Entropia** opisuje średnią ilość informacji przypadającą na symbol źródła. Zależy od prawdopodobieństw poszczególnych symboli:

$$
H(X)=-\sum_i p_i\log_2 p_i
$$

gdzie $p_i$ to prawdopodobieństwo wystąpienia symbolu.

Intuicja:

- gdy symbole są równie prawdopodobne, źródło jest mniej przewidywalne;
- gdy niektóre symbole dominują, źródło jest bardziej przewidywalne i łatwiejsze do kompresji.

Dla przykładu z wykładu entropia wynosi około **1,96 bitu na symbol**, a kod Huffmana uzyskuje 2 bity na symbol. Entropia jest teoretycznym punktem odniesienia dla granicy średniej kompresji bezstratnej danego źródła. *(s. 74–80)*

---

## 4. Sygnał, pasmo i przepustowość

### Sygnał i pasmo

**Sygnał** jest fizyczną reprezentacją informacji — może to być np. zmienne w czasie napięcie elektryczne albo fala elektromagnetyczna.

**Pasmo** określa zakres częstotliwości wykorzystywanych przez sygnał lub dostępnych w kanale. Wyraża się je w hercach (**Hz**).

**Transformata Fouriera** pozwala analizować sygnał w dziedzinie częstotliwości: pokazuje, z jakich składowych częstotliwościowych się on składa. *(s. 85–96)*

### Stosunek sygnału do szumu

**SNR** to stosunek mocy sygnału do mocy szumu:

$$
SNR=\frac{P_{\text{sygnału}}}{P_{\text{szumu}}}
$$

Im wyższy SNR, tym z reguły łatwiej poprawnie odebrać informację. W praktyce znaczenie mają również zakłócenia pochodzące od innych nadajników. *(s. 89–90, 189)*

### Twierdzenie Shannona–Hartleya

Dla idealizowanego kanału z szumem maksymalna teoretyczna szybkość niezawodnej transmisji wynosi:

$$
C=B\log_2(1+SNR)
$$

- $C$ — pojemność kanału w bitach na sekundę;
- $B$ — szerokość pasma w Hz;
- $SNR$ — stosunek mocy w **skali liniowej**, nie bezpośrednio w dB.

**Wniosek:** większe pasmo i lepszy stosunek sygnału do szumu pozwalają przesyłać więcej informacji. Nie oznacza to jednak, że rzeczywista sieć zawsze osiąga tę teoretyczną granicę. *(s. 81–84)*

---

## 5. Media transmisyjne

Media dzielimy na **przewodowe** i **bezprzewodowe**.

| Medium | Charakterystyka i zastosowanie |
|---|---|
| **Skrętka / para symetryczna** | Popularna w sieciach komputerowych i telefonii. Skręcenie przewodów ogranicza wpływ zakłóceń i przesłuchów. |
| **Kabel koncentryczny** | Ma ekran ograniczający zakłócenia. Wykorzystywany m.in. w telewizji kablowej i instalacjach antenowych. |
| **Światłowód** | Przesyła informację za pomocą światła. Ma małe tłumienie i jest odporny na zakłócenia elektromagnetyczne. |
| **Fale radiowe** | Umożliwiają transmisję bez kabla i mobilność użytkowników, ale są podatne na zakłócenia oraz zmiany warunków propagacji. |

### Co pogarsza transmisję?

1. **Tłumienie** — sygnał słabnie podczas propagacji. Dla mocy tłumienie można wyrazić jako:

   $$
   L=10\log_{10}\left(\frac{P_{\text{wej}}}{P_{\text{wyj}}}\right)\ \text{dB}
   $$

2. **Dyspersja** — składowe sygnału rozchodzą się w różny sposób, przez co impulsy mogą się poszerzać i nakładać.
3. **Zakłócenia i przesłuchy** — niepożądane sygnały utrudniają odbiór.
4. **Odbicia** — występują np. przy niedopasowaniu impedancji albo na elementach toru optycznego.

**dB** wyraża stosunek wielkości, natomiast **dBm** oznacza poziom mocy odniesiony do 1 mW. *(s. 103–123)*

---

## 6. Modulacja i multipleksacja

### Modulacja

**Modulacja** to zmienianie parametrów sygnału nośnego w sposób zależny od przesyłanej informacji.

| Typ | Co jest zmieniane? |
|---|---|
| **AM / ASK** | Amplituda |
| **FM / FSK** | Częstotliwość |
| **PM / PSK** | Faza |
| **QAM** | Amplituda i faza |

AM, FM i PM to przykłady modulacji analogowych; ASK, FSK, PSK i QAM są używane do reprezentacji danych cyfrowych.

**OFDM** wykorzystuje wiele blisko rozmieszczonych, wzajemnie ortogonalnych podnośnych. Dane są rozdzielane pomiędzy nie, a poszczególne podnośne mogą używać np. QAM. *(s. 124–129)*

### Multipleksacja

**Multipleksacja** pozwala przesyłać wiele strumieni informacji z wykorzystaniem wspólnego zasobu:

- **FDM** — podział według częstotliwości;
- **TDM** — podział według czasu;
- **WDM** — podział według długości fali w światłowodzie;
- **CDM** — rozdzielenie za pomocą kodów;
- **SDM** — podział przestrzenny;
- **PDM** — wykorzystanie różnych polaryzacji.

**Różnica:** modulacja określa, jak informacja jest reprezentowana w sygnale, a multipleksacja — jak współdzielić zasób przez wiele strumieni. *(s. 130–131)*

---

## 7. Łączność bezprzewodowa i sieci komórkowe

### Anteny i propagacja

**Antena** przekształca sygnał elektryczny w falę radiową podczas nadawania i odwrotnie podczas odbioru. Anteny mogą być m.in. kierunkowe lub dookólne.

W uproszczonym modelu wolnej przestrzeni moc odbierana maleje proporcjonalnie do kwadratu odległości: po podwojeniu odległości spada około **czterokrotnie**. W rzeczywistym środowisku wpływają na nią także ściany, budynki, drzewa, odbicia i opady. *(s. 181–187)*

### Dlaczego zasięg się zmienia?

Sygnał może docierać do odbiornika różnymi drogami. Fale nakładają się na siebie, wzmacniając lub osłabiając sygnał. Powoduje to **zaniki**, które mogą zmieniać się wraz z położeniem i otoczeniem użytkownika. Problemem są też interferencje od innych nadajników. *(s. 189–190)*

### Idea sieci komórkowej

Obszar działania sieci jest dzielony na **komórki** obsługiwane przez stacje bazowe. Pozwala to ponownie wykorzystywać zasoby radiowe w różnych miejscach i obsłużyć więcej użytkowników.

Ponieważ widmo jest współdzielone, użytkowników trzeba rozdzielać m.in. według **częstotliwości, czasu, kodu lub przestrzeni**. *(s. 192–197)*

### Generacje sieci

- **1G** — analogowa telefonia komórkowa.
- **2G** — cyfrowa telefonia, np. GSM.
- **3G** — większe możliwości transmisji danych i multimedia.
- **4G** — szybka transmisja pakietowa, LTE.
- **5G** — rozwój w kierunku większych przepływności, obsługi wielu urządzeń oraz niskich opóźnień.

Trzy scenariusze 5G:

- **eMBB** — szybki dostęp do danych i multimediów;
- **mMTC** — obsługa dużej liczby urządzeń, np. IoT;
- **URLLC** — komunikacja o wysokiej niezawodności i małych opóźnieniach. *(s. 227–230)*

### Inne zastosowania fal radiowych

Fale radiowe służą również do **lokalizacji i nawigacji**, np. GPS, oraz do obrazowania. Położenie można wyznaczać m.in. na podstawie czasu nadejścia lub mocy sygnałów. *(s. 198–204)*

---

## 8. Internet i transmisja pakietowa

**Internet to „sieć sieci”** — połączone ze sobą sieci operatorów, przez które komunikują się urządzenia końcowe i serwery.

### Pakiety i routing

W transmisji pakietowej dane są dzielone na **pakiety**. Pakiet zawiera dane oraz informacje sterujące, np. adres źródła i celu.

**Router** kieruje pakiet dalej na podstawie informacji o trasach. Pakiety mogą:

- przejść różnymi drogami;
- dotrzeć w innej kolejności;
- zostać utracone — wtedy, zależnie od usługi i protokołu, mogą być retransmitowane.

**DNS** tłumaczy nazwy domenowe na adresy IP. *(s. 206–214)*

### Protokoły i warstwy

**Protokół** to zestaw reguł określających format wiadomości i sposób komunikacji między urządzeniami.

Modele warstwowe porządkują zadania sieci. W uproszczonym modelu TCP/IP wyróżnia się warstwy:

1. aplikacji;
2. transportową;
3. sieciową;
4. dostępu do sieci.

Model **OSI** dzieli komunikację bardziej szczegółowo — na siedem warstw. *(s. 209–210)*

### Multimedia i streaming

- **Multipleks telewizyjny** umożliwia przesyłanie wielu programów w jednym strumieniu.
- **OTT** to dostarczanie treści przez Internet.
- **CDN** to sieć serwerów dystrybuujących treści bliżej użytkowników, co może zmniejszać opóźnienia i obciążenie serwera źródłowego.
- W **streamingu adaptacyjnym** materiał jest podzielony na fragmenty dostępne w różnych jakościach; aplikacja wybiera wersję stosownie do dostępnej przepustowości. *(s. 216–222)*

---

## 9. Część branżowa: infrastruktura i AI

Prezentacja Nokia pokazuje praktyczną stronę budowy sieci: znaczenie **routerów IP, sieci światłowodowych, centrów danych i automatyzacji**. Rozwój usług AI zwiększa wymagania dotyczące przepustowości, opóźnień, niezawodności i zużycia energii. AI może też wspierać zarządzanie samą siecią.

Wspomniano również o **Containerlab** — narzędziu open source do tworzenia wirtualnych laboratoriów sieciowych i testowania konfiguracji. *(s. 132–170)*

---

## Najważniejsze rzeczy do zapamiętania

1. **Schemat transmisji:** informacja → kodowanie → sygnał → kanał → odbiór i odtworzenie informacji.
2. **Entropia** opisuje średnią ilość informacji; kompresja wykorzystuje przewidywalność danych.
3. **Pasmo i SNR** ograniczają możliwą szybkość transmisji — opisuje to wzór Shannona–Hartleya.
4. **Tłumienie, dyspersja, zakłócenia i odbicia** pogarszają jakość sygnału.
5. **Modulacja** koduje informację w parametrach sygnału, a **multipleksacja** pozwala współdzielić zasoby.
6. **Sieci radiowe** zapewniają mobilność, ale muszą radzić sobie z interferencjami, zanikami i ograniczonym widmem.
7. **Internet przesyła dane w pakietach**, a routery wybierają ich dalszą drogę.
8. **Sieć komórkowa dzieli obszar na komórki**, by efektywniej wykorzystywać częstotliwości i obsługiwać wielu użytkowników.
