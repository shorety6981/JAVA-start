# 二叉搜索树的第k大节点

### 题目      
给定一棵二叉搜索树，请找出其中第k大的节点。           
  
### 思路    
根据leetcode精选解题方法而来，加上了一些自己的理解以及改成C++版本              

1.因为二叉搜索树的特点是左子树小于根结点，右子树大于根结点的结构，所以从右子树开始遍历              
2.dfs函数中的那一行替换成自己需要的          
  先判断k是否为0，若为0，则表示已经找到了需要的那个点，无须进行下面步骤，返回               
3.令k=k-1，再判断k是否为0，为0则将此时的结点值赋给res,得到结果          
  这个时候就体现了res,count为全局变量的好处了，因为两个函数中都共享这一个变量，对此变量做出修改           



### 代码
```
class Solution {
public:
    int res=0,count=0;
    int kthLargest(TreeNode* root, int k) {
        count=k;
        dfs(root);
        return res;
    }
    void dfs(TreeNode* root)
    {
        if(root==NULL)
            return ;
        dfs(root->right);
        if(count==0)
            return ;
        if(--count==0)
            res = root->val;
        dfs(root->left);
    }
};
```
