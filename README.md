# reversingly
#include <iostream>
using namespace std;

class node {
public:
    int data;
    node *next;

    node(int data) {
        this->data = data;
        this->next = nullptr;
    }
};

void print(node *head) {
    if (head == nullptr) {
        cout << "Empty linked list." << endl;
    } else {
        node *p = head;
        while (p != nullptr) {
            cout << p->data << " ";
            p = p->next;
        }
        cout << endl;
    }
}

void insert(node*& head, int data) {
    node *newNode = new node(data);

    if (head == nullptr) {
        head = newNode;
    } else {
        node *temp = head;
        while (temp->next != nullptr) {
            temp = temp->next;
        }
        temp->next = newNode;
    }
}

void reverse(node *& head){
    if(head == nullptr || head->next == nullptr){
        cout << "Empty or single node linked list." << endl;
        return;
    }

    node* cur = head;
    node* prev = nullptr;
    node* next = nullptr;

    while(cur != nullptr){
        next = cur->next;
        cur->next = prev;
        prev = cur;
        cur = next;
    }

    head = prev;
}

int main() {
    node* head = nullptr;
    int x;
    cout << "Enter the number of nodes: ";
    cin >> x;

    int data;
    for (int i = 1; i <= x; i++) {
        cout << "Enter data for node " << i << ": ";
        cin >> data;
        insert(head, data);
    }

    cout << "Original linked list: ";
    print(head);

    reverse(head);

    cout << "Reversed linked list: ";
    print(head);

    return 0;
}

output: 
Enter the number of nodes: 7
Enter data for node 1: 1
Enter data for node 2: 2
Enter data for node 3: 3
Enter data for node 4: 4
Enter data for node 5: 5
Enter data for node 6: 6
Enter data for node 7: 7
Original linked list: 1 2 3 4 5 6 7      
Reversed linked list: 7 6 5 4 3 2 1   
