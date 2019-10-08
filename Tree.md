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

Tree.prototype.insert = function(val){
	let n = new Node(val);
	let current = this.root;
	if(current === null){
		this.root = n;
		return;
	}
	while(current !== null){
		if(current.value < val){
            if(current.right){
                current = current.right;
            } else {
				current.right = n;
				return;
			}
		}
        if(current.value >= val){
            if(current.left){
                current = current.left;
            } else {
                current.left = n;
                return;
            }
        } 
    }
}

```
