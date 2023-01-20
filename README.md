# swappping-two-nodes-of-linkedlist-
swapping two nodes of linkedlist - in java, while taking care of all the boundary cases.
public class Solution {
	public static LinkedListNode<Integer> swapNodes(LinkedListNode<Integer> head, int i, int j) {
        if(head==null || head.next==null || i==j) return head;
        int m = i, n = j;
        if(i>j){
            m = j;
            n = i;
        }
        if(m==0&&n==1){
            LinkedListNode<Integer> temp1 = head.next, temp2 = head.next.next;
            temp1.next = head;
            head.next = temp2;
            return temp1;
        }
        LinkedListNode<Integer>n01 = null;
        LinkedListNode<Integer> temp = head;
        int ct = 0;
        while(ct<m && temp.next!=null){
            n01 = temp;
            temp = temp.next;
            ct++;
        }
        LinkedListNode<Integer>n1 = temp, n10 = temp.next;
        LinkedListNode<Integer>n02 = null;
        while(ct<n&&temp.next!=null){
            n02 = temp;
            temp = temp.next;
            ct++;
        }
        LinkedListNode<Integer>n2 = temp, n20 = temp.next;
        if(m==0){
            n2.next = n10;
            n02.next = n1;
            n1.next = n20;
            return n2;
        }
        if((n-m)==1){
            LinkedListNode<Integer>tent = n01, tent1 = n01.next, tent2 = n01.next.next, tent3 = n01.next.next.next;
            tent.next = tent2;
            tent2.next = tent1;
            tent1.next = tent3;
            return head;
        }
        n01.next = n2;
        n2.next = n10;
        n02.next = n1;
        n1.next = n20;
        return head;


    }
}    
