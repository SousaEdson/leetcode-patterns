# Identificar o início do loop em listas encadeadas
https://leetcode.com/problems/linked-list-cycle-ii

Basicamente utilizar `tortoise and hare` para identificar se existe um loop. Caso exista, retornar o slow para o início da lista e incrementar tanto slow quanto fast, um nó por iteração, até que ambos sejam iguais. Em resumo isso acontece porque a distância do início da lista até o ponto onde slow e fast se encontraram é a mesma distância desse ponto até o começo da lista.

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {

        ListNode slow = head;
        ListNode fast = head;
        boolean containsCycle = false;

        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast){
                containsCycle = true;
                slow = head;
                break;
            }
        }   

        if(!containsCycle) return null;
        while(slow != fast){
            slow = slow.next;
            fast = fast.next;
        }

        return slow;
    }
}
```