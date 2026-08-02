# Remoção do nth último elemento de uma lista encadeada
https://leetcode.com/problems/remove-nth-node-from-end-of-list
- Encontrar o nth último elemento é simples, basta descartar os n primeiros nós utilizando `current` e depois avançar `previous` e `current` até que current seja `null`. Dessa forma sempre vai existir uma distância de `n` entre o final e o nth elemento a partir do final
- O segredo aqui é apontar previous incialmente para o dummy. Dessa forma previous vai apontar para o elemento que deve ser removido e nunca vai ser o último elemento, o que faz com que a remoção `previous.next = previous.next.next` possa ser executada sem risco de null pointer.
- Como o elemento removido pode ser o primeiro, é necessário utilizar um dummy pointer. O valor de head não pode ser utilizado como referência.
```Java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode current = head;
        ListNode dummy = new ListNode(0, head);
        ListNode previous = dummy;

        while(n > 0){
            current = current.next;
            n--;
        }
        while(current != null){
            previous = previous.next;
            current = current.next;            
        }
        previous.next = previous.next.next;
        return dummy.next;
    }
}```