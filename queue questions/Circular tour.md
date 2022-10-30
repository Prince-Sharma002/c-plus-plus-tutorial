#  Circular tour

```c++

int tour(petrolPump p[],int n)
    {
       
       int balance = 0;
       int deficit = 0;
       int start = 0;
       
       for(int i=0 ; i<n ; i++){
           
           balance = balance + p[i].petrol - p[i].distance;
           
           // if balance is negative start move next to current ith position and  
           // deficit stored value of current total deficient petrol
           if(balance < 0){
               
               deficit += balance;
               start = i+1;
               
               // set balance again zero and traversal starts from i+1
               balance = 0;
               
           }
           
       }
       
       // if deficient + balance greater than or equal to zero that means circular can be complete 
       if(deficit + balance >= 0)
           return start;
       else
           return -1;    
       
   
    }

```