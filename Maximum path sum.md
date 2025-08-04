# Approach
<!-- Describe your approach to solving the problem. -->
- In this case also we write the same manner
- Find max sum of nodes using
-     left node + current node
-     right node + current node
-     or just current node
-     return max of all these denoting what max can be made till this node that can be used by above node
-     In doing so add this work of finding max using all the paths obtained till this node. i.e. all max paths that are possiblwe at this node
# Complexity
- Time complexity:o(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:o(n)
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
    int fn(TreeNode* root,int &maxi){
        if(root==nullptr)return 0;
        int left=fn(root->left,maxi);
        int right=fn(root->right,maxi);
        int curve=root->val+left+right;
        maxi=max({maxi,curve,root->val+right,root->val+left,root->val});
        return max({root->val+right,root->val+left,root->val});
    }
    int maxPathSum(TreeNode* root) {
        int maxi=INT_MIN;
        fn(root,maxi);
        return maxi;
    }
};
```
