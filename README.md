# Data Structure and Algorithms
## Sliding Window
> ## 1) Sliding Window Maximum
> Problem: You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.
Return the max sliding window.

* Firstly we have to use the SW technique
* Use Priority queue pair to maintain the required element in the queue
* We have to print the max element in every subarray whose size is k so push the top most element in the queue which is maximum.
* we have to keep in mind that ` while(!pq.empty() && pq.top().second <= i-k) pq.pop();` this part is very important because it will pop the element which are out of window size
* last return the vectro
```C++
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        vector<int>ans;
        priority_queue<pair<int,int>>pq;
        for(int i=0; i<k; i++){
            pq.push({nums[i],i});
        }
        ans.push_back(pq.top().first);
        for(int i=k; i<nums.size(); i++){
            pq.push({nums[i],i});
            while(!pq.empty() && pq.top().second <= i-k) pq.pop();

            ans.push_back(pq.top().first);
        }
        return ans;
    }
};
```


