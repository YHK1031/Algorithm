# NextPermutation
<ol>
	<li>Find the last index i where N[i] < N[i+1] from the first iteration.</li>
	<li>Find the largest index j where N[j] > N[i] by iterating from last index of the array to the index i found in previous step.</li>
	<li>Swap two of them each other.</li>
	<li>Reverse from i+1 to the last of the array.</li>
</ol>

```JAVA
public static void nextPermute(int[] arr) {
		int idx = -1;
		for(int i=0;i<arr.length-1;i++) {
			if(arr[i]<arr[i+1]) idx = i;
		}
		if(idx==-1) return;
		int tar = -1;
		for(int j = arr.length-1;j>=idx;j--) {
			if(arr[idx]<arr[j]) { 
				int temp = arr[j];
				arr[j]= arr[idx];
				arr[idx]=temp;
				break;
			}
		}
	    	for (int i = idx + 1; i < (arr.length + idx + 1) / 2; i++) {
            		int tmp = arr[i];
            		arr[i] = arr[arr.length - (i - idx)];
            		arr[arr.length - (i - idx)] = tmp;
    	  	}	
}
```
