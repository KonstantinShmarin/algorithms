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
The selection sort algorithm sorts an array by repeatedly finding the minimum element (considering ascending order) from unsorted part and putting it at the beginning. The algorithm maintains two subarrays in a given array.

1) The subarray which is already sorted.
2) Remaining subarray which is unsorted.

In every iteration of selection sort, the minimum element (considering ascending order) from the unsorted subarray is picked and moved to the sorted subarray.

Following example explains the above steps:
</p>

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

* 2 - explanation:
<p align="justify">
From the comparions presented here, one might conclude that selection sort should never be used. It does not adapt to the data in any way (notice that the four animations above run in lock step), so its runtime is always quadratic.

However, selection sort has the property of minimizing the number of swaps. In applications where the cost of swapping items is high, selection sort very well may be the algorithm of choice.
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortselection.gif)


-- Pseudocode --
```
for i = 1:n,
    k = i
    for j = i+1:n, if a[j] < a[k], k = j
    → invariant: a[k] smallest of a[i..n]
    swap a[i,k]
    → invariant: a[1..i] in final position
end

```

-- C# --
```C#
// C# program for implementation  
// of Selection Sort 
using System; 
  
class GFG 
{  
//----------------------------------------------------------
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
//----------------------------------------------------------
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

-- JavaScript --
```javascript
function selectionSort(inputArr) {
    let n = inputArr.length;

    for(let i = 0; i < n; i++) {
        // Finding the smallest number in the subarray
        let min = i;
        for(let j = i+1; j < n; j++){
            if(inputArr[j] < inputArr[min]) {
                min=j;
            }
        }
        if (min != i) {
            // Swapping the elements
            let tmp = inputArr[i];
            inputArr[i] = inputArr[min];
            inputArr[min] = tmp;
        }
    }
    return inputArr;
}

let inputArr = [5, 2, 4, 6, 1, 3];
selectionSort(inputArr);
console.log(inputArr);

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
```python
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


### <center> Shell (Метод Шелла) </center>


* 1 - explanation:
<p align="justify">
ShellSort is mainly a variation of Insertion Sort. In insertion sort, we move elements only one position ahead. When an element has to be moved far ahead, many movements are involved. The idea of shellSort is to allow exchange of far items. In shellSort, we make the array h-sorted for a large value of h. We keep reducing the value of h until it becomes 1. An array is said to be h-sorted if all sublists of every h’th element is sorted.
</p>

<p align="justify">
Time Complexity: Time complexity of above implementation of shellsort is O(n2). In the above implementation gap is reduce by half in every iteration. There are many other ways to reduce gap which lead to better time complexity.
</p>

* 2 - explanation:
<p align="justify">
The worse-case time complexity of shell sort depends on the increment sequence. For the increments 1 4 13 40 121…, which is what is used here, the time complexity is O(n3/2). For other increments, time complexity is known to be O(n4/3) and even O(n·lg2(n)). Neither tight upper bounds on time complexity nor the best increment sequence are known.

Because shell sort is based on insertion sort, shell sort inherits insertion sort’s adaptive properties. The adapation is not as dramatic because shell sort requires one pass through the data for each increment, but it is significant. For the increment sequence shown above, there are log3(n) increments, so the time complexity for nearly sorted data is O(n·log3(n)).

Because of its low overhead, relatively simple implementation, adaptive properties, and sub-quadratic time complexity, shell sort may be a viable alternative to the O(n·lg(n)) sorting algorithms for some applications when the data to be sorted is not very large.
</p>

![Shell ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/shellsort.gif)


-- Pseudocode --
```
h = 1
while h < n, h = 3*h + 1
while h > 0,
    h = h / 3
    for k = 1:h, insertion sort a[k:h:n]
    → invariant: each h-sub-array is sorted
end

```

-- C# --
```C#
// C# implementation of ShellSort 
using System; 
  
class ShellSort 
{ 
    /* An utility function to  
       print array of size n*/
    static void printArray(int []arr) 
    { 
        int n = arr.Length; 
        for (int i=0; i<n; ++i) 
        Console.Write(arr[i] + " "); 
        Console.WriteLine(); 
    } 
//---------------------------------------------------------
    /* function to sort arr using shellSort */
    int sort(int []arr) 
    { 
        int n = arr.Length; 
  
        // Start with a big gap,  
        // then reduce the gap 
        for (int gap = n/2; gap > 0; gap /= 2) 
        { 
            // Do a gapped insertion sort for this gap size. 
            // The first gap elements a[0..gap-1] are already 
            // in gapped order keep adding one more element 
            // until the entire array is gap sorted 
            for (int i = gap; i < n; i += 1) 
            { 
                // add a[i] to the elements that have 
                // been gap sorted save a[i] in temp and 
                // make a hole at position i 
                int temp = arr[i]; 
  
                // shift earlier gap-sorted elements up until 
                // the correct location for a[i] is found 
                int j; 
                for (j = i; j >= gap && arr[j - gap] > temp; j -= gap) 
                    arr[j] = arr[j - gap]; 
  
                // put temp (the original a[i])  
                // in its correct location 
                arr[j] = temp; 
            } 
        } 
        return 0; 
    } 
//--------------------------------------------------------- 
    
    // Driver method 
    public static void Main() 
    { 
        int []arr = {12, 34, 54, 2, 3}; 
        Console.Write("Array before sorting :\n"); 
        printArray(arr); 
  
        ShellSort ob = new ShellSort(); 
        ob.sort(arr); 
  
        Console.Write("Array after sorting :\n"); 
        printArray(arr); 
    } 
}  
  
// This code is contributed by nitin mittal. 

```

-- JavaScript --
```javascript
const ShellSort = arr => {
    const l = arr.length;
    let gap = Math.floor(l / 2);
    while (gap >= 1) {
        for (let i = gap; i < l; i++) {
            const current = arr[i];
            let j = i;
            while (j > 0 && arr[j - gap] > current) {
                arr[j] = arr[j - gap];
                j -= gap;
            }
            arr[j] = current;
        }
        gap = Math.floor(gap / 2);
    }
    return arr;
};

```

-- JavaScript --
```javascript
function shellSort(arr) {
    var increment = arr.length / 2;
    while (increment > 0) {
        for (i = increment; i < arr.length; i++) {
            var j = i;
            var temp = arr[i];

            while (j >= increment && arr[j-increment] > temp) {
                arr[j] = arr[j-increment];
                j = j - increment;
            }

            arr[j] = temp;
        }

        if (increment == 2) {
            increment = 1;
        } else {
            increment = parseInt(increment*5 / 11);
        }
    }
    return arr;
}

console.log(shellSort([3, 0, 2, 5, -1, 4, 1]));

```

-- PHP --
```php
<?php
function shell_Sort($my_array)
{
	$x = round(count($my_array)/2);
	while($x > 0)
	{
		for($i = $x; $i < count($my_array);$i++){
			$temp = $my_array[$i];
			$j = $i;
			while($j >= $x && $my_array[$j-$x] > $temp)
			{
				$my_array[$j] = $my_array[$j - $x];
				$j -= $x;
			}
			$my_array[$j] = $temp;
		}
		$x = round($x/2.2);
	}
	return $my_array;
}
 
$test_array = array(3, 0, 2, 5, -1, 4, 1);
echo "Original Array :\n";
echo implode(', ',$test_array );
echo "\nSorted Array\n:";
echo implode(', ',shell_Sort($test_array)). PHP_EOL;
?>
```

-- Python --
```python
# Python3 program for implementation of Shell Sort 
  
def shellSort(arr): 
  
    # Start with a big gap, then reduce the gap 
    n = len(arr) 
    gap = n//2
  
    # Do a gapped insertion sort for this gap size. 
    # The first gap elements a[0..gap-1] are already in gapped  
    # order keep adding one more element until the entire array 
    # is gap sorted 
    while gap > 0: 
  
        for i in range(gap,n): 
  
            # add a[i] to the elements that have been gap sorted 
            # save a[i] in temp and make a hole at position i 
            temp = arr[i] 
  
            # shift earlier gap-sorted elements up until the correct 
            # location for a[i] is found 
            j = i 
            while  j >= gap and arr[j-gap] >temp: 
                arr[j] = arr[j-gap] 
                j -= gap 
  
            # put temp (the original a[i]) in its correct location 
            arr[j] = temp 
        gap //= 2
  
  
# Driver code to test above 
arr = [ 12, 34, 54, 2, 3] 
  
n = len(arr) 
print ("Array before sorting:") 
for i in range(n): 
    print(arr[i]), 
  
shellSort(arr) 
  
print ("\nArray after sorting:") 
for i in range(n): 
    print(arr[i]), 
  
# This code is contributed by Mohit Kumra 
```

### <center> Merge (Слиянием) </center>


* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)


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

-- C# --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- JavaScript --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- PHP --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Python --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

###  <center> Heap (Куча) </center>


* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)


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

-- C# --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- JavaScript --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- PHP --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Python --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

###  <center> Quick (Быстрая) </center>


* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)


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

-- C# --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- JavaScript --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- PHP --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Python --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

###  <center> Quick3 (Быстрая3) </center>


* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)


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

-- C# --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- JavaScript --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- PHP --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Python --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```




## <center> Searching Algorithms </center>

###  <center> Linear Search (Линейный поиск) </center>


* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)


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

-- C# --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- JavaScript --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- PHP --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Python --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

### <center> Binary Search (Бинарный поиск) </center>



* 1 - explanation:
<p align="justify">

Bubble sort has many of the same properties as insertion sort, but has slightly higher overhead. In the case of nearly sorted data, bubble sort takes O(n) time, but requires at least 2 passes through the data (whereas insertion sort requires something more like 1 pass).
</p>



![Selection ](https://raw.githubusercontent.com/KonstantinShmarin/algorithms/main/img/sortbubble.gif)


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

-- C# --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- JavaScript --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- PHP --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```

-- Python --
```
FOR J=1 TO N-1 STEP 1
 F=0
 FOR I=0 TO N-1-J STEP 1
   IF A[I]>A[I+1] THEN SWAP A[I],A[I+1]:F=1
 NEXT I
 IF F=0 THEN EXIT FOR
NEXT J

```
