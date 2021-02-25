# <center> Algorithm Implementation </center>

## <center> Sorting Algorithms </center>

###  <center> Insertion (Вставками) </center>
* 1 - explanation: 
<p align="justify">
Although it is one of the elementary sorting algorithms with O(n2) worst-case time, insertion sort is the algorithm of choice either when the data is nearly sorted (because it is adaptive) or when the problem size is small (because it has low overhead).

For these reasons, and because it is also stable, insertion sort is often used as the recursive base case (when the problem size is small) for higher overhead divide-and-conquer sorting algorithms, such as merge sort or quick sort.
</p>

* 2 - explanation: 

<p align="justify">
Although it is one of the elementary sorting algorithms with O(n2) worst-case time, insertion sort is the algorithm of choice either when the data is nearly sorted (because it is adaptive) or when the problem size is small (because it has low overhead).

For these reasons, and because it is also stable, insertion sort is often used as the recursive base case (when the problem size is small) for higher overhead divide-and-conquer sorting algorithms, such as merge sort or quick sort.
</p>


-- Pseudocode --
```
arr[] = 64 25 12 22 11

// Find the minimum element in arr[0...4]
// and place it at beginning
11 25 12 22 64

// Find the minimum element in arr[1...4]
// and place it at beginning of arr[1...4]
11 12 25 22 64

// Find the minimum element in arr[2...4]
// and place it at beginning of arr[2...4]
11 12 22 25 64

// Find the minimum element in arr[3...4]
// and place it at beginning of arr[3...4]
11 12 22 25 64 

```

-- Pseudocode --
```
for i = 2:n,
    for (k = i; k > 1 and a[k] < a[k-1]; k--)
        swap a[k,k-1]
    → invariant: a[1..i] is sorted
end

```

-- Pseudocode --
```
insert :: Ord a ? a ? [a] ? [a]
insert x [] = [x]
insert x (y : ys)
  | x ? y = x : y : ys
  | otherwise = y : insert x ys
 
isort :: Ord a ? [a] ? [a]
isort [ ] = [ ]
isort (x : xs) = insert x (isort xs)

```

-- C#  --
```C#
// C# program for implementation  
// of Selection Sort 
using System; 
  
class GFG 
{  
    static void sort(int []arr) 
    { 
        int n = arr.Length; 
  
        // One by one move boundary of unsorted subarray 
        for (int i = 0; i < n - 1; i++) 
        { 
            // Find the minimum element in unsorted array 
            int min_idx = i; 
            for (int j = i + 1; j < n; j++) 
                if (arr[j] < arr[min_idx]) 
                    min_idx = j; 
  
            // Swap the found minimum element with the first 
            // element 
            int temp = arr[min_idx]; 
            arr[min_idx] = arr[i]; 
            arr[i] = temp; 
        } 
    } 
  
    // Prints the array 
    static void printArray(int []arr) 
    { 
        int n = arr.Length; 
        for (int i=0; i<n; ++i) 
            Console.Write(arr[i]+" "); 
        Console.WriteLine(); 
    } 
  
    // Driver code  
    public static void Main() 
    { 
        int []arr = {64,25,12,22,11}; 
        sort(arr); 
        Console.WriteLine("Sorted array"); 
        printArray(arr); 
    } 
  
} 
// This code is contributed by Sam007 
```


###  <center> Selection (Выбором) </center>


### <center> Bubble (Пузырьком) </center>


### <center> Shell (Метод Шелла) </center>


### <center> Merge (Слиянием) </center>


###  <center> Heap (Куча) </center>


###  <center> Quick (Быстрая) </center>


###  <center> Quick3 (Быстрая3) </center>





## <center> Searching Algorithms </center>

###  <center> Linear Search (Линейный поиск) </center>

### <center> Binary Search (Бинарный поиск) </center>
