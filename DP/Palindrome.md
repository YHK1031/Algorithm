# Palindrome problem using DP
When solving palindrome problem, first thing should do is making dp boolean table.<br>
dp[start][end] where start is start of the certain point of the string and end is end of the certain point of the string.<br>
Follow the steps to make the dp table
<ol>
  <li>Size of 1 by itself is a palindrome. It should return true for every single element by itself</li>
  <li>Size of 2 which represents the start of the palindrome of even number of array.</li>
  <li>If numbers in both edges are equal and String inside of it is palindrome, it is palindrome.</li>
</ol>

```JAVA
for(int i=1;i<=n;i++) {
	arr[i]=sc.nextInt();
}
for(int i=1;i<=n;i++) {
	dp[i][i]=true;
}
for(int i=1;i<n;i++) {
	if(arr[i]==arr[i+1]) dp[i][i+1]=true;
}
for(int i=2;i<n;i++) {
	for(int j=1;j<=n-i;j++) {
		if(arr[j]==arr[j+i] && dp[j+1][j+i-1]) {
			dp[j][j+i]=true;
		}
	}
}
