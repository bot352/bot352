AIM: Write a program to store the elements in a 1-D array and perform the operations like searching, sorting, reversing the elements.

PROGRAM CODE:
#include <stdio.h>  // No need for conio.h in modern compilers 

int arr[20], size; // a global variable of array and size is declared.

//Function Prototypes getting declared to carry out operations.
void disp(); // works to print array
void sort(); // works to sort the array
void reverse(); // works to reverse array 
void search(int val); // works to find the element of array given by user whether it exists or not.

int main() {
    int ch, val; // variables declared( ch for taking user Menu choice and val for the element to search in a array.)
    
    printf("Enter array size: ");
    scanf("%d", &size); //1st user input stm asking no. of Elements they want to store i.e size.

    printf("Enter %d elements: ", size);
    for(int i = 0; i < size; i++)  
        scanf("%d", &arr[i]); // 2nd User input stm taking array elements one-by-one in a linear manner reading form into arr[i] using for-loop to take repetitive element from user.

    do {
        printf("\n**** Menu ****\n");
        printf("1.Display  2.Sort  3.Reverse  4.Search  5.Exit\n"); //Display Menu list consisting names of operations performed further Using do while loop until Exit.
        printf("Enter choice: ");
        scanf("%d", &ch); // 3rd user input asking for the choice i.e which operation to be performed among the Menu list displayed above.

        switch(ch) { 
//handling user choices of selecting the operations to be performed using switch case
            case 1: disp(); break;
            case 2: sort(); break;
            case 3: reverse(); break;
            case 4: 
                printf("Enter value to search: ");
                scanf("%d", &val);
                search(val); 
                break;
            case 5: return 0;
            default: printf("Invalid choice! Try again.\n");
        }
    } while(1);  // No syntax error, but ensuring infinite loop until choice is 5
}

// Function to display array elements
void disp() {
    printf("Array: ");
    for(int i = 0; i < size; i++)  
        printf("%d ", arr[i]);
    printf("\n");
} // this Function consist of methods for operation to display each element in one line using for loop.


// Function to sort array using Bubble Sort
void sort() {
for(int i = 0; i < size - 1; i++) {                     for(int j = 0; j < size - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    printf("Sorted ");
    disp();
}

// Function to reverse the array
void reverse() {
    for(int i = 0, j = size - 1; i < j; i++, j--) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    printf("Reversed ");
    disp();
}

// Function to search for an element in the array
void search(int val) {
    for(int i = 0; i < size; i++) {
        if(arr[i] == val) {
            printf("Value found at position %d.\n", i);
            return;
        }
    }
    printf("Value not found.\n");
}
AIM: Read the two arrays from the user and merge them and display the elements in sorted order.

PROGRAM CODE:
#include <stdio.h>// header file, no need of getch() and conio.h 

void mergeAndSort(int arr1[], int size1, int arr2[], int size2, int arr3[]);
// thus is a function Prototype which will tell the compiler that we will define mergeAndSort() later in the program.

int main() {
    int arr1[20], arr2[20], arr3[40];
    int i, size1, size2;
// here arr1[20] , arr2[20] ate 2 arrays which will store a set of elements for 1st and 2nd array input by user.

//arr3[40] is the merged array in Which the size of arr1 and size of arr2 will get add i.e arr[40]=arr[20]+arr[20]


 // 1st input stm taking input for first array
    printf("Enter the size of array 1: ");
    scanf("%d", &size1);
    printf("Enter %d elements in array 1:\n", size1);
    for(i = 0; i < size1; i++)
        scanf("%d", &arr1[i]);

// 2nd input stm taking input for second array
    printf("Enter the size of array 2: ");
    scanf("%d", &size2);
    printf("Enter %d elements in array 2:\n", size2);
    for(i = 0; i < size2; i++)
        scanf("%d", &arr2[i]);

//this is a function call which will merge both arrays taken input into arr3[] and sorts it.
   mergeAndSort(arr1, size1, arr2, size2, arr3);

    // Displaying merged sorted array
    printf("Merged and Sorted Array:\n");
    for(i = 0; i < size1 + size2; i++)
        printf("%d ", arr3[i]);
    printf("\n");
// this will loop through arr3[] and print all the element In sorted order.
    return 0;
}

// Function to merge and sort two arrays
void mergeAndSort(int arr1[], int size1, int arr2[], int size2, int arr3[]) {
    int i, j, k, temp;

    // Copying elements of both arrays into arr3
    for(i = 0; i < size1; i++)
        arr3[i] = arr1[i]; // cpy arr1 elements to arr3
    for(j = 0; j < size2; j++)
        arr3[size1 + j] = arr2[j]; // cpy arr2 elements to arr3

//till here arr3[] contains all elements from both array but still not sorted 

    // Sorting the merged array using Bubble Sort
    for(i = 0; i < (size1 + size2) - 1; i++) {
        for(j = 0; j < (size1 + size2) - i - 1; j++) {
            if(arr3[j] > arr3[j + 1]) {
                temp = arr3[j];
                arr3[j] = arr3[j + 1];
                arr3[j + 1] = temp;
            }
        }
    }
}
Write a program to create a singly linked list and display the node elements in reverse order

PROGRAM CODE: 💢💢This is a C++ program not C program!!!!!💢💢

#include <iostream>
using namespace std;

// Node class representing a single element in the linked list
class Node {
public:
    int data;   // Stores the value of the node
    Node* next; // Pointer to the next node in the list

    // Constructor to initialize a new node with a given value
    Node(int val) {
        data = val;
        next = nullptr; // Initially, next is set to NULL
    }
};


// LinkedList class to manage the linked list operations
class LinkedList {
private:
    Node* head; // Pointer to the first node (head) of the list

public:
    // Constructor to initialize an empty list
    LinkedList() {
        head = nullptr;
    }

    // Function to create a linked list by inserting multiple values
    void create() {
        int val;
        cout << "Enter values (-1 to stop): ";
        while (true) {
            cin >> val; // Take input from the user
            if (val == -1) break; // Stop when -1 is entered
            insertAtEnd(val); // Insert the value at the end of the list
        }
        cout << "List created successfully.\n";
    }

    // Function to insert a new node at the end of the linked list
    void insertAtEnd(int val) {
        Node* newNode = new Node(val); // Create a new node with the given value

        // If the list is empty, make newNode the head
        if (head == nullptr) {
            head = newNode;
        } else {
            Node* temp = head; // Start from the head
            while (temp->next != nullptr) // Traverse to the last node
                temp = temp->next;
            temp->next = newNode; // Attach the new node at the end
        }
    }

    // Function to display the linked list elements
    void display() {
        if (head == nullptr) { // If the list is empty
            cout << "List is empty.\n";
            return;
        }

        Node* temp = head; // Start from the head
        cout << "List: ";
        while (temp != nullptr) { // Traverse through the list
            cout << temp->data << " "; // Print each node's value
            temp = temp->next; // Move to the next node
        }
        cout << endl;
    }

    // Function to reverse the linked list
    void reverse() {
        Node* prev = nullptr; // Previous node starts as NULL
        Node* current = head; // Start from the head
        Node* nextNode = nullptr; // Pointer to store the next node

        while (current != nullptr) { // Loop until we reach the end
            nextNode = current->next; // Store the next node
            current->next = prev; // Reverse the link (point current node to previous)
            prev = current; // Move previous forward (prev becomes current)
            current = nextNode; // Move current forward (current becomes nextNode)
        }
        head = prev; // After the loop, prev will be the new head
    }

    // Function to display the list in reverse order
    void displayReverse() {
        reverse(); // First, reverse the list
        cout << "Reversed ";
        display(); // Then, display the reversed list
    }

    // Destructor to free memory and avoid memory leaks
    ~LinkedList() {
        Node* temp;
        while (head != nullptr) { // Loop through all nodes
            temp = head; // Store the current head
            head = head->next; // Move head to the next node
            delete temp; // Delete the old head
        }
    }
};


// Main function 
int main() {
    LinkedList list; // Create an object of LinkedList class

    list.create(); // Create the linked list by taking user input
    list.display(); // Display the list
    list.displayReverse(); // Display the list in reverse order

    return 0; // End of the program
}
AIM : Write a program to search the elements in the linked list and display the same.

PROGRAM CODE:💢💢This is a C++ program not C program!!!!!💢💢

#include <iostream> 
using namespace std;

// Node class representing a single element in the linked list
class Node {
public:
    int data;   // Stores the value of the node
    Node* next; // Pointer to the next node

    // Constructor to initialize a new node with a given value
    Node(int val) : data(val), next(nullptr) {}
};

// LinkedList class to manage the list operations
class LinkedList {
private:
    Node* head; // Pointer to the first node of the list

public:
    // Constructor initializes an empty list
    LinkedList() : head(nullptr) {}

    // Function to insert a new node at the end of the linked list
    void insert(int val) {
        Node* newNode = new Node(val); // Create a new node with the given value

        if (!head) head = newNode; // If the list is empty, set head to newNode
        else {
            Node* temp = head; // Start from head
            while (temp->next) temp = temp->next; // Traverse to last node
            temp->next = newNode; // Attach newNode at the end
        }
    }

    // Function to display the linked list elements
    void display() {
        for (Node* temp = head; temp; temp = temp->next) // Traverse the list
            cout << temp->data << " "; // Print each node's value
        cout << endl;
    }

    // Function to search for an element in the linked list
    void search(int val) {
        int pos = 1; // Position counter
        for (Node* temp = head; temp; temp = temp->next, pos++) {
            if (temp->data == val) { // If value is found
                cout << "Found at node " << pos << endl;
                return;
            }
        }
        cout << "Not found\n"; // If value is not found
    }

    // Destructor to free memory when the object is destroyed
    ~LinkedList() {
        while (head) { // Traverse the list
            Node* temp = head; // Store current head
            head = head->next; // Move head to next node
            delete temp; // Delete previous head node
        }
    }
};


int main() {
    LinkedList list; // Create an object of LinkedList class
    int val;

    // Creating the linked list by taking user input
    cout << "Enter values (-1 to stop): ";
    while (cin >> val && val != -1) // Take input until -1 is entered
        list.insert(val); // Insert values into the list

    // Display the list
    cout << "List: ";
    list.display();

    // Searching for an element in the list
    cout << "Enter value to search: ";
    cin >> val;
    list.search(val);

    return 0; // End of the program
}
AIM:Write a program to create double linked list and sort the elements in the linked list.

PROGRAM CODE:-💢💢This is a C++ program not C program!!!!!💢💢

#include <iostream>
using namespace std;

// Node class representing a single element in the doubly linked list
class Node {
public:
    int value;    // Stores the value of the node
    Node* next;   // Pointer to the next node
    Node* prev;   // Pointer to the previous node

    // Constructor to initialize a new node
    Node(int val) : value(val), next(nullptr), prev(nullptr) {}
};

// DoublyLinkedList class to manage the list operations
class DoublyLinkedList {
private:
    Node* head; // Pointer to the first node of the list

public:
    // Constructor initializes an empty list
    DoublyLinkedList() : head(nullptr) {}

    // Function to create a doubly linked list by inserting multiple values
    void createList() {
        int val;
        cout << "Enter values (-1 to stop): ";
        while (cin >> val && val != -1) {
            addNode(val); // Insert the value at the end of the list
        }
        cout << "Doubly Linked List created successfully.\n";
    }

    // Function to insert a new node at the end of the list
    void addNode(int val) {
        Node* newNode = new Node(val); // Create a new node with the given value

        if (!head) { // If the list is empty, set head to newNode
            head = newNode;
        } else {
            Node* temp = head;
            while (temp->next) temp = temp->next; // Traverse to the last node
            temp->next = newNode; // Attach newNode at the end
            newNode->prev = temp; // Set previous pointer
        }
    }

    // Function to display the linked list elements
    void displayList() {
        if (!head) {
            cout << "List is empty.\n";
            return;
        }

        Node* temp = head;
        cout << "Doubly Linked List: ";
        while (temp) { // Traverse and print the list
            cout << temp->value << " ";
            temp = temp->next;
        }
        cout << endl;
    }

    // Function to sort the doubly linked list (Bubble Sort)
    void sortList() {
        if (!head) return; // If list is empty, no need to sort

        for (Node* i = head; i; i = i->next) {
            for (Node* j = i->next; j; j = j->next) {
                if (i->value > j->value) { // Swap if not in order
                    swap(i->value, j->value);
                }
            }
        }
    }

    // Destructor to free memory and avoid memory leaks
    ~DoublyLinkedList() {
        while (head) {
            Node* temp = head;
            head = head->next;
            delete temp;
        }
    }
};


int main() {
    DoublyLinkedList list; // Create an object of DoublyLinkedList class

    list.createList(); // Create the linked list by taking user input
    list.displayList(); // Display the list

    cout << "Sorted List:\n";
    list.sortList(); // Sort the list
    list.displayList(); // Display the sorted list

    return 0; // End of the program
}
AIM :  Write a program to implement the concept of stack with Push, Pop, Display and exit operation.

PROGRAM CODE:

#include <stdio.h>
#define MAX 30

int stack[MAX], top = -1;

void push();
void pop();
void peek();
void display();

int main() {
    int choice;
    do {
        printf("\n**** Main Menu ****\n");
        printf("1. Push\n2. Pop\n3. Peek\n4. Display\n5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1: push(); break;
            case 2: pop(); break;
            case 3: peek(); break;
            case 4: display(); break;
            case 5: printf("Exiting...\n"); break;
            default: printf("Invalid choice! Try again.\n");
        }
    } while (choice != 5);
    return 0;
}

void push() {
    if (top == MAX - 1) 
        printf("Stack is full.\n");
    else {
        printf("Enter value to push: ");
        scanf("%d", &stack[++top]);
        printf("Successfully pushed.\n");
    }
}

void pop() {
    if (top == -1) 
        printf("Stack is already empty.\n");
    else {
        printf("Popped value: %d\n", stack[top--]);
            }
}

void peek() {
    if (top == -1) 
        printf("Stack is empty.\n");
    else {
        printf("Topmost element: %d\n", stack[top]);
           }
}

void display() {
    if (top == -1) 
        printf("Stack is empty.\n");
    else {
        printf("Stack: ");
        for (int i = top; i >= 0; i--) 
            printf("%d ", stack[i]);
        printf("\n");
    }
}
AIM :  Write a program to implement bubble sort.

PROGRAM CODE:

#include <stdio.h>

// Function prototypes
void bubbleSort(int arr[], int n);
void display(int arr[], int n);

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};  
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original array: ");
    display(arr, n);

    bubbleSort(arr, n);  // Function call

    printf("Sorted array: ");
    display(arr, n);

    return 0;
}

// Function to perform Bubble Sort
void bubbleSort(int arr[], int n) {
    int i, j, temp;
    for (i = 0; i < n - 1; i++) {  
        for (j = 0; j < n - i - 1; j++) {  
            if (arr[j] > arr[j + 1]) {  
// Swap if element is greater than next
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

// Function to display the array
void display(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
AIM :  Write a program to implement selection sort.

PROGRAM CODE:

#include <stdio.h>

// Function prototypes
void selectionSort(int arr[], int n);
void display(int arr[], int n);

int main() {
    int arr[] = {29, 10, 14, 37, 13};  
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original array: ");
    display(arr, n);

    selectionSort(arr, n);  // Function call

    printf("Sorted array: ");
    display(arr, n);

    return 0;
}

// Function definition to perform Selection Sort
void selectionSort(int arr[], int n) {
    int i, j, minIndex, temp;
    for (i = 0; i < n - 1; i++) {  
        minIndex = i;
        for (j = i + 1; j < n; j++) {  
            if (arr[j] < arr[minIndex]) {  
                minIndex = j;  // Update index of minimum element
            }
        }
        // Swap if a smaller element is found
        if (minIndex != i) {
            temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }
}

// Function definition display the array
void display(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
AIM :  Write a program to implement merge sort.

PROGRAM CODE:💢💢This is a C++ program not C program!!!!!💢💢

#include <iostream>
using namespace std;

// MergeSort class to handle sorting
class MergeSort {
public:
    // Function to perform merge sort
    void sort(int arr[], int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            sort(arr, left, mid);      // Sort left half
            sort(arr, mid + 1, right); // Sort right half
            merge(arr, left, mid, right);
        }
    }

private:
    // Function to merge two sorted halves
    void merge(int arr[], int left, int mid, int right) {
        int temp[right - left + 1], i = left, j = mid + 1, k = 0;

        while (i <= mid && j <= right)  
            temp[k++] = (arr[i] < arr[j]) ? arr[i++] : arr[j++];

        while (i <= mid) temp[k++] = arr[i++];
        while (j <= right) temp[k++] = arr[j++];

        for (i = left, k = 0; i <= right; i++, k++)  
            arr[i] = temp[k];  
    }
};

int main() {
    int arr[] = {38, 27, 43, 3, 9, 82, 10};
    int n = sizeof(arr) / sizeof(arr[0]);

    MergeSort sorter; // Create an object of the MergeSort class
    sorter.sort(arr, 0, n - 1);

    cout << "Sorted Array: ";
    for (int num : arr) cout << num << " ";
    cout << endl;

    return 0;
}

