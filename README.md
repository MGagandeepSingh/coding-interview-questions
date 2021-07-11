# coding-interview-questions
Contains question asked during the hacker rank or codelity

## Microsoft
1. The binary representation of 30-bit unsigned integer Q is donates by the sequence [Q[29], Q[28], ..., Q[1], Q[0]] where Q[29] corresponds to the most significant bit of Q. Leading zeroes may appear.

A 30-bit unsigned integer N is given. The right cyclic shift of N by one bit is the 30-bit unsigned integer whose binary representation is [N[0], N[29], N[28], ..., N[2], N[1]]. A right cyclic shift of N by K bits is the result of performing a right cyclic shift of N by one bit K times.

For Example
  
    the right cyclic shift of 9736 by one bit is 4,868.
    the right cyclic shift of 9736 by two bit is 2,434.
    the right cyclic shift of 9736 by three bit is 1,217.
    the right cyclic shift of 9736 by five bit is 26,84,35,760.
    the right cyclic shift of 9736 by eleven bit is 80,95,00,676.
    
The number 80,95,00,676 is the largest value that can be obtained by performing a right cyclic shift of 9,736.

You are given an implementation of a function:
  
   class Solution {
      public int solution(int N);
   }
   
that, given a 30-bit unsigned integer N, returning any integer K such that the right cyclic shift of N by K bits yields the largest possible value. If there are several integers K fulfilling this condition, the function may return any of them.

For example, given N=9,736, the function may return 11, as explained above.

The attached code is still incorrect for some inputs. Despite the error(s0, the code may produce a correct answer for the example test cases. The goal of the exercise is to find and fix the bug(s) in the implementation. You can modify at most two lines.

Assume that:
  N is an integer within the range [0 ... 1,07,37,41,823].
  
In your solution, focus on the correctness. The performance of your solution will not be the focus of the assessment.


Given solution:

```
class Solution {
  int solution(int N) {
    int largest = 0;
    int shift = N;
    int temp = 0;
    for(int i = 1: i < 30; i++) {
      int index = (temp & 1);
      temp = ((temp >> 1) | (index) << 29));
      if(temp > largest) {
        largest = temp;
        shift = i;
      }
    }
  }
  return shift;
}
```
