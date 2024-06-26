# Week5 - Data Structures

* ## [Course link](https://cs50.harvard.edu/x/2024/weeks/5/)</br>
[![Week5 - Data structure](https://img.youtube.com/vi/0euvEdPwQnQ/0.jpg)](https://www.youtube.com/watch?v=0euvEdPwQnQ)

## Data Structures
A data structure represents how data is stored and organized in the computer memory. There are many types of data structures, and they serve many different purposes.

## Stacks and Queues
### Queue
1. The queue has the FIFO attribute that executes the data sequence in a "first in, first out" manner. Imagine people lining up in front of a store. Customers who are earlier in the queue have priority to select merchandise and pay, while customers behind them have to wait for the people in front of them. 
2.  Two indexes are needed to record the start and end position of the data. The starting index of the data is called the front, and the last data index is called the rear. Queues are also used for job scheduling in programming.</br></br></br>

<h3 style="text-align: center;">Empty queue</h3>
<div style="display: flex; flex-direction: row; justify-content: space-evenly;">
<div>
    
![image](https://hackmd.io/_uploads/B1qyM4om0.png)    

</div>    
<div>
    <ul>
            <li>First element 'A' </li>
            <li>front index = -1</li>
            <li>rear index = 0</li>
    </ul>
</div>
</div>
<div>
    
```c
#define MAX_SIZE = 5
// declare queue data structure
typedef struct que{
    char data[MAX_SIZE];
    int front;
    int rear;
}queue;
    
// declare an "empty" queue Q
queue Q;
Q.front = -1;
Q.rear = -1;
    
// Assign 0 index value
Q->data[0] = A;
```
</div></br>

<h3 style="text-align: center;">Insert new data: Enqueue</h3>
<div style="display: flex; flex-direction: row; justify-content: space-evenly;">  
<div>
    
![image](https://hackmd.io/_uploads/SkwSG4i7R.png)
      
</div>    

<div>
    <ul>
            <li>Insert 1st index element'B'</li>
            <li>front index = -1</li>
            <li>rear index = 1 </li>
    </ul>
</div>
</div>
<div>
    
```c
// enqueue
enqueue(queue *Q, char value)
{
    if(Q->rear == (MAX_SIZE - 1))
    {
        printf("The queue is out of space");
    }
    else
    {
        Q->data[++Q->rear] = value;
    }
}  
// Before inserting data: rear = 0
// Q->data[rear + 1] = B;
Q->data[0 + 1] = B;
```    
</div></br>

<h3 style="text-align: center;">Delete data: Dequeue</h3>
<div style="display: flex; flex-direction: row; justify-content: space-evenly;">
    
<div>

![image](https://hackmd.io/_uploads/r1juzVoQ0.png)
        
</div>

<div> 
    <ul>
            <li>Delete 0th index element'A'</li>
            <li>front index = 0</li>
            <li>rear index = 1</li>
    </ul>
</div>
</div>
<div>

```c
//dequeue
dequeue(queue *Q)
{
    if(Q->front == Q->rear)
    {
        printf("Queue is empty");
    }
    else
    {
        printf("%c", Q->data[++Q->front]);
    }
}
// Before deleting data front = 0
// printf("%c", Q->data[front + 1]);
printf("%c", Q->data[0 + 1]);
``` 
</div>
[tbd]ex???Other data structure can also apply the queue concept.</br>

### Stack
* The stack has the LIFO attribute and executes the data sequence in a "last in, first out" manner. Stacking has usage for data reversal, parsing, recursion, and backtracking. Think about playing Tower of Hanoi. To move the tower from one side to the other, always move the top disk to other rods once a time.

* Consider the concept of system stacking, as shown below: Function 1 is the last function called. It is also located in the top frame and has the highest execution priority. When f1  completes, it passes values back to main(), and continues executing the rest of the code.  
</br><img src ="https://hackmd.io/_uploads/BJTVVdom0.png" width = 30% style="display: block; margin: auto;"></br></br></br>

* The complete operation and definition of data structure stacking are as follows:

```c
// Define a stack structure
#define MAX_SIZE 5

typedef struct stack
{
    char data[MAX_SIZE];// store data in stack    
    int top;// record the top index number
}stack;
```

<h3 style="text-align: center">Isempty( )</h3></br>

<div style="display: flex; flex-direction: row; justify-content: space-around;">
<div>
</br>
  
<img src = "https://hackmd.io/_uploads/BkHZYFiQR.png" width = 15%>

</div>

<div>

* S->top is -1 if the stack is empty. 
```c
int isEmpty(stack *S)
{
    if(S->top == -1)
    {
        printf("Stack is empty!");
        return 1;
    }
    return 0;
}
    
```

</div>
</div>
</br>

<h3 style="text-align: center">Isfull( )</h3></br>

<div style="display: flex; flex-direction: row; justify-content: space-around;">
<div>
<img src = "https://hackmd.io/_uploads/rkLxh6RQ0.png" width = 15%>
</div></br>
    
<div>
  
* S->top = 4 if  the stack is full
  
```c
int isFULL(stack *S)
{
    if(S->top == MAX_SIZE -1)
    {
        printf("Stack is full!");        
        return 1;
    }
    return 0;
}
``` 
</div>
</div>    
</br>

<h3 style="text-align: center">Push( ): Insert data</h3></br>

<div style="display: flex; flex-direction: row; justify-content: space-around;">   
<div>
<img src = "https://hackmd.io/_uploads/B1cgkfRmR.png" width = 15%>
</div>
<div></br>

* Before inserting data, S->top = -1
* After inserting data, S->top = -1 + 1 = 0
```c
push(char value, stack *S)
{
    // if Stack is full, print message and return 1
    if(isFull(S))
    {
         return 1;   
    }
    // if there're still space in stack, 
    // top value +1, and set S->data[top] = value
    S->data[++S->top] = value;
}
```
    
</div>
</div>
</br> 


<h3 style="text-align: center">Pop( ): Delete data</h3></br>

<div style="display: flex; flex-direction: row; justify-content: space-around;">
  
  <div>
    
  <img src = "https://hackmd.io/_uploads/rkMGkf0m0.png" width = 15%>
  
  </br>
  
  * Before deleting data, S->top = 2 
  
  </div>
  </br>
  <div>    
  
  <img src = "https://hackmd.io/_uploads/ryk7kMCQ0.png" width = 15%>
  
  </br>
  
  * After deleting data, S->top = 1

  </div>
  </br>
</div></br>

```c
pop (stack *S)
{
    char popValue;
    if(isEmpty(S))
    {
        return 1;
    }
    // Store the deleted value in the variable popValue
    S->data[top] = popValue;
    // else, S->top - 1 and print the NEXT top value
    printf("%c", S->data[--S->top]);
}
```
</br></br></br>

---

## Resizing Arrays------Pros and Cons in Memory allocation
* If we want to resize an array (or other data structures), the intuitive thing is to ask for more memory.  And if we don't know exactly how much memory is needed, exceeded memory might be allocated than we need and storing garbage values, which is probably not a good design.
* One of the data structures in dynamic memory allocation is the Linked list, and it can solve this problem. Data in the linked list can grow and shrink flexibly.

## Linked list
* Link lists are not stored in contiguous memory blocks. A linked list consists of many nodes, which contain pointers and information. The pointer in the node points to the next node's address, repeats this process until it reaches the end of the linked list, and points to NULL eventually. A linked list establishes data connection by dynamically allocating memory and linking them with pointers. </br></br></br>

<img src = "https://hackmd.io/_uploads/Hyjzamn7C.png" width = 80% style="display:block; margin: auto;"></br>

* In the picture below, we'd like to build a connection between three integers 1, 2, and 3 in the computer memory shown below. On the picture's left side is a pointer recording the address 0x123, pointing to the first node in this list. </br></br></br>

<img src = "https://hackmd.io/_uploads/HyLQk42mR.png" width = 80% style="display:block; margin: auto;"></br>

* The building logic of a linked list 
</br></br></br>

### Single linked list 
* Nodes in the single-linked list store pointers pointing to the next node in one single direction. The red arrow in the picture is a pointer pointing to the next node. And so is the second pointer, keeping track of the next node. The node at the end of the linked list points to NULL since it has nothing else to point to.

<img src = "https://hackmd.io/_uploads/BJPZRyi7A.png" width = 50% style="display:block; margin: auto;">
</br></br></br>

> * Create a single linked list
0. The single linked list's structure includes nodes stored values' datatype and a pointer to link with other nodes.


```c 
// General form of a single linked list node
Typedef struct sllist
{
    dataType value;
    Struct sllist* next;// the next node's address
}sllnode;

// structure of nodefor the following example 
typedef struct node
{
    int number;
    struct node *next;
}
node;
```
</br>

1. The first step to declare a new linked list is to create a pointer "head" of the list, which points to the first node of the list. 

```c
// list is the first element in the list
// It doesn't store any value, 
// It points to the first node in the list
node *list;
list->next = NULL;
```
</br>

> * Insert the first node
```c
// creat the first node
node *n1 = malloc(sizeof(node));
// Assign value to the first node
n->number = 2;
// n is the last element of the list, 
// It points to nothing, so set next pointer to NULL
n->next= NULL;
// Set head pointer points to the head of the list
list = n;
```
* Set list points to the node n's address

<img src = "https://hackmd.io/_uploads/Syejo_3QC.png" width = 80% style="display:block; margin: auto;">
</br>

>* Insert the second node

```c
// creat a new node
node *n = malloc(sizeof(node));
// Assign value to new node
n->number = 1;
// Initialize n points to NULL
n->next = NULL;
// set new node points to the first node
n->next = list;
// update list head to n
list = n;
```

<img src = "https://hackmd.io/_uploads/B1daquhQC.png" width = 80% style="display:block; margin: auto;">
* Result is head->1->2
</br>

> * Delete a node

Delete a node in a linked list means you free the node's memory. For example, if we would like to delete the last inserted node, integer 1, the head of the list changes to point to node 2, and then frees node 1's memory. 

```c
// create a pointer nptr to remember
//the head of the list AFTER freeing node 1
node *nptr = NULL;
// *nptr points to node 2
nptr = list->next;
// free the head of the list : node 1
free(list);
// reassign head to nptr: node 2
list = nptr;
```
</br>

> * Calculate the node length

```c
int count()
{
    int length = 0;
    current = head->next;
    while(current!=NULL)
    {
        length++;
        current = current->next;
    }
    return length;
}
```

### Double linked list
* A single linked list traverses with a single direction. It's not an efficient way to find in finding a node. 
* A double-linked list can visit nodes back and forth, which is much more convenient.
* A double-linked list contains values and pointers pointing to the previous node (blue arrow), and the pointer points to the next node (red arrow).

<img src = "https://hackmd.io/_uploads/BJR2a1sXR.png" width = 50% style="display:block; margin: auto;">
</br>

> * Define double linked list structure
```c 
// define a double linked list node
Typedef struct dllist
{
    dataType value;
    Struct dllist* prev;// previous node's address
    Struct dllist* next;// the next node's address
}dllnode;

```

## Hashing and hash tables
A hash function is an algorithm that reduces a larger value to something small and predictable. Generally, this function takes in an item you wish to add to your hash table and returns an integer representing the array index in which the item should be placed. The hash table combines array and linked lists. 

* An example of hash table: 

<img src = "https://hackmd.io/_uploads/rkDS6Zs7A.png" width = 90% style="display:block; margin: auto;">
</br>

* Collisions: When adding a new word to the hashed location but finds it already had value in 
that space.
* A linked list can store the same indexed values on the hashed location to prevent collisions.

<img src = "https://hackmd.io/_uploads/HJYMAWsQA.png" width = 90% style="display:block; margin: auto;">
</br>

## Tree

<img src = "https://hackmd.io/_uploads/SykTMRR70.png" style="display:block; margin: auto;"></br>

* A tree consists of many intersection points(roots), considered as a combination of subtrees. The number of sub-trees in a root is called the degree of the node. For example, root 1 has two sub-trees having two degrees of the node. Root 2 has three degrees of the node. The root 3 only has one degree of the node. The height/depth/degree of this tree is three.
</br></br></br>

<img src = "https://hackmd.io/_uploads/HkrTOcpXC.png" style="display:block; margin: auto;"></br>

* A data structure in which trees are mutually exclusive but connected through nodes is called a forest. The figure below shows two mutually exclusive trees: T1 and T2.

</br>

* Binary tree
    Each node in the binary tree data structure has at most two child nodes (child nodes), which are called the left child node and the right child node.

* Traversal(走訪/遍歷):

<img src = "https://hackmd.io/_uploads/SyCMwG1NA.png" style="display:block; margin: auto;">

1. Inorder traversal:(中序走訪)

    DBGEHACFI

2. Preorder traversal(前序走訪)

    ABDEGHCFI

3. Postorder traversal(後序走訪)

    DGHEBIFCA

## Tries:
<img src = "https://hackmd.io/_uploads/HJHKf2pQR.png" width = 90% style="display:block; margin: auto;"></br>

* If we want to find the word "TOAD" in the tries data structure, we have to enter the first level of tries to find the letter "T", start from the letter "T" and enter the next level of tries to try to find the letter "O",... The disadvantage is the waste of memory.

```python
// demonstrate trie in python @Murky
class Node:
    def __init__(self):
        self.isWord = False
        self.children = dict()

class Trie:

    def __init__(self):
        self.root = Node()
        

    def insert(self, word: str) -> None:
        cur = self.root

        for c in word:
            if c not in cur.children:
                cur.children[c] = Node()
            cur = cur.children[c]
        cur.isWord = True
        
    def search(self, word: str) -> bool:
        cur = self.root

        for c in word:
            if c not in cur.children:
                return False
            cur = cur.children[c]
        return cur.isWord
        

    def startsWith(self, prefix: str) -> bool:
        cur = self.root

        for c in prefix:
            if c not in cur.children:
                return False
            cur = cur.children[c]
        return True


```

---

## P-Sets
* ### [**Inheritance**](https://cs50.harvard.edu/x/2024/psets/5/inheritance/)
In problem Inheritance, it's asked to generate 3 generations' blood types randomly, including child to parents and their grandparents. </br>

* Expected output
<img src = "https://hackmd.io/_uploads/rJolDh6mA.png" style="display:block; margin: auto;">
* Steps
0. Define a person's structure. A person has two parents and a pair of alleles.
1. Create 3 generation family
2. Randomly determine their blood type
3. Print the result
4. Free memory allocated.

```c
// Define a person's struct.
typedef struct person
{
    struct person *parents[2];
    char alleles[2];
}person;
```

1. A child has two parents</br>
<img src = "https://hackmd.io/_uploads/BkR77JJ4A.png" width=60% style="display:block; margin: auto;">
</br>

2. Parent 0 and Parent1 also have their parents</br>

<img src = "https://hackmd.io/_uploads/Hy84X1yVA.png" width=60% style="display:block; margin: auto;">
</br>

3. Since we only calclulate 3 generations in this problem, set grandparents' parents to NULL

<img src = "https://hackmd.io/_uploads/ryjHXkkER.png" width=60% style="display:block; margin: auto;">
</br>



```c
// recursively create family generation by generation
Const int generations = 3;

if (generations > 1)
{
    // Create two new parents for current person 
    // by recursively calling create_family()
    // parent0 has his/her family
    person *parent0 = create_family(generations - 1);
    // parent1 has his/her family
    person *parent1 = create_family(generations - 1);

    ....
)
        
// if generation = 1, means creating grandparents
// since we only create 3 generations in this problem
// set grandparents' parents to NULL        
else
{

    new_person->parents[0] = NULL;
    new_person->parents[1] = NULL;
    // And randomly assign their alleles, 
    // and their child randomly inheritant one of the pair alleles.
    p->alleles[0] = random_allele();
    p->alleles[1] = random_allele();
}

```
The function random_allele( ) returns one in the pair of blood type alleles: 'A', 'B', or 'O'. Use rand( ) and rand ( ) randomly assign it.

* Free allocated memory before exiting: Tree traversal
Node 1 to Node 7 are the nodes we want to free. (In the code the node denotes as *p)

<img src = "https://hackmd.io/_uploads/BJhorZ1VR.png" width=65% style="display:block; margin: auto;">
</br>

* If we reach the end of the tree, which are grandparents nodes, grandparents nodes don't have parent[0], parent[1]. If conditional statements detect that a person's parent[0] and parent[1] are NULL, then start freeing nodes. Otherwise, keep calling the function free-family() to free nodes.
* Nodes start freeing from :
    node 1 -> node2 -> node 3 -> node 4 -> node 5 -> node 6 -> node 7 as shown below. The debug tool is your friend to observe calling system stack.

![image](https://hackmd.io/_uploads/HkcSHZyN0.png)

```c
void free_family(person *p)
{
    // Initialization
    person *p0 = NULL;
    person *p1 = NULL;
    // If detect grandparents' parents
    // which is NULL since only count 3 generations in this problem
    if (p == NULL)
    {
        return;
    }
    
    // reassign current person's parents
    p0 = p->parent[0]; 
    p1 = p->parent[1];
    // free parent[0], and their parents
    free_family(p0);
    // free parent[1], and their parents
    free_family(p1);
    
    // free the child
    free(p);   
}
```
---

## Resources

1. Fundamental of datastuctures,  CHEN,HUEI-JHEN, 2008.05
2. cs50 week 5 notes










