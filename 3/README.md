# Pętla for i choinka

Nie ma nic gorszego niż konieczność wielokrotnego wykonywania tej samej czynności. Pewnie dlatego prawdopodobnie wiele osób mając problem z zaśnięciem liczy barany. Nie ma to nic wspólnego z cudownymi właściwościami usapiającymi tych uroczych ssaków - powodem jest to, że ciągłe powatarzanie czegoś jest nużące, a umysłowi łatwiej się wyłączyć, jeśli tylko nie jest skupiony na czymś interesującym.

Ci programiści, którzy nie mają problemów z zaśnieciem również nieszczególnie przepadaja za powtarzaniem się. Dużym szczęściem jest, występowanie w większości języków programowania pętli for. Służy ona do automatycznego powtarzania innych instrukcji programistycznych i bloków kodu.

W tym rozdziale przyjrzymy się pętlom for, jak również innemu typowi pętli dostępnemu w języku Python: pętli while.

## Używanie pętli for

Aby pięciokrotnie wyświetlić słowo cześć w Pythonie, możemy napisać:

```
>>>print("cześć")
cześć
>>>print("cześć")
cześć
>>>print("cześć")
cześć
>>>print("cześć")
cześć
>>>print("cześć")
cześć
```

Ale jest to raczej męczące. Aby się nie męczyć, możemy użyć pętli for, aby zmniejszyć ilość pisania oraz powtarzania:
```
>>> for x in range (0,5):
...     print("cześć")
...
cześć
cześć
cześć
cześć
cześć
```
Jak widzicie użyliśmy funkcji range, można jej użyć do utworzenia listy liczb z przedziału od liczby początkowej do liczby o 1 mniejszej od liczby końcowej. Zdaję sobie sprawę z tego, że może brzmieć to trochę niejasno, więc połączmy funkcję range z funkcją list, aby dowiedzieć się, jak to działa. Funkcja range w zasadzie nie tworzy listy liczb, ale zwraca tzw. iterator, czyli typ obiektu w języku Python, który został zaprojektowany z myślą o pętlach.

Gdy jednak połączymy funkcję range z funkcją list, uzyskamy listę z liczbami:
```
>>> print(list(range(10,20)))
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
>>>
```
W przypadki pętli for, kod tak naprawdę nakazuje Pythonowi wykonać pewne zadania:
* Rozpocząc odliczanie od 0 i zakończyć przed dotarciem do 5
* Wartość każdej kolejnej wyliczanej liczby zapisywać w zmiennej x.

Następnie Python wykonuje blok kodu. Zwróc uwagę, że na początku tego wiersza znajdują się cztery dodatkowe spacje. Gdybyśmy wpisali kod w środowisku programistycznym (IDLE), wcięcia wykonywane byłyby automatycznie.

Gdy wciśniemy ENTER po wpisaniu drugiego wiersza, program pięć razy wyświetli nam "cześć". Możemy nawet zliczyć, używając x w naszej instrukcji print:
```
>>> for x in range(0,5):
...     print("cześć %s" %x)
...
cześć 0
cześć 1
cześć 2
cześć 3
cześć 4
```

Dla porównania zauważmy, jeżeli znów pozbędziemy się pętli for, nasz kod może wyglądać mniej więcej tak:

```markdown
>>> x=0
>>> print("cześć %s" %x)
cześć 0
>>> x=1
>>> print("cześć %s" %x)
cześć 1
>>> x=2
>>> print("cześć %s" %x)
cześć 2
>>> x=3
>>> print("cześć %s" %x)
cześć 3
>>> x=4
>>> print("cześć %s" %x)
cześć 4
>>>
```
W ten sposób użycie pętli uchroniło nas tak naprawdę przed pisaniem ośmiu dodatkowych wierszy kodu. Programiści nie cierpią się powtarzać, dlatego pętla for należy do najpopularniejszych instrukcji w językach programowania.

# Choinka

Mimo, że święta już dawno minęły choinki są na czasie. W ramach ćwiczenia spróbujemy narysować takie drzewko w konsoli.

Zaczniemy od najprostszej możliwej wersji zadania, aby później rozszerzyć je do bardziej funkcjonalnej. Tak więc, na zachętę, pół choinki:

    print("*")
    print("**")
    print("***")
    print("*")
    print("**")
    print("***")
    print("****")
    print("*")
    print("**")
    print("***")
    print("****")
    print("*****")
    print("******")

Po uruchomieniu wygląda tak:

    *
    **
    ***
    *
    **
    ***
    ****
    *
    **
    ***
    ****
    *****
    ******
Nie wygląda to najgorzej, ale trochę pisania było. A co, gdybyśmy chcieli
mniejszą choinkę? Albo większą, złożoną z setek elementów do wydrukowania
na papierze A0? To stanowczo zbyt dużo pisania, nawet gdyby robić to
przy użyciu mnożenia napisów (``"*" * 100``, itd.). Ewidentnie jest to
czynność tak powtarzalna, że program może to zrobić za nas.


## Listy i pętla ``for``

Do wykonywania takich powtarzalnych czynności będą służyły nam pętle.
Pozostając w świątecznym klimacie, wyobraźmy sobie na chwilę, że
jesteśmy Świętym Mikołajem, który ma za zadanie dostarczyć wszystkim
prezenty.

Jak wiadomo, Mikołaj posiada listę osób, którym należą się prezenty.
Najprostszym podejściem, które gwarantuje, że nikogo nie
pominiemy, będzie przechodzenie po kolei po liście i dostarczanie kolejnym
osobom ich prezentów. Abstrahując od fizycznych aspektów zadania [#speed]_,
procedura dostarczania prezentów mogłaby wyglądać tak::

    Niech ListaOsób zawiera osoby, którym należy się prezent.

    Dla każdej osoby (dalej znanej jako Osoba), będącej na ListaOsób:
        Dostarcz prezent do Osoba

Formatowanie powyższego tekstu nie jest przypadkowe. Właściwie jest
to zamaskowany program w Pythonie:

    gift_list = people_who_deserve_gifts()

    for person in gift_list:
        deliver_gift(person)
        print("Dostarczono prezent dla:", person)
    print("Dostarczono wszystkie prezenty")

Większość rzeczy powinna już wyglądać znajomo. Wywołujemy tutaj dwie funkcje:
`people_who_deserve_gifts` i `deliver_gift` - jak one działają,
wie tylko Mikołaj. Wynikowi wywołania pierwszej z nich nadajemy nazwę
`gift_list`, aby móc się później do tej wartości odwołać (tak samo jak w opisie powyżej).

Nowym elementem jest sama pętla, która składa się z:

* słowa :keyword:`for`,
* nazwy, którą chcemy nadawać kolejnym elementom,
* słowa :keyword:`in`,
* wartości będącej listą lub nazwy która się do takiej odwołuje,
* treści wciętej o jeden poziom (dokładnie tak samo, jak w przypadku :keyword:`if`).

No tak, ale wciąż nie powiedzieliśmy niczego o listach. To dlatego, że
nie różnią się one zbytnio od ich intuicyjnego pojmowania w życiu
codziennym. Spokojnie możemy myśleć o listach w Pythonie tak samo,
jak o każdej innej liście (zakupów, gości na impreze, wyników z kolokwium, itd.)
zapisanej na kartce i ponumerowanej.

Zacznijmy od pustej kartki (włącz tryb interaktywny):

    >>> L = []
    >>> L
    []

W każdym momencie możemy sprawdzić, ile mamy zapisanych elementów
na naszej liście - robimy to za pomocą funkcji :func:`len`.

    >>> len(L)
    0

Stwórzmy inną listę (może być pod tą samą nazwą lub inną):

    >>> L = ["Ala", "Ola", "Jacek"]
    >>> len(L)
    3

Podobnie jak w przypadku krotek, kolejne elementy listy rozdzielamy
przecinkami. Inaczej niż w przypadku krotek, nawiasy ``[`` i ``]`` są obowiązkowe.

Aby podejrzeć, jaki element znajduje się na konkretnej pozycji na
liście (pamiętaj, że liczymy pozycje od 0), wpisujemy:

    >>> L[0]
    'Ala'
    >>> L[1]
    'Ola'
    >>> L[2]
    'Jacek'
    >>> L[3]
    Traceback (most recent call last):
     File "<stdin>", line 1, in <module>
    IndexError: list index out of range

Możemy też wykorzystać pętle`for`, aby wykonać jakieś
instrukcje dla każdego elementu na liście:

    >>> for name in L:
    ...     print("Imie:", name)
    ...
    Imie: Ala
    Imie: Ola
    Imie: Jacek

W ten sam sposób możemy wydrukować pierwszą cześć naszej pół-choinki:

    >>> lst = [1, 2, 3]
    >>> for n in lst:
    ...     print("*"*n)
    ...
    *
    **
    ***

No tak, ale nadal musieliśmy ręcznie wypisać zawartość całej listy.
Problem ten rozwiąże nam funkcja`range` (czyli zakres, przedział).
Jeśli opis podany przez ``help(range)`` wyda Ci się zbyt skomplikowany, oto
kilka przykładów:

    >>> list(range(2, 5, 1))
    [2, 3, 4]
    >>> list(range(1, 11, 2))
    [1, 3, 5, 7, 9]
    >>> list(range(1, 11))
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    >>> list(range(1, 2))
    [1]
    >>> list(range(2))
    [0, 1]

Funkcja`range` nie tworzy bezpośrednio listy, ale zwraca generator.
Generatory pozwalają tworzyć sekwencje wartości, nie zajmując niepotrzebnie
pamięci. Aby otrzymać listę z takiej sekwencji, musimy użyć funkcji
`list`.

Funkcja`range` ma trzy formy. Najprostsza (i najczęściej używana),
tworzy sekwencję od 0 do podanej liczby. Pozostałe formy pozwalają podać
początek zakresu oraz krok. Utworzona sekwencja nigdy nie zawiera końca
podanego zakresu.

Wydrukujmy więc większą choinkę:

    >>> lst = list(range(1, 11))
    >>> lst
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    >>> for i in lst:
    ...     print("*"*i)
    *
    **
    ***
    ****
    *****
    ******
    *******
    ********
    *********
    **********

:func:`range` zaoszczędziło nam sporo pisania. Możemy zaoszczędzić
jeszcze więcej, jeśli pominiemy nazwanie samej listy:

    >>> for i in list(range(1, 5)):
    ...     print(i*"#")
    #
    ##
    ###
    ####

Gdy używamy słowa kluczowego`for`, nie musimy używać funkcji
`list`. `for` potrafi poradzić sobie z funkcją `range`, więc
można nasz program uprościć jeszcze bardziej:

    >>> for i in range(1, 5):
    ...     print(i*"#")
    #
    ##
    ###
    ####


Nic nie stoi na przeszkodzie, aby jedną pętlę umieścić wewnątrz innej.
Należy jedynie pamiętać o odpowiednich wcięciach i
użyciu innych nazw, np. ``i`` i ``j`` (lub też bardziej adekwatnych do
zawartości listy):

    >>> for i in range(1, 3):
    ...    for j in range(2, 4):
    ...        print(i, j)
    1 2
    1 3
    2 2
    2 3

Dzięki temu możemy powtarzać nasz kawałek choinki:

    >>> for i in range(3): # powtórz 3 razy
    ...    for size in range(1, 4):
    ...        print(size*"*")
    *
    **
    ***
    *
    **
    ***
    *
    **
    ***

Zanim przejdziesz do kolejnego rozdziału, stwórz plik ``xmas.py`` z
tym programem i spróbuj go przerobić tak, aby przy każdym z trzech powtórzeń
pierwszej (zewnętrznej) pętli, druga wykonywała się jeden raz więcej. W ten sposób
powinniśmy otrzymać naszą pół-choinkę z początku rozdziału.


## Definiowanie funkcji


Widzieliśmy już, w jaki sposób funkcje rozwiązują wiele z naszych problemów. Jednak
nie rozwiązują ich wszystkich - a przynajmniej nie do końca tak, jak chcielibyśmy.
Musimy wtedy sami rozwiązać dany problem. Jeśli występuje on często
w naszym programie, to miło byłoby mieć funkcję, która zrobi to za nas.

Python daje nam taką możliwość:

    >>> def print_triangle(n):
    ...     for size in range(1, n+1):
    ...         print(size*"*")
    ...
    >>> print_triangle(3)
    *
    **
    ***
    >>> print_triangle(5)
    *
    **
    ***
    ****
    *****

Przyjrzyjmy się bliżej tzw. definicji funkcji :func:`print_triangle`:

    def print_triangle(n):
        for size in range(1, n+1):
            print(size*"*")

Definicja funkcji zaczyna się zawsze od słowa`def`. Następnie
podajemy nazwę, którą wybraliśmy dla naszej funkcji. W nawiasach musimy
wskazać, jak mają zostać nazwane jej argumenty, gdy zostanie ona wywołana.
W kolejnych liniach zaś podajemy instrukcje, które mają zostać wykonane,
gdy użyjemy tej funkcji.

Jak widać na przykładzie, instrukcje w funkcji mogą zawierać
nazwy, które podaliśmy jako nazwy argumentów. Zasada działania jest
następująca - jeśli stworzyliśmy funkcję z trzema argumentami:

    >>> def foo(a, b, c):
    ...     print("FOO", a, b, c)

to wywołując ją (tak samo jak każdą inną wcześniej), musimy podać
wartości dla każdego z argumentów:

    >>> foo(1, "Ala", 2 + 3 + 4)
    FOO 1 Ala 9
    >>> x = 42
    >>> foo(x, x + 1, x + 2)
    FOO 42 43 44

Pamiętaj, że nazwy to tylko etykiety. Jeśli zmienimy etykietkę
z jednej na inną, to pozostałe etykiety się nie zmienią - tak
będzie też z argumentami:

    >>> def plus_five(n):
    ...     n = n + 5
    ...     print(n)
    >>> x = 43
    >>> plus_five(x)
    48
    >>> x
    43


### Zwracanie wartości


Funkcje, z których wcześniej korzystaliśmy, miały jedną istotną własność,
której brakuje tym, które stworzyliśmy sami - zwracały wartość zamiast
natychmiast ją wypisywać. Aby osiągnąć ten sam efekt, należy użyć
instrukcji`return`. Jest to specjalna instrukcja, która
może występować jedynie w funkcjach.

Możemy teraz ulepszyć nasz kalkulator BMI, dodając do niego funkcję
obliczającą BMI::

    def calc_bmi(height, weight):
        return weight / height ** 2

Na koniec rozwiążemy w elegacki sposób problem z końca poprzedniego rozdziału:



    # xmas.py

    def print_triangle(n):
        for size in range(1, n+1):
            print(size * "*")

    for i in range(2, 5):
        print_triangle(i)

Wygląda to tak:

    *
    **
    *
    **
    ***
    *
    **
    ***
    ****


## Pełna choinka

Poprzedni rozdział był dość teoretyczny, więc teraz postaramy się
skorzystać przynajmniej z części tej wiedzy, kończąc nasz program
do wyświetlania choinki.

Dla przypomnienia::

    # xmas.py

    def print_triangle(n):
        for size in range(1, n+1):
            print(size * "*")

    for i in range(2, 5):
        print_triangle(i)

Jak możemy ulepszyć funkcję`print_triangle`, aby wyświetlała
cały segment choinki, a nie tylko pół?

Przede wszystkim ustalmy, jak ma wyglądać wynik dla konrektnej
wartości argumentu ``n``. Wydaje się sensowne, aby ``n`` było szerokością.
Wtedy dla ``n = 5`` oczekiwalibyśmy::

      *
     ***
    *****

Warto zauważyć, że każda linia składa się z dwóch gwiazdek więcej
niż poprzednia. Możemy więc skorzystać z trzeciego argumentu`range`:


    def print_segment(n):
        for size in range(1, n+1, 2):
            print(size * "*")

    print_segment(5)

Po uruchomieniu wygląda to tak:

    *
    ***
    *****

Nie do końca o to chodziło, bo brakuje wyrównania do środka. Z pomocą
przychodzi metoda`unicode.center` wspomniana w poprzednim rozdziale:


    def print_segment(n):
        for size in range(1, n+1, 2):
            print((size * "*").center(n))

    print_segment(5)

Oto nasza pełna choinka:

      *
     ***
    *****

Pojawia się jednak kolejny problem:



    def print_segment(n):
        for size in range(1, n+1, 2):
            print((size * "*").center(n))

    for i in range(3, 8, 2):
        print_segment(i)

Nie wygląda to tak jakbyśmy chcieli:

     *
    ***
      *
     ***
    *****
       *
      ***
     *****
    *******

Jako że z góry wiemy jakiej wielkości będzie najszerszy segment, możemy
dodać kolejny argument do`print_segment`, tak aby wyrównywać
do tej szerokości. Łącząc całą naszą dotychczasową wiedzę:


    def print_segment(n, total_width):
        for size in range(1, n+1, 2):
            print((size * "*").center(total_width))

    def print_tree(size):
        for i in range(3, size+1, 2):
            print_segment(i, size)

    print("Podaj wielkość choinki:")
    n = int(input())
    print_tree(n)

Jak widać poniżej osiągnęliśmy upragniony efekt. Tak wygląda nasza finał naszego zadania:

    Podaj wielkość choinki:
    7
       *
      ***
       *
      ***
     *****
       *
      ***
     *****
    *******
