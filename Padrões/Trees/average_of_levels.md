637. Average of Levels in Binary Tree
https://leetcode.com/problems/average-of-levels-in-binary-tree

A solução é basicamente usar um BFS, já que o problema pede a média por nível. Porém, o BFS por si só não informa qual o nível que está sendo processado, para isso, é necessário o seguinte ajuste: Consultar o tamanho da fila a cada iteração e remover essa quantidade de elementos por vez. Dessa forma, cada iteração sempre estará processando todos os nós de um nível, visto que, no início do loop, somente nós do mesmo nível estão na fila.
Obs. Lembrar de utilizar long para acumular valores que podem estourar um int.
```Java
class Solution {

    public List<Double> averageOfLevels(TreeNode root) {

        List<Double> averages = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int width = queue.size();
            long sum = 0;
            for(int i=0; i<width; i++){
                TreeNode current = queue.poll();
                sum += current.val;
                if(current.left != null) queue.offer(current.left);
                if(current.right != null) queue.offer(current.right);
            }
            averages.add(Double.valueOf(sum) / width);
        }
        return averages;
    }
}
```