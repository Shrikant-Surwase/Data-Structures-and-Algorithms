# Generate Parentheses

## statement:
### Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

## Solution:

In this problem we have 2 options
1. We have to calculate each combination of the given 2*n length of string and then check isValid then push_back in ans vector
2. We have to use backtracking (open < n) && (close < open) method to check the valid string

## 1. Time complexity is O(n*2^n) because we use 2^n combination here
### CODE: 
```C++
class Solution {
public:
 bool isValid(string s){
     stack<int>st;
     for(auto i: s){
         if(i =='(') st.push(i);
         else{
             if(st.empty()) return false;
             if(i == ')') st.pop();
             else st.push(i);
         }
     }
     return st.empty() == true;
 }
 void f(int n, vector<string>&ans, string curr){
     if(n == 0){
         if(isValid(curr)){
             ans.push_back(curr);
         }
         return;
     }
     curr += '(';
     f(n-1,ans,curr);
     curr.pop_back();
     curr+=')';
     f(n-1,ans,curr);
 }
    vector<string> generateParenthesis(int n) {
        //we need to create each and every possible combination and then 
        //check the valid conbination and it in ans vector
        //return ans;

        vector<string>ans;
        string curr;
        f(2*n,ans,curr);
        return ans;
    }
};
```
## 2. Time complexity is O(2^n) only Backtracking algo
### Code:
```C++
class Solution {
public:

 void f(int n, int open, int close, vector<string>&ans, string str){
     if(str.size() == 2*n){
         ans.push_back(str);
         return;
     }
    if(open < n){
        str+='(';
        f(n,open+1,close,ans,str);
        str.pop_back();
    }
    if(close < open){
        str+=')';
        f(n,open,close+1,ans,str);
        str.pop_back();
    }
 }
    vector<string> generateParenthesis(int n) {
        vector<string>ans;
        if(n == 0) return ans;
        string str;
        f(n,0,0,ans,str);
        return ans;
    }
};
```
