# The N - Queens Puzzle

```c++


#include <bits/stdc++.h> 

bool isSafe( int row , int col ,  vector<vector<int>> board , int n ){
    

    int x = row;
    int y = col;

    // check if queen is present in same row of another queen
    while( y >= 0 ){
        
        if( board[x][y] == 1 )
            return false;
        
        y--;
        
    }
    
    
    x = row;
    y = col;
    
    // check if queen presnet in diagonal of another queen
    while( y >= 0 && x>=0 ){
        
        if( board[x][y] == 1 )
            return false;
        
        y--;
        x--;
      
        
    }
    
    x = row;
    y = col;
    
    while( y >= 0 && x<n ){
        
        if( board[x][y] == 1 )
            return false;
        
        y--;
        x++;
      
        
    }    
   
    return true;
   
}


void copyFxn( vector<vector<int>> board ,vector<vector<int>> &ans , int n ){
    
    vector<int> temp;
    for( int i=0 ; i<n ; i++ ){
        for( int j=0 ; j<n ; j++ ){
            
            temp.push_back( board[i][j] );
        }
    }
    
    ans.push_back(temp);
}


void solve( int col , vector<vector<int>> &board , vector<vector<int>> &ans , int n  ){
    
    // base condition - if col = n that means all col have queen place
    if( col == n ){
        copyFxn( board , ans  , n);
        return ;
    }
    
    
    for( int rowIndex = 0 ; rowIndex < n ; rowIndex++ ){
        
        if( isSafe( rowIndex , col , board , n  ) ){
            board[rowIndex][col] = 1;
            
            // Recursion
            solve( col+1 , board , ans , n);
            
            // backTracking
            board[rowIndex][col] = 0;
            
        }
        
    }
  
}


vector<vector<int>> nQueens(int n)
{
	
    vector<vector<int>> board( n , vector<int>(n , 0) );
    vector<vector<int>> ans;
    
    solve( 0 ,  board , ans  , n  );
	
    
    return ans;
}

```