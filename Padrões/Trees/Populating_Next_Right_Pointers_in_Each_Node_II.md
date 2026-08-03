# Populating Next Right Pointers in Each Node II
https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii

Basicamente BFS utilizando processando todos elementos de nível por vez, que é feito consultando previamente a largura (tamanho da fila) da árvore. 
Ponto de atenção: Sempre utilizar a variável width caso queira identificar qual a ordem do nó no nível (identificar último/primeiro nó). O width é fixo, enquanto que o tamanho da fila pode estar mudando.
```Java
class Solution {
    public Node connect(Node root) {
        
        if(root == null) return null;
        Queue<Node> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int width = queue.size();
            while(width > 0){
                Node current = queue.poll();
                if(width > 1){
                    current.next = queue.peek();
                }
                if(current.left != null) queue.offer(current.left);
                if(current.right != null) queue.offer(current.right);
                width--;
            }
        }

        return root;
    }
}
```