# Binary Search Tree Implementation Step-by-Step

We use recursion to implement the operations. Recursive programs are simple, elegant and intuitive. While implementing the operations using iteration can be a very good programming exercise, it is not advised as it can render the program difficult to read/grasp.

**Note**: Recursion in object-oriented programming should exercise delegation of responsibilities from BST to root which in turn to its left or right, so on and so forth. For example, it is advised to avoid implementing **insert(root,key)** and rather implement as **root.insert(key)**.

Let us now define a BSTNode and BST which contains root which is of BSTNode type.

## 1. Defining a BSTNode and BST

``` java
// BSTNode.java

public class BSTNode {
    protected int data;
    protected BSTNode left;
    protected BSTNode right;

    public BSTNode() { };
    public BSTNode(int d) {
        data = d;
    }
}
```

``` java
// BST.java

public class BST {
    protected BSTNode root;
}
```

``` java
// BSTDriver.java

public class BSTDriver {
    public static void main(String[] args) {
        BST b = new BST();
        b.root = new BSTNode(50);
        System.out.println(b.root.data);  // prints 50
    }
}
```

## 2. Defining insert operation

Before we can do any search on a BST, we have to insert some keys into it. Let's implement insert operation. The insert operation is implemented as follows.

 - The test driver invokes insert on BST instance.
 - The BST instance creates root if it is not present. Otherwise, it invokes insert on root (i.e. delegates the insert responsibility to the root).
 - The root checks if the the key needs to inserted to its left or right. If it is not empty, root recursively delegates to its left or right.

``` java
// BSTNode.java

public class BSTNode {
    protected int data;
    protected BSTNode left;
    protected BSTNode right;

    public BSTNode() { };
    public BSTNode(int d) {
        data = d;
    }
    
    public void insert(int key) {
        // Two cases - decide left or right
        if (key < data)  { // 1. go leftwards
            // Two sub cases - left slot is empty or not
            if (left == null)  // left is available for insertion
                left = new BSTNode(key);
            else  // left is not available, so delegate insert to left child
                left.insert(key);
        }
        else {  // 2. go rightwards
            // Two sub cases - right slot is empty or not
            if (right == null)  // right is available for insertion
                right = new BSTNode(key);
            else  // right is not available, so delegate insert to right child
                right.insert(key);
        }
    }
}
```

``` java
// BST.java

public class BST {
    protected BSTNode root;
    
    public void insert(int key) {
        if (root == null)
            root = new BSTNode(key);
        else
            root.insert(key);
    }
}
```

``` java
// BSTDriver.java

public class BSTDriver {
    public static void main(String[] args) {
        BST b = new BST();
        b.insert(50);
        b.insert(20);
	b.insert(80);
        b.insert(10);
        b.insert(30);
        b.insert(5);
	b.insert(15);
	b.insert(25);
        b.insert(35);
        b.insert(70);
        b.insert(90);
        b.insert(65);
        b.insert(75);
        b.insert(85);
        b.insert(95);
    }
}

/*
                  -----------------50-----------------
                  |                                  |
          -------20------                   --------80--------
          |             |                   |                |
    -----10----     ----30----         -----70----      -----90-----
    |         |     |        |         |         |      |          |
    5        15    25        35       65         75     85         95

*/
```

## 3. Defining search operation

The primary purpose of binary search tree is that it allows searching a key in O(log n) time. Again, the implementation is recursive and applies the principle of delegation.

  - If BST does not contain any node (i.e. root is null), no search can be done. Therefore, return false.
  - Otherwise, delegate the search responsibility to root. 
  - The root checks if key matches it data, if so, it returns true.
  - Otherwise, based on the key value, it delegates the search to its left or its right,provided left or right exists.
  - This process continues until either key matches a data or no match is found and leaf is reached.

``` java
// BSTNode.java

public class BSTNode {
    protected int data;
    protected BSTNode left;
    protected BSTNode right;

    public BSTNode() { };
    public BSTNode(int d) {
        data = d;
    }
    
    public void insert(int key) { ... }
    
    public boolean search(int key) {
        if (key == data)
            return true;
        else if (key < data && left != null)
            return left.search(key);
        else if (key > data && right != null)
            return right.search(key);
        else
            return false;
    }
}
```

``` java
// BST.java

public class BST {
    protected BSTNode root;
    
    public void insert(int key) { ... }
    
    public boolean search(int key) {
        if (root == null)
            return false;
        else
            return root.search(key);
    }
}
```

``` java
// BSTDriver.java

public class BSTDriver {
    public static void main(String[] args) {
        BST b = new BST();
        b.insert(50);
        :
	:
        b.insert(95);
	System.out.println( b.search(43) );  // prints false
        System.out.println( b.search(70) );  // prints true
    }
}
```

## 4. Defining inorder, preorder, postorder traversals

``` java
// BSTNode.java

public class BSTNode {
    protected int data;
    protected BSTNode left;
    protected BSTNode right;

    public BSTNode() { };
    public BSTNode(int d) {
        data = d;
    }
    
    public void insert(int key) { ... }
    public boolean search(int key) { ... }
    
    public void inorder() {
        // Inorder traversal - traverse left, visit this, traverse right
        if (left != null)  // traverse leftwards only if left subtree exists
            left.inorder();
        System.out.print(data + " ");
        if (right != null)  // traverse rightwards only if right subtree exists
            right.inorder();
    }

    public void preorder() {
        // Preorder traversal - visit this, traverse left, traverse right

	// Implement your logic here


    }

    public void postorder() {
        // Postorder traversal - traverse left, traverse right, visit thiser


	// Implement your logic here

    }    
}
```

``` java
// BST.java

public class BST {
    protected BSTNode root;
    
    public void insert(int key) { ... }    
    public boolean search(int key) { ... }
    
    public void inorder() {
        if (root == null)
            return false;
        else
            return root.inorder(key);
    }
    
    public void preorder() {
    	// Implement your logic here
    
    
    }
    
    public void postorder() {
    	// Implement your logic here
    
    
    
    }
}
```

``` java
// BSTDriver.java

public class BSTDriver {
    public static void main(String[] args) {
        BST b = new BST();
        b.insert(50);
        :
	:
        b.insert(95);
	System.out.println( b.search(43) );  // prints false
        System.out.println( b.search(70) );  // prints true
	b.inorder();  // prints 5 10 15 20 25 30 35 50 65 70 75 80 85 90 95
	b.preorder(); // prints 50 20 10 5 15 30 25 35 80 70 65 75 90 85 95
	b.postorder(); // prints 5 15 10 25 35 30 20 65 75 70 85 95 90 80 50
    }
}
```

