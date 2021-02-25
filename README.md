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
Insertion sort is a simple sorting algorithm that works similar to the way you sort playing cards in your hands. 
The array is virtually split into a sorted and an unsorted part.
Values from the unsorted part are picked and placed at the correct position in the sorted part.

Algorithm

![Insertion](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/insertionsort.png)

<b>To sort an array of size n in ascending order:</b> 
- 1: Iterate from arr[1] to arr[n] over the array. 
- 2: Compare the current element (key) to its predecessor. 
- 3: If the key element is smaller than its predecessor, compare it to the elements before. Move the greater elements one position up to make space for the swapped element.
</p>

![Insertion](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortinsert.gif)

-- Pseudocode --
```
Another Example: 
12, 11, 13, 5, 6
Let us loop for i = 1 (second element of the array) to 4 (last element of the array)
i = 1. Since 11 is smaller than 12, move 12 and insert 11 before 12 
11, 12, 13, 5, 6
i = 2. 13 will remain at its position as all elements in A[0..I-1] are smaller than 13 
11, 12, 13, 5, 6
i = 3. 5 will move to the beginning and all other elements from 11 to 13 will move one position ahead of their current position. 
5, 11, 12, 13, 6
i = 4. 6 will move to position after 5, and elements from 11 to 13 will move one position ahead of their current position. 
5, 6, 11, 12, 13 
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
// C# program for implementation of Insertion Sort
using System;
 
class InsertionSort {
 
    // Function to sort array
    // using insertion sort
    void sort(int[] arr)
    {
        int n = arr.Length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;
 
            // Move elements of arr[0..i-1],
            // that are greater than key,
            // to one position ahead of
            // their current position
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }
 
    // A utility function to print
    // array of size n
    static void printArray(int[] arr)
    {
        int n = arr.Length;
        for (int i = 0; i < n; ++i)
            Console.Write(arr[i] + " ");
 
        Console.Write("\n");
    }
 
    // Driver Code
    public static void Main()
    {
        int[] arr = { 12, 11, 13, 5, 6 };
        InsertionSort ob = new InsertionSort();
        ob.sort(arr);
        printArray(arr);
    }
}
 
// This code is contributed by ChitraNayal.
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

-- javascript --
```javascript
<script>
    // Javascript program for insertion sort

    // Function to sort an array using insertion sort
    function insertionSort(arr, n)
    {
        let i, key, j;
        for (i = 1; i < n; i++)
    {
        key = arr[i];
        j = i - 1;

        /* Move elements of arr[0..i-1], that are  
        greater than key, to one position ahead  
        of their current position */
        while (j >= 0 && arr[j] > key)
    {
        arr[j + 1] = arr[j];
        j = j - 1;
    }
        arr[j + 1] = key;
    }
    }

    // A utility function to print an array of size n
    function printArray(arr, n)
    {
        let i;
        for (i = 0; i < n; i++)
        document.write(arr[i] + " ");
        document.write("<br>");
    }

    // Driver code
    let arr = [12, 11, 13, 5, 6 ];
    let n = arr.length;

    insertionSort(arr, n);
    printArray(arr, n);

    // This code is contributed by Mayank Tyagi

</script>
```

-- PHP --
```php
<?php 
// PHP program for insertion sort
 
// Function to sort an array
// using insertion sort
function insertionSort(&$arr, $n)
{
    for ($i = 1; $i < $n; $i++)
    {
        $key = $arr[$i];
        $j = $i-1;
     
        // Move elements of arr[0..i-1],
        // that are    greater than key, to 
        // one position ahead of their 
        // current position
        while ($j >= 0 && $arr[$j] > $key)
        {
            $arr[$j + 1] = $arr[$j];
            $j = $j - 1;
        }
         
        $arr[$j + 1] = $key;
    }
}
 
// A utility function to
// print an array of size n
function printArray(&$arr, $n)
{
    for ($i = 0; $i < $n; $i++)
        echo $arr[$i]." ";
    echo "\n";
}
 
// Driver Code
$arr = array(12, 11, 13, 5, 6);
$n = sizeof($arr);
insertionSort($arr, $n);
printArray($arr, $n);
 
// This code is contributed by ChitraNayal.
?>
```

-- Python --
```Python
# Python program for implementation of Insertion Sort
 
# Function to do insertion sort
def insertionSort(arr):
 
    # Traverse through 1 to len(arr)
    for i in range(1, len(arr)):
 
        key = arr[i]
 
        # Move elements of arr[0..i-1], that are
        # greater than key, to one position ahead
        # of their current position
        j = i-1
        while j >= 0 and key < arr[j] :
                arr[j + 1] = arr[j]
                j -= 1
        arr[j + 1] = key
 
 
# Driver code to test above
arr = [12, 11, 13, 5, 6]
insertionSort(arr)
for i in range(len(arr)):
    print ("% d" % arr[i])
 
# This code is contributed by Mohit Kumra
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

* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
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


### <center> Shell (Метод Шелла) </center>


### <center> Merge (Слиянием) </center>


###  <center> Heap (Куча) </center>


###  <center> Quick (Быстрая) </center>


###  <center> Quick3 (Быстрая3) </center>





## <center> Searching Algorithms </center>

###  <center> Linear Search (Линейный поиск) </center>

### <center> Binary Search (Бинарный поиск) </center>
