## Binary Search Tree

### Implementation

```
function Node(value) {
  this.value = value;
  this.left = null;
  this.right = null;
}

function Tree() {
  this.root = null;
}
```

### Insertion

```
Tree.prototype.insertAt = function insertAt(node, value){
    if(node === null) return new Node(value);
    if(value < node.value) node.left = insertAt(node.left, value);
    if(value > node.value) node.right = insertAt(node.right, value);
    return node;
}

Tree.prototype.insert = function(value){
    this.root = this.insertAt(this.root, value);
}
```

### Search 

```
Tree.prototype.searchAt = function searchAt(value, node){
    if(node && node.value === value) return node;
    if(value < node.value && node.left !== null) return searchAt(value, node.left);
    if(value > node.value && node.right !== null) return searchAt(value, node.right);
    return "Not Found";
}

Tree.prototype.search = function(value, node){
    if(!node) node = this.root;
    return this.searchAt(value,node);
}
```

### Deletion

```
Tree.prototype.delete = function(value){
    this.root = this.deleteAt(value, this.root, this);
}

Tree.prototype.deleteAt = function deleteAt(value, node, ctx){
	if(node === null) return node;
	if(value < node.value) node.left = deleteAt(value, node.left, this);
	if(value > node.value) node.right = deleteAt(value, node.right, this);
	if(value === node.value){
		if(node.left === null && node.right === node) {
			node = null;
        } else if(node.left === null){
			node = node.right;
			return node;
		} else if(node.right === null){
            node = node.left;
			return node;
        } else {
			let temp = ctx.findMin(node.right);
			node.value = temp.value;
			node.right = deleteAt(temp.value, node.right);
		}
    }
	return node;
}
```

### Pre Order Traversal

```
Tree.prototype.printPreorder = function preorder(node = this.root){
    if(node == null) return;
    console.log(node.value);
    preorder(node.left);
    preorder(node.right);
}
```

### Inorder Traversal

```
Tree.prototype.printInorder = function inorder(node = this.root){
    if(node == null) return;
    inorder(node.left);
    console.log(node.value);
    inorder(node.right);
}
```

### Post Order Traversal

```
Tree.prototype.printPostorder = function postorder(node = this.root){
    if(node == null) return;
    postorder(node.left);
    postorder(node.right);
    console.log(node.value);
}
```

### Find minimum node

```
Tree.prototype.findMinNode = function findMinNode(node){
    if(node.left === null) return node;
    return findMinNode(node.left);
}

Tree.prototype.findMin = function(node) {
    if(!node) node = this.root;
    return this.findMinNode(node);
}
```

### Find maximum node

```
Tree.prototype.findMaxNode = function findMaxNode(node) {
    if(node.right === null) return node;
    return findMaxNode(node.right);
}

Tree.prototype.findMax = function(node){
    if(!node) node = this.root;
    return this.findMaxNode(node);
}
```

