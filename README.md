# Iteration

Iteration is the basic idea of repeating a number of instructions multiple times without writing out the instructions more than once.

It is commonly also called *looping* because the programming structures most languages use are called *loops*. In the GCSE, you will have met two kinds of loops:

* For-loops
* While-loops

For-loops are an example of so-called *definite* iteration, meaning that we can deduce the number of repetitions a priori (before we run the code), while while-loops are an example of *indefinite* iteration because the number of iterations may vary based on events at run-time. In the A-Level, you will be required to know one more kind of indefinite iteration (do-until-loops), and because we are working with Python, I want to show you the difference between classical for-loops and the structure that Python provides in their place.

## Basics: For-loops

A for-loop in the classical sense defines a counter variable, i.e. a variable of integer type which steps between two given values. For instance, a for loop may use a counter variable called `i` which begins at 1 and is incremented by 1 after every repetition of a given block of code until it reaches 5, after which the code would stop being repeated. Within the given block of code, the *loop body*, the variable `i` is available to be used, and on each repetition, the value of it will be different. In the pseudocode that the exams will use, this may look like this:

```basic
for i=1 to 5
    print(i)
next i
```
and the output from this program would be the following:
```
1
2
3
4
5
```
We could use the variable `i` like any other variable within the body of the loop, but outside of it, the variable does not exist. This is called being *out of scope*, which we will discuss in much more detail when talking about subroutines. 

In the exam pseudocode, for-loops are inclusive of the upper limit for the counter variable, so the loop will include a repetition where the value of the counter variable is equal to the given upper bound, in this case 5. In other languages, it depends on the exact specification. More on that later.

When specifying a for-loop, the exam-style pseudocode also allows you to specify a step size for the loop; meaning that rather than incrementing by 1 after each repetition, you can specify by how much the variable should change. This looks as follows:

```basic
for i = 1 to 5 step 2
    print(i)
next i
```
In the first iteration, the variable `i` would have value 1, then increase by the specified step size, 2. The next value would therefore be 3, then 5. If, after a repetition, the variable would be increased to be strictly greater than the upper limit, the for-loop stops. Therefore, the output of the above code would be 
```
1
3
5
```
and if the for-loop were instead
```basic
for i=1 to 6 step 2
    print(i)
next i
```
you'd get the same output because after the teration on which `i==5`, the value would be increased to 7, which is beyond 6. 

### For-Loops in Real Programming Languages
Many programming languages feature for-loops inspired by the syntax that C used. In C, a for-loop is specified in the following way:
```C
for(int i = 1; i <= 5; i = i+1){
    // the loop body goes here
}
```
After the keyword `for` indicating that a for-loop is being constructed, there are three components to the for-loop. 
1) The counter variable is declared and initialised, in the above example this would be `int i = 1`. The counter variable does not need to be an integer (as it is above, marked by `int`) and it does not need to start at 1. This variable declaration and definition is executed before the for-loop begins. 
2) The condition that needs to hold for the loop to continue is specified, above this is `i <= 5` or "as long as `i<=5`, repeat the below code." You could specify any condition here.
3) The change in the counter variable after each repetition; here `i = i+1`. This is an assignment to the counter variable which occurs after every iteration: once the loop body has run, this change is made before the condition is checked. You could specify much smaller or much larger steps if you wanted.

In contrast, for example, the language Visual Basic (VBA) has for-loops much more closely aligned with the pseudocode. These look as follows:
```basic
for i=1 to 5
    print(i)
end for
```
In fact, the OCR pseudocode was very likely inspired by the syntax in VBA. 

In Python, for-loops look very different. The loop equivalent to the above for-loops would be the following code, which uses the `range` function. 
```python
for i in range(1, 6):
    print(i)
```
The `range` function is an odd little piece of code, and technically this fits more neatly into the next category of loop, but because Python does not have "pure" for-loops in the classical sense, using `range` is the closest approximation.

`range` generates a sequence of numbers which is determined by the up to three parameters the programmer gives to `range`:
* if the `range` command is given just one number $y$, it will generate the numbers between $0$ and $y-1$ (i.e. it generates $y$ numbers, starting at $0$.) If the number $y$ is negative, it generates no numbers at all.
* if the `range` command is given two numbers, $x$ and $y$, it will generate numbers starting at $x$ and increasing by $1$ after each iteration until $y-1$ would be exceeded by increasing it further. This means (if $x$ and $y$ are integers) that `range(x, y)` will generate $y-x$ numbers (unless y is smaller than $x$, in which case it will not generate any numbers). 
* if the `range` command is given three numbers $x$, $y$ and $z$, it will generate numbers starting at $x$ and increasing by $z$ after each iteration, until increasing it another time would make the number be equal to at least $y$. This last example is a bit more complicated to understand, so here are two examples:

```python
for v in range(0.5, 0.9, 0.1):
    print(v)
```
would output the values `0.5`, `0.6`, `0.7`, and `0.8`. If the `0.5` were replaced with `0.55`, the values that would be output are `0.55`, `0.65`, `0.75` and `0.85` because the next (hypothetical) number would be `0.95`. The reason this is implemented in this way is that then, the function `range(x, y, z)` always generates a total of 

$$\max\left(0, \left\lfloor\frac{y-x}{z}\right\rfloor\right)$$

numbers, which is a nice property to be able to determine the number of iterations the for-loop will have. If the upper bound were included, i.e. if the example `for i in range(0.5, 0.9, 0.1)` were to also generate `0.9`, the expression to calculate the number of elements generated would generally be very difficult to express. The above expression is also valid for the cases where `range` only gets two or even one parameter; if two numbers $x$ and $y$ are given, $z$ is simply set to $1$ by default and if one number is given, it is interpreted as $y$, $x$ is assumed to be $0$ and z is assumed to be $1$. 

## New: For-Each-Loops

For-Loops rely on the presence of a counter variable that changes by a certain amount after each iteration. However, we often have a collection of data that we wish to repeat code for every member of. For instance, when I complete the register at the beginning of each lesson, instead of thinking "Is student 1 present?", "Is student 2 present?" et cetera, I think about the students' names: "Is Izzy present?", "Is Isy present?", "Is Isobel present?", "Is Isabelle present?", "Is Isabella present?", et cetera. 

I have a mental collection of names (which includes very many variations of the same name) and I go through each one, without counting how many names I have already gone through. The same can be done in programming languages: when we have collections of objects in our programs, such as arrays or lists, we may wish to perform the same action on each member of succh a collection. It is then possible to use a for-loop with a counter and keep specifying "first, take the $n$th item out of my collection of things, then execute these instructions using it." But it is more convenient to specify "For each item in this collection, repeat the following instructions." That is the idea of a for-each loop.

Python uses this idea by default. For instance, if you have a list of Disney princesses, you can use the following code to call every one of them beautiful:
```python
princesses = ["Elsa", "Snow White", "Rapunzel", "Pocahontas"]
for princess in princesses:
    print(princess, "is beautiful!")
```
The output would be
```
Elsa is beautiful!
Snow White is beautiful!
Rapunzel is beautiful!
Pocahontas is beautiful!
```

Java has the same concept, which means that Java has both classical for-loops and for-each loops:
```java
String[] princesses = {"Elsa", "Snow White", "Rapunzel", "Pocahontas"};

for(String princess : princesses){
    System.out.print(princess); // prints the name of the princess without line break.
    System.out.println(" is beautiful");
}
```

## Basics: While-Loops
You will also have encountered `while`-loops already. `while`-loops are a kind of *indefinite* or *condition-controlled* iteration, which evaluate a condition after each iteration to determine whether the loop should continue repeating its body instructions. Rather than having a counter variable, the while loop is given a Boolean expression in addition to its body and the following process is how the loop runs:
1) check the condition. If it evaluates to `False`, jump to step 4, if it evaluates to `True`, jump to step 2
2) execute the body of the loop
3) jump to step 1
4) the loop is complete.

Essentially, "while" the condition is true, the loop continues. The exam-style pseudocode will write these structures like this:
```basic
password = "W0lders"
attempt = input("Please enter your password: ")
while attempt != password
    print("Incorrect.")
    attempt = input("Please try again: ")
end while
```

The equivalent code in Python would be written as 
```python
password = "W0lders"
attempt = input("Please enter your password: ")
while attempt != password:
    print("Incorrect.")
    attempt = input("Please try again: ")
```

And the equivalent Java would be written as 
```java
String password = "W0lders";
// taking input is not available by default in Java!
Scanner scan = new Scanner(System.in);
System.out.print("Please enter your password: ")
String attempt = scan.nextLine()
while (attempt != password) {
    System.out.println("Incorrect.")
    attempt = scan.nextLine("Please try again: ")
}
```

As you can see, the functionality of while-loops across langauges is much more homogeneous than for for-loops. That's nice, isn't it?

## New: Do-Until-Loops
A second kind of indefinite iteration is a closely related kind of loop, the *do-until-loop*. Instead of the process outlined above, the steps a do-until-loop goes through are the following:
1) Execute the loop body.
2) Evaluate the condition. If it is false, jump to step 1. If it is true, jump to step 3.
3) The loop is complete.

It is quite uncommon in real programming languages, VBA has them and another example of a language that has them is Ruby. The exam-style pseudocode looks like this:
```basic
do:
    print("Hello!") 
until 1 > 0
```
The big differences to a while-loop are as follows:
* The condition is checked after the loop body is executed.
  * This means that the loop body will be run at least once, no matter what the condition.
* The condition checks whether the loop should *stop*, not whether it should continue.

Thus, in the above pseudocode, even though the condition `1 > 0` clearly tells the loop to stop running as soon as possible, the string `Hello!` is printed anyway. 

Ruby's do-until loops look like this:
```ruby
begin
    puts "Hello!";
end until 1>0
```

Some languages also provide do-while loops and until-do loops. Try to figure out how these work yourself!

Hello Fleur and Hannah, this is a callback to that first lesson!