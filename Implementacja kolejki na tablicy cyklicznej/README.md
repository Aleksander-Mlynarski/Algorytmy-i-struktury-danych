# Kolejka Cykliczna z Dynamiczną Realokacją (Dynamic Circular Queue)

## O projekcie
Repozytorium zawiera implementację kolejki typu FIFO (First-In-First-Out) zrealizowaną od zera przy użyciu **bufora cyklicznego** (Circular Array). 

Zamiast polegać na wbudowanych, wysokopoziomowych mechanizmach zarządzania rozmiarem w Pythonie, projekt symuluje zachowanie niskopoziomowych tablic o stałym rozmiarze. Wewnętrzna reprezentacja opiera się na listach statycznych zainicjalizowanych wartościami `None`, a zarządzanie rozmiarem i spójnością pamięci realizowane jest całkowicie manualnie.

## Mechanika i Architektura Pamięci
* **Podwójne Indeksowanie:** Struktura zarządzana jest przez dwa niezależne wskaźniki: indeks odczytu (początek kolejki) oraz indeks zapisu (koniec kolejki).
* **Efekt Cykliczności (Wrap-around):** Po osiągnięciu fizycznego końca przypisanej pamięci (tablicy), wskaźniki "zawijają się" na jej początek (indeks 0), co optymalizuje wykorzystanie wolnych komórek bez konieczności ciągłego przesuwania elementów.
* **Dynamiczna Realokacja (Array Doubling):** Gdy bufor ulega przepełnieniu (indeks zapisu "dogania" indeks odczytu), algorytm natychmiastowo alokuje nową, **dwukrotnie większą** przestrzeń w pamięci. Następnie dane są sekwencyjnie przepisywane z uwzględnieniem "wyprostowania" struktury cyklicznej w celu zachowania ciągłości FIFO. Pamięć początkowa jest ustawiona na 5 elementów.

## Interfejs Publiczny (API)
Struktura udostępnia klasyczne transformatory i obserwatory:
* `enqueue(data)` – Wstawia element na miejsce zapisu i aktualizuje indeks. Wyzwala realokację pamięci w przypadku przepełnienia.
* `dequeue()` – Pobiera i usuwa element z miejsca odczytu, przesuwając indeks. Odporna na wywołania na pustej strukturze (zwraca `None`).
* `peek()` – Zwraca element z początku kolejki bez jego usuwania.
* `is_empty()` – Weryfikuje stan kolejki sprawdzając przecięcie się wskaźników odczytu i zapisu.
* `__str__` – Zwraca logiczny ciąg danych (od pierwszego do ostatniego dodanego elementu), ukrywając wewnętrzną cykliczność tablicy.

## Mechanizmy Diagnostyczne
Na potrzeby weryfikacji architektury zaimplementowano metodę debugującą, która wprost wypisuje surowy stan wewnętrznej tablicy Pythona. Pozwala to na "prześwietlenie" klasy i wizualną ocenę przemieszczania się wartości oraz poprawności realokacji elementów wraz z pustymi komórkami (`None`).

## Scenariusz Testowy (Integration Test)
Dołączony moduł uruchomieniowy weryfikuje odporność struktury na obciążenie:
1. Pętla zapisów powodująca przesunięcia cykliczne.
2. Wymuszenie kolizji wskaźników odczytu i zapisu.
3. Weryfikacja wizualna dwukrotnego powiększenia pamięci oraz "wyprostowania" ciągłości logicznej danych.
4. Całkowite opróżnienie bufora poprzez pętlę odczytów (zabezpieczenie przed wyciekami i błędami indeksowania).