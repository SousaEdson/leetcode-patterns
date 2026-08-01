# Reverter lista encadeada
https://leetcode.com/problems/reverse-linked-list/description/

- Manter um nó previous que começa como null e um current no início da lista
- Para cada elemento da lista
  - Salva o próximo elemento em uma variável temporária
  - Aponta o current para o nó anterior
  - previous avança para o próximo
  - current pega o valor de volta da variável temporária
``` Java
class Solution {
    public ListNode reverseList(ListNode head) {

        ListNode previous = null;
        ListNode current = head;

        while(current != null){
            ListNode temp = current.next;
            current.next = previous;
            previous = current;
            current = temp;
        }

        return previous;
    }
}
```
Não é uma regra fixa, mas no geral a ordem das operações em listas parece seguir um padrão: Uma variável recebe um valor logo após o seu valor ter sido lido. No seguinte bloco, por exemplo: 
```java
ListNode temp = current.next;
current.next = previous;
previous = current;
current = temp;
```
O valor de `current.next` é lido e logo em seguida é sobrescrito. Assim segue para todos os outros. Não é uma regra, mas pode ser útil para verificar se nenhuma etapa foi pulada.