# Detecção de ciclos em listas encadeadas
https://leetcode.com/problems/linked-list-cycle
### Tortoise and Hare / Floyd cycle detection algorithm 
A ideia é basicamente inicializar um ponteiro `slow` e um `fast` no início da lista. O `slow` avança um nó por iteração enquanto o `fast` avança dois nós por iteração. Dessa forma, a cada iteração a distância para eles aumenta em 1. Caso exista um loop, em algum momento essa distância vai ser exatamente o tamanho do loop, o que só pode acontecer caso os dois nós ocupem a mesma posição.
```java
public class Solution {
    public boolean hasCycle(ListNode head) {        
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null){            
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast) return true;
        }

        return false;
    }
} 
```
### Detalhes de implementação
- Primeiro avança os ponteiros, depois confere se são iguais, para evitar comparar `head` com `head` na primeira iteração
- É necessário verificar por nulidade tanto no fast quanto no `fast.next`. A condição `fast = fast.next.next` depende que tanto `fast` quanto `fast.next` não sejam nulos.