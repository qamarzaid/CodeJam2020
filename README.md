12
## Google Codejam 2020
### Qualification Round
####  Problem: Vestigium
```
Vestigium means "trace" in Latin. In this problem we work with Latin squares and matrix traces.

The trace of a square matrix is the sum of the values on the main diagonal (which runs from the
upper left to the lower right).

An N-by-N square matrix is a Latin square if each cell contains one of N different values, and 
no value is repeated within a row or a column. In this problem, we will deal only with "natural
Latin squares" in which the N values are the integers between 1 and N.

Given a matrix that contains only integers between 1 and N, we want to compute its trace and check
whether it is a natural Latin square. To give some additional information, instead of simply telling 
us whether the matrix is a natural Latin square or not, please compute the number of rows and the number
of columns that contain repeated values.
```
##### Input
```
The first line of the input gives the number of test cases, T. T test cases follow. Each starts with a line
containing a single integer N: the size of the matrix to explore. Then, N lines follow. The i-th of these
lines contains N integers Mi,1, Mi,2 ..., Mi,N. Mi,j is the integer in the i-th row and j-th column.
```
##### Output
```
For each test case, output one line containing Case #x: k r c, where x is the test case number (starting from 1),
k is the trace of the matrix, r is the number of rows of the matrix that contain repeated elements, and c is the
number of columns of the matrix that contain repeated elements.
```
##### Limits
##### Test set 1 (Visible Verdict)
```
Time limit: 20 seconds per test set.
Memory limit: 1GB.
1 ≤ T ≤ 100.
2 ≤ N ≤ 100.
1 ≤ Mi,j ≤ N, for all i, j.
```
##### Sample Input:
 ```
3
4
1 2 3 4
2 1 4 3
3 4 1 2
4 3 2 1
4
2 2 2 2
2 3 2 3
2 2 2 3
2 2 2 2
3
2 1 3
1 3 2
1 2 3
```
##### Sample Output:
```
Case #1: 4 0 0
Case #2: 9 4 4
Case #3: 8 0 2
```
##### Code:
```python

# template
def  inp():
	return(int(input()))
def inlt():
	return(list(map(int,input().split())))
def insr():
	s=input()
	return(s[:len(s)-1])
def invr():
	return(map(int,input().split()))
#for input


# main code
def solve():
	n=inp()
	arr=[]
	for i in range (n):
		s=inlt()
		arr.append(s)
	#return arr
	k=0
	for i in range(n):
		k=k+arr[i][i]
	#return k
	r=[[0]* n for i in range(n)]
	rcount=0
	for i in range (n):
		for j in range(n):
			
			r[i][arr[i][j]-1]+=1
		if 0 in r[i]:
			rcount=rcount+1

	c=[[0]* n for i in range(n)]
	ccount=0
	for i in range (n):
		for j in range(n):
			c[i][(arr[j][i])-1]+=1
		if 0 in c[i]:
			ccount=ccount+1

	print("Case #" + str(z+1) +":",k,rcount,ccount)
	#print(r)

	


t=inp()
for z in range (t):
	solve()
	
	#print(z)
```
[Code Demo Link](https://replit.com/@ZaidQamar/vestigium#main.py)


![](https://media.giphy.com/media/zXmbOaTpbY6mA/giphy.gif)
#### Problem: Nested Depth
```
tl;dr: Given a string of digits S, insert a minimum number of opening and closing parentheses into it 
such that the resulting string is balanced and each digit d is inside exactly d pairs of matching parentheses.

Let the nesting of two parentheses within a string be the substring that occurs strictly between them.
An opening parenthesis and a closing parenthesis that is further to its right are said to match if their 
nesting is empty, or if every parenthesis in their nesting matches with another parenthesis in their nesting.
The nesting depth of a position p is the number of pairs of matching parentheses m such that p is included in 
the nesting of m.

For example, in the following strings, all digits match their nesting depth: 0((2)1), (((3))1(2)), ((((4)))),
((2))((2))(1). The first three strings have minimum length among those that have the same digits in the same order,
but the last one does not since ((22)1) also has the digits 221 and is shorter.

Given a string of digits S, find another string S', comprised of parentheses and digits, such that:

1. all parentheses in S' match some other parenthesis,
2. removing any and all parentheses from S' results in S,
3. each digit in S' is equal to its nesting depth, and
4. S' is of minimum length.
```
##### Input:
```
The first line of the input gives the number of test cases, T. T lines follow. Each line represents
a test case and contains only the string S.
```
##### Output:
```
For each test case, output one line containing Case #x: y, where x is the test case number 
(starting from 1) and y is the string S' defined above.
```
##### Limits
```
Time limit: 20 seconds per test set.
Memory limit: 1GB.
1 ≤ T ≤ 100.
1 ≤ length of S ≤ 100.
```
###### Test set 1 (Visible Verdict)
```
Each character in S is either 0 or 1.
```
###### Test set 2 (Visible Verdict)
```
Each character in S is a decimal digit between 0 and 9, inclusive.
```
##### Sample Input:
```
4
0000
101
111000
1
```
##### Sample Output:
```
Case #1: 0000
Case #2: (1)0(1)
Case #3: (111)000
Case #4: (1)
```
##### Code:
```python
#Template
#for input
def InP():
	return int(input())

def InL():
	return (list(map(int,input().split())))

def InS():
	s=input()
	return (s[:len(s)])

def inV():
	return map(int,input().split())



#main code
def Solution():
	S=InS()
	#print(S)
	o=""
	for i in range (len(S)):
		o=o+("(" * int(S[i]))+ S[i]+(")"*int(S[i]))
	#print(o)
	n=["("]
	if o[0]=="0":
		n[0]="0"
	for i in range(1,len(o)):
		if o[i] =="(" and n[-1]==")":
			n.pop()
		else:
			n.append(o[i])
	A=""
	print("Case #"+str(z+1)+ ":","",A.join(n))




#iterator test case
t=InP()
for z in range(t):
	Solution()
	
```
[Code Demo Link](https://replit.com/@ZaidQamar/nesting-Depth-2#main.py)


![](https://media.giphy.com/media/26BRzI0MafGdqWGOc/giphy.gif)


