Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

```
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | null
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */

function lowestCommonAncestor(root: TreeNode | null, p: TreeNode | null, q: TreeNode | null): TreeNode | null {
    
    // Input validation, edge cases
    if(root === null || p === null || q === null) return null;
    if(root.val === p.val && isPresent(root, q)) return  p;
    if(root.val === q.val && isPresent(root, p)) return  q;
    
    if (p.val < root.val && q.val < root.val){
        return lowestCommonAncestor(root.left, p, q);
    }
    if (p.val > root.val && q.val > root.val){
        return lowestCommonAncestor(root.right, p, q);
    }
    return root;
};

function isPresent(root: TreeNode | null, node: TreeNode) {
    if(root === null) return false;
    return root.val === node.val || (isPresent(root.left, node) && isPresent(root.right, node));
}

```
