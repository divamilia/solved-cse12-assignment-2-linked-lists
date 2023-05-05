Download Link: https://assignmentchef.com/product/solved-cse12-assignment-2-linked-lists
<br>
In this lab you will implement a doubly linked list, and create JUnit tests to verify its proper operation.

<ul>

 <li>You will implement a doubly linked list,</li>

 <li>Build a ListIterator for the list</li>

 <li>Perform some big-O and Theta analysis</li>

</ul>




<h1>Part 1 – Doubly Linked Lists</h1>

Your first task is to implement a doubly linked list called <strong>MyLinkedList </strong>and a corresponding <a href="https://www.google.com/url?q=http%3A%2F%2Fcs.oberlin.edu%2F%7Egr151%2Fjdk-1.6%2Fdocs%2Fapi%2Fjava%2Futil%2FListIterator.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHEewcTS7OOexjqYTBwvNBn94SHnw"><strong>ListIterator </strong></a><a href="https://www.google.com/url?q=http%3A%2F%2Fcs.oberlin.edu%2F%7Egr151%2Fjdk-1.6%2Fdocs%2Fapi%2Fjava%2Futil%2FListIterator.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHEewcTS7OOexjqYTBwvNBn94SHnw">f</a>or your class.

To ease the time burden, we are providing starter files for both testing and the MyLinkedList class itself. It is highly recommended that you generate the javadocs for the supplied

MyLinkedList.java file. You should be able to complete the assignment by properly programming the “Stubbed­out” methods. Make sure to look in the source code for the string

“XXX­CHANGE­XXX”, these indicate method returns that need to be changed to reflect proper function. the return statements are there so that the supplied MyLinkedList.java will compile.




You should also Look up the -private flag to javadoc. You will find it useful. We recommend printing out the generated javadoc and use it as a checklist

<u>MyLinkedList</u>

Your MyLinkedList class is just a subset of the Java Collection’s Framework <a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Futil%2FLinkedList.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNFQQ1P4uI8LNq-OKeDLI9svHYWbcg">LinkedList</a><a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Futil%2FLinkedList.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNFQQ1P4uI8LNq-OKeDLI9svHYWbcg">,</a> and therefore should match its behavior on the described subset.

Implementing the LinkedList interface directly is a bit painful, so Java makes it easier by providing a skeletal implementation of the List interface in the AbstractList abstract class.  <u>Your</u>   <u>MyLinkedList class must extend</u> <a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Futil%2FAbstractList.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHsS1jrAJ70WqTYcpdDx-U2jaq-MQ">AbstractList</a> <a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Futil%2FAbstractList.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHsS1jrAJ70WqTYcpdDx-U2jaq-MQ">(</a>You will receive no credit if your class does not extend AbstractList directly). The starter file already does this for you.

[Side note, can be skipped: If you look carefully at the AbstractList documentation, you will see that Java recommends that MyLinkedList should actually implement <a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Futil%2FAbstractSequentialList.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHW4ILzU9gPZeJeoBQ_a22nBxmsLA">AbstractSequentialList</a><a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Futil%2FAbstractSequentialList.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHW4ILzU9gPZeJeoBQ_a22nBxmsLA">.</a> The reasons for this are somewhat subtle and should make more sense in a week or two.]

In doubly linked lists, the removal of items can be especially tricky as you need to be sure to properly update the neighbor’s next and previous pointers, as well as handle the special cases for removal from the head (front) or tail of the list.

<strong>You should not allow “null”</strong> objects to be inserted into the list; if the user of your class attempts to do so, your code must throw a <a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Flang%2FNullPointerException.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNGbcS3nSUFjvMjtLu9WiCaUWEx_nw">NullPointerException</a><a href="https://www.google.com/url?q=http%3A%2F%2Fdocs.oracle.com%2Fjavase%2F7%2Fdocs%2Fapi%2Fjava%2Flang%2FNullPointerException.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNGbcS3nSUFjvMjtLu9WiCaUWEx_nw">.</a> Please note that this specification is different from LinkedList from the Java Collection’s Framework, which does allow you to store null objects.

<strong>What follows are the methods that you must implement in your MyLinkedList class. </strong>Before you start, read the online documentation of AbstractList and make sure you can answer the following questions (you do not have to submit the answers):

<ul>

 <li>Which method(s) is (are) defined as abstract in MyLinkedList’s superclass?</li>

 <li>What happens if you do not override the add() method of the superclass and a user of your ADT invokes the add() method?</li>

 <li>According to the AbstractList documentation, what are all the different types of exceptions an ArrayList can throw?</li>

 <li>Constructors</li>

</ul>

You should only need to have a single public 0-argument constructor that creates an empty list and initializes all the necessary variables to track your list, as in the following diagram.

Private Methods Node getNth(int index)

a method that returns the <strong>Node </strong>at a specified index, not the content.

You might also want a removeNode(Node n) method that allowed to keep from duplicating code in your Iterator. But you aren’t required to implement one unless you want to.

<h3>Public             Methods</h3>

<h4>boolean   add(T   data) void add(int index, T data)</h4>

add   an   element   into   this   list    (either    at    end    or    by    index) throw a  NullPointerException  if  the  user  tries  to  add  a  null  pointer throw IndexOutOfBoundsException as needed (same rules as MyArrayList)

Note: the boolean add method will presumably always return true; it is a boolean function due to the method definition in AbstractList

<h4>T get(int i)</h4>

get        contents        at        position        i

throw  IndexOutOfBoundsException  as needed

<strong>T          set(int          i,T           data)</strong> set   the   value    at    index    i    to    data throw NullPointerException if data  is  null throw  IndexOutOfBoundsException  as needed

<h4>T remove(int i)</h4>

remove the element from position i in this list

throw IndexOutOfBoundsException as needed

<strong>void clear()</strong>

remove all elements from the list

boolean isEmpty()

determine if the list is empty

<strong>int size()</strong> return the number of elements being stored

Programming hints

<ul>

 <li>You’ll probably want to create a nested class (that is, a class inside a class) to represent a node in your linked list. A nested class is sometimes called an inner class. To accomplish this, you cannot declare a Node class as public, but you can include it in the same file</li>

</ul>

(and even in the same class) as MyLinkedList. If it is contained within

<strong>MyLinkedList&lt;T&gt;</strong>, then it can just use the generic label <strong>T </strong>because it is within the class.

<ul>

 <li>public class MyLinkedList&lt;T&gt; extends AbstractList&lt;T&gt; { class Node { // this is called a Nested Class. Only usable within MyLinkedList T data;</li>

</ul>

Node next;

Node prev;




// more code here

}

/* Lots more code will go here */

}

<h2><u>Testing your List</u></h2>

<strong> </strong>

Download the supplied file LinkedListTester.java. This is a starter file the defines a <u>small</u> number of tests against the Java Collection’s Framework LinkedList class. ● Compile and run LinkedListTester.java as-is.

<ul>

 <li><strong>Modify this file to create <em>at least </em>10 (ten) additional meaningful tests on the public methods described above</strong>. Recall lecture, where you often want to test the a) common case (all inputs are valid), b) error case (where bad is given and your code reacts accordingly) and c) edge cases (Null elements is a good edge case for this assignment!).  In your README.txt file, briefly describe what each of these tests are attempting to validate. This will test against LinkedList’s.</li>

 <li><strong>Copy </strong>Your LinkedListTester.java and rename it to be MyLinkedListTester.java.</li>

</ul>

(Don’t forget to redefine the class from LinkedListTester to MyLinkListTester), and modify the tests to create MyLinkedList objects.  You should be able to just   change LinkedList to MyLinkedList throughout so you get lines like

<strong>MyLinkedList</strong><strong>&lt;</strong><strong>String</strong><strong>&gt; x </strong><strong>= </strong><strong>new </strong><strong>MyLinkedList</strong><strong>&lt;</strong><strong>String</strong><strong>&gt;(); </strong>

<strong> </strong>

<h1>Part 2 – ListIterator</h1>

(Note that a ListIterator isA Iterator, but has additional methods defined).  ListIterators define the notion of a “cursor” so that a user of the ListIterator can ask for the list element just before the cursor OR the one following the cursor.

Once your MyLinkedList class is working, you will need to create a <a href="https://www.google.com/url?q=http%3A%2F%2Fcs.oberlin.edu%2F%7Egr151%2Fjdk-1.6%2Fdocs%2Fapi%2Fjava%2Futil%2FListIterator.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHEewcTS7OOexjqYTBwvNBn94SHnw">ListIterator</a> <a href="https://www.google.com/url?q=http%3A%2F%2Fcs.oberlin.edu%2F%7Egr151%2Fjdk-1.6%2Fdocs%2Fapi%2Fjava%2Futil%2FListIterator.html&amp;amp;sa=D&amp;amp;sntz=1&amp;amp;usg=AFQjCNHEewcTS7OOexjqYTBwvNBn94SHnw">w</a>hich is returned by the <strong>listIterator() </strong>method. You can do this one of two ways:

<ol>

 <li>Through the use of an anonymous class:</li>

</ol>

public ListIterator&lt;T&gt; listIterator(){ return  new ListIterator&lt;T&gt;(){ // TODO – your code here

}; }

<ol start="2">

 <li>Or through the use of an inner helper class (contained inside the definition of the MyLinkedList class). <strong>This is the approach taken in the example file and is highly recommended</strong>. ListIterators are relatively complex classes. class MyListIterator implements ListIterator&lt;T&gt; {</li>

</ol>

// class variables here

public boolean hasNext() { // your code here

}

// more methods, etc.

}

The ListIterator is able to traverse the list by moving a <u>space at a time in either direction (</u><strong>make certain to write multiple tests t<u>o</u> verify</strong>). It might be helpful to consider that the iterator has size+1 positions in the list: just before the head, between the 0 and 1 index, …, just after the tail.

After one call to next(), the iterator is logically in the state shown below

In either case, you will need to implement all of the methods of a listIterator —

<strong>hasNext()</strong>/<strong>next()</strong>,<strong>hasPrevious()</strong>/<strong>previous()</strong>,

<strong>nextIndex()</strong>/<strong>previousIndex()</strong>, <strong>remove()</strong>, <strong>set(x)</strong>, and <strong>add(x)</strong>. See the

ListIterator JavaDoc for details, but there are notes below.

boolean hasNext()

Return true if there are more elements when going in the forward direction.

<strong>T next()</strong> Return the next element in the list when going forward.  Throw NoSuchElementException if there is no such element

boolean hasPrevious()

Return true if there are more elements when going in the reverse direction.

<strong>T previous()</strong> Return the next element in the list when going backwards. Throw NoSuchElementException if there is no such element

int nextIndex()

Return the index of the element that <strong>would </strong>be returned by a call to next()

Return the list size if at the end of the list

int previousIndex()

Return the index of the element that <strong>would </strong>be returned by a call to previous()

Return -1 if at the start of the list

<strong>void set(T x)</strong> Change the value in the node returned by the most recent next/previous with the new value. Throw an IllegalStateException if neither next nor previous were called

Throw an IllegalStateException if add or remove have been called since the most recent next/previous <strong>void   remove()</strong> Remove the last element returned  by  the  most  recent  call  to  either  next/previous Throw   an   IllegalStateException   if    neither    next    nor    previous    were    called Throw an IllegalStateException if add has been called since the most recent next/previous

void add(T x)

Insert the given item into the list immediately before whatever would have been returned by a call to next()

The new item is inserted before the current cursor, so it would be returned by a call to previous() immediately following.

The value of nextIndex or previousIndex both are increased by one Throw a NullPointerException if x is null.

<strong>Which Exceptions to throw for ListIterator? </strong>

<strong>Your methods should properly throw InvalidStateException, NoSuchElement, and NullPointer exceptions. This means you DO NOT HAVE TO IMPLEMENT throwing ALL exceptions as the javadoc would indicate. In addition to the documentation above, the starter file already indicates through the method header which exceptions you should be throwing in which methods. </strong>

<strong> </strong>Your class MUST support multiple ListIterator instances

When testing your code, we create multiple ListIterator instances on the same Junit test fixture to verify that each instance is independent of all others.  When testing this particular feature of your code, we will NOT invoke the remove() method or add() methods (in other words when testing multiple instance of the ListIterator, the list structure will not be modified, elements might be modified with set()).   We will test the modification routines (add, remove) when just a single ListIterator instance has been created on a Junit test fixture.

<strong> </strong><u>Programming Hints</u>

<strong> </strong>It is useful to have a number of state fields to simplify the writing of the various methods above. Since the cursor of the ListIterator exists logically between 2 nodes, it is useful to just keep references to the next Node and the previous Node. It may also be helpful to keep an int value of the index of the next node.

If you construct your MyLinkedList to use sentinel nodes as discussed in the book and lecture, and you properly throw exceptions for going out of range, you shouldn’t have to worry about checking for null values at the ends of the list since the sentinel nodes are there.

Since set() and remove() both change based on what direction was last being traversed, it makes sense to keep a boolean flag to indicate a forward or reverse direction.

<u>Public Methods to add to MyLinkedList.java</u>

Once you are <strong>sure </strong>your iterator is working, you should override the following methods in MyLinkedList. Each of these should just create a new MyLinkedListIterator and return it.

<strong>ListIterator&lt;T&gt; listIterator()</strong>

<h3>Iterator&lt;T&gt; iterator()</h3>

have these factory methods return your ListIterator class for the current list.

<strong>Note: </strong>You inherit a working ListIterator from AbstractList, but the one you create will be more efficient. We suggest that while you are building and initially testing your ListIterator, you create a differently named factory method to use. You could use names like QQQiterator() and

QQQlistIterator() until you are sure it is working correctly. If you jump right into overriding iterator()/listIterator() then things like toString() may stop working for you.

<u>Testing your Iterator</u>

You’ll want to test your <strong>ListIterator </strong>and be sure that it works properly. As a partial test, look at the supplied JUnit test in MyLinkedListTester.java that creates a fibonacci sequence. You should understand how this particular test works as a sample.

You should also look at the supplied code called Sieve.java which is a LinkedList implementation  of the Sieve of Eratosthenes to compute prime numbers in a range.  It works properly with the  Java Collection Framework LinkedList. You should be able to change one boolean variable (See comments), recompile and have it use your MyLinkedList implementation.  The program should  run properly with either implementation. This is more than a “unit” test, but  it is a good validation of your program.

Apportioning your Time

This is a much more comprehensive programming assignment than HW1. If you approach it incorrectly, it will take too long. Suggested amount of time and order of doing things<strong>. Don’t try to do the assignment all at once. Spread it out over multiple days and make backups of your in-progress code. </strong>

<ol>

 <li>Write tests against LinkedList that will help you develop your Linked list implementation without testing the ListIterator class (beyond what is already in the supplied  starting tests). This will help you understand the LinkedList interface. You (obviously) only need to write tests for methods that are common to both LinkedList and MyLinkedList. . Make sure your test suite runs properly against LinkedList instances. (1 – 2 hours)</li>

 <li>Copy/rename your testing class to MyLinkedListTester, compile it, run it against the supplied outline of MyLinkedList. You should have <em>many </em>test failures.</li>

 <li>Develop the linked list methods (Node inner class, methods). Develop until all the tests you developed passed. Change Sieve.java to use MyLinkedList and verify it works.  ( 2 –  4 hours).</li>

 <li>Develop some test methods for testing the iterator (see the code and notes above). The ListIterator is more involved because of tracking states. Try some tests that move the iterator forwards and backwards. (1 – 2 hours)</li>

 <li>Develop the ListIterator implementation using your tests to help you ( 2 – 4 hours).</li>

 <li>Uncomment the lines near the end of the starter MyLinkedList.java file, to make your ListIterator active.</li>

</ol>

<h3><u>README.txt file</u></h3>

Include in your submission a file named README.txt. The contents of the README.txt file should include the following:

<ol>

 <li>Your name</li>

 <li>Any known problems or assumptions made in your classes or program</li>

</ol>

Look through your programs and make sure you’ve included your name at the top of all of them. We are expecting you to hand in the following files:

<ul>

 <li>java</li>

 <li>java</li>

 <li>README</li>

</ul>

How your assignment will be evaluated.

<ul>

 <li>Coding Style

  <ul>

   <li>Does your class and tester properly generate javadoc documentation</li>

  </ul></li>

</ul>

○ Is your code readable by others

■ consistent indentation (TABs or Spaces is OK)

■ are variables sensibly named

■ are access modifiers (public, private, protected) used appropriately

■ are helper methods used when needed to reduce code duplication

<ul>

 <li>Correctness

  <ul>

   <li>Does your code compile</li>

  </ul></li>

</ul>

○ Does it pass all of <u>your</u> unit tests that you defined

○ Does it pass all of <u>our</u> unit tests (we are users of your ADT implementation, you don’t get access to our unit tests)

■ We’ll check basic functionality, including Exceptions

○ Does your code have any errors (e.g. generates exceptions when it isn’t supposed to) (That would be bad).

<ul>

 <li>Unit test coverage

  <ul>

   <li>Have you created at least 10 more <u>meaningful</u> unit tests? (that’s a bare minimum, you are very likely to have significantly more tests)</li>

  </ul></li>

</ul>

○ Does your unit testing approach for listIterator() appear to be sufficient? We supply you with one unit test for listIterator(), that is not sufficient. Good tests will include testing what happens before the head and after the tail

○ We’re not telling you exactly what to test, that’s part of learning to create approaches to developing and debugging more complicated code. <strong>We are also NOT expecting full test coverage</strong>. Your tests should help you develop your code and insure its proper operation.

PART 2  –  Analyzing Runtime

In this part of the assignment, you will turn in a traditional “homework” (non-programming assignment)

You will submit the following file for this assignment:

<h4>● Part2.txt</h4>

This will be a plain text file (NOT .docx or .pdf or anything else). You should use the ^ symbol to indicate exponentiation (e.g. n<sup>2 </sup>should be written n^2) and write out the words Theta (Θ) and Omega (Ω) where appropriate. At the top of your Part2.txt file, please include the following  header:

CSE 12 Homework 2

Your Name

Your PID

The date

<h4>Warm up with Big-O, Big-Theta and Big-Omega</h4>

True/False. In a section labeled TRUE/FALSE in your Part2.txt file, state whether each of the following equalities are true or false.  You should put the number of the question followed by either the   word True or False. One answer/line. eg.




TRUE/FALSE

<ol>

 <li>True</li>

 <li>False</li>

</ol>




and so on.




<ol>

 <li>n <sup>2</sup> + 100 = O(n <sup>4</sup>)</li>

 <li>n <sup>2</sup> + 100 = O(n <sup>2</sup>)</li>

 <li>n <sup>2</sup> + 100 = O(n)</li>

 <li>n <sup>2</sup> − 1, 000, 000, 000 = O(n)</li>

 <li>n <sup>2</sup> + n = O(n)</li>

 <li>n <sup>2</sup> + n = O(n <sup>2</sup>)</li>

 <li>n <sup>2</sup> * n = O(n <sup>2</sup>)</li>

 <li>n <sup>2</sup> * n = O(n <sup>3</sup>)</li>

 <li>n <sup>2</sup> + log(n) * n <sup>2 </sup>= O(n <sup>2</sup>)</li>

 <li>n <sup>2</sup> + log(n) * n <sup>2 </sup>= O(n <sup>2</sup>)</li>

 <li>n <sup>2</sup> + 100 = Ω(n <sup>4</sup>)</li>

 <li>n <sup>2</sup> + 100 = Ω(n <sup>2</sup>)</li>

 <li>n <sup>2</sup> + 100 = Ω(n)</li>

 <li><em>n </em><sup>2</sup> + <em>n = </em>Ω(n)</li>

 <li><em>n </em>+ 100, 000 = Ω(n)</li>

 <li><em>n </em><sup>2</sup> + <em>n </em>+ 100 = θ(<em>n</em>)</li>

 <li><em>n </em><sup>2</sup> + <em>n </em>+ 100 = θ(<em>n <sup>2</sup></em>)</li>

 <li><em>n </em><sup>2</sup> + <em>n </em>+ 100 = θ(<em>n <sup>3</sup></em>)</li>

 <li><em>n </em><sup>2</sup> * <em>n </em>+ 100 = θ(<em>n <sup>3</sup></em>)</li>

 <li>100 * n log(n) = θ(<em>n log n </em>)</li>

</ol>

<h4>Analyzing running time of code</h4>

In this part you will practice your skills of estimating running time of code snippets.  For each  piece of code below, state the running time of the snippet in terms of the loop limit variable, <em>n</em>.   You should assume that the variables n and sum are already declared and have a value. You should express your answer using Big­O or Big­Θ (Theta) notation, though your Big­O bound will only receive full credit if it is a tight bound. We allow you to use Big-O because it is often theconvention to express only upper bounds on algorithms or code, but these upper bounds are generally understood to be as tight as possible. In all cases, your expressed bounds should be simplified as much as possible, with no extra constant factors or additional terms (e.g. O(n) instead of O(2n+5))

For each piece of code, state the running time and then give a short explanation of why that running time is correct. We are not asking for a formal proof­­you’ll learn how to do that in CSE 101. For now your explanation should simply include an (approximate but reasonable) equation for how many instructions are executed, and then a relationship between your equation and your stated bound. Place your answers in in your <strong>Part2.txt </strong>file in a section labeled RUNTIME. Here is an example:




Ex.

for ( int i = 5; i &lt; n; i++ )

sum++;

Most precise answer:

Running time O(n)

Explanation: There is a single loop that runs n-5 times. Each time the loop runs it executes 1 instruction in the loop header and 1 instruction in the loop header and 1 instruction in the body of the loop. The total number of instructions is 2*(n-5) + 1 (for the last loop check) = 2n-9 = O(n).

A slightly less precise but still acceptable for full credit answer:

Running time: O(n).

Explanation: There is a single loop that runs n-5 times. Each time the loop runs it executes 1 instruction, so the total number of instructions executed is 1* (n­5) = O(n) (also OK: Θ(n)).

<ol>

 <li>for ( int i = 0; i &lt; n; i+=2 ) sum++;</li>

 <li>for ( int i = 1; i &lt; n; i*=2 ) sum++</li>

 <li>for ( int i = 0; i &lt; n; i++ ) for ( int j = 0; j &lt; n; j++ ) sum++;</li>

 <li>for ( int i = 0; i &lt; n; i++ ) sum++</li>

</ol>

for ( int j = 0; j &lt; n; j++ ) sum


// The above are two loops one after the other, NOT nested

<ol start="5">

 <li>for ( int i = 0; i &lt; 2*n; i++ ) sum++</li>

 <li>for ( int i = 0; i &lt; n*n; i++ ) sum++;</li>

 <li>for ( int i = 0; i &lt; n; i++ ) for ( int j = 0; j &lt; n*n; j++ ) sum++;</li>

 <li>for ( int i = 0; i &lt; n; i++ ) for ( int j = 0; j &lt; 10000; j++ ) sum++;</li>

</ol>

<h3>TURNING IN YOUR ASSIGNMENT</h3>

Similar to PR1, we will supply you a bundlePR2 and checkCompilePR2 script that are to be run on the UCSD lab machines under your cs12s&lt;zz&gt; account. The resulting tar file upon successful creation will then be uploaded to gradescope.




The following will be collected

<ul>

 <li><strong>MyLinkedList.java </strong>● <strong>MyLinkedListTester.java </strong>● <strong>README.txt</strong>.</li>

</ul>

<h4>● Part2.txt</h4>





