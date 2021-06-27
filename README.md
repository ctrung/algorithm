# algorithm

**TOC**

* [Binary search (Recherche dichotomique)](#binary-search-recherche-dichotomique)
* [Selection sort (Tri par sélection)](#selection-sort-tri-par-sélection)

## Binary search (Recherche dichotomique)

Retourne la position d'un élément dans un tableau **trié**.

Si l'élément n'existe pas, retourne une valeur négative (-1).\
En java, retourne -(insertion-point + 1), où insertion-point représente l'index où l'élément devrait être inséré.


Complexité : O(log n)
```java
<T extends Comparable<? super T>> int binarySearch(T[] array, T item) {
    int low = 0;
    int high = array.length - 1;

    while (low <= high) {
        int mid = (low + high) / 2;
        T guess = array[mid];

        int comp = item.compareTo(guess);

        if (comp == 0) return mid;

        if (comp > 0) low = mid + 1;
        else high = mid - 1;
    }

    return -(low + 1);
}
```
Exemples
```
{2, 3, 5, 7, 9},  0 = -1
{2, 3, 5, 7, 9},  4 = -3
{2, 3, 5, 7, 9},  8 = -5
{2, 3, 5, 7, 9},  2 = 0
{2, 3, 5, 7, 9},  7 = 3
{2, 3, 5, 7, 9},  9 = 4
{2, 3, 5, 7, 9},  10 = -6
```

**NB**
* `Comparable<? super T>` indique que T est comparable avec tout objet dont la classe est un ancêtre de T. Eg, si `Foo implements Comparable<Object>` (Foo est comparable avec n'importe quel objet).


# Selection sort (Tri par sélection)

A chaque passe, on cherche le plus petit élément et on le met dans un nouveau tableau.\
A la fin, le nouveau tableau contient les éléments classés dans l'ordre croissant.

Complexité : O(n2)

```java
<T extends Comparable<? super T>> T[] selectionSort(T[] array) {
    for (int i = 0; i < array.length; i++) {
        int smallerIndex = i;
        // cette boucle pour chercher le plus petit élément dans le reste du tableau
        for (int j = i; j < array.length - 1; j++) {
            if (array[j + 1].compareTo(array[smallerIndex]) < 0) {
                smallerIndex = j + 1;
            }
        }
        // on intervertit
        T temp = array[i];
        array[i] = array[smallerIndex];
        array[smallerIndex] = temp;
    }
    return array;
}
```
Exemples
```
{2, 3, 5, 7, 9} = {2, 3, 5, 7, 9}
{5} = {5}
{} = {}
```

**NB**
* L'implémentation ci dessus effectie le tri sur place au lieu d'instancier un nouveau tableau.
