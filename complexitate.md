# Complexitate
### Diaconescu Rares, Nitu Alexia
Algoritmi si complexitatea lor:
|  Algoritm   | Complexitate minima | Complexitate medie | Complexitate maxima |Complexitate spatiala |
| :-------------: | :-------------: | :-------------: |:-------------: | :-------------: |
| BFS/DFS cu m<sub>adj</sub>  | n<sup>2</sup>  | n<sup>2</sup>  |n<sup>2</sup>  |n<sup>2</sup>  |n<sup>2</sup> |
| BFS/DFS cu v<sub>vec</sub>  | n+m  | n+m  | n+m  | n+m | m |
| Roy Warshall  | n<sup>3</sup>  | n<sup>3</sup>  |n<sup>3</sup>  | n<sup>2</sup> |
| Sortare quick/merge  | n×log(n)  | n×log(n)  |n<sup>2</sup>/n×log(n)  | n
| Hello World   | 1  | 1  | 1  

### DFS cu m<sub>adj</sub>

---

```cpp
#include <iostream>
using namespace std;

const int NMAX = 100;
int a[NMAX+5][NMAX+5], n;
bool v[NMAX+5];

void dfs(int nod) {
    v[nod] = 1;
    for(int i = 1; i <= n; ++i)
        if(a[nod][i] && !v[i])
            dfs(i);
}

int main() {
    int x, y, m;
    cin >> n >> m;
    for(int i = 1; i <= m; ++i){
        cin >> x >> y;
        a[x][y] = 1;
        //a[y][x] = 1; pentru grafuri neorientate
    }
    for(int i = 1; i <= n; ++i)
            if(!v[i])
                dfs(i);
    return 0;
}
```
### DFS cu v<sub>vec</sub>

---

```cpp
#include <iostream>
#include <vector>
using namespace std;

const int NMAX = 100;
int n;
bool v[NMAX+5];
vector<int> G[NMAX+5];

void dfs(int nod) {
    v[nod] = 1;
    for(int i : G)
        if(!v[i])
            dfs(i);
}

int main() {
    int x, y, m;
    cin >> n >> m;
    for(int i = 1; i <= m; ++i){
        cin >> x >> y;
        G[x].push_back(y);
        //G[y].push_back(x); pentru grafuri neorientate
    }
    for(int i = 1; i <= n; ++i)
            if(!v[i])
                dfs(i);
    return 0;
}
```
### Roy-Warshall

---

```cpp
for(int k = 1; k <= n; ++k)
    for(int i = 1; i <= n; ++i)
        for(int j = 1; j <= n; ++j)
            if(!a[i][j])
                a[i][j] = a[i][k]*a[k][j];
```
### Merge Sort

---

```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int p, int q, int r) {
    int n1 = q - p + 1;
    int n2 = r - q;

    int L[n1], M[n2];

    for (int i = 0; i < n1; i++)
        L[i] = arr[p + i];
    for (int j = 0; j < n2; j++)
        M[j] = arr[q + 1 + j];
    int i, j, k;
    i = 0;
    j = 0;
    k = p;
    while (i < n1 && j < n2) {
        if (L[i] <= M[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = M[j];
            j++;
        }
        k++;
    }
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = M[j];
        j++;
        k++;
    }
}
void mergeSort(int arr[], int l, int r) {
  if (l < r) {
    int m = l + (r - l) / 2;
    mergeSort(arr, l, m);
    mergeSort(arr, m + 1, r);
    merge(arr, l, m, r);
  }
}
int main() {
  int arr[] = {6, 5, 12, 10, 9, 1};
  mergeSort(arr, 0, 5);
  return 0;
}
```
### Hello World!

---

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World!";
    return 0;
}
```
