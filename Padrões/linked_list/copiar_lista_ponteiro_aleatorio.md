# Copiar lista encadeada com ponteiro aleatório
https://leetcode.com/problems/copy-list-with-random-pointer/description/

- Basicamente utilizar um HashMap com a seguinte função: Armazenar uma relação dos nós antigos para os novos nós. Depois é só construir os apontamentos e utilizar o map para consultar a nova head.

```Java
class Solution {
    public Node copyRandomList(Node head) {
        Map<Node, Node> oldNodeToNewNode = new HashMap<>();
        Node current = head;

        while(current != null){
            Node newNode = new Node(current.val);
            oldNodeToNewNode.put(current, newNode);    
            current = current.next;    
        }

        current = head;
        while(current != null){
            Node newNode = oldNodeToNewNode.get(current);
            newNode.next = oldNodeToNewNode.get(current.next);
            newNode.random = oldNodeToNewNode.get(current.random);
            current = current.next;            
        }

        return oldNodeToNewNode.get(head);    
    }
}
```