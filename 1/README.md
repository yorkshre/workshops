#Wprowadzenie do Pythona


Zacznijmy od uruchomienia interpretera, który zainstalowaliśmy w poprzednim rozdziale. Uruchom:
```markdown
(warsztaty) ~$ python
Python 3.4.0 (...)
Type "copyright", "credits" or "license" for more information.
>>
```

Wcześniej pracowaliśmy w konsoli systemu operacyjnego i mogliśmy wydawać mu polecenia. Zachętą dla nas był ~$. Po uruchomieniu polecenia python zmienił się znak zachęty na >>>. To jest informacja dla nas, że teraz wydajemy wyłącznie polecenia w języku Python. Poprzednie polecenia (takie jak: cd, mkdir) nie będą działać. W tym momencie zaczynamy uczyć się nowego języka. Znaków >>> (podobnie jak ~$) nie wpisujemy sami.

Teraz możemy coś policzyć, np. wpisując 2 + 2:
```markdown
>>> 2 + 2
4
```
Python świetnie sprawdza się jako kalkulator:
```markdown
>>> 6 * 7
42
>>> 1252 - 38 * 6
1024
>>> (3 - 5) * 7
-14
>>> 21 / 7
3.0
>>> 3**2
9
>>> 5 / 2
2.5
```
Należy zwrócić szczególną uwagę, że ułamki dziesiętne zapisujemy zgodnie z zasadami języka angielskiego, czyli z kropką, a nie z przecinkiem. Przecinki będą nam służyły do definiowania :ref:`krotek <bmi-tuples>` (ang. tuple), ale o tym później.

##Przedstaw się

###Napisy

Same liczby to jednak trochę za mało do skutecznego porozumiewania się. Musimy więc nauczyć się posługiwać napisami (ang. string). Oto kilka przykładów:
```markdown
>>> "Hello World"
'Hello World'
>>> 'Foo Bar'
'Foo Bar'
>>> "Rock 'n' Roll"
"Rock 'n' Roll"
>>> 'My name is "James"'
'My name is "James"'
```
Napisy można również dodawać:
```markdown
>>> 'My name is ' + '"James"'
'My name is "James"'
```
oraz mnożyć przez liczby całkowite:
```markdown
>>> 'Hastur' * 3
'HasturHasturHastur'
```
Napis zawsze musi zaczynać się i kończyć tym samym znakiem. Może to być apostrof (') albo cudzysłów ("). Nie ma to wpływu na wartość napisu, tzn. wpisując "Batman" tworzymy napis Batman - cudzysłowowy nie są jego częścią, służą jedynie wskazaniu, że jest to napis (niestety, Python nie jest aż tak sprytny, aby się tego domyślić).

###Drukowanie napisów

Jak w takim razie przedstawić wartość w postaci czytelnej dla człowieka? Do tego posłuży nam funkcja :func:`print`:
```markdown
>>> print("Witaj świecie")
Witaj świecie
```
Możemy w ten sposób wypisać kilka napisów w jednej linii, bez dodawania ich do siebie. Zostaną one oddzielone od siebie spacjami:
```markdown
>>> print("Cześć, mam na imię", "Łukasz")
Cześć, mam na imię Łukasz
```
Funkcja :func:`print` ma też dużo więcej zastosowań, bo potrafi wypisać niemalże wszystko. Na razie jedynym innym znanym nam rodzajem wartości są liczby:
```markdown
>>> print(1)
1
>>> print(1, 2, 3)
1 2 3
>>> print("2 + 2 =", 2 + 2)
2 + 2 = 4
```
Na razie na tym skończymy naszą pracę z konsolą interaktywną. Aby z niej wyjść, wpisz poprostu quit():
```markdown
>>> quit()
```
Lub (szybciej) wciskając na klawiaturze Ctrl+D w przypadku Linuxa lub Ctrl+Z w przypadku Windowsa.

###Pliki źródłowe

Do tej pory cały nasz kod wykonywany był w tzw. trybie interaktywnym, w którym podajemy komendy pojedynczo i natychmiast dostajemy na nie odpowiedź. Jest to świetny sposób na eksperymentowanie i poznawanie nowych elementów języka, więc jeszcze do niego wrócimy.

Nasz pierwszy program może wyglądać tak:
```markdown
print("Cześć, mam na imię Łukasz.")
```
Zapisz ten program w pliku wizytowka.py, a następnie uruchom go z linii poleceń wykonując python wizytowka.py:
```markdown
(warsztaty) ~$ python wizytowka.py
Cześć, mam na imię Łukasz.
(warsztaty) ~$
```
Pojedynczy program może zawierać więcej niż jedno polecenie. Każde powinno znajdować się w osobnej linii, np.:
```markdown
print("Cześć,")
print()

print("Mam na imię Łukasz.")

print()
print("Papa.")
```

Puste linie pozwalają oddzielić wizualnie różne części programu, tak aby ułatwić rozczytanie jego treści. Tutaj rozdzieliliśmy nagłówek wiadomości od jej treści i zakończenia.

##Kalkulator BMI

Teraz napiszemy prosty program do kalkulacji BMI (Body Mass Index). Formuła do jego obliczenia jest następująca:

>BMI = (masa w kg) / (wzrost w metrach) do kwadratu

Umiemy dzielić, potęgować i wypisywać liczby. Stwórzmy więc nowy plik o nazwie bmi.py i spróbujmy napisać program obliczający nasze BMI:

Po uruchomieniu:
```markdown
$ python bmi.py
```
W wyniku dostaniemy:

Jak widać, nasz program wymaga jeszcze nieco pracy:

1. Jeśli ktoś inny chciałby skorzystać z tego programu, musi on zmienić jego treść. W dodatku musi się domyślić, które wartości ma zmienić.
2. Osobie, która nie zna na pamięć tabelki BMI, wartość 21.387755102040817 nic nie powie.
3. Wypisywanie tylu miejsc po przecinku jest zbędne. BMI mierzy się z dokładnością do dwóch miejsc po przecinku.

Ale programowanie to w końcu sztuka rozwiązywania problemów, więc do dzieła. Przy okazji poznamy kilka nowych elementów Pythona.

##Nazwy

Spróbujmy więc rozwiązać pierwszy problem. Na początek chcielibyśmy, aby nasz program był bardziej czytelny, tj. aby dla czytającego było oczywiste, która wartość to waga, a która wzrost.

Dlatego nadamy tym wartościom nazwy:

Wynik działania programu się nie zmienił:

Aby lepiej zrozumieć działanie nazw, wróćmy na chwilę do trybu interaktywnego i nadajmy kilka nazw:
```markdown
>>> x = 42
>>> PI = 3.1415
>>> name = "Amelia"
>>> print("Rzeczy:", x, PI, name)
Rzeczy: 42 3.1415 Amelia
```
Możemy nadać wiele nazw tej samej wartości:
```markdown
>>> y = x
>>> print(x, y)
42 42
```
Możemy też dowolnie zmieniać wartość przypisaną do nazwy. Nie musi ona być tego samego typu, co poprzednio:
```markdown
>>> x = 13
>>> print(x)
13
>>> x = "Skarabeusz"
>>> print(x)
Skarabeusz
```
Nazwy są niezależne od siebie. Przed chwilą przypisaliśmy do x nową wartość, jednak wartość przypisana do y pozostaje bez zmian:
```markdown
>>> print(y)
42
Note
```

##Dla znających inne języki.

Pewnie dziwi Cię, dlaczego nie używamy pojęcia "zmienna". To dlatego, że nazwy w Pythonie nie działają tak samo jak zmienne. W większości języków operacja y = x stworzyłaby kopię wartości x i wstawiła ją do zmiennej y.

W Pythonie nic nie jest po kryjomu kopiowane. y staje się jedynie alternatywną nazwą dla tej samej wartości. Jeśli zmienimy tę wartość, tak x, jak i y pokażą to samo.

W naszym przykładzie nie zmieniliśmy wartości liczby 42, a jedynie wartość przypisaną do x (w szczególności wartości liczb są niezmienne, choć w 1897 r. izba niższa stanu Indiana zatwiedziła zmianę wartości liczby pi na 3 - wniosek upadł dopiero w Senacie). Dlatego print(y) da nam 42.

Jak już widzieliśmy w naszym programie, nazwy możemy nadawać też wynikom obliczeń oraz używać nazw w obliczeniach:
```markdown
>>> w = 65.5
>>> h = 175.0 / 100.0
>>> bmi = w / h**2
>>> print(w, h, bmi)
65.5 1.75 21.387755102040817
```
Jednak raz wyliczona wartość się nie zmienia:

```markdown
>>> w = 64
>>> print(w, h, bmi)
64 1.75 21.387755102040817
```
dopóki nie każemy Pythonowi wyliczyć jej ponownie:

```markdown
>>> bmi = w / h**2
>>> print(w, h, bmi)
64 1.75 20.897959183673468
```

Na koniec tego rozdziału dodamy kilka komentarzy do naszego programu, aby użytkownik (włącznie z nami!) pamiętał, że wagę należy podać w kilogramach.

Komentarze pozwalają umieścić w pliku dowolny tekst, który zostanie zignorowany przez interpreter Pythona.

Komentarzem w Pythonie jest wszystko po znaku # aż do końca linii:
```markdown
# Waga w kilogramach
weight = 65.5
# Wzrost w metrach
height = 1.75

bmi = weight / height**2 # Obliczamy BMI
print("Twoje BMI to:", bmi)
```

#Wywoływanie funkcji

Nasz program wygląda już całkiem nieźle, ale użytkownik, chcąc policzyć swoje BMI, nadal musi zmieniać treść programu. Wygodniej byłoby, gdyby po uruchomieniu programu mógł wpisać wymagane wartości w konsoli i odczytać swoje BMI.

Aby móc napisać taki program, musimy nauczyć się operowania funkcjami. Pierwszą, która poznamy, będzie :func:`help`:
```markdown
>>> help
Type help() for interactive help, or help(object) for help about object.
```
:func:`help` jest bardzo przyjazną funkcją, bo sama nam mówi, jak powinniśmy jej używać. Pomaga też w zrozumieniu innych funkcji:
```markdown
>>> help(input)
Help on function input in module builtins:
<BLANKLINE>
input(...)
    input([prompt]) -> string
<BLANKLINE>
    Read a string from standard input.  The trailing newline is stripped.
    If the user hits EOF (Unix: Ctl-D, Windows: Ctl-Z+Return), raise EOFError.
    On Unix, GNU readline is used if enabled.  The prompt string, if given,
    is printed without a trailing newline before reading.
<BLANKLINE>

```
Właśnie :func:`input` będziemy używać do wczytywania danych od użytkownika. Jak czytamy w opisie, wczytuje ona napis:
```markdown
>>> input()  # doctest: +SKIP
ala ma kota
'ala ma kota'
```
W tym momencie zapoznamy się z "wywoływaniem funkcji". Robi się to za pomocą nawiasów (), które informują interpreter, że ma daną funkcję wywołać. Wywołanie funkcji spowoduje uruchomienie jej. Jeżeli zapomnimy wpisać () po nazwie funkcji, nie zostanie ona wywołana i nie dostaniemy żadnego błędu (ponieważ jest to ciągle poprawny program).

Wywołane funkcje najczęściej _zwracają_ jakąś wartość. Funkcja :func:`input` zwraca napis, dlatego możemy użyć jej wszędzie tam gdzie do tej pory używaliśmy napisów.

Przykładowo możemy zapamiętać wczytany napis pod jakąś nazwą:

Czy to już wystarcza nam do poprawienia programu?

Jak widać, Python nie wie, o co nam chodzi i jakiego właściwie wyniku oczekujemy. Jak pokazaliśmy wcześniej, zarówno napisy (str), jak i liczby (int) można do siebie dodawać. Python nie wie, czy chodzi nam o liczbę 63.5, czy o napis "60.53". Tylko my to wiemy i musimy zawrzeć tę informację w programie.

Poznajmy więc dwie kolejne funkcje:

```markdown

>>> help(int)  # doctest: +NORMALIZE_WHITESPACE
Help on class int in module builtins:
<BLANKLINE>
class int(object)
 |  int(x=0) -> integer
 |  int(x, base=10) -> integer
 |
 |  Convert a number or string to an integer, or return 0 if no arguments
 |  are given.  If x is a number, return x.__int__().  For floating point
 |  numbers, this truncates towards zero.
 |
 |  ...
 
 ```
oraz

```markdown
>>> help(float)  # doctest: +NORMALIZE_WHITESPACE
Help on class float in module builtins:
<BLANKLINE>
class float(object)
 |  float(x) -> floating point number
 |
 |  Convert a string or number to a floating point number, if possible.
 |
 |  ...
 ```
Funkcja :func:`help` nie omieszkała nas poinformować, iż w rzeczywistości :func:`int` i :func:`float` nie są funkcjami, lecz klasami (o czym będzie więcej później) - stąd też informacja na temat wszystkich innych rzeczy, do których można ich użyć. Nas na razie interesuje jedynie podstawowa funkcjonalność zamiany napisów na liczby odpowiedniego typu.

Przetestujmy :func:`int` i :func:`float`:
```markdown
>>> int("0")
0
>>> int(" 63 ")
63
>>> int("60.5")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '60.5'
>>> float("0")
0.0
>>> float(" 63 ")
63.0
>>> float("60.5")
60.5
```
Zanim skorzystamy z nowo poznanych funkcji w naszym programie, skonstruujmy oczekiwany plan jego działania:

1. Poproś użytkownika o podanie wzrostu
2. Wczytaj od użytkownika napis i zapamiętaj go pod nazwą height
3. Zamień napis na liczbę z ułamkiem
4. Poproś użytkownika o podanie wagi
5. Wczytaj od użytkownika napis i zapamiętaj pod nazwą weight
6. Zamień napis na liczbę z ułamkiem
7. Korzystając z zapamiętanych wartości, oblicz BMI i zapamiętaj jako bmi
8. Wypisz obliczone BMI
9. Nie powinno nas zaskoczyć, że te osiem punktów można wprost przełożyć na osiem linii naszego programu (nie licząc odstępów):

Powyższy program możesz zapisać do pliku bmi.py i uruchomić python bmi.py. W efekcie powinniśmy dostać:

Podsumowując: aby wywołać funkcję, musimy znać jej nazwę (poznaliśmy dotąd część: :func:`print`, :func:`help`, :func:`input`, :func:`int`, :func:`float` i :func:`quit`), oraz wiedzieć, jakich danych ona od nas oczekuje (tzw. lista argumentów).

Podanie samej nazwy nie wywoła funkcji, powie nam jedynie, że to funkcja:

```markdown
>>> input  # doctest: +SKIP
<built-in function input>
```
Aby wywołać funkcję, musimy dopisać nawiasy po jej nazwie:

```markdown
>>> input()  # doctest: +SKIP
```
W tym momencie funkcja zostanie wykonana przez Pythona.

Wszystkie argumenty podajemy w nawiasach. Aby podać więcej niż jeden, rozdzielamy je przecinkiem:
```markdown
>>> int("FF", 16)
255
```
#Sprawdzanie warunków

Przejdźmy do naszego następnego problemu. Chcemy, aby nasz program, korzystając z poniższej tabeli, wypisał odpowiednią dla obliczonego BMI klasyfikację:

| BMI           | Klasyfikacja    | 
| ------------- |:---------------:|
|< 18,5         | niedowaga       | 
| 18,5 – 24,99  | waga prawidłowa |  
| ≥ 25,0        | nadwaga         |  

Skorzystamy więc z tzw. instrukcji warunkowej :keyword:`if`, która wykonuje dalszą część programu pod podanym warunkiem:

Porównania: prawda czy fałsz?

Kolejnym elementem, o którym jeszcze nie wspomnieliśmy, są porównania. Dla liczb działają one identycznie jak na lekcjach matematyki:
```markdown
>>> 2 > 1
True
>>> 1 == 2
False
>>> 1 == 1.0
True
>>> 10 >= 10
True
>>> 13 <= 1 + 3
False
>>> -1 != 0
True
```
Wynikiem porównania jest zawsze True albo False. Porównania można łączyć w bardziej skomplikowane warunki za pomocą słów :keyword:`and` oraz :keyword:`or`:

```markdown
>>> x = 5
>>> x < 10
True
>>> 2*x > x
True
>>> (x < 10) and (2*x > x)
True
>>> (x != 5) and (x != 4)
False
>>> (x != 5) and (x != 4) or (x == 5)
True
```

##Wcięcia

Kolejna rzecz, na którą warto zwrócić uwagę, to wcięcia w kodzie. Otwórz tryb interaktywny i wpisz prosty warunek, np.:
```markdown
>>> if 2 > 1:
...
```
Na razie nic się jeszcze nie wydarzyło, o czym świadczą kropki ... zamiast zachęty >>>, którą dotąd widzieliśmy. Python oczekuje od nas dalszych instrukcji, które mają być wykonane, jeśli warunek 2 > 1 okaże się prawdziwy. Sprawmy, żeby wypisał "OK":

```markdown

>>> if 2 > 1:
... print("OK")
  File "<stdin>", line 2
    print("OK")
        ^
IndentationError: expected an indented block
```
Niestety, nie udało się nam. Python musi wiedzieć, czy instrukcja, którą wpisaliśmy, jest kontynuacją :keyword:`if` czy kolejną instrukcją nieobjętą warunkiem. W tym celu musimy wciąć nasz kod:

```markdown
>>> if 2 > 1:
...  print("OK")
...
OK
```
Wystarczy do tego jedna spacja albo TAB. Jednak wszystkie linie, które mają się wykonywać po sobie, muszą być wcięte tak samo:
```markdown
>>> if -1 < 0:
...  print("A")
...   print("B")
  File "<stdin>", line 3
    print("B")
    ^
IndentationError: unexpected indent

>>> if -1 < 0:
...     print("A")
...   print("B")
  File "<stdin>", line 3
    print("B")
            ^
IndentationError: unindent does not match any outer indentation level

>>> if -1 < 0:
...   print("A")
...   print("B")
...
A
B

```
Aby uniknąć chaosu, większość programistów Pythona używa czterech spacji na każdy poziom wcięcia. My też będziemy tak robić:
```markdown
>>> if 2 > 1:
...     if 3 > 2:
...         print("OK")
...     else:
...         print("FAIL")
...     print("DONE")
OK
DONE
```
Co, jeśli nie?

Samo :keyword:`if` właściwie by nam wystarczyło do napisania naszego programu:
```markdown

if bmi < 18.5:
    print("niedowaga")
if bmi >= 18.5:
    if bmi < 25.0:
        print("waga prawidłowa")
if bmi >= 25.0:
    print("nadwaga")
```
Jednak użyliśmy jeszcze :keyword:`else` i :keyword:`elif`, aby nie musieć powtarzać podobnych warunków oraz zwiększyć czytelność. W bardziej skomplikowanych programach może nie być oczywiste na pierwszy rzut oka, że kolejny warunek jest przeciwieństwem poprzedniego.

Korzystając z :keyword:`else` mamy gwarancję, że podane tam instrukcje zostaną wykonane tylko jeśli nie zostały wykonane instrukcje wpisane pod :keyword:`if`:

```markdown
if bmi < 18.5:
    print("niedowaga")
else:
    # jeśli nasz program wykonuje tę instrukcję,
    # to na pewno bmi >= 18.5 !
    if bmi < 25.0:
        print("waga prawidłowa")
    else:
        # teraz na pewno bmi >= 25.0, więc nie musimy
        # już tego sprawdzać
        print("nadwaga")
 ```
Zwróć szczególną uwagę na wcięcia. ;) Każde użycie :keyword:`else`, będzie powodować, że nasz kod będzie coraz bardziej wcięty. Jest to bardzo uciążliwe, gdy mamy do sprawdzenia kilka czy kilkanaście wykluczających się warunków. Dlatego autorzy języka dodali drobne "usprawnienie" w postaci instrukcji :keyword:`elif`, która pozwala od razu sprawdzić kolejny warunek:
```markdown
if n < 1:
    print("jeden")
elif n < 2:
    # jeśli nie było n < 1, a jest n < 2
    print("dwa")
elif n < 3:
    # jeśli żaden z poprzednich warunków nie zaszedł, tj.
    # n >= 1 i n>= 2, ale n < 3
    print("trzy")
else:
    # trolle umieją liczyć jedynie do trzech
    print("dużo")
```
##Formatowanie napisów

Ostatnim problemem, o którym wspomnieliśmy, była zbyt duża ilość cyfr w wypisywanym BMI. Ze wszystkich trzech jest on najprostszy do rozwiązania, dlatego zostawiliśmy go sobie na koniec naszej "przygody" z kalkulatorem BMI.

Wiemy już, że napisy można dodawać do siebie oraz mnożyć przez liczby całkowite. Zaraz zobaczymy, że można też wykonać na nich operację formatowania. Jednak najpierw potrzebny nam będzie jeszcze jeden typ danych (oprócz napisów i liczb, które już znamy).

##Krotki

Na samym początku wspomnieliśmy już, że nie możemy używać przecinka w liczbach, bo będzie nam potrzebny później do krotek. A oto i one:

```markdown
>>> 1, 2, 3
(1, 2, 3)
>>> ("Ala", 15)
('Ala', 15)
>>> x = 1,5
>>> print(x)
(1, 5)
Krotka to nic innego jak kilka wartości zgrupowanych w jedną. Wartości, które chcemy zgrupować, rozdzielamy przecinkami. Dla zwiększenia czytelności możemy całość otoczyć nawiasami, ale nie jest to konieczne - z wyjątkiem przypadku, gdy chcemy zgrupować zero elementów (jakkolwiek dziwnie może to brzmieć):

>>> ()
()
```

Krotki można ze sobą łączyć:

```markdown
>>> names = ("Paulina", "Kowalska")
>>> details = (27, 1.70)
>>> names + details
('Paulina', 'Kowalska', 27, 1.7)
```
Mogą też zawierać inne krotki, np. informację o punkcie na mapie możemy zgrupować w następujący sposób:
```markdown
>>> point = ("Nazwa punktu", (x, y))
gdzie x i y to jakieś liczby.
```
Do zgrupowanych wartości możemy odwołać się używając ich pozycji w krotce (licząc od zera), np.:
```markdown 
>>> p = (10, 15)
>>> p[0]  # pierwsza wartość
10
>>> p[1]  # druga wartość
15
```

##Formatowanie

Wracając do naszego programu: aktualnie jego wynik sprowadza się do jednej linijki. Teraz chcemy wypisać zarówno BMI jako liczbę oraz przedział, w którym się mieści, tj.:

Twoje BMI jest równe: 21.39 (waga prawidłowa)
Zmodyfikuj aktualny program tak, aby obliczone BMI było dostępne pod nazwą bmi, a nazwa przedziału pod nazwą category. Wtedy będziemy mogli użyć :func:`print` i uzyskać pożądany wynik:

No prawie, nadal mamy zbyt dużo cyfr. W dodatku mielibyśmy problem, gdybyśmy chcieli np. wygenerować taki napis i zapamiętać pod jakąś nazwą, bo korzystamy z :func:`print` do rozdzielania elementów. Na szczęście jest lepszy sposób:
```markdown
>>> bmi = 21.387755102040817
>>> category = "waga prawidłowa"
>>> wynik = "Twoje BMI: %f (%s)" % (bmi, category)
>>> wynik
'Twoje BMI: 21.387755 (waga prawid\u0142owa)'
>>> print(wynik)
Twoje BMI: 21.387755 (waga prawidłowa)
```

Mamy tutaj napis i krotkę połączone znakiem %. Napis jest szablonem, który będziemy wypełniać wartościami z krotki. Miejsca do wstawienia oznaczone są również procentem (%). Następująca po nim litera określa jakiego rodzaju wartość będziemy chcieli wstawić w to miejsce. I tak, liczbom całkowitym odpowiada i jak integer (zamiennie używa się też d jak decimal), napisom s jak string, a liczbom zmiennoprzecinkowym f jak float:

```markdown
>>> "Napis: %s, Liczby: %d %f" % ("Ala", 10, 3.1415)
'Napis: Ala, Liczby: 10 3.141500'
```
Teraz zamiast dziewięciu miejsc po przecinku zawsze dostajemy sześć, jednak formatowanie ma tę zaletę, że pozwala nam na większą kontrolę poprzez wstawienie pomiędzy % a znak f dodatkowych informacji, np. jeśli chcemy wyświetlić tylko dwa miejsca po kropce:

```markdown
>>> "%.2f" % 3.1415
'3.14'
>>> "%.2f" % 21.387755102040817
'21.39'
```
Opcji formatowania jest mnóstwo, więc nie będziemy ich tu wszystkich pokazywać. Jedną z bardziej przydatnych jest wyrównanie do konkretnej liczby znaków:

Możemy też wyrównać napis do lewej dodając - przed liczbą znaków:

Wyrównanie na środek pozostawiamy jako ćwiczenie dla czytelnika. ;)

##Podsumowanie

W tym rozdziale poznaliśmy podstawy składni Pythona. Wiemy jak zapisać liczby całkowite, liczby zmiennoprzecinkowe, napisy oraz krotki z nich złożone.

Poznaliśmy funkcję :func:`print`, która wypisuje informacje użytkownikowi oraz funkcję :func:`input`, która je od niego wczytuje.

Wiemy też, że wcięcia mogą mieć znaczenie, szczególnie gdy chcemy użyć instrukcji :keyword:`if` (również w połączeniu z :keyword:`else` i :keyword:`elif`).

Umiemy stworzyć plik z programem i go uruchomić. Nasz program prosi użytkownika, aby odpowiedział na kilka prostych pytań, wykonuje obliczenia i prezentuje wynik w użytecznej dla niego formie.

Całkiem sporo jak na nasz pierwszy program. Przed nami jeszcze dużo pracy, ale jak najbardziej możemy być dumni z tego co udało nam się zrobić do tej pory.
