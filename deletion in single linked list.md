
# DELETION IN SINGLE LINKED LIST




```c++

              

// Online C++ compiler to run C++ program online
#include <iostream>
using namespace std;

class Node{
  
  public:
  int data;
  Node* next;  // creating a pointer pointing to a node

  Node( int data){
      
      this->data = data;
      this->next = NULL;    // creating a single node constructor pointing to null
      
  }  
    
};

void deleteHead(Node* &head ){
    
    Node* temp = head;
    head = temp->next;
    delete temp;
    
}


void deleteByValue(Node* &head , int value){
    
    // empty linked list 
    if(head == NULL){
        return ;
    }
    
    // delete single node linked list
    if(head->next == NULL){
        deleteHead(head);
        return ;
    }
    
    // delete head node
    if(value == head->data){
        deleteHead(head);
        return ;
    }
    
    // other cases
    Node* temp = head;
    while(temp->next->data != value)
        temp = temp->next;
        
    // first create an temp object
    Node* tempNode = temp->next;
    temp->next = tempNode->next;
    delete tempNode;
  
}


void insertAtTail(Node* &tail , int data){
    
    Node* newNode = new Node(data);
    tail->next = newNode;
    tail = newNode;
    
    return ;
    
}



void print(Node* &head ){
    
    if(head == NULL){
        cout<< "empty" <<endl;
        return ;
    }
    
    Node* temp = head;
    while(temp->next != NULL){
        
        cout<< temp->data << " ";
        temp = temp->next;
       
    }
    
    cout<< temp->data << endl;

}



int main() {
    
   Node* node1 = new Node(1);
   
   Node* head = node1;
   Node* tail = node1;
   
   insertAtTail( tail , 2 );
   insertAtTail( tail , 3 );
   insertAtTail( tail , 4 );
   insertAtTail( tail , 5 );
   insertAtTail( tail , 6 );
   insertAtTail( tail , 7 );

   deleteByValue(head , 1);
     
   print(head);
    
}


```