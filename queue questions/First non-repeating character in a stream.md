#  First non-repeating character in a stream

```c++

string FirstNonRepeating(string A){
		    
		    // use map for count character occurence
		    unordered_map<char , int > count;
		    
		    
		    queue < char > q;
		    
		    // answer is stored in ans string
		    string ans = "";
		    
		    
		    for(int i=0 ; i<A.length() ; i++){
		        
		        char ch = A[i];
		        
		        // count number of character occurence
		        count[ch]++;
		        
		        q.push(ch);
		        
		        while(!q.empty()){
		            
		            // if count greater than 1 that means we need to put "#" 
		            if( count[q.front()] > 1 ){
		                q.pop();
		            }
		            // if count is less than or equal to one that means first element of queue would stored in ans
		            else{
		                ans.push_back(q.front());
		                break;
		            }
		            
		        }
		        
		        // if queue is empty that means occurence of that character is greater than one
		        if(q.empty() ){
		            ans.push_back('#');
		        }
		        
		    }
		    return ans;
		    
		    
		    
		}

```