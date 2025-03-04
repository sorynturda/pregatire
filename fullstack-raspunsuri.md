```python
def generate_permutations(arr):
    if len(arr) <= 1:
        return [arr]
    result = []
    for i in range(len(arr)):
        current = arr[i]
        remaining = arr[:i] + arr[i+1:]
        for p in generate_permutations(remaining):
            result.append([current] + p)
    return result  # O(n!)
```

**Complexitatea spațiului:**
- Similar cu complexitatea timpului, dar măsoară memoria suplimentară necesară
- Exemple:
  - O(1): Spațiu constant (variabile simple)
  - O(n): Spațiu linear (array-uri, liste cu n elemente)
  - O(n²): Matrici n×n

**Comparații între clase de complexitate:**

Pentru n = 1,000,000:
- O(1): ~1 operație
- O(log n): ~20 operații
- O(n): ~1,000,000 operații
- O(n log n): ~20,000,000 operații
- O(n²): ~1,000,000,000,000 operații (impracticabil)
- O(2^n): imposibil de calculat (număr astronomic)

**Analiza complexității pentru algoritmi compuși:**

1. **Algoritmi secvențiali:**
   - Adună complexitățile și păstrează termenul dominant
   ```
   O(n) + O(n²) + O(log n) = O(n²)
   ```

2. **Algoritmi imbricați:**
   - Multiplică complexitățile
   ```
   O(n) * O(m) = O(n*m)
   ```
   ```javascript
   // Exemplu O(n*m)
   for (let i = 0; i < n; i++) {     // O(n)
     for (let j = 0; j < m; j++) {   // O(m)
       // operație
     }
   }
   ```

3. **Recursivitate:**
   - Folosește relații de recurență
   - Tehnici: Tree method, Master theorem
   ```
   T(n) = 2*T(n/2) + O(n)  // Pentru merge sort, rezultă O(n log n)
   ```

**Importanța analizei complexității:**
1. Predicția performanței pentru seturi de date mari
2. Compararea algoritmilor și alegerea celui mai eficient
3. Înțelegerea limitelor și potențialelor îmbunătățiri
4. Anticiparea problemelor de scalabilitate

**Optimizarea algoritmilor:**
- Recunoașterea și eliminarea operațiunilor redundante
- Utilizarea structurilor de date adecvate
- Aplicarea tehnicilor precum memoizarea, programarea dinamică
- Schimbarea abordării pentru a obține o clasă de complexitate mai bună

### 33. Ce sunt algoritmii de sortare și care este diferența între sortarea stabilă și instabilă?
**Răspuns:** Algoritmii de sortare sunt proceduri care aranjează elementele unei colecții într-o anumită ordine, cel mai adesea crescător sau descrescător. Acești algoritmi sunt fundamentali în computer science și sunt utilizați în numeroase aplicații.

**Sortare stabilă vs. instabilă:**

- **Sortare stabilă:** Păstrează ordinea relativă a elementelor cu chei egale. Dacă două elemente A și B au aceeași valoare și A apare înaintea lui B în șirul inițial, A va apărea înaintea lui B și în șirul sortat.

- **Sortare instabilă:** Nu garantează menținerea ordinii relative a elementelor cu chei egale.

Stabilitatea este importantă când sortăm după multiple criterii sau când ordinea originală conține informații semnificative.

**Exemplu:** Avem un array de obiecte (nume, rang) care trebuie sortate după rang:
```
[(Alice, 3), (Bob, 9), (Charlie, 3), (David, 5)]
```

După sortare stabilă, Charlie ar trebui să rămână după Alice deoarece ambii au același rang:
```
[(Alice, 3), (Charlie, 3), (David, 5), (Bob, 9)]
```

O sortare instabilă ar putea produce:
```
[(Charlie, 3), (Alice, 3), (David, 5), (Bob, 9)]
```

**Algoritmi principali de sortare:**

1. **Bubble Sort:**
   - **Complexitate:** O(n²) timp, O(1) spațiu
   - **Stabilitate:** Stabil
   - **Funcționare:** Compară și schimbă perechi adiacente repetat
   - **Utilizare:** Simplu de implementat, eficient doar pentru seturi mici
   
   ```javascript
   function bubbleSort(arr) {
       const n = arr.length;
       for (let i = 0; i < n; i++) {
           for (let j = 0; j < n - i - 1; j++) {
               if (arr[j] > arr[j + 1]) {
                   [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]]; // Swap
               }
           }
       }
       return arr;
   }
   ```

2. **Selection Sort:**
   - **Complexitate:** O(n²) timp, O(1) spațiu
   - **Stabilitate:** Instabil (în implementarea clasică)
   - **Funcționare:** Găsește elementul minim și îl plasează la poziția corectă
   - **Utilizare:** Simplu, minimizează numărul de swap-uri
   
   ```python
   def selection_sort(arr):
       n = len(arr)
       for i in range(n):
           min_idx = i
           for j in range(i+1, n):
               if arr[j] < arr[min_idx]:
                   min_idx = j
           arr[i], arr[min_idx] = arr[min_idx], arr[i]  # Swap
       return arr
   ```

3. **Insertion Sort:**
   - **Complexitate:** O(n²) timp (worst/average), O(n) timp (best), O(1) spațiu
   - **Stabilitate:** Stabil
   - **Funcționare:** Construiește șirul sortat incrementând un element la un moment dat
   - **Utilizare:** Eficient pentru seturi mici sau aproape sortate
   
   ```java
   void insertionSort(int[] arr) {
       int n = arr.length;
       for (int i = 1; i < n; i++) {
           int key = arr[i];
           int j = i - 1;
           
           while (j >= 0 && arr[j] > key) {
               arr[j + 1] = arr[j];
               j--;
           }
           arr[j + 1] = key;
       }
   }
   ```

4. **Merge Sort:**
   - **Complexitate:** O(n log n) timp, O(n) spațiu
   - **Stabilitate:** Stabil
   - **Funcționare:** Divide array-ul în jumătăți, sortează recursiv, apoi combină
   - **Utilizare:** Eficient pentru seturi mari, performanță predictibilă
   
   ```javascript
   function mergeSort(arr) {
       if (arr.length <= 1) return arr;
       
       const mid = Math.floor(arr.length / 2);
       const left = mergeSort(arr.slice(0, mid));
       const right = mergeSort(arr.slice(mid));
       
       return merge(left, right);
   }
   
   function merge(left, right) {
       let result = [];
       let i = 0, j = 0;
       
       while (i < left.length && j < right.length) {
           if (left[i] <= right[j]) {
               result.push(left[i++]);
           } else {
               result.push(right[j++]);
           }
       }
       
       return result.concat(left.slice(i)).concat(right.slice(j));
   }
   ```

5. **Quick Sort:**
   - **Complexitate:** O(n log n) timp (average), O(n²) timp (worst), O(log n) spațiu
   - **Stabilitate:** Instabil
   - **Funcționare:** Alege un pivot, partajează array-ul, sortează recursiv partițiile
   - **Utilizare:** Foarte eficient în practică, consumă mai puțină memorie decât merge sort
   
   ```python
   def quick_sort(arr):
       if len(arr) <= 1:
           return arr
       
       pivot = arr[len(arr) // 2]
       left = [x for x in arr if x < pivot]
       middle = [x for x in arr if x == pivot]
       right = [x for x in arr if x > pivot]
       
       return quick_sort(left) + middle + quick_sort(right)
   ```

6. **Heap Sort:**
   - **Complexitate:** O(n log n) timp, O(1) spațiu
   - **Stabilitate:** Instabil
   - **Funcționare:** Construiește un heap și extrage repetat elementul maxim/minim
   - **Utilizare:** Eficient pentru space-constrained applications
   
   ```java
   void heapSort(int[] arr) {
       int n = arr.length;
       
       // Build heap
       for (int i = n / 2 - 1; i >= 0; i--)
           heapify(arr, n, i);
       
       // Extract elements from heap
       for (int i = n - 1; i > 0; i--) {
           // Move current root to end
           int temp = arr[0];
           arr[0] = arr[i];
           arr[i] = temp;
           
           // Call heapify on reduced heap
           heapify(arr, i, 0);
       }
   }
   
   void heapify(int[] arr, int n, int i) {
       int largest = i;
       int left = 2 * i + 1;
       int right = 2 * i + 2;
       
       if (left < n && arr[left] > arr[largest])
           largest = left;
       
       if (right < n && arr[right] > arr[largest])
           largest = right;
       
       if (largest != i) {
           int swap = arr[i];
           arr[i] = arr[largest];
           arr[largest] = swap;
           
           heapify(arr, n, largest);
       }
   }
   ```

7. **Counting Sort:**
   - **Complexitate:** O(n + k) timp, O(n + k) spațiu (unde k e range-ul valorilor)
   - **Stabilitate:** Stabil (dacă e implementat corect)
   - **Funcționare:** Numără aparițiile fiecărei valori și reconstruiește array-ul
   - **Utilizare:** Eficient pentru range mic de valori (numere întregi)
   
   ```javascript
   function countingSort(arr) {
       const max = Math.max(...arr);
       const counts = new Array(max + 1).fill(0);
       
       // Count occurrences
       for (let num of arr) {
           counts[num]++;
       }
       
       // Reconstruct the array
       let sorted = [];
       for (let i = 0; i <= max; i++) {
           for (let j = 0; j < counts[i]; j++) {
               sorted.push(i);
           }
       }
       
       return sorted;
   }
   ```

8. **Radix Sort:**
   - **Complexitate:** O(nk) timp, O(n + k) spațiu (unde k e numărul de cifre)
   - **Stabilitate:** Stabil
   - **Funcționare:** Sortează pe baza cifrelor individuale, de la least significant la most significant
   - **Utilizare:** Eficient pentru numere întregi cu același număr de cifre
   
   ```python
   def radix_sort(arr):
       # Find the maximum number to know number of digits
       max_num = max(arr)
       
       # Do counting sort for every digit
       exp = 1
       while max_num // exp > 0:
           counting_sort_by_digit(arr, exp)
           exp *= 10
       
       return arr
   
   def counting_sort_by_digit(arr, exp):
       n = len(arr)
       output = [0] * n
       count = [0] * 10
       
       # Store count of occurrences in count[]
       for i in range(n):
           index = arr[i] // exp % 10
           count[index] += 1
       
       # Change count[i] so that it contains actual
       # position of this digit in output[]
       for i in range(1, 10):
           count[i] += count[i - 1]
       
       # Build the output array
       i = n - 1
       while i >= 0:
           index = arr[i] // exp % 10
           output[count[index] - 1] = arr[i]
           count[index] -= 1
           i -= 1
       
       # Copy the output array to arr[]
       for i in range(n):
           arr[i] = output[i]
   ```

**Tabel comparativ al algoritmilor de sortare:**

| Algoritm | Timp Best | Timp Average | Timp Worst | Spațiu | Stabil |
|----------|-----------|--------------|------------|--------|--------|
| Bubble   | O(n)      | O(n²)        | O(n²)      | O(1)   | Da     |
| Selection| O(n²)     | O(n²)        | O(n²)      | O(1)   | Nu     |
| Insertion| O(n)      | O(n²)        | O(n²)      | O(1)   | Da     |
| Merge    | O(n log n)| O(n log n)   | O(n log n) | O(n)   | Da     |
| Quick    | O(n log n)| O(n log n)   | O(n²)      | O(log n)| Nu    |
| Heap     | O(n log n)| O(n log n)   | O(n log n) | O(1)   | Nu     |
| Counting | O(n + k)  | O(n + k)     | O(n + k)   | O(n + k)| Da    |
| Radix    | O(nk)     | O(nk)        | O(nk)      | O(n + k)| Da    |

**Alegerea algoritmului potrivit:**

1. **Pentru seturi mici (< 50 elemente):**
   - Insertion Sort adesea funcționează cel mai bine

2. **Pentru seturi aproape sortate:**
   - Insertion Sort sau Bubble Sort cu optimizări

3. **Pentru eficiență generală și seturi mari:**
   - Quick Sort pentru memorie limitată
   - Merge Sort pentru garanții de performanță și stabilitate

4. **Pentru range limitat de valori întregi:**
   - Counting Sort sau Radix Sort

5. **Pentru constrângeri de memorie stricte:**
   - Heap Sort (in-place)

6. **Când stabilitatea este critică:**
   - Merge Sort
   - Insertion Sort
   - Bubble Sort
   - Counting Sort (implementat corect)

### 34. Explică recursivitatea și dă un exemplu practic.
**Răspuns:** Recursivitatea este o tehnică de programare în care o funcție se apelează pe sine însăși pentru a rezolva probleme care pot fi descompuse în subprobleme similare cu problema originală, dar de dimensiuni mai mici. O funcție recursivă constă de obicei dintr-un caz de bază (condiție de oprire) și un caz recursiv.

**Componente ale unei funcții recursive:**
1. **Cazul de bază (base case):** Condiția care oprește recursivitatea
2. **Cazul recursiv:** Partea în care funcția se apelează pe sine
3. **Progresul către cazul de bază:** Fiecare apel recursiv trebuie să se apropie de cazul de bază

**Exemplu clasic: Calculul factorialului**

```javascript
function factorial(n) {
    // Cazul de bază
    if (n === 0 || n === 1) {
        return 1;
    }
    // Cazul recursiv
    return n * factorial(n - 1);
}

console.log(factorial(5)); // 120
```

Execuție pentru factorial(5):
```
factorial(5) = 5 * factorial(4)
factorial(4) = 4 * factorial(3)
factorial(3) = 3 * factorial(2)
factorial(2) = 2 * factorial(1)
factorial(1) = 1 (caz de bază)
```

Apoi rezolvare în sens invers:
```
factorial(2) = 2 * 1 = 2
factorial(3) = 3 * 2 = 6
factorial(4) = 4 * 6 = 24
factorial(5) = 5 * 24 = 120
```

**Exemplu practic: Traversarea unui arbore de directoare**

Să presupunem că vrem să găsim toate fișierele într-un director și subdirectoarele sale:

```python
import os

def list_all_files(directory):
    files = []
    
    # Listează conținutul directorului curent
    entries = os.listdir(directory)
    
    for entry in entries:
        full_path = os.path.join(directory, entry)
        
        # Cazul de bază: dacă e fișier, adaugă-l la listă
        if os.path.isfile(full_path):
            files.append(full_path)
        # Cazul recursiv: dacă e director, apelează recursiv
        elif os.path.isdir(full_path):
            # Adaugă fișierele din subdirector la listă
            files.extend(list_all_files(full_path))
    
    return files

# Exemplu de utilizare
all_files = list_all_files('/path/to/directory')
for file in all_files:
    print(file)
```

**Exemplu: Algoritmul de căutare binară recursiv**

```java
int binarySearch(int[] array, int target, int left, int right) {
    // Cazul de bază: elementul nu a fost găsit
    if (left > right) {
        return -1;
    }
    
    int mid = left + (right - left) / 2;
    
    // Cazul de bază: elementul a fost găsit
    if (array[mid] == target) {
        return mid;
    }
    
    // Cazuri recursive
    if (array[mid] > target) {
        // Caută în jumătatea stângă
        return binarySearch(array, target, left, mid - 1);
    } else {
        // Caută în jumătatea dreaptă
        return binarySearch(array, target, mid + 1, right);
    }
}

// Apel inițial
int index = binarySearch(array, target, 0, array.length - 1);
```

**Avantajele recursivității:**
1. **Simplitate:** Pentru anumite probleme, soluția recursivă este mai simplă și mai intuitivă
2. **Eleganta:** Cod mai curat și mai ușor de înțeles pentru algoritmi complecși
3. **Divide și cucerește:** Permite descompunerea problemelor mari în subprobleme similare
4. **Potrivit pentru structuri recursive:** Natural pentru arbori, grafuri, și alte structuri recursive

**Dezavantajele recursivității:**
1. **Overhead de performanță:** Fiecare apel recursiv adaugă un frame în stack
2. **Risc de stack overflow:** Recursivitate prea adâncă poate duce la epuizarea stack-ului
3. **Potențial pentru duplicarea calculelor:** Fără memoizare, unele calcule pot fi repetate

**Optimizări pentru recursivitate:**

1. **Tail recursion:** O formă specială de recursivitate unde apelul recursiv este ultima operație
   ```javascript
   // Factorial cu tail recursion
   function factorialTail(n, accumulator = 1) {
       if (n === 0 || n === 1) {
           return accumulator;
       }
       return factorialTail(n - 1, n * accumulator);
   }
   ```

2. **Memoizare:** Stocarea rezultatelor intermediare pentru a evita recalcularea
   ```javascript
   // Fibonacci cu memoizare
   function fibonacciMemo(n, memo = {}) {
       if (n in memo) return memo[n];
       if (n <= 1) return n;
       
       memo[n] = fibonacciMemo(n - 1, memo) + fibonacciMemo(n - 2, memo);
       return memo[n];
   }
   ```

3. **Transformarea în iterație:** Convertirea recursivității în loop-uri când e posibil
   ```javascript
   // Factorial iterativ
   function factorialIterative(n) {
       let result = 1;
       for (let i = 2; i <= n; i++) {
           result *= i;
       }
       return result;
   }
   ```

**Recursivitate vs. Iterație:**
- Recursivitatea este adesea mai elegantă și mai apropiată de definiția matematică a problemei
- Iterația este de obicei mai eficientă ca performanță și consum de memorie
- Unele probleme (traversarea arborilor, backtracking) sunt mai natural exprimate recursiv
- Multe algoritmi recursivi pot fi convertiți în versiuni iterative folosind o stivă explicită

### 35. Ce este programarea funcțională și care sunt principiile sale?
**Răspuns:** Programarea funcțională (FP) este o paradigmă de programare care tratează calculul ca evaluare a funcțiilor matematice și evită schimbarea stării și mutarea datelor. Este o abordare declarativă care pune accentul pe ce trebuie calculat, nu pe cum să se calculeze.

**Principii fundamentale ale programării funcționale:**

1. **Funcții pure (Pure functions):**
   - Returnează același rezultat pentru aceleași argumente de intrare
   - Nu au efecte secundare (nu modifică starea globală, nu afectează intrările)
   - Sunt deterministe și predictibile

   ```javascript
   // Funcție pură
   function add(a, b) {
       return a + b;
   }
   
   // Funcție impură (depinde de starea externă)
   let total = 0;
   function addToTotal(value) {
       total += value; // Modifică starea externă
       return total;
   }
   ```

2. **Imutabilitate (Immutability):**
   - Datele nu sunt modificate după creare
   - În loc să modifici un obiect, creezi unul nou cu modificările dorite
   - Ajută la evitarea efectelor secundare și face codul mai predictibil

   ```javascript
   // Abordare imperativă (mutabilă)
   const numbers = [1, 2, 3];
   numbers.push(4); // Modifică array-ul original
   
   // Abordare funcțională (imutabilă)
   const numbers = [1, 2, 3];
   const newNumbers = [...numbers, 4]; // Creează un nou array
   ```

3. **Transparență referențială (Referential transparency):**
   - O expresie poate fi înlocuită cu rezultatul său fără a schimba comportamentul programului
   - Rezultat direct al utilizării funcțiilor pure și imutabilității
   - Facilitează raționamentul despre cod și optimizările compilatorului

   ```javascript
   // transparent referențial
   const x = add(2, 3); // poate fi înlocuit direct cu 5
   ```

4. **Funcții de ordin superior (Higher-order functions):**
   - Funcții care pot primi alte funcții ca argumente
   - Funcții care pot returna funcții
   - Permite abstractizări puternice și componibilitate

   ```javascript
   // Funcție care primește altă funcție ca argument
   function map(array, transformFn) {
       return array.map(transformFn);
   }
   
   // Funcție care returnează o altă funcție
   function multiplier(factor) {
       return function(number) {
           return number * factor;
       };
   }
   
   const double = multiplier(2);
   double(5); // 10
   ```

5. **Recursivitate în loc de iterație:**
   - Preferința pentru recursivitate în locul buclelor pentru operații repetitive
   - O abordare mai declarativă pentru algoritmi
   - Adesea optimizată prin tail recursion

   ```javascript
   // Recursiv
   function sum(arr) {
       if (arr.length === 0) return 0;
       return arr[0] + sum(arr.slice(1));
   }
   
   // Cu tail recursion
   function sumTail(arr, acc = 0) {
       if (arr.length === 0) return acc;
       return sumTail(arr.slice(1), acc + arr[0]);
   }
   ```

6. **Evaluare lazy (Lazy evaluation):**
   - Calculul valorilor doar când sunt necesare
   - Permite crearea și operarea pe secvențe potențial infinite
   - Optimizează performanța evitând calcule inutile

   ```javascript
   // Generator pentru numere Fibonacci (evaluare lazily)
   function* fibonacciGenerator() {
       let a = 0, b = 1;
       while (true) {
           yield a;
           [a, b] = [b, a + b];
       }
   }
   
   const fib = fibonacciGenerator();
   console.log(fib.next().value); // 0
   console.log(fib.next().value); // 1
   console.log(fib.next().value); // 1
   ```

7. **Pattern Matching:**
   - Destructurarea datelor și ramificarea bazată pe structură
   - Facilitează lucrul cu tipuri de date algebrice
   - Nu toate limbajele funcționale au suport nativ

   ```haskell
   -- Haskell example
   factorial :: Integer -> Integer
   factorial 0 = 1
   factorial n = n * factorial (n - 1)
   ```

8. **Funcții curried și aplicare parțială:**
   - Currying: transformarea unei funcții cu multiple argumente în o secvență de funcții cu un singur argument
   - Aplicare parțială: furnizarea doar a unei părți din argumentele unei funcții, rezultând o nouă funcție

   ```javascript
   // Funcție normală
   function add(a, b) {
       return a + b;
   }
   
   // Funcție curried
   function curriedAdd(a) {
       return function(b) {
           return a + b;
       };
   }
   
   const add5 = curriedAdd(5); // Aplicare parțială
   add5(3); // 8
   ```

9. **Compunerea funcțiilor (Function composition):**
   - Combinarea a două sau mai multe funcții pentru a crea o nouă funcție
   - Permite crearea de funcționalități complexe din funcții simple

   ```javascript
   // Compunere manuală
   function compose(f, g) {
       return function(x) {
           return f(g(x));
       };
   }
   
   const double = x => x * 2;
   const increment = x => x + 1;
   
   const doubleAndIncrement = compose(increment, double);
   doubleAndIncrement(5); // 11 (5*2+1)
   ```

**Avantajele programării funcționale:**

1. **Cod mai ușor de testat:**
   - Funcțiile pure primesc input și returnează output, fără dependențe externe
   - Izolarea facilitează testarea unitară

2. **Predictibilitate și transparență:**
   - Fără efecte secundare ascunse sau modificări de stare neașteptate
   - Comportament consistent indiferent de context

3. **Concurență mai sigură:**
   - Imutabilitatea elimină multe probleme tipice cu accesul concurent la date
   - Race conditions reduse semnificativ

4. **Debugging și raționament mai ușor:**
   - Logica de program mai clară, fără a urmări modificări de stare
   - Erori mai izolate și localizabile

5. **Reutilizare și modularitate:**
   - Funcțiile mici, specializate sunt mai ușor de refolosit
   - Compunerea funcțiilor promovează modularitatea

6. **Memoizare și optimizări:**
   - Funcțiile pure permit caching-ul rezultatelor (memoizare)
   - Compilatoarele pot optimiza codul mai ușor datorită transparenței referențiale

**Paradigme hibride și programare funcțională în limbaje mainstream:**

Multe limbaje moderne suportă un stil funcțional alături de alte paradigme:

- **JavaScript:**
  ```javascript
  // Array functions
  const numbers = [1, 2, 3, 4, 5];
  const doubled = numbers.map(n => n * 2);
  const sum = numbers.reduce((acc, n) => acc + n, 0);
  const evens = numbers.filter(n => n % 2 === 0);
  ```

- **Python:**
  ```python
  # List comprehensions and higher-order functions
  numbers = [1, 2, 3, 4, 5]
  doubled = [n * 2 for n in numbers]
  evens = filter(lambda n: n % 2 == 0, numbers)
  from functools import reduce
  sum_all = reduce(lambda acc, n: acc + n, numbers, 0)
  ```

- **Java (8+):**
  ```java
  List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
  List<Integer> doubled = numbers.stream()
                               .map(n -> n * 2)
                               .collect(Collectors.toList());
  int sum = numbers.stream().reduce(0, Integer::sum);
  ```

**Limbaje funcționale pure sau primary funcționale:**
- Haskell (pur funcțional)
- Clojure (dialect Lisp pentru JVM)
- Elm (pentru frontend web)
- F# (.NET)
- Scala (JVM, mix de OOP și funcțional)
- Erlang/Elixir (concurență și toleranță la erori)

### 36. Cum funcționează garbage collection și cum afectează performanța aplic- **Optimizarea GROUP BY:**
  - Adaugă indecși pe coloanele din GROUP BY
  - Folosește HAVING doar pentru filtrarea rezultatelor agregării

**6. Optimizarea serverului și configurării:**

- **Alocarea de memorie suficientă:**
  - Cache-uri, buffere și memory pools suficiente
  
- **Optimizări hardware:**
  - SSD-uri pentru stocarea bazelor de date
  - RAM suficient pentru a ține datele frecvent accesate în memorie
  
- **Parametri specifici de configurare:**
  - sort_buffer_size, join_buffer_size (MySQL)
  - work_mem, shared_buffers (PostgreSQL)

**7. Instrumente de optimizare:**

- Explainer vizual pentru planurile de execuție
- Analizoare de query-uri: Slow Query Log în MySQL
- Unelte de monitorizare: MySQL Workbench, pg_stat_statements

**8. Exemple concrete de optimizare:**

**Exemplu 1 - De la subconsultare la JOIN:**
```sql
-- Subconsultare (posibil mai lentă)
SELECT o.order_id, o.order_date, o.amount
FROM orders o
WHERE o.customer_id IN (
    SELECT customer_id 
    FROM customers 
    WHERE country = 'USA'
);

-- JOIN (posibil mai rapidă)
SELECT o.order_id, o.order_date, o.amount
FROM orders o
INNER JOIN customers c ON o.customer_id = c.customer_id
WHERE c.country = 'USA';
```

**Exemplu 2 - Optimizarea unei clauze WHERE cu funcții:**
```sql
-- Versiune lentă
SELECT * 
FROM transactions 
WHERE MONTH(transaction_date) = 3 AND YEAR(transaction_date) = 2023;

-- Versiune optimizată
SELECT * 
FROM transactions 
WHERE transaction_date BETWEEN '2023-03-01' AND '2023-03-31';
```

### 24. Ce este ORM (Object-Relational Mapping) și care sunt avantajele și dezavantajele?
**Răspuns:** Object-Relational Mapping (ORM) este o tehnică de programare care convertește date între sistemele de tipuri incompatibile din limbajele de programare orientate pe obiecte și bazele de date relaționale. ORM creează o "hartă" virtuală între modelele de date din codul programului și tabelele din baza de date.

**Cum funcționează ORM:**
- Definești clase care reprezintă tabelele din baza de date
- ORM-ul generează automat SQL pentru operațiuni CRUD
- Instanțele obiectelor sunt mapate la rânduri din tabel
- Relațiile dintre obiecte sunt mapate la relațiile dintre tabele

**Exemple populare de ORM:**
- **Java:** Hibernate, JPA
- **Python:** SQLAlchemy, Django ORM
- **JavaScript/Node.js:** Sequelize, TypeORM, Prisma
- **PHP:** Doctrine, Eloquent (Laravel)
- **C#/.NET:** Entity Framework, NHibernate
- **Ruby:** Active Record (Rails)

**Exemplu de implementare (JavaScript/Sequelize):**
```javascript
// Definiția modelului
const User = sequelize.define('user', {
  firstName: {
    type: Sequelize.STRING,
    allowNull: false
  },
  lastName: {
    type: Sequelize.STRING
  },
  email: {
    type: Sequelize.STRING,
    unique: true
  }
});

// Utilizare
// Creare
const user = await User.create({
  firstName: 'John',
  lastName: 'Doe',
  email: 'john.doe@example.com'
});

// Citire
const users = await User.findAll({
  where: {
    lastName: 'Doe'
  }
});

// Actualizare
await user.update({ lastName: 'Smith' });

// Ștergere
await user.destroy();
```

**Avantaje ORM:**

1. **Productivitate crescută:**
   - Reduce cantitatea de cod boilerplate
   - Permite dezvoltatorilor să se concentreze pe logica de business
   - Reduce timpul de dezvoltare

2. **Abstractizarea bazei de date:**
   - Același cod poate funcționa cu diferite baze de date (MySQL, PostgreSQL, etc.)
   - Migrarea între sisteme de baze de date devine mai ușoară

3. **Securitate îmbunătățită:**
   - Protecție automată împotriva SQL injection
   - Escaparea și validarea parametrilor

4. **Mapare orientată pe obiecte:**
   - Lucrul cu obiecte în loc de rânduri și coloane
   - Integrare naturală cu programarea orientată pe obiecte

5. **Caching și optimizări:**
   - Multe ORM-uri oferă caching la nivel de sesiune
   - Încărcare lazy vs. eager pentru relații

6. **Gestionarea relațiilor:**
   - Suport pentru relații One-to-One, One-to-Many, Many-to-Many
   - Încărcarea automată a obiectelor asociate

7. **Validarea datelor:**
   - Definirea regulilor de validare la nivel de model

**Dezavantaje ORM:**

1. **Overhead de performanță:**
   - Generarea și execuția SQL poate fi mai lentă decât SQL manual optimizat
   - Consum suplimentar de memorie și CPU pentru mapare

2. **Curba de învățare:**
   - Învățarea ORM-ului poate fi la fel de complexă ca învățarea SQL
   - Fiecare ORM are propriile particularități și API

3. **Complexitate pentru interogări avansate:**
   - Interogările complexe pot fi mai dificil de exprimat prin ORM
   - Optimizarea query-urilor devine mai puțin transparentă

4. **Black box syndrome:**
   - Dezvoltatorii pot să nu înțeleagă SQL-ul generat
   - Dificultate în debugging-ul problemelor de performanță

5. **Potențial pentru ineficiență:**
   - Problema "N+1 queries"
   - Poate încărca mai multe date decât este necesar

6. **Limitări pentru feature-uri specifice bazelor de date:**
   - Unele funcționalități specifice unei anumite baze de date pot fi greu de accesat

**Când să folosești ORM:**
- Pentru aplicații CRUD standard
- Când dezvoltarea rapidă este prioritară
- Pentru echipe mai puțin familiarizate cu SQL
- Când portabilitatea între baze de date este importantă

**Când să eviți ORM sau să folosești SQL nativ:**
- Pentru interogări foarte complexe sau optimizate
- Când performanța este critică
- Pentru operațiuni bulk sau batch processing
- Când ai nevoie de control total asupra SQL-ului generat

### 25. Explică diferența dintre DELETE, TRUNCATE și DROP în SQL.
**Răspuns:** DELETE, TRUNCATE și DROP sunt trei comenzi SQL utilizate pentru eliminarea datelor sau structurilor din baze de date, dar diferă semnificativ în scop, comportament și impact.

**1. DELETE:**
- **Scop:** Elimină rânduri specifice dintr-o tabelă
- **Nivel de operare:** La nivel de rând (înregistrare)
- **Sintaxă:**
  ```sql
  DELETE FROM table_name WHERE condition;
  ```
- **Caracteristici:**
  - Poate șterge toate rândurile sau doar rânduri specifice folosind o clauză WHERE
  - Acțiunea poate fi anulată (rollback) într-o tranzacție activă
  - Declanșează triggeri (triggers)
  - Păstrează autoincrement-ul și nu resetează contoarele
  - Necesită drepturi de DELETE pe tabelă
  - Înregistrează fiecare rând șters în transaction log

- **Exemplu:**
  ```sql
  DELETE FROM employees WHERE department_id = 5;
  ```

**2. TRUNCATE:**
- **Scop:** Elimină toate datele dintr-o tabelă, păstrând structura
- **Nivel de operare:** La nivel de tabelă
- **Sintaxă:**
  ```sql
  TRUNCATE TABLE table_name;
  ```
- **Caracteristici:**
  - Șterge toate rândurile, nu acceptă condiții WHERE
  - În majoritatea sistemelor, nu poate fi anulat prin rollback (DDL, nu DML)
  - Nu declanșează triggeri
  - Resetează contoarele autoincrement (de obicei la 1 sau valoarea inițială)
  - Necesită drepturi mai înalte (de obicei DROP)
  - Folosește mai puțin transaction log (nu înregistrează fiecare rând)
  - Mult mai rapidă decât DELETE pentru tabele mari

- **Exemplu:**
  ```sql
  TRUNCATE TABLE audit_logs;
  ```

**3. DROP:**
- **Scop:** Elimină complet o structură din baza de date
- **Nivel de operare:** La nivel de obiect de bază de date
- **Sintaxă:**
  ```sql
  DROP TABLE table_name;
  ```
- **Caracteristici:**
  - Elimină tabela, inclusiv datele, structura, indecșii, constrangerile, etc.
  - Nu poate fi anulat prin rollback în majoritatea sistemelor (este DDL)
  - Eliberează spațiul de stocare
  - Invalidează dependențele (view-uri, chei străine, etc.)
  - Necesită drepturi de DROP
  - Operațiune foarte rapidă indiferent de dimensiunea datelor

- **Exemple:**
  ```sql
  DROP TABLE old_customers;
  DROP DATABASE test_db;
  DROP INDEX idx_lastname;
  DROP VIEW active_users;
  ```

**Comparație succintă:**

| Caracteristică | DELETE | TRUNCATE | DROP |
|----------------|--------|----------|------|
| Tip operație | DML | DDL (majoritatea) | DDL |
| Rânduri afectate | Toate sau specifice | Toate | N/A |
| Structură păstrată | Da | Da | Nu |
| Condiție WHERE | Da | Nu | Nu |
| Rollback | Da | De obicei nu | De obicei nu |
| Triggeri | Da | Nu | Nu |
| Reset autoincrement | Nu | Da | N/A |
| Viteză relativă | Cea mai lentă | Rapidă | Cea mai rapidă |
| Logging | Fiecare rând | Minimal | Minimal |
| Impact | Cel mai mic | Mediu | Cel mai mare |

**Considerații pentru alegere:**

- Folosește **DELETE** când:
  - Trebuie să ștergi rânduri specifice
  - Ai nevoie de triggeri
  - Operațiunea trebuie să facă parte dintr-o tranzacție
  - Ai relații cu alte tabele (constrangeri de integritate)

- Folosește **TRUNCATE** când:
  - Trebuie să ștergi toate datele rapid
  - Nu ai nevoie de triggeri sau rollback
  - Vrei să resetezi contoarele autoincrement
  - Nu ai constrangeri de integritate care să împiedice operațiunea

- Folosește **DROP** când:
  - Nu mai ai nevoie de tabela sau obiectul respectiv
  - Vrei să elimini complet structura și toate datele asociate
  - Ești conștient de impactul asupra dependențelor

### 26. Ce sunt stored procedures și când ar trebui folosite?
**Răspuns:** Stored procedures (proceduri stocate) sunt blocuri de cod SQL precompilate și stocate în baza de date, care pot fi apelate și executate ulterior. Acestea pot conține logică procedurală, cum ar fi condiții, bucle, variabile, și pot include multiple instrucțiuni SQL.

**Caracteristici principale:**

1. **Precompilare și caching:**
   - Compilate și optimizate la creare
   - Planul de execuție poate fi stocat în cache
   - Execuție mai rapidă pentru apeluri repetate

2. **Parametrizare:**
   - Acceptă parametri de intrare și ieșire
   - Pot returna rezultate multiple (seturi de rezultate)

3. **Encapsulare:**
   - Ascund complexitatea implementării
   - Abstractizează operațiunile complexe

4. **Control și securitate:**
   - Permit gestionarea permisiunilor la nivel de procedură
   - Pot implementa reguli de business la nivel de bază de date

**Exemplu de procedură stocată (MySQL):**
```sql
DELIMITER //

CREATE PROCEDURE GetEmployeesByDepartment(
    IN departmentId INT,
    OUT employeeCount INT
)
BEGIN
    -- Declararea variabilelor
    DECLARE deptName VARCHAR(100);
    
    -- Găsirea numelui departamentului
    SELECT department_name INTO deptName
    FROM departments
    WHERE department_id = departmentId;
    
    -- Afișarea angajaților
    SELECT employee_id, first_name, last_name, hire_date
    FROM employees
    WHERE department_id = departmentId
    ORDER BY hire_date DESC;
    
    -- Calcularea numărului de angajați
    SELECT COUNT(*) INTO employeeCount
    FROM employees
    WHERE department_id = departmentId;
    
    -- Afișarea unui mesaj
    SELECT CONCAT('Department: ', deptName, ' has ', employeeCount, ' employees') AS message;
END //

DELIMITER ;

-- Apelarea procedurii
CALL GetEmployeesByDepartment(10, @count);
SELECT @count AS 'Number of employees';
```

**Când să folosești stored procedures:**

1. **Securitate îmbunătățită:**
   - Utilizatorii pot avea permisiuni pentru proceduri fără acces direct la tabele
   - Reduce riscul de SQL injection
   - Implementează controlul accesului granular

2. **Performanță mai bună:**
   - Reduce traficul de rețea (doar parametrii și rezultatele sunt transferate)
   - Execuție mai rapidă prin caching și precompilare
   - Procesare pe server pentru a evita multiple călătorii client-server

3. **Logică de business la nivel de bază de date:**
   - Implementarea regulilor de business consistent în toată aplicația
   - Logica validată centralizat
   - Independență de platforma client sau limbajul de programare

4. **Operațiuni complexe sau în batch:**
   - Execuția mai multor instrucțiuni într-o singură tranzacție
   - Procesare complexă care implică multiple tabele sau operațiuni
   - Tranzacții atomice cu multiple pași

5. **Reutilizare și standardizare:**
   - Aceeași logică utilizată consistent de către diferite aplicații
   - Reducerea duplicării codului SQL în aplicații

6. **Migrare și administrare:**
   - Mai ușor de gestionat schimbările în structura bazei de date
   - Actualizarea procedurilor independent de aplicație

**Dezavantaje și considerații:**

1. **Portabilitatea:**
   - Sintaxa și capacitățile variază între diferite sisteme de baze de date
   - Migrarea între sisteme poate fi dificilă

2. **Debugging:**
   - Instrumente mai limitate pentru debugging comparativ cu limbajele de programare
   - Poate fi mai dificil de testat

3. **Versioning și source control:**
   - Mai dificil de integrat în sistemele de control al versiunilor
   - Provocări în gestionarea schimbărilor și deployment

4. **Separarea logicii:**
   - Poate duce la dispersarea logicii de business între aplicație și baza de date
   - Dificultate în menținerea unei arhitecturi curate

**Stored procedures vs. cod în aplicație:**

- **Procedură stocată:** Când logica este strâns legată de date, necesită performanță, securitate strictă, sau este partajată între multiple aplicații
- **Cod în aplicație:** Când logica este specifică aplicației, implicată în UI, sau când portabilitatea și flexibilitatea sunt prioritare

### 27. Ce este sharding și când e necesar?
**Răspuns:** Sharding este o tehnică de partajare a bazei de date care implică distribuirea orizontală a datelor pe mai multe servere fizice sau instanțe separate, numite "shard-uri". Fiecare shard conține o subsetă a datelor și operează ca o bază de date independentă, dar împreună formează o singură bază de date logică.

**Cum funcționează sharding-ul:**

1. **Divizarea datelor:**
   - Datele sunt împărțite pe baza unui "shard key" (cheie de partajare)
   - Fiecare shard conține doar o porțiune din totalul datelor
   - Același schema este replicat pe toate shard-urile

2. **Rutarea interogărilor:**
   - Interogările sunt direcționate către shard-ul specific care conține datele relevante
   - Un "shard manager" sau "router" determină care shard trebuie accesat

3. **Strategii de sharding:**
   - **Range-based sharding:** Divizare bazată pe intervale de valori (ex: clienții A-M pe un shard, N-Z pe altul)
   - **Hash-based sharding:** Utilizarea unei funcții hash pe cheia de partajare (distribuție mai uniformă)
   - **Directory-based sharding:** Menținerea unui director explicit care mapează cheile la shard-uri
   - **Geography-based sharding:** Divizare bazată pe locație (date europene pe un shard, date americane pe altul)

**Diagrama simplificată a arhitecturii:**
```
Client → Shard Manager/Router → [Shard 1, Shard 2, Shard 3, ...]
```

**Când este necesar sharding-ul:**

1. **Volumul de date depășește capacitatea unui singur server:**
   - Când baza de date devine prea mare pentru a fi gestionată eficient pe un singur server
   - Când depășești limitele fizice de stocare

2. **Performanță și throughput:**
   - Când ai nevoie să scalezi operațiunile de scriere (sharding-ul distribuie încărcătura)
   - Când timpul de răspuns degradează din cauza volumului de date sau a numărului de cereri

3. **Scalabilitate orizontală:**
   - Când ai nevoie să adaugi capacitate prin adăugarea mai multor servere (în loc de upgrade-uri verticale)
   - Pentru aplicații care au creștere continuă și previzibilă

4. **Disponibilitate și izolare a eșecurilor:**
   - Pentru a limita impactul căderilor de server la doar o parte din date
   - Pentru a îmbunătăți disponibilitatea globală a sistemului

5. **Optimizare geografică:**
   - Când ai nevoie să localizezi datele mai aproape de utilizatori pentru latență redusă
   - Pentru a respecta cerințele de rezidenței a datelor (legi și reglementări)

**Avantaje ale sharding-ului:**

1. **Scalabilitate aproape nelimitată:**
   - Adăugarea de noi shard-uri permite creșterea capacității
   - Distribuie încărcătura de scriere pe multiple servere

2. **Performanță îmbunătățită:**
   - Fiecare server procesează un set mai mic de date
   - Memorie cache mai eficientă pe fiecare shard
   - Paralelizarea naturală a operațiunilor

3. **Izolarea problemelor:**
   - Un shard problematic afectează doar o parte din date
   - Mentenanța poate fi efectuată per-shard

4. **Optimizări fizice:**
   - Hardware specializat pentru tipuri specifice de date
   - Localizarea geografică pentru latență redusă

**Provocări și dezavantaje:**

1. **Complexitate crescută:**
   - Arhitectură și administrare mai complexe
   - Debugging și monitorizare mai dificile
   - Nevoia de instrumente suplimentare pentru gestionare

2. **Tranzacții și JOIN-uri între shard-uri:**
   - Dificultate în menținerea ACID pentru operațiuni care traversează shard-uri
   - JOIN-urile între date pe shard-uri diferite devin complexe sau imposibile

3. **Rebalansarea datelor:**
   - Migrarea datelor când se adaugă sau se elimină shard-uri
   - Potențial pentru indisponibilitate sau degradare a performanței în timpul rebalansării

4. **Alegerea cheii de sharding:**
   - O cheie neadecvată poate duce la dezechilibru (hotspots)
   - Schimbarea strategiei de sharding este dificilă după implementare

5. **Overhead operațional:**
   - Mentenanță multiplă pentru fiecare shard
   - Backup-uri și recovery mai complexe
   - Monitorizare și alertare pentru multiple instanțe

**Implementări practice:**

1. **Sharding nativ în baze de date:**
   - MongoDB: Sharding integrat
   - MySQL: MySQL Cluster sau MySQL Fabric
   - PostgreSQL: Citus, pg_shard

2. **Middleware pentru sharding:**
   - Vitess (pentru MySQL)
   - Hibernate Shards
   - Apache ShardingSphere

3. **Servicii cloud:**
   - Amazon Aurora
   - Google Cloud Spanner
   - Azure Cosmos DB

**Alternativele la sharding:**

1. **Replicare:** Pentru scalarea operațiunilor de citire
2. **Vertical partitioning:** Împărțirea tabelelor pe coloane
3. **Caching layers:** Redis, Memcached pentru reducerea încărcării
4. **Read replicas:** Pentru distribuirea încărcării de citire

### 28. Cum gestionezi migrările de baze de date într-o aplicație în dezvoltare continuă?
**Răspuns:** Gestionarea migrărilor de baze de date este esențială pentru dezvoltarea continuă a aplicațiilor, permițând evoluția schemei bazei de date în paralel cu codul aplicației. Un sistem bun de migrare asigură că toate mediile (dezvoltare, testare, producție) au aceeași structură de bază de date.

**Concepte fundamentale:**

1. **Migrare:** O schimbare discretă, numerotată, a schemei bazei de date
2. **Versioning:** Urmărirea versiunii curente a bazei de date
3. **Up/Down Migration:** Cod pentru aplicarea schimbării (up) și pentru anularea ei (down)
4. **Migration History:** Înregistrarea migrărilor aplicate

**Proces de bază pentru gestionarea migrărilor:**

1. **Crearea migrărilor:**
   - Generarea unui fișier de migrare pentru fiecare schimbare
   - Numerotarea/datarea secvențială pentru a stabili ordinea
   - Implementarea atât a codului "up" cât și "down"

2. **Testarea migrărilor:**
   - Verificarea pe un mediu de dezvoltare
   - Asigurarea că migrarea poate fi anulată (down migration)
   - Testarea impactului asupra datelor existente

3. **Aplicarea migrărilor:**
   - Executarea migrărilor în ordinea corectă
   - Înregistrarea migrărilor aplicate
   - Verificarea stării finale a bazei de date

4. **Integrarea în CI/CD:**
   - Automatizarea aplicării migrărilor la deployment
   - Verificarea consistenței între versiunile de cod și migrări
   - Rollback automat în caz de eșec

**Unelte și framework-uri pentru migrări:**

1. **Soluții dedicate:**
   - **Flyway:** Bazat pe convenții, suport pentru SQL nativ
   - **Liquibase:** Bazat pe XML/YAML/JSON, abstractizare mai mare
   - **Alembic:** Pentru Python/SQLAlchemy

2. **Framework-uri cu suport integrat:**
   - **Rails ActiveRecord Migrations** (Ruby on Rails)
   - **Laravel Migrations** (PHP)
   - **Entity Framework Migrations** (.NET)
   - **Django Migrations** (Python)
   - **Prisma Migrate** (Node.js/TypeScript)

**Exemplu de migrare cu Flyway (SQL):**
```sql
-- V1__Create_customer_table.sql
CREATE TABLE customers (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- V2__Add_customer_status.sql
ALTER TABLE customers ADD COLUMN status VARCHAR(20) DEFAULT 'active';
```

**Exemplu de migrare cu ActiveRecord (Ruby):**
```ruby
# 20230101120000_create_customers.rb
class CreateCustomers < ActiveRecord::Migration[7.0]
  def up
    create_table :customers do |t|
      t.string :name, null: false
      t.string :email
      t.timestamps
    end
    add_index :customers, :email, unique: true
  end
  
  def down
    drop_table :customers
  end
end

# 20230102130000_add_customer_status.rb
class AddCustomerStatus < ActiveRecord::Migration[7.0]
  def up
    add_column :customers, :status, :string, default: 'active'
  end
  
  def down
    remove_column :customers, :status
  end
end
```

**Best practices pentru gestionarea migrărilor:**

1. **Migrări atomice:**
   - Fiecare migrare ar trebui să facă o singură schimbare logică
   - Facilitează debugging-ul și rollback-ul

2. **Idempotență:**
   - Migrările ar trebui să poată fi aplicate de mai multe ori fără efecte secundare
   - Folosirea condițiilor precum "IF NOT EXISTS" sau verificări înainte de modificări

   ```sql
   -- Exemplu de migrare idempotentă
   IF NOT EXISTS (SELECT * FROM information_schema.columns 
                 WHERE table_name = 'customers' AND column_name = 'status')
   BEGIN
       ALTER TABLE customers ADD COLUMN status VARCHAR(20) DEFAULT 'active';
   END
   ```

3. **Migrări ireversibile:**
   - Unele schimbări nu pot fi anulate ușor (ex: ștergerea datelor)
   - Documentează clar schimbările ireversibile
   - Consideră migrări alternative când e posibil

4. **Gestiunea datelor:**
   - Migrarea nu doar a schemei, ci și a datelor când e necesar
   - Strategii pentru transformarea datelor existente

5. **Migrări concurente:**
   - Design pentru compatibilitate între versiuni consecutive ale aplicației
   - Pattern-uri precum "expand-contract" pentru schimbări complexe:
     1. Expandează: Adaugă noua structură fără a afecta cea veche
     2. Migrează: Mută datele și actualizează codul pentru a folosi ambele structuri
     3. Contractează: Elimină structura veche când nu mai e folosită

6. **Performanță:**
   - Considerație pentru impactul migrărilor asupra sistemelor în producție
   - Strategii pentru migrări pe tabele mari (locking, batching)
   - Planificarea migrărilor în ferestre de mentenanță când e necesar

7. **Testare:**
   - Testarea migrărilor cu date reale (anonimizate)
   - Verificarea performanței pe volume mari de date
   - Teste automatizate pentru validarea stării finale

8. **Rollback plan:**
   - Plan clar pentru anularea migrărilor problematice
   - Backup-uri înainte de migrări majore
   - Strategii pentru rollback când down-migration nu e fezabilă

**Strategii pentru migrări complexe:**

1. **Migrări în mai mulți pași:**
   - Împărțirea schimbărilor mari în pași incrementali
   - Deployment-uri multiple cu schimbări compatibile cu versiunea anterioară

2. **Blue-Green Deployments:**
   - Două instanțe ale bazei de date (blue și green)
   - Migrarea pe instanța inactivă, apoi switch-ul traficului

3. **Schema versioning:**
   - Menținerea mai multor versiuni ale schemei în paralel
   - Aplicația poate lucra cu multiple versiuni

4. **Feature Flags:**
   - Controlul activării funcționalităților care necesită schimbări de schemă
   - Permite rollout gradual și testare în producție

### 29. Ce sunt view-urile în SQL și când sunt utile?
**Răspuns:** View-urile în SQL sunt interogări stocate care sunt accesate ca și cum ar fi tabele normale. Ele nu stochează date, ci oferă o reprezentare virtuală a datelor din una sau mai multe tabele de bază.

**Definirea unui view:**
```sql
CREATE VIEW active_customers AS
SELECT customer_id, name, email, city
FROM customers
WHERE status = 'active';

-- Utilizare
SELECT * FROM active_customers;
```

**Caracteristici principale:**

1. **Virtualizare:**
   - Nu stochează date propriu-zise
   - Execută interogarea de bază la fiecare accesare
   - Reflectă întotdeauna datele curente din tabelele de bază

2. **Abstractizare:**
   - Ascunde complexitatea interogărilor
   - Oferă o interfață simplificată pentru date

3. **Tipuri specifice:**
   - **Simple views:** Bazate pe o singură tabelă
   - **Complex views:** Bazate pe multiple tabele (JOINs, GROUP BY, etc.)
   - **Materialized views:** Stochează fizic rezultatele (disponibile în unele DBMS-uri)
   - **Updatable views:** Permit operațiuni DML (cu anumite restricții)

**Când sunt utile view-urile:**

1. **Simplificarea interogărilor complexe:**
   - Encapsularea JOIN-urilor complexe, subquery-urilor și agregărilor
   - Reducerea duplicării codului SQL în aplicație

   ```sql
   CREATE VIEW order_summary AS
   SELECT o.order_id, c.name as customer_name, 
          SUM(oi.quantity * oi.price) as total_amount,
          o.order_date,
          COUNT(oi.item_id) as items_count
   FROM orders o
   JOIN customers c ON o.customer_id = c.customer_id
   JOIN order_items oi ON o.order_id = oi.order_id
   GROUP BY o.order_id, c.name, o.order_date;
   ```

2. **Securitate și control al accesului:**
   - Restricționarea accesului la coloane sau rânduri specifice
   - Oferirea unui nivel de acces granular

   ```sql
   CREATE VIEW employee_public_info AS
   SELECT employee_id, first_name, last_name, department, position
   FROM employees;
   -- Ascunde informații sensibile precum salariul, SSN, etc.
   ```

3. **Compatibilitate și independență a aplicației:**
   - Izolarea aplicației de schimbările în schema de bază
   - Menținerea compatibilității cu sistemele legacy

   ```sql
   -- View care menține o structură compatibilă cu aplicația legacy
   CREATE VIEW legacy_customer_format AS
   SELECT 
     id as customer_number,
     CONCAT(first_name, ' ', last_name) as full_name,
     -- Alte transformări pentru compatibilitate
   FROM customers_new;
   ```

4. **Prezentare a datelor pentru raportare:**
   - Formatarea și agregarea datelor pentru rapoarte
   - Standardizarea interogărilor pentru cerințe comune de business

   ```sql
   CREATE VIEW monthly_sales AS
   SELECT 
     DATE_FORMAT(order_date, '%Y-%m') as month,
     product_category,
     SUM(amount) as total_sales,
     COUNT(DISTINCT customer_id) as unique_customers
   FROM orders
   JOIN order_items ON orders.order_id = order_items.order_id
   JOIN products ON order_items.product_id = products.product_id
   GROUP BY DATE_FORMAT(order_date, '%Y-%m'), product_category;
   ```

5. **Calcularea datelor derivate:**
   - Standardizarea formulelor și a regulilor de business
   - Asigurarea consistenței calculelor în toată aplicația

   ```sql
   CREATE VIEW product_metrics AS
   SELECT 
     product_id,
     name,
     price,
     cost,
     (price - cost) as margin,
     ((price - cost) / cost * 100) as margin_percent
   FROM products;
   ```

6. **Simplificarea migrărilor:**
   - Facilitarea migrărilor graduale între scheme de baze de date
   - Menținerea compatibilității între versiuni ale schemei

**Avantaje ale view-urilor:**

1. **Consistența datelor:**
   - Implementare centralizată a logicii de business
   - Evitarea duplicării logicii în aplicație

2. **Întreținere simplificată:**
   - Modificări ale logicii în locul central (view)
   - Fără necesitatea schimbării codului aplicației

3. **Performanță (în anumite scenarii):**
   - Optimizarea query-urilor complexe de către optimizer
   - Materialized views pentru caching-ul rezultatelor

4. **Reziliență la schimbări:**
   - View-urile pot absorbi schimbări minore în schema de bază

**Limitări și dezavantaje:**

1. **Performanță:**
   - View-urile complexe pot afecta negativ performanța
   - Pot ascunde probleme de optimizare

2. **Restricții pentru view-uri actualizabile:**
   - Multe view-uri complexe nu permit operațiuni UPDATE, INSERT sau DELETE
   - Reguli specifice DBMS-ului pentru actualizabilitate

3. **Dependențe ascunse:**
   - View-urile creează dependențe între obiecte în baza de date
   - Pot complica refactorizările majore

**Materialized Views:**

Un tip special de view disponibil în unele DBMS-uri (PostgreSQL, Oracle) care stochează fizic rezultatele interogării:

```sql
CREATE MATERIALIZED VIEW monthly_sales_summary AS
SELECT 
  DATE_TRUNC('month', order_date) as month,
  SUM(amount) as total_sales
FROM orders
GROUP BY DATE_TRUNC('month', order_date);

-- Actualizarea unui materialized view
REFRESH MATERIALIZED VIEW monthly_sales_summary;
```

**Avantaje:**
- Performanță mult mai bună pentru interogări complexe
- Reduc încărcarea pentru calcule intensive

**Dezavantaje:**
- Datele pot deveni învechite (necesită refresh explicit)
- Consumă spațiu de stocare

### 30. Explică conceptul de race condition în contextul bazelor de date și cum poate fi evitat.
**Răspuns:** O race condition (condiție de cursă) în contextul bazelor de date apare când două sau mai multe tranzacții accesează și modifică aceleași date simultan, iar rezultatul final depinde de ordinea exactă a operațiunilor. Acest comportament poate duce la inconsistențe, date corupte sau rezultate neașteptate.

**Scenarii tipice de race condition:**

1. **Lost Updates (Actualizări pierdute):**
   - Două tranzacții citesc aceeași valoare
   - Ambele fac modificări bazate pe valoarea inițială
   - Ultima tranzacție care scrie suprascrie modificările primei

   ```
   Tranzacția 1: Citește sold = 1000
   Tranzacția 2: Citește sold = 1000
   Tranzacția 1: Calculează noul sold = 1000 - 200 = 800
   Tranzacția 2: Calculează noul sold = 1000 + 500 = 1500
   Tranzacția 1: Scrie sold = 800
   Tranzacția 2: Scrie sold = 1500 (suprascrie T1, pierderea retragerii de 200)
   ```

2. **Dirty Reads (Citiri murdare):**
   - O tranzacție citește date modificate de o altă tranzacție care nu a fost încă validată (commit)
   - Dacă a doua tranzacție face rollback, prima a lucrat cu date invalide

3. **Non-repeatable Reads (Citiri nerepetabile):**
   - O tranzacție citește aceleași date de două ori
   - Între cele două citiri, o altă tranzacție modifică și validează datele
   - A doua citire returnează valori diferite de prima

4. **Phantom Reads (Citiri fantomă):**
   - O tranzacție execută o interogare care returnează un set de rânduri
   - O altă tranzacție inserează sau șterge rânduri care ar fi fost incluse în rezultatul primei interogări
   - O reexecutare a interogării inițiale returnează un set diferit de rânduri

**Metode de evitare a race conditions:**

1. **Izolarea tranzacțiilor:**
   - Setarea unui nivel adecvat de izolare a tranzacțiilor
   - Balansarea între consistență și concurență

   ```sql
   -- Setarea nivelului de izolare în SQL
   SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
   
   BEGIN TRANSACTION;
   -- operațiuni
   COMMIT;
   ```

   **Niveluri de izolare (standard SQL):**
   - **READ UNCOMMITTED:** Cel mai relaxat, permite toate fenomenele de concurență
   - **READ COMMITTED:** Previne dirty reads, dar permite non-repeatable și phantom reads
   - **REPEATABLE READ:** Previne dirty și non-repeatable reads, dar permite phantom reads
   - **SERIALIZABLE:** Cel mai strict, previne toate fenomenele, dar reduce concurența

2. **Locking explicit:**
   - **Shared (Read) Locks:** Permit altor tranzacții să citească, dar nu să modifice
   - **Exclusive (Write) Locks:** Împiedică alte tranzacții să citească sau să modifice

   ```sql
   -- Exemplu de lock explicit în MySQL
   SELECT * FROM accounts WHERE account_id = 123 FOR UPDATE;
   
   -- Exemplu în PostgreSQL
   SELECT * FROM accounts WHERE account_id = 123 FOR UPDATE;
   ```

3. **Operații atomice:**
   - Utilizarea operațiilor atomic oferite de DBMS

   ```sql
   -- Atomic update fără race condition
   UPDATE accounts 
   SET balance = balance - 200 
   WHERE account_id = 123;
   ```

4. **Optimistic Concurrency Control (OCC):**
   - Se bazează pe detectarea conflictelor, nu pe prevenirea lor
   - Utilizează versiuni sau timestamps pentru a detecta modificări concurente
   - Potrivit pentru situații cu probabilitate scăzută de conflict

   ```sql
   -- Implementare simplă cu version column
   UPDATE accounts 
   SET balance = 800, version = version + 1 
   WHERE account_id = 123 AND version = 5;
   
   -- Dacă 0 rânduri afectate, înseamnă că a fost modificat între timp
   ```

5. **Pessimistic Concurrency Control (PCC):**
   - Se bazează pe blocarea resurselor înainte de modificare
   - Previne conflictele, dar poate reduce concurența
   - Potrivit pentru situații cu probabilitate ridicată de conflict

6. **Database Constraints:**
   - Utilizarea constrângerilor pentru a asigura integritatea datelor
   - Constrângeri de unicitate, chei străine, etc.

7. **Application-level strategies:**
   - Proiectarea tranzacțiilor pentru a minimiza suprapunerile
   - Utilizarea pattern-urilor precum Command Query Responsibility Segregation (CQRS)

**Exemple concrete de evitare a race conditions:**

**Exemplu 1: Transfer bancar sigur**
```sql
BEGIN TRANSACTION;
  -- Lock ambele conturi implicate (ordinea previne deadlocks)
  SELECT * FROM accounts WHERE account_id IN (123, 456) ORDER BY account_id FOR UPDATE;
  
  -- Verifică dacă există sold suficient
  SELECT balance FROM accounts WHERE account_id = 123 INTO @balance;
  IF @balance >= 200 THEN
    -- Efectuează transferul
    UPDATE accounts SET balance = balance - 200 WHERE account_id = 123;
    UPDATE accounts SET balance = balance + 200 WHERE account_id = 456;
    
    -- Înregistrează tranzacția
    INSERT INTO transactions(from_account, to_account, amount) VALUES (123, 456, 200);
  ELSE
    -- Nu există sold suficient
    ROLLBACK;
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Insufficient funds';
  END IF;
COMMIT;
```

**Exemplu 2: Incrementare concurentă sigură (inventory management)**
```sql
-- Versiunea vulnerabilă la race condition
SELECT quantity FROM inventory WHERE product_id = 42;  -- Să zicem că returnează 10
-- Calculează noua cantitate
-- quantity = 10 - 3 = 7
UPDATE inventory SET quantity = 7 WHERE product_id = 42;

-- Versiunea sigură
UPDATE inventory 
SET quantity = quantity - 3 
WHERE product_id = 42 AND quantity >= 3;

-- Verifică dacă a fost actualizat
IF ROW_COUNT() = 0 THEN
  -- Nu s-a putut actualiza, probabil cantitate insuficientă
END IF;
```

**Exemplu 3: Optimistic locking cu version column**
```sql
-- Citirea inițială
SELECT id, data, version FROM documents WHERE id = 101;

-- Utilizatorul face modificări
-- ...

-- Încercarea de a salva modificările
UPDATE documents 
SET data = 'New content', version = version + 1 
WHERE id = 101 AND version = 3;

-- Verifică dacă a fost actualizat
IF ROW_COUNT() = 0 THEN
  -- Conflict detectat, date modificate între timp
  -- Afișează mesaj utilizatorului sau încearcă din nou
END IF;
```

**Deadlocks și prevenirea lor:**

Un deadlock apare când două sau mai multe tranzacții se așteaptă reciproc să elibereze resurse blocate. Strategii pentru prevenirea deadlock-urilor:

1. **Ordinea consistentă de blocare:**
   - Întotdeauna accesează resursele în aceeași ordine (ex: blocare conturi în ordine de ID)

2. **Timeouts:**
   - Setarea unui timeout pentru achiziția lock-urilor
   
3. **Detectare și rezolvare:**
   - DBMS-urile moderne detectează și rezolvă automat deadlock-urile
   - De obicei, una din tranzacții este aleasă ca "victimă" și primește rollback

## Tehnici de Programare Fundamentale

### 31. Care sunt structurile de date fundamentale și când ai folosi fiecare?
**Răspuns:** Structurile de date sunt moduri de organizare a datelor pentru utilizare eficientă în diferite operațiuni. Alegerea structurii de date potrivite este esențială pentru performanța și corectitudinea algoritmilor.

**1. Arrays (Tablouri/Vectori):**
- **Descriere:** Colecție de elemente de același tip, stocate secvențial în memorie.
- **Operațiuni eficiente:** Accesul direct prin index (O(1)), iterare secvențială.
- **Operațiuni ineficiente:** Inserare/ștergere în poziții arbitrare (O(n)).
- **Variante:** Array unidimensional, multidimensional, jagged array.
- **Când să-l folosești:**
  - Când ai nevoie de acces rapid la elemente prin index
  - Când dimensiunea este fixă sau rar schimbată
  - Pentru implementarea altor structuri de date
  - Pentru algoritmi bazați pe accesul secvențial

```javascript
// JavaScript
const numbers = [1, 2, 3, 4, 5];
const matrix = [[1, 2], [3, 4], [5, 6]]; // Array 2D
```

**2. Linked Lists (Liste înlănțuite):**
- **Descriere:** Secvență de noduri, fiecare conținând date și referințe către nodul(urile) adiacent(e).
- **Operațiuni eficiente:** Inserare/ștergere la început/sfârșit (O(1)), inserare după un nod cunoscut.
- **Operațiuni ineficiente:** Accesul la poziție arbitrară (O(n)).
- **Variante:** Simplu înlănțuită, dublu înlănțuită, circulară.
- **Când să o folosești:**
  - Când ai nevoie de inserări/ștergeri frecvente
  - Când dimensiunea este dinamică
  - Când accesul secvențial este suficient
  - Pentru implementarea stack-urilor și queue-urilor

```java
// Java
class Node {
    int data;
    Node next;
    
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class LinkedList {
    Node head;
    
    void add(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        
        Node current = head;
        while (current.next != null) {
            current = current.next;
        }
        current.next = newNode;
    }
}
```

**3. Stacks (Stive):**
- **Descriere:** Colecție LIFO (Last In, First Out).
- **Operațiuni principale:** push (adăugare), pop (eliminare), peek (consultare vârf).
- **Complexitate:** O(1) pentru toate operațiunile principale.
- **Când să o folosești:**
  - Pentru evaluarea expresiilor
  - Pentru urmărirea apelurilor de funcții
  - Pentru algoritmi de backtracking
  - Pentru management-ul memoriei
  - Pentru implementarea undo/redo
  - Pentru algoritmi de parsare

```python
# Python
stack = []
stack.append(1)  # push
stack.append(2)
top = stack.pop()  # pop, top = 2
```

**4. Queues (Cozi):**
- **Descriere:** Colecție FIFO (First In, First Out).
- **Operațiuni principale:** enqueue (adăugare), dequeue (eliminare), peek (consultare început).
- **Complexitate:** O(1) pentru toate operațiunile principale.
- **Variante:** Queue simplă, deque (double-ended queue), priority queue.
- **Când să o folosești:**
  - Pentru procesarea task-urilor în ordinea sosirii
  - Pentru algoritmi BFS (Breadth-First Search)
  - Pentru buffering și caching
  - Pentru gestionarea resurselor partajate

```csharp
// C#
Queue<string> queue = new Queue<string>();
queue.Enqueue("first");  // adăugare
queue.Enqueue("second");
string item = queue.Dequeue();  // eliminare, item = "first"
```

**5. Hash Tables (Tabele hash):**
- **Descriere:** Structură care mapează chei la valori folosind o funcție hash.
- **Operațiuni eficiente:** Inserare, căutare, ștergere (în medie O(1)).
- **Operațiuni ineficiente:** Iterare ordonată.
- **Variante:** HashMap, HashSet, Dictionary, Hashtable.
- **Când să o folosești:**
  - Pentru căutare rapidă, inserare și ștergere
  - Pentru implementarea cache-urilor
  - Pentru eliminarea duplicatelor
  - Pentru mapări chei-valori
  - Pentru optimizarea algoritmilor prin memoizare

```javascript
// JavaScript
const userInfo = new Map();
userInfo.set('name', 'John');
userInfo.set('age', 30);
console.log(userInfo.get('name'));  // John
```

**6. Trees (Arbori):**
- **Descriere:** Structură ierarhică cu noduri conectate prin edge-uri.
- **Variante:**
  - **Binary Tree:** Fiecare nod are maxim doi copii
  - **Binary Search Tree (BST):** Tree ordonat (stânga < părinte < dreapta)
  - **AVL Tree:** BST balansat
  - **Red-Black Tree:** BST balansat cu proprietăți specifice
  - **B-Tree și B+ Tree:** Pentru sisteme de fișiere și baze de date
- **Operațiuni:** Inserare, căutare, ștergere, traversare
- **Când să-l folosești:**
  - Pentru reprezentarea datelor ierarhice
  - Pentru căutare eficientă (BST: O(log n) în cazul mediu)
  - Pentru parcurgerea în diferite ordini (preorder, inorder, postorder)
  - Pentru implementarea dicționarelor și mulțimilor
  - Pentru compresie (Huffman trees)

```python
# Python - Binary Search Tree
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

class BST:
    def __init__(self):
        self.root = None
        
    def insert(self, key):
        if self.root is None:
            self.root = Node(key)
        else:
            self._insert(self.root, key)
            
    def _insert(self, node, key):
        if key < node.val:
            if node.left is None:
                node.left = Node(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = Node(key)
            else:
                self._insert(node.right, key)
```

**7. Graphs (Grafuri):**
- **Descriere:** Colecție de noduri/vertices conectate prin edge-uri/arce.
- **Reprezentări:** Liste de adiacență, matrice de adiacență, matrice de incidență.
- **Variante:** Graf direcționat, nedirecționat, ponderat, neponderat, ciclic, aciclic.
- **Algoritmi comuni:** DFS, BFS, Dijkstra, Bellman-Ford, Kruskal, Prim.
- **Când să-l folosești:**
  - Pentru modelarea rețelelor (sociale, transport, comunicații)
  - Pentru probleme de rutare și căutare de drum
  - Pentru analiza dependențelor
  - Pentru algoritmi de scheduling
  - Pentru probleme de flow/network

```java
// Java - Graf reprezentat prin listă de adiacență
class Graph {
    private int V; // Număr de noduri
    private LinkedList<Integer>[] adj; // Liste de adiacență
    
    Graph(int v) {
        V = v;
        adj = new LinkedList[v];
        for (int i = 0; i < v; ++i)
            adj[i] = new LinkedList<>();
    }
    
    void addEdge(int v, int w) {
        adj[v].add(w); // Adaugă w la lista lui v
    }
}
```

**8. Heap (Grămadă):**
- **Descriere:** Arbore binar complet cu proprietatea de heap (max sau min).
- **Operațiuni principale:** inserare, extragere max/min, construire.
- **Complexitate:** Inserare: O(log n), Extragere max/min: O(log n), Construire: O(n).
- **Când să-l folosești:**
  - Pentru priority queues
  - Pentru algoritmi de sortare (heap sort)
  - Pentru găsirea top-k elemente
  - Pentru algoritmi de grafuri (Dijkstra)

```python
# Python - folosind heapq (min-heap)
import heapq

h = []
heapq.heappush(h, (5, 'task5'))
heapq.heappush(h, (1, 'task1'))
heapq.heappush(h, (3, 'task3'))

# Extrage elementul cu prioritatea cea mai mică
next_task = heapq.heappop(h)  # (1, 'task1')
```

**9. Trie (Arbore de prefix):**
- **Descriere:** Arbore pentru stocarea eficientă a șirurilor, cu elemente comune partajate.
- **Operațiuni:** Inserare, căutare, ștergere, căutare prefix.
- **Când să-l folosești:**
  - Pentru autocomplete/sugestii
  - Pentru verificarea cuvintelor (spell checking)
  - Pentru căutări de prefix
  - Pentru algoritmi de string matching

```javascript
// JavaScript - Trie simplu
class TrieNode {
    constructor() {
        this.children = {};
        this.isEndOfWord = false;
    }
}

class Trie {
    constructor() {
        this.root = new TrieNode();
    }
    
    insert(word) {
        let current = this.root;
        for (let char of word) {
            if (!current.children[char]) {
                current.children[char] = new TrieNode();
            }
            current = current.children[char];
        }
        current.isEndOfWord = true;
    }
    
    search(word) {
        let current = this.root;
        for (let char of word) {
            if (!current.children[char]) {
                return false;
            }
            current = current.children[char];
        }
        return current.isEndOfWord;
    }
}
```

**10. Set și MultiSet (Bag):**
- **Descriere:** Colecție de elemente unice (Set) sau cu duplicate permise (MultiSet).
- **Operațiuni eficiente:** Adăugare, eliminare, verificare a existenței.
- **Când să-l folosești:**
  - Pentru eliminarea duplicatelor
  - Pentru testarea apartenenței
  - Pentru operații de mulțimi (uniune, intersecție)
  - Pentru numărarea frecvențelor (MultiSet)

```csharp
// C#
HashSet<int> uniqueNumbers = new HashSet<int>();
uniqueNumbers.Add(5);
uniqueNumbers.Add(5);  // Ignorat, 5 există deja
bool contains = uniqueNumbers.Contains(5);  // true
```

**Alegerea structurii de date potrivite:**

Când alegi o structură de date, consideră:
1. Operațiunile necesare și frecvența lor
2. Complexitatea timpului pentru operațiunile critice
3. Cerințele de memorie
4. Ușurința de implementare și întreținere
5. Scalabilitatea

O alegere bună a structurii de date poate face diferența între un algoritm eficient și unul ineficient pentru aceeași problemă.

### 32. Explică complexitatea algoritmilor și notația Big O.
**Răspuns:** Complexitatea algoritmilor este o măsură a resurselor (timp și spațiu) necesare pentru a executa un algoritm în funcție de dimensiunea datelor de intrare. Notația Big O este cel mai comun mod de a exprima această complexitate, concentrându-se pe comportamentul asimptotic (cazul cel mai defavorabil) când dimensiunea intrării devine mare.

**Ce este notația Big O:**
- O(f(n)) descrie o limită superioară a timpului de execuție (sau a spațiului utilizat) în funcție de dimensiunea intrării n
- Indică rata de creștere a complexității, nu timpul exact
- Se concentrează pe termenul dominant, ignorând constante și termeni de ordin inferior
- Exprimă cazul cel mai defavorabil (worst-case scenario)

**Proprietăți ale notației Big O:**
- Ignoră constante: O(2n) = O(n)
- Ignoră termenii de ordin inferior: O(n² + n) = O(n²)
- Poate fi combinată pentru algoritmi secvențiali: O(f(n)) + O(g(n)) = O(max(f(n), g(n)))
- Poate fi multiplicată pentru algoritmi imbricați: O(f(n)) * O(g(n)) = O(f(n) * g(n))

**Clase comune de complexitate (în ordine crescătoare):**

1. **O(1) - Timp constant:**
   - Timpul de execuție nu depinde de dimensiunea intrării
   - Exemple: Accesul într-un array prin index, inserarea/eliminarea la început/sfârșit în liste dublu înlănțuite, operațiuni pe stack și queue

```javascript
function isEven(num) {
    return num % 2 === 0;  // O(1)
}
```

2. **O(log n) - Timp logaritmic:**
   - Timpul crește logaritmic cu dimensiunea intrării
   - Apare adesea în algoritmi care înjumătățesc problema la fiecare pas
   - Exemple: Căutare binară, operațiuni în arbori balansați, algoritmi divide-and-conquer eficienți

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1  # O(log n)
```

3. **O(n) - Timp liniar:**
   - Timpul crește liniar cu dimensiunea intrării
   - Exemple: Traversarea unei liste/array, căutare secvențială, găsirea minimului/maximului

```java
int sum(int[] array) {
    int total = 0;
    for (int value : array) {
        total += value;
    }
    return total;  // O(n)
}
```

4. **O(n log n) - Timp linearitmic:**
   - Apare adesea în algoritmi eficienți de sortare și dividere
   - Exemple: Merge sort, quick sort (caz mediu), heap sort, algoritmi eficienți pe arbori

```javascript
function mergeSort(arr) {
    if (arr.length <= 1) return arr;
    
    const mid = Math.floor(arr.length / 2);
    const left = mergeSort(arr.slice(0, mid));
    const right = mergeSort(arr.slice(mid));
    
    return merge(left, right);  // O(n log n)
}
```

5. **O(n²) - Timp pătratic:**
   - Apare adesea în algoritmi care implică verificarea tuturor perechilor posibile
   - Exemple: Bubble sort, insertion sort, selection sort, compararea tuturor elementelor între ele

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr  # O(n²)
```

6. **O(2^n) - Timp exponențial:**
   - Timpul se dublează (aproximativ) cu fiecare element adăugat
   - Deseori impracticabil pentru intrări de dimensiuni medii sau mari
   - Exemple: Generarea tuturor submulțimilor, rezolvarea problemei comis-voiajorului prin forță brută, recursivitate ineficientă

```javascript
function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);  // O(2^n)
}
```

7. **O(n!) - Timp factorial:**
   - Crește extrem de rapid cu dimensiunea intrării
   - Practic imposibil pentru intrări mai mari de ~10-12 elemente
   - Exemple: Generarea tuturor permutărilor, rezolvarea problemei comis-voiajorului prin verificarea tuturor rutelor posibile

```python# Răspunsuri la Top 50 Întrebări pentru Interviu Fullstack Developer

## Programare Orientată pe Obiecte (OOP)

### 1. Ce este programarea orientată pe obiecte și care sunt principalele sale caracteristici?
**Răspuns:** Programarea orientată pe obiecte (OOP) este o paradigmă de programare bazată pe conceptul de "obiecte", care pot conține date și cod: date sub formă de câmpuri (atribute sau proprietăți) și cod sub formă de proceduri (metode). Principalele caracteristici ale OOP sunt:
- **Încapsulare** - ascunderea detaliilor de implementare și restricționarea accesului direct la componente
- **Moștenire** - capacitatea unei clase de a prelua proprietăți și metode de la o altă clasă
- **Polimorfism** - capacitatea de a prezenta aceeași interfață pentru diferite tipuri de date subiacente
- **Abstractizare** - procesul de ascundere a detaliilor complexe și prezentarea doar a funcționalităților esențiale

### 2. Explică cele 4 principii fundamentale ale OOP: Încapsulare, Moștenire, Polimorfism și Abstractizare.
**Răspuns:**
- **Încapsulare:** Principiul de a împacheta datele (atributele) și metodele care operează pe date într-o singură unitate (clasă) și de a restricționa accesul direct la unele componente. Se implementează prin specificatori de acces (public, private, protected). Avantaj: ascunde implementarea și expune doar funcționalitățile necesare.

- **Moștenire:** Permite unei clase (derivată/copil) să preia proprietățile și comportamentele unei alte clase (de bază/părinte). Ajută la reutilizarea codului și stabilirea unei ierarhii între clase. Exemplu: clasa "Car" poate moșteni atribute și metode de la clasa "Vehicle".

- **Polimorfism:** Capacitatea obiectelor de clase diferite de a răspunde la aceeași metodă în moduri diferite. Există două tipuri principale: polimorfism la compilare (overloading) și polimorfism la runtime (overriding).

- **Abstractizare:** Procesul de identificare a caracteristicilor esențiale ale unui obiect și ignorarea detaliilor nerelevante. Se implementează prin clase abstracte și interfețe, permitând definirea unui model conceptual fără a specifica toate detaliile de implementare.

### 3. Ce este o clasă și ce este un obiect în OOP?
**Răspuns:** 
- **Clasa** este un blueprint sau un șablon care definește structura și comportamentul (atribute și metode) pe care obiectele de acest tip le vor avea. Este o definiție teoretică a unui tip de date.

- **Obiectul** este o instanță concretă a unei clase. Acesta ocupă spațiu în memorie și are valori specifice pentru atributele definite în clasă. Obiectele sunt entități în timp real care pot efectua acțiunile definite prin metodele clasei.

Exemplu:
```java
// Definirea unei clase
class Car {
    String make;
    String model;
    int year;
    
    void startEngine() {
        System.out.println("Engine started!");
    }
}

// Crearea unui obiect (instanță)
Car myCar = new Car();
myCar.make = "Toyota";
myCar.startEngine(); // Apelarea unei metode
```

### 4. Care este diferența dintre o clasă abstractă și o interfață?
**Răspuns:**

**Clasă abstractă:**
- Poate conține atât metode abstracte (fără implementare) cât și metode concrete (cu implementare)
- Poate conține variabile de membru, constructori
- O clasă poate moșteni doar o singură clasă abstractă
- Suportă specificatori de acces (public, private, protected)
- Folosită când există funcționalități comune între clase înrudite

**Interfață:**
- Conține doar declarații de metode (în Java 8+ poate include metode default și statice)
- Nu poate conține variabile de instanță (doar constante)
- O clasă poate implementa multiple interfețe (rezolvând problema moștenirii multiple)
- Toate metodele sunt implicit publice
- Folosită pentru a defini un contract între obiecte fără a specifica implementarea

Interfețele definesc "ce poate face" un obiect, iar clasele abstracte definesc parțial "ce este" un obiect.

### 5. Ce înseamnă suprascrierea (overriding) și supraîncărcarea (overloading) metodelor?
**Răspuns:**

**Suprascrierea (Overriding):**
- Permite unei subclase să ofere o implementare specifică pentru o metodă deja definită în superclasă
- Metoda din subclasă trebuie să aibă aceeași semnătură (nume, parametri, tip returnat) ca cea din superclasă
- Se aplică la runtime (polimorfism dinamic)
- Este marcată de obicei cu anotarea `@Override`

Exemplu:
```java
class Animal {
    void makeSound() {
        System.out.println("Generic animal sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Woof woof!");
    }
}
```

**Supraîncărcarea (Overloading):**
- Permite definirea mai multor metode cu același nume în aceeași clasă, dar cu parametri diferiți
- Metodele pot varia în numărul, tipul sau ordinea parametrilor
- Se decide la compilare (polimorfism static)
- Nu are legătură cu moștenirea

Exemplu:
```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }
    
    double add(double a, double b) {
        return a + b;
    }
    
    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

### 6. Explică conceptul de moștenire multiplă și problemele asociate cu aceasta.
**Răspuns:** Moștenirea multiplă este un concept în OOP care permite unei clase să moștenească atribute și metode de la mai multe clase părinte. Nu toate limbajele de programare o suportă direct (Java și C# nu, C++ da).

**Probleme asociate:**
1. **Problema diamantului:** Apare când o clasă moștenește de la două clase care au la rândul lor un părinte comun. Ambiguitatea apare în determinarea versiunii metodei care trebuie folosită.

```
    A
   / \
  B   C
   \ /
    D
```

2. **Conflicte de nume:** Când clase părinte diferite au metode sau atribute cu același nume.

3. **Complexitatea designului:** Crește complexitatea și poate duce la un cod greu de întreținut.

4. **Încălcarea principiului de responsabilitate unică:** Poate duce la clase care au prea multe responsabilități.

**Soluții alternative:**
- Utilizarea interfețelor (în Java, C#)
- Utilizarea mixins sau traits (în PHP, Scala)
- Utilizarea compoziției în locul moștenirii multiple

### 7. Ce sunt design patterns? Dă exemplu de 2-3 design patterns comune și când le-ai folosi.
**Răspuns:** Design patterns sunt soluții reutilizabile pentru probleme comune de design software. Ele reprezintă cele mai bune practici și sunt testate în timp de dezvoltatori.

**Exemple de design patterns:**

1. **Singleton Pattern:**
   - Asigură că o clasă are o singură instanță și oferă un punct global de acces la aceasta
   - **Când să-l folosești:** Pentru obiecte care trebuie să fie unice în întreaga aplicație (conexiuni la baze de date, configurații, logging)

2. **Factory Pattern:**
   - Oferă o interfață pentru crearea de obiecte fără a specifica clasa concretă
   - **Când să-l folosești:** Când sistemul trebuie să fie independent de cum sunt create, compuse și reprezentate obiectele

3. **Observer Pattern:**
   - Definește o dependență one-to-many între obiecte, astfel încât când un obiect își schimbă starea, toți dependenții săi sunt notificați
   - **Când să-l folosești:** În sistemele de UI (pentru actualizarea componentelor), pentru evenimente și notificări, implementarea pattern-ului publish-subscribe

4. **Strategy Pattern:**
   - Definește o familie de algoritmi, încapsulează fiecare în parte și le face interschimbabile
   - **Când să-l folosești:** Când ai nevoie de diferite variante ale unui algoritm sau când un algoritm are mai multe comportamente care pot fi schimbate dinamic

### 8. Ce este Singleton pattern și când ar trebui folosit?
**Răspuns:** Singleton este un design pattern creațional care garantează că o clasă are o singură instanță și oferă un punct global de acces la această instanță.

**Implementare tipică:**
```java
public class Singleton {
    // Instanța statică privată
    private static Singleton instance;
    
    // Constructor privat pentru a preveni instanțierea din exterior
    private Singleton() {}
    
    // Metodă statică publică pentru a obține instanța
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

**Pentru thread safety:**
```java
public class ThreadSafeSingleton {
    private static ThreadSafeSingleton instance;
    
    private ThreadSafeSingleton() {}
    
    public static synchronized ThreadSafeSingleton getInstance() {
        if (instance == null) {
            instance = new ThreadSafeSingleton();
        }
        return instance;
    }
}
```

**Când să folosești Singleton:**
- Când trebuie să existe exact o instanță a unei clase (conexiuni la baze de date)
- Când instanța trebuie să fie accesibilă din orice punct al aplicației
- Pentru resurse partajate (pools, caches, registre)
- Pentru configurații globale sau manageri centralizați

**Dezavantaje:**
- Poate face testarea mai dificilă (creează cuplaj strâns)
- Poate acționa ca o variabilă globală ascunsă
- Poate complica multithreading-ul dacă nu este implementat corect

### 9. Ce este Factory pattern și când ar trebui folosit?
**Răspuns:** Factory Pattern este un design pattern creațional care oferă o interfață pentru crearea de obiecte într-o superclasă, dar permite subclaselor să modifice tipul de obiecte care vor fi create.

**Există trei variante principale:**
1. **Simple Factory:** Nu este un pattern oficial, dar o practică comună
2. **Factory Method:** Definește o interfață pentru crearea unui obiect, dar lasă subclasele să decidă ce clasă să instanțieze
3. **Abstract Factory:** Oferă o interfață pentru crearea de familii de obiecte înrudite fără a specifica clasele concrete

**Exemplu de Factory Method:**
```java
// Interfață produs
interface Product {
    void operation();
}

// Implementări concrete
class ConcreteProductA implements Product {
    @Override
    public void operation() {
        System.out.println("Operation from Product A");
    }
}

class ConcreteProductB implements Product {
    @Override
    public void operation() {
        System.out.println("Operation from Product B");
    }
}

// Creator abstract
abstract class Creator {
    public abstract Product createProduct();
    
    public void someOperation() {
        // Folosește produsul
        Product product = createProduct();
        product.operation();
    }
}

// Implementări concrete ale creatorului
class ConcreteCreatorA extends Creator {
    @Override
    public Product createProduct() {
        return new ConcreteProductA();
    }
}

class ConcreteCreatorB extends Creator {
    @Override
    public Product createProduct() {
        return new ConcreteProductB();
    }
}
```

**Când să folosești Factory Pattern:**
- Când o clasă nu poate anticipa clasa de obiecte pe care trebuie să le creeze
- Când vrei să încapsulezi logica de creare și să separezi crearea de utilizare
- Pentru a respecta principiul open/closed: extinderea sistemului cu noi tipuri fără a modifica codul existent
- Când ai familii de obiecte care trebuie folosite împreună

### 10. Ce înseamnă "composition over inheritance" și de ce este important?
**Răspuns:** "Composition over inheritance" (compoziție în locul moștenirii) este un principiu de design în programarea orientată pe obiecte care sugerează că este mai bine să obții funcționalități noi prin compoziția obiectelor (conținerea altor obiecte care furnizează funcționalitatea dorită) decât prin moștenire.

**De ce este important:**
1. **Flexibilitate mai mare:** Compoziția permite schimbarea comportamentului la runtime prin schimbarea obiectelor componente.
2. **Cuplaj mai redus:** Obiectele dependente pot fi înlocuite cu implementări alternative.
3. **Evită ierarhii complexe de moștenire:** Previne problemele asociate cu ierarhii adânci și moștenire multiplă.
4. **Respectă principiul "Has-a" vs "Is-a":** Compoziția reprezintă relații "Has-a" (un Car are un Engine), în timp ce moștenirea reprezintă relații "Is-a" (un Car este un Vehicle).

**Exemplu:**
În loc de:
```java
class Animal {
    void eat() { ... }
    void move() { ... }
}

class Bird extends Animal {
    void fly() { ... }
}

class Penguin extends Bird {  // Problema: pinguinii nu pot zbura!
    @Override
    void fly() {
        throw new UnsupportedOperationException();
    }
}
```

Mai bine:
```java
interface Eater {
    void eat();
}

interface Mover {
    void move();
}

interface Flyer {
    void fly();
}

class Animal implements Eater, Mover {
    public void eat() { ... }
    public void move() { ... }
}

class Bird extends Animal implements Flyer {
    public void fly() { ... }
}

class Penguin extends Animal {  // Pinguinul nu implementează Flyer
    // Nu există metoda fly() - nu apare problema
}
```

### 11. Explică conceptul de dependency injection.
**Răspuns:** Dependency Injection (DI) este un design pattern în care obiectele primesc dependențele lor din exterior, în loc să le creeze sau să le găsească singure. Acest lucru promovează un cuplaj redus între componente și face codul mai ușor de testat, întreținut și extins.

**Tipuri de Dependency Injection:**
1. **Constructor Injection:** Dependențele sunt furnizate prin constructorul clasei
2. **Setter Injection:** Dependențele sunt furnizate prin metode setter
3. **Interface Injection:** Dependențele sunt furnizate prin implementarea unei interfețe

**Exemplu de Constructor Injection:**
```java
// Fără Dependency Injection
class UserService {
    private UserRepository repository;
    
    public UserService() {
        // Serviciul creează propria dependență - cuplaj strâns
        this.repository = new MySQLUserRepository();
    }
}

// Cu Dependency Injection
class UserService {
    private UserRepository repository;
    
    // Dependența este injectată din exterior
    public UserService(UserRepository repository) {
        this.repository = repository;
    }
}

// Utilizare
UserRepository repository = new MySQLUserRepository();
// Sau pentru testare: UserRepository repository = new MockUserRepository();
UserService service = new UserService(repository);
```

**Avantaje:**
- **Testabilitate:** Facilitează testarea prin mock-uri și stub-uri
- **Reducerea cuplajului:** Clasele depind de abstracții, nu de implementări concrete
- **Flexibilitate:** Comportamentul poate fi schimbat furnizând implementări diferite
- **Separarea responsabilităților:** Separarea creării obiectelor de utilizarea lor

**Frameworks pentru DI:**
- Spring (Java)
- Angular (JavaScript/TypeScript)
- ASP.NET Core (C#)

### 12. Ce sunt excepțiile și cum le gestionezi în OOP?
**Răspuns:** Excepțiile sunt evenimente care apar în timpul execuției unui program și perturbă fluxul normal de instrucțiuni. Ele sunt folosite pentru a gestiona situațiile de eroare și condițiile neașteptate într-un mod structurat.

**Gestionarea excepțiilor în OOP:**

1. **Try-Catch-Finally:**
```java
try {
    // Cod care poate genera excepții
    int result = 10 / 0;  // Va genera ArithmeticException
} catch (ArithmeticException e) {
    // Gestionarea excepției specifice
    System.out.println("Cannot divide by zero: " + e.getMessage());
} catch (Exception e) {
    // Gestionarea oricărei alte excepții
    System.out.println("An error occurred: " + e.getMessage());
} finally {
    // Se execută întotdeauna, indiferent dacă apare sau nu o excepție
    System.out.println("Cleanup code");
}
```

2. **Throw și Throws:**
```java
public void validateAge(int age) throws IllegalArgumentException {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
}
```

3. **Crearea excepțiilor personalizate:**
```java
// Excepție personalizată
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

// Utilizare
public void withdraw(double amount) throws InsufficientFundsException {
    if (amount > balance) {
        throw new InsufficientFundsException("Not enough money in account");
    }
    // Rest of the code
}
```

**Principii de bună practică:**
- Prinde excepțiile cât mai aproape de sursa lor
- Nu înghiți excepțiile fără a le gestiona
- Utilizează excepții verificate (checked) pentru condiții recuperabile
- Utilizează excepții neverificate (unchecked) pentru erori de programare
- Includeți informații relevante în mesajele de excepție
- Creează ierarhii logice pentru excepțiile personalizate

### 13. Ce înseamnă immutability și de ce este importantă în dezvoltarea software?
**Răspuns:** Immutability (imutabilitatea) reprezintă conceptul conform căruia, odată creat, un obiect nu își poate modifica starea. Pentru a "schimba" un obiect imutabil, se creează de fapt un nou obiect.

**Caracteristici ale obiectelor imutabile:**
- După creare, starea nu poate fi modificată
- Toate câmpurile sunt finale (final în Java)
- Clasa însăși poate fi declarată finală pentru a preveni moștenirea
- Orice câmp mutabil trebuie gestionat pentru a preveni modificările (defensive copying)

**Exemplu în Java:**
```java
public final class ImmutablePerson {
    private final String name;
    private final int age;
    private final List<String> hobbies;  // Colecție potențial mutabilă
    
    public ImmutablePerson(String name, int age, List<String> hobbies) {
        this.name = name;
        this.age = age;
        // Defensive copy pentru a preveni modificarea externă
        this.hobbies = Collections.unmodifiableList(new ArrayList<>(hobbies));
    }
    
    public String getName() {
        return name;
    }
    
    public int getAge() {
        return age;
    }
    
    public List<String> getHobbies() {
        return hobbies;  // Deja imutabilă prin unmodifiableList
    }
    
    // Pentru a "modifica", returnăm un nou obiect
    public ImmutablePerson withAge(int newAge) {
        return new ImmutablePerson(this.name, newAge, this.hobbies);
    }
}
```

**De ce este importantă imutabilitatea:**
1. **Thread safety:** Obiectele imutabile sunt implicit thread-safe, eliminând necesitatea sincronizării
2. **Predictibilitate:** Starea nu se schimbă, ceea ce face codul mai ușor de înțeles
3. **Cachability:** Obiectele imutabile pot fi în siguranță cache-uite sau refolosite
4. **Securitate:** Obiectele pasate nu pot fi modificate de cod malițios
5. **Reduce efectele secundare:** Facilitează programarea funcțională și raționamentul despre cod

**Exemple de clase imutabile în bibliotecile standard:**
- String în Java
- Primitive wrapper classes (Integer, Boolean, etc.)
- BigInteger și BigDecimal
- LocalDate, LocalTime în Java 8+

### 14. Ce sunt clasele interne (inner classes) și când ar trebui folosite?
**Răspuns:** Clasele interne sunt clase definite în interiorul altei clase (numită clasă exterioară). Ele pot accesa membrii privați ai clasei exterioare și sunt folosite pentru a grupa clase care sunt logic legate.

**Tipuri de clase interne:**

1. **Clase interne normale (non-statice):**
   - Au acces la toți membrii clasei exterioare, inclusiv cei privați
   - O instanță a clasei interne este implicit asociată cu o instanță a clasei exterioare

```java
class Outer {
    private int x = 10;
    
    class Inner {
        void display() {
            System.out.println("x from outer class: " + x);  // Accesează membrul privat
        }
    }
    
    void createInner() {
        Inner inner = new Inner();
        inner.display();
    }
}

// Utilizare din exterior
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
```

2. **Clase interne statice:**
   - Nu necesită o instanță a clasei exterioare
   - Pot accesa doar membrii statici ai clasei exterioare

```java
class Outer {
    private static int x = 10;
    
    static class StaticInner {
        void display() {
            System.out.println("static x from outer class: " + x);
        }
    }
}

// Utilizare
Outer.StaticInner inner = new Outer.StaticInner();
```

3. **Clase locale:** Definite în interiorul unei metode

```java
class Outer {
    void method() {
        class LocalInner {
            void display() {
                System.out.println("Local inner class");
            }
        }
        
        LocalInner inner = new LocalInner();
        inner.display();
    }
}
```

4. **Clase anonime:** Clase fără nume, definite și instanțiate într-o singură expresie

```java
interface Clickable {
    void onClick();
}

class Button {
    void setClickListener(Clickable listener) {
        // ...
    }
}

// Utilizare
Button button = new Button();
button.setClickListener(new Clickable() {
    @Override
    public void onClick() {
        System.out.println("Button clicked");
    }
});
```

**Când să folosești clasele interne:**
- Pentru a încapsula logica auxiliară în contextul unei clase principale
- Pentru a ascunde implementarea
- Când o clasă este relevantă doar în contextul altei clase
- Pentru a implementa callback-uri sau listeneri (clasele anonime)
- Pentru definirea adaptorilor sau a claselor helper

### 15. Ce este SOLID și cum ajută la scrierea unui cod mai bun?
**Răspuns:** SOLID este un acronim pentru cinci principii de design în programarea orientată pe obiecte, introduse de Robert C. Martin (Uncle Bob), care ajută la crearea unui software mai ușor de înțeles, testat, extins și întreținut.

**Principiile SOLID:**

1. **S - Single Responsibility Principle (SRP):**
   - O clasă ar trebui să aibă un singur motiv pentru a se schimba (o singură responsabilitate)
   - Exemplu: Separă logica de business de cea de persistență a datelor

```java
// Rău
class User {
    void saveToDatabase() { ... }
    void generateReport() { ... }
}

// Bine
class User { ... }
class UserRepository {
    void save(User user) { ... }
}
class UserReportGenerator {
    void generateReport(User user) { ... }
}
```

2. **O - Open/Closed Principle (OCP):**
   - Clasele ar trebui să fie deschise pentru extindere, dar închise pentru modificare
   - Extinde funcționalitatea prin adăugarea de cod nou, nu prin modificarea codului existent

```java
// Rău
class Rectangle {
    double width, height;
}

class AreaCalculator {
    double calculateArea(Object shape) {
        if (shape instanceof Rectangle) {
            Rectangle rect = (Rectangle) shape;
            return rect.width * rect.height;
        } 
        else if (shape instanceof Circle) {
            Circle circle = (Circle) shape;
            return Math.PI * circle.radius * circle.radius;
        }
        // Trebuie modificat codul pentru fiecare formă nouă
    }
}

// Bine
interface Shape {
    double calculateArea();
}

class Rectangle implements Shape {
    double width, height;
    
    @Override
    public double calculateArea() {
        return width * height;
    }
}

class Circle implements Shape {
    double radius;
    
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// AreaCalculator nu trebuie modificat pentru forme noi
class AreaCalculator {
    double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}
```

3. **L - Liskov Substitution Principle (LSP):**
   - Obiectele unei clase derivate trebuie să poată înlocui obiectele clasei de bază fără a afecta corectitudinea programului
   - Subclasele nu ar trebui să schimbe comportamentul de bază

```java
// Violarea LSP
class Rectangle {
    protected int width, height;
    
    public void setWidth(int width) {
        this.width = width;
    }
    
    public void setHeight(int height) {
        this.height = height;
    }
    
    public int getArea() {
        return width * height;
    }
}

class Square extends Rectangle {
    @Override
    public void setWidth(int width) {
        super.setWidth(width);
        super.setHeight(width);  // Modifică comportamentul clasei de bază
    }
    
    @Override
    public void setHeight(int height) {
        super.setHeight(height);
        super.setWidth(height);  // Modifică comportamentul clasei de bază
    }
}
```

4. **I - Interface Segregation Principle (ISP):**
   - Multe interfețe specifice sunt mai bune decât o interfață generală
   - Clientul nu ar trebui forțat să depindă de metode pe care nu le folosește

```java
// Rău
interface Worker {
    void work();
    void eat();
    void sleep();
}

// Bine
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

interface Sleepable {
    void sleep();
}

class Human implements Workable, Eatable, Sleepable {
    @Override
    public void work() { ... }
    
    @Override
    public void eat() { ... }
    
    @Override
    public void sleep() { ... }
}

class Robot implements Workable {
    @Override
    public void work() { ... }
    // Nu e forțat să implementeze eat() și sleep()
}
```

5. **D - Dependency Inversion Principle (DIP):**
   - Modulele de nivel înalt nu ar trebui să depindă de modulele de nivel jos; ambele ar trebui să depindă de abstracții
   - Abstracțiile nu ar trebui să depindă de detalii; detaliile ar trebui să depindă de abstracții

```java
// Rău
class EmailSender {
    void sendEmail(String message) { ... }
}

class NotificationService {
    private EmailSender emailSender = new EmailSender();
    
    void sendNotification(String message) {
        emailSender.sendEmail(message);
    }
}

// Bine
interface MessageSender {
    void sendMessage(String message);
}

class EmailSender implements MessageSender {
    @Override
    public void sendMessage(String message) { ... }
}

class SMSSender implements MessageSender {
    @Override
    public void sendMessage(String message) { ... }
}

class NotificationService {
    private MessageSender messageSender;
    
    // Dependency Injection
    public NotificationService(MessageSender messageSender) {
        this.messageSender = messageSender;
    }
    
    void sendNotification(String message) {
        messageSender.sendMessage(message);
    }
}
```

**Beneficiile aplicării principiilor SOLID:**
- Cod mai ușor de înțeles și de întreținut
- Cod mai flexibil și adaptabil la schimbări
- Testabilitate îmbunătățită
- Reutilizabilitate mai mare
- Reducerea bug-urilor și a efectelor secundare nedorite

## Baze de Date

### 16. Ce este o bază de date relațională și care sunt principalele caracteristici?
**Răspuns:** O bază de date relațională este un tip de bază de date care stochează și organizează datele în tabele (sau relații) cu rânduri și coloane, stabilind relații între aceste tabele prin chei.

**Caracteristici principale:**

1. **Model bazat pe tabele:** Datele sunt organizate în tabele bidimensionale cu rânduri (înregistrări) și coloane (atribute)

2. **Schema predefinită:** Structura tabelelor, tipurile de date și relațiile sunt definite înainte de introducerea datelor

3. **Relații între date:** Datele din tabele diferite pot fi legate printr-un sistem de chei primare și străine

4. **Integritatea datelor:** Reguli de integritate asigură validitatea datelor și relațiilor dintre ele:
   - **Integritate de entitate:** Fiecare înregistrare trebuie să fie unic identificabilă (cheie primară)
   - **Integritate referențială:** Cheile străine trebuie să facă referire la chei primare valide sau să fie nule
   - **Integritate de domeniu:** Valorile trebuie să respecte tipul de date și constrângerile definite

5. **ACID:** Proprietăți care garantează fiabilitatea tranzacțiilor:
   - **Atomicitate:** Tranzacțiile sunt "totul sau nimic"
   - **Consistență:** Doar datele valide sunt salvate
   - **Izolare:** Tranzacțiile nu interferează între ele
   - **Durabilitate:** Odată ce o tranzacție este salvată, rămâne persistentă

6. **Limbaj standardizat (SQL):** Folosit pentru interogarea și manipularea datelor

7. **Normalizare:** Proces de organizare a datelor pentru a reduce redundanța și a îmbunătăți integritatea

8. **Indexare:** Mecanisme pentru optimizarea interogărilor și îmbunătățirea performanței

**Exemple de sisteme de baze de date relaționale:**
- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite

### 17. Explică diferența dintre bazele de date SQL și NoSQL.
**Răspuns:** Bazele de date SQL (relaționale) și NoSQL (non-relaționale) sunt două categorii majore de sisteme de gestionare a bazelor de date, fiecare cu propriile caracteristici și cazuri de utilizare.

**Baze de date SQL:**
- **Structură:** Schema predefinită, organizare tabelară (rânduri și coloane)
- **Scalabilitate:** Mai ales verticală (hardware mai puternic)
- **Relații:** Suport nativ pentru relații complexe între tabele
- **ACID:** Aderență completă la proprietățile ACID
- **Standardizare:** Limbaj standard (SQL) pentru interogări
- **Use-cases:** Aplicații care necesită integritate a datelor, tranzacții complexe (sisteme bancare, ERP)
- **Exemple:** MySQL, PostgreSQL, Oracle, SQL Server

**Baze de date NoSQL:**
- **Structură:** Schema flexibilă sau fără schemă, diverse modele de date
- **Scalabilitate:** Mai ales orizontală (mai multe servere/noduri)
- **Relații:** Relații gestionate în aplicație sau relații simple
- **ACID:** De obicei sacrifică unele proprietăți ACID pentru performanță și scalabilitate (deși unele oferă acum tranzacții ACID)
- **Standardizare:** Fără limbaj standard, fiecare sistem are propria interfață
- **Use-cases:** Big data, timp real, conținut distribuit, IoT, aplicații mobile
- **Tipuri și exemple:**
  - **Document:** MongoDB, CouchDB (stochează documentele ca JSON)
  - **Key-Value:** Redis, DynamoDB (simple perechi cheie-valoare)
  - **Column-family:** Cassandra, HBase (optimizate pentru citiri/scrieri rapide de coloane)
  - **Graph:** Neo4j, Amazon Neptune (optimizate pentru relații complexe)

**Comparație pe caracteristici specifice:**

| Caracteristică | SQL | NoSQL |
|----------------|-----|-------|
| Schema | Rigidă, predefinită | Flexibilă, poate evolua |
| Scalabilitate | Verticală | Orizontală |
| Complexitate interogări | Interogări complexe prin JOIN-uri | Interogări simple, fără JOIN-uri sau JOIN-uri limitate |
| Consistență | Consistență puternică | Deseori "eventual consistency" |
| Performanță | Poate fi limitată de relații | Optimizată pentru operațiuni specifice |
| Maturitate | Tehnologie matură | Relativ mai nouă, evoluează rapid |

**Când să alegi fiecare tip:**
- **SQL:** Când ai nevoie de integritate strictă a datelor, relații complexe, tranzacții ACID, raportare avansată
- **NoSQL:** Când ai nevoie de scalabilitate masivă, scheme flexibile, performanță ridicată pentru anumite tipuri de acces la date, date distribuite geografic

### 18. Ce sunt cheile primare și cheile străine într-o bază de date relațională?
**Răspuns:**

**Cheia Primară (Primary Key):**
- Identifică în mod unic fiecare rând/înregistrare dintr-un tabel
- Nu poate conține valori NULL
- Trebuie să fie unică pentru fiecare înregistrare
- De obicei, este indexată pentru performanță mai bună la căutări
- Poate fi:
  - **Naturală:** Folosind un atribut existent care este unic (ex. CNP, ISBN)
  - **Artificială/Surogat:** Valoare generată (ex. ID auto-increment)
  - **Compusă:** Combinație de două sau mai multe coloane

Exemplu SQL:
```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,  -- Cheie primară simplă
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE
);

-- SAU cheie primară compusă
CREATE TABLE Enrollments (
    course_id INT,
    student_id INT,
    semester VARCHAR(20),
    grade FLOAT,
    PRIMARY KEY (course_id, student_id, semester)
);
```

**Cheia Străină (Foreign Key):**
- Creează o legătură între date din două tabele
- Face referire la cheia primară din alt tabel (tabelul părinte)
- Asigură integritatea referențială a datelor
- Poate fi NULL (dacă nu are constraint NOT NULL)
- Poate avea reguli pentru CASCADE, SET NULL, etc.

Exemplu SQL:
```sql
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100),
    department VARCHAR(50)
);

CREATE TABLE Enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    enrollment_date DATE,
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
```

**Relații posibile folosind chei primare și străine:**
1. **One-to-One:** O înregistrare din tabelul A este asociată cu exact o înregistrare din tabelul B
2. **One-to-Many:** O înregistrare din tabelul A poate fi asociată cu mai multe înregistrări din tabelul B
3. **Many-to-Many:** Implementată prin tabel de joncțiune cu chei străine către ambele tabele

**Acțiuni ON DELETE/UPDATE:**
- **CASCADE:** Șterge/actualizează automat înregistrările asociate
- **SET NULL:** Setează cheia străină la NULL
- **SET DEFAULT:** Setează cheia străină la o valoare implicită
- **RESTRICT/NO ACTION:** Previne ștergerea/actualizarea dacă există înregistrări asociate

```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) 
    REFERENCES Customers(customer_id)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```

### 19. Ce este normalizarea bazelor de date și care sunt formele normale principale?
**Răspuns:** Normalizarea este procesul de organizare a datelor într-o bază de date pentru a reduce redundanța și a îmbunătăți integritatea datelor. Aceasta implică împărțirea tabelelor mari în tabele mai mici și mai specializate și definirea relațiilor între acestea.

**Obiectivele normalizării:**
- Eliminarea redundanței datelor
- Minimizarea anomaliilor de actualizare, inserare și ștergere
- Îmbunătățirea integrității datelor
- Simplificarea interogărilor

**Forme normale principale:**

1. **Prima Formă Normală (1NF):**
   - Fiecare tabel are o cheie primară
   - Fiecare coloană conține valori atomice (indivizibile)
   - Nu există grupuri repetitive sau coloane multi-valoare
   - Fiecare rând/coloană intersecție conține exact o valoare

Exemplu - Tabel care nu respectă 1NF:
```
| Student_ID | Courses            |
|------------|-------------------|
| 1          | Math, Physics     |
| 2          | Chemistry, Biology|
```

Tabel normalizat (1NF):
```
| Student_ID | Course    |
|------------|-----------|
| 1          | Math      |
| 1          | Physics   |
| 2          | Chemistry |
| 2          | Biology   |
```

2. **A Doua Formă Normală (2NF):**
   - Trebuie să fie în 1NF
   - Toate atributele non-cheie depind complet de întreaga cheie primară
   - Elimină dependențele parțiale (relevantă doar pentru chei primare compuse)

Exemplu - Tabel care nu respectă 2NF:
```
| Student_ID | Course_ID | Course_Name | Student_Name |
|------------|-----------|-------------|--------------|
| 1          | C1        | Math        | John         |
| 1          | C2        | Physics     | John         |
| 2          | C2        | Physics     | Jane         |
```

Tabele normalizate (2NF):
```
| Student_ID | Student_Name |
|------------|--------------|
| 1          | John         |
| 2          | Jane         |

| Student_ID | Course_ID |
|------------|-----------|
| 1          | C1        |
| 1          | C2        |
| 2          | C2        |

| Course_ID | Course_Name |
|-----------|-------------|
| C1        | Math        |
| C2        | Physics     |
```

3. **A Treia Formă Normală (3NF):**
   - Trebuie să fie în 2NF
   - Toate atributele non-cheie depind direct de cheia primară și sunt independente între ele
   - Elimină dependențele tranzitive (A→B și B→C, deci A→C)

Exemplu - Tabel care nu respectă 3NF:
```
| Student_ID | Department_ID | Department_Name | Department_Head |
|------------|---------------|----------------|-----------------|
| 1          | D1            | Computer Science| Dr. Smith       |
| 2          | D1            | Computer Science| Dr. Smith       |
| 3          | D2            | Physics        | Dr. Johnson     |
```

Tabele normalizate (3NF):
```
| Student_ID | Department_ID |
|------------|---------------|
| 1          | D1            |
| 2          | D1            |
| 3          | D2            |

| Department_ID | Department_Name  | Department_Head |
|---------------|-----------------|-----------------|
| D1            | Computer Science| Dr. Smith       |
| D2            | Physics         | Dr. Johnson     |
```

4. **Forma Normală Boyce-Codd (BCNF):**
   - O formă mai strictă a 3NF
   - Pentru orice dependență funcțională X→Y, X trebuie să fie o superchei
   - Rezolvă anumite anomalii rare care pot apărea în 3NF

5. **A Patra Formă Normală (4NF):**
   - Trebuie să fie în BCNF
   - Nu conține dependențe multi-valoare

6. **A Cincea Formă Normală (5NF):**
   - Elimină anomaliile rămase în dependențele de joncțiune

**Dezavantaje ale normalizării excesive:**
- Poate complica interogările care necesită date din multiple tabele
- Poate reduce performanța pentru anumite tipuri de interogări
- Implementarea și menținerea relațiilor pot fi complexe

**Denormalizare controlată:**
- Uneori se folosește intenționat redundanța pentru a îmbunătăți performanța
- Comună în aplicații de tip data warehouse sau sisteme analitice

### 20. Explică conceptul de JOIN în SQL și tipurile de JOIN.
**Răspuns:** JOIN în SQL este o operație care permite combinarea rândurilor din două sau mai multe tabele bazate pe o coloană comună sau o condiție de legătură. Este folosit pentru a recupera date din multiple tabele într-o singură interogare.

**Tipuri principale de JOIN:**

1. **INNER JOIN:**
   - Returnează rândurile când există o potrivire în ambele tabele
   - Exclude rândurile care nu au corespondent în cealaltă tabelă
   
```sql
SELECT Orders.order_id, Customers.customer_name
FROM Orders
INNER JOIN Customers
ON Orders.customer_id = Customers.customer_id;
```

2. **LEFT JOIN (sau LEFT OUTER JOIN):**
   - Returnează toate rândurile din tabela din stânga
   - Pentru rândurile fără potrivire în tabela din dreapta, se folosesc valori NULL
   
```sql
SELECT Customers.customer_name, Orders.order_id
FROM Customers
LEFT JOIN Orders
ON Customers.customer_id = Orders.customer_id;
-- Returnează toți clienții, chiar și cei fără comenzi
```

3. **RIGHT JOIN (sau RIGHT OUTER JOIN):**
   - Returnează toate rândurile din tabela din dreapta
   - Pentru rândurile fără potrivire în tabela din stânga, se folosesc valori NULL
   
```sql
SELECT Orders.order_id, Customers.customer_name
FROM Orders
RIGHT JOIN Customers
ON Orders.customer_id = Customers.customer_id;
-- Efect similar cu LEFT JOIN dar cu ordinea tabelelor inversată
```

4. **FULL JOIN (sau FULL OUTER JOIN):**
   - Returnează rânduri când există o potrivire în oricare dintre tabele
   - Combină efectele LEFT JOIN și RIGHT JOIN
   
```sql
SELECT Customers.customer_name, Orders.order_id
FROM Customers
FULL JOIN Orders
ON Customers.customer_id = Orders.customer_id;
-- Returnează toți clienții și toate comenzile
```

5. **CROSS JOIN:**
   - Returnează produsul cartezian al celor două tabele
   - Fiecare rând din prima tabelă este combinat cu fiecare rând din a doua tabelă
   - Nu necesită condiție de JOIN
   
```sql
SELECT Customers.customer_name, Products.product_name
FROM Customers
CROSS JOIN Products;
-- Combinație a fiecărui client cu fiecare produs
```

6. **SELF JOIN:**
   - JOIN al unei tabele cu ea însăși
   - Util pentru găsirea relațiilor între rânduri în aceeași tabelă
   
```sql
SELECT e1.employee_name as Employee, e2.employee_name as Manager
FROM Employees e1
INNER JOIN Employees e2
ON e1.manager_id = e2.employee_id;
-- Afișează angajații și managerii lor
```

**Diagrama Venn pentru tipurile de JOIN:**
- INNER JOIN: intersecția celor două cercuri
- LEFT JOIN: tot cercul stâng plus intersecția
- RIGHT JOIN: tot cercul drept plus intersecția
- FULL JOIN: ambele cercuri complet (uniunea)

**Sintaxe alternative:**
- Sintaxa veche cu virgulă și WHERE:
```sql
-- Similar cu INNER JOIN
SELECT Orders.order_id, Customers.customer_name
FROM Orders, Customers
WHERE Orders.customer_id = Customers.customer_id;
```

**Performance considerations:**
- JOIN-urile necesită resurse, în special pentru tabele mari
- Indexarea coloanelor de JOIN îmbunătățește performanța
- JOINs multiple trebuie optimizate pentru a evita produse carteziene nedorite

### 21. Ce sunt indecșii într-o bază de date și cum îmbunătățesc performanța?
**Răspuns:** Indecșii sunt structuri de date speciale care îmbunătățesc viteza operațiunilor de căutare într-o bază de date prin organizarea datelor pentru acces rapid. Ei funcționează similar cu indexul unei cărți, permițând găsirea rapidă a informațiilor fără a scana întreaga tabelă.

**Cum funcționează indecșii:**
- Sunt stocați separat de datele propriu-zise
- Conțin referințe (pointeri) către datele reale
- Organizează valorile într-o structură optimizată pentru căutare (de obicei B-tree sau variante)
- Sistemul de gestiune a bazei de date îi menține automat la actualizarea datelor

**Tipuri de indecși:**

1. **Index Primar:**
   - Creat automat pentru cheia primară
   - Unic, nu permite valori NULL
   - Determină ordinea fizică a datelor (în multe DBMS-uri)

2. **Index Unic:**
   - Asigură că valorile din coloana indexată sunt unice
   - Similar cu indexul primar, dar poate fi aplicat pe coloane care nu sunt chei primare
   - Poate permite o singură valoare NULL în unele DBMS-uri

```sql
CREATE UNIQUE INDEX idx_email ON users(email);
```

3. **Index Non-Unic:**
   - Permite valori duplicate
   - Folosit pentru coloane frecvent folosite în căutări

```sql
CREATE INDEX idx_last_name ON users(last_name);
```

4. **Index Compus:**
   - Construit pe multiple coloane
   - Ordinea coloanelor este importantă pentru eficiență

```sql
CREATE INDEX idx_name ON users(last_name, first_name);
```

5. **Index Parțial/Filtrat:**
   - Acoperă doar o subsetă a rândurilor bazată pe o condiție
   - Reduce dimensiunea indexului și îmbunătățește performanța

```sql
CREATE INDEX idx_active_users ON users(last_login) WHERE status = 'active';
```

6. **Index Full-Text:**
   - Optimizat pentru căutări text
   - Suportă căutări complexe (stemming, stop words, etc.)

```sql
CREATE FULLTEXT INDEX idx_content ON articles(title, content);
```

7. **Index Spatial:**
   - Pentru date geografice/spațiale
   - Optimizat pentru interogări bazate pe locație

**Cum îmbunătățesc performanța:**

1. **Căutări rapide:**
   - Reduce nevoia de a scana toate rândurile (table scan)
   - Transformă complexitatea de timp din O(n) în O(log n) pentru multe operații

2. **Optimizarea JOIN-urilor:**
   - Accelerează operațiile de JOIN prin accesul rapid la rândurile de legătură

3. **Îmbunătățirea sortării:**
   - Poate elimina necesitatea unei sortări explicite pentru clauzele ORDER BY

4. **Aplicarea constrângerilor de unicitate:**
   - Verifică rapid dacă o valoare există deja

5. **Optimizarea interogărilor agregat:**
   - Poate accelera funcții precum MIN(), MAX()

**Dezavantaje și considerații:**

1. **Spațiu de stocare:**
   - Indecșii ocupă spațiu suplimentar pe disc

2. **Overhead pentru scriere:**
   - INSERT, UPDATE, DELETE devin mai lente pentru că indecșii trebuie actualizați

3. **Mentenanță:**
   - Necesită reconstruire sau reindexare periodică pentru anumite operațiuni

4. **Selecție adecvată:**
   - Indecșii nefolosiți consumă resurse fără beneficii
   - Prea mulți indecși pot încetini operațiunile de scriere

**Când să folosești indecși:**
- Pe coloane folosite frecvent în clauze WHERE
- Pe coloane folosite în JOIN-uri
- Pe coloane folosite în ORDER BY sau GROUP BY
- Pe coloane cu cardinalitate medie spre mare (multe valori distincte)

**Când să eviți indecșii:**
- Pe tabele foarte mici
- Pe coloane actualizate frecvent
- Pe coloane cu cardinalitate mică (puține valori distincte)
- Pe coloane rar folosite în căutări

### 22. Ce este o tranzacție în baze de date și care sunt proprietățile ACID?
**Răspuns:** O tranzacție într-o bază de date este o unitate logică de lucru care conține una sau mai multe operațiuni (SELECT, INSERT, UPDATE, DELETE) și care trebuie să fie executată complet sau deloc. Tranzacțiile asigură integritatea și consistența datelor, în special în medii concurente sau în caz de erori.

**Proprietățile ACID:**

ACID este un acronim care reprezintă cele patru proprietăți esențiale pe care tranzacțiile trebuie să le garanteze:

1. **Atomicitate (Atomicity):**
   - O tranzacție trebuie să fie tratată ca o unitate indivizibilă de lucru
   - Fie toate operațiunile din tranzacție sunt executate cu succes, fie nicio operațiune nu este executată (principiul "totul sau nimic")
   - Dacă orice parte a tranzacției eșuează, întreaga tranzacție este anulată (rollback)

Exemplu:
```sql
BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 1000 WHERE account_id = 123;
    UPDATE accounts SET balance = balance + 1000 WHERE account_id = 456;
    -- Dacă a doua operație eșuează, prima este de asemenea anulată
COMMIT;
```

2. **Consistență (Consistency):**
   - O tranzacție trebuie să transforme baza de date dintr-o stare validă în altă stare validă
   - Toate regulile de integritate, constrângerile, cascadele și declanșatorii trebuie respectate
   - Datele trebuie să respecte toate regulile definite

Exemplu: Într-un transfer bancar, suma totală de bani în sistem trebuie să rămână aceeași înainte și după tranzacție.

3. **Izolare (Isolation):**
   - Tranzacțiile concurente nu trebuie să afecteze reciproc rezultatele
   - Rezultatul tranzacțiilor concurente trebuie să fie același ca și cum tranzacțiile ar fi fost executate secvențial
   - Nivelurile de izolare controlează cât de strict este aplicată această proprietate

Niveluri comune de izolare:
- **READ UNCOMMITTED:** Permite citirea datelor modificate dar nevalidate (dirty reads)
- **READ COMMITTED:** Previne citirile murdare, dar permite citirile fantomă și nerepetabile
- **REPEATABLE READ:** Previne citirile murdare și nerepetabile, dar permite citirile fantomă
- **SERIALIZABLE:** Cel mai restrictiv nivel, previne toate problemele de concurență

```sql
BEGIN TRANSACTION ISOLATION LEVEL SERIALIZABLE;
    -- operații
COMMIT;
```

4. **Durabilitate (Durability):**
   - Odată ce o tranzacție este validată (commit), modificările sale devin permanente
   - Modificările supraviețuiesc chiar și în cazul unei căderi de sistem sau pene de curent
   - De obicei, implementată prin jurnalizare (write-ahead logging)

**Implementarea tranzacțiilor:**

În majoritatea sistemelor SQL:
```sql
BEGIN TRANSACTION;
    -- operații de modificare a datelor
    -- (pot fi multe instrucțiuni)
COMMIT;  -- Pentru a finaliza cu succes
-- sau
ROLLBACK;  -- Pentru a anula toate modificările
```

**Puncte de salvare (savepoints):**
```sql
BEGIN TRANSACTION;
    -- operații
    SAVEPOINT point1;
    -- mai multe operații
    ROLLBACK TO SAVEPOINT point1;  -- Anulează doar operațiile după savepoint
    -- mai multe operații
COMMIT;
```

**Probleme de concurență:**
1. **Lost Update:** Două tranzacții modifică aceeași dată, a doua suprascrie prima
2. **Dirty Read:** O tranzacție citește date modificate de altă tranzacție nevalidată
3. **Non-repeatable Read:** În cadrul aceleiași tranzacții, citiri repetate returnează rezultate diferite
4. **Phantom Read:** O tranzacție regăsește rânduri noi care satisfac o condiție, adăugate de altă tranzacție

**Control concurență:**
- **Locking:** Exclusiv (write) și partajat (read)
- **Versioning:** Multi-Version Concurrency Control (MVCC)
- **Timestamp Ordering:** Bazat pe timpul tranzacției

### 23. Cum optimizezi o interogare SQL care rulează lent?
**Răspuns:** Optimizarea interogărilor SQL este un proces metodic care implică identificarea și rezolvarea problemelor de performanță. Iată abordarea pas cu pas:

**1. Analiza interogării:**

- **Folosirea EXPLAIN (sau EXPLAIN PLAN):**
  - Oferă detalii despre planul de execuție al interogării
  - Indică operațiile costisitoare (full table scans, temp tables)
  
  ```sql
  EXPLAIN SELECT * FROM orders JOIN customers ON orders.customer_id = customers.id WHERE orders.amount > 1000;
  ```

- **Instrumentație și profiling:**
  - Măsoară timpul exact necesar fiecărei părți a interogării
  - Multe DBMS-uri oferă unelte de profiling
  
  ```sql
  -- MySQL
  SET profiling = 1;
  -- Rulează interogarea
  SHOW PROFILE;
  ```

**2. Optimizarea prin indecși:**

- **Adăugarea indecșilor potriviți:**
  - Crearea indecșilor pe coloanele din clauza WHERE, JOIN, ORDER BY, GROUP BY
  
  ```sql
  CREATE INDEX idx_orders_amount ON orders(amount);
  CREATE INDEX idx_orders_customer ON orders(customer_id);
  ```

- **Verificarea utilizării indecșilor:**
  - Asigură-te că interogarea folosește indecșii disponibili
  - Utilizarea FORCE INDEX pentru a sugera un anumit index

- **Indecși compuși:**
  - Creează indecși pe multiple coloane pentru interogări complexe
  - Ordinea coloanelor în index este importantă
  
  ```sql
  CREATE INDEX idx_orders_customer_date ON orders(customer_id, order_date);
  ```

**3. Optimizarea interogării:**

- **Selectează doar coloanele necesare:**
  - Evită `SELECT *` când ai nevoie doar de anumite coloane
  
  ```sql
  -- Rău
  SELECT * FROM products;
  
  -- Bine
  SELECT product_id, name, price FROM products;
  ```

- **Limitarea rezultatelor:**
  - Folosește LIMIT/TOP pentru a returna doar câte rezultate ai nevoie
  
  ```sql
  SELECT * FROM logs ORDER BY created_at DESC LIMIT 100;
  ```

- **Filtrare eficientă:**
  - Plasează condițiile cele mai restrictive primele
  - Folosește operatori eficienți (= este mai rapid decât LIKE)
  
  ```sql
  -- Mai puțin eficient
  SELECT * FROM customers 
  WHERE YEAR(registration_date) = 2023 AND status = 'active';
  
  -- Mai eficient (poate folosi index pe status)
  SELECT * FROM customers 
  WHERE status = 'active' AND YEAR(registration_date) = 2023;
  ```

- **Evitarea funcțiilor pe coloanele indexate:**
  - Funcțiile aplicate pe coloane pot împiedica utilizarea indecșilor
  
  ```sql
  -- Nu poate folosi index pe registration_date
  SELECT * FROM customers WHERE YEAR(registration_date) = 2023;
  
  -- Poate folosi index
  SELECT * FROM customers 
  WHERE registration_date BETWEEN '2023-01-01' AND '2023-12-31';
  ```

**4. Optimizarea JOIN-urilor:**

- **Ordinea JOIN-urilor:**
  - Începe cu tabelele care filtrează cele mai multe rânduri
  
- **Tipul potrivit de JOIN:**
  - Folosește INNER JOIN în loc de LEFT JOIN când e posibil
  
- **Denormalizare strategică:**
  - În unele cazuri, stocarea datelor redundante poate îmbunătăți performanța
  
- **Reducerea numărului de JOIN-uri:**
  - Folosește subconsultări sau view-uri când e adecvat

**5. Strategii avansate:**

- **Partitionarea tabelelor:**
  - Împărțirea tabelelor mari în secțiuni logice mai mici
  
  ```sql
  CREATE TABLE sales (
      id INT,
      sale_date DATE,
      amount DECIMAL(10,2)
  ) PARTITION BY RANGE (YEAR(sale_date)) (
      PARTITION p0 VALUES LESS THAN (2020),
      PARTITION p1 VALUES LESS THAN (2021),
      PARTITION p2 VALUES LESS THAN (2022),
      PARTITION p3 VALUES LESS THAN MAXVALUE
  );
  ```

- **Optimizarea subconsultărilor:**
  - Transformarea unor subconsultări în JOIN-uri
  - Evitarea subconsultărilor corelate când este posibil
  
- **Materializarea rezultatelor intermediare:**
  - Folosirea tabelelor temporare pentru rezultate intermediare în interogări complexe
  
  ```sql
  CREATE TEMPORARY TABLE temp_results AS
  SELECT customer_id, SUM(amount) AS total
  FROM orders
  GROUP BY customer_id;
  
  -- Apoi folosești temp_results
  ```

- **Eliminarea DISTINCT nenecesar:**
  - DISTINCT este costisitor; folosește-l doar când e necesar
  
- **Optimizarea GROUP BY:**