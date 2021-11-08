# Clean Code

## Introduction

All of us write code, but what separates an excellent programmer from an average programmer is **clean code**. Computers can run code regardless if it's clean or not, although humans have problems understanding and developing upon badly written code.

I have been trying since I have first written proper code to write cleaner and cleaner code over the years. In this file, I will include what I learned over the years, either from personal experience or from what other people, who have been coding far more than I have, told me.

I will also include **examples** of badly written code and clean code in the C programming language so you view the difference yourself side by side.

<br>

## Table of contents

1) **[Variable names](#variable-names)**
2) **[Function names](#function-names)**
3) **[What functions should do and not do](#what-functions-should-do-and-not-do)**
4) **[Formatting](#formatting)**
5) **[Comments](#comments)**
6) **[Camel Case](#camel-case)**
7) **[Useful resources](#useful-resources)**
8) **[Notes](#notes)**

<br>

---

### Variable names

One of the most useful rules is writing **proper variable names**. A variable name should indicate what is going to be used in the code without the programmer having to think or look through the entire code to find meaning, this is done by giving it a good name and **descriptive name**, not single-letter names.

Example:

Badly written code

```C
int a;
int b;
int c;

scanf("First number: %i", &a);
scanf("Second number: %i", &b);

c = a + b;

printf("Result: %i", c);
```

<br>

Well written code

```C
int firstNumber;
int secondNumber;
int result;

scanf("First number: %i", &firstNumber);
scanf("Second number: %i", &secondNumber);

result = firstNumber + secondNumber;

printf("Result: %i", result);
```

In this example I have written some code to add two numbers and display the result, both of those programs compile and run, but the badly written code example has **less descriptive** variable names, now imagine if we were to write **thousands** of lines of code with bad variable names and you can see how much time a simple and descriptive name can save us.

<br>

### Function names

Just like variable names, function names should have a **descriptive** name to indicate their **function** to the programmer, either the programmer is you or your co-worker that reads your code for the first time.

Example:

Badly written code

```C
void file(FILE* inputFile) {
    char inputChar;

    while ((inputChar = fgetc(inputFile)) != EOF) {
        printf("%c", inputChar);
    }
}
```

<br>

Well written code

```C
void displayFileContents(FILE* inputFile) {
    char inputChar;

    while ((inputChar = fgetc(inputFile)) != EOF) {
        printf("%c", inputChar);
    }
}
```

In this example, I have written a simple function that reads and displays the contents of a file to the terminal, just like before both of these samples compile and run, but for a programmer, it might be difficult to understand the functionality of a **function based on a name like file** like I have done in the badly written code example above.

<br>

### What functions should do and not do

It is very tempting to cram pack a function full of functionality but it's not useful in the long run. A function needs to do **one thing and one thing only** which is mentioned in the **name** of the function.

Example:

Badly written code

```C
void addNums(int firstNum, int secondNum, char* msg) {
    int result = firstNum + secondNum;

    printf("%s%i", msg, result);
}
```

<br>

Well written code

```C
int addNums(int firstNum, int secondNum) {
    return firstNum + secondNum;
}
```

Both functions add the two numbers but first function also displays a message and the result without returning the number itself, although that may be useful in **some** scenarios a function must almost always do one thing and one thing only.

If the function is about opening a file it should open a file and **return the output** to a variable, it should not open a file and print the result first for example. If the function is about writing to a file it should **get some input from the parameters** and write that data to the file, the function itself should **not** get input from the user and then save the input from the user to the file.

<br>

### Formatting

Formatting your code is very important to make it more understandable and not what I like to call *[spaghetti code](https://en.wikipedia.org/wiki/Spaghetti_code#Examples)*.
There is no clear way to do it but I personally separate the code in segments of code.

Example:

Badly written code

```C
int main(int argc, char** argv) {
    if (argc == 1){
        printf("NO INPUT DETECTED\n");
        return -1;
    }
    FILE* inputFile = fopen("input.txt", "r");
    displayFileContents(inputFile);
    fclose(inputFile)
    return 0;
}
```

<br>

Well written code

```C
int main(int argc, char** argv) {
    if (argc == 1){
        printf("NO INPUT DETECTED\n");
        return -1;
    }

    FILE* inputFile = fopen("input.txt", "r");
    displayFileContents(inputFile);
    fclose(inputFile)
    
    return 0;
}
```

This is the exact same code but with two extra lines to **separate** the code segments, from the start when we check if there is a file name, to the middle when we open / read / close the file, and in the end when we terminate the program. This makes it **far easier** for someone to **understand the structure** of the code. One more good practice to follow is using camel case in variable names and function names.

<br>

### Comments

Comments are something I personally avoid, this is because I prefer the code to **"speak for itself"** whenever I can. If code needs comments to explain what it does it might be because the code is not written in a clean way. With that said, I will mention one use of comments which I personally find very useful, which is to explain at the **start of the code** the purpose of the program, the input, and the output of the program.

Example:

```C
/*
Program name: Text editor
Input: Filename (string)
Output: Output File (File)

Purpose: This is a terminal text editor just like nano 
or vim, it takes the name of the file you wish to create 
or edit and during the exit of the program it will save
or create the following file with the data the user entered
during the runtime of the program
*/
```

<br>

### Camel Case

Camel case is really useful because it makes your code easier  to read with basically no real work involved, you just capitalize some letters there and there and that's really it, and this ease is why it's one of the **core basics of writting clean code**. Camel case is mostly *(if not only)* used in two seperate cases, one of them being how you name variable names and the second is naming function names, and they may sound simple and kinda mundane but they **really** do make a difference.

Example:

Badly written code

```C
int main(int argc, char** argv) {
    int outputnum = addtwonums(numone, numtwo);

    printf("The result is %i\n", outputnum);

    return 0;
}
```

<br>

Well written code

```C
int main(int argc, char** argv) {
    int outputNum = addTwoNums(numOne, numTwo);

    printf("The result is %i\n", outputNum);

    return 0;
}
```

<br>

---

### Useful resources

The videos below are a few videos I **highly** recommend you watch about how to write clean code and what clean code is about. 

<br>

Videos:
* https://www.youtube.com/watch?v=UjhX2sVf0eg
* https://www.youtube.com/watch?v=HcijbAI4eB0
* https://www.youtube.com/watch?v=flzINYpIcc8

<br>

---

### Notes

If you have any suggestions about how to make this tutorial better please, by all means, help me do add those suggestions so more people can learn how to write clean code.
