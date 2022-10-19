# Add Two Number Represented By linked list

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


// &head - pass by reference of type Node*
void insertAtStart(Node* &head ,  int data){
    // created another node
    Node* node = new Node(data);
    
    // pointed node to head
    node->next = head;
    
    // created new node as a head node 
    head = node;
    
}

void insertAtTail(Node* &tail , int data){
    
    Node* temp = new Node(data);
    tail->next = temp;
    tail = temp;
    
}


int returnInNumber(Node* head){
        Node* temp = head;
        
        // if linked list is null return 0
        if(temp == NULL)
            return 0;
            
            
        // linked list in number form is stored in ans        
        int ans = 0;
        while(temp != NULL){
            ans = temp->data + ans*10;
            temp = temp->next;
        }
        
        return ans;
        
}



void printNodes(Node* &head ){
    
    Node* temp = head;
    while(temp->next != NULL){
        
        cout<< temp->data << " ";
        temp = temp->next;
        
        
    }
    
    cout<< temp->data;;


}


int main() {
    
  
   // first linked list 
   Node* node1 = new Node(1);
   Node* head1 = node1;
   Node* tail1 = node1;
   
   insertAtTail(tail1 , 2);
   insertAtTail(tail1 , 3);
   
   // second linked list
   Node* node2 = new Node(1);
   Node* head2 = node2;
   Node* tail2 = node2;
   
   insertAtTail(tail2 , 5);
   
   
    
   // returnInNumber function return linked list element in integer form 
   int num1 = returnInNumber(head1);
   int num2 = returnInNumber(head2);
       
   int ans = num1 + num2;
    
    cout<< endl;

    
    // create ans linked list in which insertion is done at head
    
    // last number of ans is stored in ans linked list
    Node* ansNode = new Node( ans%10);
    ans = ans/10;
 
    Node* ansHead = ansNode;
    
    while(ans != 0){
        
        insertAtStart(ansHead ,  ans%10);
        ans = ans / 10;
        
    }
    
    printNodes(ansHead);
    
    cout<< endl ;
   
 
}


```