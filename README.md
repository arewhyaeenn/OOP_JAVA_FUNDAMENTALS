# Object-Oriented Programming - Java Fundamentals

In this lab, you will learn:

* The structure of a basic program in Java.
* What expressions, statements and blocks are.
* What a comment is, and how to comment in Java.
* How to name variables, constants, classes, ...
* How to store and manipulate data in a variable.
* What "declaration" and "assignment" are, how to declare and assign value to variables and constants in Java.
* How to create and store data in a constant.
* The difference between variables and constants.
* How to access a variable's value.
* The eight primitive data types in Java, and what data they store.
* What a `String` is, and how to create one in Java.
* What literal values are, and how to format primitive literals and `String` literals.
* How to perform basic arithmetic operations in Java.
* What "operator precedence" means and how to determine the order in which operations will occur in Java.
* What typecasting is, and how to convert between the primitive number types in Java.
* How to use shortcut operators to make common calculations more concise.
* How to access members of the `Math` class.
* Where to find the Java 8 API, and documentation for classes in Java 8.

There are exercises throughout the reading below. The answers are included at end of the lab, and are linked to the questions. Try to complete each exercise before reading their answer! You are encouraged to discuss them (and anything else in this lab) with your neighbors.

After the answers to exercises, you can find the lab assignment itself. This is what must be submitted. 

## Java Program Structure

Any Java program consists of at least one **class**. The programs we will discuss and create today will each be comprised of exactly one class. We'll spend more time covering exactly what a class is and how classes interact in future labs.

Each class has a name, also known as an **identifier**; we'll go over what qualities identifiers must have to be valid later in this lab.

Each class also has a **body**, denoted with a set of curly braces `{}`. Everything inside the curly braces is part of the class, and is said to be in the **scope** of the class.

Below is a class whose identifier is `MyClass` and whose body is empty.

```java
class MyClass
{
	
}
```

Every Java program has exactly one **main method**. If a program has multiple classes, there might be more than one main method in the classes, but the program will only run one of the main methods (the one from the class on which `java` was run).

Any main method consists of the header `public static void main(String[] args)`, followed by curly braces `{}`. The contents of the curly braces are the **body** of the main method. `main` is an identifier reserved for the main method. `public`, `static`, and `void` are all keywords in Java, and we will discuss their individual uses and meanings in future labs. We will also discuss the meaning of `String[] args` in a future lab.

When a program is run, execution starts inside the body of the main method.

Below is the simplest possible program in Java. It defines a class called `MyClass` whose contents consist exclusively of a main method with an empty body.

<a name="q1"></a>**[EXERCISE 1](#a1)** : What does the program below do when run?

```java
class MyClass
{
	public static void main(String[] args)
	{
	
	}
}
```

## Comments

**Comments** are plain text that is ignored by the compiler, so it does not affect how the program runs. You'll generally want to add comments to your code to explain how it functions, what its purpose is, etc.

Comments in Java come in two varieties: single-line comments and multi-line comments. Single line comments start with `//` and span a single line. Anything that appears after a `//` on a line is **commented out**, so it will be ignored by the compiler.

Multi-line comments can span multiple lines; they begin with `/*` and end with `*/`.

Usually, when you make a new class, you should include comments at the start of the file explaining what the class is for or what it does.

The two snippets below are identical in functionality; in the first, the program description is in several single-line comments and in the second it is in one multi-line comment.

```java
// The class MyClass below
// does absolutely nothing.

class MyClass
{
	public static void main(String[] args)
	{
	
	}
}
```

```java
/*
	The class MyClass below
	does absolutely nothing.
*/

class MyClass
{
	public static void main(String[] args)
	{
	
	}
}
```

You'll sometimes want to include comments alongside small parts of your program indicating what those parts do. This is usually unnecessary; ideally your code itself is well-written enough to be readable, so commenting the purpose of individual lines is unnecessary.

```java
class MyClass
{
	public static void main(String[] args)
	{
		// declare an int variable called myInteger
		int myInteger;
		
		// assign the value 1 to myInteger
		myInteger = 1;
	}
}
```

<a name="q2"></a>**[EXERCISE 2](#a2)**: Two programs are identical, except that one contains comments and the other program doesn't. Both programs are compiled. Is there any difference between the compiled versions of the programs?

<a name="q3"></a>**[EXERCISE 3](#a3)**: Do comments affect the performance (e.g. speed) of a program?

## Identifiers

### Properties

An **identifier** is essentially a name for a variable, constant, method, class... basically anything that you create will need a name by which you can refer to it.

In Java, an identifier must have the following properties:

* Starts with a **Java letter**:
	* `A-Z`
	* `a-z`
	* `_`
	* `$`
* Can contain any number of Java letters and digits `0-9`
* Cannot contain spaces
* Cannot be keywords (words reserved by Java, like `int` and `class`)

Java identifiers are **case sensitive**. `number1` and `Number1` are different identifiers!

<a name="q4"></a>**[EXERCISE 4](#a4)**: Determine whether each of the following is a single valid identifiers in Java; if not, determine why not.

1. `asdf`
2. `ASDF`
3. `aSDf`
4. `as df`
5. `$asdf`
6. `myvariable`
7. `for`
8. `var1`
9. `1var`

### Conventions

It is generally wise to choose an identifier that describes the thing being named; your identifiers should try to describe the purpose of the object being named, or describe the data that will be stored in it. Nondescriptive variable names are generally frowned upon, as they make code harder to read and therefore harder to edit and improve. Choosing good identifiers can reduce the need for comments explaining code by making the code itself readable enough to not require as much commenting!

It is helpful to categorize identifiers and systematically name members of different categories, so an identifier is enough to determine what type of data is referred to.

There are many conventions for formatting identifiers. One common convention is:

* Class identifiers are in `PascalCase`, meaning each word in the identfier starts with a capital and the rest is lowercase. The class called `MyClass` in the example above is named using `PascalCase`
* Variables are named in `camelCase`, which is the same as `PascalCase` but the first word starts with a lower case. The variable `myInteger` in the example above is named using `camelCase`.
* Constants are named in `UPPER_SNAKE_CASE`; every word in the identifier is caps locked, with underscores separating the words.

The naming conventions you use will vary from project to project. In industry, most teams have an agreed upon coding style used by everyone on the team in order to facilitate collaboration. It is not important what system you choose for identifier selection, **as long as you are systematic and consistent**. That is, it doesn't matter which system you choose as long as you choose and stick to a system.

The setup above leaves `lower_snake_case` available, so if another type of identifier is added into the mix, it can be written in this style.

## Expressions, Statements and Blocks

An **expression** is a combination of one or more constants, variables, operators, and functions that are interpreted to **produce a value**. As a rule of thumb, something is an expression if it results in an **output** or **value**. For instance, `5 + 4` is an expression, whose output is `9`. Simpler yet, `5` is an expression whose value is `5`.

A **statement** is a combination of elements (constants, variables, ...) that are interpreted to **carry out an encoded action or sequences of actions**. For example, the statement `int x = 5;` performs two actions: it declares an `int` variable `x` and then **assigns** the value `5` to `x`. This is a specific type of statement, called an **assignment statement**, which we'll discuss in the next section. In Java, statements end with a semicolon `;`.

A **block** is a sequence of statements in curly braces `{}`. In Java, anywhere that you can put a statement, you can also put a block.

## Declaration and Assignment

### Variables

Variables are created and named with **declarations**. A variable declaration specifies:

* What type of data the variable will refer to.
* The identifier for the variable.

```java
int myNumber;
```

The declaration above declares a variable called `myNumber` of type `int`. This means `myNumber` can hold an integer value within the bounds of the `int` type.

Notice that no value is given to `myNumber` in the statement above. The variable is declared and ready to store an integer value, but no value has been **assigned** to it. The first assignment to a variable is said to **initialize** the variable. Variables that have not been initialized (also known as **uninitialized variables**) cannot be **accessed** (i.e. their values cannot be used). Code which attempts to access a variable that has been declared but not initialized will not compile. For example:

```java
class MyClass
{
    public static void main(String[] args)
    {   
        int x;
        System.out.println("x's value is : " + x);
    }
}
```

The code above will not compile. This is because `x` is declared with the statement `int x;`, but is never initialized. The next line `System.out.println("x's value is : ", + x);` would attempt to access `x` to print its value.

A declared variable can be made to hold a specfied value with an **assignment**; this is done with `=`, the **assignment operator**. A statement which uses the assignment operator to assign a value to a variable is called an **assignment statement**. Assignment statements are written out in the form `<identifier> = <expression> ;`; the value of the expression on the right is stored in the variable with the identifier on the left.

```java
// declare myNumber
int myNumber;

// assign value 1 to myNumber;
myNumber = 1;
```

Compilation will fail if the variable **might** not have been initialized. For instance, the program below gets an input from the user (typed in the console). If that input is `0`, it assigns value `1` to `x`; otherwise it does not perform this assignment, so `x` is left uninitialized. Because `x` might be left uninitialized, the code will not even compile. Don't worry about the lines below that don't make sense; we haven't covered the `Scanner` yet, or `if` statements. The `if` statement might make intuitive sense to you, and it might not; either way, we'll cover it later.

```java
import java.util.Scanner;

class MyClass
{
    public static void main(String[] args)
    {
        Scanner scan = new Scanner(System.in);

        int x;

        System.out.print("Enter an integer : ");
        int userInput = scan.nextInt();
        
        if (userInput == 0)
        {
            x = 1;
        }
        System.out.println("hello " + x);
    }
}
```

Variables can be **reassigned** whenever desired; that is, their values can be changed to a new value at any time. Variables can **never** be **redeclared**. Once a variable has been declared, it cannot be declared again.

A variable can be declared and assigned on the same line:

```java
// declare myVariable, assign its value to 1
int myVariable = 1;
```

This sort of combined declaration and assignment will not work if the variable has already been declared, because variables cannot be redeclared. For instance, the following snippet would not compile:

```java
int myVariable = 1;
int myVariable = 2;
```

But this would:

```java
int myVariable = 1;
myVariable = 2;
```

<a name="q5"></a>**[EXERCISE 5](#a5)**: Read the program below, and see if  you can determine what it does. What is printed? Try running it and see if you were correct.

```java
class MyClass
{
	public static void main(String[] args)
	{
		// declare myNumber
		int myNumber;
		
		// assign value 1 to myNumber and print it
		myNumber = 1;
		System.out.println("My number is : " + myNumber);
		
		// reassign myNumber's value to 2, and print it
		myNumber = 2;
		System.out.println("My number is : " + myNumber);
	}
}	
```

### Constants

A **constant** is similar to a variable, but it has one key difference: a constant's value can only be assigned once, and after this assignment its value cannot change.

Declaring a constant is similar to declaring a variable, but the constant declaration has an extra keyword, `final`, which denotes that any value assigned to the constant is final (i.e. it cannot be changed).

```java
// declare a constant int
final int MY_CONSTANT;

// set its value permanently
MY_CONSTANT = 1;
```

Note another difference: the identifier `MY_CONSTANT` has been spelled using a different capitalization scheme than the `myVariable`. This is a **choice**; the capitalization scheme used for identifiers does not affect what the referenced variables, constants, classes etc can do. To reiterate from the previous section, identifiers should be formatted systematically based on what they reference.

<a name="q6"></a>**[EXERCISE 6](#a6)**: If you try to compile the following program, what happens?

```java
class MyClass
{
	public static void main(String[] args)
	{
		final int MY_CONSTANT = 1;
		
		MY_CONSTANT = 2;
	}
}
```

## Accessing Primitive Data

When data has been stored in a variable or constant, it generally has been saved with the intention to **access** the data later. Otherwise, why store it to begin with?

Whenever the identifier of a variable or constant is used (except on the left side of an assignment statement) it is used as a reference to the value stored in the variable.

In the snippet below, `x` is initially assigned the value `2` and then `y` is assigned the **value** of `x`. This does not mean that `x` and `y` are the same variable; `y` has been given a **copy** of `x`'s value. The use of `x` anywhere other than as the left side of an assignment statement (`x = ...`) accesses `x`'s stored data (i.e. `x`'s value).

```java
class MyClass
{
	public static void main(String[] args)
	{
		int x = 2;
		int y = x;
	}
}
```

<a name="q7"></a>**[EXERCISE 7](#a7)**: In the snippet below, what is printed out as the value of `y` at the bottom? Since `y` was declared and initialized with `int y = x;`, does changing `x`'s value also change `y`'s value?

```java
class MyClass
{
	public static void main(String[] args)
	{
		int x = 2;
		int y = x;
		
		x = 3;
		
		System.out.println("x's value is : " + x);
		System.out.println("y's value is : " + y);
	}
}
```

## Java's Primitive Data Types

Java has eight built-in, basic data types called **primitives**. These are not the only data types in Java - new data types can be defined at will (we will make our own data types later in the semester through class definitions). But any data that is not primitive data is comprised of primitive data; all data types are constructed out of the primitive data types. Primitives are to data types as primes are to natural numbers.

Four of Java's eight primitive data types are for storing integer numbers:

* `byte` :
	* integer data, stored in 8 bits (1 byte)
	* minimum value: `-128`
	* maximum value: `127`
* `short` :
	* integer data, stored in 16 bits (2 bytes)
	* minimum value: `-32768`
	* maximum value: `32767`
* `int` :
	* integer data, stored in 32 bits (4 bytes)
	* minimum value: `-2147483648`
	* maximum value: `2147483647`
* `long` :
	* integer data, stored in 64 bits (8 bytes)
	* minimum value : `-9223372036854775808`
	* maximum value : `9223372036854775807`

Two of the remaining four primitive data types are numerical. They are not for storing integer data, but for storing **floating point** data, i.e. (positive or negative) numbers with non-whole parts. These two data types are:

* `float` :
	* floating point data, stored in 32 bits (4 bytes)
	* minimum positive value: `1.4E-45`
	* maximum positive value: `3.4028235E38`
* `double` :
	* floating point data, stored in 64 bits (8 bytes)
	* minimum positive value: `4.9E-324`
	* maximum positive value: `1.7976931348622157E308`

Note the `E`s in the numerical values above; the values are in scientific notation.

There are two remaining primitive data types:

* `char` :
	* character data, stored in 16 bits (2 bytes)
	* stores a single character
	* can store any unsigned 16-bit character in Unicode, a convention for character storage. You can learn more [here](https://docs.oracle.com/javase/6/docs/api/java/lang/Character.html) if desired.
* `boolean` :
	* boolean data is stored in a single bit (1/8 of a byte)
	* stores either `true` or `false` (i.e. 1 or 0, a bit); these are the only possible values

<a name="q8"></a>**[EXERCISE 8](#a8)**: Imagine you want to store integer data in a variable. Imagine further that based on the context, you know that:

* The value of the integer will never be negative.
* The value of the integer will always be at most `40000`.

What primitive data type should you use to store the data?

## The `String` Data Type

A `String` is a sequence of characters. For instance, `"abc 123"` could be a `String` composed of the sequence of characters `'a'`, `'b'`, `'c'`, `' '`, `'1'`, `'2'`, `'3'`.

`String`s are not a primitive data type in Java; they are instead objects. In fact, all data types in Java other than the eight primitives discussed earlier are objects. We will discuss the differences between objects and primitives in the next lab.

## Literal Values

Literal values are expressions which directly represent values for different data types without any evaluation necessary. For instance, `1` is an `int` literal, but `1+2` is not, though `1+2` **is** an integer expression.

### Integer Literals

`int`, `short` and `byte` literals are formatted as follows: an optional `+` or `-` sign followed by a collection of digits. This should be somewhat intuitive; literal values for these three data types, meant to store integer values, are characters which represent integer values.

Consider for example the three statements below:

```java
byte a = 11;
short b = -123;
int c = +61427;
```

Each statement does two things:

* Declares a variable (of type `byte`, `short` or `int`).
* Assigns value to the variable, using a literal value. The literals used above are `11`, `-123`, and `+61427`.

`long` literals are similar to `byte`, `short` and `int` literals but they have an extra piece: a trailing `L` (uppercase or lowercase). So, while `12` is a `byte`, `short` or `int` literal, `12l` and `12L` are `long` literals.

```java
long d = 25l;
```

In general, these integer literals are encoded in base `10`. But different encodings can be used if desired.

Integer literals (`byte`, `short`, `int` and `long` literals, that is) that start with `0` are treated as **octal** integers, meaning the value of the literal is read in base `8`.

Integer literals that start with `0x` are **hexadecimal** literals, encoded in base `16` (using the digits `0-9` and then the letters `a-f`).

You can read up on octal values [here](https://en.wikipedia.org/wiki/Octal) and hexedecimal values [here](https://simple.wikipedia.org/wiki/Hexadecimal) if desired.

### Floating Point Literals

Floating point literals are like integer literals, but they include a decimal point. They are formatted as follows:

`float` : an optional `+` or `-` sign, followed by a decimal number with a trailing `f`

`double`: an optional `+` or `-` sign, followed by a decimal number

Literals for both floating point types can be given in either fixed or scientific notation. The `double` literal `122.3` (in fixed notation) is identical to a scientific notation equvialent `1.223e2` (which means `1.223` times `10` raised to the power `2`).

<a name="q9"></a>**[EXERCISE 9](#a9)** : What are the `float` literal equivalents of the `double` literals `122.3` and `1.223e2`?

The following declarations and assignments would all be valid:

```java
double a = 122.3;
double b = 1.223e2;
float c = 122.3f;
float d = 1.223e2f;
```

### Boolean Literals

Literal values for `boolean` primitives are very simple. `boolean` data is either `true` or `false`. These are the only possible literal values for `boolean`s.

```java
boolean firstBool = true;
boolean secondBool = false;
```

### Character Literals

`char` data is represented with an individual character in single quotes. For example, the character `a` would be represented with literal `'a'`.

Here are a few sample declarations and assignments for `char` variables:

```java
char theFirstLetter = 'a';
char theNextLetter = 'b';
```

### String Literals

`String` literal data is represented as a sequence of 0 or more characters in double quotes. If you wanted to store the word "pancake" in a `String` variable, you would do it using the literal `"pancake"`.

A string with 0 characters, called an **empty string**.

For example, the following statement declares a variable named `pancakeString` of type `String` and stores in it the sequence of characters `"pancake"`.

```java
String pancakeString = "pancake";
```

## Arithmetic Operators

The five basic arithmetic operations in Java are `+`, `-`, `*`, `/`, and `%`. They are used for addition, subtraction, multiplication, division and remainder respectively. If `x` and `y` are both primitive numerical variables or constants of the same type (the numerical primitives are `byte`, `short`, `int`, `long`, `float`, and `double`) then:

* `x + y` is the sum of `x` plus `y`
* `x - y` is the difference, `x` minus `y`
* `x * y` is the product of `x` times `y`
* `x / y` is the quotient of `x` divided by `y`
* `x % y` is the remainder of `x` divided by `y`

The order in which arithmetic operations are executed can be determined the same way it is in mathematics, using **PEMDAS** (if you're not sure what **PEMDAS** is, use those search engine skills). You may have noticed that there isn't an operator for exponentiation; it is done with a **method** from the `Math` class, which we will discuss later. The remainder `%` operator has the same precedence as multiplication `*` and division `/`. If multiple arithmetic operators have the same precedence, they are performed from left to right.

<a name="q10"></a>**[EXERCISE 10](#a10)**: Assume `x` and `y` are `int` variables with respective values `5` and `3`. What are the results of the following expressions:

* `x + y * 5`
* `x + (y * 5)`
* `(x + y) * 5`
* `y % x`
* `y % x * y`
* `y % (x * y)`

## "Shortcut" Operators

For each of the arithmetic operators `+`, `-`, `*`, `/`, and `%` there is a shortcut assignment operator `+=`, `-=`, `*=`, `/=`, `%=`. These shortcut operators work as follows:

* `x = x + 5;` is the same as `x += 5;`
* `x = x - 5;` is the same as `x -= 5;`
* `x = x * 5;` is the same as `x *= 5;`
* `x = x / 5;` is the same as `x /= 5;`
* `x = x % 5;` is the same as `x %= 5;`

In the first example above, `x = x + 5;` takes the value of `x` before the operation, adds `5` to this value, and then assigns this new value to `x`. The shortcut `x += 5;` does exactly the same thing. In both cases, `x` gets `5` larger than it was prior. The other shortcut operators are the same, relative to the arithmetic operation they are providing a shorthand for.

There are also shortcuts for **incrementation** and **decrementation**, i.e. increasing or decreasing a numerical value by 1. That is, there is a shorter way to write `x = x + 1;` and `x = x - 1;`.

We could shorten `x = x + 1;` to `x += 1;` as described above, but it can be written even more concisely as `x++;` or `++x;`. Similarly, we could shorten `x = x - 1;` to `x -= 1;`, but it can be written more concisely as `x--;` or `--x;`.

## Types, Assignment, Conversion and Casting

Sometimes it is necessary to convert data (particularly numerical primitive data) from one type to another. For instance, you might want to store `byte` data in `int` form. Some conversions can be carried out **implicitly**; if you store `byte` data in an `int` variable, the data is converted to `int` form without the need for anything extra on your part. For example, the following statements are perfectly valid:

```java
byte x = 5;
int y = x;
```

Above, a `byte` variable called `x` is given the value `5`, and then that same value is stored in `int` form in the variable `y`.

Not all conversions are this easy. An `int` can store `byte` data easily, because an `int` formats its data in the same way a `byte` does but an `int` is larger. Performing the converse conversion is not as easy. The statements below will not work:

```java
int x = 5;
byte y = x;
```

The statements above do not compile because, to put it loosely, an `int` does not fit in a `byte` box. The closest we can get to performing the statements above is with a **type cast**, an explict conversion from one type to another. This is performed by putting the desired type, in parenthesis, before the value being converted:

```java
int x = 5;
byte y = (byte) x;
```

The above takes the `int` value `5` stored in `x` and converts it to the equivalent `byte` value. Since `5` is within the bounds for a `byte`, the conversion happens without error. But `byte` data must be in the close interval `[-128, 127]`.

<a name="q11"></a>**[EXERCISE 11](#a11)**: Try to predict what value will be printed for `y` in the program below. Then, run the program and verify your prediction.

```java
class MyClass
{
	public static void main(String[] args)
	{
		int x = 128;
		byte y = (byte) x;
		
		System.out.println("y has value : " + y);
	}
}
```

The table below lists each primitive data type (in the left column) and the types of values that can be accepted (i.e. implicitly converted) for storage in that data type. As a rule of thumb, the "more complex" data types can store the "less complex" ones without any need for explicit conversion, while the converse is not true. In other words, upgrading data types does not require type casting, but downgrading them does.

**TYPE**  | **ACCEPTED TYPES**
:-------: | :----------------:
`byte`    | `byte`
`short`   | `short`, `byte`
`int`     | `int`, `short`, `byte`, `char`
`long`    | `long`, `int`, `short`, `byte`, `char`
`float`   | `float`, `long`, `int`, `short`, `byte`, `char`
`double`  | `double`, `float`, `long`, `int`, `short`, `byte`, `char`
`boolean` | `boolean`
`char`    | `char`

As the table above denotes, storing `byte` data in a `short` variable would not require type casting, but storing `short` data in a `byte` variable would require casting. One oddity of the implicit conversions above is that an `int` can store `char` data implicitly. This is because `char` data is actually stored in integer form (see [Unicode](https://en.wikipedia.org/wiki/Unicode)).

In Unicode, the digits and the english alphabet are all congiguous (i.e. in a row) integers. The digits `0` through `9` are the integers `48` through `57`. The capital letters `A` through `Z` are the integers `65` through `90`, and the lowercase letters `a` through `z` are the integers `97` through `122`.

## The `+` Operator, Strings, and Polymorphism

**Polymorphism** is a key concept in Object Oriented Programming. We will be discussing polymorphism much more in future labs. But, let's discuss it briefly now with the `+` operator as an example.

When broken into its greek roots, "poly" and "morph", "polymorphism" essentially means "many forms". In programming, an entity is said to be polymorphic if it can take more than one form, or have more than one meaning depending on context.

The `+` operator is polymorphic. It behaves differently depending on the types of its operands. We already know how it behaves with primitive numerical inputs; this is already polymorphism, as it returns outputs in different data types depending on the types of its operands. 

The polymorphic behavior of the `+` operator is more easily seen in how it behaves with `String` operands. Any data with a defined way to be converted to `String` form can be added to a `String`, and this will result in **concatenation**. That is, if one of the inputs for the `+` operator is a `String`, it performs a **different operation** that it would if they were all numerical primitives. For instance, `50 + "elephants"` results in the `String` value `"50elephants"`.

<a name="q12"></a>**[EXERCISE 12](#a12)**: Consider the following statements. Give that addition is evaluated from left to right, predict what should be printed by each one. Then, create a program to test your predictions.

```java
System.out.println( 5 + " elephants" );
System.out.println( 5 + 6 + " elephants" );
System.out.println( 5 + (6 + " elephants") );
```

## Arithmetic Operations (Again)

The arithmetic operations are **all** polymorphic in how they perform calculations with numerical primitives; it's just less obvious than it is with `String` data because it's easy to think of all numbers as just numbers, and not pay attention to how the number is encoded in binary.

We will not dwell on the binary representations of the numerical data types here; you will cover that in future classes and/or do some independent research on the subject. But it is important to note that the numerical primitives store their contained data in different formats. Specifically, the floating point types `float` and `double` use one format, while the integer types `byte`, `short`, `int` and `long` use a different format.

When an operation is performed with two primitive numbers, the operation depends on the types of the two numbers. For instance, addition with two `int`s is a different operation than addition with two `float`s, because the data is stored in a different format and must therefore be interpreted differently and used differently in calculations.

In the snippet below, the first multiplication is **floating point multiplication**, while the second is **integer multiplication**. While numerically these operations appear identical, the bitwise calculations being performed under the hood are very different.

```java
class MyClass
{
	public static void main(String[] args)
	{
		float x = 2.5f;
		float y = 3.3f;
		float z = x * y;
		
		int a = 2;
		int b = 3;
		int c = a * b;
	}
}
```

The built-in operations in Java result in data whose type depends on the types of the inputs. In the snippet above, `a * b` is an `int` because `a` and `b` are both `int`s. Similarly, `x * y` is a `float` because `x` and `y` are both `float`s.

But what happens when you mix data types in an operation? What if, in the snippet above, the operation `x * a` was done to mulitiply a `float` with an `int`? Integer multiplication cannot be done with floating point data, nor can floating point multiplication be done with integer data. But, if you were to use the expression `x * a`, you would get neither a syntax error nor a runtime error.

When the built-in arithmetic operations are used with integer and floating point operands, the integer operands are implicitly converted to floating point form. This might make sense intuitively; any integer can also be represented as a floating point number, but the converse is not true. For example, `1` could be represented as `1.0f`, but `2.5f` cannot be written in integer form because it is not an integer.

So, if you perform an operation with an integer operand and a floating point operand, the result is a floating point number. What if you want to store that number as an integer? You can do so, but with a cost: loss of precision.

In the snippet below, a `float` with value `2.6f` is multiplied by an `int` with value `3`. The result is a `float` with value `7.8f`. This result is then cast as an `int`. Notice that `7.8` is not an integer. So what happens? The answer is: the `.8` is truncated; the result is rounded down to the integer value `7`.

```java
float x = 2.6f;
int y = 3;

int z = (int) (x * y);
```

## Integer Division, Floating Point Division and Loss of Precision

Most of the arithmetic operations result in an output that is approximately the same with different operand types. For instance, the output of `2.0f * 3.0f` is numerically approximately equal to `2 * 3` (though the results are encoded differently).

This is not true for the division operation! Integer division (i.e. division performed with `byte`, `short`, `int`, and `long` data) results in an integer output (rounded down). For instance, `5 / 2` results in `2`, not `2.5`. If you wish to divide `5` by `2` using floating point division, you must make at least one of the operands a floating point type. For instance, `5.0 / 2` would perform floating point division, because the numerator `5.0` is a `double` literal. With variables, performing floating point division on integer data looks like this:

```java
int x = 5;
int y = 2;

// integer division
int z1 = x / y;

// float cast, then floatinf point division
float z2 = (float) x / y;

// integer division, then float cast
float z3 = (float) (x / y);

System.out.println("z1 is " + z1);
System.out.println("z2 is " + z2);
System.out.println("z3 is " + z3);
```

Note that in the calculation of `z2` above, the typecast of to `(float)` type happens **before** division occurs above; first, `x`'s value is converted to `float` form, and then it is divided by `y`.

<a name="q13"></a>**[EXERCISE 13](#a13)**: In the snippet above, what values do `z1`, `z2` and `z3` have when printed? Run the snippet in a Java program to verify your answer.

## Arithmetics and Floating Point Data

Generally, operations carried out with floating point data have a margin of error; that is, when arithmetic operations are performed with floating point data, the result is often inaccurate by a very small amount. Try running the following program to see for yourself:

```java
class MyClass
{
    public static void main(String[] args)
    {
        System.out.println(8 % 3.2);
    }
}
```

The printed value should, in theory, be `1.6`, because `8` is as large as `2` whole `3.2`s, plus a remainder of `1.6`. What is the actual result?

## Operator Precedence

There are **many** operators in Java in addition to the arithmetic ones (and some arithmetic ones that we haven't discussed yet). The order in which operators' operations are carried out is determined using Java's operator precedence, which is shown in the table below. The operators at the top of the table are carried out first, and those at the bottom, last. It is not necessary for you to understand what most of the operators below are, for now.

![Operator Precedence](./figures/operatorPrecedence.png)

## The `Math` Class and Documentation

There are many functions and constants useful in mathematics in general which are accessible through the `Math` class. For instance, there is not an operator for exponentiation in Java, but the `Math` class has a function for it.

You can see documentation for the `Math` class and all of its contained utilities on [its page in the Java 8 API](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html). (You could easily find this page by searching "java 8 math").

In the documentation linked above, you can find every constant and method in the `Math` class, and descriptions of what those constants and methods do. Documentation like this is available for all built-in packages in the [Java 8 API](https://docs.oracle.com/javase/8/docs/api/).

As a programmer, one of your most valuable skills is finding, reading and interpreting documentation (and StackOverflow posts) in order to learn how to use tools and how to debug programs using those tools.

Members of a class can be accessed with the **access operator** (a dot following the class name). Member accesses are made in the form `<ClassIdentifier>.<memberIdentifier>`. For instance, the `PI` constant is a member of the `Math` class, so its value can be accessed with `Math.PI`. Similarly, the `pow` function is a member of the `Math` class, so it can be accessed with `Math.pow`. `Math.pow` is a function which takes two inputs and raises the first to the power of the second. For instance, `Math.pow(2, 3)` returns the result of raising `2` to the power `3`. We will discuss functions calls in a future lab, but for now note that when a function takes inputs, those inputs are given in a comma-separated list, in parenthesis, after the function itself.

<a name="q14"></a>**[EXERCISE 14](#a14)**: The program below does not compile. Use the `Math` class documentation to figure out why, and fix the problem.

```java
class MyClass
{
    public static void main(String[] args)
    {
        int x = 4;
        int y = 3;

        int z = Math.pow(x, y);

        System.out.println(x + " raised to the power " + y + " is " + z);
    }
}
```

## Answers to Selected Exercises

### <a name="a1"></a>**[EXERCISE 1](#q1)** 

The short answer is "Nothing", in that nothing appears to happen from the user perspective when running the program. The longer answer is that, as stated above, a class called `MyClass` is defined, so a small amount of memory is set aside and the class definition is written in that memory, but these all happen under the hood in Java. As far as output is concerned, this program does nothing.

### <a name="a2"></a>**[EXERCISE 2](#q2)**

No, there is no difference between the two compiled programs; comments are ignored by the compiler. There are even tools called reverse compilers which take compiled code and convert back to Java; if you take a Java program with comments, compile it and then reverse-compile the result, you'll get your original program without the comments.

### <a name="a3"></a>**[EXERCISE 3](#q3)**

Because comments are ignored by the compiler, they **do not** affect the performance of the program. They can make the program take (infinitesimally) more time to compile, but in general run time matters and compile time does not matter because a program only needs to be compiled once and then the compiled program can be used as many times as desired.

### <a name="a4"></a>**[EXERCISE 4](#q4)**

1. Yes, `asdf` is a valid identifier.
2. Yes, `ASDF` is a valid identifier.
3. Yes, `aSDf` is a valid identifier.
4. No, `as df` is not a valid identifier, identifiers cannot contain spaces.
5. Yes, `$asdf` is a valid identifier, `$` is a Java letter.
6. Yes, `myvariable` is a valid identifier, but something more readable like `myVariable` or `MY_VARIABLE` would be better.
7. No, `for` is not a valid identifier because `for` is a keyword in Java (but we haven't talked about this particular keyword yet, so that wasn't a very fair question).
8. Yes, `var1` is a valid identifier, identifiers can contain digits.
9. No, `1var` is not a valid identifier; while identifiers can contain digits, they must start with a Java letter.

### <a name="a5"></a>**[EXERCISE 5](#q5)**

The program does precisely what the comments state it does: it declares an `int` variable called `myNumber`, assigns `myNumber`'s value to `1`, prints that value `1`, reassigns `myNumber`'s value to `2`, and then prints this new value `2`.

### <a name="a6"></a>**[EXERCISE 6](#q6)**

The program does not compile. The value of constant data (data declared with the `final` keyword) cannot be changed.

### <a name="a7"></a>**[EXERCISE 7](#q7)**

`y`'s value is still `2` at the end. When `y` is initialized with `int y = x;`, it is given the same value as `x` (`2`). When `x`'s value then changes to `3`, `y`'s does not change with it because `y` contained a copy of `x`'s data at the time of assignment, not a reference to `x` itself.

### <a name="a8"></a>**[EXERCISE 8](#q8)**

The variable should be stored using an `int`. A `byte` is not large enough (`byte` has a maximum value of `127`). A `short`'s maximum value is `32767`, which is not quite large enough for the maximum stored value of `40000`. An `int` is large enough, with a maximum value far beyond `40000`. A `long` would work, but given the maximum value of `40000` and `int` is big enough, so there's no reason to use extra space for a `long`.

### <a name="a9"></a>**[EXERCISE 9](#q9)**

`float` literals are written the same as `double` literals, but with a trailing `f`. The `float` equivalent of `122.3` is `122.3f`. The `float` equivalent of `1.223e2` is `1.223e2f`.

### <a name="a10"></a>**[EXERCISE 10](#q10)**

If `x` is an `int` with value `5` and `y` is an `int` with value `3` then:

* `x + y * 5` evaluates to an `int` with value `20`.
* `x + (y * 5)` evaluates to an `int` with value `20` as well; the parenthesis are redundant, because multiplication happens before addition without them.
* `(x + y) * 5` evaluates to an `int` with value `40`; the parenthesis cause the addition to be evaluated before the multiplication.
* `y % x` evaluates to an `int` with value `3` (the remainder when `3` is divided by `5`).
* `y % x * y` evaluates to `9`; the `%` and `*` have the same precedence, so they are performed from left to right, so the `%` results in a `3` like before, which is then multiplied by `y`'s value, `3`.
* `y % (x * y)` evaluates to `3`. The parenthesis ensure that the multiplication is carried out first, resulting in `15`. The remainder when `3` is divided by `15` is `3`.

### <a name="a11"></a>**[EXERCISE 11](#q11)**

`y` ends up with value `-128`. This is because the maximum `byte` value is `127`; an attempt to convert `128` to a `byte` is an attempt to convert **1 more than `127`** to `byte` form. In Java (and most languages) when integer data becomes too large for its container, it "comes back in on the other side". In this case, 1 more than the maximum `byte` value, `127`, is the minimum `byte` value, `-128`.

### <a name="a12"></a>**[EXERCISE 12](#q12)**

* `System.out.println( 5 + " elephants" );` prints out "`5 elephants`".
* `System.out.println( 5 + 6 + " elephants" );` prints out "`11 elephants`". Addition is done from left to right, so the addition `5 + 6` is done before `String` concatenation.
* `System.out.println( 5 + (6 + " elephants") );` prints out "`56 elephants`". The parenthesis cause `6` to be added to `" elephants"` first, resulting in a `String` with value `"6 elephants"`, to which `5` is then concatenated.

### <a name="a13"></a>**[EXERCISE 13](#q13)**

* `z1` has the `int` value `2`, because it is calculated using integer division.
* `z2` has the `float` value `2.5f`, because it is calculated using floating point division; `x` is explicitly converted to a `float`, and `y` is then implicitly converted to match `x`'s type for division.
* `z3` has the `float` value `2.0f`. First, `x` is divided by `y` using integer division to get an integer value `2`, which is then converted to the `float` value `2.0f`.

### <a name="a14"></a>**[EXERCISE 14](#q14)**

This program:

```java
class MyClass
{
    public static void main(String[] args)
    {
        int x = 4;
        int y = 3;

        int z = Math.pow(x, y);

        System.out.println(x + " raised to the power " + y + " is " + z);
    }
}
```

does not compile because `Math.pow` returns a floating point value in the form of a `double`, and the program attempts to implicitly store that floating point value in an `int`. One way to fix this is to cast the result of the `pow` call to an `int`:

```java
class MyClass
{
    public static void main(String[] args)
    {
        int x = 4;
        int y = 3;

        int z = (int) Math.pow(x, y);

        System.out.println(x + " raised to the power " + y + " is " + z);
    }
}
```

However, as we've discussed, this might lead to a loss of precision. Due to floating point error, the `pow` call might return `63.999...` instead of `64`, and when this `63.999` is cast as an `int` it becomes `63`. (With these particular numbers, no rounding error occurs, but the idea is what matters).

Another way to fix the issue could be to make `z` a `double` so it can store the output of `Math.pow`:

```java
class MyClass
{
    public static void main(String[] args)
    {
        int x = 4;
        int y = 3;

        double z = Math.pow(x, y);

        System.out.println(x + " raised to the power " + y + " is " + z);
    }
}
```

However, in this case both inputs for `Math.pow` are integers, so the result is definitely an integer; we might want to store it in integer form, in which case we could use the `Math.round` function to round away the floating point error in the result of exponentiation (and make `z` a long, as this is the type returned by `Math.round`):

```java
class MyClass
{
    public static void main(String[] args)
    {
        int x = 4;
        int y = 3;

        long z = Math.round( Math.pow(x, y) );

        System.out.println(x + " raised to the power " + y + " is " + z);
    }
}
```

# Lab Assignment

## Task 1

Use the program below as a starting point. Below each commented instruction, write a corresponding statement that does what the comment describes. After each step, you should print out a message stating any variables that have changed with their new values.

A sample run is provided after the starter code.

```java
public class FillInTheCode
{
    public static void main(String[] args)
    {
        int a = 1;
        int b = 2;
        double c = 0;

        System.out.println("a is " + a);
        System.out.println("b is " + b);
        System.out.println("c is " + c);

        System.out.println("\nSetting c to the sum of a and b.");
        // TODO set c equal to the sum of a and b ("set c" means "assign c's value").

        System.out.println("\nDeclaring d, setting its value to a's value.");
        // TODO declare a new double with identifier d, and set its value to a's value.

        System.out.println("\nSetting d to 4 times the sum of a and d.");
        // TODO set d equal to 4 times the sum of a and d.

        System.out.println("\nSetting c to the average of a and b.");
        // TODO set c equal to the average of a and b (without loss of precision).
    }
}
```

### Task 1 Sample Run

```
a is 1
b is 2
c is 0.0

Setting c to the sum of a and b.
c is now 3.0

Declaring d, setting its value to a's value.
d is now 1.0

Setting d to 4 times the sum of a and d.
d is now 8.0

Setting c to the average of a and b.
c is now 1.5

Process finished with exit code 0
```


## Task 2

Using the program below as a starting point, write a program which prompts the user for the radius of a circle, reads their response in the console as a `double`, and calculates and prints the circle's area and circumference.

The provided code prompts the user for the radius and stores their response in the variable `radius`. You need to fill in the calculation of and printing of the area and circumference.

```java
import java.util.Scanner;

public class Circle
{
    public static void main(String[] args)
    {
        Scanner scan = new Scanner( System.in );
        System.out.print("Enter the radius of a circle : ");

        double radius = scan.nextDouble();

        // TODO find and print the area and circumference of the circle.
        // Your printed messages should be complete sentences, not just numbers.
    }
}
```

### Task 2 Sample Run

```
Enter the radius of a circle : 2.5
The area is 19.634954084936208 and the circumference is 15.707963267948966.

Process finished with exit code 0
```

## Task 3

In task 2, you have an example of use of the `Scanner` class from the `java.util` package to get user input in the form of a double. This `Scanner` class can be used to get other types of data from the console too! Find the API for the Java 8 `Scanner` (using your favorite search engine) and read through it to find the appropriate methods to use (instead of `nextDouble()`) to get the appropriate data from the user in the task below.

Note that you can use the same `Scanner` for multiple inputs. The line `Scanner scan = new Scanner( System.in );` **constructs** (i.e. sets up) a new `Scanner`, and this setup only needs to happen once. Afterward, the `Scanner` named `scan` can be used to get as many inputs as desired.

Also note the line `import java.util.Scanner;` at the top of the program in the previous task. The scanner is not in `java.lang`, the core of the Java language, so if you want to use it you need to `import` it.

Write a program which asks the user three questions. The first question should be answered with a `String`, the second with an `int`, and the third with a `boolean`.

Store the users responses to these questions in variables with the appropriate types.

Then, when the user is done answering all three questions, print out messages that summarize their responses to your questions.

A sample run is below. You can use the questions I used, but it's more fun if you make up your own!

### Task 3 Sample Run

```
SURVEY TIME

Why did the chicken cross the road?
Idk dude it's a chicken...

How many toes do you have?
7

true or false : Radishes are the coolest vegetable.
true


SURVEY SUMMARY:

The chicken crossed the road because "Idk dude it's a chicken..."

You have 7 toes...?

Radishes are the coolest vegetable : true

Process finished with exit code 0

```

## Task 4

Write a program which:

* prompts the user for 3 integers
* calculates and prints their average

Be careful not to use integer divsion! This will result in a loss of precision!

### Task 4 Sample Run

```
Enter an integer : 5
Enter another integer : 5
Enter a final integer : 6

The average of 5, 5 and 6 is 5.333333333333333
```

## Task 5

Write a program which prompts the user for an integer number of seconds.

The program should then print out the corresponding number of hours, remaining minutes, and remaining seconds.

### Task 5 Sample Run

```
Enter a number of seconds : 3661
3661 seconds is equivalent to 1 hours, 1 minutes, and 1 seconds.

Process finished with exit code 0
```

## Task 6

Write a program which prompts the user for a temperature in Fahrenheit and then prints out the equivalent temperature in Celcius.

### Task 6 Sample Run

```
Enter a temperature in Fahrenheit : 32.9
32.9 degrees Fahrenheit is equivalent to 0.4999999999999992 degrees Celcius.
```

## Task 7 (Optional)

Write a program which generates a random integer from `1` to `100` (inclusive), then prompts the user to guess the number. It should then print a message telling the user whether or not their guess is correct. This will require an `if` statement, use of the `Random` class and the `==` equality operator, none of which have been covered yet; you will need to do some research.

## Task 8 (Optional)

The following task requires functionality that has not been covered in this lecture. You will need to do some research to determine how to do it.

Create a file in your lab folder called `input.txt`. Open `input.txt`, and write some stuff on the first line. Do not add any additional lines.

Write a program which opens `input.txt`, reads its first line, and prints that line to the console.

This will require some research. Here is a brief overview; you'll need to google and find some examples to help you figure out exactly how to do this:

* Open your input file with the `File` class.
* Create a new `Scanner` (like we did to get input from the console). Instead of `System.in`, use your opened file as its input.
* Use the appropriate method from the `Scanner` class to read the first line of the file into a `String` variable.
* Print your `String` variable.

## Task 9 (Optional)

Edit your program from task 8 as follows: Instead of just writing a single line, print **all** lines from `input.txt` to the console.

Your program should work if `input.txt` has no lines, one line, or more than `input.txt` one line. You'll need to research the `while` loop (which we'll cover later in the semester) and the `Scanner`'s `hasNext` method.

