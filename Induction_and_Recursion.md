# Induction and Recursion

**Zhenguo Chen**

## Introduction

[Induction](https://en.wikipedia.org/wiki/Mathematical_induction) and [recursion](https://en.wikipedia.org/wiki/Recursion)
are very important concepts in both mathematics and computer science. They are widely used proof
technique which can help us solve lots of complicated problems, such as [Tower of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi).
It proves a given statement in two steps:
1. Base case. Base case is the simplest case whose answer is known by us and does not require
recursion to be proved.
2. Inductive step. In this step, we use a set of rules to reduce all other cases to base case.

This idea can be very helpful for programming. Recursion, as defined in wiki:

>A recursive function definition has one or more base cases, meaning input(s) for which the function produces a result trivially (without recurring), and one or more recursive cases, meaning input(s) for which the program recurs (calls itself). For example, the factorial function can be defined recursively by the equations 0! = 1 and, for all n > 0, n! = n(n − 1)!.

Here are a few examples on how induction and recursion
are used.

## Factorial

Recall from discrete mathematics that factorial is defined as `n! = n*(n-1)*...*1` and `0! = 1`.
Here, our base case is `factorial(0) = 1` and our recursion step is `factorial(n) = factorial(n-1)*n`.
Therefore, for a c++ factorial function, we can do something like the following:

```
int factorial(int n) {
    if (n==0)
        return 1;
    else
        return n*factorial(n-1);
}
```

## Tree Traversal

[Tree Traversal](https://en.wikipedia.org/wiki/Tree_traversal), as defined in wiki:

>In computer science, tree traversal (also known as tree search) is a form of graph traversal and refers to the process of visiting (checking and/or updating) each node in a tree data structure, exactly once. Such traversals are classified by the order in which the nodes are visited.

There are usually three ways for us to traverse a tree: Pre-order, In-order and Post-order. If
we want to print out the data of a given tree with In-order traversal, we can use the following
recursion:

```
// in-order traversal
void helper(node *root) {
    if (root == NULL)
        return;
    
    helper(root->left);
    cout << root->data << " ";
    helper(root->right);
}
void inOrder(node *root) {
    helper(root);    
}
```

With this recursion, Pre-order and Post-order traversal can also be simply solved by changing
the order of function calls:

```
// pre-order traversal                      // post-order
void helper(node *root) {                   void helper(node *root) {
    if (root == NULL)                           if (root == NULL)
        return;                                     return;
        
    cout << root->data << " ";                  helper(root->left);
    helper(root->left);                         helper(root->right);
    helper(root->right);                        cout << root->data << " ";
}                                           }
void inOrder(node *root) {                  void inOrder(node *root) {
    helper(root);                               helper(root);
}                                           }
```

## Tower of Hanoi

As shown in this [video](https://www.youtube.com/watch?v=aMEbboWmVCo), the optimal solution for
Tower of Hanoi with size 4 is 15. So, how about when there are n discs? What is the minimal number
of moves required to solve this problem? Let's think about this with induction:

1. When `n = 1`. Only one move is required. We use `T(n)` to denote the minimal number of moves.
Therefore, we have `T(1) = 1`.
2. When `n` is large, we can first transfer the `n-1` smallest to a different peg (requiring `T(n-1)`
moves), then move the largest (requiring one move), and finally transfer the `n-1` smallest back
onto the largest (requiring `T(n-1)` moves).

Therefore, we have `T(n) = 2*T(n-1)+1`. By adding `1` to both sides of equation, we get `T(n)+1 = 2*(T(n-1)+1)`.
Thus, we have T(n) = 2<sup>n</sup>-1.

## Symmetric Tree

Recursion is widely used in binary tree. Here, as our last example, given a binary tree, how can
we check if this tree is symmetric around its center? Let's think about this in a recursive way:
we want to check if a tree is symmetric, then we need to check if its left child is symmetric to
its right child. However, to do it recursively, we need to go into its left child and right child. By
going into its left child and right child, we lose our global knowledge of the whole tree,
and we will not be able to compare the values between left subtree and right subtree. To solve this
problem, we will need a helper function which accept left subtree and right subtree as parameters.
Here is an example of solution:

```
bool isSymmetric(TreeNode* root) {
    if(root == NULL)
        return true;
    return check(root->left, root->right);
}

bool check(TreeNode* left, TreeNode* right){
    if(!left && !right)
        return true;
    else if(!left || !right)
        return false;
    
    if(left->val != right->val)
        return false;
    else
        return check(left->left, right->right) && check(left->right, right->left);
}
```
We need to pay attention to the last statement--`return check(left->left, right->right) && check(left->right, right->left);`.
When we are checking the whole tree recursively, we want to check if the left subtree of left child is
symmetric to the right subtree of right child, and the right subtree of left child is symmetric to
the left subtree of right child.

The examples above only show us the basic usage of induction and recursion. The true power and
beauty of induction and recursion need more exploration. Hope this essay can encourage those
who are interested to learn more!