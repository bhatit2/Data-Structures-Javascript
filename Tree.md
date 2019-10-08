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

Tree.prototype.insert = function preorder(val, node){
	function insertAt(val, node){
        if(node == null){
            return new Node(val);
        }
        if(node.value < val) {
            node.right = insertAt(val, node.right)       
        }
        if(node.value >= val) {
            node.left = insertAt(val, node.left)
        }
    	return node;
    }
	this.root = insertAt(val, this.root);
}
```
