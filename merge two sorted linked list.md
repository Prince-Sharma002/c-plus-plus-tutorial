# Merge Two Sorted Linked List

```c++

Node<int>* solve(Node<int>* first , Node<int>* second){
  
    
    // if only one element is present in first linked list
    // join it with second linked list
    if(first->next == NULL){
        first->next = second;
        return first;
    }
    
    
    Node<int>* curr1 = first;
    Node<int>* next1 = curr1->next;
    Node<int>* curr2 = second;
    Node<int>* next2 = curr2->next;
    
    
    while(next1 != NULL &&  curr2 != NULL){
        
        if(curr2->data >= curr1->data && curr2->data <= next1->data){
            
            //inserting node from second to first linked list in sorted way
            curr1->next = curr2;
            next2 = curr2->next;
            curr2->next = next1;
            
            // move ahead of pointers
            curr1 = curr2;
            curr2 = next2;
            
            
        }
        // if element of second linked list is greater than next1 element 
        else{
            
            // move ahead of poniter of first linked list
            curr1 = next1;
            next1 = next1->next;
            
            // if first linked list is fully traverse 
            // join end of first linked list with curr2
            if(next1 == NULL){
                curr1->next = curr2;
                return first;
                
            }
            
        }
        
    }
    
     return first;
    
}


// first and second sorted linked list.
Node<int>* sortTwoLists(Node<int>* first, Node<int>* second)
{
   
    if(first == NULL)
        return second;
    
    if(second == NULL)
        return first;
    
    if(first->data <= second->data)
        solve(first , second);
    else
        solve(second , first);
    
    
}


```