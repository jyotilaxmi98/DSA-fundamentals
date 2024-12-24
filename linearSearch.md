## Linear Search code using C++ for last minute revision:

``` C++

#include <iostream>
#include <vector>
using namespace std;

int search(vector<int>&arr, int x){
    for(int i=0; i<arr.size(); i++){
        if(arr[i] == x)
        return i;
    }
    return -1;
}




int main(){

    vector<int> arr = {20,100,60,40,2,1};
    int x = 2;

    int result = search(arr,x);

    if(result == -1){
        cout<<"Element is not present"<<endl;
    }
    else{ 
        cout<<"The element found is present at index:"<< result<< endl;
    }
    return 0;
}
 ```

