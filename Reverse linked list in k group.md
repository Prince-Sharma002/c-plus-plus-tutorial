# Reverse Linked List in K Group ( Problem )

```c++


Node* kReverse(Node* head, int k) {
  

    // if linked list is empty or having a single element 
    if(head == NULL || head-> next == NULL )
        return head;
    
    
    // creating pointers
    Node* prev =  NULL;
    Node* curr = head;
    Node* forw = NULL;
    
    
    
    // reverse first k element 
    int c = 0;
    while( c < k && curr != NULL){
        
        forw = curr -> next;
        curr -> next = prev;
        prev = curr;
        curr = forw;
        
        c++;
        
    }
    
    
    // recursive call for reversing next k element having head is prev of next reverse linked list
    if(curr != NULL){
        head -> next = kReverse(forw , k);
    }
    
    return prev;
  
}


```