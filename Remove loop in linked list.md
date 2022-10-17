# Remove loop in Linked List

```c++

Node *removeLoop(Node *head)
{

    // If linked list is empty
    if(head == NULL){
        return NULL;
    }
    
    
        
    Node* temp = head;

    // create map that will check if traversed element is already visited
    map<Node* , bool > visited ;
    
    while(temp != NULL){
        

        // if visited is true it means there is loop exist
        if(visited[temp->next] == true){
            
            // point temp to null to remove loop
            temp -> next = NULL;
            return head;
        }
        
        visited[temp] = true;
        temp = temp->next;
        
    }
    
    return head;
    
  
}


```