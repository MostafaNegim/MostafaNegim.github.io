```go

package linked_list

import "fmt"

type Node struct {
	Value int
	Next *Node
}

type LinkedList struct {
	Head *Node
}

func (ll *LinkedList) Print() {
	var next *Node = ll.Head
	if ll.Head == nil {
		fmt.Println("[]")
		return
	}
	fmt.Printf("[")
	for next != nil {
		fmt.Printf("%d->", next.Value)
		next = next.Next
	}
	fmt.Printf("]\n")
}

func (ll *LinkedList) AddToHead(value int) {
	newHead := Node{
		Value: value,
		Next: nil,
	}
	if ll.Head != nil {
		newHead.Next = ll.Head
	}
	ll.Head =&newHead
}
```