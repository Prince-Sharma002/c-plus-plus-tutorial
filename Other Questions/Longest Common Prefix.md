# Longest Common Prefix

```c++

string longestCommonPrefix(vector<string> &arr, int n)
{
    bool isMatch = true;
    
    for( int i=0 ; i< arr[0].size() ; i++ ){
        char ch = arr[0][i];
        

        for( int j=1 ; j<n ; j++){
            
            if( arr[j][i] == ch ){
                isMatch = true;
            }
            else{
                isMatch = false;
                break;
            }
            
        } 
        
        
        if( isMatch == false){
            return arr[0].substr(0 , i);
        }
        
    }
    
}


```