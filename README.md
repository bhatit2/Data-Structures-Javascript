# LinkedList-Javascript
Linked list implementation and operations in Javascript

### Find Length of a linkedList
`
LinkedList.prototype.getSize = function(){
	let current = this.root;
	let count = 0;
    while(current !== null){
        count++;
        current = current.next;
    }  
	return count;
}
`
