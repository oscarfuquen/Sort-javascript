# Bubble Sort
How it works:

step-1: you compare the first item with the second. If the first item is bigger than the second item. you swap them so that the bigger one stays in the second position.

step-2:And then compare second with third item. if second item is bigger than the third, we swap them. otherwise, they stayed in their position. Hence, the biggest among first three is in the third position.

step-3:we keep doing it. until we hit the last element of the array. In that way we bubble up the biggest item of the array to the right most position of the array.

step-4: Look at the inner loop in the code below.

step-5: We repeat this process, starting from the last item of the array. look at the outer loop in the code below. We do this way, so that after finishing the first inner loop, the biggest one will be in the last item of the array.

step-6: and then we move backward inside the outer loop.

# Selection Sort
how does it works: This is very simple. Go through the array, find the index of the lowest element swap the lowest element with the first element. Hence first element is the lowest element in the array.

Now go through the rest of the array (excluding the first element) and find the index of the lowest and swap it with the second element.

thats how it continues to select (find out) the lowest element of the array and putting it on the left until it hits the last element.

# Insertion sort
How it works: Imagine you are playing cards. Somebody is giving you cards one by one. When you are receiving card, you are planning to put them in a way so that the smaller one is on the left. This means you want to insert them in a sorted way

step-1: If the first card you are getting is 5. Just hold the card in your hand. you dont have to do anything.

step-2: If the second card is 2, you want to put it before 5 so that the two cards you have are sorted. When you are putting the card with number 2 at the left, you are changing the position of the card 5 from first position to second position. And then first position becomes available and you put 2 there.

step-3: If the third card is 4. you will start from second position. In the second position, you have card 5 which is bigger than 4. Hence you will move 5 to the third position. The next card to the left is 2 which is smaller than 4. Hence, you wont move 2. And you will insert card 4 in the second position.

step-4: Then you got 10. It is bigger than the previous card which is 5. Hence, you just add it at the last position.

step-5: The next card is 7. You just move the position of the card 10 to the right and insert card 7.

step-6: If the last card is 3. You will have to move 10 to the right as it is bigger than 3. and then you check with the next card to the left it is 7 which is bigger than 3. you move it to the right. similarly, you move 5, 4 to the right. And put the number 3 before 2 as 2 is smaller than 3.

Code Insertion sort: Code is similar to the card and image above. It starts with the second element. Pick the second element to be inserted and then compare to the previous element. If the first one is bigger, move the first one to second position and second one at first.

Now first and second item is sorted.

Then, pick the third element and check whether the second element is bigger than the third. keep going similar way until you hit the first element or a element smaller than the element you are comparing with. When you get an item smaller than the picked item, you insert it.

# Merge Sort

just break down your array into small and small pieces and until you have one items in each pieces. then merge together by comparing them. If you still have hard time to figure out what i am talking about, look at merge sort gif taken from wikipedia

Code Merge Sort: Merge sort has two parts. Main part does divide or breaks down and second part is merging/combining parts. At the time of combining, parts are combined together.

Divide: the first function named as mergeSort is actually a divide function. where an array is divided into two.

merge: this is just merging two sorted array. Just be careful this two array could be in different size

# Quick sort
Step-1: You have to pick a pivot. This could be randomly selected or the middle one. Here we select the last element of the array.

Step-2: Put all the items smaller than the pivot value to the left and larger than the pivot value to the right.

Step-3:Repeat the step-2 for both left and right side of the pivot (pick a pivot, put all item smaller than the pivot to the left and larger on the right)

Explain the code

Call Quick sort: Pass the array and pass left and right to the quickSort function. For the first call, left would be the index of the first element which is 0 and right would be the index of the last element which would be length -1.

Select Pivot: We select pivot as the last index of the array.

Call Partition function: After calculating the pivot, we send the pivot to the partition function. In the partition function we pass array, pivot index, left and right.

partitionIndex: In the partition function, we keep move all the items smaller than the pivot value to the left and larger than pivot value to the right. We have to keep track of the position of the partition. so that we can split the array into two parts in the next step. This tracking of the index where we partition the array is done by using partitionIndex variable. the initial value is left.

Swap function: This is just a helper function to swap values of the array.

move elements: we start a for loop from the left, and if the values is smaller than the pivot values we swap it with the position of the partitionIndex and increase the value of the partitionIndex. If the value is bigger, we don't do anything. We keep going until the element before the last element (remember last element is the pivot)

place pivot After moving all the smallest element to the left, we swap the last element (pivot value) with the partitionIndex. By doing this, the pivot sits where it suppose to sit when the full array is sorted. As all elements left to it smaller and all element right to it is bigger. End of the function partition, return the partitionIndex

Repeat the process: Now come back to quickSort function. when you get the partitionIndex, apply quickSort for the left side of the array and right side of the array. keep doing it until left is smaller than right.

#Heap sort

Given an array of 6 elements: 15, 19, 10, 7, 17, 16, sort it in ascending order using heap sort.

Steps:

Consider the values of the elements as priorities and build the heap tree.
Start deleteMin operations, storing each deleted element at the end of the heap array.
After performing step 2, the order of the elements will be opposite to the order in the heap tree. 
Hence, if we want the elements to be sorted in ascending order, we need to build the heap tree 
in descending order - the greatest element will have the highest priority.

Note that we use only one array , treating its parts differently:

when building the heap tree, part of the array will be considered as the heap, 
and the rest part - the original array.
when sorting, part of the array will be the heap, and the rest part - the sorted array.
This will be indicated by colors: white for the original array, blue for the heap and red for the sorted array

Here is the array: 15, 19, 10, 7, 17, 6

Building the heap tree
The array represented as a tree, complete but not ordered:

Start with the rightmost node at height 1 - the node at position 3 = Size/2. 
It has one greater child and has to be percolated down:


After processing array[3] the situation is:


Next comes array[2]. Its children are smaller, so no percolation is needed.

The last node to be processed is array[1]. Its left child is the greater of the children. 
The item at array[1] has to be percolated down to the left, swapped with array[2].


As a result the situation is:


The children of array[2] are greater, and item 15 has to be moved down further, swapped with array[5].


Now the tree is ordered, and the binary heap is built.
Sorting - performing deleteMax operations:
1. Delete the top element 19.
1.1. Store 19 in a temporary place. A hole is created at the top


1.2. Swap 19 with the last element of the heap. 
As 10 will be adjusted in the heap, its cell will no longer be a part of the heap. 
Instead it becomes a cell from the sorted array

1.3. Percolate down the hole


1.4. Percolate once more (10 is less that 15, so it cannot be inserted in the previous hole)


Now 10 can be inserted in the hole


2. DeleteMax the top element 17
2.1. Store 17 in a temporary place. A hole is created at the top


2.2. Swap 17 with the last element of the heap. 

As 10 will be adjusted in the heap, its cell will no longer be a part of the heap.
Instead it becomes a cell from the sorted array

2.3. The element 10 is less than the children of the hole, and we percolate the hole down:


2.4. Insert 10 in the hole


3. DeleteMax 16
3.1. Store 16 in a temporary place. A hole is created at the top


3.2. Swap 16 with the last element of the heap. 
As 7 will be adjusted in the heap, its cell will no longer be a part of the heap.
Instead it becomes a cell from the sorted array

3.3. Percolate the hole down (7 cannot be inserted there - it is less than the children of the hole)


3.4. Insert 7 in the hole


4. DeleteMax the top element 15
4.1. Store 15 in a temporary location. A hole is created.


4.2. Swap 15 with the last element of the heap. 

As 10 will be adjusted in the heap, its cell will no longer be a part of the heap. 
Instead it becomes a position from the sorted array

4.3. Store 10 in the hole (10 is greater than the children of the hole)


5. DeleteMax the top element 10.
5.1. Remove 10 from the heap and store it into a temporary location.


5.2. Swap 10 with the last element of the heap. 

As 7 will be adjusted in the heap, its cell will no longer be a part of the heap. Instead it becomes a cell from the sorted array

5.3. Store 7 in the hole (as the only remaining element in the heap


7 is the last element from the heap, so now the array is sorted

