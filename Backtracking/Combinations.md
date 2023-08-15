
# Combinations 

## statement:
### Given two integers n and k, return all possible combinations of k numbers chosen from the range [1, n]. You may return the answer in any order.

Solution:
 ### Here the catch is we need to calculate the combination of size k so we use backtracking for combination

 ```C++
class Solution {
public:
        vector<vector<int>>ans;
 void f(int j, int n, int k, vector<int>&curr){
     if(curr.size() == k){
         ans.push_back(curr);
         return;
     }
     for(int i=j; i<=n; i++){
         curr.push_back(i);
         f(i+1,n,k,curr);
         curr.pop_back();
     }
     return;
 }
    vector<vector<int>> combine(int n, int k) {

        vector<int>curr;
        f(1,n,k,curr);
        return ans;
    }
};


```
