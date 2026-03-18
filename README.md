# Algorytmy i Struktury Danych (ASD) w Pythonie

## O projekcie
Repozytorium zawiera zbiór autorskich implementacji fundamentalnych struktur danych oraz algorytmów obliczeniowych. Projekty zostały zrealizowane od zera w języku Python, bez użycia zewnętrznych bibliotek matematycznych (takich jak NumPy). 

Projekty te to praktyczne ćwiczenia z programowania. Skupiałem się w nich na pisaniu czystego kodu, zrozumieniu, jak struktury danych działają "pod maską" (np. operowanie na referencjach w miejsce klasycznych wskaźników z C) oraz na podstawowej optymalizacji algorytmów.

## Wykorzystane technologie
* **Python 3**
* **Podstawy OOP:** Tworzenie klas, metody magiczne (przeciążanie operatorów) i ukrywanie danych wewnętrznych.
* **Obsługa błędów:** Wyłapywanie wyjątków i zabezpieczanie programu przed wywaleniem się przy nietypowych danych wejściowych.

## Spis Treści (Projekty)

### 1. Jednokierunkowa Lista Wiązana (Singly Linked List)
* Obiektowa implementacja struktury węzłowej (`Node` / `LinkedList`).
* Realizacja koncepcji wskaźników przy użyciu referencji w Pythonie.
* Zaimplementowane operacje dodawania na początek/koniec oraz bezpieczne usuwanie węzłów.
* Odporność na błędy (np. próba usunięcia elementu z pustej listy nie przerywa działania programu).

### 2. Obiektowa Implementacja Macierzy (2D Array)
* Stworzenie struktury danych reprezentującej macierz za pomocą list zagnieżdżonych.
* Wykorzystanie metod magicznych (`__add__`, `__mul__`, `__eq__`, `__getitem__`) do natywnego używania operatorów matematycznych (+, *, ==).
* Walidacja wymiarów macierzy przed wykonaniem operacji algebraicznych.

### 3. Obliczanie Wyznacznika Macierzy - Metoda Chio
* Implementacja algorytmu sprowadzającego dużą macierz do mniejszych podmacierzy.
* Szybkie przerywanie obliczeń dla macierzy z rzędami lub kolumnami składającymi się z samych zer.
* Algorytm dynamicznej zamiany wierszy (ze zmianą znaku wyznacznika), który zapobiega błędowi dzielenia przez zero na pierwszej pozycji macierzy.

## Konfiguracja i Uruchamianie
Każdy skrypt zawiera własne bloki testowe (wywoływane przez `if __name__ == '__main__':`), co pozwala na ich niezależne uruchamianie i błyskawiczną weryfikację poprawności na gotowych danych. W repozytorium znajduje się również plik `.dockerignore`, który jest od razu dostępny dla każdego, kto sklonuje kod i będzie chciał zbudować z niego obraz u siebie – gwarantuje to czyste środowisko bez kopiowania śmieciowych plików systemowych.
