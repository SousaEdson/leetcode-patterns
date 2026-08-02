# 104. Maximum Depth of Binary Tree
https://leetcode.com/problems/maximum-depth-of-binary-tree

Por definição a profundidade de um nó em uma árvore binária é medida pela quantidade de arestas da raiz até o nó. Esse exercício na verdade pede a quantidade de nós existentes da raiz até o nó.
A solução é basicamente somar 1 à maior profundidade encontrada entre as subárvores da esquerda e da direita. 
```Java
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));        
    }
}
```
Para consultar a profundidade real de uma árvore (maior quantidade de arestas da raíz as folhas) seria necessário realizar a seguinte alteração no caso base:
```java
if(root == null) return -1;
```
Dessa forma, uma árvore que possui somente a raíz possui profundidade 0.
