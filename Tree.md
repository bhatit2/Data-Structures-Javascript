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

Tree.prototype.search = function(value){
    let current = this.root;
    while(current !== null){
	if(current.value === value) return current;
	current = (value < current.value) ? current.left : current.right;
    }
    return "Not found";
}

Tree.prototype.printPreorder = function preorder(node = this.root){
    if(node == null) return;
    console.log(node.value);
    preorder(node.left);
    preorder(node.right);
}

Tree.prototype.printInorder = function inorder(node = this.root){
    if(node == null) return;
    inorder(node.left);
    console.log(node.value);
    inorder(node.right);
}

Tree.prototype.printPostorder = function postorder(node = this.root){
    if(node == null) return;
    postorder(node.left);
    postorder(node.right);
    console.log(node.value);
}

```
