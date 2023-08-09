# Combination Sum


## statement:
### Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.
### The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

### The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

Solution:

Here we need to understand that we have one template for Backtracking like as follows:
```C++
class Solution {
public:
vector<vector<int>>ans;
 void f(int i, vector<int>given, vector<int>curr, int k, int n){
     if(n == 0 || n < 0 || curr.size() == k){ //here is base conditions where input tastecase is false
         if(n == 0){
             ans.push_back(curr);
         }
         return;
     }
     for(int j=i; j<given.size(); j++){
         curr.push_back(given[j]); //this three line is essential to make conbinations
         f(j+1,given,curr,k,n-given[j]);
         curr.pop_back();
     }
 }
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int>given ={1,2,3,4,5,6,7,8,9};
        vector<int>curr;
        f(0,given,curr,k,n);
        return ans;
    }
};
```

## Code
```C++
class Solution {
public:
 vector<vector<int>>ans;
 void f(int i, vector<int>g, vector<int>curr, int t){
     if(i == g.size() || t == 0 || t < 0){
         if(t == 0){
             ans.push_back(curr);
         }
         return;
     }
     for(int j=i; j<g.size();j++){
         curr.push_back(g[j]);
         f(j,g,curr,t-g[j]);
         curr.pop_back();
      
     }
 }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<int>curr;
        f(0,candidates,curr,target);
        return ans;
    }
};
```
