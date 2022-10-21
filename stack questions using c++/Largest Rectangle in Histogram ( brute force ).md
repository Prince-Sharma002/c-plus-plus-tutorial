#  Largest Rectangle in Histogram ( brute force)

```c++

int main() {
	
	int arr[] = {10,15,11};
	
	int n = sizeof(arr)/sizeof(arr[0]);

	
	int ans = 0;
	
	for(int i=0 ; i<n ; i++){
		
		int leftans = arr[i];
		int rightans = arr[i];
		
		int leftindex = 1;
		int rightindex = 1;
		
		
		// left traversal
		for(int j=i-1 ; j>=0 ; j--){
			
			
			if(arr[i] <= arr[j])
				leftindex++;
			else
				break;
						
		} 
		
		leftans = leftans*leftindex;
		
		
		
		// right traversal
		
		for(int j=i+1 ; j<n ; j++){
			
			
			if(arr[i] <= arr[j])
				rightindex++;
			else
				break;
			
		}
		
		
		
		rightans = rightans * rightindex;
		
		
		int sum = leftans + rightans - arr[i];
		if(sum > ans)
			ans = sum;
		
	
	}
	
	cout<< "answer is " << ans;

	return 0;
}


```