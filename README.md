# -based-on-leetcodeNo.101-
# 疑惑点：用来递归的子函数返回的一直是bool值，但输入却是其他数据结构(大雾)
## 题目：给你一个二叉树的根节点 root ， 检查它是否轴对称
``` python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True

        def isMirror(t1, t2):
            if not t1 and not t2:
                return True
            if not t1 or not t2:
                return False
            return (t1.val == t2.val) and isMirror(t1.left, t2.right) and isMirror(t1.right, t2.left)

        return isMirror(root.left, root.right)
```
首先，需要明确的一点是：isMirror()返回的一定是bool value,  
但事实上，从最底层（能递归到的最底层）向上return的bool value只是决定了递归是否需要进行下去，如果return的是false，递归将结束，如果是true，递归将继续。
