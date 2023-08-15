# Letter Combinations of a Phone Number

## statement:
### Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order. A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Solution:
ye 1st question hai jo Backtracking ko samjne ke liye easy hai

1)Nehami lakshat thev=  jevha pn print kraych asel js ki substring/subsequence then backtracking use kra karan ithe apn 2d array use krtoy jo ki aplyala save krnyasathi use hoto and then return kra 2d array
2)2d ani 1d array bnva, 2d ka tr ans save krnyasathi and 1d for reference
3)Hya problem madhe aplyala numbers dile ahet mnje we need to find the substring and then store it if the lenght==given string length
4)Base conditions is very important if(str.size() == given.size()) then we need to add str in ans;
## code
```C++
class Solution {
public:
  void f(int id, string d, string g[], string str, vector<string>&ans){
      if(id == d.size()){
          ans.push_back(str);
          return;
      }
      int index = d[id]-'0';
      string temp = g[index];
      for(int i=0; i<temp.size(); i++){
          str.push_back(temp[i]);
          f(id+1,d,g,str,ans);
          str.pop_back();
      }

  }
    vector<string> letterCombinations(string digits) {
        vector<string>ans;
        string given[10]={"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
    if(digits.size() == 0) return ans;
     string str="";
     f(0,digits,given,str,ans);
     return ans;
    

    }
};
```
