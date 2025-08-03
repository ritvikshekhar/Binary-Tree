# Binary-Tree-DFS
## All Patterns of DFS questions in Binary Tree 

##  Leetcode: Link:https://leetcode.com/problems/path-sum/
# Intuition
This is a DFS question which comes by seeing we need to go indepth to reach each leaf one after another.
# Approach
See code for DFS.
# Complexity
- Time complexity:$$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:$$O(n)$$
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
    bool fn(TreeNode* root,int Sum, int targetSum) {
        if(root==nullptr){
            return false;
        }
        else if (root->left==nullptr && root->right==nullptr && Sum+(root->val)==targetSum){
            return true;
        }
        else if(root->left==nullptr && root->right==nullptr && Sum+(root->val)!=targetSum){
            return false;
        }
        
        bool ans1=fn(root->left,Sum+root->val,targetSum);
        bool ans2=fn(root->right,Sum+root->val,targetSum);
        return (ans1 || ans2);
    }
bool hasPathSum(TreeNode* root, int targetSum){
int Sum=0;
return fn(root,Sum,targetSum);
    }
};
```
```
so what I am doing is from
node 1---node 2 only when its not null
when you reach lleaf node return
```



##    same type question: https://leetcode.com/problems/path-sum-ii/description/
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
void fn(TreeNode* root,int sum,vector<int>arr,vector<vector<int>>&result, int targetsum) {
      if(root==nullptr){
            return ;
        }
        else if (root->left==nullptr && root->right==nullptr && sum+(root->val)==targetsum){
           arr.push_back(root->val);
           result.push_back(arr);
        }
        else if(root->left==nullptr && root->right==nullptr && sum+(root->val)!=targetsum){
            return ;
        }  
         arr.push_back(root->val);
         fn(root->left,sum+root->val,arr,result,targetsum);
         fn(root->right,sum+root->val,arr,result,targetsum);
    }
     vector<vector<int>> pathSum(TreeNode* root, int targetSum){
         int sum=0;
         vector<vector<int>>result;
         vector<int>arr;
         fn(root,sum,arr,result,targetSum);
         return result;
     }
};
```
