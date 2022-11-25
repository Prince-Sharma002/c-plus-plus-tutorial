# Graph Implementation ( Adjacency List )

```c++



#include <bits/stdc++.h>

using namespace std;
template < typename T >


class graph{
  
  public:
  unordered_map< T  , list<T> > ad;
  
  void insertEdge( T a , T b , bool direction){
      
  // direction - 0 = undirected graph 
  // direction - 1 = directed graph
  
  // create an edge from a to b
  ad[a].push_back( b );
  
  // for edge from b to a
  if( direction == 0 )
      ad[b].push_back( a );

}
  
  
  
// printing graph  
void print_ad(){
    
      for( auto i:ad ){
          cout<< i.first << "->";
          for( auto j : i.second )
            cout<< j <<  " ,";
          
          cout<< endl ;  
      }
      
  }
  
};


int main() {
   
   int m;
   cout<< "enter no. of edges" <<endl ;
   cin>> m ;
   
   graph<char> g;
   
   // inserting data 
   for( int i=0 ; i<m ; i++ ){
       char a , b;
       cin >> a >> b;
       
       // directed graph
       g.insertEdge( a , b , 1);

   }
   
   g.print_ad();
  
    return 0;
}


```