C++ Priortiy Queue STL([Source](https://www.geeksforgeeks.org/priority-queue-in-cpp-stl/))
--
* Default Behaviour:
  1. Acts as a max-heap -> Top element is the greatest.
  2. Stores elements in non-increasing order.

* Customization:
   1. Can be configured as min-heap to keep the smallest element at the top using custom comparators.

* Underlying Implementation: 
    1. Built on heap data structures.
    2. Internally uses an array/vector for storage.

* Common Operations:
     1. push(): Insert an element.
     2. pop(): Remove the top- priority element.
     3. top():Access the top-priority element.
* Time Complexity : O(log N) for insertion and removal.

* Syntax - _std:: priority_queue```<int>```pq;_

Code: To demonstrate the use of priority_queue in `C++`
--
``` C++
#include <iostream>
#include <queue>
using namespace std;

int main()
{
    int arr[6] = { 10, 2, 4, 8, 6, 9 };

    // defining priority queue
    priority_queue<int> pq;

    // printing array
    cout << "Array: ";
    for (auto i : arr) {
        cout << i << ' ';
    }
    cout << endl;
    // pushing array sequentially one by one
    for (int i = 0; i < 6; i++) {
        pq.push(arr[i]);
    }

    // printing priority queue
    cout << "Priority Queue: ";
    while (!pq.empty()) {
        cout << pq.top() << ' ';
        pq.pop();
    }

    return 0;
}
```
**Output: <br>Array: 10 2 4 8 6 9 <br>
Priority Queue: 10 9 8 6 4 2 


