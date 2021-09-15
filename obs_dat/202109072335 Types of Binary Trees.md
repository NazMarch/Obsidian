Types of Binary Trees:

# Full Binary Tree
has 0 or 2 children. We can also say a full binary tree is a binary tree in which all nodes except leaf nodes have two children.

1.

```mermaid
	graph TB
	Root --> N1 
	Root --> N2
	N2 --> N2.1 & N2.2
	N1 --> N1.1 & N1.2
```

2.

```mermaid
	graph TB 
	Root --> N2
	N2 --> N2.1 & N2.2
	N2.1 --> N2.2.1 & N2.2.2
	Root --> N1
```

3.

```mermaid
	graph TB 
	Root --> N1
	N1 --> N1.2 & N1.1
	Root --> N2
```

# Complete Binary Tree
