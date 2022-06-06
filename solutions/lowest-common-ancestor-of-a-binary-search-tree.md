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
    
    const [foundP, pathP] = binarySearchWithPath(root, p);
    if(!foundP) return null;
    
    const [foundQ, pathQ] = binarySearchWithPath(root, q);
    if(!foundQ) return null;
    
    let lca = null;
    while(pathP !== null && pathQ !== null && pathP[0] === pathQ[0]) {
        lca = pathP[0]
        pathP.shift();
        pathQ.shift();
    }
    return lca;
};

function binarySearchWithPath(root: TreeNode, node: TreeNode): [boolean, TreeNode[]] {
    if(root === null) return [false, []]
    if(root.val === node.val) return [true, [root]]
    
    const [foundInLeftChild, pathLeft] = binarySearchWithPath(root.left, node);
    const [foundInRightChild, rightRight] = binarySearchWithPath(root.right, node);
    
    if(foundInLeftChild) return [true, [root, ...pathLeft]];
    if(foundInRightChild) return [true, [root, ...rightRight]];
    
    return [false, []];
}
```
