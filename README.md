# stack-with-array

stack.h

class Stack {
private:
    int* array;
    int size;
    int top;

public:
    Stack(int size);
    ~Stack();
    void push(int num);
    void pop();
    bool isFull();
    bool isEmpty();
    int peek();
    void display();
};

imp

#include "Stack.h"
#include <iostream>
using namespace std;

Stack::Stack(int size) {
    array = new int[size];
    this->size = size;
    top = -1;
}

Stack::~Stack() {
    delete[] array;
}

void Stack::push(int num) {
    if (isFull()) {
        cout << "The stack is full. Cannot push " << num << ".\n";
    }
    else {
        top++;
        array[top] = num;
    }
}

void Stack::pop() {
    if (isEmpty()) {
        cout << "The stack is empty. Cannot pop.\n";
    }
    else {
        top--;
    }
}

bool Stack::isFull() {
    return top == size - 1;
}

bool Stack::isEmpty() {
    return top == -1;
}

int Stack::peek() {
    if (!isEmpty()) {
        return array[top];
    }
    else {
        cout << "The stack is empty. No top element.\n";
        return -1;
    }
}

void Stack::display() {
    if (isEmpty()) {
        cout << "The stack is empty.\n";
    }
    else {
        cout << "Stack elements:\n";
        for (int i = top; i >= 0; i--) {
            cout << "array[" << i << "] = " << array[i] << endl;
        }
    }
}


main

#include "Stack.h"
#include <iostream>
using namespace std;

int main() {
    int size, choice, num;

    cout << "Enter the size of the stack: ";
    cin >> size;

    Stack myStack(size);

    do {
        cout << "\n--- Stack Menu ---\n";
        cout << "1. Push\n";
        cout << "2. Pop\n";
        cout << "3. Peek\n";
        cout << "4. Display\n";
        cout << "5. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
        case 1:
            cout << "Enter the number to push: ";
            cin >> num;
            myStack.push(num);
            break;

        case 2:
            myStack.pop();
            break;

        case 3:
            num = myStack.peek();
            if (num != -1) {
                cout << "Top element is: " << num << endl;
            }
            break;

        case 4:
            myStack.display();
            break;

        case 5:
            cout << "Exiting program.\n";
            break;

        default:
            cout << "Invalid choice. Please try again.\n";
        }
    } while (choice != 5);

    return 0;
}
