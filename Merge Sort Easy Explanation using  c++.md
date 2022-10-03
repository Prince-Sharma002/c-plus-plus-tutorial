
# MERGE SORT 




```c++

                                                                // Merge sort

void merge(int arr[] , int s , int e){
    
    int mid = s + (e-s)/2;
    
    //sizes of splits subarray 
    int left_Array_size = mid + 1 -s;
    int right_Array_size = e-mid;
    
    //creating dynamic arrays
    int* left_Array = new int[left_Array_size];
    int* right_Array = new int[right_Array_size];
    

    //copy values in split subarrays
    
    //inserting in left subarray 
    
    int main_Array_Index = s;//left subarray start with s    
    
    for(int i=0 ; i<left_Array_size ; i++){
        left_Array[i] = arr[main_Array_Index];
        
        //increasing main array index
        main_Array_Index++ ;
    }
    
    
    //inserting in right subarray
    main_Array_Index = mid+1; //right subarray starts with mid+1
    
    for(int i=0 ; i<right_Array_size ; i++){
        right_Array[i] = arr[main_Array_Index];
        main_Array_Index++ ;
    }
    
    
    // Now we need to replace element in original array from both the splits subarray
    // in sorted way by comparing values
    
    int i=0 ; 
    int j=0 ;
    main_Array_Index = s;
    
    while( i<left_Array_size && j<right_Array_size){
        
        if(left_Array[i] < right_Array[j]){
            
            arr[main_Array_Index] = left_Array[i];
            main_Array_Index++;
            i++;
            
        }
        else{
            
            arr[main_Array_Index] = right_Array[j];
            main_Array_Index++;
            j++;
            
        }
        
    }   
    
    
    while( i < left_Array_size){
        
        arr[main_Array_Index] = left_Array[i];
        main_Array_Index++;
        i++;
        
    }
    
    while( j < right_Array_size){
        
        arr[main_Array_Index] = right_Array[j];
        main_Array_Index++;
        j++;
        
    }


    // deleting subarray to avoid memory leakage
    delete []left_Array;
    delete []right_Array;
        
}



void mergeSort(int arr[] , int s , int e){
    
    // stop splitting ( if s = e - single element left)
    //                ( if s > e - empty array)
    if(s>=e){
        return ;
    }
    
    int mid = s + (e-s)/2;
    
    
    // recursion splits array until single element
    mergeSort(arr , s , mid);
    mergeSort(arr , mid+1 , e);
    
    
    // merge function use for merging splited subarray in sorted order 
    // left array (s , mid)
    // right subarray (mid+1 , e) 
    merge(arr , s , e);
    
    
}




int main() {

  int arr[] = {6,5,4,4,3,2,1};
  int n = sizeof(arr)/sizeof(arr[0]) - 1 ;
  
  
  
  mergeSort(arr , 0 , n);
  
  
  // print array
  for(int i=0 ; i<= n ; i++){
      cout<< arr[i] << " ";
      
  } 
    
}

```


## Time complexity 

Time complexity - ` 0(nlogn) ` 

Merge sort divides the array into two part and takes `log(n)` time .
and merging two halves takes linear time . 


## Inplace and stability

- [Inplace](https://www.geeksforgeeks.org/in-place-algorithm/) - No , merge sort is not Inplace as it takes extra dynamic space in storing elements in subarray.
- [stability](https://www.geeksforgeeks.org/stable-and-unstable-sorting-algorithms/) - Yes , merge sort stable because it maintain order.
