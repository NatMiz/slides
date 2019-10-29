title: TWeb
subtitle: <i class="fas fa-tasks"></i> Regular Expressions and Web Applications
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

- Regular Expressions

- HTML Forms

- Web Applications with Express

- Introduction of next week's assignment

---

class: inverse center middle

#  <i class="fas fa-question-circle"></i> Quiz

---


# <i class="fas  fa-question-circle"></i> Feeling the Quiz Fatigue?


.center[

<img src="images/speakup_comeback.gif" style="width: 50%; margin-top: 40px" />

Speakup will **comeback**... 

Sooner or later!
]

---

# <i class="fas fa-question-circle"></i> Coding Challenge


Ecrivez un programme qui, étant donné les titres de livres suivants, crée un index inversé.

```js
var stopwords = ["the", "and", "a", "in"]
var books = ["Fantastic Mr Fox", " The Fox and the Star", "The Fox and the Hound", "Fox in Socks", "Maybe a Fox"];

var index = books.map().flatMap().reduce();

var stopwords = ["the", "and", "a", "in"]
var books = ["Fantastic Mr Fox", " The Fox and the Star", "The Fox and the Hound", "Fox in Socks", "Maybe a Fox"];

// Solution presented in class
var index = books
    .map(book => book.toLowerCase().split(" ")) 
    .map(words => words.filter(word => word != '' && !stopwords.includes(word))) 
    .flatMap((words, position) => words.map(word => [word, position]))
    .reduce((dict, [word, position]) => {
        dict[word] = dict[word] || [];
        dict[word].push(position);
        return dict;
    }, {});

index["fox"] // [0, 1, 2, 3, 4]
index["fantastic"] // [0]
index["the"] // undefined
```

---

class: inverse center middle

# <i class="far fa-edit"></i> Correction

---

class: center middle

## <i class="fas fa-hand-paper"></i> Ex5: Express and Form Validation

---

class: center middle

# <i class="fas fa-hand-paper"></i> Questions ?

---


class: inverse center middle

# <i class="fab fa-js"></i> Regular Expressions

---

## <i class="fab fa-js"></i> Regular Expressions .red[*]

Regular expressions are patterns used to **match** and **extract** character combinations in strings. 

It is usefull for validating inputs, parsing files, extracting information from free text.

For instance, given the format for [registration plates](https://fr.wikipedia.org/wiki/Plaque_d%27immatriculation_suisse
) in Switzerland: 
- Validate that the given string a valid registration plate
- Extract all the registration plates listed in a unstructured text 

Format for registration plates in Switzerland:

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions]

---

## <i class="fab fa-js"></i> Building Regular Expressions .red[*]

The following notations can be used to define a regular expression in Javascript.

```js
var re = /ab+c/;
var re = new RegExp(/ab+c/);
```

A regular expression is usually built in a **recursive** fashion with the following constructs:

- **Character Classes** (`.`, `\s`, `\d`) that distinguish types of chararters (letters or digits)
- **Character sets** (`[a-z]`) that match any of the enclosed characters
- **Either operator** (`x|y`) that match either the left or right handside values
- **Quantifiers** (`*`, `+`, `?`, `{n}`, `{n,m}`) that indicate the number of times an expression matches
- **Boundaries** (`^`, `$`) that indicate the beginnings and endings of lines and words
- **Groups** (`()`, `(?<name>)`, `(?:)`) that extracts and remember (or not) information from the input 
- **Assertions** (`x(?=y)`) that helps at defining conditional expressions


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions]

---


## <i class="fab fa-js"></i> Fun with Flags .red[*]

Regular expressions have optional flags that allow for functionality like global and case insensitive searching.

```js
var re = /ab+c/; // no flag
var re = /ab+c/g; // global search
var re = /ab+c/i; // case-insensitive search
var re = /ab+c/m; // multi-line search

var re = /ab+c/gi // global case-insensitive search
```

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions]


---

## <i class="fab fa-js"></i> Executing Regular Expressions .red[*]

The following notations can be used to execute regular expressions.

```js
var re = /ab+c/g;

re.test("ac"); // false
re.test("abbc"); // true

re.exec("ac"); // null
re.exec("abbc"); // ["abbc"]

"abc abbc".matchAll(re); // [["abc"], ["abbc"]]
```

In addition to `matchAll`, a string comes with the `match`, `replace`, `search` and `split` methods.


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions]

---

## <i class="fas fa-hand-paper"></i> Hands-on with Regular Expressions

- Try the afformentionned constructs with an online regex evaluator.

- Write a regular expression that extracts the canton and the number of a Swiss registration plates.

- Write a regular expression that extracts a list of Swiss registration plates from a free text.

.footnote[.red[*] https://regexr.com]

---

class: inverse center middle

# <i class="fab fa-js"></i> HTML Forms

---

## <i class="fab fa-js"></i> HTML Forms .red[*]

HTML Forms are one of the main points of interaction between a user and a web site or application. Forms allow users to enter data, generally sending that data to the web server.

The `<form>` element defines a form.

```html
<form action="/articles/" method="POST">
    <label for="email">Author's e-mail:</label>
    <input type="email" id="email" name="email">
    <label>Title:
        <input type="text" id="title" name="title">
    </label>
    <label for="content">Content:</label>
    <textarea id="content" name="content"></textarea>
    <button type="submit">Save</button>
</form>
```

- The `action` attribute defines the location (URL) where the form should be sent when it is submitted.
- The `method` attribute defines which HTTP method to send the data with (it can be "get" or "post").

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Your_first_HTML_form]

---

## <i class="fab fa-js"></i> HTML Input Element .red[*]

How an `<input>` works varies considerably depending on the value of its type attribute.

Some of the available types are: `text`, `password`, `submit`, `hidden`, `radio`, `checkbox`, `file`, `email`, `url`, `date`, `url`, etc.

- The `name` attribute specifies a name for the value, which is used when the form is submitted.

- The `value` attribute specifies the default value of the `<input>`.

- The `paceholder` attribute lets you specify a text that appears within the `<input>` element's content area itself when empty.

- The `required` attribute indicates that the `<input>` is mandatory.

- The `readonly` attribute indicates that the `<input>` cannot be edited.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input]

---

class: inverse center middle

# <i class="fab fa-js"></i> ExpressJS

---

## <i class="fab fa-js"></i> ExpressJS .red[*]

Fast, unopinionated, minimalist web framework for Node.js.

Web frameworks usually come with:
- A **middleware** layer that helps at customizing the behavior of the framework.
- A **router** that helps at defining the HTTP endpoints.
- A **template engine** that helps at rendering webpages.


Multi-page applications (MPA) are decreasing in popularity, but they almost always do the job.
As the Web (as a platform) evolves slowly, MPAs are often cheaper and simpler to maintain. 

.footnote[.red[*] https://expressjs.com/]

---

## <i class="fas fa-hand-paper"></i> Let's play with these concepts .red[*]

```js
const express = require('express')
const app = express()
const port = 3000

// Serve static files
app.use(express.static("public"));

// Define a Middleware
app.use('/form/', (req, res, next) => {
    console.log(req);
    next();
});

// Handle get requests
app.get('/form/', (req, res) => {
    res.send('Hello World!');
});

// Handle post requests
app.post('/form/', (req, res) => {
    res.send('Post saved!')
});

app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```

.footnote[.red[*] https://github.com/tweb-classroom/example-express]
