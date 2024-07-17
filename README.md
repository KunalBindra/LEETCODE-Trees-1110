# LEETCODE-Trees-1110
The provided code defines a class `Solution` with a method `delNodes` that takes a binary tree `root` and an integer array `to_delete` as input and returns a list of nodes that are not marked for deletion.

Here's a breakdown of the code:

**Class Solution:**

- This class likely implements functionality for manipulating binary trees.

**Method delNodes(TreeNode root, int[] to_delete):**

- This method takes a binary tree `root` and an integer array `to_delete` as input.
- The `to_delete` array contains values of nodes that should be removed from the tree.
- The method returns a `List` containing the nodes that are not present in the `to_delete` array.

**Steps:**

1. **Initialization:**
   - An empty `ArrayList` called `ans` is created to store the nodes that will be returned.
   - A `Set` called `toDeleteSet` is created from the `to_delete` array using streams. This set allows for faster lookups of values to be deleted.

2. **Recursive Helper Function dfs(TreeNode root, Set<Integer> toDeleteSet, boolean isRoot, List<TreeNode> ans):**
   - This recursive function traverses the binary tree and performs the deletion logic.
   - Base Case: If the current node (`root`) is `null`, it returns `null`.
   - `deleted`: A boolean variable is set to `true` if the current node's value (`root.val`) exists in the `toDeleteSet`.
   - **Handle Root Node:**
     - If `isRoot` is `true` (meaning the current node is the root of the original tree) and the node is not marked for deletion (`!deleted`), it adds the node to the `ans` list. This ensures the root is included in the result if not marked for deletion.
   - **Handle Children:**
     - Recursive calls are made to the `dfs` function for both the left and right children of the current node.
     - The `isRoot` parameter is set to `false` for the children's recursive calls as they are no longer the root of the subtree.
     - The returned values from the left and right recursive calls are assigned to `root.left` and `root.right` respectively. This maintains the tree structure.
   - **Return Node:**
     - If the current node is marked for deletion (`deleted`), it returns `null`. This effectively removes the node from the tree.
     - Otherwise, it returns the current node (`root`). This keeps the node in the tree.

**Overall:**

The `delNodes` function traverses the tree using a depth-first search approach. It checks each node against the `toDeleteSet`. If a node is marked for deletion, its children are processed recursively as potential new roots for the subtree. Nodes that are not marked for deletion are added to the `ans` list and the tree structure is maintained. Finally, the `delNodes` function returns the list of nodes that are not present in the `to_delete` array.
