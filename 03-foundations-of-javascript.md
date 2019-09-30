title: TWeb
subtitle: <i class="fas fa-tasks"></i> Foundations of JavaScript
author: Bertil Chapuis
class: animation-fade
layout: true

<!-- This slide will serve as the base layout for all your slides -->

---

class: inverse center middle

# {{title}}

## {{subtitle}}

<p style="margin-top: 40px">{{author}}</p>

---

## <i class="fas fa-tasks"></i> Overview of Today's Class

- Quiz about last week's lecture

- Correction of last week's assignment

- JavaScript

  - Values, Types, and Operators

  - Program Structure

  - Functions

- Developper Tools

  - Chrome DevTools

  - Visual Studio Code

- Introduction of next week's assignment

---

class: inverse center middle

#  <i class="fas fa-question-circle"></i> Quiz

---

# <i class="fas  fa-question-circle"></i> Speakup

You can answer to the following Quiz on Speakup.

http://www.speakup.info/

Room Number:  **XXXXX**

Once connected, answer to the first test question.

---

# <i class="fas fa-question-circle"></i> Question 1

A quelle couche de la Suite des protocoles Internet (Internet Protocol Suite) le protocol TCP appartient-il?

**A)** Application

**B)** __Transport__

**C)** Internet

**D)** Link

---

# <i class="fas fa-question-circle"></i> Question 2

Quel protocol est utilisé par DNS pour transférer les fichiers de Zone?

**A)** HTTP

**B)** __TCP__

**C)** IP

**D)** UDP

---

# <i class="fas fa-question-circle"></i> Question 3

Qu'est qu'un Root Server dans le Domain Name System (DNS)?

**A)** Un serveur qui gère les sous domaine d'un nom de domaine racine (www.domaine.com, web.domaine.com, etc.)

**B)** Un serveur qui gère la racine des noms appartenant à un domaine (domaine1.com, domaine2.com, etc.)

**C)** __Un serveur qui gère la racine des noms de domaine (com, org, net, etc.)__

**D)** Aucune affirmation correcte

---

# <i class="fas fa-question-circle"></i> Question 4

Dans le domaine `www.example.com`, qu'est-ce que le sous-domaine (subdomain)?

**A)** __www__

**B)** example

**C)** com

**D)** Aucune affirmation correcte

---

# <i class="fas fa-question-circle"></i> Question 5

A quoi sert un DNS lookup?

**A)** A assigner une adresse IP à un nom de domaine?

**B)** A obtenir une connexion HTTP à partir d'un nom de domaine?

**C)** A visualiser la route prise par les packets sur le réseau?

**D)** __Aucune affirmation correcte__

---

# <i class="fas fa-question-circle"></i> Question 6

A quelle partie de l'url correspond le fragment?

`https://tim:1234@example.com:443/index.html?param=value#home`

**A)** ?param=value

**B)** /index.html

**C)** tim:1234

**D)** __#home__

**E)** https://

---

# <i class="fas fa-question-circle"></i> Question 7

Une requête HTTP contient toujours:

**A)** __une méthode__

**B)** __une resource__

**C)** __des headers__

**D)** un body

**E)** un port de destination

**F)** une code de status (status code)

**G)** un user agent (User-Agent)

---

# <i class="fas fa-question-circle"></i> Question 8

Parmis les éléments suivants, identifiez le ou lesquels correspondent à du HTML valide:

**A)** `<a href="https://www.heig-vd.ch">Heig-vd<a>`

**B)** `<img src="image.jpg" />`

**C)** __`<p>Mon paragraphe</p>`__

**D)** `<!DOCTYPE html>`

**E)** `Aucun element correct`

---

# <i class="fas fa-question-circle"></i> Question 9

Qu'est ce que le DOM?

**A)** Un arbre (tree) qui représente le CSS en mémoire

**B)** La strucutre d'un fichier HTML sauvée sur le disque

**C)** Un language de programmation permettant de manipuler des documents

**D)** __Aucune réponse correcte__

---

# <i class="fas fa-question-circle"></i> Question 10

Qu'est-ce qu'une déclaration CSS?

**A)** __Une paire propriété et valeur__

**B)** Un bloc contenant une liste de propriétés CSS

**C)** Un sélecteur CSS associé à une liste de propriétés CSS

**D)** La valeur d'une propriété CSS

---

# <i class="fas fa-question-circle"></i> Question 11

Quelles elements HTML de la structure suivante sont sélectionnés par le selecteur `ul li:nth-child(1)`?

```html
<ul>
    <li>A</li>
    <li>B</li>
    <li>C
        <ul>
            <li>D</li>
            <li>E
                <ol>
                    <li>F</li>
                    <li>G</li>
                </ol>
            </li>
        </ul>
    </li>
</ul>
```

Bonne réponses: A, D, F

---

# <i class="fas fa-question-circle"></i> Question 12

A quel rendu correspond le code HTML/CSS suivant? (Bonne réponse: C)

```html
<div id="a">
  <div id="b">
    Hello World!
  </div>
</div>
```

```css 
#a {
  display: block;
  padding: 10px;
  background-color: red;
  border: solid 10px black;
}
#b {
  text-align: center;
  display: block;
  background-color: white;
}
```

<img src="images/quiz_html_css_b.png" style="width:250px">
<img src="images/quiz_html_css_c.png" style="width:250px">
<img src="images/quiz_html_css_a.png" style="width:250px">
<img src="images/quiz_html_css_d.png" style="width:250px">

---

class: inverse center middle

# <i class="far fa-edit"></i> Correction

---

.center[
<img src="images/ex1_screenshot.png"  style="width:600px" />
]

---

class: center middle


# <i class="fas fa-hand-paper"></i> Questions ?




---

class: inverse center middle

# <i class="fab fa-js"></i> JavaScript

---

## <i class="fab fa-js"></i> JavaScript.red[*]

JavaScript is a lightweight, **interpreted**, or **just-in-time** compiled programming language with first-class functions.

### Interpreted 
The execution does not require the compilation of the programm into machine-code.

### Just-in-time (JIT)
The parts of the the program that are hot (called a lot) are compiled into machine code.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript]

---

## <i class="fab fa-js"></i> JavaScript.red[*]

JavaScript is a **prototype-based**, multi-paradigm, **dynamic** language, supporting **object-oriented**, **imperative**, and **declarative** (e.g. functional programming) styles.

### Dynamic
Performs at runtime what static languages perform at compilation time (e.g. dynamic typing).

### Object Oriented and Prototype-based
Behavior reuse (and inheritence) is performed by cloning and extending objects.

### Imperative 
Mutates the state of the program using statements.

### Declarative
A programming style that avoids side effects by describing what a computation should perform.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript]

---

## <i class="fab fa-js"></i> JavaScript and ECMAScript History

ECMAScript (or ES) is a specification created by Ecma International to standardize JavaScript.

.center[
<img src="images/js_history_es6.png" alt="JavaScript History" style="width: 80%; margin-top: 100px;">
]

---

## <i class="fab fa-js"></i> From the browser to the server

Server-side JavaScript is not a novel idea (Netscape was already doing it in 1996).

Rhino, a JavaScript engine written in Java by has been released as early as 1997.

In 2008, the first version of Chrome includes [V8](https://v8.dev/), an open-source JavaScript engine created by Lars Bak.

In 2009, Ryan Dahl creates node.js, a JavaScript environment based on V8 that runs on the server.


<img src="images/logo_v8.png" style="width: 150px; float: left" />

<img src="images/logo_nodejs.png" style="margin-left: 40px;width: 130px; float: left" />

---

## <i class="fab fa-js"></i> Client-side and Server-side Programming

Today, JavaScript is commonly used in the browser (client-side) and on the server (server-side).

.center[
<img src="images/Fetching_a_page.png" style="width: 60%; margin-top: 40px" />
]

---

## <i class="fab fa-js"></i> ECMAScript 6 Support.red[*]

.center[
<img src="images/js_compat_table.png" style="width: 100%" />
]

.footnote[.red[*] https://kangax.github.io/compat-table/es6/]

---

## <i class="fab fa-js"></i> Eloquent Javascript.red[*]

<img src="images/js_eloquent_javascript.jpg" style="width: 30%" />


.footnote[.red[*] https://eloquentjavascript.net/]

---

## <i class="fab fa-js"></i>Client-side Javascript

Include JavaScript stored in the HTML:

```html
<scriptt type='text/javascript'>
  console.log('Hello, World!');
  document.writeln('Hello, World!')
</scriptt>
```

Include JavaScript stored in a separate file:

```html
<scriptt src="script.js"></scriptt>
```

The `async` attribute indicates that the browser should load the script asynchronously and then execute it as soon as it’s downloaded.

The `defer` attribute indicates that the browser should execute the script after the document has been parsed but before the DOM content has been loaded.

The `type="module"` attribute causes the code to be treated as a JavaScript module (ECMAScript 6).

---

## <i class="fab fa-js"></i> Server-side Javascript.red[*]

After installing nodejs, a REPL (Read-Eval-Print-Loop) can be obtained by typing the node command:

```bash
$ node
Welcome to Node.js v12.8.0.
Type ".help" for more information.
> console.log("Hello, World!")
Hello World!
```

.footnote[.red[*] https://nodejs.org/api/repl.html]

---

## <i class="fas fa-hand-paper"></i> Get to know the REPL commands.red[*]


- `.clear` - Resets the REPL context to an empty object and clears any multi-line expression currently being input.
- `.exit` - Close the I/O stream, causing the REPL to exit.
- `.help` - Show this list of special commands.
- `.save` - Save the current REPL session to a file: > .save ./file/to/save.js
- `.load` - Load a file into the current REPL session. > .load ./file/to/load.js
- `.editor` - Enter editor mode (<ctrl>-D to finish, <ctrl>-C to cancel).

.footnote[.red[*] https://nodejs.org/api/repl.html#repl_commands_and_special_keys]

---

## <i class="fab fa-js"></i> JavaScript's Types

ECMAScript defines 7 **primitive** (Immutable) types for values.

```js
3.14; // Number
true; // Boolean
"Heig-vd"; // String
undefined; // Undefined
null; // Null
9007199254740992n; // BigInt
Symbol("Symbol") // Symbol
```

ECMAScript defines a special mutable type called **object** for collections of properties (objects and array).

```js
{prop: "value"}; // Object
```

In a dynamic language you don't specify the type when you declare a variable and the type of a variable can change.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Data_types]



---

## <i class="fab fa-js"></i> JavaScript Operators

### Typeof

The `typeof` operator returns a string indicating the type of the unevaluated operand.

### Assignment

An assignment operator assigns a value to its left operand based on the value of its right operand.

```js
a = 1; 

// arithmetic assignments
a += 1; // addition
a -= 1; // subtraction
a *= 1; // multiplication
a /= 1; // division
a %= 1; // modulo
a **= 1; // exponentiation
```




---

## <i class="fab fa-js"></i> JavaScript Operators

### Arithmetic 

```js
1 + 1; // addition
1 - 1; // subtraction
1 / 1; // division
1 * 1; // multiplication
1 % 1; // modulo
1 ** 1; // exponentiation
```

### String

```js
"con" + "cat" + "e" + "nate";
`PI = ${Math.PI}`; // template literals
```

### Logical

```js
!true // false
true && false // false
true || false // true
true ? true : false // true
```


---

## <i class="fab fa-js"></i> JavaScript Operators

### Comparison

```js
1 < 2;
2 > 1;
1 == 1;
1 != 2;
```

### Automatic Type Conversion

Automatic type conversion is a the root of many issues.

```js
"1" == 1 // true
false == 0 // true
8 * null // 0
```

### Strict equality

Strict equality compares both the type and the value.

```js
"1" === 1 // false
```

---

## <i class="fab fa-js"></i> JavaScript Statements

The `var` statement declares a variable, optionally initializing it to a value. The **scope** of a variable declared with var is its current execution context, which is either the enclosing function or, for variables declared outside any function, global.

```js
var x = 1;
{var x = 2;} // same variable
console.log(x); // 2
```

The `let` statement declares a block scope local variable, optionally initializing it to a value. The **scope** of a variable declared with let is limited to its block or expression.

```js
let x = 1;
{let x = 2;} // different variable
console.log(x); // 1
```

Constants are block-scoped, much like variables defined using the let statement. The value of a constant can't be changed through reassignment, and it can't be redeclared.

```js
const x = 1;
x = 2; // raises an error
```

A single statement can define multiple variables or constants: `let one = 1, two = 2;`.

---

## <i class="fab fa-js"></i> JavaScript Conditional Execution

In JavaScript, conditional execution is created with the if keyword.

```js
let num = 1;
if (num < 10) {
  console.log("Small!");
} else if (num < 100) {
  console.log("Medium");
} else {
  console.log("Large");
}
```


---

## <i class="fab fa-js"></i> JavaScript While and Do While

While and do while are used to loop until a condition is met.

```js
let num = 0;
while (num < 10) {
  console.log(num);
  num += 1;
}
```

```js
let num = 0;
do {
  console.log(num);
  num += 1;
} while (num < 10);
```

---

## <i class="fab fa-js"></i> JavaScript For Loops

The classic `for` statement is used to loop a given number of times over a block.

```js
for (let num = 0; num < 10; num++) {
  console.log(num);
}
```

The `for...in` statement iterates over the enumerable properties of an object.

```js
var object1 = {a: 1, b: 2, c: 3};
for (var property1 in object1) {
  string1 += object1[property1];
}
```

The `for...of` statement creates a loop iterating over iterable objects.

```js
let nums = [0, 1, 2, 3, 4, 5, 6, 7, 8 , 9];
for (let num of nums) {
  console.log(num);
}
```

---

## <i class="fab fa-js"></i> JavaScript Break and Continue.red[*]

The `break` statement terminates the current loop.

The `continue` statement terminates execution of the current iteration and continues execution of the loop with the next iteration.

`break` and `continue` can also be used with labelled statements.

```js
mylabel:
for (let num = 0; num < 5; num++) {
  if (num === 5) {
    continue mylabel;
  }
  console.log(num)
}
```

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label]


---

## <i class="fab fa-js"></i> JavaScript Switch

Sometimes a switch is more direct than an `if...elseif...else` statement.

```js
let val = "a";
switch(val) {
  case "a":
    doSomething(val);
    break;
  case "b":
    doSomethingElse(val);
    break;
  default:
    doNothing(val);
    break;
}
```

---

## <i class="fab fa-js"></i> JavaScript Exceptions
 
In Javascript, exceptions can be handled using the `try...catch` statement.

```js
try {
  variable; // ReferenceError: variable is not defined
} catch (error) {
  // Fails silently
}
```

Exceptions can be triggered  using `throw` and `Error`:

```js
throw new Error("AAHHARG!!!");
```

---

## <i class="fab fa-js"></i> JavaScript Functions

A function is created with an expression that starts with the keyword `function` and can be assigned to a regular regular variable.
It can have parameters and may `return` a value.

```js
var square = function(x) {
  return x * x;
}
```

### Declaration Notation

```js
function square(x) {
  return x * x;
}
```

### Arrow Functions

```js
var square = x => x * x
```

```js
var square = (x) => {
  return x * x;
} 
```

---

## <i class="fab fa-js"></i> JavaScript Function Parameters

Function parameters can be made optional by specifying default values.

```js
var square = function(x = 2) {
  return x * x;
}
square() // 4
```

---

## <i class="fab fa-js"></i> JavaScript Function Scopes

The scope of a variable, is the part of the program in which it is visible. 

The scope of the variables defined with `var` outside of a function is `global`, it is visible everywhere.

The scope of the variables defined with `let` and `const` are `local` to the block that they are declared in.

The scope of function parameters can be referenced only in that function and are `local`.

Local variables added to the **call stack** every time a function is called and freed it returns.

## Closure

A closure is the combination of a function and the local scope within which that function was declared.

```js
function wrap(value) {
  let v = value;
  return () => v;
}
wrap(1)() // 1
```
---

## <i class="fab fa-js"></i> JavaScript Recursion

It is fine for a function to call itself.

```js
function factorial(n) {
  return n == 1 ? n : n * factorial(n-1); 
}
factorial(5) // 5 * 4 * 3 * 2 * 1 = 120
```

.. as long as it does not overflow the call stack.

---

## <i class="fas fa-hand-paper"></i> JavaScript DevTools

- Experiment with the Chrome DevTools

- Experiment with the Visual Studio Code

---

## <i class="fas fa-hand-paper"></i> JavaScript Exercise

- Implement a recursive function that computes the fibonacci sequence.

- Look the call stack with the Chrome DevTools.

---

class: center middle inverse

# <i class="fas fa-hand-paper"></i> Questions ?

---

## <i class="fas fa-hand-paper"></i> Questions about Today's Lecture

- JavaScript

  - Values, Types, and Operators

  - Program Structure

  - Functions

- Developper Tools

  - Chrome DevTools

  - Visual Studio Code

---

class: inverse center middle

# <i class="fas fa-tasks"></i> Group Assignment

---

#  <i class="fas fa-tasks"></i> Group Assignment

- Same groups as last week

- Install Visual Studio Code, Node.js and Docker

- If needed, watch Olivier's webcasts on [client-side](https://www.youtube.com/watch?v=qAVGS85SmSg&list=PLfKkysTy70QZUPYjLkkYcwqvVph4q9cKZ&index=3&t=0s) and [server-side](https://www.youtube.com/watch?v=YMqIChybZCE&list=PLfKkysTy70QZUPYjLkkYcwqvVph4q9cKZ&index=4&t=0s) debugging.

- Go to the [Github Classroom](https://classroom.github.com/classrooms/54867215-tweb-classroom) and start exercise 2 (Introduction to JavaScript)

- **Interact** with the assistants if needed... ;)

- The repository will be frozen **next Tuesday at 12am**
