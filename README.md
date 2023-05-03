Download Link: https://assignmentchef.com/product/solved-cpts355-homework-2
<br>
<ol>

 <li><strong>intersect, intersectTail, and intersectAll </strong></li>

</ol>

<h1>(a) intersect</h1>

The function intersect takes two lists, l1 and l2, and returns a list including the elements that exists in both lists. The resulting list should not include any duplicates. The elements in the output can have arbitrary order.

You may use the built in elem function or the HW1 exists function in your solution.




The type of intersect can be   intersect :: Eq a =&gt; [a] -&gt; [a] -&gt; [a]

Examples:

<strong>&gt;</strong> intersect [2,2,5,6,6,8,9] [1,3,2,2,4,4,5,7,8,10]

[2,5,8]

<strong>&gt;</strong> intersect [5,6,7,8,9] [8,8,10,10,11,12,5]

[5,8]

<strong>&gt;</strong> intersect [“a”,”b”,”d”] [“c”,”e”,”f”,”g”]

[]

<strong>&gt; </strong>intersect [1,2,3] []

[]




<h1>(b) intersectTail</h1>

Re-write the intersect function from part (a) as a tail-recursive function.  Name your function intersectTail.

The type of intersectTail should also be    Eq a =&gt; [a] -&gt; [a] -&gt; [a] You may use the same test cases provided above to test your function.




<h1>(c) intersectAll</h1>

Using intersect function defined above and the foldr (or foldl) function, define intersectAll which takes a list of lists and returns a list containing the intersection of all the sublists of the input list. <strong>Provide an answer using </strong><strong>foldr (or </strong><strong>foldl); without using explicit recursion. </strong>

The type of intersectAll should be  one of the following:

intersectAll:: (Foldable t, Ord a) =&gt; t [a] -&gt; [a]  OR intersectAll:: Ord a =&gt; [[a]] -&gt; [a]




Examples:

<strong>&gt;</strong> intersectAll [[1,3,3,4,5,5,6],[3,4,5],[4,4,5,6],[3,5,6,6,7,8]] [5]

<strong> </strong>

<strong>&gt;</strong> intersectAll [[3,4],[-3,-4,3,4],[-3,-4,5,6]]

[ ]




<strong>&gt;</strong> intersectAll [[3,4,5,5,6],[4,5,6],[],[3,4,5]]

[ ]




<strong> </strong>

<h2>2. partition</h2>

partition function takes a predicate function (op) and a list (iL) as input, and returns a 2-tuple  (left,right)  as output where left is the list of the elements (e<sub>i</sub>) in iL for which  (op e<sub>i</sub>) evaluates to True, and right is the list of those elements in iL for which (op e<sub>i</sub>) evaluates to False. The elements of left and right retain the same relative order they possessed in iL.  Your function shouldn’t need a recursion but should use the higher order function ”filter”. You may define additional helper function(s), <u>which are not recursive</u>.

The type of the partition function should be:

partition :: (a -&gt; Bool) -&gt; [a] -&gt; ([a], [a])




Examples: <em> </em>

<strong>&gt;</strong> partition (x -&gt; (x&lt;=4)) [1,7,4,5,3,8,2,3]

([1,4,3,2,3],[7,5,8])

<strong>&gt;</strong> partition null [[1,2],[1],[],[5],[],[6,7,8]]

([[],[]],[[1,2],[1],[5],[6,7,8]])

<strong>&gt;</strong> partition (elem 1) [[1,2],[1],[],[5],[],[6,7,8]]

([[1,2],[1]],[[],[5],[],[6,7,8]])

<strong>&gt;</strong> partition (x -&gt; (x&lt;=4)) []

([],[])

<em> </em>

<ol start="3">

 <li><strong>sumL, sumMaybe, and sumEither</strong></li>

</ol>

<strong> </strong>

<h1>(a)sumL</h1>

Function sumL is given a list of lists and it returns the sum of all numbers in all sublists of the input list. Your function shouldn’t need a recursion but should use functions “map” and “foldr”.

You may define additional helper functions <u>which are not recursive.</u>

The type of the sumL function can be one of the following:  sumL :: (Num b) =&gt; [[b]] -&gt; b sumL :: (Num b, Foldable t) =&gt; [t b] -&gt; b




Examples:

<strong>&gt;</strong> sumL [[1,2,3],[4,5],[6,7,8,9],[]]

45

<strong>&gt;</strong> sumL [[10,10],[10,10,10],[10]]

60

<strong>&gt;</strong> sumL [[]]

0

<strong>&gt;</strong> sumL []

0




<h1>(b)sumMaybe –</h1>

Function sumMaybe is given a list of Maybe lists and it returns the sum of all Maybe values  in all sublists of the input list. Your function shouldn’t need a recursion but should use functions “map” and “foldr”. You may define additional helper functions <u>which are not recursive.  </u>The type of the sumMaybe function can be one of the following:

sumMaybe :: (Num a) =&gt; [[(Maybe a)]] -&gt; Maybe a

sumMaybe :: (Num a, Foldable t) =&gt; [t (Maybe a)] -&gt; Maybe a

<em>(Note: To implement </em>sumMaybe<em>, change your </em><em>sumL function and your helper function in order to handle </em><em>Maybe values instead of numbers. Assume the integer value for </em><em>Nothing is </em><em>0.)</em>




Examples:

<strong>&gt;</strong> sumMaybe [[(Just 1),(Just 2),(Just 3)],[(Just 4),(Just 5)],[(Just 6),Nothing

],[],[Nothing ]]

Just 21

<strong>&gt;</strong> sumMaybe [[(Just 10),Nothing],[(Just 10), (Just 10), (Just 10),Nothing,Nothing]] Just 40

<strong>&gt;</strong> sumMaybe [[Nothing ]]

Nothing

<strong>&gt;</strong> sumMaybe []

Nothing




<h1>(c)sumEither</h1>




Define the following Haskell datatype:

data IEither  = IString String | IInt Int                 deriving (Show, Read, Eq)







Define an Haskell function sumEither that takes a list of IEither lists and it returns an IInt value which is the sum of all values  in all sublists of the input list. The parameter of the IString values should be converted to integer and included in the sum. You may use the following function to convert a string value to integer.

getInt x = read x::Int




Your sumEither  function shouldn’t need a recursion but should use functions “map” and “foldr”. You may define additional helper functions <u>which are not recursive.  </u>The type of the sumEither function can be one of the following:

sumEither:: Foldable t =&gt; [t IEither] -&gt; IEither sumEither:: [[IEither]] -&gt; IEither




Examples:

<strong>&gt;</strong> sumEither [[IString “1”,IInt 2,IInt 3],[IString “4”,IInt 5],[IInt 6,IString

“7”],[],[IString “8”]]

IInt 36

<strong>&gt;</strong> sumEither [[IString “10” , IInt 10],[],[IString “10”],[]]

IInt 30

<strong>&gt;</strong> sumEither  [[]]

IInt 0

<strong> </strong>

<strong>                 </strong>

<h2>4.  depthScan, depthSearch, addTrees</h2>

In Haskell, a polymorphic binary tree type with data both at the leaves and interior nodes might be represented as follows:

data Tree a = LEAF a | NODE a (Tree a) (Tree a)               deriving (Show, Read, Eq)




<h1>(a) depthScan –</h1>

Write a function depthScan that takes a tree of type (Tree a) and returns a list of the a values stored in the leaves and the nodes.  The order of the elements in the output list should be based on the depth-first order traversal of the tree.

The type of the depthScan function should be:   depthScan :: Tree a -&gt; [a]

<sup>                                </sup>1




Examples:

t1 =  NODE           “Science”

(NODE “and” (LEAF “School”)(NODE

“Engineering”

(LEAF “of”)

(LEAF “Electrical”)))

(LEAF “Computer”) depthScan t1

[“School”,”of”,”Electrical”,”Engineering”,”and”,”Computer”,”Science”]




t2 = NODE 1 (NODE 2 (NODE 3 (LEAF 4) (LEAF 5)) (LEAF 6)) (NODE 7 (LEAF 8) (LEAF 9)) depthScan t2

[4,5,3,6,2,8,9,7,1]

depthScan (LEAF 4)

[4]




<h1>(b) depthSearch</h1>

Write a function depthSearch that takes a tree of type (Tree a) and a value and returns the level of the tree where the value is found. If the value doesn’t exist in the tree, it returns -1.  The tree nodes should be visited with depth-first -order traversal and the level of the first matching node should be returned.  The type of the depthSearch function can be:

depthSearch :: (Ord p, Num p, Eq a) =&gt; Tree a -&gt; a -&gt; p













t3 = NODE 1 (NODE 2 (NODE 3 (LEAF 2) (LEAF 5)) (LEAF 1)) (NODE 1 (LEAF 8) (LEAF 5)) depthSearch t3 1

<ul>

 <li>depthSearch t3 5</li>

 <li>depthSearch t3 8</li>

</ul>

3 depthSearch t3 4

-1




<h1>(c) addTrees –</h1>

Write a function addTrees that takes two (Tree int)  values and returns an (Tree int) where the corresponding nodes from the two trees are added. The trees might have different depth. You should copy particular branches/nodes of the trees if the other tree doesn’t have that branch/node. See the example below.

The type of the addTrees function can be:

addTrees :: Num a =&gt; Tree a -&gt; Tree a -&gt; Tree a

<sup>                                </sup>1                    1                      2

<h1>+   =</h1>

<sup> </sup>4     5                        10 11         4      5 10 11







We can create the above Tree(s) as follows:  left :

left = NODE 1 (NODE 2 (NODE 3 (LEAF 4) (LEAF 5)) (LEAF 6)) (NODE 7 (LEAF 8) (LEAF 9)) right:

right = NODE 1 (NODE 2 (LEAF 3) (LEAF 6)) (NODE 7 (NODE 8 (LEAF 10) (LEAF 11)) (LEAF 9))




And addTrees left right will return the rightmost (Tree Int) which is equivalent to the following:

NODE 2

(NODE 4 (NODE 6 (LEAF 4) (LEAF 5)) (LEAF 12))

(NODE 14 (NODE 16 (LEAF 10) (LEAF 11)) (LEAF 18))

<h2>5.  Tree examples  – 4%</h2>

Create <u>two</u> trees of type Tree. The height of both trees should be at least 4. Test your functions depthScan, depthSearch, addTrees with those trees. The trees you define should be different than those that are given.




Here is some additional test data.

l1 = LEAF “1” l2 = LEAF “2” l3 = LEAF “3” l4 = LEAF “4” n1 = NODE “5” l1 l2 n2 = NODE “6” n1 l3 t4 = NODE “7” n2 l4

depthScan t4

[“1″,”2″,”5″,”3″,”6″,”4″,”7”]

<h2>Testing your functions</h2>

We will be using the HUnit unit testing package in CptS355.  See  <u>http://hackage.haskell.org/package/HUnit</u>  for additional documentation.




The file HW2SampleTests.hs provides at least one sample test case comparing the actual output with the expected (correct) output for each problem.  This file imports the HW2 module (HW2.hs file) which will include your implementations of the given problems.

You are expected to add <strong>at least 2 more test cases</strong> for each problem. Make sure that your test inputs cover all boundary cases. Choose test input different than those provided in the assignment prompt.

In HUnit, you can define a new test case using the TestCase function and the list TestList includes the list of all test that will be run in the test suite. So, make sure to add your new test cases to the TestList list. All tests in TestList will be run through the “runTestTT tests” command.




If you don’t add new test cases you will be deduced at least 5% in this homework.




<em><u>Important note about negative integer arguments:</u></em>

In Haskell, the -x, where x is a number, is a special form and it is a