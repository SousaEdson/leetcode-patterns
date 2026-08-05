# 100. Same Tree
https://leetcode.com/problems/same-tree

É necessário somente realizar uma travessia pre-order (Root, Left, Right) conferindo se os nós são iguais. O algoritmo é basicamente o seguinte:

- Se ambos forem null, retorna true
- Se um dos dois for null, retorna false
- Se o valor dos dois nós for diferente retorna false
- Explora left e right, retornando true caso ambas retorn em true    

Esse problema poderia ser resolvido com qualquer tipo de travessia, visto que todos os nós precisam ser verificados. Porém, pre-order é mais natural para esse tipo de problema, visto que a exploração das subárvores nem precisa ser feita caso alguma validação na raiz seja falsa.
```Java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null && q == null) return true;
        if(p == null || q == null) return false;
        return p.val == q.val && isSameTree(p.left, q.left) && isSameTree(p.right, q.right);        
    }
}
```