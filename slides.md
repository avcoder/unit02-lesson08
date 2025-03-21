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

# Recap
(30 min) 

- Assignment 2 is due Apr. 13
- Challenge: Create recipe finder app

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
- Note: frontend JS mostly modifies JSON data to be suitable for browser!
-->

---
transition: slide-left
---

# AJAX
(30 min) What is AJAX and its importance in web dev

- Google Maps as an example of using AJAX
- Before fetch was invented, demo:
   - XMLHttpRequest
   - jQuery's `.get()` etc
   - libraries like: Axios
   - terminal command: `curl`
- Challenge: use [Deck of Cards API](https://deckofcardsapi.com/) to setup a board and draw cards

<!--
-->

---
transition: slide-left
---

# Fetch API
(50 min) 

- basic usage of fetch (GET and POST)
- Demo: create node server to examine request, send response; Use network tab to examine response in browser
- use Postman to send POST request
- Challenge: Use [Cat API](https://thecatapi.com/) to send a POST request via fetch

<!--
-->

---
layout: image-right
transition: slide-left
image: /assets/scott.png
backgroundSize: 500px 160px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- 🔋 [placeholder](htt)

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

- Examine web request and response structure
- Demo: to handle network request errors
- Challenge: use Netlify's serverless function to create Live Poll chart

<!--
-->

---
transition: slide-left
---

# Exercise
(remainder of time)

- Use this [Joke API](https://official-joke-api.appspot.com/random_joke) to display the question, then upon clicking a button, displays the punchline
- Stretch goal: Create a new button that fetches a new joke; Accumulate jokes in an unordered list below current joke

---
transition: slide-left
---

# Homework

- Work on Assignment 2 due Apr. 13
- Need API ideas?  Use chatgpt:
<img src="/assets/chatgpt.png" alt="chatgpt">