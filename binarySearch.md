## Binary Search

- finding position of a traget value in a sorted array
- divided search space into two halves to find middle index



Implemented using two ways:
- Iterative Binary Search algorithm
- Recursive Binary Search algorithm

## Iterative approach

```
#include<iostream>
#include<vector>

using namespace std;


int binarySearch(vector<int>&arr, int x, int left, int right){
    
    while(left <= right){
        int mid = left + (right-left)/2;
        
    if(arr[mid] == x) 
        return mid;

    
    if(arr[mid] <= x)
       left = mid+1;
       
    else
      right = mid-1;
}
return -1;
}
int main(){
    
    vector<int>arr = {200,6,8,4,21,5};
    
    int x = 40;
    
    int n = arr.size();
    
    int result = binarySearch(arr,x,0,n-1);
    
    if(result == -1){
        cout<<"The element is not found in the array"<< endl;
        }
    else {
        cout<< "The target value is found which is present at index:"<< result<< endl;
    }  
    
    return 0;
    
    
}

```

## Recursive approach 

```

#include<iostream>
#include<vector>

using namespace std;


int binarySearch(vector<int>&arr, int x, int left, int right){
    
    while(left <= right){
        int mid = left + (right-left)/2;
        
        
    if(arr[mid] == x)    
       return mid;
       
    if(arr[mid] > x)  
       return binarySearch(arr,x,left,mid-1);
       
      return binarySearch(arr,x,mid+1,right); 
}

return -1;

}
int main(){
    
    vector<int>arr = {200,6,8,4,21,5};
    
    int x = 40;
    
    int n = arr.size();
    
    int result = binarySearch(arr,x,0,n-1);
    
    if(result == -1){
        cout<<"The element is not found in the array"<< endl;
        }
    else {
        cout<< "The target value is found which is present at index:"<< result<< endl;
    }  
    
    return 0;
    
    
}

```






