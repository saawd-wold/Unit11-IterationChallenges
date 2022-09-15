# Tasks

## For-Loops

1) Look at each given piece of pseudocode. In the folder `ans/ForLoops1Outputs/` fill the files `Out1.txt`, `Out2.txt` and `Out3.txt` with the outputs tht each piece of pseudocode would produce. 
```basic
'Pseudocode 1
x = 2
for i = 1 to 4
    print(x)
next i
```
```basic
'Pseudocode 2
s = "ShineJesusShine"
for end = 5 to 15 step 5
    print(s.substring(0, end))
next end
```
```basic
'Pseudocode 3
'assume prime(x) is true if x is a prime number 
'else false. assume sqrt(x) is the sqare root of x.
for round = 1 to 25
    if prime(round) then
        print("PRIME!")
    else if prime(sqrt(round)) then
        print("SQUARE PRIME!")
    end if
next round
```
2) Java uses the same syntax for for-loops as C, for which there is an explanation in `README.md`. Fill in the for-loop in `src/ForLoops2.java` so that, given an integer `limit` the program outputs the even numbers between `limit` and `limit * 2`. 

   *You only have to complete the line pointed out by the comment, everything else is already set up for you.*

3) In `src/ForLoops3.py`, write a Python program which uses the `range` function to produce a times table in the style of the following (also going up to $12 \times 12$):
```
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
(...)
1 * 12 = 12
2 * 1 = 2
2 * 2 = 4
(...)
4 * 5 = 20
(...)
12 * 11 = 132
12 * 12 = 144
```
*Hint: You will need to use a for-loop inside a for-loop.*

## For-Each-Loops

1) Edit the file `src/ForEachLoops1.py`. It should output the sentence "(...) is a teacher at Woldingham." for each teacher that is specified in the list `teachers` in the first line.
2) In the file `src/ForEachLoops2.py`, write a program that will output "Give me a W", "Give me a O", "Give me a L", and so on until the cheerleaders have spelled out "Woldingham", without using a `range` command.

## While-Loops

1) In `src/WhileLoops1.py`, write a program that receives an integer as input from the user and doubles it repeatedly as long as the number is less than 1000, printing each number generated this way.
2) In `src/WhileLoops2.py`, complete the code that has been begun for you to write a program that receives a positive integer from the user and determines the binary representation, using at least one while-loop. 

   *To add a character `c` to a string `s`, you can use `s.append(c)`.* 

## Do-Until-Loops

In `ans/until.txt`, state whether each of the following True/False statements is true or false.
*Please capitalise your answers (i.e. like "1: True" or "1: False").*

1. Any program that uses a while-loop can be rewritten to use a do-until-loop.
2. If you write a do-until-loop in which the condition is `True`, the loop body will not be executed because the compiler will see that the condition is already True.
3. The difference between a while-loop and a do-until-loop is merely that the former checks the condition before running the body while the latter checks the condition afterwards.
4. Do-until loops are the standard loop to have for a programming language, Python is unusual because it has while-loops but not do-until-loops.
5. Do-until-loops are an example of indefinite iteration.