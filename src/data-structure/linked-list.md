# Linked List

```
package linked_list

import "fmt"

type Node struct {
	Value int
	Next  *Node
}

type LinkedList struct {
	Head *Node
}

func (ll *LinkedList) Print() {
	if ll.Head == nil {
		fmt.Println("[]")
		return
	}
	fmt.Printf("[")
	ll.IterateList(func(v int) {
		fmt.Printf("%d->", v)
	})
	fmt.Printf("]\n")
}

func (ll *LinkedList) AddToHead(value int) {
	newHead := Node{
		Value: value,
		Next:  nil,
	}
	if ll.Head != nil {
		newHead.Next = ll.Head
	}
	ll.Head = &newHead
}

func (ll *LinkedList) IterateList(fn func(v int)) {
	for node := ll.Head; node != nil; node = node.Next {
		fn(node.Value)
	}
}

``