# Fibonacci Heap — Insertion and Union

> Source: https://www.geeksforgeeks.org/fibonacci-heap-insertion-and-union/ — GeeksforGeeks. (Implementation shown in Python; the source page also provides C++/Java/C#/JavaScript versions.)

**Fibonacci Heap** is a collection of trees with min-heap or max-heap property. In Fibonacci Heap, trees can have any shape even all trees can be single nodes (This is unlike Binomial Heap where every tree has to be a Binomial Tree). In this article, we will discuss Insertion and Union operation on Fibonacci Heap. 

**Prerequisites:** Fibonacci Heap (Introduction)

**Insertion:** To insert a node in a Fibonacci heap H, the following algorithm is followed: 

> 1.  Create a new node 'x'.
> 2.  Check whether heap H is empty or not.
> 3.  If H is empty then: \
>     - Make x as the only node in the root list.
>     - Set H(min) pointer to x.
> 4.  Else: \
>     - Insert x into root list and update H(min).

**Example:** 

![[img/fibins-01.jpg|600]]

**Union:** Union of two Fibonacci heaps H1 and H2 can be accomplished as follows: 

> 1.  Join root lists of Fibonacci heaps H1 and H2 and make a single Fibonacci heap H.
> 2.  If H1(min) < H2(min) then: \
>     - H(min) = H1(min).
> 3.  Else: \
>     - H(min) = H2(min).

**Example:** 

![[img/fibins-02.jpg|600]]

**Following is a program to demonstrate building and inserting in a Fibonacci heap: ** 

```
# Python program to demonstrate building
# and inserting in a Fibonacci heap

class node:
    def __init__(self):
        self.parent = None  # Assign data
        self.child = None  # Initialize next as null
        self.left = None
        self.right = None
        self.key = -1

# Creating min pointer as "mini"
mini = node()

# Declare an integer for number of nodes in the heap
no_of_nodes = 0

# Function to insert a node in heap

def insertion(val):
    new_node = node()
    new_node.key = val
    new_node.parent = None
    new_node.child = None
    new_node.left = new_node
    new_node.right = new_node

    global mini
    if mini.key != -1:
        (mini.left).right = new_node
        new_node.right = mini
        new_node.left = mini.left
        mini.left = new_node
        if (new_node.key < mini.key):
            mini = new_node
    else:
        mini = new_node

# Function to display the heap

def display(mini):
    ptr = mini
    if (ptr == None):
        print("The Heap is Empty")
    else:

        print("The root nodes of Heap are: ")
        print(ptr.key, end="")
        ptr = ptr.right
        if(ptr != mini):
            print("-->", end="")

        while ptr != mini and ptr.right != None:
            print(ptr.key, end="")
            ptr = ptr.right
            if ptr != mini:
                print("-->", end="")
        print()
        print(f"The heap has {no_of_nodes} nodes")

# Function to find min node in the heap

def find_min(mini):
    print(f"min of heap is: {mini.key}")

# Driver code
no_of_nodes = 7
insertion(4)
insertion(3)
insertion(7)
insertion(5)
insertion(2)
insertion(1)
insertion(10)

display(mini)

find_min(mini)

# The code is contributed by Gautam goel (gautamgoel962)
```

**Output**

    The root nodes of Heap are:
    1-->2-->3-->4-->7-->5-->10
    The heap has 7 nodes
    min of heap is: 1
