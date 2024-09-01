Three way Partitioning of an Array around a Given Range in C
Here, in this page we will discuss the program for Three way partitioning of an array around a given range in C programming language. We are given with an array and a range say [low, high].

Three way Partitioning
Partition the array in such a way :
All the elements less than low value, should come first.
Elements between the low and high value come in middle.
All elements greater than high should come at the last.
Method Discussed :
Method 1 : Naive Approach
Method 2 : Efficient Approach
Method 1 :
Declare an array of n size and initialize the elements of the array .
Now, Initialize lower limit and upper limit of the range and store them in variable say low and high respectively.
Now, sort the array after sorting the array got partitioned.
Note : By this algorithm the order of the array can’t be maintained.

Time and Space Complexities :
Time-Complexity : O(n*n)
Space-Complexity : O(1)
Method 1 : Code in C
Run
#include <stdio.h>

int main(){

  int a[] = {2, 89, 34, 16, 17, 10, 11, 78, 30, 19};
  int n = sizeof(a)/sizeof(a[0]);
  
  int low = 15, high = 20;

  for(int i= 0; i<n; i++){
      for(int j=i+1; j<n; j++){ if(a[i]> a[j]){
            int temp = a[i];
            a[i] = a[j];
            a[j] = temp;
          }
      }
  }
  
  for(int i=0; i<n; i++)
  printf("%d ",a[i]);

}
Output :
2 10 11 16 17 19 30 34 89 78
Related Pages
Given an array which consists of only 0, 1 and 2

Find the “Kth” max and min element of an array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2 :
Call getPartition function, in that function pass the array, size and low and high value of the range.
In the getPartition function,
Declare two pointer one is ptr1 set at 0 index and another is ptr2 set at last index i.e, n-1.
Now, traverse the array till i<=ptr2.
Check if current value is lower than low value than swap it with ptr1 pointing value, and increase the value of ptr1 and i.
Else if current value is greater than high than swap it with ptr2 value, and decrease the value of ptr2 .
Otherwise increase the value of i.
Time and Space Complexities :
Time-Complexity : O(n)
Space-Complexity : O(1)
Method 2 : Code in C
Run
#include<stdio.h>

void swap(int a, int b){
    int temp = a;
    a = b;
    b = temp;
}
void getPartition(int a[], int n, int low, int high)
{
   int ptr1 = 0, ptr2 = n-1;
   for (int i=0; i<= ptr2; i++)
   {
      if (a[i] < low) 
      swap(a[i++], a[ptr1++]); 
      else if (a[i] > high)
      swap(a[i], a[ptr2--]);
      else
      i++;
    }
}

int main(){

  int a[] = {2, 89, 34, 16, 17, 10, 11, 78, 30, 19};
  int n = sizeof(a)/sizeof(a[0]);
  
  int low = 15, high = 20;

  getPartition(a, n, low, high);

  for(int i=0; i
Output :
2 10 11 16 17 19 30 34 89 78
