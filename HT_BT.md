# Approach
- Intially thought that check for each node
- You go to each node and check that this node is balacned or not. 

# Complexity
- Time complexity: O(n^2) 
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n^2)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int ht(TreeNode* root){
        if(root==nullptr)return 0;
        return 1+max(ht(root->left),ht(root->right));
    }
    int diameterOfBinaryTree(TreeNode* root) {
        if(root==nullptr)return 0;
        // d1
        int leftht=ht(root->left);
        int rightht=ht(root->right);
        int d1=leftht+rightht;
        //d2
        int d2=diameterOfBinaryTree(root->left);
        //d3
        int d3=diameterOfBinaryTree(root->right);
        return max(d1,max(d2,d3));
    }
};
```

# Approach
-But to improve on it 
- we can do it using apprcoh told by //// mik ////
- we write a function which return max depth for a node let say root node
- In doing this proccess what we will do is that we can calculate the diamater for each node and take its max .. to obtain max one by taking the left and right ht calculated by the function.
  

# Complexity
- Time complexity: O(n) 
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
// return max dept from from that root node going till left / right
    int solve(TreeNode* root,int &ans){
        if(root==nullptr)return 0;
        // max ht from left
        int left=solve(root->left,ans);
        int right=solve(root->right,ans);
        int diameter=left+right;
        ans=max({ans,diameter});
        return 1+max(left,right);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        int ans=INT_MIN;
        solve(root,ans);
        return ans;
    }
};
```
