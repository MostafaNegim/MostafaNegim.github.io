# Linked List

```go
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
		fmt.Printf(" %d ->", v)
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

func (ll *LinkedList) AddToEnd(value int) {
	var last = &Node{
		Value: value,
	}
	lastNode := ll.LastNode()
	if lastNode != nil {
		lastNode.Next = last
	} else {
		// List is empty
		ll.Head = last
	}
}

func (ll *LinkedList) IterateList(fn func(v int)) {
	for node := ll.Head; node != nil; node = node.Next {
		fn(node.Value)
	}
}

func (ll *LinkedList) LastNode() *Node {
	var lastNode *Node
	for node := ll.Head; node != nil; node = node.Next {
		if node.Next == nil {
			lastNode = node
		}
	}
	return lastNode
}
func (ll *LinkedList) Length() int {
	var count = 0
	ll.IterateList(func(v int) { count++ })
	return count
}

func (ll *LinkedList) NodeWithValue(value int) *Node {
	for node := ll.Head; node != nil; node = node.Next {
		if node.Value == value {
			return node
		}
	}
	return nil
}

func (ll *LinkedList) AddAfter(nodeProperty, value int) {
	node := ll.NodeWithValue(nodeProperty)

	newNode := &Node{
		Value: value,
		Next: node.Next,
	}
	node.Next = newNode
}
```