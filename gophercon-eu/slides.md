---
# You can also start simply with 'default'
theme: apple-basic
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Refactoring Go - Patterns and Practices for Maintaining and Evolving Large Codebases
info: |
  More info at https://github.com/brittanyellich/refactoring-go
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
layout: intro

# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# Refactoring Go

Patterns and Practices for Maintaining and Evolving Large Codebases




<div class="absolute bottom-10">
  <span class="font-700">
    Brittany Ellich | <a href="https://brittanyellich.com" target="_blank">brittanyellich.com</a>
  </span>
</div>

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/brittanyellich/refactoring-go" target="_blank" class="slidev-icon-btn">
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
This is your system.
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
Eventually, a feature comes along. Your PM wants something new which requires a significant shift in your application.
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

"It would be faster to just rewrite the whole thing"

<p v-click>Does this sound familiar?</p>

<!--
Someone on your team suggests a full rewrite.

Raise hands?
-->

---
transition: slide-left
layout: statement
---

You're wrong.
<p v-click>(probably)</p>

<!--
Pause.

I'm going to tell you why that's wrong in three points.
-->

---
transition: slide-left
layout: intro
---

# Refactoring Go

Patterns and Practices for Maintaining and Evolving Large Codebases

## Brittany Ellich

[brittanyellich.com](https://brittanyellich.com)

<!--
Welcome to my talk: Refactoring Go - Patterns and Practices for Maintaining and Evolving Large Codebases

Hello my name is Brittany Ellich - Software engineer, speaker, and educator helping developers build better software, stronger careers, and a more inclusive tech industry.

-->


---
transition: slide-left
---

# What we're going to talk about

- Refactor, don't rebuild (the top 3 arguments and why they're wrong)
- How to refactor (some principles and a few examples)
- How to prioritize your refactoring efforts
- Getting AI to help you

<!--
Here's what we're going to talk about today
-->

---
layout: section
---

# Refactor, don't rebuild

The top 3 arguments and why they're wrong

---
transition: slide-left
layout: image-right
image: 'images/5.png'
---

# 1. It will be faster to just rewrite it

<!--
When you plan your app, you're thinking about the feature and some of the scope of the rewrite, but as anyone who has ever guessed a story point can tell you, humans are really bad at estimating, and this is estimating on a huge scale.
-->

---
transition: slide-left
layout: image-right
image: 'images/6.png'
---

# 1. It will be faster to just rewrite it

<!--
You're thinking of only about 20% of the entire app. 

There's the other 80% that will take the rest of the time, just to get to parity with your existing application.
-->

---
transition: slide-left
layout: image-right
image: 'images/7.png'
---

# 1. It will be faster to just rewrite it

<!--
Not only that, there's the other app you have to maintain and support during that same time.
-->

---
transition: slide-left
layout: image-right
image: 'images/8.png'
---

# 1. It will be faster to just rewrite it

<p v-click>No, it won't be.</p>

<!--
And, oh yeah, you have to move all that data over and decommission the old app
-->


---
transition: slide-left
---

# 2. We will move faster with clean code.

<ul v-click>
    <li>"If we start over, we can do it right this time"</li>
    <li>"We'll avoid all the mistakes from the legacy system"</li>
    <li>"The new code will be so much cleaner and more maintainable"</li>
</ul>



---
transition: slide-left
---

# 2. We will move faster with clean code.

Production applications will never be clean, and they don't need to be.

<!--
Messiness reflects the real-world complexity. Your "ugly" edge cases represent actual business requirements.
The workarounds encode institutional knowledge. That weird conditional isn't poor coding - it's handling a critical customer scenario someone discovered at 2 AM during an outage.
Accumulated complexity serves users: Every seemingly unnecessary feature exists because someone, somewhere, depends on it.
-->

---
transition: slide-left
---

# 3. The current technology stack is holding us back.

<ul v-click>
    <li>"If we rebuild in X, we will solve all our performance problems"</li>
    <li>"We're spending too much time fighting against outdated tools"</li>
    <li>"New developers can't be productive in this legacy stack"</li>
</ul>

<!--
A lot of times these efforts come with an excuse for the team to learn a new technology. But that learning is going to be an undertaking on its own. 

Not only that, refactoring a legacy codebase is arguably much more technically interesting. 

A lot of companies have "promotion" projects that result in these rewrites, but I argue it's more impactful to modernize a legacy codebase in less time and a technology the team is already familiar with than to rewrite a brand new one.
-->

---
transition: slide-left
---

# 3. The current technology stack is holding us back.

It isn't.

<!--

Good software design principles can be applied to any tech stack.

An aside, if it isn't already in Go, rewrite in Go :) Not only because we are at a Go conference, but if you're in the business of building long-term software (which you probably are) the compatibility guarantee is priceless. If you want to write once and run forever, Go is the language to use.

-->

---
layout: center
class: text-center
---

# Refactor, don't rebuild.

<p v-click><bold>Preserve institutional knowledge</bold>: embedded in existing code</p>
<p v-click><bold>Incremental risk management</bold>: small changes, quick feedback</p>
<p v-click><bold>Continuous value delivery</bold>: users see improvements immediately</p>
<p v-click><bold>Learn as you go</bold>: discover requirements through existing behavior</p>
<p v-click>The best software products emerge from continuous improvement, not perfect planning.</p>

<!--
There are some cases where a rebuild makes sense. But if you can't clearly articulate why a rebuild is necessary, refactor instead.
You probably don't need a rewrite.
It will probably take too long.
Your production application will not be the perfect, bug-free, clean-code space you think it will be.
You won't suddenly work better by adopting a new technology.
Agile > Waterfall
-->

---
layout: section
---

# How to refactor

Some principles and a few examples

---
layout: default
---

# The Refactoring Mindset

<ul>
<li v-click><bold>Start with tests</bold>: A safety net before changing anything</li>
<li v-click><bold>Make your error handling consistent</bold>: This affects the rest of your application's structure</li>
<li v-click><bold>Focus on interfaces</bold>: These define your system's boundaries</li>
</ul>

<!--
Start with tests: Add characterization tests to capture current behavior, then refactor with confidence

- Small steps win
- Preserve knowledge - encapsulate "messy" code in tests and sequester in functions
- Continuous improvement - Do this alongside feature work, don't wait for refactoring sprints
-->

---
layout: section
---

# Go Code Smells

<ol>
    <li>1. Error handling </li>
    <li>2. Fat interfaces</li>
    <li>3. Tightly coupled models</li>
    <li>4. Empty interface overuse</li>
    <li>5. Excessive parameter</li>
</ol>

---
transition: slide-left
---

# Inconsistent error handling

**The Problem**: Lost context, double handling, silent failures

```go
// Bad: No context, inconsistent patterns
return errors.New("invalid amount")

// Good: Clear context and consistent wrapping
return fmt.Errorf("process payment: invalid amount %.2f", amount)
```

**Go Proverb**: "Errors are values" - program with them, don't just check them

<!--
Reading: "100 Go Mistakes" #49-52 on error handling patterns
-->

---
transition: slide-left
---

# Large interfaces

**The Problem**: Large interfaces force clients to depend on methods they don't use

```go
// Bad: Clients depend on methods they don't use
type UserService interface {
    CreateUser(u User) error
    SendEmail(to string) error
    GenerateReport() []byte
}

// Good: Focused, testable interfaces
type UserManager interface {
    CreateUser(u User) error
}
type NotificationService interface {
    SendEmail(to, subject, body string) error
}
type ReportService interface {
    GenerateReport() []byte
}
```

**Go Proverb**: "The bigger the interface, the weaker the abstraction"

<!--
Reading: Go Proverbs talk, "100 Go Mistakes" #5-7 on interface design
-->

---
transition: slide-left
---

# Tightly coupled models mixing concerns

**The Problem**: Single structs mixing API responses, database, and validation concerns

```go
// Bad: Mixed concerns
type User struct {
    ID       int    `json:"id" db:"user_id" validate:"required"`
    Name     string `json:"name" db:"full_name" validate:"min=2,max=50"`
    Email    string `json:"email" db:"email_addr" validate:"email"`
    Password string `json:"-" db:"password_hash"`
}

// Good: Separated concerns
type User struct {        // Domain model
    ID    int
    Name  string
    Email string
}
type UserAPI struct {     // API representation
    ID    int    `json:"id"`
    Name  string `json:"name"`
    Email string `json:"email"`
}
type UserDB struct {      // Database model
    ID       int    `db:"user_id"`
    Name     string `db:"full_name"`
    Email    string `db:"email_addr"`
    Password string `db:"password_hash"`
}
```

<!--
Mixed concerns make evolution painful. Changing JSON structure shouldn't require database migration
Reading: Clean Architecture principles, Domain-Driven Design
-->

---
transition: slide-left
---

# Overuse of empty interface{} weakening type safety

**The Problem**: Using any/interface{} when specific types would be better

```go
// Bad: Runtime type checking required
func Process(data interface{}) error

// Good: Specific interfaces or generics
func Process[T Processor](data T) error
```

**Go Proverb**: "The empty interface says nothing"

<!--
Catches errors at compile time instead of runtime
Reading: "100 Go Mistakes" #8 on any usage
-->

---
transition: slide-left
---

# Excessive parameter lists reducing readability

**The Problem**: Functions become unreadable and error-prone

```go
// Bad: Too many parameters
func ProcessOrder(customerID string, items []string, quantities []int, 
                 prices []float64, discountRate float64, shippingMethod string,
                 taxRate float64) error

// Good: Meaningful structs
type OrderRequest struct {
    CustomerID string
    Items      []OrderItem
    Shipping   ShippingInfo
    Pricing    PricingRules
}
func ProcessOrder(req OrderRequest) error
```

<!--
Go doesn't have named parameters, making long parameter lists especially problematic
Reading: "100 Go Mistakes" #11 on functional options pattern
-->

---
layout: section
---

# How to prioritize your refactoring efforts

---
transition: slide-left
layout: image-right
image: 'images/9.png'
---

# A prioritization framework

<!--
Categorize each item by the amount of effort and amount of impact
-->

---
transition: slide-left
layout: image-right
image: 'images/10.png'
---

# A prioritization framework

<!--
It roughly looks like this!
-->

---
transition: slide-left
layout: image-right
image: 'images/11.png'
---

# A prioritization framework

The Three-Bucket Approach

- High Impact, Low Effort: Start here

<!--
It roughly looks like this!
-->

---
transition: slide-left
layout: image-right
image: 'images/12.png'
---

# A prioritization framework

The Three-Bucket Approach

- High Impact, Low Effort: Start here
- High Impact, High Effort: Plan next

<!--
It roughly looks like this!
-->

---
transition: slide-left
layout: image-right
image: 'images/13.png'
---

# A prioritization framework

The Three-Bucket Approach

- High Impact, Low Effort: Start here
- High Impact, High Effort: Plan next
- Low Impact, Any Effort: Ignore this

<!--
It roughly looks like this!
-->

---
layout: section
---

# How to get AI to help you

Would this be a talk in 2025 if I didn't mention AI?

---
layout: image-right
image: 'codingagent.jpg'
---

# Coding agent use cases

<ul>
    <li v-click>Increasing test coverage</li>
    <li v-click>Searching your codebase to find inconsistent approaches</li>
    <li v-click>Taking patterns and applying them across your codebase incrementally</li>
</ul>

<!--
An aside: I'm not here to sell you all on Copilot. That's not my job. But this is the tool I've used the most.
These are all great use cases because I know that they work
There are ways to make this work better (ask me about them/read my blog post about it!)
-->

---
layout: section
---

# Recap

- Refactor, don't rebuild
- How to refactor: First tests, then error handling, then interfaces
- How to prioritize: First high impact, low effort; then high impact, high effort
- Get AI to help you (this is a great use case for AI)

---
layout: center
class: text-center
---

# Thank you!

My website is [brittanyellich.com](https://brittanyellich.com), let's be internet friends!
