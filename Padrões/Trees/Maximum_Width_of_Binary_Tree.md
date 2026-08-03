# 662. Maximum Width of Binary Tree
https://leetcode.com/problems/maximum-width-of-binary-tree

O problema basicamente pede pela maior distância entre nós do mesmo nível. A ideia dessa solução é utilizar um BFS processando todos os nós do mesmo nível na mesma iteração e utilizar um hashMap para registrar a posição de cada nó dentro do nível. Dessa forma, o próximo nó a ser inserido na fila sempre vai ter a posição `2 * posicao_atual` caso seja o nó esquerdo e `(2 * posicao_atual) + 1` caso seja o nó direito. Após processar um nível basta computar a distância do primeiro para o último nó e conferir se é maior do que a maior distância encontrada até então.

```Java
class Solution {
    public int widthOfBinaryTree(TreeNode root) {

        Queue<TreeNode> queue = new LinkedList<>();
        Map<TreeNode, Integer> nodeWidth = new HashMap<>();
        int currentLevel = 0;
        int maxWidth = 0;
        queue.offer(root);
        nodeWidth.put(root, 0);

        while(!queue.isEmpty()){
            int width = queue.size();   
            int firstNodeWidth = 0;
            int secondNodeWidth = 0;
            for(int i=0; i<width; i++){
                TreeNode current = queue.poll();
                int currentWidth = nodeWidth.get(current);
                if(i == 0) firstNodeWidth = currentWidth;
                if(i == width - 1) secondNodeWidth = currentWidth;                
                if(current.left != null){
                    queue.offer(current.left);
                    nodeWidth.put(current.left, (2 * currentWidth));
                }
                if(current.right != null){
                    queue.offer(current.right);
                    nodeWidth.put(current.right, (2 * currentWidth) + 1);
                }
            }
            maxWidth = Math.max(maxWidth, secondNodeWidth - firstNodeWidth);
        }    

        return maxWidth + 1;        
    }
}
```