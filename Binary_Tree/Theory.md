# Binary Tree
A Tree Data Structure can be traversed in following ways:

## Depth First Search or DFS
        1)Inorder Traversal
        2)Preorder Traversal
        3)Postorder Traversal
### 1) Inorder Traversal (Left->root->right):


#### Mainly two way to Implement the Inorder traversal:
1) ${\color{green} Using \space Stack}$ TC:O(N) SC:O(N):
2) ${\color{green}Using \space Recursion}$ TC:O(N) SC:O(N):

```C++
1)Stack === function print():
2)Recursion === function print1();

//we neet to understand how the binary tree is form

#include<bits/stdc++.h>
using namespace std;

class Node{
    public:
     int data;
     Node*left,*right;
     Node(int n){
         data = n;
         left=right=NULL;
     }
};
void print1(Node*head){
    if(head == NULL) return;
    print1(head->left);
    cout<<head->data<<" ";
    print1(head->right);
}
void print(Node*head){
    stack<Node*>st;
    Node*curr = head;
    while(true){
        
            if(curr != NULL){
                st.push(curr);
                curr=curr->left;
            }else{
                if(st.empty()) break;
                else{
                    curr=st.top();
                    st.pop();
                    cout<<curr->data<<" ";
                    
                        curr=curr->right;
                    
                }
            }
        
        
    }
}
int main(){
    Node*g = new Node(0);
    g->left = new Node(1);
    g->right=new Node(2);
    g->left->left=new Node(3);
    g->left->right = new Node(4);
     g->right->left=new Node(5);
      g->right->right = new Node(6);
    print(g);
    
}
```



## Breadth First Search or BFS
    1)Level Order Traversal or Breadth First Search or BFS
