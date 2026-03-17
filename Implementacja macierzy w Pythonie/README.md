# Obiektowa Implementacja Macierzy (2D Array) w Pythonie

## O projekcie
Projekt przedstawia implementację dwuwymiarowej tablicy (macierzy) od zera, zrealizowaną w pełni obiektowo. Zamiast korzystać z gotowych bibliotek naukowych (jak NumPy), struktura została zbudowana z wykorzystaniem mechanizmów wbudowanych języka Python. 

Kluczowym aspektem projektu jest zastosowanie **metod magicznych (dunder methods)**, co pozwala na naturalne i intuicyjne operowanie na macierzach przy pomocy standardowych operatorów matematycznych, upodabniając składnię do rozwiązań znanych z języka C/C++.

## Zaimplementowane funkcjonalności

### 1. Przeciążanie operatorów (Magic Methods)
Klasa `Matrix` pozwala na wykonywanie klasycznych operacji algebraicznych z wykorzystaniem standardowych operatorów:
* `__add__ (+)` – dodawanie dwóch macierzy o zgodnych wymiarach.
* `__mul__ (*)` – właściwe mnożenie macierzowe (iloczyn macierzy), z walidacją zgodności liczby kolumn pierwszej macierzy z liczbą wierszy drugiej.
* `__eq__ (==)` – głębokie porównywanie wartości wszystkich elementów obu macierzy.
* `__getitem__ ([])` – bezpośredni dostęp do elementów poprzez indeksowanie w stylu C: `macierz[wiersz][kolumna]`.
* `__str__` – formatowanie obiektu do postaci czytelnego ciągu znaków, pozwalające na eleganckie wyświetlanie struktury w konsoli przy użyciu instrukcji `print()`.

### 2. Konstruktor (Inicjalizacja)
Metoda `__init__` implementuje wzorzec zachowania zbliżony do przeciążania konstruktorów w innych językach. Przyjmuje dwa typy argumentów inicjalizujących:
* **Lista list (`List[List[int]]`)** – tworzy macierz bezpośrednio z podanych wartości.
* **Krotka rozmiarów (`Tuple[int, int]`)** – tworzy macierz o podanych wymiarach i wypełnia ją wartością domyślną (standardowo `0`, z możliwością podania własnej).

### 3. Enkapsulacja i Hermetyzacja
Wewnętrzna struktura przechowująca dane (`__matrix`) została sprywatyzowana (name mangling). Dostęp do niej oraz jej modyfikacja z zewnątrz odbywa się wyłącznie poprzez zdefiniowany interfejs publiczny klasy (np. metody `size()` oraz przeciążony operator indeksowania).

### 4. Transpozycja Macierzy
Projekt zawiera zewnętrzną funkcję `transpose(m: Matrix)`, która realizuje operację transpozycji. Funkcja ta celowo operuje wyłącznie na publicznym interfejsie obiektu (`size()` oraz `[]`), demonstrując prawidłowe podejście do manipulacji ukrytymi danymi struktury.

## Przykładowe użycie i formatowanie wyjścia

Zaimplementowana metoda `__str__` dba o odpowiednie wyrównanie znaków. Zgodnie ze scenariuszem testowym, kod dla operacji transpozycji, dodawania i mnożenia generuje czysty wynik bez zbędnych opisów:

```text
|  1 -1 |
|  0  3 |
|  2  1 |

|  2  1  3 |
|  0  4  2 |

|  5  1 |
|  4  2 |