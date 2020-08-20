# Linked Lists:

- an array versus a linked list:
![img](https://miro.medium.com/max/700/1*cUehR5S18XSoVLaPNfNzlA.jpeg)

- A Linked List is a sequence of Nodes that are connected/linked to each other.
- There are two types of Linked List - Singly and Doubly. 
- Singly refers to the number of references the node has.
- Doubly refers to there being two (double) references within the node. 
- Nodes are the individual items/links that live in a linked list. 
-  Each node contains a property called Next. 
- The Head is a reference type of type Node to the first node in a linked list.
- The Current reference is a reference type of type Node that is currently being looked at. 
- ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList1.PNG)

--------------
- ### Traversal:
  - The best way to approach a traversal is through the use of a while() loop.
  -  This allows us to continually check that the Next node in the list is not null.
  - If we accidentally end up trying to traverse on a node that is null, a NullReferenceException gets thrown and our program will crash/end.
  - The Current will tell us where exactly in the linked list we are and will allow us to move/traverse forward until we hit the end.
  - EXAMPLE:

 >  <code>ALGORTIHM Includes (value)</code>
  
 > 	<code>// INPUT <-- integer value</code>
	
 > <code>// OUTPUT <-- boolean</code>
	
 >   <code>Current <-- Head</code>
	
 >   <code>	WHILE Current is not NULL</code>
	
 >   <code>	IF Current.Value is equal to value</code>
	
 >   <code>		return TRUE</code>
	
 >   <code>	Current <-- Current.Next</code>
	
 >   <code>return FALSE</code>
 
 ------------
    
 ### Big O:
   - The Big O of time for Includes would be O(n).
   -  This is because, at its worse case, the node we are looking for will be the very last node in the linked list.
   -  n represents the number of nodes in the linked list.
   
---------
### Adding a Node:
  #### Adding O(1):
  - 1 - Set Current equal to Head. This will guarantee us that we are starting from the very beginning.
  - 2 - We can then instantiate the new node that we are adding.
      - The values passed in as arguments into the Add() method will define what the value of the Node will be.
       ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList2.PNG)
      ----------
      - newNode.Next by default is set to null. We want to set newNode.Next property to the same location that the Head node is pointing towards.
      - Because Head is just a reference type, we will be assigning it to the same allocation in memory as the node it is pointing too. In this case, it’s Node1.
       ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList3.PNG)
      -----------
      - At this point in the program we now “technically” have newNode at the beginning of the linked list, but we are not done yet.
      - We now have to re-assign where Head is pointing too. Since Node1 is no longer the first node in the list, we want to re-assign Head to point at newNode.
      - While we are at it, let’s just re-assign current as well to make sure should any further operation start at the new true start of the linked list.
      ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList4.PNG)
      -------------
       - Pseudo code for an Add method on a Linked list:
       
      <pre>	ALGORITHM Add(newNode)
		// INPUT <-- Node to add 
		// OUTPUT<-- No output

			Current <-- Head
			newNode.Next <-- Head
			Head <-- newNode
			Current <-- Head</pre>
      ---------------
  #### Adding a Node O(n):
  ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LLInsert1.PNG)
  - Now let’s create a new node (node6). We will set the value of node6 to be 16. The Next will be null because we haven’t yet attached it into the linked list.
  ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LLInsert2.PNG)
  - Now let’s start the adding. We can do an AddBefore method or an AddAfter.
  - we want check if the value of the next node is equal to the value we are supposed to be watching for.
  - If it is, we want to set the new node (node6)’s .Next equal to the existing node.
  ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LLInsert3.PNG)
  - 1 - Current is pointing to node3.
  - 2 - node3.Next property is equal to node4.
  - 3 - Since this is the node we want to insert before, we can now set our node6.Next property also to node4.
  - We do this at the time the node is found to prevent setting node6.Next to a node that may not exist.
  - 4 - Uh-Oh, now both node3 and node6 are pointing to the same next node. node6 is not quite fully apart of the linked list.
  - 5 - Next, we have to adjust node3.Next to point to the newly created node, node6. 
  - Since we still have Current pointing to node3 this will be a straightforward transaction.
  - We just simply tell Current (because it is pointing to the same memory location as node3) to change it’s Next to point to the new node (node6).
  - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LLInsert4.PNG)
  - And now we have a complete link list with the newly added node exactly where we wanted it.
  - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LLInsert5.PNG)
  -----------
  
  - Pseudo code for an AddBefore method in a linked list

	<pre>	ALGORITHM AddBefore(newNode, existingNode)
		// INPUT <-- New Node, Existing Node
		// OUTPUT <-- No Output

			Current <-- Head

			while Current.Next is not equal to NULL
				if Current.Next.Value is equal to existingNode.Value
					newNode.Next <-- existingNode
					Current.Next <-- newNode

				Current <-- Current.Next;</pre>
        
        ----------
        
        #### Print Out Nodes:
        
         - the pseudo code for a method to print out all the nodes in a linked list:
        
     <pre> ALGORITHM Print()
		// INPUT <-- None
		// OUTPUT <-- string to console

			Current <-- Head

			while Current.Next is not equal to NULL
				OUTPUT <-- "Current.Value --> "
				Current <-- Current.Next

			OUTPUT <-- "Current.Value --> NULL"</pre>
      
     --------------------
     ### Linear data structures:
      - linear data structures, which means that there is a sequence and an order to how they are constructed and traversed.
      - non-linear data structures, items don’t have to be arranged in order, which means that we could traverse the data structure non-sequentially.
     ![img](https://miro.medium.com/max/700/1*Xokk6XOjWyIGCBujkJsCzQ.jpeg)
     
     - Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.
     - ![img](https://miro.medium.com/max/700/1*G43FVT5xJ1n1QDKVNZUxXQ.jpeg)
     ----------------
     - A __static data structure__ needs all of its resources to be allocated when the structure is created; 
     - this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory.
     
     - a __dynamic data structure__ can shrink and grow in memory. 
     - It doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape can change, and the amount of memory it needs can change as well.
     ------------
     #### Parts of a linked list:
     - A linked list is made up of a series of nodes, which are the elements of the list.
     - A single node: It has just two parts: data, or the information that the node contains, and a reference to the next node.
     > A node only knows about what data it contains, and who its neighbor is.
     - ![img](https://miro.medium.com/max/700/1*K0_eV07tJtKQSVGKfP18bw.jpeg)
     
     ------------
     
     #### Lists for all shapes and sizes:
     
      - __Singly linked__ lists are the simplest type of linked list, based solely on the fact that they only go in one direction.
      - There is a single track that we can traverse the list in; we start at the head node, and traverse from the root until the last node, which will end at an empty null value.
      
      - it can also have a reference pointer to its preceding node, too!
      - This is what we call a __doubly linked list__, because there are two references contained within each node: a reference to the next node, as well as the previous node.
      - This can be helpful if we wanted to be able to traverse our data structure not just in a single track or direction, but also backwards, too.
      - ![img](https://miro.medium.com/max/700/1*AeMDLFUjR0w0J4n8CP4H6g.jpeg)
      
      - A __circular linked list__ is a little odd in that it doesn’t end with a node pointing to a null value.
      
      ------------ 
      ![img](https://miro.medium.com/max/500/1*FC0XX0-9Vx7yCS0dTS2Zrw.jpeg)
      - An O(1) function takes constant time, which is to say that it doesn’t matter how many elements we have, 
        or how huge our input is: it’ll always take the same amount of time and memory to run our algorithm.
      - An O(n) function is linear, which means that as our input grows ,
        the space and time that we need to run that algorithm grows linearly.
      - O(n²) function, which clearly takes exponentially more time and memory the more elements that you have. 
      
