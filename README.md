java c
Algorithms and Data Structures I 
Project 2:   LinkedDS
Background 
This   project   is designed to   increase your experience with linked data structures.   Similar to   Project   1,   you will   work with control structures, class-building, interfaces, and generics   to   create   a   new   linked   data   structure called a Linked   DS. The Linked   DS   will implement the SequenceInterface, so before doing   anything else, take a look at the method comments in   SequenceInterface   .java.
After you finish reviewing SequenceInterface.java, take a look   at   the   client   code   in   Project2.java.   Just   like   Project   1, you cannot   modify any of the code in   SequenceInterface.java   or   Project2.java.
As with most complicated programming assignments, there   are   multiple ways to   implement   the   SequenceInterface   methods, some more efficient than others. The comments in SequenceInterface.java outline the running time (efficiency)   requirements for your   implementations.   I   100%         recommend   pencil    paper   work and drawing pictures to familiarize yourself with the algorithm you’d   like to   implement before you write any   code. 
Note: The   primary   data   structure   in   your   Linked   DS   must   be   a   one-dimensional   array   of   linked   lists. You   may   not   use   any   predefined   Java   collection   class   (e.g. ArrayList) for   your   Linked   DS   data   fields. You   may not declare any one-dimensional arrays except for the alphabet   and for the   return   value   of   any   methods   that return an array (declaring a one-dimensional array   and   then   resizing   it   before   returning   is   OK).
LinkedDS 
Your Linked   DS   class header   must   be:
public class Linked   DS   implements   SequenceInterface   {
You   must   use   the   following   instance   variables   inside   the   Linked   DS   class:
private Node   [] array;   //   1-D   array   of   linked   lists
private int   size   ;   //   the   number of   items   in   the   sequence
private T   [] alphabet   ;   // the   possible   item   values   (e   .g   .,   the   decimal   digits)
private T firstItem;   //the   first   item
private T   lastItem;   //the   last   item
The   Node   private inner class is already defined   in   Linked   DS.java::
private static   class   Node   {
private int   item;   //index   in   alphabet   of   item
private   Node   next   ;
private Node(int   item){
this   .item   =   item;
next   =   null   ;
}
}
Besides the methods in SequenceInterface, the following constructor is required:
public Linked   DS(T   []   alphabet)
Here’s   an   example   of   how   the   Linked   DS   should   work   using   a   1D   array   of   linked   lists.
The   alphabet   for   decimal   digits   is   the   same   as   it   was   in   the example for   Project   1:   {0,   1,   2,   3,   4,   5,   6,   7,   8,   9}.   Remember, your   Linked   DS   must   work   on   any   generic   type, not   just   decimal   integers. Just   like Project   1, let’s   use   the   sequence   9875732732   as   an   example. This   diagram   shows   how   it   would   look   in   a Linked   DS:

Each of the ten digits of the alphabet is   represented   by an   array   of   Node   objects.   Each   entry   in the   array   is   a Node   that serves as the head of a linked   list   that   contains   the   successors   of an   item   in   the   sequence,   stored   by   their position   in the sequence   in ascending order.   In the example,   the   first   two   lists   are   empty   because   0   and   1 are   not   in   the   example   sequence   (9875732732).The   Node   at   index 2 (which represents the decimal digit   2)   has   only   one   other   node   in   its   chain:   a   7,   meaning      that the   item at   index 7   is what follows 2   in the sequence.   There’s   only   one代 写Algorithms and Data Structures I Project 2: LinkedDSJava
代做程序编程语言   item   in   2’s   linked   list   because   2   is      only succeeded by another number once   in the sequence.   The   Node   at   index   7   (which   represents   the   decimal   digit   7) has   three   nodes   because   7,   in   its   three   occurrences   in   9875732732,   is   followed   by   5,   3,   and   3,   in   that order.   Every   pair of consecutive   items   in the sequence   results   in a   node   in the diagram.
The   sequence   9875732732   has   the   following   properties:
first()   ==   9
last()   ==   2
size()   ==   10
isEmpty()   ==   false
getFrequencyOf(3) ==   2
getFrequencyOf(2) ==   2
getFrequencyOf(7, 3) == 2   //73   appeared   twice   in   the   sequence
successors(7) ==   {5, 3} //5   and   3   are   the   unique   items   that   immediately   follow   7 in   the   sequence
If   we   start   with   the   example   sequence   9875732732   and   then   call   push(7), 7 will   be   inserted   to   the   beginning of   the   sequence, it   will   become   79875732732, and   this   diagram   shows   the   whole   model:

Note that a   Node   containing 9 was inserted into   the   beginning   of 7’s   linked   list.   This   is   because   9   is   now   the   first   item that comes after a   7   in the   sequence.
The   sequence   79875732732   has   the   following   properties:
first()   ==   7
last()   ==   2
size()   ==   11
isEmpty()   ==   false
getFrequencyOf(3) ==   2
getFrequencyOf(2) ==   2
getFrequencyOf(7, 3) == 2   //73   appeared   twice   in   the   sequence
successors(7) ==   {9, 5, 3}   //9,   5,   and   3   are   the   unique   items   that   immediately follow 7   in   the   sequence
After   you   have   finished   implementing   Linked   DS, the   Project2.java   test   file   should   compile   and   run correctly and give the same output as shown   in P2Out.txt.   Just   like   Project   1,   I strongly recommend that   you   stub out the code   in   Project2.java and test your methods   incrementally,   instead   of all   at   once   at   the   end. 
Starter Code 
All starter code and example output is   available for   download from   this   folder:
Project 2 Starter Code 
Deliverables 
You are responsible for   submitting:
-               Linked   DS   .javaAll other files will be automatically supplied to Gradescope.   I would   suggest   avoiding   making   code   changes   to      any of the other files (besides stubbing out   Project2.java to test   parts of your   implementations   at   a   time   as   you   work).
If you   use   Eclipse or any other Java   IDEs to work on this   project,   remember to test   on   a   command   line   before   submitting. Sometimes   editors   add   package   lines   to   the   top   of      .java   files   that   will   break   the   autograder.
Hints 
-          To   create   an   array   of   generic   types   (T)   of   size   length,   use   this:
T   []   result =   (T   [])new   Object   [length]   ;
-          Adding @SuppressWarnings("unchecked")   above that line   will prevent your compiler from   warning you about the unchecked   cast.
-             Unlike our linked implementations in   class, the   Nodes   here   always   contain   ints   as   data.   This   is   because   the   ints   represent the   index of the actual T   item   in the alphabet array.
-          See file   P2Out.txt   to   see   how   your   output   should   look.   As   noted,   your   output   when   running   Project2.java should be   identical to this.
- Draw pictures! Drawing a   picture of a   linked chain will   be   much   more   helpful when debugging and         deciding on an efficient way to implement the   different   methods.   If you   have access   to   a whiteboard,   use   it!   If not,   pencil    paper or a   tablet will   also work fine. 



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
