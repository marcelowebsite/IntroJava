One of the most important things we do as programmers is manage complexity; functions allow us to encapsulate complex calculations into a black box, and call it when needed.

For example, imagine that we need to find whether numbers are even; we can easily do the calculation, using % ; however, it will be much nicer if we encapsulate this into itw own function. We could write the function as follows:

```java
boolean isEven(int number)
{
    return (number%2) == 0;    
}
```

When defining a function, we write its return type, then the name and the parameters, and then the code, within braces (well, actually many times we will precede the function name with *public static*, which will be explained later). Within the function we can include as many statements as we want (for now, we will do simple functions, with just one line). 
 
In the function above, the return type is boolean, so the function will return either true or false; it takes one parameter, an int, which will be referred as *number* from within the function. The function just returns one expression, which is whether the remainder of the number divided by two is zero (which is the definition of even :).

We can call the function inside an expression as follows:
```java
boolean is7Even=isEven(7); // what would be the value ?
boolean is*Even=isEven(8);
```

When we call a function, with an expression like `isEven(7)`, the function gets executed; first the actual parameter (7 in this case) gets evaluated, then the code for the function gets executed, with the formal parameter (number) replaced with the actual value (you can imagine the formal parameter, number, is like a variable inside the function; finally, the return value gets substituted instead of the function call. 

## Local variables and scope

Within a function, we can define variables if we need them; this variables are only visible within the function (and only keep their value within that function call), so we could also define isEven as follows:
```java
boolean isEven(int number)
{
    int remainderBy2=number%2;
    return remainderBy2==0;   
} 
```

The local variable, `remainderBy2`, can only be accessed within the function, and every call to the function gets its own copy of the variable; each function call gets its own independent context (or *activation frame*) in which it is executed.

## Function composition
We can define functions that take as many parameters as we need (although they can only return one value), and you can include and combine the function calls in any ways you want; for example (although it would be overkill in real life), let us define the following function:

```java
int add(int number1, int number2)
{
    int sum=number1+number2;
    return sum;   
}
```

This function adds two numbers (WOW !!! :). It allows us to show how we can combine function calls as in the following code:

```java
int n=add(3,7); // what's the answer
int n2=add(n, 3); 
```

OK, everything seems normal here; lets look at the next one:

```java
int n3=add( add(2,3), add(5,7));
```
Here, first we evaluate the arguments, in left-to-right order, so the compiler will first evaluate `add(2,3)`, in its own activation frame, number1=2, number2=3, sum=5 and returns 5; then evaluates `add(5,7)` in its own activation frame, returning 12, and finally evaluates the outer expression, which is equivalent to add(5,12), yielding 12.
 
## Exercises (assume we have the functions above)

1. What would be the value of `ans` at the end of the following code fragment:
    ```java
    int a=10;
    int b=add(a,a);
    int ans=add(5, add(a,b));
    ```
    
2. What would be the value of `ans` at the end of the following code fragment:
    ```java
    int x=add(10,5);
    boolean ans=isEven(add(x,1));
    ```