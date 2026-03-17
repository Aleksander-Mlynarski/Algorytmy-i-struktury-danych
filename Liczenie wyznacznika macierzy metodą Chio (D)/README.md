# Obliczanie Wyznacznika Macierzy - Metoda Chio

## O projekcie
Projekt zawiera obiektową implementację algorytmu obliczania wyznacznika macierzy kwadratowej $n \times n$ przy użyciu **metody kondensacji Chio**. 

Algorytm opiera się na podejściu rekurencyjnym. Pozwala sprowadzić problem obliczenia wyznacznika macierzy o rozmiarze $n \times n$ (gdzie $n > 2$) do obliczenia wyznacznika macierzy zredukowanej o rozmiarze $(n-1) \times (n-1)$. Elementami nowej macierzy są wartości wyznaczników podmacierzy $2 \times 2$, które można łatwo policzyć klasyczną metodą "na krzyż".

## Podstawa matematyczna
Zgodnie z metodą Chio, wyznacznik macierzy $A$ wyraża się poniższym wzorem:

$$|A| = \frac{1}{a_{1,1}^{n-2}} \begin{vmatrix} 
\begin{vmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{vmatrix} & \cdots & \begin{vmatrix} a_{1,1} & a_{1,n} \\ a_{2,1} & a_{2,n} \end{vmatrix} \\ 
\vdots & \ddots & \vdots \\ 
\begin{vmatrix} a_{1,1} & a_{1,2} \\ a_{n,1} & a_{n,2} \end{vmatrix} & \cdots & \begin{vmatrix} a_{1,1} & a_{1,n} \\ a_{n,1} & a_{n,n} \end{vmatrix} 
\end{vmatrix}$$

*(Źródło implementacji: [Forum Matematyka.pl](https://matematyka.pl/viewtopic.php?t=360950))*

## Rozwiązywanie problemów brzegowych (Edge Cases)
Algorytm w swojej podstawowej formie wymaga dzielenia przez element $a_{1,1}$. Rodzi to matematyczny problem (dzielenie przez zero), gdy $a_{1,1} = 0$. 

Aby program był w pełni uniwersalny, zaimplementowano następujące mechanizmy:
1. **Zamiana wierszy (Pivoting):** Jeśli $a_{1,1} = 0$, algorytm szuka innego niezerowego elementu w pierwszej kolumnie i zamienia odpowiednie wiersze miejscami, pamiętając o **zmianie znaku** końcowego wyznacznika.
2. **Optymalizacja macierzy zerowych:** Jeśli cały wiersz lub cała kolumna składa się z samych zer, algorytm natychmiast zwraca `0`, optymalizując czas wykonania i przerywając niepotrzebną rekurencję.

## Przypadki testowe

Poniższe macierze testowe służą do walidacji poprawności zaimplementowanego algorytmu:

### Test 1: Standardowa macierz $5 \times 5$
```text
[
  [5, 1, 1, 2, 3],
  [4, 2, 1, 7, 3],
  [2, 1, 2, 4, 7],
  [9, 1, 0, 7, 0],
  [1, 4, 7, 2, 2]
]