## LinkedList operations

### Find Length of a linkedList
```
LinkedList.prototype.getSize = function(){
    let current = this.root;
    let count = 0;
    while(current !== null){
	count++;
	current = current.next;
    }  
    return count;
}
```

### Delete value from Linked List
```
LinkedList.prototype.deleteValue = function(value){
	let current = this.root;
	if(current === null){
		return new Error("cannot delete from an empty list");
	}
	if(current.value === value){
		this.root = current.next;
		return;
	}
	let prev;
	while(current.next !== null){
		prev = current;
		current = current.next;
		if(current.value === value){
			let temp = current.next;
			prev.next = temp;
			return;
		}
	}
	return "value not found";
}
```

### Print middle element of a linked list

```
LinkedList.prototype.printMiddle = function(){
	let slowRef = this.root;
	let fastRef = this.root;
	while( fastRef !== null && fastRef.next !== null){
		slowRef = slowRef.next;
		fastRef = fastRef.next.next;
	}
	console.log(slowRef.value);
}
```

### Get Nth node in a LinkedList
```
LinkedList.prototype.getNthNode = function(n){
	let current = this.root;
	let i = 0;
	while(current !== null){
        if(n === i){
        	return current.value;
        }
		current = current.next;
		i++;
	}
	return "not found";
}
```

### Print List
```
LinkedList.prototype.print = function printNode(node = this.root){
	if(node == null) return;
	console.log(node.value);
	printNode(node.next);
}
```
