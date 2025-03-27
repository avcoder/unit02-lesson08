---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# JavaScript - part 8/8
JavaScript Foundations
- [ ] AJAX
- [ ] Fetch API

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
TODO: fill in anchor href above to point to github repo for these slides
-->

---
transition: slide-left
---

# Other Tidbits
(5 min) 

- Assignment 2 is due Apr. 13
- query params, forms, `new URL()`
- Destructuring objects, arrays
- Closures
- Local Storage
- getter/setter
- `class`, `new`

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
- Show A#2 in LMS
-->

---
transition: slide-left
---

# Query Params
(5 min) How does client/browser send data to server?

- query params, `new URL()`

<img src="/assets/jake.png">

- form method is default to `GET` unless set to `POST`
   - view Network tab's Payload
- Challenge: create JS router that looks at url, if query param where `k=hello` shows 'World', but if `k=bye` show 'Earth'

<!--
- const currentUrl = new URL(window.location.href);
- const kValue = currentUrl.searchParams.get("k");

- function render(msg) { document.body.innerHTML = msg }

- if (kValue === "hello") { render("World") }
- else if (kValue === "bye") { render("Earth") }
- else { render("Wut?") }
-->

---
transition: slide-left
---

# Closures
(5 min) 

- Closures

```js
function factory() {
  let a = 0;
  return function render() {
    console.log(a);
    a += 1;
  };
}

const fn = factory();
fn();
```

<!--
-->

---
transition: slide-left
---

# Destructuring Arrays
(5 min) 

- Destructuring [arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring)

```js
// array destructuring
const [a, b] = [10, 20];
const [a, b, ...c] ['a', 'b', 'c', 'd', 'e']

// can swap in only 1 line!
let a = 2;
let b = 3;
[b, a] = [a, b]
```

- Challenge: Create a function called `useState()` that takes in an argument.  That argument will serve as the initial value for a variable
The function returns an array of 2 elements: 
   - The first element returns the value of the variable
   - The second element returns another function that takes in an argument, where if it's called, sets the variable
   - Test: `const [age, setAge] = useState(0)`

<!--
- let value
- function useState(v = value) { 
- value = v;
- function setAge(x) { value = x }
- return [value, setAge] }
- const [age, setAge] = useState(0);
-->

---
transition: slide-left
---

# Destructuring Objects
(5 min) 

- Destructuring [objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring#object_destructuring)

```js
// object destructuring
const user = {
    name: 'al',
    age: 20,
    isFaculty: true,
    grade: () => console.log('hi')
}

const { age, grade: mark } = user;
```
- Challenge: Within a function parameter, destructure `age` and `name` if called with `getData({ name: "al", age: 23, is_: true })`

<!--
- function getData({ age, name }) { console.log(age, name) }
- getData({ name: "al", age: 23, is_: true });
-->

---
transition: slide-left
---

# Local Storage
(5 min) 

- [Local Storage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

```js
localStorage.setItem("age", 20);
localStorage.setItem("name": "al");

localStorage.getItem('age')
localStorage.removeItem('age')
localStorage.clear();
```

- View DevTools > Application > Local Storage

<!--
-->

---
transition: slide-left
---

# getter/setter
(5 min) [MDN get](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get), [MDN set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set)

- Challenge: Create a setter such that everytime an array of objects is set (within an object), it calls the render function to display list on page automatically
```js
const user = {
  name: "al",
  pets: ["a", "b"],
  render: function () {
    console.log(this);
    main.innerHTML = this.pets.map((p) => `<li>${p}</li>`).join("");
  },
  get msg() {
    console.log("can do more stuff here");
    return `${this.name} has ${this.pets}`;
  },
  set animals(animalList) {
    this.pets = animalList;
    this.render();
  },
};
```

<!--
-->

---
transition: slide-left
---

# AJAX
(5 min) What is AJAX and its importance in web dev

- Google Maps as an example of using AJAX
- Before fetch was invented, demo:
   - XMLHttpRequest
   - jQuery's `.get()` etc
   - libraries like: Axios
   - terminal command: `curl`
- Challenge: use [Deck of Cards API](https://deckofcardsapi.com/) to setup a board and draw cards
   - Stretch goal: use localStorage such that if you refresh the browser, you still have the same cards drawn

<!--
-->

---
transition: slide-left
---

# XMLHttpRequest
(1 min) 

```js
// Create a new XMLHttpRequest object
var xhr = new XMLHttpRequest();

// Configure the request (GET method, URL)
xhr.open("GET", "https://official-joke-api.appspot.com/random_joke", true);

// Set up a function to handle the response
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 200) {
    // Parse the JSON response
    var response = JSON.parse(xhr.responseText);
    console.log(response);
  }
};

// Send the request
xhr.send();
```

<!--
-->

---
transition: slide-left
---

# jQuery's `$.ajax()`
(1 min) 

```js
// Use jQuery to make an AJAX GET request
$.ajax({
    url: 'https://official-joke-api.appspot.com/random_joke',  // API URL
    method: 'GET',  // HTTP method
    success: function(response) {
        // Handle the response (JSON data)
        console.log(response);
    },
    error: function(xhr, status, error) {
        // Handle errors
        console.error('Error:', error);
    }
});

```

<!--
-->

---
transition: slide-left
---

# Axios
(1 min) 

```js
// Use Axios to make a GET request
axios.get('https://official-joke-api.appspot.com/random_joke')
    .then(function (response) {
        // Handle the response (JSON data)
        console.log(response.data);
    })
    .catch(function (error) {
        // Handle errors
        console.error('Error:', error);
    });
```

<!--
-->

---
transition: slide-left
---

# `curl`
(1 min) Terminal command `curl`

```
// Use Axios to make a GET request
curl https://official-joke-api.appspot.com/random_joke | jq
```

<!--
-->

---
transition: slide-left
---

# Fetch API
(20 min) 

- basic usage of fetch (GET and POST)
- use Postman to send POST request
- Challenge: Use [JSON Placeholder](https://jsonplaceholder.typicode.com/guide/) to make a POST request
```js
const res = await fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  body: JSON.stringify({
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
});
const data = await res.json();
console.log(data);
```

<!--
-->

---
layout: image-right
transition: slide-left
image: /assets/lydia.png
backgroundSize: 500px 420px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- ▶️ [Chrome for Devs Channel](https://www.youtube.com/@ChromeDevs/videos)
- 💯 [JS Quiz by Lydia Hallie](https://javascript-questions.vercel.app/)
- 😎 [Promises Async/Await Visualized](https://dev.to/lydiahallie/javascript-visualized-promises-async-await-5gke)
- 😸 [The Cat API](https://thecatapi.com/)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

<!-- 
- take attendance
-->

---
transition: slide-left
---

# Working with Responses and Error Handling
(40 mins)  Extract JSON data from response

- How do you extract JSON from a web response?
- What does res.json() do?
- Demo: create node server to examine request, send response; Use network tab to examine response in browser
- Challenge: use [Netlify's serverless](https://www.netlify.com/blog/intro-to-serverless-functions/) function to create Live Poll chart that is publicly accessible

<!--
-->

---
transition: slide-left
---

# Homework

- Work on Assignment 2 due Apr. 13
- Need API ideas?  Use chatgpt:
<img src="/assets/chatgpt.png" alt="chatgpt">
- Next week we have a lab Wed. 6:30pm
   - 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)