# minor-project
Minor Project in C code to handle the various operations of the data structures Stack and

Queue with their separate operations like the provided screen layout.a) Choose Your Data Structure: -
1.stack
2.queue

b) If Choose Stack: -
1.push
2.pop
3.display
4.exit

c) If Choose Queue:
1.Enqueue
2.Dequeue
3.Display
4.Back to main menu
solution:
#include <stdio.h>
#include <stdlib.h>

#define SIZE 5

// Stack Implementation
int stack[SIZE], top = -1;
void push() {
    if (top == SIZE - 1)
        printf("Stack Overflow!\n");
    else {
        int val;
        printf("Enter value to push: ");
        scanf("%d", &val);
        stack[++top] = val;
    }
}
void pop() {
    if (top == -1)
        printf("Stack Underflow!\n");
    else
        printf("Popped: %d\n", stack[top--]);
}
void displayStack() {
    if (top == -1)
        printf("Stack is empty!\n");
    else {
        printf("Stack: ");
        for (int i = top; i >= 0; i--)
            printf("%d ", stack[i]);
        printf("\n");
    }
}

// Queue Implementation
int queue[SIZE], front = -1, rear = -1;
void enqueue() {
    if (rear == SIZE - 1)
        printf("Queue Overflow!\n");
    else {
        int val;
        printf("Enter value to enqueue: ");
        scanf("%d", &val);
        if (front == -1) front = 0;
        queue[++rear] = val;
    }
}
void dequeue() {
    if (front == -1 || front > rear)
        printf("Queue Underflow!\n");
    else
        printf("Dequeued: %d\n", queue[front++]);
}
void displayQueue() {
    if (front == -1 || front > rear)
        printf("Queue is empty!\n");
    else {
        printf("Queue: ");
        for (int i = front; i <= rear; i++)
            printf("%d ", queue[i]);
        printf("\n");
    }
}

int main() {
    int choice, subChoice;
    while (1) {
        printf("\nChoose Data Structure:\n1. Stack\n2. Queue\n3. Exit\n");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                while (1) {
                    printf("\nStack Operations:\n1. Push\n2. Pop\n3. Display\n4. Exit\n");
                    scanf("%d", &subChoice);
                    if (subChoice == 1) push();
                    else if (subChoice == 2) pop();
                    else if (subChoice == 3) displayStack();
                    else break;
                }
                break;
            case 2:
                while (1) {
                    printf("\nQueue Operations:\n1. Enqueue\n2. Dequeue\n3. Display\n4. Back to main menu\n");
                    scanf("%d", &subChoice);
                    if (subChoice == 1) enqueue();
                    else if (subChoice == 2) dequeue();
                    else if (subChoice == 3) displayQueue();
                    else break;
                }
                break;
            case 3:
                exit(0);
            default:
                printf("Invalid choice! Try again.\n");
        }
    }
    return 0;
}
