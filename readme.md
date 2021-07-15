Problem 1: Given an array a[] of size n. For every i from 0 to n-1 output max(a[0], a[1],..., a[i]).

Approach: 1. Keep a variable mx which stores the maximum till ith element. 2. Iterate over the array and update, mx = max(mx, a[i])

Testcase 1: Input: a[6]={0,-9,1,3,-4,5} Output:0 0 1 3 3 5


```cpp
#include<iostream>
using namespace std;



int main(){
    int n;
    cin>>n;

    int a[n];
    for(int i=0; i<n; i++)
    {
        cin>>a[i];
    }

    int mx= -199999;
    for(int i=0; i<n; i++)
    {
        mx = max(mx, a[i]);
        cout<< mx <<endl;
    }
    return 0;

}
```

Problem2: An arithmetic array is an array that contains at least two integers and the differences between consecutive integers are equal. For example, [9, 10], [3, 3, 3], and [9, 7, 5, 3] are arithmetic arrays, while [1, 3, 3, 7], [2, 1, 2], and [1, 2, 4] are not arithmetic arrays.

Approach: 1. While iterating in the array we need to maintain the following variables, 
a. Previous common difference (pd) - To compare it with current common difference (a[i] - a[i-1]). 
b. Current arithmetic subarray length (curr) - It denotes the arithmetic subarray length including a[i]. 
c. Maximum arithmetic subarray length (ans) - It denotes the max. Arithmetic subarray length till a[i]. 
2. While iterating, there will be two cases, a. pd = a[i] - a[i-1] i. 
Increase curr by 1 ii. ans = max(ans, curr) 
3. After loop ends, output the answer. (stored in ans variable)

TestCase 1:  Input: a[7]={10,7,4,6,8,10,11} Output: 4

```cpp
#include<iostream>
using namespace std;

int main(){
    int n;
    cin>>n;
    int a[n];
    for(int i=0; i<n; i++)
    {
        cin >> n;
    }
    int ans = 2;
    int d = a[1] - a[0];
    int j = 2;
    int curr = 2;
    while(j<n)
    {
        if(a[j] - a[j-1] == d){
            curr++;
        }
        else
        {
            d = a[j] - a[j-1];
            curr = 2;
        }
        ans = max(ans, curr);
        j++;
    }
    cout<< ans <<endl;
    return 0;
}
```

Problem 3: Isyana is given the number of visitors at her local theme park on N consecutive days. The number of visitors on the i-th day is Vi. A day is record breaking if it satisfies both of the following conditions: ● The number of visitors on the day is strictly larger than the number of visitors on each of the previous days. ● Either it is the last day, or the number of visitors on the day is strictly larger than the number of visitors on the following day. Note that the very first day could be a record breaking day! Please help Isyana find out the number of record breaking days.

Approach: Intuition: If we can optimise step (1), then we can optimise our overall solution. For step (1): We need to check if a[i] > { a[i-1], a[i-2],..., a[0] }, which is same as a[i] > max(a[i-1], a[i-2],..., a[0]) For this, we will keep a variable mx, which will store the maximum value till a[i]. Then we just need to check, a[i] > mx a[i] > a[i+1] , { if i+1 < n } and update mx, mx = max(mx, a[i]) So step (1) time complexity reduces to O(1)

Testcase 1: Input: a[8]={1,2,0,7,2,0,2,2} Output=2

```cpp
#include<iostream>
using namespace std;


int main()
{
    int n;
    cin >> n;

    int a[n+1];
    a[n] = -1;
    for (int i=0; i<n; i++){
        cin>> a[i];
    }

    
    if(n ==1){
        cout << "1" <<endl;
    }

    int ans = 0;
    int mx = -1;

    for(int i=0; i<n; i++){
        if(a[i]>mx && a[i] > a[i+1])
            ans++;
        mx = max(mx, a[i]);
    }
    cout << ans <<endl;
    return 0;
}
```