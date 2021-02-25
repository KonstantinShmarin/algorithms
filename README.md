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

![Insertion](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortinsert.gif)

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

//------------------------------------------
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
 //------------------------------------------
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

-- javascript --
```javascript
function insertionSort(arr) {
  let memIndex = 0
  for (let i = 0; i < arr.length; i++) {
    memIndex = i;
    for (let j = i + 1; j >= 0; --j) {
      if (arr[j] >= arr[i]) {
        break;
      }
      if (arr[j] < arr[i]) {
        var temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i = i - 1;
      }
    }
    i = memIndex;
  }
  return arr;
}
const arr = [5, 1, 6, 2, 4, 9, 9, 3, 1, 1, 1];
console.log('Unsorted array', arr);
console.log('Sorted array:', insertionSort(arr));

```

-- PHP --
```php
<?php 
// PHP program for implementation  
// of selection sort  
function selection_sort(&$arr, $n)  
{ 
    for($i = 0; $i < $n ; $i++) 
    { 
        $low = $i; 
        for($j = $i + 1; $j < $n ; $j++) 
        { 
            if ($arr[$j] < $arr[$low]) 
            { 
                $low = $j; 
            } 
        } 
          
        // swap the minimum value to $ith node 
        if ($arr[$i] > $arr[$low]) 
        { 
            $tmp = $arr[$i]; 
            $arr[$i] = $arr[$low]; 
            $arr[$low] = $tmp; 
        } 
    } 
} 
  
// Driver Code 
$arr = array(64, 25, 12, 22, 11); 
$len = count($arr); 
selection_sort($arr, $len); 
echo "Sorted array : \n";  
  
for ($i = 0; $i < $len; $i++)  
    echo $arr[$i] . " ";  
  
// This code is contributed  
// by Deepika Gupta.  
?>  

```

-- Python --
```Python
# Python program for implementation of Selection 
# Sort 
import sys 
A = [64, 25, 12, 22, 11] 
  
# Traverse through all array elements 
for i in range(len(A)): 
      
    # Find the minimum element in remaining  
    # unsorted array 
    min_idx = i 
    for j in range(i+1, len(A)): 
        if A[min_idx] > A[j]: 
            min_idx = j 
              
    # Swap the found minimum element with  
    # the first element         
    A[i], A[min_idx] = A[min_idx], A[i] 
  
# Driver code to test above 
print ("Sorted array") 
for i in range(len(A)): 
    print("%d" %A[i]),  

```

### <center> Bubble (Пузырьком) </center>

* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>

* 2 - explanation:
<p align="justify">

Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.
<b><p>Example:</p>
First Pass:</b>
( 5 1 4 2 8 ) –> ( 1 5 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1.
( 1 5 4 2 8 ) –>  ( 1 4 5 2 8 ), Swap since 5 > 4
( 1 4 5 2 8 ) –>  ( 1 4 2 5 8 ), Swap since 5 > 2
( 1 4 2 5 8 ) –> ( 1 4 2 5 8 ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.

<b>Second Pass:</b>
( 1 4 2 5 8 ) –> ( 1 4 2 5 8 )
( 1 4 2 5 8 ) –> ( 1 2 4 5 8 ), Swap since 4 > 2
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –>  ( 1 2 4 5 8 )
Now, the array is already sorted, but our algorithm does not know if it is completed. The algorithm needs one whole pass without any swap to know it is sorted.

<b>Third Pass:</b>
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )

</p>

![Bubble](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)

-- Pseudocode --
```
for i = 1:n,
    swapped = false
    for j = n:i+1,
        if a[j] < a[j-1],
            swap a[j,j-1]
            swapped = true
    → invariant: a[1..i] in final position
    break if not swapped
end

```

<b>Sorting In Place:</b> Yes

<b>Stable:</b> Yes
<p align="justify">
Due to its simplicity, bubble sort is often used to introduce the concept of a sorting algorithm.
In computer graphics it is popular for its capability to detect a very small error (like swap of just two elements) in almost-sorted arrays and fix it with just linear complexity (2n). For example, it is used in a polygon filling algorithm, where bounding lines are sorted by their x coordinate at a specific scan line (a line parallel to x axis) and with incrementing y their order changes (two elements are swapped) only at intersections of two lines (Source: Wikipedia)
</p>

-- Pseudocode --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Pseudocode --
```
mov bx, offset array
    mov cx, n
for_i:
    dec cx
    xor dx, dx
for_j:
    cmp dx, cx
    jae exit_for_j
    jbe no_swap
    mov ah, byte ptr bx[di]
    mov byte ptr bx[di], al
    mov byte ptr bx[si], ah
no_swap:
    inc dx
    jmp for_j
exit_for_j:
    loop    for_i

```

-- C# --
```C#
// C# program for implementation  
// of Bubble Sort 
using System; 
  
class GFG 
{  
//-----------------------------------------------
    static void bubbleSort(int []arr) 
    { 
        int n = arr.Length; 
        for (int i = 0; i < n - 1; i++) 
            for (int j = 0; j < n - i - 1; j++) 
                if (arr[j] > arr[j + 1]) 
                { 
                    // swap temp and arr[i] 
                    int temp = arr[j]; 
                    arr[j] = arr[j + 1]; 
                    arr[j + 1] = temp; 
                } 
    } 
//-----------------------------------------------  
    /* Prints the array */
    static void printArray(int []arr) 
    { 
        int n = arr.Length; 
        for (int i = 0; i < n; ++i) 
            Console.Write(arr[i] + " "); 
        Console.WriteLine(); 
    } 
  
    // Driver method 
    public static void Main() 
    { 
        int []arr = {64, 34, 25, 12, 22, 11, 90}; 
        bubbleSort(arr); 
        Console.WriteLine("Sorted array"); 
        printArray(arr); 
    } 
  
} 
  
// This code is contributed by Sam007 

```

-- JavaScript --
```javascript
function sortBubble(data) {
    var tmp;
  
    for (var i = data.length - 1; i > 0; i--) {
        for (var j = 0; j < i; j++) {
            if (data[j] > data[j+1]) {
                tmp = data[j];
                data[j] = data[j+1];
                data[j+1] = tmp;
            }
        }
    }
    return data;
}

```

-- PHP --
```php
<?php  
// PHP program for implementation  
// of Bubble Sort 
  
function bubbleSort(&$arr) 
{ 
    $n = sizeof($arr); 
  
    // Traverse through all array elements 
    for($i = 0; $i < $n; $i++)  
    { 
        // Last i elements are already in place 
        for ($j = 0; $j < $n - $i - 1; $j++)  
        { 
            // traverse the array from 0 to n-i-1 
            // Swap if the element found is greater 
            // than the next element 
            if ($arr[$j] > $arr[$j+1]) 
            { 
                $t = $arr[$j]; 
                $arr[$j] = $arr[$j+1]; 
                $arr[$j+1] = $t; 
            } 
        } 
    } 
} 
  
// Driver code to test above 
$arr = array(64, 34, 25, 12, 22, 11, 90); 
  
$len = sizeof($arr); 
bubbleSort($arr); 
  
echo "Sorted array : \n"; 
  
for ($i = 0; $i < $len; $i++) 
    echo $arr[$i]." ";  
  
// This code is contributed by ChitraNayal. 
?> 

```

-- Python --

```python
# Python program for implementation of Bubble Sort 
  
def bubbleSort(arr): 
    n = len(arr) 
  
    # Traverse through all array elements 
    for i in range(n): 
  
        # Last i elements are already in place 
        for j in range(0, n-i-1): 
  
            # traverse the array from 0 to n-i-1 
            # Swap if the element found is greater 
            # than the next element 
            if arr[j] > arr[j+1] : 
                arr[j], arr[j+1] = arr[j+1], arr[j] 
  
# Driver code to test above 
arr = [64, 34, 25, 12, 22, 11, 90] 
  
bubbleSort(arr) 
  
print ("Sorted array is:") 
for i in range(len(arr)): 
    print ("%d" %arr[i]),  

```

###  <center> Selection (Выбором) </center>

### <center> Shell (Метод Шелла) </center>


### <center> Merge (Слиянием) </center>


###  <center> Heap (Куча) </center>


###  <center> Quick (Быстрая) </center>


###  <center> Quick3 (Быстрая3) </center>





## <center> Searching Algorithms </center>

###  <center> Linear Search (Линейный поиск) </center>

### <center> Binary Search (Бинарный поиск) </center>
