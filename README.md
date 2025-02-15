# Linked-List-Stack-Queue
Implement Singly and Doubly linked list. • Implement a stack using linked list. • Implement a FIFO queue using linked list


class SinglyLinkedList {
    class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; this.next = null; }
    }
    
    private Node head;
    
    void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
        } else {
            Node temp = head;
            while (temp.next != null) temp = temp.next;
            temp.next = newNode;
        }
    }
    
    void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        }
        System.out.println("null");
    }
}

class DoublyLinkedList {
    class Node {
        int data;
        Node prev, next;
        Node(int data) { this.data = data; this.prev = this.next = null; }
    }
    
    private Node head;
    
    void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
        } else {
            Node temp = head;
            while (temp.next != null) temp = temp.next;
            temp.next = newNode;
            newNode.prev = temp;
        }
    }
    
    void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " <-> ");
            temp = temp.next;
        }
        System.out.println("null");
    }
}

class StackUsingLinkedList {
    class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; this.next = null; }
    }
    
    private Node top;
    
    void push(int data) {
        Node newNode = new Node(data);
        newNode.next = top;
        top = newNode;
    }
    
    int pop() {
        if (top == null) throw new RuntimeException("Stack Underflow");
        int value = top.data;
        top = top.next;
        return value;
    }
    
    void display() {
        Node temp = top;
        while (temp != null) {
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        }
        System.out.println("null");
    }
}

class QueueUsingLinkedList {
    class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; this.next = null; }
    }
    
    private Node front, rear;
    
    void enqueue(int data) {
        Node newNode = new Node(data);
        if (rear == null) {
            front = rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
    }
    
    int dequeue() {
        if (front == null) throw new RuntimeException("Queue Underflow");
        int value = front.data;
        front = front.next;
        if (front == null) rear = null;
        return value;
    }
    
    void display() {
        Node temp = front;
        while (temp != null) {
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        }
        System.out.println("null");
    }
}

public class LinkedListStackQueue {
    public static void main(String[] args) {
        // Singly Linked List Test
        SinglyLinkedList sll = new SinglyLinkedList();
        sll.insert(10);
        sll.insert(20);
        sll.insert(30);
        sll.display();
        
        // Doubly Linked List Test
        DoublyLinkedList dll = new DoublyLinkedList();
        dll.insert(40);
        dll.insert(50);
        dll.insert(60);
        dll.display();
        
        // Stack Test
        StackUsingLinkedList stack = new StackUsingLinkedList();
        stack.push(70);
        stack.push(80);
        stack.push(90);
        stack.display();
        System.out.println("Popped: " + stack.pop());
        stack.display();
        
        // Queue Test
        QueueUsingLinkedList queue = new QueueUsingLinkedList();
        queue.enqueue(100);
        queue.enqueue(110);
        queue.enqueue(120);
        queue.display();
        System.out.println("Dequeued: " + queue.dequeue());
        queue.display();
    }
}
