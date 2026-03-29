# Tablica Mieszająca (Hash Table) z Adresowaniem Owartym

## O projekcie
Projekt zawiera autorską implementację tablicy mieszającej (Hash Table) w języku Python, stworzoną bez użycia wbudowanego typu `dict`. Celem projektu jest demonstracja mechanizmów rozwiązywania kolizji oraz zarządzania strukturą danych o stałym rozmiarze.

Implementacja obsługuje klucze będące zarówno liczbami całkowitymi, jak i ciągami znaków (z wykorzystaniem sumowania kodów ASCII).

## Architektura i Rozwiązywanie Kolizji
Tablica wykorzystuje **adresowanie otwarte**, co oznacza, że wszystkie elementy są przechowywane bezpośrednio w tablicy o rozmiarze `size`. W przypadku wystąpienia kolizji (gdy wyliczony indeks jest już zajęty), program poszukuje kolejnego wolnego miejsca przy użyciu **próbkowania kwadratowego** według wzoru:

$$index = (hash(key) + c_1 \cdot i + c_2 \cdot i^2) \pmod{size}$$

* Domyślnie $c_1=1, c_2=0$, co odpowiada **próbkowaniu liniowemu**.
* Możliwa jest zmiana parametrów na próbkowanie kwadratowe (np. $c_1=0, c_2=1$).

## Rozwiązanie problemu usuwania (Lazy Deletion)
W tablicach z adresowaniem otwartym zwykłe usunięcie elementu (wpisanie `None`) przerywa "łańcuch próbkowania", co uniemożliwia odnalezienie elementów dodanych później. 

W tym projekcie problem rozwiązano poprzez wprowadzenie flagi `is_deleted` w klasie `Element`. 
- **Remove:** Zamiast usuwać obiekt, oznaczamy go jako "usunięty".
- **Search:** Przeszukuje tablicę dalej, nawet jeśli napotka element z flagą `is_deleted`.
- **Insert:** Pozwala nadpisać miejsce oznaczone jako usunięte, optymalizując wykorzystanie pamięci.

## Główne Funkcjonalności
* `insert(key, value)` – Wstawianie danych. Jeśli klucz istnieje, następuje aktualizacja wartości. W przypadku braku miejsca wyświetla komunikat "Brak miejsca".
* `search(key)` – Wyszukiwanie wartości dla podanego klucza. Zwraca `value` lub `None`.
* `remove(key)` – Logiczne usuwanie elementu. W przypadku braku klucza wyświetla "Brak danej".
* `__str__` – Wizualizacja tablicy w formacie zbliżonym do słownika Python: `{klucz:wartość, ...}`.

## Scenariusze Testowe
Projekt zawiera dwie funkcje testowe demonstrujące zachowanie tablicy:
1. **Test 1:** Standardowe operacje (wstawianie, nadpisywanie, usuwanie) oraz obsługa kluczy typu string. Pokazuje poprawność wyszukiwania elementów po usunięciu innych danych z łańcucha kolizyjnego.
2. **Test 2:** Analiza zajętości tablicy przy specyficznych kluczach (wielokrotności rozmiaru tablicy). Porównanie efektywności próbkowania liniowego oraz kwadratowego w kontekście klastrowania danych.



## Przykładowy Wynik (Wizualizacja)
```text
{1:A, 2:B, 3:C, 4:D, None, 18:F, 31:G, 8:H, 9:I, 10:J, 11:K, 12:L, 13:M}
Poszukiwanie klucza 5: None
Poszukiwanie klucza 31: G
Po usunięciu klucza 5:
{1:A, 2:B, 3:C, 4:D, None, 18:F, 31:G, 8:H, 9:I, 10:J, 11:K, 12:L, 13:M}