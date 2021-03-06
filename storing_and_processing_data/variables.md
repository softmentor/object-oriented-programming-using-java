## Variables

A variable is a **symbolic name** for information. The variable's name should represent what information the variable contains.
They are called variables because they represent *information that can change*.

Computer memory can be thought of a huge cabinet with millions of small drawers. The content of the drawers is the information
stored in memory that we use inside our application. While it is perfectly possible to refer to a drawer using its location (for example
second row, third column), it is a lot harder to remember. There is also no link between the location and the actual content of the drawer.
Now if we place a label on the drawer that is descriptive enough of its content, which is the analogy of our variable name, it is much easier to refer to the drawer using the descriptive name (for example nine inch nails).

![Memory is analogous to a huge cabinet with millions of small drawers](img/drawers_memory.png)

As a student you actually have already been using variables for quite a while. When doing math you also use symbolic names for variables. For example

```text
x = 15
y = 13

p = x * y
```

Or when defining a linear equation

```text
y = f(x) = ax + b
```

### Declaring a variable

Before a variable can be used inside an application, it needs be **declared**. Declaring a variable can be thought of as stating to the Java interpreter that is needs to request memory for data and make it accessible using a symbolic variable name. Because the Java interpreter needs to know how much memory to set aside, you as a programmer need to specify what **type of data** the variable will hold.

The type of the variable determines the size and layout of the variable's memory; the range of values that can be stored within that memory; and the set of operations that can be applied to the variable.

Once you provided the type and name, the variable can be used to store data.

Let's take a look at an example where a variable stores the age of a person. In this case we need to define the variable to be of an *integral type*. In Java the data type is `int` (integer) for this, which can store *whole signed numbers*.

```java
public static void main(String[] args) {

    // Declaring a variable of type integer
    // and make it accessible using the symbolic name ageOfPerson
    int ageOfPerson;

    // Assign a value to the variable
    ageOfPerson = 31;

    // The variable name can also be used to retrieve the data
    System.out.println("I am " + ageOfPerson + " years old and I am a teacher at VIVES University College");
}
```

The data referred to by the variable can be changed using the **assignment operator** `=`. This is basically the same as in
math. On the left hand side you have the variable which you want to assign and on the right hand side the value.

When you wish to use the content of the variable, all you need to do is state the symbolic name where you would otherwise
use a value.

This also means that one variable can be used to assign a value to another.

```java
public static void main(String[] args) {
  int numberOfStudents;
  numberOfStudents = 36;

  int numberOfEmailAddresses;
  numberOfEmailAddresses = numberOfStudents;

  System.out.println("We have " + numberOfStudents + " students meaning we also have " + numberOfEmailAddresses + " email addresses");
}
```

Note how the variable needs to be declared (created by stating a type and name) before it is used. The following code is therefore flawed and will not run. `numberOfStudents` and `numberOfEmailAddresses` are used before they are declared.

```java
public static void main(String[] args) {
  numberOfStudents = 36;
  numberOfEmailAddresses = numberOfStudents;

  System.out.println("We have " + numberOfStudents + " students meaning we also have " + numberOfEmailAddresses + " email addresses");

  int numberOfEmailAddresses;
  int numberOfStudents;
}
```

> #### Hint::Declare a variable before using it
>
>  You must declare a variable before it can be used. This is a rule for many programming languages but not for all. Some programming languages will automatically create variables as they are used.

While the code below is perfect working code, you will not often see it being written by a more experienced programmer:

```java
public static void main(String[] args) {
  int numberOfStudents;
  numberOfStudents = 36;
}
```

This because when a variable is declared, you can **immediately initialize it** with a value in a single line of code as shown below.

```java
public static void main(String[] args) {
  int numberOfStudents = 36;
}
```

It is important to always initialize a variable before using it. If you use the variable before initializing it, you may create bugs in your program. Often Java will not even allow the usage of a variable if it is not initialized. This safety net is not provided by all programming languages. For example C++ will allow you to use uninitialized variables. In this case their value is undetermined and often contains the values of the previous program that used that same location in memory.

### Primitive data types

The `int` (integer) data type is called a **primitive data type**. Primitive data types are simple data types that are integrated in the programming language itself (they are most of the time keywords in the language). They form the base of all data storage inside your application. While more complex data types are available, or can even be created by us, in the end it always comes down to primitive data types storing the actual data.

Integer is not the only type that is supported by Java. A full overview of the different primitive data types is given below.

* `byte`: The byte data type is an 8-bit signed two's complement integer. It has a minimum value of -128 and a maximum value of 127 (inclusive). The byte data type can be useful for saving memory in large arrays, where the memory savings actually matters.

* `short`: The short data type is a 16-bit signed two's complement integer. It has a minimum value of -32,768 and a maximum value of 32,767 (inclusive). As with byte, the same guidelines apply: you can use a short to save memory in large arrays, in situations where the memory savings actually matters.

* `int`: By default, the int data type is a 32-bit signed two's complement integer, which has a minimum value of -2^31 and a maximum value of 2^31-1.

* `long`: The long data type is a 64-bit two's complement integer. The signed long has a minimum value of -2^63 and a maximum value of 2^63-1.

* `float`: The float data type is a single-precision 32-bit IEEE 754 floating point. Its range of values is 3.40282347 x 10^38 to 1.40239846 x 10^-45. As with the recommendations for byte and short, use a float (instead of double) if you need to save memory in large arrays of floating point numbers. This data type should never be used for precise values, such as currency.

* `double`: The double data type is a double-precision 64-bit IEEE 754 floating point. Its range of values is 1.7976931348623157 x 10^308, 4.9406564584124654 x 10^-324. For decimal values, this data type is generally the default choice. As mentioned above, this data type should never be used for precise values, such as currency.

* `boolean`: The boolean data type has only two possible values: `true` and `false`. Use this data type for simple flags that track true/false conditions. This data type represents one bit of information, but its "size" isn't something that's precisely defined.

* `char`: The char data type is a single 16-bit Unicode character. It has a minimum value of 0 and a maximum value of 65,535 inclusive.

> #### Warning::String is not a primitive datatype
>
>  Note that String is not listed above as a primitive datatype. That is because Strings are actually objects. More on this later.

Examples of variable declarations of different data types:

```java
int numberOfStudents = 55;              // Simple integer

char startOfAlfabet = 'a';              // Characters (from the alfabet) or other symbols
char dollarSign = '$';
char endOfLine = '\n';

// Floating point numbers
float averageWaterUseage = 3870.35478;  
double averageStudentScore = 12.5;      

// Booleans can only be true or false
boolean isOlderThanEighteen = true;
boolean isStillATeenager = false;
```

A string in Java is always placed between double quotes, for example `"Hello my name is Nico"`. A single character is placed between single quotes, as also seen in the example code above. Special characters, such as an end-of-line `'\n'` can also be stored in a variable of type char.

A character preceded by a backslash `\` is an escape sequence and has special meaning to the compiler. The following table shows the Java escape sequences:

|Escape Sequence |	Description|
| ------ | -------|
|`\t` |	Insert a tab in the text at this point.|
|`\b` |	Insert a backspace in the text at this point.|
|`\n` |	Insert a newline in the text at this point.|
|`\r` |	Insert a carriage return in the text at this point.|
|`\f` |	Insert a formfeed in the text at this point.|
|`\'` |	Insert a single quote character in the text at this point.|
|`\"` |	Insert a double quote character in the text at this point.|
|`\\` |	Insert a backslash character in the text at this point.|

These escape characters can be used inside a string or can be stored in a variable of type `char`.

```java
public static void main(String[] args) {
    System.out.println("There\tis\ta\ttab\tbetween\teach\tword");
    System.out.println("You can also use quotes here but they need to be escaped:");
    System.out.println("--------------------------------------------------------");
    System.out.println("\"C makes it easy to shoot yourself in the foot; C++ makes it harder,\nbut when you do it blows your whole leg off.\"");
    System.out.println("by Bjarne Stroustrup");
    System.out.println("--------------------------------------------------------");
}
```

Which generates the following output:

```text
There	is	a	tab	between	each	word
You can also use quotes here but the need to be escaped:
--------------------------------------------------------
"C makes it easy to shoot yourself in the foot; C++ makes it harder,
but when you do it blows your whole leg off."
by Bjarne Stroustrup
--------------------------------------------------------
```
