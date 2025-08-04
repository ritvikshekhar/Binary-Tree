# Approach
- IN THIS QUESTION WE COULD ALSO DO THAT GO ON ALL NODE AND CHECK THAT THEY ARE BALANED OR NOT.
- so THAT WILL TAKE O(N^2)

- BETTER APPROCH
  
        - BUT WHAT HERE WE DO ID THAT WE GO TO EVERY NODE
        - AND AS CALCUATED THE MAX HT OF LEFT AND RIGHT AND RETURED IT .
        -WE DO THAT HERE ALSO
        - JUST ADD A CHECK IN THAT CODE ONLY.
  

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
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
// max ht
    int fn(TreeNode* root,bool& ans){
        if(root==nullptr){
            return 0;
        }
        int left=fn(root->left,ans);
        int right=fn(root->right,ans);
        ans&=(abs(left-right)<=1);
        return 1+max(left,right);
    }
    bool isBalanced(TreeNode* root) {
        bool ans=true;
        fn(root,ans);
        return ans;
    }
};
```
