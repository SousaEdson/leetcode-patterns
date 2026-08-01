# Mergear duas listas encadeadas ordenadas
https://leetcode.com/problems/merge-two-sorted-lists

O algoritmo é:
- Descobre o menor valor
- Joga o menor valor para a dummy list
- Avança o ponteiro da lista que tinha o menor valor
- Avança o ponteiro da dummyList
Dessa forma o ponteiro da dummy list sempre aponta para o último elemento da lista ordenada, enquanto que as listas sempre apontam para o próximo elemento que deve ser comparado.
``` Java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode();
        ListNode current = dummy;

        while(list1 != null && list2 != null){
            if(list1.val < list2.val){
                current.next = list1;
                list1 = list1.next;
            }else{
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        }

        if(list1 == null) current.next = list2;
        else current.next = list1;
        return dummy.next; 
    }
}
```