title: <i class="fas fa-window-maximize"></i> Web Development
subtitle: TWEB
author: Bertil Chapuis
layout: true

<!-- This slide will serve as the base layout for all your slides -->

---

class: inverse center middle

# {{title}}

## {{subtitle}}

<p style="margin-top: 40px">{{author}}</p>

---

## <i class="fas fa-tasks"></i> Overview of Today's Class

- Internet

- World Wide Web (WWW)

- Uniform Resource Locator (URL)

- HyperText Transfer Protocol (HTTP)

- Hypertext Markup Language (HTML) 

- Cascading Style Sheets (CSS)

---

class: inverse center middle

# <i class="fas fa-network-wired"></i> Internet

---


## <i class="fas fa-network-wired"></i> Internet's Conceptual Model .red[*]

The .red[Internet Protocol Suite] is the conceptual model and set of communications protocols used in the Internet and similar computer networks.

- The .red[Application Layer] specifies the shared communications protocols and interface methods used by hosts in a communications network.<br>**Examples:** HTTP, HTTPS, FTP, SSH, SMTP, IMAP, Telnet, etc.

- The .red[Transport Layer] provide host-to-host communication services, such as connection-oriented communication, reliability, and flow control.<br>**Examples:** TCP, UDP, etc.

- The .red[Internet Layer] transports packets from the originating host across network boundaries to the destination host specified by an IP address.<br>**Examples:** IP, ICMP (traceroute), IPsec (VPN), etc.

- The .red[Link Layer] is the group of methods and communications protocols that operate on the link that a host is physically connected to.<br>**Examples:** ARP, PPP, MAC (Ethernet, Wifi, DSL, Fiber), etc.

.footnote[.red[*] https://en.wikipedia.org/wiki/Internet_protocol_suite]

---

##  <i class="fas fa-network-wired"></i> Internet's Conceptual Model

<img alt="Networking" src="images/network_reminder.svg" style="width: 125%;margin-left: -100px" />

---

## <i class="fas fa-network-wired"></i> Domain Name System

The .red[Domain Name System (DNS)] is a hierarchical and decentralized naming system (phone book) for computers connected to the Internet. 
It translates domain names to IP addresses needed for locating and identifying computer.

<img alt="Networking" src="images/network_dns.svg" style="width: 100%;" />

The DNS protocol uses .red[TCP] for Zone transfer and .red[UDP] for name queries.

---

## <i class="fas fa-network-wired"></i> Zone file .red[*]

- A Domain Name System (DNS) zone file is a text file that describes a DNS zone. 

- A DNS zone is a subset, often a single domain, of the hierarchical domain name structure of the DNS. 

- The zone file contains mappings between domain names and IP addresses and other resources, organized in the form of text representations of resource records (RR).

### Example

```md
$ORIGIN example.com.                          ; start of this zone
$TTL 1h                                       ; default expiration time 
example.com.  IN  MX    10 mail.example.com.  ; mailserver for example.com
example.com.  IN  A     192.0.2.1             ; IPv4 address for example.com
example.com.  IN  AAAA  2001:db8:10::1        ; IPv6 address for example.com
www           IN  CNAME example.com.          ; alias for example.com
```
.footnote[.red[*] https://en.wikipedia.org/wiki/Zone_file]


---

## <i class="fas fa-network-wired"></i> More about DNS

Mozilla provides a nice cartoon of how DNS works, what are its limitations in terms of security and privacy, and why DNS over HTTPS is needed.

https://hacks.mozilla.org/2018/05/a-cartoon-intro-to-dns-over-https/

Cloudflare provides a good introduction to DNS and how it is sometimes used to perform DNS amplification attacks and DNS flood attacks.

https://www.cloudflare.com/learning/ddos/glossary/domain-name-system-dns/


---


## <i class="fas fa-hand-paper"></i> Hands on!

Perform some DNS lookups with the following commands:

```bash
nslookup -type=any heig-vd.ch
```

```bash
dig heig-vd.ch
```

Perform a reverse DNS lookup with the host command:

```bash
host wikipedia.org
```

```bash
host 91.198.174.192
```

Query the whois directory to check domain name ownership:

```bash
whois heig-vd.ch
```

Print the route packets trace to network host:

```bash
traceroute heig-vd.ch
```

---

class: inverse center middle

# <i class="fas fa-window-maximize"></i> World Wide Web

---

## <i class="fas fa-window-maximize"></i>  Mozilla's Definition .red[*]

The World Wide Web - commonly referred to as WWW, W3, or the Web - is an interconnected system of public webpages accessible through the Internet. The Web is not the same as the Internet: the Web is one of many applications built on top of the Internet.

The system we know today as "the Web" consists of several components:
- The HTTP protocol governs data transfer between a server and a client.
- To access a Web component, a client supplies a unique universal identifier, called a URL (uniform resource location) or URI (uniform resource identifier).
- HTML (hypertext markup language) is the most common format for publishing web documents.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Glossary/World_Wide_Web]

---

## <i class="fas fa-window-maximize"></i>  Mozilla's Definition .red[*]


Tim Berners-Lee proposed the architecture of what became known as the World Wide Web. He created the first web server, web browser, and webpage at the CERN in 1990. 
In 1991, he announced his creation, marking the moment the Web was first made public. 

.center[
<img src="images/web_tim.jpg" style="width: 50%"/>
]

Today, the Web is constently evolving under the guidance of the World Wide Web Consortium (W3C).

.footnote[.red[*] https://worldwideweb.cern.ch/]
---

## <i class="fas fa-window-maximize"></i> Mozilla's Definition .red[*]

<img alt="The Web" src="images/HTTP_layers.png" style="text-align: center; width: 90%;" />

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview]

---

## <i class="fas fa-window-maximize"></i>  W3C's Standards

<img alt="The Web" src="images/web_standards.png" style="text-align: center; width: 100%;" />

---

## <i class="fas fa-window-maximize"></i>  Mozilla's Web APIs

<img alt="The Web" src="images/web_api.png" style="text-align: center; width: 100%;" />

---

class: inverse center middle

# <i class="fas fa-link"></i> Uniform Resource Locator

---

## <i class="fas fa-link"></i> What's in an URL?

A Uniform Resource Locator (URL), colloquially termed a web address, is a reference to a web resource that specifies its location on a computer network and a mechanism for retrieving it.

```bash
https://username:password@example.com:443/index.html?param=value#fragment
```
| Part        | Value                | Description                                          |
|-------------|----------------------|------------------------------------------------------|
| Scheme      | `https://`           | The protocol to use for the request.                 |
| Credentials | `username:password@` | The credentials to use for the request (Basic Auth). |
| Domain      | `example.com`        | The domain name where to send the request.           |
| Port        | `:443`               | The port of service endpoint.                        |
| Path        | `/index.html`        | The path of the resource.                            |
| Query       | `?param=value`       | The parameters associated with the resource.         |
| Fragment    | `#fragment`          | The path of a secondary resource.                    |

---

class: inverse center middle

# <i class="fas fa-comments"></i> HTTP

---

## <i class="fas fa-comments"></i>  Mozilla's Definition .red[*]

HTTP is a protocol which allows the fetching of resources, such as HTML documents. It is the foundation of any data exchange on the Web and it is a client-server protocol, which means requests are initiated by the recipient, usually the Web browser. A complete document is reconstructed from the different sub-documents fetched, for instance text, layout description, images, videos, scripts, and more.

.center[
<img alt="Fetching a page" src="images/Fetching_a_page.png" width="550" />
]
.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview]



---

## <i class="fas fa-hand-paper"></i> Hands on!

HTTP requests and responses are easy to look at!

Get a try with CURL:

```bash
curl -v http://httpstat.us/200?param=value
```

Or have a look at the DevTools in Chrome (CTRL+SHIFT+I):

<img alt="Fetching a page" src="images/http_devtools.png" width="550" />

---

## <i class="fas fa-user-secret"></i> Hands on!

Maybe too easy to look at...

Credentials and tokens can be captured by eavesdropping:

```bash
tcpdump -vvvs 1024 -l -A host www.heig-vd.ch \
  | strings \
  | grep -i "Authorization: Basic"
```

Now, what happen when you run the following command?

```bash
curl http://username:password@www.heig-vd.ch
```

---

## <i class="fas fa-comments"></i> HTTP Requests

```bash
GET /200?param=value HTTP/1.1
Host: httpstat.us
User-Agent: curl/7.58.0
Accept: */*
```

.red[Requests] usually have:
- a method (`GET`)
- a resource (`/200?param=value`)
- some headers (e.g. `User-Agent: curl/7.58.0`)
- an optional body (depends on the methods)

The most common .red[Methods] are:
- `GET`: Returns the resource.
- `POST`: Create resource.
- `HEAD`: Returns the headers of resource.
- `PUT`: Create or update resource.
- `DELETE`: Deletes resource:

---

## <i class="fas fa-comments"></i> HTTP Responses

```bash
HTTP/1.1 200 OK
Content-Length: 6
Content-Type: text/plain; charset=utf-8
Server: Microsoft-IIS/10.0
Access-Control-Allow-Origin: *
Date: Mon, 16 Sep 2019 20:07:29 GMT
200 OK
```    

.red[Responses] usually have:
- a status code (`200 OK`)
- some headers (e.g. `Content-Length: 6`)
- an optional body (text, HTML, json)

The most common .red[Status Codes] are:
- `200 OK`: The request has succeeded (2xx Success).
- `301 Moved Permanently`: The resource has a new location (3xx Redirection).
- `404 Not Found`: The server has not found the resource (4xx Client Error).
- `500 Internal Server Error`: The server has not found the resource (5xx Server).

---

## <i class="fas fa-hand-paper"></i> Hands on!

Get to know your methods and status codes!

### What is status code `418`?

---

## <i class="fas fa-hand-paper"></i> Hands on!

Get to know your methods and status codes!

### What is status code `418`?

>https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418

>### `418 I'm a teapot`

>The HTTP 418 I'm a teapot client error response code indicates that the server refuses to brew coffee because it is a teapot. This error is a reference to Hyper Text Coffee Pot Control Protocol which was an April Fools' joke in 1998.<br>

---
.center[
<img src="images/http_zine.png" style="width: 50%" />

https://gumroad.com/l/http-zine/buy-one-give-one
]

---

class: inverse center middle

# <i class="fas fa-code"></i> HTML

---

## <i class="fas fa-code"></i> What is HTML? .red[*]

- HTML sands for **Hypertext Markup Language**

- HTML is the most basic **building block** of the Web

- HTML defines the **structure** of web content 

- **Hypertext** refers to **links* that connect web pages to one another

- HTML uses **markup** to annotate text, images, and other content

- HTML5 is called a [living standard](https://html.spec.whatwg.org/) as it is constantly evolving.


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/HTML]




---

## <i class="fas fa-code"></i> Anatomy of an HTML element

<img src="images/html_basic.png" style="width: 55%">

An HTML .red[element]:
- starts with an .red[opening tag]
- may have some .red[content]
- stops with a .red[closing tag]

---

## <i class="fas fa-code"></i> Attributes of an element


<img src="images/html_attribute.png" style="width: 80%">

.red[Attributes] contain extra information about the element which you don't want to appear in the actual content.


- the `id` attribute must contains a unique value accross the document
- the `class` attribute usually refers to a class in a stylesheet
- the `style` attribute usually contains CSS properties

---

## <i class="fas fa-code"></i> Anatomy of an HTML document

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```

- `DOCTYPE` needs to be included for everything to work right (historical)
- `<html>` wraps all the content on the entire page
- `<head>` is container for the stuff that isn't the content
- `<meta charset="utf-8">` sets the character set your document should
- `<title>` sets the title of the web page.
- `<body>` contains all the content that you want to show to web users 
- Elements can be nested

---

## <i class="fas fa-code"></i> Text elements

Headings:

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
```

Paragraph

```html
<p>Paragraph</p>
```

Line break:

```html
<br />
```

Horizontal line:

```html
<hr />
```

---

## <i class="fas fa-code"></i> Semantic elements

Header (introductory content):

```html
<header></header>
```


Main (the dominant content of the body):

```html
<main></main>
```


Footer:

```html
<footer></footer>
```

---

## <i class="fas fa-code"></i> Section elements

Division (content block):

```html
<div></div>
```

Navigation:

```html
<nav></nav>
```

Article (piece of self-contained content):

```html
<article></article>
```

Section (grouping of semantic meaning):

```html
<section></section>
```

Aside (content that does not belong to the main content):

```html
<aside></aside>
```

---

## <i class="fas fa-code"></i> Hyperlink element

```html
<a href="https://www.heig-vd.ch" title="Heig-vd" target="_blank">Heig-vd</a>
```

```html
<a href="mailto:username@email.com?subject=hello&body=world!">Hello World!</a>
```

The hyperlink element must contain an `href` attribute and can specify a `title` and a `target`.
The content of the hyperlink can be an image.

## <i class="fas fa-code"></i> Image element

```html
<img src="image.jpg" alt="caption" />
```

The image element must have an `src` (image url) and `alt` (caption of the image) attribute.

## <i class="fas fa-code"></i> Audio element

```html
<audio src="audio.mp3"></audio>
```

---

## <i class="fas fa-code"></i> Canvas element

```html
<canvas></canvas>
```

The HTML canvas allows for dynamic, scriptable rendering of 2D and 3D shapes.

## <i class="fas fa-code"></i> Nested lists

Numbered lists and enumerations can be nested.

```html
<ol>
  <li>A</li>
  <li>B 
    <ul>
      <li>C</li>
      <li>D</li>
      <li>E</li>
    </ul>
  </li>
  <li>F</li>
</ol>
```

---

## <i class="fas fa-code"></i> Tables

Tables should only be used for tabular data.

```html
<table>
  <tr><!-- row -->
    <th>Student ID</th> <!-- header column -->
    <th>Grade</th>
  </tr>
  <tr>
    <td>4</td> <!-- column -->
    <td>5</td>
  </tr>
  <tr>
    <td>6</td>
    <td>7</td>
  </tr>
</table>
```

The `colspan` and `rowspan` attributes can be used to merge cells.

---

## <i class="fas fa-code"></i> Why using meta tags?

Meta tags are a great way for webmasters to provide search engines with information about their sites.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="Description" content="Great description" />
```

https://support.google.com/webmasters/answer/79812?hl=en

---

## <i class="fas fa-code"></i> HTML Entities

An HTML entity is a piece of text ("string") that begins with an ampersand (&) and ends with a semicolon (;) . Entities are frequently used to display reserved characters.

| Character | Entity   | Note                                                              |
|-----------|----------|-------------------------------------------------------------------|
| &         | `&amp;`  | Interpreted as the beginning of an entity or character reference. |
| <         | `&lt;`   | Interpreted as the beginning of a tag                             |
| >         | `&gt;`   | Interpreted as the ending of a tag                                |
| "         | `&quot;` | Interpreted as the beginning and end of an attribute's value.     |

https://developer.mozilla.org/en-US/docs/Glossary/Entity

---

##  <i class="fas fa-sitemap"></i> What is the DOM? .red[*]

- DOM stands for **Document Object Model**

- The DOM is a programming interface for HTML and XML

- The DOM represents the structure of a document in memory

- It lets other programming languages manipulating the document


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model]


---

##  <i class="fas fa-sitemap"></i> The DOM's content tree .red[*]

```html
<html>
<head>
  <title>My Document</title>
</head>
<body>
  <h1>Header</h1>
  <p>Paragraph</p>
</body>
</html>
```

When a browser such as Chrome or Firefox parses an HTML document, it builds a **content tree** and then uses it to **display** the document.

<img src="images/html_content_tree.jpg" />

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_W3C_DOM_Level_1_Core]

---

class: inverse center middle

# <i class="fas fa-paint-brush"></i> CSS

---

## <i class="fas fa-paint-brush"></i> What is CSS? .red[*]

- CSS stands for **Cascading Style Sheets**

- CSS is a core language of the **open Web**

- CSS is a **stylesheet language** for HTML or XML documents <br>(including XML dialects such as SVG, MathML or XHTML)

- CSS describes how **elements** should be **rendered** on a media <br>
  (a media can be a screen, a paper, etc.)

- CSS is **standardized** across Web browsers <br> according to the [W3C specification](https://www.w3.org/Style/CSS/#specs)

- CSS3 is the latest version of the standard.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS]


---

## <i class="fas fa-paint-brush"></i> CSS declaration .red[*]

<img src="images/css_declaration.png" />

- Setting **CSS properties** is the core function of the CSS language

- A **property** and **value** pair is called a **declaration**

- **Properties** and **values** are case-insensitive

- The pair is separated by a colon `:`

- There are more than [100 different properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) in CSS 

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax]

---

## <i class="fas fa-paint-brush"></i> CSS declarations block .red[*]

<img src="images/css_declarations_block.png" />

- CSS declarations are grouped in **blocks**

- CSS declarations are **separated** by a **semi-colon** (`;`) 

- Blocks are **delimited** by an opening (`{`) and a closing **brace** (`}`)

- Sometimes blocks can be **nested** (e.g., media queries)

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax]

---

## <i class="fas fa-paint-brush"></i> CSS Rulesets .red[*]

<img src="images/css_rulesets.png" />

- **Rulesets** apply declarations to **specific** parts of the document

- **Declaration blocks** are preceded by one or more comma-separated **selectors**

- **Selectors** are conditions selecting some elements of the page

- **Cascading** refers to the precedence of the **selectors** over each others

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax]

---

## <i class="fas fa-paint-brush"></i> Adding Stylesheet to an HTML Document

Stylesheets can be **embed** in the HTML document:

```html
!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        background-color: linen;
      }
    </style>
  </head>
  <body></body>
</html>
```

Stylesheets are usualy stored in **external** files:

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  <body></body>
</html>
```

---

## <i class="fas fa-paint-brush"></i> How does CSS work?.red[*]

When a browser displays a document, it must combine the document's content with its style information.

<img src="images/html_dom.svg" />

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_works]


---

## <i class="fas fa-paint-brush"></i> CSS Selectors .red[*]

The **type selector** selects the elements that match the given node name:

```css
p {}
```

The **id selector** selects the elements that have a given id attribute:

```css
#myid {}
```

The **class selector** selects the elements that have a given class attribute:

```css
.myclass {}
```

The **universal selector** select all the elements:

```css
** {}
```

The **attribute selector** select the elements with a given attribute:

```css
[attr=value] {}
```

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors]

---

## <i class="fas fa-paint-brush"></i> CSS Combinators .red[*]

**CSS Combinators** can be used to mix several selectors.

The ` ` (space) combinator selects nodes that are descendants of the first element.
 
```css
ul li {}
```

The `>` combinator selects nodes that are direct children of the first element.

```css
ul > li {}
```

Other combinators, such as `+`, `~`, respectively applies to **adjacent** and **sibling** elements in the DOM.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors]


---

## <i class="fas fa-paint-brush"></i> CSS Pseudo-class .red[*]

A **pseudo-class** is a keyword added to a selector that specifies a special state of the selected element(s). 

The `:hover`, `:link`, `:visited` and `:active` pseudo-class matches when the user interacts with an element with a pointing device. 

```css
a:hover {background-color: red; }
```

The :nth-child() CSS pseudo-class matches elements based on their position in a group.

```css
td:nth-child(2n) { background-color: gray; }
```

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes]

---

## <i class="fas fa-paint-brush"></i> More Pseudo-classes

.center[
<img src="images/css_pseudoclass.png" style="width:100%">
]

---

## <i class="fas fa-hand-paper"></i> Hands on!

Experiment with the **DOM** and with **selectors** in Boris's [CSS Visualizer](https://fritscher.ch/dom-css/).

https://fritscher.ch/dom-css/


```css
#abc
.abc
h1#abc
h1
h1[class=abc]
body > h1
ul li
ul li:nth-child(2)
```

---

## <i class="fas fa-paint-brush"></i> Color Property .red[*]

The color property sets the foreground color value of an element's text.

```css
p {
  /* named-color values */
  color: red;
  color: orange;

  /* hex-color values */
  color: #090;
  color: #009900;

  /* rgb() values */
  color: rgb(34, 12, 64, 0.6);
  color: rgba(34, 12, 64, 0.6);
}
```

**Color values** can be used with other CSS properties such as:

```css
background-color: #090;
border-color: #090;
```

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/color]

---

## <i class="fas fa-paint-brush"></i> Font Properties .red[*]


```css
p {
  font-family: Times New Roman, serif, Arial, sans-serif, Consolas, monospace;
  font-style: italic;
  font-weight: bold;
  font-size: 1.5em;
}
```
The font property sets an element's font to a system font.

- The first font specified that is available is used to display the element.
- The recommended font size units are `px`, `em` and `%`. Pixels are fixed, wheareas `em` and `%` are relative to the font size specified for the document.  

Additional fonts can be imported in a stylesheet with the import directive.

```css
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');

body{
  font-family: 'Roboto', sans-serif;
}
```

[fonts.google.com](https://fonts.google.com) and [fonts.com](https://fonts.com) provide public registries for fonts.


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/font]

---

## <i class="fas fa-paint-brush"></i> Text Properties .red[*]

```css
p {
  text-align: center;
  line-height: 2em;
  letter-spacing: 2em;
  text-decoration: underline;
  text-transform: uppercase;
}
```

Many CSS properties can be used to to perform text manipulation, like line breaking, justification and alignment, white space handling, and text transformation.


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Text]


---

## <i class="fas fa-paint-brush"></i> Background Properties .red[*]

```css
body {
  background-color: blue;
  background-image: url('../image.jpg');
  background-repeat: no-repeat;
  background-size: auto;
}
```

Many CSS properties applies to the background of an HTML element.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/background]

---

## <i class="fas fa-paint-brush"></i> Box Model .red[*]

```css
div {
  display: block;
  margin: 20px 10px 20px 15px;
  padding: 10px;
  border: solid 1px red;
  border-radius: 20px;
  width: 200px;
  height: 100px;
}
```

The browser's rendering engine represents each element as a rectangular box according to the standard CSS basic box model.

<img src="images/css_box_model.png" style="width: 40%">





.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model]

---

## <i class="fas fa-paint-brush"></i> Positionning .red[*]

```html
<div id="el">My element</div>
```

```css
#el {
  position: fixed
  top: 100px;
  left: 100px;
  bottom: 100px;
  right: 100px;
}
```

The position CSS property sets how an element is positioned in a document.

- `static`: The element is positioned according to the normal flow of the document.
- `relative`: The element is positioned according to the normal flow of the document, and then offset relative to itself.
- `fixed`: The element is positioned relative to its closest positioned ancestor.
- `absolute`: The element is positioned relative to the initial containing block established by the viewport.


.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/position]

---

## <i class="fas fa-paint-brush"></i> CSS Flexbox .red[*]

The flexbox model addresses the limits of the layout system (grid) in CSS.


```html
<div class="container">
  <div class="item">Item A</div>
  <div class="item">Item B</div>
  <div class="item">Item C</div>
</div>
```

```css
.container {
  display: flex;
  flex-direction: row;
}
.item {
  order: 1;
  flex-grow: 1
}
```


[CSS tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/
) provides a very good tutorial on Flexbox.

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox]

---

#  <i class="fas fa-paint-brush"></i> CSS Media Queries .red[*]

Media queries are useful when you want to modify your site or app depending on a device's general type (such as print vs. screen) or specific characteristics and parameters (such as screen resolution or browser viewport width).

```
@media only screen and (min-width : 600px) {
  body {
    color: red
  }
}
```

.footnote[.red[*] https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries]

---

class: inverse center middle

# <i class="fas fa-tasks"></i> Summary

---

## <i class="fas fa-tasks"></i> Summary of Today's Class

- Internet

- World Wide Web (WWW)

- Uniform Resource Locator (URL)

- HyperText Transfer Protocol (HTTP)

- Hypertext Markup Language (HTML) 

- Cascading Style Sheets (CSS)

---

class: inverse center middle

# <i class="fas fa-tasks"></i> Group Assignment

---

## <i class="fas fa-tasks"></i> Group Assignment

https://classroom.github.com/classrooms/54867215-tweb-classroom
