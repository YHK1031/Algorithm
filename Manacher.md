# Manacher's Algorithm
<a href="https://www.hackerrank.com/topics/manachers-algorithm">Manacher's Algorithm</a>
<a href="https://www.youtube.com/watch?v=nbTSfrEfo6M&t=120s">Youtube Lecture</a>
```
It's one of the most efficient ways of solving palindrome problems
```
The cocept of this algorithm is somewhat similar to DP(Dynamic Programming). <br>
However, I had a hard time understanding it the first time I saw. <br>
<ol>
  <li>Build a new char array with the given string
    <ul>
      <li>Start the array with '@' and ends with '$'
      <li>Insert '#' between every character in given string.
      <li>If the given string is 'aba', the converted new array would be like '@#a#b#a#$'
    </ul>
  <li>Iterate through the converted array, keeping the track of the length of palindrom string in array P
  <li>While iterating, the center, rightmost boundary, and mirrored index would be tracked.
    <ul>
      <li>First, if the index is smaller than rightmost boundary, smaller value between r-i and P[mirror] would be assigned
      <li>Second, now start compare left and right letter and see if they are the same.
      <li>Finally, when comparing is over, if i+P[i] is greater than rightmost boundary, assign c=i, r=i+P[i]. The new center is assigned because it went over the rightmost boundary.
    </ul>
</ol>

```JAVA
// s is given string
int c = 0;
int r = 0;
int maxIdx = 0;
int maxLen = 0;
char[] t = new char[s.length()*2+3];
int[] p = new int[s.length()*2+3];


t[0]='@';
t[1]='#';
t[t.length-1]='$';

// converting a given string to a new form
for(int j=0;j<s.length();j++){
  t[j+2]=s.charAt(j);
  t[j+3]='#';
}

for(int i=0;i<t.length;i++){
  int mirror = 2*c-i;
  if(i<r) p[i]=Math.min(r-i,p[mirror]);
  while(t[i+(1+p[i])]==t[i-(1+p[i])]) p[i]++;
  if(i+p[i]>r){
    c=i;
    r=i+p[i];
  }
  if(p[i]>maxLen){
    maxIdx=i;
    maxLen=p[i];
  }
}
String longestPalindrome = s.substring((maxIdx-maxLen)/2,(maxIdx+maxLen-1)/2);
```
