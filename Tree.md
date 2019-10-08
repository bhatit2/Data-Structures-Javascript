## Tree Data Structure

### Binary Search Tree implementation

```
function Node(value) {
  this.value = value;
  this.left = null;
  this.right = null;
}

function Tree() {
  this.root = null;
}

Tree.prototype.insert = function preorder(val, current=this.root){
    if(current === null){
	return new Node(val);
    }
    if(current.value < val) {
        current.right = preorder(val, current.right)
    }
    if(current.value >= val) {
        current.left = preorder(val, current.left)
    }
}
```
