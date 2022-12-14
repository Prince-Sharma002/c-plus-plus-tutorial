# Nth Fibonacci Number using DP

'''

#include<bits/stdc++.h>
using namespace std;

int fib( int n , vector<int> &dp ){
    
    if( n <= 1 ){
        return n;
    }
    
    // check in vector if fib at index present
    if( dp[n] != -1 )
        return dp[n];
    
    // recursion
    dp[n] = fib( n-1 , dp ) + fib( n-2 , dp );
    return dp[n];
}


int main()
{
    int n;
    cin>> n;
    
    vector<int> dp(n+1);
    
    // inserting value of -1 in vector
    for( int i=0 ; i<=n ; i++ ){
        dp[i] = -1;
    }
    
    cout<< fib(n , dp);
  
}

'''