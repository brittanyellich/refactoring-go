---
# You can also start simply with 'default'
theme: apple-basic
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Refactor, don't rewrite.
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true

# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
Getting started.
-->

---
transition: slide-left
layout: image-right
image: 'images/1.png'
---

<!--
This is your legacy system.
-->

---
transition: slide-left
layout: image-right
image: 'images/2.png'
---

<!--
Okay maybe this is more realistic. It's a bit hairy. It has bandaids. It has code smells.
-->

---
transition: slide-left
layout: image-right
image: 'images/3.png'
---

<!--
Eventually, a feature comes along.
-->

---
transition: slide-left
layout: image-right
image: 'images/4.png'
---

<!--
You have to integrate it with your system, but you've hit a wall. There's been enough complaints. 
-->

---
transition: slide-left
layout: image-right
image: 'images/4.png'
---

Does this sound familiar?

<!--
Raise hands?
-->

---
transition: slide-left
layout: center
---

You're wrong.

<!--
I'm going to tell you why that's wrong in three points.
-->

---
transition: slide-left
layout: center
---

You're wrong.
(probably. it depends.)

<!--
I'm going to tell you why that's wrong in three points.
-->

---
transition: slide-left
layout: intro
---

# Refactor, don't rewrite.
## Brittany Ellich

[brittanyellich.com](https://brittanyellich.com)

<!--
I'm going to tell you why that's wrong in three points.

Everyone that I have been on a team with probably think this is about them. And the answer is "yes". 
-->

---
transition: slide-left
layout: image-right
image: 'images/5.png'
---

# 1. It will just be faster to rewrite it

<!--
When you plan your app, you're thinking about the feature and some of the scope of the rewrite, but humans are really bad at considering the entirety of a system.
-->

---
transition: slide-left
layout: image-right
image: 'images/6.png'
---

# 1. It will just be faster to rewrite it

<!--
You're thinking of only about 20% of the entire app. 

There's the other 80% that will take the rest of the time.
-->

---
transition: slide-left
layout: image-right
image: 'images/7.png'
---

# 1. It will just be faster to rewrite it

<!--
Not only that, there's the other app you have to maintain and support during that same time.
-->

---
transition: slide-left
layout: image-right
image: 'images/7.png'
---

# 1. It will just be faster to rewrite it

No, it won't be.

---
transition: slide-left
---

# 2. We will move faster with clean code.

---
transition: slide-left
layout: quote
---

# You're overvaluing clean code.

<!--
Have you ever seen any quantifiable argument that clean code helps you move faster? 

Nope.

And even then, those bandaids? those were important. Those are also called bugfixes.
-->

---
transition: slide-left
---

# 3. We will do better with X technology

<!--
A lot of times these efforts come with an excuse for the team to learn a new technology. But that learning is going to be an undertaking on its own. Not only that, refactoring a legacy codebase is arguably much more technically interesting. A lot of companies have "promotion" projects that result in these rewrites, but I argue it's more impactful to modernize a legacy codebase in less time and a technology the team is already familiar with than to rewrite a brand new one.
-->

---
transition: slide-left
---

# 3. We will do better with X technology

You won't.

---
layout: center
class: text-center
---

# Refactor, don't rewrite.

You probably don't need a rewrite.
It will probably take too long.
Clean code isn't that important.
You won't suddenly work better in a new technology.


---
layout: center
class: text-center
---

# Thank you!

My website is [brittanyellich.com](https://brittanyellich.com), let's be internet friends!



