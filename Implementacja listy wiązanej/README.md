# Jednokierunkowa Lista Wiązana (Singly Linked List) w Pythonie

## O projekcie
Projekt zawiera w pełni obiektową implementację podstawowej struktury danych – **jednokierunkowej listy wiązanej**, zrealizowaną od zera w języku Python. 

W Pythonie referencje do obiektów pełnią funkcję wskaźników znanych z języków takich jak C czy C++. Architektura opiera się na dwóch głównych klasach:
* `element` – reprezentującej pojedynczy węzeł listy, przechowujący dane oraz referencję do kolejnego węzła (`next`).
* `my_List` – strukturze nadrzędnej, zarządzającej węzłami poprzez wskazanie na początek listy (`head`).

## Zaimplementowane funkcjonalności

Struktura udostępnia zestaw standardowych metod do zarządzania danymi:

### Transformatory (Modyfikacja struktury)
* `add(data)` – wstawia nowy element na początek listy (złożoność $O(1)$).
* `append(data)` – iteruje po strukturze i dołącza nowy element na jej koniec.
* `remove()` – bezpiecznie usuwa pierwszy element z listy.
* `remove_end()` – iteruje do przedostatniego węzła i bezpiecznie usuwa element z końca listy. Odporna na wywołania na pustej liście.
* `destroy_list()` – niszczy całą listę. Wykorzystuje wbudowany Garbage Collector Pythona poprzez ustawienie `head` na `None`.

### Obserwatory (Odczyt stanu)
* `is_empty()` – sprawdza, czy w liście znajdują się jakiekolwiek elementy.
* `length()` – iteruje po liście i zwraca aktualną liczbę elementów.
* `get()` – zwraca surowe dane z pierwszego elementu, ukrywając wewnętrzną reprezentację węzła.

## Przykład użycia (Testy integracyjne)
Kod zawiera wbudowany scenariusz testowy operujący na danych polskich uczelni wyższych. Dzięki nadpisaniu tzw. metody magicznej `__str__`, wywołanie `print(lista)` generuje czytelną, wizualną reprezentację struktury:

```text
-> ('UP', 'Poznań', 1919)
-> ('UW', 'Warszawa', 1915)
-> ('PG', 'Gdańsk', 1945)
-> ('AGH', 'Kraków', 1919)