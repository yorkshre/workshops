## Choinka

Zbliżają się Święta, czas na prezenty ;) A przynajmniej na drzweka iglaste
w każdym centrum handlowym. W ramach ćwiczenia spróbujemy narysować
takie drzewko w konsoli.

Zaczniemy od najprostszej możliwej wersji zadania, aby później rozszerzyć
je do bardziej funkcjonalnej. Tak więc na zachętę, pół choinki:


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

Nasza choinka wygląda tak:

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

Nie wygląda to najgorzej, ale trochę pisania było. A co gdybyśmy chcieli
mniejszą choinkę ? Albo większą, złożoną z setek elementów do wydrukowania
na papierze A0 ? To stanowczo zbyt dużo pisania, nawet gdyby robić to
przy użyciu mnożenia napisów (``"*" * 100``, itd.). Ewidentnie jest to
czynność tak powtarzalna, że program może to zrobić za nas.


## Listy i pętla ``for``


Do wykonywania takich powtarzalnych czynności będą służyły nam pętle.
Pozostając w konwencji świątecznej, wyobraźmy sobie na chwilę, że
jesteśmy Świętym Mikołajem, który ma za zadanie dostarczyć wszystkim
prezenty.

Jak wiadomo, Mikołaj posiada listę osób, którym prezenty
się należa. Najprostszym podejściem, które gwarantuję, że nikogo nie
pominiemy będzie przechodzenie po kolei po liście i dostarczanie kolejnym
osobom ich prezentów. Abstrahując od fizycznych aspektów zadania [#speed]_,
procedura dostarczania prezentów mogłaby wygląć tak:

    Niech ListaOsób zawiera osoby którym należy się prezent.

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

* Słowa :keyword:`for`
* Nazwy którą chcemy nadawać kolejnym elementom.
* Słowa :keyword:`in`
* Wartości będącej listą lub nazwy która się do takiej odwołuje.
* Treści wciętej o jeden poziom (dokładnie tak samo jak to było w przypadku :keyword:`if`)

No tak, ale jeszcze nic nie powiedzieliśmy o listach. To dlatego, że
nie różnią się one zbytnio od ich intuicyjnego pojmowania w życiu
codziennym. Spokojnie możemy myśleć o listach w Pythonie myśleć tak samo,
jak o każdej innej liście (zakupów, gości na impreze, wyników z kolokwium, itd.)
zapisanej na kartce i ponumerowanej.

Tak więc zacznijmy od pustej kartki (włącz tryb interaktywny):

    >>> L = []
    >>> L
    []

W każdym momencie możemy sprawdzić ile mamy zapisanych elementów
na naszej liście za pomocą funkcji:`len`.

    >>> len(L)
    0

Stwórzmy inną listę (może być pod tą samą nazwą lub inną):

    >>> L = ["Ala", "Ola", "Jacek"]
    >>> len(L)
    3

Podobnie jak w przypadku krotek, kolejne elementy listy rozdzielamy
przecinkami. W przeciwieństwie do krotek, nawiasy ``[`` i ``]`` są obowiązkowe.

Aby podejrzeć jaki element znajduje się na konkretnej pozycji na
liście (pamiętaj, że liczymy pozycje od 0):

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

Możemy też wykorzystać pętle `for`, aby wykonać jakieś
instrukcje dla każdej jej elementu:

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
Problem ten rozwiąże nam funkcja `range` (czyli zakres, przedział).
Jeśli opis podany przez ``help(range)`` wyda ci się zbyt skomplikowany, oto
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

Funkcja `range` nie tworzy bezpośrednio listy, ale zwraca generator.
Generatory pozwalają tworzyć sekwencje wartości, nie zajmując nipotrzebnie
pamięci. Aby otrzymać listę z takiej sekwencji musimy użyć funkcji
:func:`list`.

Funkcja :func:`range` ma trzy formy. Najprostrza (i najczęściej używana),
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

`range` zaoczszędziło nam sporo pisania. Możemy zaoszczędzić
jeszcze więcej pomijając nazywanie samej listy:

    >>> for i in list(range(1, 5)):
    ...     print(i*"#")
    #
    ##
    ###
    ####

Gdy używamy słowa kluczowego`for`, nie musimy używać funkcji
`list`. `for` potrafi poradzić sobie z funkcją `range`, więc
można nasz program jeszcze uprościć:

    >>> for i in range(1, 5):
    ...     print(i*"#")
    #
    ##
    ###
    ####


Nic nie stoi na przeszkodzie aby pętla nie mogła się znajdować
w innej pętli. Należy jedynie pamiętać o odpowiednich wcięciach i
użyciu innych nazw, np. ``i`` i ``j`` (lub też bardziej adekwatnych do
zawartości listy):

    >>> for i in range(1, 3):
    ...    for j in range(2, 4):
    ...        print(i, j)
    1 2
    1 3
    2 2
    2 3

Korzystając z tej techniki możemy powtarzać nasz kawałek choinki:

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
tym programem i spróbuj go przerobić tak aby przy każdym z trzech powtórzeń
pierwszej (zewnętrznej) pętli, druga wykonywała się raz więcej. W ten sposób
powinniśmy otrzymać naszą pół-choinkę z początku rozdziału.


## Definiowanie funkcji


Widzieliśmy już jak funkcję rozwiązują wiele z naszych problemów. Jednak
nie rozwiązują ich wszystkich lub nie do końca tak jakbyśmy chcieli.
Musi wtedy sami rozwiązać dany problem. Jeśli występuję on często
w naszym programie, to miło by było mieć funkcję, która go rozwiązuje.

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
podajemy jak chcemy aby nasza funkcja się nazywała. W nawiasach musimy
podać jak mają zostać nazwane jej argumenty, gdy zostanie ona wywołana.
W kolejnych liniach zaś podajemy instrukcje, które mają zostać wykonane,
gdy użyjemy też funkcji.

Tak jak to widać na przykładzie, instrukcje w funkcji mogą zawierać
nazwy, które podaliśmy jako nazwy argumentów. Zasada działania jest
następująca - jeśli stworzyliśmy funkcję z trzema argumentami:

    >>> def foo(a, b, c):
    ...     print("FOO", a, b, c)

To wywołując ją, tak samo jak każdą inną wcześniej, musimy podać
wartości dla każdego z argumentów:

    >>> foo(1, "Ala", 2 + 3 + 4)
    FOO 1 Ala 9
    >>> x = 42
    >>> foo(x, x + 1, x + 2)
    FOO 42 43 44

Pamiętaj, że nazwy to tylko etykiety. Jeśli przewiesimy, etykietkę
z jednej wartości na inną, to inne etykiety się nie zmienią - tak
będzie też z argumentami:

    >>> def plus_five(n):
    ...     n = n + 5
    ...     print(n)
    >>> x = 43
    >>> plus_five(x)
    48
    >>> x
    43


Zwracanie wartości
------------------

Funkcje z których wcześniej korzystaliśmy miały jedną istotną własność,
której brakuje tym, które tworzyliśmy sami - zwracały wartość zamiast
natychmiast ją wypisywać. Aby osiągnąć ten sam efekt, należy użyć
instrukcji`return`. Jest to specjalna instrukcja, która
może występować jedynie w funkcjach.

Możemy teraz ulepszyć nasz kalkulator BMI dodając do niego funkcję
obliczającą BMI::

    def calc_bmi(height, weight):
        return weight / height ** 2

Na koniec rozwiążemy w elegacki sposób problem z końca poprzedniego rozdziału:


.. testcode::

    # xmas.py

    def print_triangle(n):
        for size in range(1, n+1):
            print(size * "*")

    for i in range(2, 5):
        print_triangle(i)


.. testoutput::

    *
    **
    *
    **
    ***
    *
    **
    ***
    ****


#Obiekty i klasy


Właściwie ten rozdział mógłby być tematem całej serii zajęć, my jednak
skupimy się na absolutnych podstawach, które będą nam potrzebne przy
pracy z Django.

Wartości to obiekty
-------------------

Wszystko co do tej pory nazywaliśmy wartością możemy nazwać też obiektem.
Widzieliśmy to na przykładzie liczb całkowitych, gdy :func:`help` wypisało
nam dziesiątki linii dodatkowych informacji na temat :func:`int`.

Każdy obiekt ma klasę
---------------------

Aby się dowiedzieć jaką wystarczy użyć funkcji :func:`type`:

    >>> type(2)
    <type 'int'>
    >>> type(2.0)
    <type 'float'>
    >>> type("Gżegżółka")
    <type 'str'>
    >>> x = 1, 2
    >>> type(x)
    <type 'tuple'>
    >>> type([])
    <type 'list'>

Gdy używamy w naszym programie liczby, spodziewamy się, że będzie się
ona zachowywać tak jak liczba - bazujemy na naszej intuicji.

Jednak Python musi dokładnie wiedzieć co znaczy być liczbą całkowitą,
np. co ma się stać gdy dodajemy dwie liczby, a co gdy je dzielimy.
Klasa dostarcza tych wszystkich informacji i więcej.

Sprawdź co oferuje nam klasa ``str`` za pomocą :func:`help`.
Zacytujemy tutaj jedynie kilka ciekawszych funkcji:

    >>> help(str.lower)
    Help on method_descriptor:
    <BLANKLINE>
    lower(...)
        S.lower() -> str
    <BLANKLINE>
        Return a copy of the string S converted to lowercase.
    <BLANKLINE>
    >>> help(str.upper)
    Help on method_descriptor:
    <BLANKLINE>
    upper(...)
        S.upper() -> str
    <BLANKLINE>
        Return a copy of S converted to uppercase.
    <BLANKLINE>
    >>> help(str.ljust)
    Help on method_descriptor:
    <BLANKLINE>
    ljust(...)
        S.ljust(width[, fillchar]) -> int
    <BLANKLINE>
        Return S left-justified in a Unicode string of length width. Padding is
        done using the specified fill character (default is a space).
    <BLANKLINE>
    >>> help(str.center)
    Help on method_descriptor:
    <BLANKLINE>
    center(...)
        S.center(width[, fillchar]) -> str
    <BLANKLINE>
        Return S centered in a Unicode string of length width. Padding is
        done using the specified fill character (default is a space)
    <BLANKLINE>

Wszystko to są operacje, które każdy napis potrafi wykonać. Możemy
się do nich dostać używając kropki i wywołując jak funkcję:

    >>> x = "Ala"
    >>> x.upper()
    u'ALA'
    >>> x.lower()
    u'ala'
    >>> x.center(9)
    u'   Ala   '

I jeszcze jedna istotna funkcjonalność każdej klasy - potrafi ona
stworzyć obiekt mający jej cechy (tzw. swoją instancję):

    >>> int()
    0
    >>> str()
    ''
    >>> list()
    []
    >>> tuple()
    ()

Podsumowując, poznaliśmy już klasy :func:`int`, :func:`str`, :func:`tuple`,
:func:`list`. Aby sprawdzić jakiej klasy jest wartość (obiekt) używamy funkcji
:func:`type`. Aby stworzyć instancję klasy (czyli nowy obiekt) wywołujemy
klasę podobnie jak wywoływaliśmy funkcję, dopisując nawiasy ``()``, na przykład
``int()``.

## Definiowanie klass


Podobnie jak możemy tworzyć własne funkcje, tak i możemy tworzyć
własne klasy. W gruncie rzeczy, klasa to nic innego jak zgrupowane
funkcje:



    class Dog(object):

        def bark(self):
            print("Woof! Woof!")



    class Dog(object):

        def bark(self):
            print("Woof! Woof!")

Klasy rozpoczynają się od słowa :keyword:`class`, po którym podajemy
nazwę nowej klasy. Czym jest ``(object)`` wyjaśni się później, gdy
będziemy chcieli stworzyć bardziej skomplikowane klasy.

Warto natomiast zwrócić uwagę na fakt, że każda funkcja w klasie musi mieć
conajmniej jeden argument. Jego wartością będzie obiekt z którego wywołaliśmy
tą funkcję (czyli to co przed kropką):


    burek = Dog()
    burek.bark()


    Woof! Woof!

Argument ten może nazywać się dowolnie, ale intuicyjne jest aby nazwać go ``self``.


### Atrybuty obiektów


Obiekty poza metodami (funckjami), mogą posiadać też atrybuty:



    burek = Dog()
    burek.name = "Burek"

    print(burek.name)


    Burek

Czasami chcemy aby każdy obiekt danej klasy miał jakiś atrybut, np. każdy
pies powinien mieć imię. Możemy dodać takie wymaganie definiując funkcję
o specjalnej nazwie ``__init__``:


    class Dog(object):

        def __init__(self, name):
            self.name = name

        def bark(self):
            return "Woof! %s! Woof!" % (self.name,)

    burek = Dog(u"Burek")
    pluto = Dog(u"Pluto")
    print(burek.bark())
    print(pluto.bark())

Tak to wygląda po uruchomieniu:

    Woof! Burek! Woof!
    Woof! Pluto! Woof!


### Pełna choinka


Poprzedni rozdział był dość teoretyczny, więc teraz postaramy się
skorzystać przynajmniej z części tej wiedzy kończąc nasz program
do wyświetlania choinki.

Dla przypomnienia::

    # xmas.py

    def print_triangle(n):
        for size in range(1, n+1):
            print(size * "*")

    for i in range(2, 5):
        print_triangle(i)

Jak możemy ulepszyć funkcję :func:`print_triangle`, aby wyświetlała
cały segment choinki, a nie tylko pół?

Przede wszystkim, ustalmy jak chcemy aby wyglądał wynik dla konrektnej
wartości argumentu ``n``. Wydaje się sensowne, aby ``n`` było szerokością.
Wtedy dla ``n = 5``, oczekiwalibyśmy::

      *
     ***
    *****

Warto zauważyć, że każda linia składa się z dwóch gwiazdek więcej
niż poprzednia. Możemy więc skorzystać z trzeciego argumentu :func:`range`:

    def print_segment(n):
        for size in range(1, n+1, 2):
            print(size * "*")

    print_segment(5)

Choinka prezentuje się tak:

    *
    ***
    *****

Nie do końca o to chodziło, bo brakuje wyrównania do środka. Z pomocą
przychodzi metoda `unicode.center` wspomniana w poprzednim rozdziale:

    def print_segment(n):
        for size in range(1, n+1, 2):
            print((size * "*").center(n))

    print_segment(5)
    
Wygląda to tak:

      *
     ***
    *****

Pojawia się jednak kolejny problem:


    def print_segment(n):
        for size in range(1, n+1, 2):
            print((size * "*").center(n))

    for i in range(3, 8, 2):
        print_segment(i)
        
Poniżej widać że nie wygląda to najlepiej:

     *
    ***
      *
     ***
    *****
       *
      ***
     *****
    *******

Jakoże z góry wiemy jakiej wielkości będzie najszerszy segment, możemy
dodać dodatkowy argument do`print_segment`, tak aby wyrównywać
do tej szerokości. Łącząc całą naszą dotychczasową wiedzę:

    raw_input.queue.append("7")

    def print_segment(n, total_width):
        for size in range(1, n+1, 2):
            print((size * "*").center(total_width))

    def print_tree(size):
        for i in range(3, size+1, 2):
            print_segment(i, size)

    print("Podaj wielkość choinki:")
    n = int(raw_input())
    print_tree(n)


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


## Zadanie dla chętnych

Stwórz klasę ``XMASTree`` która dla podanego rozmiaru i wywołaniu
metody ``draw``, wydrukuje poniższe obrazki (rozmiary 1, 2 i 3):

::

          *
         /|\
        /_|_\
          |

::

           *
          /|\
         /_|_\
          /|\
         / | \
        /__|__\
           |

::

            *
           /|\
          /_|_\
           /|\
          / | \
         /__|__\
           /|\
          / | \
         /  |  \
        /___|___\
            |



