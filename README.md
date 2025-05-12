# 🧩 Wide Language

Welcome to **Intent-Oriented Programming** – Where code expresses *what you mean*, not *how you fight the compiler*.

Wide is a symbol-based, declarative, paradigm-unifying programming language designed to feel natural, composable, and deeply readable.

It doesn't have keywords (at least not for aliased types).

It doesn't waste your time.

It lets **humans speak logic** – cleanly, expressively, and across paradigms.

Wide isn’t just about code - it's about communication.

It's about intent — and Wide delivers it.

## Introduction

Wide is a keyword-less, intent-driven programming language inspired by years of experience across many real-world languages. Its design takes direct cues from:

- Python — for its clean syntax and readability-first philosophy
- Go — for its simplicity and strong opinions on structure
- Rust — for its safety, scope-aware semantics, and move-inspired modeling
- TypeScript — for its balance between strong typing and developer ergonomics
- PHP — for its pragmatic web-oriented roots and fluid development style
- OCaml — for its functional purity, immutability-first mindset, and algebraic type inspiration
- C++ — for its deep control over memory, compile-time power, and fine-grained expression of intent

Wide doesn't try to copy them — it extracts the intent behind them, strips away the noise, and rebuilds a language model based purely on semantic clarity, symbolic consistency, and developer expression.

I’ve spent 25 years programming in languages like Python, Go, Rust, TypeScript, PHP, and OCaml. Wide is what happened when I asked myself:

“What if none of them had keywords?”

And then... made it actually work.

### Why Wide?

- No keywords — only symbols that express intent
- Immutable by default, reactive when needed (`$`, `@`)
- Real functions and lambdas with context inclusion
- Strong types, simple syntax
- Built-in support for UI, iteration, async, and error control

## Opinions and Criticism

This document is designed to grab Opinions and Criticism about Wide.

Be aware the the syntax presented here is just what makes its basics up until now and may change in the future.

## Symbols and keywords

Wide has no keywords. Just some symbols to represent **Intent**. But some types maybe aliased.

## Intents

Wide is strongly typed and it uses this new concept called **Intent**.

**Intent** means the state of mind and/or desire when the person creates code.

Intent is mainly just a language concept, not to be used in daily jargon, but if you wish, you can.

Therea are 2 most fundamental intents.

### `:` Type Intent

Whenever you see the Type Intent `:` (colon symbol) you can think:

- it has type
- it returns type
- it checks type
- or it's just a block separator 🙃

### `=` Assignment Intent

Whenever you see the Assignment Intent `=` (equal symbol) you can think:

- is assigns a value *(of, from or constant of)*

There's also `space` assignment operator in Wide, it's implicit in the space after any value Entity `:` Type Intent and you don't need to explicitly use `=` Intent.

## Entities

Now that you know the 2 most basic intents, let's see some syntax.

E.g.:

```lua
composer: "Amadeus Mozart"
```

Can you spot what were the intents when you read that line of code?

If not, don't worry and just let Wide help you!

The value of the `composer` Entity is of type text `"Amadeus Mozart"`.

Notice that the Type `:` and the Assignment `space` Intents together assign the type and text value to `composer`.

`composer` is the name of an Entity, what most programming languages call *variables*.

⚠️ Wide doesn't have the concept of *variables* like most programming languages do. When you assign a value to a thing you are assigning a value to an **Entity** that is immutable by default.

If reused the same name of an entity, the previous value will be **shadowed** and no longer exists after that point in code.

```lua
composer: "Amadeus Mozart"
composer: "Antonio Vivaldi"
```

Above there exist 2 distinct Entities but the first has to die in order the last to live!

**So you must say:**

The `composer` Entity is assigned the type and text value of "Amadeus Mozart", later shadowed to the value of "Antonio Vivaldi".

You might be thinking that you can't change an Entity's value in Wide, and it's another FP boring language. But you can! When dealing with side-effects that's something you can't avoid.

⚠️ You will learn how to handle **Mutable Entities** and **Constant Entities** as you will see later.

With all that information we can move further on basic data types.

## Built-in Data Types

As you already know Wide has no Keywords, and the same is true for its core scalar, compound (objects) and function types.

Every data type in Wide is implicitly an object behind the scenes with it's own potentially having state or behaviour(s) traits.

It's built-in core data types looks like this:

| Símbolo | English Alias | Exemplos |
|:---:|--------|--------|
| ? | bool (1: true, 0: fale ) | true/false, yes/no, on/off |
| '' | char  | letter 'A', number '1', symbol '$' |
| " | string  | "hello", "sweet potatoes", "How are you?" |
| 0 | int | 1, 10, 100, 999 |
| 0.0 | float | 20.5%, -5.6°C, 10.9km |
| 0.00 | double | Pi(π)3.14159265358979323846, -23.5505200 lat, -46.6333094 lng |
| () | fn \| lambda | (add), (subtract), (print), (click)  |
| <> | obj | Person, Vehicle, Dropdown, Box, Header, Provider |

⚠️ Wide can infer those types! So you don't need to explicitly declare them as you will see.

The beauty of them is that their Intent is both the type and the value they default to,
with exception to the Boolean `?` and the Object `<>`, most values mean exactly what they read.

But if want create a Custom Type you name it and prefix with the `:` Type Intent:

```lua
:string
```

But that would serve no purpose right?

So you could use prefix it with an existing type in Wide:

```lua
"":string
```

That's a Type alias!

But you could do so pass a literal value:

```lua
:string = ""
```

⚠️ As you'll learn in Objects section, Types are close to Interfaces and they can beautifully implement each other!

Or even go more specialized mixing anything that might represent a type.

Besides not having keywords in its syntax, some words an impossible to avoid when talking to types, and as you can **alias** types, and in order to help newcomers and professionals with parity with other languages, Wide has built-in aliases for them:

```lua
{
    ?:bool {0:false, 1:true}
    '':char,
    "":string,
    0:int,
    0.0:float,
    0.00:double
    ():fn
    </>:obj
}
```

That is called **Type Overloading** and you'll learn it later in more advanced sections.

Those words are not syntax, they are English words, you can call it whatever you want on your source library, because when your code gets compiled by Wide it will revert them back for code reduction!

**Symbolic Typing Examples**

```lua
boolEntity: ?
intEntity: ''
stringEntity: ""
intEntity: 0
floatEntity: 0.0
doubleEntity: 0.00
functionEntity: ()
objectEntity: <>
```

**Overloaded Types Examples**

```lua
boolEntity: bool
intEntity: char
stringEntity: string
intEntity: int
floatEntity: float
doubleEntity: double
functionEntity: fn
objectEntity: obj
```

That would be the same explicitly as:

```lua
boolEntity:? = 0
intEntity:'' = '0'
stringEntity:"" = ""
intEntity:0 = 0
floatEntity:0.0 = 0.0
doubleEntity:0.00 = 0.00
functionEntity: () = ()
objectEntity:<> = </>
```

But it's like math where you can just reduce the values by the same value and simplify your life. The compiler will infer what type to use and you will end up to the same syntax you had before:

```lua
boolEntity: 0
charEntity: ''
stringEntity: ""
intEntity: 0
floatEntity: 0.0
doubleEntity: 0.00
functionEntity: ()
objectEntity: </>
```

Hope you noticed that the `space` Intent after the `:` Intent together assigned the values to their Entities, as you already saw, and which by themselves are also their data types symbols.

⚠️ In the case of Boolean `?` it's also `0` valued but Wide is about Intent, so its Intent is properly thought as "Question"ing and it won't make sense pretend to question why it's not `:0` because it could also be an Integer Entity's value. The point to be noticed here is that the Intent is to Question the code what it means not what it does, nor to explicitly and literally write down in its most verbose possible way of what it could so harshly be. It will get clear when you get to questioning Entities about their values, what most languages call "control structures". You could do so:

```lua
boolEntity:bool = false
```

⚠️ **Function | Lambda** Types won't be treated here because it's a different beast, and as it encompasses the whole nature and Wide's system around itself, a whole section is dedicated to Functions. But for the sake of your curiosity, its most basic shape can look like this:

```lua
(add m: int, n: int) int: m + n

m: 20
n: 10

operation: (add)

result: (operation m, n)

"{result}" -- 30
```

or on Entity definition:

```lua
m: 20
n: 10
operation: (m: int, n: int) int: m + n
result: (operation m, n)
"{result}"
```

As you'll see later, Objects in Wide can also act like Functions (Functors).

**Object Entities in (not so) brief...**

They are just like this:

```lua
object:<>
```

But when you explicitly want to create an object in memory you must do like so:

```lua
object:<> = </>
object:obj = </>
```

or implicitly do like so:

```lua
object: </>
```

Notice in the forward slash `/` between the opening and closing parts of the object syntax.

That means you want to create an object in memory.

Not using `</>` is just syntax! Nothing will happen when compiling. The compiler will remove it from compilation.

The default value of an object Entity doesn't exist until you use it.

You create an object like so:

```lua
employee: <
    name: "John",
    age: 34,
    salary: 10000.00
/>
```

## Printing on Screen

That seems nice, but how do you print on screen?

To print on screen you just enclose what you want to print inside double quotes `""` alone in a single line and depending on were you are running wide it will be printed.

```lua
"Hello, Wide!"
```

That will output:

```text
Hello, Wide!
```

⚠️ Yes! There's no need for any function, macro or any voodoo! The `""` is the syntax that does that magic itself if put it alone in a single line or passed alone when Questioning values.

If you need to print `""` double quotes inside a string you just use 2 pairs double quotes instead of one.

```lua
""Hello, "Wide"!""
```

That will output:

```text
Hello, "Wide"!
```

### Interpolation

You can use curly braces inside those quotes `"{}"` to dinamically output values:

```lua
name: "Wide"
"Hello, {name}!"

price: 9.99
"It's ${9.99}."
```

Those lines will output:

```text
Hello, Wide!

It's, $9.99.
```

⚠️ When you see `{}` anywhere its very Intent is to bind itself as a **context** for anything. It's called **Context Intent**. A context can be used to create different things, but you don't need to memorize them all as you learn, they'll get so implicit into your head that you will understand them as you go.

### Printing Entity Type

Wheneven you wanna know the type of an Entity:

```lua
number: 10
name: "Alice"
isActive: true
"{:number:}" -- int
"{:name:}" -- string
"{:isActive:}" -- bool
```

### Printing Entity Name

Wheneven you wanna know the name of an Entity:

- `:<ENTITY>:` prints the name of an Entity
- `::<ENTITY>::` prints the name of the value of an Entity in case it's been aliased.

```lua
number: 10
name: "Alice"
isActive: true
"{:<number>:} value is {number}" -- number value is 10
"{:<name>:} is {name}" -- name is Alice
"{:<isActive>: is {isActive}" -- isActive is 1
"{:<isActive>: is {::<isActive>::}" -- isActive is true
```

## Immutable, Mutable, and Constant Entities

In wide you everything you name is an Entity.

When talking about Entities you might read just Immutable, Mutable or Constant not having the need to write down nor say "Entity". In this guide, there will be cases when the word Entity will be ommited on purpose.

### Immutable Entities

As talked previously, Wide has **Entities** that work like variables or contants in other programming languages.

⚠️ Don't call them variables, please! They are not!

By default Entities are immutable:

```lua
name: "John"
age: 34
salary: '10000.00'
```

Which mean they can't change their state (inner value).

You can't create Immutable Entities in Wide that doesn't have an initial type or value.

```lua
name:
age:
salary:
```

Notice that there's no intent in the code. What's the type? What's the value? If you try to do so you'll get a compiler error and you will have to fix it.

And now is it ok?

```lua
name: string
age: float
salary: double
```

Yes, but it can makes no sense if you never assign them a value and just use the default provided by the type system! If you try to do so you'll get a compiler warning and this code will be removed when compiled if not used. So don't waste yours nor yours computer energy doing that!

You can create a new Entity with the same name by **Shadowing** it, but as you already know, the previous will cease to exist in order for the new to live. Besides that you can also change the initial type when shadowing:

```lua
value: 123
value: "Alice"
```

### Mutable Entities

If you want to be able to change an Entity's state, you can create it as a **Mutable Entity** by  prefixing its name with the `$` State Intent. Yes, it's intent is to say to you that you'll pay a price for that! Convenient?

```lua
$name: "John"
$age: 34
$salary: 10000.00
```

The same rules of assignment for Immutable Entities also apply here:

- You can't create entities without types and values
- You shoudln't create entities that won't be used

But you can change their values!

```lua
$name: "John"
$age: 34
$salary: 10000.00

$name = "Mary"
$age = 58
$salary = 20000.00
```

Did you notice that you don't use the `:` Intent here just the `=` Assignment Intent?

And what would happen if the entity doesn't exist and I don't use the `:` Intent? You got it right! A compiler error!

That's because you can only shadow Immutables, Mutables you reassign.

You can, as will see, import members from other files, but that's a different beast, because only Immutable or Constant Entities can be exported and imported in Wide!

To print them, you don't pass the `$` symbol, because that's not the name, that's just an intent.

```lua
$name = "Mary"
$age = 62
$salary = 20000.00

bonus: 20.0 ? age > 60 . 10.0

"{name} is {age} old. Salary + bonus: {salary*bonus}."
```

The expression in the assignment of the value for `bonus` Immutable:

```lua
20.0 ? age > 60 . 10.0
```

Means: *"use 20.0 if age is greater than 20 else use 10.0"*

It's mostly a Question Intent and you'll learn about very deeply.

### Constant Entities

Constant Entities are similar to Immutable Entities, but with an important difference, they can't be shadowed.

If you want to create a Constant Entity, you must enclose the Immutable Entity into the `{}` Context Intent.

You say that it's opaqued inside `{}` and can't be move down to be shadowed.

```lua
{PI: 3.14159265358979323846}
{SPEED_OF_LIGHT: 299792458.0}
{GRAVITATIONAL_CONSTANT: 6.67430e-11}
{DEFAULT_TIMEOUT_MS: 5000}
{STATUS_OK: 200}
{AVOGADRO: 6.02214076e23}
{API_URL: "https://api.example.com/v1/"}
{DEBUG_MODE: 1}
{ENV: "dev"}
```

⚠️ You don't need to name your Constant Entities in CAMEL_CASE, but it's a good convention to adopt since it gives Visual Intent to your code making them visually different from Immutables!

You output them likewise other entities:

```lua
"The speed of light is {SPEED_OF_LIGHT}."
```

### 🌕 Visual Metaphor for Shadowing Entities

|  | Meaning          | Shadowable? | Notes                        |
| ------ | ---------------- | ----------- | ---------------------------- |
| `speed_of_light:`    | Immutable Entity | ✅ Yes       | Exposed to scope, visible    |
| `$speed_of_light:`    | Mutable Entity   | ✅ Yes       | Visible, but may mutate      |
| `{speed_of_light:}`   | Constant Entity  | ❌ No        | Opaqued, contextually sealed |

**🧪 Examples**

```lua
speed_of_light: 299792458.0
$speed_of_light: 299792458.0
{SPEED_OF_LIGHT: 299792458.0}
```

Can be shadowed:

```lua
speed_of_light: 299792458.0
speed_of_light: 1 ✅ overrides the original
```

Can also be shadowed:

```lua
$speed_of_light: 299792458.0
$speed_of_light: 1
```

Cannot be shadowed — sealed inside context:

```lua
{SPEED_OF_LIGHT: 299792458.0}
SPEED_OF_LIGHT: 1  ❌ Error: constant is opaque and cannot be redefined
```

Now you can see more 2 important Intents of Wide.

### `!` Not Intent

When you see it the Not Intent `!` (exclamation symbol) you may say:

- it is not *(something)*
- it is false *(not true)*
- it can not be
- it modifies *(context, scope, characteristics)*
- it propagates *(intention)*

### `$` Change Intent

When you see it the Change Intent `$` (dolar symbol) you may say:

- it can mutate
- it can change *(something)*

⚠️ *You have already been presented to the `$` Change Intent when learned about Mutable Entities, as it is a more complex intent, placing this section there would make things unnecessarily overheaded.*

Wide has no concept of `null`, `nullptr`, `nil`, `void`, `None` nor `Option` exposed to you because is implicit when you want to change anything in Wide.

It's possible because every entity in Wide has a default state — which makes it always valid, but not necessarily populated.

As you'll see later, you just need to check agains that!

You must pay attention to the fact that the default `0` value is not used to mean any of them in Wide as well, because where `0` is used as scalar types and once defined, they do have a value, so they do have a state.

Related to objects, they may not have default values, so they may not have state. However Wide is able to determine if they changed its state.

And let's just move to a compound type example to clarify some things out.

Suppose you have an Entity of type object to model a person with this structure:

```lua
$person: <
  name: string,
  age: int
/>
```

How could you check if that changed its internal values/state?

```lua
$person: <
  name: string,
  age: int
/>

$person ? "Changed State!" . "Did not change State!"
```

It will output:
`Did not change State!`

Wide is aware of changes inside the person object.

```lua
$person: <
  name: string,
  age: int
/>

$person = <
  name: "Mary",
  age: 15
/>

$person ? "Changed State!" . "Did not change State!"
```

It will output:

```text
Changed State!
```

Now the object changed, so Wide can determine it changed its state.

---

## Comments

Wide has 3 ways to comment code:

### Inline Comments

```lua
-- This is a regular comment
```

But can place it anywhere, just in single lines or after code in a line:

```lua
(doSomething -- You can't use anywhere): ❌ Error Unterminated line
    -- No problem here, but previous broken already!
.
```

### Virtual Syntax Comments

```lua
`final class`.AircraftController </>

-- Calculate total fuel needed
`pure function`(calculateFuel amount:int efficiency:float) float:
    : amount * efficiency
.
```

⚠️ Nothing between backticks is syntax, that's just virtual.

### Multiline Comments

```lua
/*
This is a multiline comment
that can have, as it name implies,
multiple line!
*/
(doSomething /* You can use anywhere */):
    /* but don't forget to close it */
.
```

## Union Types

If you have a Entity that might have more than one possible type and you want to just force it, you can use Union Types.

```lua
value: string | number
value: 123
value: "hello"
```

But it some cases it only makes sense when used with Mutables because since when Shadowing Immutables the compiler kills the previous Entity and creates a new one with whatever same or new type you shadow it.

```lua
value: string | number
value: 123
value: "hello"

-- same as:
value: 123
value: "hello"

-- Mutables makes more sense since you could mean "restrict it"
$value: string | number
$value = "hello"
$value = 123
```

But on more specialized operations Unions came make sense!

```lua
(printId id: number | string):
  "Your ID is: {id}"
.

(printId 101)
(printId "202")
(printId { myID: 22342 }) ❌
```

The separator of the union members is allowed before the first element, so you could also write this:

```lua
(
  printId id:
  | number
  | string
):
  "Your ID is: {id}"
.
```

You can check the type:

```lua
(printId id: int | string):
  :id: == string ?
    "{id.(upper)}"
  . "{id}"
.
```

⚠️ To check a type in Wide you just surround the Entity with `:ENTITY:` and check equality with the type alias in a Question case. You can use it in Match Expression!

You can also some interesting things with Type Unions using string literals.

```lua
:kind = "circle" | "square"
kind: "circle
kind: "square
```

Now look at this:

```lua
:Circle <
  kind: "circle"
  radius: int
/>

:Square <
  kind: "square"
  sideLength: int
/>

:Shape = Circle | Square

(getArea shape: Shape) int:
  shape.kind === "circle" ?
    : Math.PI * shape.radius ** 2

  : shape.sideLength ** 2
.
```

If you went go horse, it would be like this:

```lua
:Shape <
  kind: "circle"|"square
  radius: int
  sideLength: int
/>
```

Compare that with the previous will look like having 3 intentions instead of one to do the same thing, and now you should start questioning yourself when it makes more sense going implict or explict.

## Data Structures

Aside from the basic data types, Wide has some built-in Data Structures mostly to handle the concept of Collections.

For all Data Structures:

- members are separated by commas
- they are iterable.

### List

A List is created using `[]` symbols.

Some examples:

```lua
temperatures: [22.5, 23.1, 21.8, 24.0, 12, 34, 45]
sensorReadings: [10, 12, 9, 11,, 13]
playlist: ["Song A", "Song B", "Song C"]
tasksQueue: ["Login", "Process Data", "Logout"]
row1: ["Alice", 30, "Engineer"]
row2: ["Bob", 25, "Designer"]
columnAges: [30, 25, 40]
employee: ["John", 45, 9999.00, "Developer"]
availableOptions: ["Option A", "Option B", "Option C"]
allowedPermissions: ["read", "write", "execute"]
```

There are two ways to print the members of a collection in Wide.

**One-based index (natural, human-readable):**

```lua
"My Favourite songs are:"
"- {playlist.1}"
"- {playlist.2}"
"- {playlist.3}"
```

**Zero-based index (classic style):**

```lua
"My Favourite songs are:"
"- {playlist[0]}"
"- {playlist[1]}"
"- {playlist[2]}"
```

Wide is able to make the translation because that's just syntatic-sugar ready for you to use!

**Last Item `..`**

You can just get the last item like so:

```lua
"The song I listen to least is:"
"- {playlist..}"

languages: ["PHP", "Python", "JavaScript", "Rust", "Go", "C++", "Wide"]
"The first language I learned was {languages.1}"
"The last will be {language..}"
```

The symbols `..` are called Extent Intent, and you will see it very soon.

All collections have their items accessed like so.

After presenting the core Data Structures you'll be presented to Destructuring, Ranges, and Slices and this knowledge will be expanded.

### Tuple

A Tuple is created using `()` symbols.

Some examples:

```lua
coordinates: (10, 20)
location: (-33.8688, 151.2093)
red: (255, 0, 0)
paleBlue: (173, 216, 230)
user: ("john_doe", 30, "john.doe@example.com")
product: ("Laptop", 1200.50, 5)
serverConfig: ("localhost", 8080, "http")
today: (2025, 5, 6)
gravity: (0, -9.81, 0)

"Coordinates: {coodinates.1}, {coordinates.2}"
"Red: R({red.1}), G({red.2}), B({red.3})"
```

### Set

A Set is created using `{}` symbols.

Some examples:

```lua
roles: {"admin", "editor", "viewer"}
productSkus: {"A123", "B456", "C789"}
visitedUrls: {"https://example.com", "https://openai.com", "https://github.com"}
daysOff: {"Saturday", "Sunday"}
enabledFeatures: {"dark_mode", "notifications", "auto_save"}
bannedUsers: {"troll123", "spammer99", "bad_actor"}
tags: {"python", "webdev", "tutorial"}
fruits: {"apple", "banana", "mango"}
registeredIps: {"192.168.1.10", "192.168.1.11", "10.0.0.2"}

-- Random results for sets

"This week you'll be off on {days_off.1}"
"I may take a {fruits.2} to eat now"
```

### Dictionary

A Dictionary is created using `{:}` symbols structure.

Some examples:

```lua
-- User profile data
user: {
  "name": "Alice",
  "age": 30,
  "email": "<alice@example.com>",
  "isActive": True
}

"{user.name} is {user.age}"

-- Nested data for a blog post
post: {
  "title": "Why Python Rocks",
  "author": {
    "name": "Bob",
    "id": 42
  },
  "tags": ["python", "programming", "tutorial"],
  "published": True
}

"{post.title} by {post.author.name}"
"Tags: {post.tags.1}, {post.tags.2}, {post.tags.3}
```

### String

A String is created using `""` symbols structure.

Some examples:

```lua
message: "Hello, Wide!"
name: "Mary Alice"
```

## Destructuring

Destructuring in a way to unpack values from arrays and objects into distinct Entities.

It provides a more concise and readable way to extract data from these Collections.

All Collections in Wide provide support for destructuring at some level.

Depending on the Collection order will not be preserved.

Entities created by destructuring a Collection will cause to create Constant-like Immutable Entities.

**List**

```lua
user: ["Mary", 35, 10000.00]

{name, age, salary}: languages

"{name} is {age} years old and makes {salary} monthly"

languages: ["PHP", "Python", "JavaScript", "Rust", "Go", "C++", "Wide"]

{...language}: languages

"The first 3 languages to learn this year are:"
"1 - {language.1}"
"2 - {language.2}"
"3 - {language.3}"
```

Entities created at destructuring are all Immutable and can be shadowed.

For Tuples, Sets, and Dictionaries you'll mostly do the same, but Sets won't preserve the order.

**Tuple**

```lua
{name, age, city}: ("Alice", 25, "New York")

"{name} is {age} years old and lives in {city}"

{...user}: ("Alice", 25)

"{user.1} is {user.2} years old and ives in {user.3}"
```

**Set**

```lua
lotteryCompetitors: {"Alice", "Bob", "Charlie", "Diana", "Eve", "Frank"}

{firstWinner, secondWinner, thirdWinner}: lotteryCompetitors

"Winners are:"
" #1 {firstWinner}"
" #2 {secondWinner}"
" #3 {thirdWinner}"

{...winners}: lotteryCompetitors

"Winners are:"
" #1 {winners.1}"
" #2 {winners.2}"
" #3 {winners.3}"
```

**Dictionary**

```lua
post: {
  "title": "Why Python Rocks",
  "author": {
    "name": "Bob",
    "id": 42
  },
  "tags": ["python", "programming", "tutorial"],
  "published": True
}

{title, author, tags}: post
"{title} by {author}"
"- {tags.1}"
"- {tags.2}"
"- {tags.3}"
```

**String**

Strings are Immutable, but can accessed like Lists.

```lua
message: "Hello, Wide!"
"{message.1}" -- H
"{message.8}" -- W

...letter: message
"{letter.1}" -- H
"{letter.2}" -- e
"{letter.3}" -- l
"{letter.4}" -- l
"{letter.5}" -- o
```

### Fixed Size Collections

All Collections in Wide can have a fixed size:

```lua
numbers:[2] = [] -- Same as: [0, 0]
numbers:[2] = [1] -- Same as: [1, 0]
numbers:[2] = [1, 2] -- Same as: [1, 2]
numbers:[2] = [1, 2, 3] ❌ -- Error!
```

Notice that the count is placed in after of the `:` Type Intent and the `=` Assignment Intent must be used forcebly:

```lua
numbers:[2] -- Same as: [2]
numbers:[2] = [] -- Same as: [0, 0]
```

### Typed Collections

All Collections in Wide can have an explicit type:

```lua
numbers:[]int
-- Same as: [0, 0]

numbers:[2]int = []
-- Same as: [0, 0]

numbers:[]int = [1, 2, 3]
-- Same as: [1, 2, 3]

names:[]string
-- Same as: ["", ""]

names:[2]string = []
-- Same as: ["", ""]

names:[]string = ["Alice", "Mary", "Diane"]
-- Same as: ["Alice", "Mary", "Diane"]
```

But of course, why do that if Wide can infer it for you?

### `//` Inclusion Intent

Whenever you see the Type Intent `//` you can think:

- it can be in(side) *(a questioned condition)*
- it can match something *(regular expression)*
- it can be where *(algegraic)*
- it can include *(countable elements)*

### Counting Collections

Every Collection in Wide can be questioned about how many elements it has using the `//` Inclusion Intent.

```lua
numbers: [10, 20, 30, 40, 50]

"How many elements in 'numbers'?"
"There are {/numbers/} elements in 'numbers'"
-- There are 5 elements in 'numbers'
```

And if the Collection has fixed size it works the same way:

```lua
numbers:[5] = [10]

"How many elements in 'numbers'?"
"There are {/numbers/} elements in 'numbers'"
-- There are 5 elements in 'numbers'
```

Simple count string characters:

```lua
message: "Hello, Wide!"

"'message' has {/message/} characters"
-- 'message' has 12 characters
```

### `..` Extent Intent

Whenever you see the Extent Intent `..` you can think:

- it has length
- it has degree
- it has sequence
- it has boundary

You have already been exposed to it when learning how to access Collections indexes.

## Slices

Slices extract subsequences from collections using start, stop, and step notation `:0..0:0`, meaning `start..end:step` that create a Range.

The feature here is the `..` Extent Intent that's both a Slice and/or Range depending on the Context it is used.

```lua
list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

"{list:..}" -- [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
"{list:1..4}" -- [1, 2, 3, 4]
"{list:3..5}" -- [3, 4, 5]
"{list:7..}" -- [7, 8, 9, 10]
"{list:-3..}" -- [8, 9, 10]
"{list:1..6:2}" -- [1, 3, 5]
"{list:1..:2}" -- [1, 3, 5, 7, 9]
```

```lua
string: "Hello, Wide!"

"{string:..}" -- ['H', 'e', 'l', 'l', 'o', ',', ' ', W', 'i', 'd', 'e']
"{string:8..11}" -- ['W', 'i', 'd', 'e']
"{string:1..5}" -- ['H', 'e', 'l', 'l', 'o']
"{string:8..}" -- ['W', 'i', 'd', 'e', '!']
```

```lua
tuple: ('a', 'b', 'c', 'd', 'e')

"{tuple:..}" --  ('a', 'b', 'c', 'd', 'e')
"{tuple:2..4}" --  ('b', 'c', 'd')
"{tuple:1..3}" --  ('a', 'b', 'c')
```

There's more to slices, but that's just a taste for you to meat Ranges after Iterations.

## Iterations

Wide has a revamped approach to iterating over Collections data.

Following Wide's idea of not having keywords, you'll be able to iterate data without `for`, `while`,  `do-while`, `foreach` in a simple way.

### `~` Iteration Intent

Whenever you see the Iteration Intent `~` (tilde symbol) you can think:

- **it has repeation**
- **it has continuity**
- or **it has recursion**

All Collections in Wide are Iterables and you can iterate over equally.

### Iterating with Collections

Iterating in Wide is done with lambdas.

You can get the index of the current iteration using `.` or `[]` after the name of the collection Entity.

```lua
numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

~(number : numbers):
  "Number at #{numbers.} is {number}"
  -- Number at #1 is 1

-- or inline
~(number : numbers): "Number at #{numbers.} is {number}"

-- You haven't been presented to Functions yet,
-- but here's a simple Function  to return a squared number
-- and inlined to look like a Lambda
(squared number:int) int : number ** 2

-- or passing function to lambda
~((squared number) : numbers) :
  "Number at #{numbers.} squared is {number}"
```

```lua
uniqueColors: {"red", "green" , "blue" }

~(color : uniqueColors) :
  "Color is {color}"

-- or inline
~(color : uniqueColors) : "Color is {color}"

-- simple Function to make the string upper case.
(upper input:string) : string.(upper)

-- or passing function to lambda
~((upper color) : uniqueColors) : "{color}"
```

```lua
uniqueColors: {"red":'R', "green":'G', "blue":'B'}

~({key, value} : uniqueColors) :
  "{key.(capitalize)} is represented by the letter: {value}"

~(color : uniqueColors) : "Color is {color}"

```

The same is true for all other Collections.

### Controlled Repetition

Sometimes you may just need to repeat things.

Wide has smart functional built-in structures to iterate recursively until a condition is met or not.

You can also apply some of the knowledge you have with Slices to control even more repetition.

**Interate Until condition is met:**

```lua
$counter: 1

~(counter <= 10):
  "Counter value is: {counter}"
  $counter = counter + 1

```

The above example is syntacticaly the same as:

```lua
$counter: 1

~(counter <= 10)..: -- Extent intent here
  "Counter value is: {counter}"
  $counter = counter + 1

```

**Special Conditions:**

`:1:` step into one time at least and ignoring condition once

```lua
~(choice != 'Q'):1:
  "Menu"
  "- Open (O)"
  "- Print (P)"
  "- Quit (Q)"
  -- Some logic here...

```

`..3` run the first three iterations only independently if they meet or not the condition

```lua
$counter: 1

~(counter <= 10)..3:
  "Counter value is: {counter}"
  $counter = counter + 1

```

`3..` run from third iteration up to end independently if they meet or not the condition

```lua
$counter: 1

~(counter <= 10) 3..:
  "Counter value is: {counter}"
  $counter = counter + 1

```

`3..6` run from third iteration up to sixth independently if they meet or not the condition

```lua
$counter: 1

~(counter <= 10) 3..6:
  "Counter value is: {counter}"
  $counter = counter + 1
```

### Interrupting Repetition

```lua
$counter: 1

~(counter <= 10):
  "Counter value is: {counter}"

  $counter = counter + 1

  `continue`
  > ? count % 2 == 0

  `break`
  . ? count == 5
```

### Loop

**Infinite**

```lua
~():
  "Do something until break"

```

**For-like**

```lua
~($i: 0)($i < 10)($i = $i + 1):
  "imprima {i}"
```

## Ranges

Ranges generate numerical sequences for iteration.

They are based on the concept learned for Slices and Iterations.

Some examples:

**Wide one-based style**

The following example start all at 1

```lua
range: ~(6)
~(val : range): "{val}" -- 1 2 3 4 5 6

-- no need for temporary entity
~(val : (6)): "{val}" -- 1 2 3 4 5 6
```

```lua
range: ~(3..6)
~(val : range): "{val}" -- 3 4 5 6

-- no need for temporary entity
~(val : (3..6)): "{val}" -- 3 4 5 6
```

```lua
range: ~(3..10:2)
~(val : range): "{val}" -- 3 5 7 9

-- no need for temporary entity
~(val : (3..10:2)): "{val}" -- 3 5 7 9
```

**Classic Zero-based index**

```lua
range: ~([6])
~(val : range): "{val}" -- 0 1 2 3 4 5

-- no need for temporary entity
~(val : ([6])): "{val}" -- 0 1 2 3 4 5
```

```lua
range: ~([3:6])
~(val : range): "{val}" -- 3 4 5

-- no need for temporary entity
~(val : ([3:6])): "{val}" --: 3 4 5
```

```lua
range: ~([3:10:2])
~(val : range): "{val}" -- 3 5 7 9

-- no need for temporary entity
~(val : ([3:10:2])): "{val}" -- 3 5 7 9
```

⚠️ In this documentation Wide syntax will use just One-based indexes.

## `?` Question Intent

Every time you want to question your code for anything you use the `?` Question Intent.

As you might guess, Wide has no keywords for them as well.

Some examples:

```lua
name: "Ada"

name == "Ada" ?
  "Welcome, Ada!"
.

-- inline
name == "Ada" ? "Welcome, Ada!"
-- No need for . Resolution
```

```lua
number: 10

number > 10 ?
  "{number} is greater than 10"
.

-- inline
number > 10 ? "{number} is greater than 10"
-- No need for . Resolution
```

You can just use an empty space if you mean `==` equality.

As you can see you don't need to use the `.` Resolution Intent when going inline.
Yyou can go inline or single-line, your choice!

This is true for all other Question Intents you'll see.

```lua
name: "Mary"

name == "Mary" ? -- if
  "Welcome, Mary!"
. "Welcome, Stranger!" -- else

-- or
name == "Mary" ? "Welcome, Mary!" . "Welcome, Stranger!"
```

```lua
name: "Mary"

name == "Alice" ? -- if
  "Welcome, Alice!"
name == "Mary" ?? -- else if
  "Welcome, Mary!"
name == "Claire" ?? -- else if
  "Welcome, Claire!"
name == "Diane" ?? -- else if
  "Welcome, Diane!"
. "Welcome, Stranger!" -- else
```

⚠️ You might be wondering: What the `.` is called in Wide? - Well it has a name, and it's called `.` Resolution Intent and, in brief, it's used to stop propagation from a Context or Scope, and to ask for a final action as you'll learn.

You can also nest Questions:

```lua
name: "Alice"
authorized: false

name == "Alice" ?
  "Welcome, Alice!" -- if(1)

  authorized ?
    "You are authorized!" -- if(2)
  . "You are NOT authorized!" -- else(2)

. "Welcome, Stranger!" -- else(1)

```

⚠️ Pay attention to identation! If put on same level, it will mean different things.

You can simulate a Ternary Operator by inlining a simple Question like so:

```lua
age: 17
authorized: "Authorized" ? age > 17 . "Not Authorized"
```

The above reads:

```text
Authorized if age is greater than 17 else Not Authorized
```

Same as:

```lua
age: 17
authorized: age > 17

authorized ?
  "Authorized"
. "Not Authorized"
```

Case when there are multiple expressions to question:

```lua
age: 17
supervised: true
name: "Authorized" ? age > 17 || supervised . "Not Authorized"
```

As you already know Wide has no null, nil, None, Option madness keywords to mean voidness.
If you need to check the existence of a value, you check agains it's state just passing the Entity.

```lua
name:string  -- string is the type (alias), not the value
""Welcome, {name ?. "Stranger"}!""
```

That would print:

```text
Welcome, Stranger
```

```lua
name: "Alice"
""Welcome, {name ?. "Stranger"}!""
```

That would print:

```text
Welcome, Alice!
```

### Regular Question Expression 🤣

Regular Expression in Wide is done using the `//` Inclusion Intent.

```lua
 /cat|dog/ entityToMatch
```

```lua
animal: "bird"
"matched" ? /cat|dog/ animal  . "did not match!"

text: "my dog is a beautiful dog and I love my dog"
~({match} /cat|dog/ text): "{match}"
```

You must always pass an entity after the expression:

```lua
"matched" ? /cat|dog/ `animal` . "did not match!" ❌ -- No entity to match after expression

~({match} /cat|dog/ `text`): "{match}" ❌ -- No entity to match after expression
```

Another way to Question in a *Switch-like*:

```lua
a: 2

(a)?
  1:
    "one", -- By default when separating it will "break"
  2:
    "two"
    "two again",
  3:
    "three",
  4:
    "Four" >>,  -- >> If Fall through case has previous body
  5, 6, 7: -- Fall through
    "mistery number" -- No need for `,` here
  . "other number" -- Resolution Intent is obrigatory to close the questions and `,` is not allowed here since it would make no sense.
  `.` -- But could be just empty
```

Another example:

```lua
day: 4

day?
  (1, 7):
    "Weekend!",
  (2, 3, 4, 5, 6 ):
    "Weekday!"
  .
```

By default all cases in a *Switch-like* Question break at `,` comma symbol. If wanna to let fall throught the next case,

In the *Switch-like* Question its case doesn't return values, so that if you place `""` after the `:` you actually will get those same texts printed.

```lua
a: 2

(a) ?
  1:  "one",
  2:  "two" "two again" "two again again",
  3:  "three",
  4:  "Four" >>,
  (4, 5, 6, 7): -- when grouping you must use a tuple
      "mistery number"
  .   "other number"
```

```lua
day: 4

day?
  (1, 7): "Weekend!",
  (2, 3, 4, 5, 6 ): "Weekday!"
  .
```

If you want to return a value, you can specialize your Question using Match Expressions:

```lua
item: 10

message: item ?
  -- in all the cases it will return what's after ':'
  = 11: "It's 11"
  < 10
    -- if you go newline you'll move ':' to the return line
      : "Less than 10"
  > 10: "Greater than 10"
  -- you must use ':' return operator in Match Expression Case
  .   : "It's 10"
  `.` -- cannot be empty

"{message}"
```

If you want to both return and print you it can. You can also give a temporary name for the match expression:

```lua
item: 10
times10: item ?
  -- create a temporary "eq" name for the match expression case
  = 11 {eq}:
    "It's 11"
    : eq * 10
  < 10 {lt}:
    "Less than 10"
    : lt * 10
  > 10 {gt}:
    "Greater than 10"
    : gt * 10
  .
    "It's 10"
    : item * 10 -- used questioned Entity name "item" since no special naming need

"{message}"
```

⚠️ You can also use Regular Expressions in Match Expressions. Just be creative!

You'll soon see Functions, but it's interesting to mark it here. When scoped alone inside a function you can do like so:

-- Basic function

```lua
(verifyNumber x:int) string:
  "What {x} verifies?"

```

Guess you can figure out that the `:` Type Intent here means `return it`.
So that would be the same as:

```lua
(verifyNumber x:int) string: x ?
  = 11: "It's 11"
  < 10: "Less than 10"
  > 10: "Greater than 10"
  .   : "It's 10" `Default

```

⚠️ The difference between Switch-like Question and Match Expression, is that Match Expressions return values, like you saw in the function above.

## List Comprehensions

Wide itself doesn't have List Comprehensions like Python, but you can use Iterators and Questions to achieve the same results in a very simpler fashion.

```lua
fruits: ["apple", "banana", "cherry", "kiwi", "mango"]

newList: ~(x : fruits) ? /a/ x -- "? /a/ x" question: is a "in" x

"{newList}" -- Output ["apple, "banana", "chery", "kiwi", "mango"]
```

Same as:

```lua
fruits: ["apple", "banana", "cherry", "kiwi", "mango"]

$newList: []

~(x : fruits) :
  /a/ x ? $newList[] = x

"{newList}" -- Output ["apple, "banana", "chery", "kiwi", "mango"]
```

Notice that in the second case, you had to use the `$` Intent because you have to explicitly make it mutable. In the first case the Collection is Immutable.

When you use `? /a/ : x` you are checking if the value of the `character` `a` matches inside `x`. You just can think of them like mini Match Expressions with only 1 possibility.

Now compare you Python:

```python
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = [x for x in fruits if "a" in x]
print(newlist)
```

Same as:

```python
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = []
for x in fruits:
  if "a" in x:
    newlist.append(x)
print(newlist)
```

⚠️ You can go crazy with Iterators in Wide! But be careful not to forget that Intent might not be explict.

It's possible to switch between Colletions Types

**To Tuple :()**

```lua
fruits: ["apple", "banana", "cherry", "kiwi", "mango"]

newList:() = ~(x : fruits) ? /a/ x

"{newList}" -- Output ("apple, "banana", "chery", "kiwi", "mango")
```

**To Set :{}**

```lua
fruits: ["apple", "banana", "cherry", "kiwi", "mango"]

newList:{} = ~(x : fruits) ? /a/ : x

"{newList}" -- Output {"apple, "banana", "chery", "kiwi", "mango"}
```

**To Dictionary :{:}**

```lua
fruits: ["apple", "banana", "cherry", "kiwi", "mango"]

newList:{:} = ~({x.1 : x} : fruits) ? /a/ : x

"{newList}" -- Output {"a":"apple, "b":"banana", "c":"chery", "k":"kiwi", "m":"mango"}
```

And is true for each other! Just change to the Collection you want.

### Destructuring Chain

You can create a chain of destructured members:

```lua
people: [
  {"name":"Alice", "age": 34}
  {"name":"Eve", "age": 29}
  {"name":"Oscar", "age": 42}
  {"name":"Uma", "age": 25}
  {"name":"Igor", "age": 38}
  {"name":"Bob", "age": 45}
  {"name":"Aaron", "age": 31}
]

grouped:{:} = ~(
  {
    person.name.1.(lower) : {
      "name": person.name,
      "age": person.age
    }
  } : person : people -- Chain: A dictionary member from person from people
) ? person.age > 30 && person.name.1 : /[aeiou]/i

"{grouped}"
```

## Functions

With all that base you can now touch on Functions.

This guide pretends you know all the previous sections' content in order to make any good use of what you'll see. Just showcasing simple functions, wouldn't make sense first. As Wide is mostly Function/Lambda powered, but they will just make sense if you do know it's basic and core features or syntax previously.

Functions and Lambdas have a special syntax that deviates from what most programming language have.

In its nature Functions are related to Lambdas.

## Basic Syntax

A Function itself that does nothing other than exist:

```lua
():
```

To invoke a Function you do like so:

```lua
() -- Does nothing
```

Named Function:

```lua
(greet):
(greet) -- Does nothing
```

Function that prints a message:

```lua
(greet): -- No return type
  "Hello, Wide!" -- No return value, will just print to screen

(greet) -- Output: Hello, Wide!
```

### Parameters

Function that prints a message based on single parameter:

```lua
(greet name:string): -- No return type
  "Hello, {name}!" -- No return value, will just print to screen

(greet "World") -- Output: Hello, World!
```

**Returning Values:**

The `:` Type Intent is used to return a value from a Function.

Function that returns a message based single on parameter:

```lua
(greet name:string) string: -- Return type is of type string
  : "Hello, {name}!" -- Return value is of type string

(greet "World") -- Doesn't output anything
""{(greet "World")}"" -- Hello, World!

message: (greet "World")
"{message}" -- Hello, World!
```

As you saw, the `:` Type Intent is used to return a value from a Function, but you can inline it like so:

```lua
-- Inlined function
(greet name:string) string : "Hello, {name}!"
-- No need for . Resolution
```

⚠️ Pay attention when inlining a Function that returns a string which the type is inferred by Wide!

This:

```lua
(greet name:string): "Hello, {name}!" -- Type is inferred to be "string"
```

Is not the same as this:

```lua
(greet name:string): -- No return type
  "Hello, {name}!" -- No return value, will just print to screen
```

⚠️ When you inline a Function you don't need use the `.` Resolution Intent, but if you like, you can!

⚠️ **Remember:** If you wan't to print anything from a Function you must always place the printer line inside the Function body and never inline the function.

Again:

```lua
(greet name:string): -- No return type
  "Hello, {name}!" -- Will print to screen, will just print to screen
```

For all other data or structure types it's okay since they can't be printed directly other then inside `""`.

```lua
-- Wide knows when it's another type other then "" and there's no confusion
(times10 number:int): number * 10 -- int return inferred (no : "" here)

result: (times10 10)

"{result}" -- 100
```

**Multiple parameters:**

You separate parameters using `,` commas. Yes! `,` Separation Intent!

```lua
(add n:int, m:int, o:int) : n + m + o

result = (add 5, 10, 15) -- You also separate values by commas
"{result}" -- 30
```

**Default parameter value:**

```lua
(greet name: "Stranger"):
    "Hello, {name}!"

(greet) -- Hello, Stranger
```

**Named Parameters:**

```lua
(greet name:string, greeting: "Hello", warm: false):
  "{greeting}, {name}!"
  warm ? "You are awesome!"

(greet "Alice") -- "Hello, Alice"
(greet name: "Alice", greeting: "Hi") -- Hi, Alice!
(greet name: "Alice", warm: true) -- Hello, Alice! \n You are Welcome!
```

⚠️ Parameters without a default value must appear in the same order they have in the Function signature.

```lua
...
(greet "Alice", warm: true)
(greet "Alice", greeting: "Hi")
```

**Unnamed Parameters**

If don't want to name your parameters you just do so:

```lua
(add ..numbers:int):
  sum: 0
  ~(number:numbers): sum += number

  : sum

result = (sum 10, 20, 30, 50)
"{result}" -- 100
result = (sum 10, 20, 30)
"{result}" -- 50
result = (sum 10, 20)
"{result}" -- 30
result = (sum 10)
"{result}" -- 10
result = (sum)
"{result}" -- 0
```

You can also mix with positional once they come first:

```lua
(add a:int, b:int ..numbers:int):
  sum: 0
  ~(number:numbers): sum += number

  : sum

-- Just for clarity names were used, but no need!
result: (sum a:10, b:20, 30, 50)
```

### Changing External Entities

You can change external Entities by using the `$` State Intent after function invokation and passing the variables you want to allow mutate inside:

```lua
(funcCall $name) $ $name
```

Some examples:

```lua
$name: "Mary"
$message: "Hello"
times: 10

(greet name: "Stranger", message:"Hello", times: 5):
  name: "Alice"

  ~(times) :
    "{message}, {name}!"
. -- You can use the Resolution Intent to sign separation

"{message}" -- initial value STILL!
"{name}" -- initial value STILL

(greet $name) -- Ordinary function call

"{message}" -- initial value STILL!
"{name}" -- initial value STILL

/*
 Here function call will change the outside scope.
*/
(greet $name) $ $name
"{message}" -- initial value STILL!
"{name}" -- initial value CHANGED!

(greet $name, $message) $ $name, $message
"{name}" -- initial value CHANGED!
"{message}" -- initial value CHANGED!
```

There's no way to pass an Immutable!

```lua
(greet $name, time:10) $ times ❌ -- Error cannot mutate immutable Entity 'times'!

(greet "John", "Hi") $ name, message ❌ -- Error cannot mutate immutable Object String
```

**Moving the scope of an Entity:**

You can similarly move the scope of an Entity using the `<<` Move Intent:

```lua
number1: 10
number2: 20

(add a:int, b:int):
  : a + b


"{number1}"
"{number2}"
sum: (add number1, number2) << number1 -- number2 moved to sum Function scope
"{sum}"
"{number1}"
"{number2}" ❌ -- Error 'number2' does not exist in this scope
```

And for moving Mutables:

```lua
$number2: 20 -- Mutable now

"{number1}"
"{number2}"
sum: (add number1, $number2) << $number2 -- $number2 moved to sum Function scope
"{sum}"
"{number1}"
"{number2}" ❌ -- Error '$number2' does not exist in this scope
```

## Lambdas

To create a Lambda in Wide you just create an Entity an assign function to it.

```lua
fn = (): "Do nothing"
(fn) -- will print nothing!


msg: (fn)
"{msg}" -- will ouput "Do nothing"
```

When directly creating Lambda as values for Entities, it seems more pleasing and Mathematically correct to use the `=` operator.

```lua
fn: ():
  "Do nothing"


fn = ():
  "Do nothing"

```

You can use any! Your choice!

Lambdas can have parameters:

```lua
greet = (name:string):
  "Hello, {name}!"


(greet "Wide") -- Hello Wide!
```

Lambdas are just like functions but they have some special powers.

With regular Functions you can't access the outter scope, with Lambdas you can using the `//` Inclusion Intent.

```lua
name: "Wide"

greet = (greet: string) /name/ :
  "{greet}, {name}!"


(greet "Hello") -- Output: Hello, Wide!
```

And of course you can just spread the whole world inside a Lambda:

```lua
greet: "Hi"
$name: "Wide"

greet = () /.../ :
  "{greet}, {name}!"


(greet) -- Output: Hello, Wide!
```

Lamdas can change also the state of Mutable entities alike functions, but just for the parameters used in the `//` Inclusion Intent, not Lambda's signature:

```lua
$name: "Wide"

greet = (greet: string) /$name/ :
  $name: "World"
  "{greet}, {name}!"

"{name}" -- initial state STILL
(greet "Hello") $ $name
"{name}" -- initial state CHANGED
```

Of course, you also can't use Immutables for that!

You can also Move Entities to Lambda Scope if you need that.

```lua
(greet "Hello") << $name
"{$name}" ❌ -- Error '$name' does not exist in this scope
```

### `@` Event Intent

Whenever you see the Type Intent `@` you can think:

- it has behaviour *(metadata)*
- it has asynchronous behaviour *(async/await)*
- it has concurrent behaviour *(processes)*
- it has reactive hehaviour *(live update, assertion related)*
- it has deferred behaviour *(later used, error)*
- or it has event *(you guessed it!)*

## Error Handling

In Wide if you want to control if an Error has happened you just need to capture that event.

If you want to stop execution immediately on error you can use assertion:

```lua
(division n:int, m:int) int:
  @(
    m == 0,
    "Cannot divide by {n} by {m}"
  )
  : n / m


(division 10, 0) ❌ -- Execution will stop immediatly
```

If you want to capture the error you can propagate using the `!` Not Intent:

```lua
(division n:int, m:int) int:
  !@(
    m == 0,
    "Cannot divide by {n} by {m}"
  )
  : n / m

-- somewhere else in code
n: 10
m: 0

@result: (division n, m)

result ?
  "result is {result}"
  . "{@result}" -- Cannot divide by zero - won't break the application flow!


-- or default to value (in this case 0)
result: @(division n, m)?.0
"{result}"
```

You can also self-capture the error using `:` at the end and closing with `.` Resolution Intent where stops the propagation:

```lua
(printUserData):
  @(
    error,
    "error fetching data"
  ): -- start capturing here
    users: query("select from users")
    ~(user: user): "{user.name}"
  . -- stop capturing here ( . could be ommited)

(printUserData) -- If an error occur it will break execution immediatly
```

And propagate captured error just using preceding `:` with `!`

```lua
(fetchUserData) []User:
  users:[]User

  !@(
    error,
    "error fetching users"
  ): -- start propagating captured error
    users: (query "select name, age from users")
  . -- stop propagating here

  : users


@(fetchUserData)
  ? ~({name, age} : users):
    "{name} is {age} years old!"
  . "{@}" -- Will print "error fetching users" -- if an error occur
```

## Async/Await Functions

Wide can handle async/await like in many contexts, but in Functions it's kinda magical!

On Function Declaration you just prefix the name with `@` and it says `async` event started.

On Function Call you just prefix the name with `@` and it says `await` event started.

```lua
(@fetchUserData) []User:
  users:[]User

  !@(
    error,
    "error fetching users"
  ):
    users: (@query "select name, age from users")
  .

  : users
.
```

But look how magical things get now checking for Error on an Async Function!

```lua
@(fetchUserData)
  ? ~({name, age} : users):
    "{name} is {age} years old!"
  . "{@}"
```

It's both awaiting and capturing the error Events at the same time with just one Intent!

### Concurrency

When you prefix a list with `@[]` you can create a concurrent Context:

```lua
@[
  (processOne),
  (processTwo),
  (processThree)
]
```

## Function Special Return Cases

### HTML Fragment Return `<></>`

When working with Web projects that are HTML-heavy, Wide has some niceties for you!

Wide makes HTML Functional and Reactive by nature on the Web Browser.

The HTML Fragment `<></>` is used to enclose the HTML Function body.

When you are building UI's you can also make your Entities reactive by just prefixing them with `@` Event Intent.

```lua
-- Functional Component
(Main children:HTML): <>
  {children}
</>

-- Functional Component
(Greet name: string): <>
  <p>Hello, {name}</p>
</>

-- Functional Component
(HomePage):
  userName: "Mary"
  currentDate: 2025

  -- Function used in button onclick
  (changeUser):
    -- When you prefix an Entity when "shadowing" you mean:
    -- "React Asyncronously to it in-place" and update the UI
    @userName: "Alice" -- Event Intent here!

    -- Nothing will happen in the UI, just locally Shadowed
    userName: "John"
  .

  -- no need for : in special HTML returning Function
  <>
    <Main> -- Functional Component
      <header>
        <h1>Welcome!</h1>
      </header>
      <Greet name={userName} /> -- Functional Component
      <button onclick={changeUser}>
        Change Username
      </button>
      <footer>&copy; {currentDate}</footer>
    </Main>
  </>
```

## Functional Object Programming 🤣

Here the Functional meet Object-Oriented and they live happy forever!

You are gonna be presented to the most important concepts of Wide Objects and how they can help your Intentions to Model real world scenarios.

### Objects

⚠️ Wide has no keywords but naming is necessary, so English was choosen for naming Entities in Wide and its core Objects, Functions, Types and others.

Every Entity in Wide is an Object behind the scenes.

Let's take 3 cases as example:

*(just keep watching)*

```lua
number: 10
name: "Wide"
alive: true
-- or
number:int = 10
name:int = "Wide"
alive:int = true
```

is the same as

```lua
number:Int32 = 10
name:String = "Wide"
alive:Boolean = true
```

which in its core are `Resolution Objects`:

```lua
.Int32 </>
.String </>
.Boolean </>
```

both derive from `Extent Object` named guess what? - Object:

```lua
..Object </>

.Int32 ..Object </>
.String ..Object </>
.Boolean ..Object </>
```

Have you notice anything?

||Object |Intent|
|---|---|---|
|`.` |Resolution Object| Resolution Intent|
|`..`| Extent Object| Extent Intent|

That's not mere coincidence!

Whatever exists in an Extent Object is spread over the Object extended by it.

An Extent Object can both extend or be extended and can't be used directly in Entity definition nor assignment.

A Resolution Object can only be extended and can only be used in Entity definition or assignment.

As you have already seen, Wide uses `<>` for object type definition and `</>` for value assignment.

And here's where it came from!

### Anonymous Objects

Every time you see it `</>` alone you are seeing an object, but as you have already seen ni the very beginnigs of this Guide, you can create anonymous objects:

```lua
$person: < -- Unnamed Objects is an Anonymous Object
    name: string,
    age: int
/>
```

### Resolution Objects

They are objects that you use to create concrete Object Entities and you can resolve them.

You create a concrete object by prefixing its name with `.`:

```lua
.Thing </>

thing: <Thing />
```

**Adding Functions to Objects**

Objects are Entities that can have their own Entities and Functions.

```lua
.Thing <
  -- this an Object Function
  .(doSomething):
    "Doing something!"
/>

thing: <Thing />
thing.(doSomething) -- Doing nothing!
```

### [] Meta Intent

Whenever you see the Meta Intent `[]` you can think:

- it is shared data
- it has shared data
- it has exchangable data

Think of it like Entities for Data that only Objects can have.

They form a List, that's why they use `[]` symbols.

```lua
.Thing <
  -- This is an Meta Entity [do]
  .[do]: true

  -- this an Object Function
  .(doSomething):
    .do ? "Do something!"
/>

thing: <Thing />
thing.[do] ? thing.(doSomething) -- "Do something!"
```

And now things can get weird for some and amazing for others:

```lua
.Thing <
  -- Make Meta Entity Mutable
  .[$do]: true

  .(doSomething):
    .$do ? "Do something!"
/>

/*
 you now can pass it in the object creation as HTML properties.
 in this case is like using a mutable inside "", you don't need to use $do just do
*/
thing: <Thing do=false />

-- or you could use another Entity's value using {} interpolation like you'd do in "":
doSomething: false
thing: <Thing do={doSomething} /> -- No need for [] Meta Intent here as well

-- here you must use $do!
thing.[$do] ? thing.(doSomething) -- this Question is not resolved
```

⚠️ It won't make sense to use Immutable Meta Entities in the example above since you can't use `=` with Immutables.

In wide the term **Context** is different from **Scope**!

Where a Context means mostly the place where something happens, a Scope means the shape and extent of this Context's Intents.

So Context is meant for the place of code and Scope for Objects that exist in it!

So you can picture a Wide source file like so:

```lua
-- start of file
`{` -- locally implicit
"your source code goes here"
`}` -- locally implicit
-- end of file
```

There's a hidden `{}` that **Isolates** your source code from **Side-effects** unless you explicitly **Resolve* it. *(Remember you resolve side-effects!)*

So your code is in **Isolation Intent** mode. (Which is also the antonym of `Context`)

If anything is in **Isolation Intent** and you wanna something from any Context, you must `Resolve` it using the well known `.` Resolution.

**Isolation Intent** is the only Intent that doesn't have a symbol.

**Resolve** a Context means: *question*, *find*, *prefer*, or *select* anything within a scope preserving its characteristics.

That all said, in Wide **Isolation Intent** is the **Static Scope** of a file Entity or an Entity. *(reading just file is ok!)*

Finally, when you resolve anything you must preserve it's characteristics in order to know what you are trying to resolve:

```lua
/*
 preserves Context Entity Scope
 (static to file - no need for Resolution Intent - implicit)
 which is just a named thing
*/
anyEntityUsed

/*
 () preserves Context Function Scope
 (static to file - no need for Resolution Intent - implict)
 which is a named thing surrounded by ()
*/
(anyFunctionUsed)

/*
 [] preserves Object Entities Scope
 (not static to object Context - needs Resolution Intent - explit)
 which is a named thing surrounded by []
*/
anyObject.[anyEntityUsed]

/*
 () preserves Object Functions Scope
 (not static to object Context - needs Resolution Intent - explit)
 which is a named thing surrounded by ()
*/
anyObject.(anyFunctionUsed)
```

In Wide Intentions must be clear!

### Object static scope

As the file hides `{}` using Isolation to preserve side-effects, so does objects:

```lua
.Thing <
`{` -- locally implicit
  -- This is an ordinary Entity, so it's static
  do: true  -- No .[]

  -- This is an ordinary Function, so it's static
  (doSomething): -- NO .()
    do ? "Do something!"
`}` -- locally implicit
/>
```

The `.` Resolution Intent were removed from Entity and Function Object, what now?

Angry Birds mode turning on...

```lua
Thing.do
Thing.(doSomething)
```

🤣 I'm with you in this hard moment of your life!

Why not make everthing accessible this whey?

Now the Resolution Intent is using "Thing" Object in its own Context and like in the file Context you can access the ordinary Entity and Function like that. But as the ordinary Function has () in its name, you can't use just `Thing.doSomething` because it would imply that it is an Entity not a Function.

```lua
.Thing <
  .[do]: true

  .(doSomething):
    .do ? "Do something!"

  -- a resolvable Object Function that returns a new Thing
  .(new) Thing: <Thing/>

  -- static Entity that returns a Lambda that returns a new Thing
  new: (): <Thing/>

  -- static Entity of type Lambda that returns a Lambda that returns the return of local (new) Function
  new:() = (): .(new)
/>

`.(new) Thing: <Thing/>`
thing: Thing.new -- lazy
thing.(doSomething)

`new: (): <Thing/>`
thing: (Thing.new)
thing.(doSomething)

`new:() = (): .(new)`
thing: Thing.(new)
thing.(doSomething)
```

That moment when I realized I'd have to call it **Object Intent Programming** to not set the world of programming apart!

Well, you can go the best way you want! Your choice!

### Object Internal Grouping

When you have multiple Meta Entities you can just group them:

```lua
.Thing <
  .[
    entityOne:bool,
    entityTwo:bool,
    entityThree: bool
  ]

  ..[
    entityFour:bool,
    entityFive:bool,
    entitySix: bool
  ]

  #[
    entitySeven:bool,
    entityEight:bool,
    entityNine: bool
  ]
/>
```

### Extent Objects

They are objects that you create to use in other Object Entities and you can't resolve them directly.

You can only use one Extent Object when creating Resolution Objects.

You can use several Interfaces and Traits when creating Resolution Objects as you will see soon.

You create Extent Objects using `..` before its name:

```lua
..Thing</>
.SomeThing ..Thing </>

thing: <Something/> -- Ok,  no problem!
thing: <Thing/> ❌ -- Error you cannot resolve Extent Object Thing
```

Notice that `Thing` object now uses 2 `..` not 1 `.`!

### Access Transparency

Every object can have 4 ways for you to access them called:

- static *(in Isolation Intent - has no symbol - and doesn't preserve scope characteristics)*
- public *(using `.` preserves scope characteristics)*
- protected *(using `..` preserves scope characteristics)*
- private *(using `#` - local to object)*

⚠️ It made sense keep the OOP jargons for me because I didn't want to change the World of programming by calling them like:

- contextual (*static*)
- resolvable (*public*)
- extendable (*protected*)
- individual (*private*)

But if you like to promote hate you can call'em like so!

```lua
.Thing <
  count:int -- static
  .[name]:string -- public
  ..[value]:obj -- protected

  #[instance]:Thing -- private

  (count) int: count -- static
  .(name) string: .name -- public
  ..(value) obj: .value -- protected
  #(instance) Thing: .instance ?. <Thing /> -- private
/>

-- Thing is extended by Something
.SomeThing ..Thing </>
```

In the above example Something becomes:

```lua
.SomeThing <
  count:int
  .[name]:string
  ..[value]:obj
  `#[instance]:Thing` -- not extended

  (count) int: count
  .(name) string: .name
  ..(value) obj: .value
  `#(instance):Thing` -- not extended
/>
```

As you can see only the `#instance` Entity and `#(intance)` wasn't extended.

Somethings to notice:

**#1**
Static Entities or Functions are accessed without `.` Intent.

**#2**
Non-static Entities or Functions are accessed with only one `.` Intent independent of their Scopecharacteristic (`.`,`..`,`#`).

**#2**
When used inside an Object `.` Intent means both *self* but not *static*.

**3**
Entities and Function can have the same name.

### Constructor Object Lambdas

Objects can have constructors that behaves as an Object Lambda.

The concept of **Constructor/Lambda Promotion** can be used, and when done the Entities you created inside the Object Lambda become Meta Entitities of the enclosing Object.

You must pass the Accessor to mean you want to promote.

Entities without the Acessor won't become Meta Entities and must be used just like ordinary parameters.

The most basic Object Lambda Looks like so:

```lua
.Thing <()/>

thing: <Thing () />
```

With NOT promoted Entities:

```lua
.Thing <
  (
    entityOne:bool,
    entityTwo:bool,
    entityThree:bool
  ):
    /*
     you should have a body when
     using NOT promoted Entities
     since it will make no sense just using them
    */
    entityOne ? "Do One thing"
    entityTwo ? "Do Two thing"
    entityThree ? "Do Three thing"
/>

thing: <Thing (true, true, true) />
```

When NOT promoted parameters are used you can also segment it:

```lua
.Thing <
  (...params:int ):
    ~(param : params) :
      "{param}"
/>

thing: <Thing (1, 2, 3, 4)>
```

```lua
.Thing <
  (
    .do:bool, -- Has Acessor, is promoted to Meta Entity
    ..what:string, -- Has Acessor, is promoted to Meta Entity
    #when:string = "Never!", -- Has Acessor, is promoted to Meta
    nothing: false, -- Has NOT, is NOT promoted
  ):
    nothing ? "Doing nothing"

  .(doSomething):
    .do ? "{.what} will be done {.where}"
/>

thing: <Thing (do: true, what: "Something", nothing: true )/> -- Doing nothing
thing.(doSomething) -- Something will be done Never!

thing: <Thing (do: true, what: "Something")/>
thing.(doSomething) -- Something will be done Never!

thing: <Thing (do: true, what: "Nothing", when: "Always!")/>
thing.(doSomething) -- Nothing will be done Always!
```

With all you know until now, can you guess `()` means?

But you can make explict you intentions and separate constructor entities:

```lua
.Thing <
    #(when:string = "Never!")
    .(do:bool)
    ..(what:string)

    -- Object Function
    .(doSomething):
        .do ? "{.what} will be done {.where}"
    .
/>
```

It's like Function declarations without ending `:` Type Intent.

### Abstract Extent Objects

If want to just blueprint an Object's Intents that provides or not some default behaviour you can abstract placing a `!` Not Intent before the Object's name, its Entities and/or Functions.

Protected, Public, Static Entities and Functions can't be abstracted and just used inside the abstract extent content.

```lua
-- Notice that ".." turned ".!"
.!Thing <
  -- static Entity cannot be abstracted but used in context
  thingName: "Thing"

  -- Notice that "." turned "!"
  ![name]:string

  -- Notice that "." turned "!"
  ![instance]:obj

  -- static Function cannot be abstracted but used in context
  (thingName): thingName

  -- Notice that "." turned "!"
  !(instance) Thing: -- abstract Function doesnt have body

  .(name) string:
    : .name ?. (thingName) -- resolvable Function can have body
/>
```

❌ If you don't provide implementation for everything marked as `!` Wide will break with an error.

This is how Something will look after abstracting an Extent:

```lua
.SomeThing .!Thing <
  -- Notice that now "!" turned "."
  .[name]:string = "Something"

  -- Notice that now "!" turned "."
  .[instance]:Something = </>

  -- Notice that now "!" turned "."
  .(instance): .instance

  -- Notice that now "!" turned "."
  .(name) string: -- not abstract Function can be modified
    : .name ?. "How is it possible for me not having a name?"
/>
```

### Interfaces

Interfaces are usable Objects with empty Functions. You can use them in other Objects. Once used you are forcebly required to implement their Functions' bodies in the Object they are used.

An Interface can use one or more other interfaces.

Interfaces can define constants literals, Meta Entities and Functions for objects.

```lua
:Speaker <
  .(speak):
/>

:Mover <
  .(move):
/>

-- Tuple is used to compose.
:TalkingMover :(Speaker, Mover) <
  .[name]: string -- assignable property via interface
/>
-- same as
:TalkingMover :Speaker :Mover </>
```

To use in Classes just compose and implement Interface's Functions:

```lua
.Person :Speaker <
  .(speak):
    "Shit!"
/>

.Robot :(Speaker, Mover) <
  .(speak):
    "Bits and Shits!"

  .(move):
    "Shifting bits >>>>>"
/>

.TalkingCar :TalkingMover <
  .[name]: "Talking Car"

  .(speak):
    "Beep beep!"

  .(move):
    "Rolling tyres..."
/>
```

### Traits

Traits are Object that can be used to give Objects new characteristics (traits).

You can use as many traits as you want!

Traits can use interfaces.

Traits can not use Objects.

```lua
::Hello <
  .(sayHello):
    "Hello "
/>

::Wide <
  .(sayWide):
    "Wide!"
/>
```

You can use like:

```lua
.HelloWide <
  ::(Hello, Wide) -- use tuples to group
  -- Or individually
  `::Hello`
  `::Wide`

  .(exclamation): "!"
/>

obj: <HelloWide/>
obj.(sayHello)
obj.(sayWide)
obj.(exclamation)
```

**Resolving Conflicts**

```lua
::A <
  .(smallTalk): "a"
  .(bigTalk): "A"
/>

::B <
  .(smallTalk): "b"
  .(bigTalk): "B"
/>

.Talker <
  ::(A, B) { -- Remember the Context to create a new Scope? Here it is explicitly!
    -- you just alias it with the name of the other Trait and Wide imply it!
    B.(smallTalk): A`.(smallTalk)`, -- you don't need to write down .(smallTalk)
    A.(bigTalk): B`.(bigTalk)` -- you don't need to write down .(bigTalk)
    -- if you alias and that's not a Trait, it will be used
    B.(bigTalk): `B.(`talk`)` -- you just write talk
  }
/>
```

You can change Trait's visibility:

```lua
.Talker <
  ::(A, B) {
    B.(smallTalk): B.., -- just change the Accessor
    A.(bigTalk): A# -- just change the Accessor
  }
/>
```

You can mix conflict resolution and aliasing

```lua
.Talker <
  ::(A, B) {
    B.(smallTalk): A..`(smallTalk)`,
    A.(bigTalk): B#`(bigTalk)`
    B.(bigTalk): `B`#(talk)
  }
/>
```

⚠️ Traits allow abstract Functions like Abstract Extent Objects.
⚠️ Traits allow static Static Entities and Static Functions

### Enums

```lua
-- Numeric enum
#StatusCodes {
  OK: 200
  BadRequest: 400
  Unauthorized -- Auto-incremented to 401
  NotFound: 404
}

requestStatus: StatusCodes.OK

-- String enum
#CardinalDirections <
  North: "North"
  East: "East"
  South: "South"
  West: "West"
/>

currentDirection: CardinalDirections = CardinalDirections.East

-- Heterogeneous enum (must explict with Generics))
#MixedValues{string|int} <
  StringValue: "string"
  NumberValue: 1
/>

(handleResponse code: StatusCodes):
  code?
    StatusCodes.OK:
      -- Handle successful response
    StatusCodes.NotFound:
      -- Handle resource not found
    -- ... other cases

```

### Structs

A struct is a user-defined data type that groups Entities of potentially different types into a single unit. It is similar to an Object, but with the key difference that its members are public by default.

It's not an Object `</>` so it doesn't uses it.

```lua
Point {
  x: int
  y: int
}

Person {
  name: string
  age: int
  address: string
}

Car {
  brand: string
  model: string
  year: int
}
```

Structs can be used anywhere as a Type for an Entity, and even for other structs:

```lua
Point {
  x: int
  y: int
}

point: Point = {10, 20}
-- or
point: Point{10, 20}

Rectangle {
  topLeft: Point
  bottomRight: Point
}

rectangle: Rectangle{
  Point {0, 0},
  Point {100, 100}
}

rectangle: {
  Point {0, 0},
  Point {100, 100}
}
```

## Generics

In Wide Generics are closely related to the Scope characteristics like you learned before.

You create Generics in Wide using `{}` Context Intent, because guess what? - you are gonna change that!

You can pass the Type you want to resolve to a Function or Object of any kind.

```lua
(calculateAverage{T} A:T B:T) T: (a + b) / 2

a: 32
b: 50
average: (calculateAverage{int} a, b)

c: 4.5
d: 10.3
average: (calculateAverage{float} c, d)

❌ -- This would fail
average: (calculateAverage{int} a, c) -- int and float are not the same
```

```lua
.Calculate{T}<
    .(average A:T B:T) T: (a + b) / 2
>

calculator: <Calculate {int} />
a: 32
b: 50
average: calculator.(average{int} a, b)

c: 4.5
d: 10.3
average: calculator.(average{float} c, d)

❌ -- This would fail
average: calculator.(average{float} a, c) -- int and float are not the same
```

```lua
.Stack{T} <
  #[stack]: []T

  .(push item: T):
    .stack.(push item)
/>

numberStack: <Stack{Int}/>
stringStack: <Stack{string}/>

aString: "A String"
aNumber: 100
aPerson: <
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
/>

stringStack.(push aString)
numberStack.(push aNumber)

❌ -- These would fail!
numberStack.(push aPerson)
numberStack.(push aString)
stringStack.(push aPerson)
stringStack.(push aNumber)

```

Multiple type parameters can be defined within the angle brackets {} when declaring a generic function, interface, trait, enum, struct or object. Each type parameter represents a distinct type that can be specified when the generic is used.

```lua
(processData{T, U} input1: T, input2: U) T, U :
  : [input1, input2]

result: (processData<int, string> 10, "hello") --  result is of type [number, string]
```

Union types (|) allow a generic type to accept values of different types. This is useful when a function or component needs to handle a variety of input types.

```lua
(handleInput{T} input: T) T -- next line continues
  // T: string | int:  -- `//` here means "Where"
  : input

strResult: (handleInput "world") -- strResult is of type string
numResult: (handleInput 20) -- numResult is of type int
```

Intersection types (&) combine multiple types into one, requiring a value to satisfy all the specified types. This is useful when a generic type needs to have properties or methods from multiple types.

```lua
:HasName <
  .[name]: string
/>

:HasAge <
  .[age]: int
/>

(processEntity{T} entity: T) string
  // T: HasName & HasAge:
  : "{entity.name} is {entity.age} years old"


person: = <
  name: "John",
  age: 30
/>

message: (processEntity person)
```

Type constraints can be used with generics to specify that a type parameter must extend a certain type or implement an interface. This ensures that the generic type has the necessary properties or methods.

```lua
:Printable <
  .(print):
/>

(printItem{T: Printable} item: T):
  item.(print)

.Document :Printable <
  .(print):
      "Printing Document"
/>


doc: <Document/>
(printItem doc)
```

## Attributes in Wide Language

In Wide, **attributes** are metadata-like constructs that can be applied to functions, meta entities, objects, and more — very much like annotations in other languages. But unlike traditional attributes, they are full-fledged **objects** in Wide, with support for inheritance, traits, macros, and default parameters.

Wide attributes are not just markers — they're living pieces of logic you can reason with.

### Attribute Binding in Wide

Wide supports annotations (called **attributes**) using a concise and composable syntax.

Attributes are declared using `@{}` Intents and contain one or more calls to functions and/or objects:

```lua
@{
  (route path: "/aircraft/{id}")
}
(show id:int) View : "..."
```

```lua
.Book<
  @{
    (belongsTo localKey:'author_id')
  }
  .[author]:Author

  @{
    (belongsTo localKey:'collection_id')
  }
  .[collection]:BookCollection
/>
```

### Multiple Attributes

You can chain multiple attributes inside the same block:

```lua
.Book<
  @{
    (belongsTo localKey: "author_uuid"),
    (inverse inverseKey: "uuid")
  }
  .[author]:Author
/>
```

### Attribute Inheritance

Attributes can inherit from one another using `:` or `::` just like other constructs:

```lua
:HttpRouteAttribute<
  [.path]:string
/>

:GetRoute :HttpRouteAttribute<
  .[method]: "GET"
/>

.BookController <
  @{
    <GetRoute path:"/books" />
  }
  .(listBooks):
    -- list books...
/>
```

This allows base metadata behaviors to be reused and extended without duplication.

### Default Values in Attributes

Attributes support **default parameter values**, making them easier to use:

```lua
.Logged <
  .[required]: true
  .[roles]: ["user"]
/>

@{
  <Logged />
}
(viewDashboard)

@{
  <Logged required:false, roles:["guest"] />
}
(previewDashboard)
```

### Traits and Composition in Attributes

Since attributes are objects, they can **implement traits** or even **use other attributes** internally:

```lua
::Auditable<
  .(auditLog message:string) : "..."
/>

:AuditAttribute :Auditable<
  .[logLevel]:"INFO"
/>

@{
  <AuditAttribute logLevel:"DEBUG" />
}
(deleteItem)
```

This enables **modular attribute logic** through traits.

## Attributes and Macros

Attributes can pair with **compile-time macros**, injecting logic or altering behavior at compile time:

```lua
@{
  <AutoToString />
}
<Person />
```

Use cases include:

- Auto-generating methods (e.g., `(toString)`)
- Validations (e.g., required fields)
- Dependency injection markers

### Pipe Intent

Pipe operator in wide is `>>` with is itself an Intent.

```lua
userInput: [12 7 9 33 8]

result: userInput
  >> .(filter) (n): n % 2 = 0
  >> .(map) (n): n * n
  >> .(sum)
```

In the above example the pipes were used with a built-in List `[]` that implements all those Functions.

The `.` Resolution Intention knows that `>>` Pipe Intent, but if Wide had a resolvable Object called "List", the previous example would be the same like:

```lua
userInput: [12 7 9 33 8]

result: userInput
  >> List.(filter) (n): n % 2 = 0
  >> List.(map) (n): n * n
  >> List.(sum)
```

What indeed is internally is like this:

```lua
userInput: [12 7 9 33 8]

result: userInput
  >> [].(filter) (n): n % 2 = 0
  >> [].(map) (n): n * n
  >> [].(sum)
```

⚠️ Don't use []! It's ugly and unnecessary!

You can go Async with Pipes:

```lua
@(
  (fetchURL "https://example.com/api/data")
  >> (parseJSON)
  >> (filter isValid)
  >> (map extractName)
  >> (saveToDB)
)
```
