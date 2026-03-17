# 📌 Implementacja klasy `macierz` w Pythonie

## Opis projektu

Celem projektu jest implementacja klasy reprezentującej **macierz dwuwymiarową** w języku Python, z dostępem do elementów w stylu języka C:

```python
m[i][j]
```

Klasa umożliwia wykonywanie podstawowych operacji na macierzach:

* dodawanie (`+`)
* mnożenie macierzowe (`*`)
* porównywanie (`==`)
* dostęp do elementów (`[]`)
* wypisywanie macierzy (`print`)

Dodatkowo zaimplementowana jest funkcja transponująca macierz.

---

## ⚙️ Funkcjonalności

### 🔹 Konstruktor

Tworzenie macierzy możliwe jest na dwa sposoby:

1. **Na podstawie listy list:**

```python
m = macierz([[1, 2], [3, 4]])
```

2. **Na podstawie rozmiaru (wiersze, kolumny) oraz wartości domyślnej:**

```python
m = macierz((2, 3), 1)  # macierz 2x3 wypełniona jedynkami
```

---

### 🔹 Dostęp do elementów

```python
m[i][j]
```

---

### 🔹 Operacje na macierzach

* **Dodawanie:**

```python
m1 + m2
```

* **Mnożenie macierzowe:**

```python
m1 * m2
```

* **Porównanie:**

```python
m1 == m2
```

---

### 🔹 Wypisywanie macierzy

```python
print(m)
```

Format:

```
| 1 0 2 |
|-1 3 1 |
```

---

### 🔹 Rozmiar macierzy

```python
m.size()
```

Zwraca:

```python
(liczba_wierszy, liczba_kolumn)
```

---

### 🔹 Transpozycja macierzy

Zaimplementowana jako osobna funkcja:

```python
def transpose(m):
    ...
```

---

## ▶️ Przykładowe użycie

```python
def main():
    m1 = macierz([[1, 0, 2], [-1, 3, 1]])

    # transpozycja
    print(transpose(m1))

    # dodawanie
    m2 = macierz((2, 3), 1)
    print(m1 + m2)

    # mnożenie
    m3 = macierz([[3, 1], [2, 1], [1, 0]])
    print(m1 * m3)
```

---

## 📤 Wynik działania programu

Program wypisuje **wyłącznie trzy macierze wynikowe**:

1. transpozycję
2. sumę
3. wynik mnożenia

Bez dodatkowych komunikatów.

---

## 🧩 Wymagania implementacyjne

Klasa powinna implementować następujące metody specjalne:

* `__init__`
* `__getitem__`
* `__add__`
* `__mul__`
* `__eq__`
* `__str__`

Dodatkowo:

* metoda `size()`
* prywatne pole `__matrix` przechowujące dane

---

## 📁 Struktura projektu

```
.
├── macierz.py
└── README.md
```

---

## 🚀 Uruchomienie

```bash
python macierz.py
```

---

## 📝 Uwagi

* Operacje sprawdzają zgodność wymiarów macierzy.
* Wynikiem operacji jest nowy obiekt klasy `macierz`.
* Wewnętrzna reprezentacja danych jest ukryta (enkapsulacja).
