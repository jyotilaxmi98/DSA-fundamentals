# Monotonic Stack  

Source : [Click here](https://leetcode.com/discuss/study-guide/5148505/Monotonic-Stack-Guide-%2B-List-of-Problems/)

---

# Problem statement

When we want to solve problems like:
- Next greater Element
- Next smaller Element
- Previous greater Element
- Previous smaller Element
- Lexicographically Smallest/Greatest
- Histogram Related Problems left and right boundaries for each bar,

the concept of monotonic stack is used.

# What is monotonic stack?

Monotonic stack is a data structure that maintains elements in strictly increasing or decreasing order. Mononotic stacks can be achieved by enforcing push() and pop() operations depending on whether we want monotonic increasing stack or monotonic decreasing stack.


# Types : 

- Strictly increasing - every element of the stack is strictly greater than the previous element. Example - [1, 5,8,10]
- Non-decreasing - every element of the stack is greater than or equal to the previous element. Example - [1, 5,8,10,10]
- Strictly decreasing - every element of the stack is strictly smaller than the previous element - [10, 8, 5, 4, 1]
- Non-increasing - every element of the stack is smaller than or equal to the previous element. - [10, 10, 8, 5, 5, 4, 1]

Assuming that the right most element is at the top of the stack and left most element is at the bottom of the stack

_Generic template_ :
This template can be followed to build a stack keeping the monotonous property alive during the execution of the program -

``` C++
function buildMonoStack(arr) {
  // initialize an empty stack
  stack = [];
  
  // iterate through all the elements in the array
  for (i = 0 to arr.length - 1)) {
    while (stack is not empty && element represented by stack top `OPERATOR` arr[i]) {
      // if the previous condition is satisfied, we pop the top element
      let stackTop = stack.pop();
  
      // do something with stackTop here e.g.
      // nextGreater[stackTop] = i
    }
  
    if (stack.length) {
      // if stack has some elements left
      // do something with stack top here e.g.
      // previousGreater[i] = stack.at(-1)
    }

    // at the ened, we push the current index into the stack
     stack.push(i);
  }
  
  // At all points in time, the stack maintains its monotonic property
}
```

About the above template:

- We initialize an empty stack at the beginning.
- The stack contains the index of items in the array, not the items themselves
- There is an outer for loop and inner while loop.
- At the beginning of the program, the stack is empty, so we don't enter the while loop at first.
- The earliest we can enter the while loop body is during the second iteration of for loop. That's when there is at least an item in the stack.
- At the end of the while loop, the index of the current element is pushed into the stack
- The OPERATOR inside the while loop condition decides what type of monotonic stack are we creating.
The OPERATOR could be any of the four - >, >=, <, <=

# Time Complexity
Each element in the array is interacted with at most four times:

- When its value is checked against the top of the stack (in the while condition).
- When it is pushed onto the stack.
- When it is compared with another item during iteration (in the while condition again).
- When it is popped from the stack.

Since these interactions are constant for each element, the overall time complexity is linear—O(n), where n is the number of elements in the array.

# Space Complexity
We use a stack as an extra data structure, which in the worst case could store all the elements in the array. This means the space complexity is also linear—O(n), where n is the number of elements in the array.


# Key Insight: Monotone Stacks for Efficient Queries

Next Greater and Previous Greater Elements:
To find these, we build a monotone decreasing stack.
👉 Why? A decreasing stack ensures we can efficiently locate larger elements as we traverse the array.

Next Smaller and Previous Smaller Elements:
To find these, we build a monotone increasing stack.
👉 Why? An increasing stack allows us to efficiently locate smaller elements during traversal.

# Pro Tip: Easy Way to Remember
Think of it as an inverse relationship:

"Greater" → Decreasing Stack
"Smaller" → Increasing Stack

# Next Greater

Suppose we are given an array and we are told to find next greater elements of each item in the array-

``` C++
std::vector<int> arr = {13, 8, 1, 5, 2, 5, 9, 7, 6, 12};
```
We want to find the next greater elements and their indexes.

1. Next greater elements: 
The next greater element for an item is the first larger element found to its right.
If no such element exists, we use -1 or null.
```C++
// Result: Next Greater Elements
std::vector<int> nextGreaterElements = {-1, 9, 5, 9, 5, 9, 12, 12, 12, -1};
```
2. Next greater indexes: Instead of the element itself, we can store the index of the next greater element.
If no greater element exists, we use -1.
```C++
// Result: Next Greater Indexes
std::vector<int> nextGreaterIndexes = {-1, 6, 3, 6, 5, 6, 9, 9, 9, -1};
```
# Summary:
- For 13 (index 0): No greater element → -1 (or null).
- For 8 (index 1): Next greater is 9 (index 6).
- For 1 (index 2): Next greater is 5 (index 3).
Similarly, we calculate for other elements.

This logic helps optimize the solution using a stack-based approach!

C++ implementation-
```C++
#include <vector>
#include <stack>
using namespace std;

vector<int> findNextGreaterIndexes(vector<int>& arr) {
    // Initialize an empty stack to store indices
    stack<int> stk;

    // Initialize the nextGreater array with -1 (invalid index)
    vector<int> nextGreater(arr.size(), -1);

    // Iterate through all the elements of the array
    for (int i = 0; i < arr.size(); i++) {
        // While the stack is not empty AND the element at the stack's top is 
        // strictly smaller than the current element
        while (!stk.empty() && arr[stk.top()] < arr[i]) {
            // Pop the top of the stack, which represents the index of the item
            int stackTop = stk.top();
            stk.pop();

            // The next greater index for stackTop is the current index i
            nextGreater[stackTop] = i;
        }

        // Push the current index onto the stack
        stk.push(i);
    }

    return nextGreater;
}
```

Notes:
-- For finding next greater elements (not equal) we use a monotonic non increasing stack (type 4)
If the question was to find next greater or equal elements, then we would have used a monotonic strictly decreasing stack (type 3)
We use the operator < in while loop condition above - this results in a monotonic non increasing stack (type 4). If we use <= operator, then this becomes a monotonic strictly decreasing stack (type 3)
Time and space complexity - O(n)



















