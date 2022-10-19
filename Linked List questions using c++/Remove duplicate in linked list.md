# Remove Duplicate Nodes in Linked List

```c++

// Online C++ compiler to run C++ program online
#include <iostream>
#include <array>
#include <vector>
#include <map>
#include <string>
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


void removeDuplicate(Node* &head){
    
    
    Node* curr = head;
  
    Node* temp = head;
    
    
    // map variable is use to map integer with boolean value
    map<int , bool> visited;
    
    visited[temp->data] = true;
   
    while(temp->next != NULL){
        
        visited[temp->data] = true;
        
        
        // if inside visited map boolean value is true it means that integer is present already
        // Now we have to  delete that same value integer.
        if(visited[temp->next->data] == true){
            
            Node* next_next = temp->next->next;
            Node* todelete = temp->next;
            
            temp->next = next_next;
            delete todelete;
             
        }
        
        // if in visited map boolean value is false it means that integer is present only
        // at once time at that moment
        else{
            
            temp = temp->next;
            
        }
        

    }
    
    
}






void insertAtTail(Node* &tail , int data , Node* &head){
    
    Node* temp = new Node(data);
    tail->next = temp;
    tail = temp;
  
}




void print(Node* &head ){
    
    Node* temp = head;
    while(temp->next != NULL){
        
        cout<< temp->data << " ";
        temp = temp->next;
    }
    
    cout<< temp->data << endl;

}



int main() {
   
   // insert data inside linked list 
   Node* node1 = new Node(1);
   
   Node* head  = node1;
   Node* tail = node1;
   
   insertAtTail(tail , 3 , head);
   insertAtTail(tail , 3 , head);
   insertAtTail(tail , 3 , head);
   insertAtTail(tail , 5 , head);
   insertAtTail(tail , 3 , head);
   insertAtTail(tail , 2 , head);
   insertAtTail(tail , 3 , head);
   insertAtTail(tail , 2 , head);
  

  // remove duplicate integer function
  removeDuplicate(head);
   
   
  // print linked list 
  print(head);
   
   

   
    
    
    
    
}


```