# algorithm

TOC



## Binary search (Recherche dichotomique)

Retourne la position d'un élément dans un tableau trié. Si l'élément n'existe pas, retourne -(insertion-point + 1), où insertion-point représente l'index où l'élément devrait être inséré.


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

NB :
* Comparable<? super T> indique que T est comparable avec tout objet dont la classe est un ancêtre de T. Eg, Foo implements Comparable<Object> indique que Foo est comparable avec n'importe quel objet.
