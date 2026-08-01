# Reverter um intervalo de uma Lista Encadeada
https://leetcode.com/problems/reverse-linked-list-ii/

Essa solução consiste de descartar os nós iniciais e reverter normalmente o intervalo. No final é preciso ajustar os apontamentos:
- O primeiro elemento do range deve apontar para o restante da fila
- O último elemento do range deve ser apontado pelo nó que vinha logo antes do range
```Java
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {        
        ListNode dummy = new ListNode(0, head);       
        ListNode previous =  dummy;
        ListNode current = head;

        for(int i=1; i<left; i++){
            previous = current;
            current = current.next;
        }

        ListNode pre = previous;
        ListNode first = pre.next;
        for(int i=left; i <= right; i++){
            ListNode temp = current.next;
            current.next = previous;            
            previous = current;
            current = temp;
        }      

        first.next = current;
        pre.next = previous; 
        return dummy.next;            
    }
}
```
A ideia dessa solução é inserir elemento por elemento no começo do intervalo. Dessa forma, ao final do processo, o intervalo inteiro estará invertido. O processo consiste de:
- Identificar o início do range e manter um ponteiro apontando para o início do range
- Para cada nó da lista, inserir o próximo na primeira posição
```Java
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {

        ListNode dummy = new ListNode(0, head);
        ListNode previous = dummy;

        for(int i=1; i<left; i++){
            previous = previous.next;
        }

        ListNode current = previous.next;        
        for(int i=left; i<right; i++){
            ListNode nextNode = current.next;
            current.next = nextNode.next;
            nextNode.next = previous.next;
            previous.next = nextNode;            
        }

        return dummy.next;        
    }
}
```