Download Link: https://assignmentchef.com/product/solved-cs341-project-1-16-small-f-functions
<br>
In Project 1 you’re going to write 16 small functions on list operations both provided by the standard library and useful utility functions.  Submit the 16 functions, each in a separate .fs file as named and provided for you the in Projects folder, in a single zip on Gradescope. In addition, put all your functions into a file named Project01-ALL.fs in a Project1 module inside the file to make all the functions available on a single import.

Programming Exercise

Each function should be written in a separate file.  We have provided the template code in each file, with comments describing the behavior of the code, the function declaration (you may write additional functions as desired, but the computation must begin by invoking the function as given) and some sample code that tests the function you have written against a couple of test cases.  Instructions for the behavior of each function are included in the comments of the template code, and a copy of the template for each function has been included in this document (though using the files directly from the zip should give you less spacing/nonprinting character errors).




YOU MAY NOT INVOKE THE FUNCTION OF THE SAME NAME FROM THE LIST LIBRARY IN YOUR SOLUTION.

<strong> </strong>

<h3>Exercise #01: length L</h3>

The first function to write, length (which you have already written in Homework 6), returns the length of the list passed in a s a parameter and should be written in the Project01-01.fs file.




//

// length L

//

// Returns length of L

//

// Examples: length []  =&gt; 0

//           length [1] =&gt; 1

//           length [1; 3; 98] =&gt; 3

//           length [1; 2; 19; 67] =&gt; 4

//           length [‘a’; ‘b’; ‘c’; ‘d’; ‘e’] =&gt; 5

//           length [“List”; “of”; “strings”] =&gt; 3 //




<h3>Exercise #02:  max L</h3>

The function max returns the value of the maximum element (as determined by the &gt; operator), and should be written in the Project01-02.fs file.




//

// max L

//

// Returns maximum element of L

//

// Examples: max []          =&gt; raises an exception (Unhandled Exception: System.ArgumentException: The input sequence was empty.) //           max [-2; 4]     =&gt; 4

//           max [34]        =&gt; 34

//           max [10; 10; 9] =&gt; 10

//           max [‘a’; ‘e’; ‘c’] =&gt; e //




<h3>Exercise #03:  min L</h3>

The function min returns the value of the minimum element (as determined by the &lt; operator), and should be written in the Project01-03.fs file.




//

// min L

//

// Returns minimum element of L

//

// Examples: min []          =&gt; raises an exception (Unhandled Exception:

System.ArgumentException: The input sequence was empty.)

//           min [-2; 4]     =&gt; -2

//           min [34]        =&gt; 34

//           min [10; 9; 9; 101] =&gt; 9

//           min [‘d’, ‘r’, ‘b’] =&gt; b //

<strong> </strong>

<h3>Exercise #04:  nth L n</h3>

The function nth returns the value of the element at index n of the list and should be written in the Project0104.fs file.




//

// nth L n

//

// Returns nth element of L

//

// Examples: nth []   0       =&gt; raises an exception //           nth [94] 2       =&gt; raises an exception

//           nth [94]  0      =&gt; 94

//           nth [94]  -1     =&gt; raises an exception

//           nth [1; 45; 6] 1 =&gt; 45

//           nth [1; 45; 6] 5 =&gt; raises an exception

//           nth [‘q’; ‘w’; ‘e’; ‘r’; ‘t’; ‘y’] 5 =&gt; ‘y’

// You may not call List.nth, List.Item, .[], etc directly in your solution. //




<h3>Exercise #05:  map F L</h3>

The function map returns a new list created from the elements of the list passed in (L), after they have been transformed by the application of function F.  This function does not modify the original list, creating a brand new list one element at a time.  The map function should be written in the Project01-05.fs file




//

// map F L

//

// Maps function F to L – Returns list produced by mapping function F over L //

// Examples: map (fun x -&gt; x + 1) []                  =&gt; []

//           map (fun x -&gt; x + 1) [23]                =&gt; [24]

//           map (fun x -&gt; x – 1) [23; 43]            =&gt; [22; 42]

//           map (fun x -&gt; x – 1) [23; 43]            =&gt; [22; 42]

//           map (fun i -&gt; (char i)) [99; 97; 115; 116] =&gt; [‘c’;’a’;’s’;’t’]

//           map (fun c -&gt; (char ((int c)+1))) [‘a’;’b’;’c’]  =&gt; [‘b’;’c’;’d’] //




<h4><u>Exercise #06</u>:  iter F L</h4>

The function iter behaves like map, but instead of building a new list from the elements of L, applies F and then throws away the result.  This is generally used only for functions which have side-effects, such as printing functions which do not change memory, but have the side effect of outputting to the screen.  The iter function should be written in the Project01-06.fs file.




//

// iter F L

//

// Applies function F to the elements of L

//

// Examples: iter (fun x -&gt; printfn “%A squared is %A” x (x*x) ) [1; 2] =&gt; 1 squared is 1 //                                                                         2 squared is 4

//           iter (fun x -&gt; printf “%c” x) [‘t’; ‘r’; ‘u’; ‘e’]     =&gt; true

//           iter (fun x -&gt; printfn “Iterating…”) []              =&gt;  //

<strong> </strong>

<h4><u>Exercise #07</u>:  reduce F L</h4>

The function reduce takes a binary function, and pairwise applies the function to the elements of the list.  The first application of the function takes the first and second elements as parameters, each following application uses the result of the previous application as the first parameter, and the next element of the list as the second parameter.  The reduce function should be written in the Project01-07.fs file.




//

// reduce F L

//

// reduces L to a single value by applying function F

//

// Examples: reduce (fun x y -&gt; x+y) []             =&gt; Unhandled Exception:

System.ArgumentException: The input list was empty.

//           reduce (fun x y -&gt; x*y) [23; 4]        =&gt; 92

//           reduce (fun x y -&gt; x+y) [23; 43; -60]  =&gt; 6

//           reduce (fun x y -&gt; if x &gt; y then x else y)

//                  [‘c’; ‘a’; ‘n’; ‘a’; ‘d’; ‘a’]  =&gt; ‘n’  //

<strong> </strong>

<h4><u>Exercise #08</u>:  fold F start L</h4>

The function fold applies a function f to each element of the collection by threading an accumulator argument through the computation.  What this means is that the first parameter of the function initially has the value passed in to the accumulator, and then the result of each application of the function between the accumulator and an element of the list becomes the new accumulator for the next step.  These “updates” to the accumulator are accomplished via new values to the parameter for each function invocation.  The fold function should be written in the Project01-08.fs file.




//

// fold F accumulator L //

// Applies a function f to each element of the collection, threading an accumulator argument through the computation.

//

// Returns a value

//

// Examples:

//          fold (fun x y -&gt; x&amp;&amp;y) true [] =&gt; true

//          fold (fun x y -&gt; x+(string y)) “Hello ” [‘W’;’o’;’r’;’l’;’d’] =&gt; “Hello World”

//          fold (fun x y -&gt; x+y) -60 [23; 43; 6] =&gt; 12

//          fold (fun x y -&gt; x*y) 1 [23; 5; 80] =&gt; 9200 //

<strong> </strong>

<h4><u>Exercise #09</u>:  flatten L</h4>

The function flatten takes a list of lists, and puts the elements all together into a single list.  The flatten function should be written in the Project01-09.fs file.




//

// flatten L

//

// Flatten a list of lists to a single list

//

// Returns list

//

// Examples:

//          flatten [[]] =&gt; []

//          flatten [[1]] =&gt; [1]

//          flatten [[1; 2]; [2; 3; 4]] =&gt; [1; 2; 2; 3; 4]

//   flatten [[‘o’; ‘n’]; [‘ ‘]; [‘w’; ‘i’; ‘n’; ‘g’; ‘s’]] =&gt;  //      [‘o’; ‘n’; ‘ ‘; ‘w’; ‘i’; ‘n’; ‘g’; ‘s’]

//




<h4><u>Exercise #10</u>:  zip L1 L2</h4>

The function zip combines the elements of two lists pairwise, resulting in a list of tuples, where the first tuple in the list contains the first element of L1 as the first element, and the first element of L2 as the second element The zip function should be written in the Project01-10.fs file.




//

// zip L1 L2

//

// Zip two lists

//

// Returns list of tuples

//

// Examples:

//          zip [] [] =&gt; []

//          zip [1] [1] =&gt; [(1, 1)]

//          zip [1; 2; 40] [3; 56; 6] =&gt; [(1, 3); (2, 56); (40, 6)]

//          zip [1; 2; 3] [‘a’; ‘b’; ‘c’] =&gt; [(1, ‘a’); (2, ‘b’); (3, ‘c’)] //




<h3>Exercise #11:  unzip L</h3>

The function unzip takes a list of pairs (tuples of size 2) and splits them apart into two lists.  Since two lists are returned by this function, the return value is a tuple containing two lists.  The unzip function should be written in the Project01-11.fs file.

<strong> </strong>

//

// unzip L

//

// Unzip a list of pairs to a pair of lists

//

// Returns tuple of lists

//

// Examples:

//          unzip [] =&gt; ([], [])

//          unzip [(1, 3); (2, 56); (40, 6)] =&gt; ([1; 2; 40], [3; 56; 6])

//          unzip [(1, ‘a’); (2, ‘b’); (3, ‘c’)] =&gt; ([1; 2; 3], [‘a’; ‘b’; ‘c’])

//




<h4><u>Exercise #12</u>:  range stop</h4>

The function range creates a list of integers from 0 to the stop value.  The list should not include the stop value, but instead contain stop elements (0 to stop-1).  The range function with a single parameter should be written in the Project01-12.fs file.  Do not use List Comprehensions, build the list recursively.




//

// range stop

//

// Returns the range of integers starting from 0

// and using the stop as the upper limit, non-inclusive

//

// Examples:

//          range 0 =&gt; []

//          range 1 =&gt; [0]

//          range 10 =&gt; [0; 1; 2; 3; 4; 5; 6; 7; 8; 9]

//




<h4><u>Exercise #13</u>:  range2 start stop</h4>

The function range2 creates a list of integers from start to stop.  The list should include start but not stop, having (stop-start) elements.  Called with a 0 as the value of start, should behave the same as the single parameter version of range.  The range2 function with two parameters should be written in the Project0113.fs file.  Do not use List Comprehensions, build the list recursively.

<strong> </strong>

//

// range2 start stop

//

// Returns a list of integers over the range from start as the lower limit (inclusive) to stop as the upper limit (non-inclusive)

//

// Examples:

//          range2 0 0 =&gt; []

//          range2 0 1 =&gt; [0]

//          range2 1 5 =&gt; [1; 2; 3; 4]

//          range2 -2 3 =&gt; [-2; -1; 0; 1; 2]

//




<h4><u>Exercise #14</u>:  range3 start stop step</h4>

The function range3 creates a list of integers from start to stop moving step values at a time.  The list should include start but not stop, having floor((stop-start)/step) elements.  Called with a 0 as the value of step, should behave the same as the two parameter version of range.  The range3 function with three parameters should be written in the Project01-14.fs file.  Do not use List Comprehensions, build the list recursively.




//

// range3 start stop step

//

// Returns the a list of integers over the range from start as the lower limit (inclusive) to stop as the upper limit (non-inclusive), incrementing by the amount specified in step

//

// Examples:

//          range3 0 0 1   =&gt; []

//          range3 0 2 1   =&gt; [0; 1]

//          range3 1 5 2   =&gt; [1; 3]

//          range3 5 -2 -3 =&gt; [5; 2; -1]

//




<h4><u>Exercise #15</u>:  slice L start stop</h4>

The function slice returns a slice of the list using the limits provided and should be written in the Project0115.fs file.  Instructions for the behavior of this function are included in the comments, and a copy of the file is included here.

<strong> </strong>

//

// slice L start stop

//

// Returns a slice of the list with the specified starting and ending indices (start inclusive and end non-inclusive)

// This function creates a list containing the copied values from the input list between the starting and ending index

//

// Examples:

//          slice [1; 2; 3; 4; 5] 0 0 =&gt; []

//          slice [1; 2; 3; 4; 5] 0 1 =&gt; [1]

//          slice [1; 2; 3; 4; 5] 1 4 =&gt; [2; 3; 4]

//          slice [1; 2; 3; 4; 5] 0 5 =&gt; [1; 2; 3; 4; 5]

//          slice [1; 2; 3; 4; 5; 6; 7; 8; 9; 10] 6 2 =&gt; [] //




<h4><u>Exercise #16</u>:  filter F L</h4>

The function filter applies the predicate function F to the elements of list L and returns a list containing only the elements satisfying the predicate function.  The filter function should be written in the Project01-16.fs file.




//

// filter F L //

// Applies the function F to the elements of list L and returns a list containing only the elements from L satisfying the condition

//

// Examples:

//          filter (fun param -&gt; false) [1; 2; 3] -&gt; []

//          filter (fun param -&gt; true) [1; 2; 3] -&gt; [1; 2; 3]

//          filter (fun x -&gt; x % 2 = 0) [1; 2; 3; 4; 5; 6] -&gt; [2; 4; 6]

//          filter (fun x -&gt; x % 5 = 0) [1; 5; 3; 15; 25] -&gt; [5; 15; 25]

//          filter (fun (s,x) -&gt; s.Length &lt;= 4) [(“Cat”, 10); (“Deer”, 3); (“Giraffe”, 13)] -&gt; [(“Cat”, 10); (“Deer”, 3)]  //

<h2>Grading and Electronic Submission</h2>

The functions are in separate files to make them easier to test for you.  In order to make your submission easier to test for us, put all the files into Project01-ALL.fs in the Project1 module so all of the functions will be accessible from our testing application.  Ensure that your functions have no side effects such as outputting to the console with printfn otherwise they will be marked as incorrect.  When you’re ready, submit your 15 source code files “Project01-01.fs” .. “Project01-16.fs” IN ADDITION TO the “Project01-ALL.fs” file on Gradescope under “Project01”.




[ <em><u>Note</u>: if you added additional code to the Project01-ALL.fs for testing purposes, such as a main() function, you’ll need to comment out / delete that code before submitting.</em> ]


