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

Tree.prototype.insertAt = function insertAt(node, value){
    if(node === null) return new Node(value);
    if(value < node.value) node.left = insertAt(node.left, value);
    if(value > node.value) node.right = insertAt(node.right, value);
    return node;
}

Tree.prototype.insert = function(value){
    this.root = this.insertAt(this.root, value);
}

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

Tree.prototype.findMinNode = function findMinNode(node){
    if(node.left === null) return node;
    return findMinNode(node.left);
}

Tree.prototype.findMin = function(node) {
    if(!node) node = this.root;
    return this.findMinNode(node);
}

Tree.prototype.findMaxNode = function findMaxNode(node) {
    if(node.right === null) return node;
    return findMaxNode(node.right);
}

Tree.prototype.findMax = function(node){
    if(!node) node = this.root;
    return this.findMaxNode(node);
}

```
