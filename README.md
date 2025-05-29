**🤡 WARNING: This file is a hot mess and will embarrass me in public.**

***⚠️⚠️⚠️ This is a draft illustrating potential syntax, not a beginner's tutorial. There is no current implementation; it's a preliminary concept open to feedback. This syntax may evolve based on your input, and there's no guarantee of future implementation. I'm gathering opinions and constructive criticism to assess its viability. Feel free to share this link with AI language models for syntax validation. This is envisioned as a web-first language. I'm an independent developer exploring potential solutions, not promoting a product or representing a large corporation. Wide prioritizes its own design principles and is not tied to any programming language. Ultimately, Wide aims to extend HTML functionality as full programming language.***

# 🧩 Wide Language

```html
<!-- hello.wide.html -->
()=> {
  greet() => <p>"Hello, {name}!"</p>
}

<!-- html wide is used to say it must be parsed as Wide -->
<!DOCTYPE html wide>
<html>
  <body>
    <h1>{ greet("World") }</h1>
    <p>HTML first language!</p>
  </body>
</html>

<!-- output -->
<!DOCTYPE html>
<html>
  <body>
    <h1>Hello, World!</h1>
    <p>HTML first language!</p>
  </body>
</html>
```

Welcome to **Intent-Oriented Programming**.

Wide is a symbol-based, declarative, paradigm-unifying programming language designed to feel natural, composable, and deeply readable just using symbols you already know.

It doesn't have keywords (at least not for aliased types).

It lets **humans speak logic** — cleanly, expressively, and across paradigms.

Wide isn’t just about code — it's about communication.

It's about intent — and Wide delivers it.

## Introduction

Wide is a keyword-less, intent-driven programming language inspired by years of experience across many real-world languages and the Web.

Its design takes direct cues from:

- HTML — for its wide used markup on the Web
- CSS — for its abstract way of selecting elements
- Python — for its clean syntax and readability-first philosophy
- Go — for its simplicity and strong opinions on structure
- Rust — for its safety, scope-aware semantics, and move-inspired modeling
- TypeScript — for its balance between strong typing and developer ergonomics
- PHP — for its pragmatic web-oriented roots and fluid development style
- OCaml — for its functional purity, immutability-first mindset, and algebraic type inspiration
- C++ — for its deep control over memory, compile-time power, and fine-grained expression of intent

Wide doesn't try to copy them — it extracts the intent behind them, strips away the noise, and rebuilds a language model based purely on semantic clarity, symbolic consistency, and developer expression.

### Why Wide?

- Web ready!
- No keywords — only symbols that express intent
- Immutable by default, reactive when needed (`$`, `@`)
- Real functions and lambdas with context inclusion
- Strong types, simple syntax
- Built-in support for UI, iteration, async, and error control

## Opinions and Criticism

This document is designed to grab Opinions and Criticism about Wide.

Be aware the the syntax presented here is just what makes its basics up until now and may change in the future.

I cannot assure I'm the best communicator in the world nor here in the draft, but I can assure I just wanna create a better place for everyone!

## HTML in its core

Wide was born from the need to universalize HTML and make it a full and reactive programming language! React itself did a great job in putting HTML as a layer inside a Javascript library, and I could get a lot of ideas from the last 10 years fighting it when using Node.JS and just wanted to use it server-side. So I said to myself: Why not a language that speaks the web, so that any language could transpile itself into Wide and be itself a programming language?

That's why Objects in Wide are <> and </> symbols, because in Wide you can do this when going HTML mode:

```html
<!-- looping.wide -->
() => {
  <ul>
    <~(counter <= 10)>
      <li>
        counter == 1 ?
          <span class="one">
            "{ counter } is one"
          </span>
        counter == 2 ??
          <span class="two">
            "{ counter } is two"
          </span>
        counter == 3 ??
          <span class="three">
            "{ counter } is three"
          </span>
        . <span class="another">
            "{ counter } is another"
          </span>
      </li>
    </>
  </ul>
}
```

But if you were just vanilla Wide cli you could do just so:

```lua
() => {
  ~(counter <= 10) {
    counter == 1 ? "{ counter } is one"
    counter == 2 ?? "{ counter } is two"
    counter == 3 ?? "{ counter } is three"
    . "{ counter } is another"
  }
}
```

## Symbols and keywords

Wide has no keywords. Just some symbols to represent **Intent**. But some types maybe aliased. That can make the language portable from people coming from other languages.

## Intents

Wide is strongly typed and it uses this new concept called **Intent**.

**Intent** means the state of mind and/or desire when people create code.

Intent is mainly just a language concept, not to be used in daily jargon, but if you wish, you can.

There are 2 most fundamental intents.

### `:` Type Intent

Whenever you see the Type Intent `:` (colon symbol) you can think:

- it has type
- it checks type
- it implies type
- it assigns type
- it defines type

### `=` Assignment Intent

Whenever you see the Assignment Intent `=` (equal symbol) you can think:

- it assigns a value *(of, from or constant of)*

----

## Entities

From that you cansee how stated is managed in Wide.

Everything you can name in Wide is called an Entity.

E.g.:

```lua
name:string = "Amadeus Mozart"
```

The value of the `name` Entity is of type text `"Amadeus Mozart"`.

If reused the same name of an entity, the previous value will be **shadowed** and no longer exists after that point in code.

```lua
name:string = "Amadeus Mozart"
name:string = "Antonio Vivaldi"
```

Above there exist 2 distinct Entities but the first has to die in order the last to live!

You can't do this:

```lua
name:string = "Amadeus Mozart"
name = "Antonio Vivaldi" ❌ Error: Immutables can't be reassigned
```

But you could've done so:

```lua
name:string = "Amadeus Mozart"
name:= "Antonio Vivaldi"
```

That says the compiler to infer the type again.

When shadowing you can change the type.

```lua
number:int = 1
number:string = "One"
```

### `:=` Infer Intent

Whenever you what the compiler to infer the type, you must join intents `:=` together to intent inference.

```lua
number:= 1
name:= "Alice"
isActive:= false
salary:= 9999.99
```

You might be thinking that you can't change an Entity's value in Wide, and it's another FP boring language. But you can! When dealing with side-effects that's something you can't avoid.

⚠️ You will learn how to handle **Mutable Entities** and **Constant Entities** as you will see later.

----

## Built-in Data Types - Type-Values

Wide has a different core data Type built to be aliased called **Type-Values**.

It's built-in core Type-Values looks like this:

| Type-Value | English Alias | Examples |
|:---:|--------|--------|
| ? | bool (1: true, 0: false ) | true/false, yes/no, on/off |
| '' | char  | letter 'A', number '1', symbol '$' |
| "" | string  | "hello", "sweet potatoes", "How are you?" |
| 0.0 | float | 20.5%, -5.6°C, 10.9km |
| 0.00 | double | Pi(π)3.14159265358979323846, -23.5505200 lat, -46.6333094 lng |
| 0 | int | -1, 0, 1 |
| 00 | uint | 1, 2, 3 |
| 08 | i8 | -128, 0, 127 |
| 08+ | u8 | 0, 255 |
| 016 | i16 | -32_768, 0, 32_767 |
| 016+ | u16 | 0, 65_535 |
| 032 | i32 | -2_147_483_648, 0, 2_147_483_647 |
| 032+ | u32 | 0, 4_294_967_295 |
| 064 | i64 | -9_223_372_036_854_775_808, 0,  9_223_372_036_854_775_807 |
| 064+ | u64 | 0, 18_446_744_073_709_551_615 |
| 0128 | i128 | -170_141_183_460_469_231_731_687_303_715_884_105_728, 0, 170_141_183_460_469_231_731_687_303_715_884_105_727 |
| 0128+ | u128 | 0, 340_282_366_920_938_463_463_374_607_431_768_211_455 |
| () | fn \| lambda | add(), subtract(), print(), click()  |
| <> | obj | Person, Vehicle, Dropdown, Box, Header, Provider |

Their Intent is both the type and the value they default to,
with exception to the Boolean `?` and the Object `<>`, most values mean exactly what they read.

Yes, the name of the type is that internally.

In wide you can create a **Custom Type** opening a context or not and where to place it and just naming it and prefixing with the `:` Type Intent:

```lua
:string
```

But that would serve no purpose! It's lost in the vaccumm of nonsense!

For core Wide **Type-Values** you can give it the aliasesname you want them to be:

```lua
?:bool
'':char
"":string
0:int
0+:uint
08:i8
08+:u8
016:i16
016+:u16
032:i32
032+:u32
064:i64
064+:u64
0128:i128
0128+:u128
0.0:float
0.00:double
<>:obj
():fn
```

⚠️ That's Wide's own Aliased Type-Values.

You can also create custom aliases assigning a type-value with the `=` Assignment Intent to a custom type, so Wide's own type aliases could be done like so.

```lua
:bool = ?
:char = ''
:string = ""
:int = 0
:uint = 0+
:i8 = 08
:u8 = 08+
:i16 = 016
:u16 = 016+
:i32 = 032
:u32 = 032+
:i64 = 064
:u64 = 064+
:i128 = 0128
:u128 = 0128+
:float = 0.0
:double = 0.00
:obj = <>
:fn = ()
```

You can also even alias from an already existing type aliased:

```lua
:Text = string
```

⚠️ As you'll learn in Objects section, Types are close cousins to Interfaces and they can beautifully implement each other!

Besides not having keywords in its syntax, some words are impossible to avoid when talking to types, and that would turn Wide impossible to work with. As you can **alias** types, and in order to help newcomers and professionals with parity with other languages, Wide has those built-in aliases for them in plain English.

You can also alias type values, but currently just `?` Boolean type has it:

```lua
?:bool {
  0:false
  1:true
}

-- or using assignment

:bool = ? {
  :false = 0
  :true = 1
}
```

Those words are not syntax, they are plain English words the compiler knows by default they were aliased and performs type lowering at compile-time.

You can rename them at any time just using the core Wide types from the previous table and examples or from already English aliased types.

For you to better understand, ***Wide is made in Brazil***, so types could be aliased like so:

```lua
?:booleano {
  0:falso,
  1:verdadeiro
}
'':caractere
"":texto
0:inteiro
0.0:flutuante
0.00:real
():funcao
</>:objeto
```

Or like so using assignment:

```lua
:booleano = ? {
  :falso = 0
  :verdadeiro = 1
}
:caractere = ''
:texto = ""
:inteiro = 0
:flutuante = 0.0
:real = 0.00
:funcao = ()
:objeto = </>
```

⚠️ Wide is able to understand both English and Portuguese alias in this case because it won't cancel the previous English ones.

⚠️ Just remember that you don't need to give aliases to the core Wide Type-Values presented before.
The compiler was provided with them for you convenience.

### Notes on Boolean Type

It is important to notice that when you use Bool Type-Values `0` or `1` you are not using Integer Type-Values like `1`, `0`, `-1`, `100`. That's why you must explicity type your Entities of type Bool.

So you can't do Math like so:

```lua
boolEntity:bool = 1
intEntity:int = 1

sum:= boolEntity + intEntity ❌ -- Error: Cannot Add bool to Integer
```

If you remove `:bool` from boolEntity the compiler will infer that is an Integer.

```lua
boolEntity:= 1
intEntity:int = 1

sum:= boolEntity + intEntity ✅ -- sum value is 2
```

But as you'll see later, you can type cast a value by using `:type` attached to the entity when using it:

```lua
boolEntity:bool = 1
intEntity:int = 1

sum:= boolEntity:int + intEntity ✅ -- sum value is 2 -> 1 + 1

boolEntity:bool = 0
sum:= boolEntity:int + intEntity ✅ -- sum value is 1 -> 0 + 1

```

⚠️ Notice that `boolEntity:int` did the trick here.

You can't turn other type into Boolean however!

```lua
intEntity:int = 1

intEntity:bool ? "True" . "False" ❌ -- "Error: Cannot cast as boolean
```

### Rules for Aliasing

When creating aliases you can't create them anywhere.

They must be in the first lines of code if there are no imports, or int the first lines of code after the imports if there are imports.

So, they can't be created inside the Entry function nor elsewhere. This is because the Compiler must know before-hand the types were aliased.

You can create a Wide file called `.aliases` and place it in the root of your project as well. Just copy and paste them inside it, and you are ready to go.

## Entry function

You haven't been presented to them yet, but Wide has an entry function - more properly a lambda - that signs to the compiler where to start the file first execution entry point.

That's like so:

```lua
() => {

}
```

Whatever you place before it is structural code that you can reuse inside the Entry function.

⚠️ When you see `{}` anywhere its very Intent is to bind itself as a **context** for anything. It's called **Context Intent**. A context can be used to create different things, but you don't need to memorize them all as you learn, they'll get so implicit into your head that you will understand them as you go.

⚠️❌ From now own, other than very specific, the Entry Function may not be used for fragment code samples.

This is how you would do that for `:string` custom type presented previously:

```lua
:myString = ""
:Text = string
:MyText = myText

() => {
  name:string = "Alice"
  name:Text = "Alice"
}
```

## Printing on Screen

That seems nice, but how do you print on screen?

To print on screen you just enclose what you want to print inside double quotes `""` alone in a single line and depending on were you are running wide it will be printed.

```lua
() => {
  "Hello, Wide!"
}
```

That will output:

```text
Hello, Wide!
```

⚠️ Yes! There's no need for any function, macro or any voodoo! The `""` is the syntax that does that magic itself if put it alone in a single line or passed alone when Questioning values.

If you need to print `""` double quotes inside a string you can use 2 pairs double quotes:

```lua
() => {
  ""Hello, "Wide"!""
}
```

That will output:

```text
Hello, "Wide"!
```

But when you use call a Function, you must use a placeholder:

```lua
greet(name:string) => "Hello, {name}"
"{}", greet("World") -- Hello, World!
```

### Printing Multiple lines

When printing multiple lines you can use `\` character to ignore line break, or just break the line to include line break.

```text
() => {
  "
  This is paragraph 1.\
  This is paragraph 2.\
  This is paragraph 3.
  "

  "\
  This is paragraph 1.\
  This is paragraph 2.\
  This is paragraph 3.\
  "
  "
  This is paragraph 1.
  This is paragraph 2.
  This is paragraph 3.
  "
}
```

The first will print the tab before the first paragraph and a new line with a tab:

```text
  This is paragraph 1. This is paragraph 2. This is paragraph 3.
  -- tab and line here!
```

And the second will print the 3 paragraphs inline and no empty line nor tabs:

```text
This is paragraph 1. This is paragraph 2. This is paragraph 3.
```

And the last will print a tab before every paragraph and a new line with a tab:

```text
  This is paragraph 1.
  This is paragraph 2.
  This is paragraph 3.
  -- tab and line here!
```

### Interpolation

You can use curly braces inside those quotes `"{}"` to dinamically output values inside text output or just to compose dynamic strings of text:

```lua
() => {
  name:= "Wide"
  "Hello, {name}!"

  price:= 9.99
  "It's ${price}."
}
```

Those lines will output:

```text
Hello, Wide!

It's, $9.99.
```

You can also just use {} as placeholders and pass a list of values you want to place in them:

```lua
() => {
  name:= "Wide"
  "Hello, {}!",  name

  price:= 9.99
  "It's ${price}.", price


  "Hello, {}. This hot-dog costs ${}", name, price
}
```

When using multiple placeholders you can align them in multiple lines:

```lua
name:= "Alice
age:= 34
occupation:= "Wide Developer"
salary:= 99999.99

"\
Employee {} is {} years old. \
Occupies the hole of {}. \
And makes ${}.\
",
name,
age,
occupation,
salary
```

### Printing Entity Type

Wheneven you wanna know the type of an Entity you enclose the Entity name with `:` and you can get its string type name:

```lua
() => {
  number:= 10
  name:= "Alice"
  isActive:= true

  "{:number:}" -- int
  "{:name:}" -- string
  "{:isActive:}" -- bool

  "{}", :number:
  "{}", :name:
  "{}", :isActive:
}
```

### Printing Entity Name

Wheneven you wanna know the name of an Entity:

- `:<ENTITY>:` prints the string name of an Entity
- `::<ENTITY>::` prints the string name of the value of an Entity in case it's been aliased.

```lua
() => {
  number:= 10
  "{:<number>:} value is {number}" -- number value is 10
  "{} value is {}", :<number>:, number


  name:= "Alice"
  "{:<name>:} is {name}" -- name is Alice
  "{} is {}", :<name>:, name

  isActive:= true
  "{:<isActive>:} is {isActive}" -- isActive is 1
  "{:<isActive>:} is {::<isActive>::}" -- isActive is true

  "{} is {}", :<isActive>:, isActive
  "{} is {}", :<isActive>:, ::<isActive>::
}
```

## Immutable, Mutable, and Constant Entities

In wide everything you name is an Entity. That includes Functions, Objects, Interfaces, Traits, Enums, Structs, Attributes, etc.

When talking about Entities you might read just Immutable, Mutable or Constant not having the need to write down nor say "Entity".

There will be cases when the word Entity will be ommited on purpose.

When you create an Entity you can say it's at **Birth** state.

### Notes on "Variables"

Some people say that there's not such a thing like Immutables and Mutables, that they are all "variables" at the end, and that Wide can't call'em "Entities"

Yes, at the end - in Assembly that's true.

But wide is not Assembly, right?

Wide is a high-level programming language that has Mutables that behave like variables and you can change them, so they are like variables.

So you can't say that Entities are themselves variables.

### Immutable Entities

By default Entities are immutable unless you sign it with `$` State Intent.

```lua
name:= "John"
age:= 34
salary:= 10000.00
```

Which mean they can't change their state (inner value).

You can't create Immutable Entities in Wide that doesn't have an initial type or value.

```lua
name:=
age:=
salary:=
```

Notice that there's no intent in the code. What's the type? What's the value? If you try to do so you'll get a compiler error and you will have to fix it.

And now is it ok?

```lua
name: string
age: float
salary: double
```

Yes, but it makes no sense if you never assign them a value and just use the default provided by the type system! If you try to do so, you'll get a compiler warning and this code will be removed by the compiler if not used.

You can create a new Entity with the same name by **Shadowing** it, but the previous one will cease to exist in order for the new to live.

Besides that you can also change the initial type when shadowing:

```lua
value:= 123   -- integer
value:= "Alice" -- string
```

But remember, you can't reassign Immutables:

```lua
value:= 123
value = "Alice" ❌ -- Error: Entity value cannot be reassigned
```

Once born an Immutable Entity won't ever change even when you shadow it. What happens it that you say the compiler to dispose that Entity from that point and use the same name for a new one. No memory address is shared!

### `$` State Intent

When you see it the State Intent `$` (dolar symbol) you may say:

- it can mutate
- it can change *(something)*
- it has state *(value)*

Wide has no concept of `null`, `nullptr`, `nil`, `void`, `None` nor `Option` exposed to you because it is implicit when you want to change anything in Wide.

It's possible because every entity in Wide has sorta default state — which makes it always valid, but not necessarily assigned to a value.

As you'll see later, you just need to check against that!

### Mutable Entities

If you want to be able to change an Entity's state, you can create it as a **Mutable Entity** by  prefixing its name with the `$` State Intent.

```lua
$name:= "John"
$age:= 34
$salary:= 10000.00
```

The same rules of assignment for Immutable Entities also apply here:

- You can't create entities without types and values
- You shoudln't create entities that won't be used

But the main obvious difference is taht you can change their values!

```lua
$name:= "John"
$age:= 34
$salary:= 10000.00

$name = "Mary"
$age = 58
$salary = 20000.00
```

Did you notice that you don't use the `:` Intent to assign a new value, just the `=` Assignment Intent? That's how you assign or reassign values on Mutables.

To print them, you don't need to pass the `$` symbol, but you can if you want to enforce that that's a Mutable.

```lua
$name = "Mary"
$age = 62
$salary = 20000.00

"{name} is {age} old. Salary: {$salary}"
```

#### Note

In Wide, the core assignment system uses only two forms:

| Symbol | Intent     | Meaning                                    |
| ------ | ---------- | ------------------------------------------ |
| `:=`   | **Birth**  | Infer Intent: defines, redefines, or shadows |
| `=`    | **Growth** | State Intent: reassigns an existing entity |

Wide uses `=` for any assignment after Entity Birth.

Whether the entity is mutable or just not yet initialized — you are saying: "Now you are ready to take a value."

### Grouped Entities

Whenever you want to define multiple Entities, you can just group them altogether.

Doing so will also create a Homogeneous Record as you'll see.

```lua
n1:int
n2:int
n3:int

n4:float
n5:float
n6:float

first:string
last:string
```

Same as:

```lua
{ n1, n2, n3 }:int

{ n4, n5, n6 }:float

{ first, last}:string
```

You can assign values as well:

```lua
{ n1 = 1, n2 = 2, n3 = 3 }:int

{ first = "Alice", last = "Smith" }:string
```

All the above examples are Immutables, but you can use them to group mutables as well.

All at once:

```lua
${
  n1 = 1,
  n2 = 2,
  n3 = 3
}:int


${ first = "Alice", last = "Smith" }:string
```

Or separately:

```lua
{
  $n1 = 1,
  $n2 = 2,
  n3 = 3
}:int

{ $first = "Alice", last = "Smith" }:string

```

And you can name them:

```lua
$data{ n1 = 1, n2 = 2, n3 = 3 }:int

$name{ first = "Alice", last = "Smith" }:string
```

And you can access them statically:

```lua
$data..n1
$data..n2
$data..n3

$name..first
$name..last
```

Or go indexed (you'll see indexing very soon - Wide uses one-base index)

```lua
$data..1
$data..2
$data..3

$name..1
$name..2
```

Or even iterate over them (you'll see iteration very soon):

```lua
~(n = $data) {
  "Value is {n}"
}
```

Wide automatically binds utility methods (if any) to Entity Groups based on the type used:

```lua
$nums{ a = 1, b = 2, c = 3 }:int
$nums.sum()       -- 6
$nums.avg()       -- 2
$nums.toList()    -- [1, 2, 3]

$name{ first = "Alice", last = "Smith" }:string
$name.join(" ")    -- "Alice Smith"

$stats.map(n => n * 2)
$words.filter(w => w.length > 4)
```

⚠️ When using utility methods you just used one `.` dot. That's because you are calling the Object corresponding to the data type itself, not the static context of the group.

But you can also bind traits via Entity Extension:

```lua
..Math Math

() => {
  values{a=1, b=2}::(Math):int
  "Max: {} and Min: {}", ..values.max(), ..values.min()
}
```

### Shadowing Exchange

You can shadow Entities from Immutable to Mutable state and vice-versa. But be carefull because excessive shadowing can be confusing. That's why explicitly using `$` in Mutables usage is the best way to go!

Without signaling `$` State Intent on usage:

```lua
n:= 1
n:= 2

$n:= 3

-- ... after 1000 lines of code

n = 4

n:= 5 -- not clear if is Mutable or Immutable
n = 6 ❌ -- Error: cannot assign twice to immutable
```

Signalling `$` State Intent on usage:

```lua
n:= 1
n:= 2

$n:= 3

-- ... after 1000 lines of code

$n = 4 -- clear that is Mutable

n:= 5
n = 6 ❌ -- Error: cannot assign twice to immutable
```

See? Always using `$` Change Intent makes it clearer when exchanging shadowing.

## `#` Enumerable Intent

Whenever you see the Enumerable Intent # (hashtag symbol) you can think:

- it can be countable
- it can be enumerable
- it can define constant value
- it can define enumerable constants

### Constant Entities

Constant Entities are similar to Immutable Entities and Enumerations themselves, but with an important difference, they can't be shadowed.

To create a Constant Entity you prefix its name with `#`:

```lua
#PI = 3.14159265358979323846
#SPEED_OF_LIGHT = 299792458.0
#GRAVITATIONAL_CONSTANT = 6.67430e-11
#DEFAULT_TIMEOUT_MS = 5000
#STATUS_OK = 200
#AVOGADRO = 6.02214076e23
#API_URL = "https://api.example.com/v1/"
#DEBUG_MODE = 1
#ENV = "dev"
```

Constants can just use the `=` because the compiler will always know what type it must be infered, but you can type them if you wish:

```lua
#PI:double = 3.14159265358979323846
```

You cannot change them:

```lua
#PI:double = 3.14159265358979323846
#PI = 3 ❌ -- Error cannot change constant PI
PI = 3 ❌ -- Error Entity PI is not defined
```

⚠️ You don't need to name your Constant Entities in CAMEL_CASE, but it's a good convention to adopt since it gives Visual Intent to your code making them visually different from Immutables!

You output them likewise other entities but using the Constant `#`Constant Intent:

```lua
"The speed of light is {#SPEED_OF_LIGHT}."
```

⚠️ You don't need to use # when using a Constant, but it can make explicit your are using them, so in the examples it will be used.

You can group them between a context `{}`:

```lua
#{
  Sunday = 0
  Monday = 1
  Tuesday = 2
  Wednesday = 3
  Thursday = 4
  Friday = 5
  Saturday = 6
}

"Sunday is {#Sunday}"
```

You can also name grouped Constants :

```lua
#Day {
  Sunday = 0
  Monday = 1
  Tuesday = 2
  Wednesday = 3
  Thursday = 4
  Friday = 5
  Saturday = 6
}
```

And use like so:

```lua
"Sunday is {#Day..Sunday}"
```

Or just:

```lua
"Sunday is {#Sunday}"
```

You can't have the same Constants grouped with different names because that would cause to be shadowing them, and they can't!

```lua
#Day {
  Sunday = 0
  Monday = 1
  Tuesday = 2
  Wednesday = 3
  Thursday = 4
  Friday = 5
  Saturday = 6
}

#Weekday { ❌ -- Error Constant Entities Cannot be shadowed in Groups
  Monday = 1
  Tuesday = 2
  Wednesday = 3
  Thursday = 4
  Friday = 5
}

#Weekend { ❌ -- Error Constant Entities Cannot be shadowed in Groups
  Sunday = 0
  Saturday = 6
}
```

Constants are closely related to Enums, with the main difference that enums enclose their constants with `</>` and can have Generics in their name and Functions to behave on selection.

Take a look at Enums section later, but the most comparison that we can make now may be overhead, so just abstract the concepts until you reach Enums.

**Enums Example:**

```lua
#Day{int} <
  Sunday = 0,
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday

  clip() => Day ? {
    Monday => "Mon",
    Tuesday => "Tue",
    Wednesday => "Wed",
    Thursday => "Thu",
    Saturday => "Sat",
    Sunday => "Sun",
  }
/>

"Sunday is {#Day..Sunday}" -- Output 0
"Sunday is {#Day..Sunday.clip()}" -- Output "Sun"

day:Day = #Sunday
"Sunday is {day}" -- Output 0
"Sunday is {day.clip()}" -- Output "Sun"
```

----

## Entity Context

First, remember that Entities must exist previously to be used, shadowed, or mutated.

```lua
"Message is: {message}" ❌ -- Error: Entity "message" is not defined
```

Entities are constrained to the Context they exist, you must use them in the same context they are created, or their nested ones.

⚠️ The exception being for Constant Entities because they fall through all contexts after usage.

```lua
#CONSTANT = true

message:= "Hi"

#CONSTANT ? {
  "Message is: {message}" ✅ -- Ok, same context
}
```

Error for Constant defined after usage:

```lua
message:= "Hi"

#CONSTANT ? {❌ -- Error: Entity "CONSTANT" is not defined
  "Message is: {message}" -- Won't execute due to previous error
}

-- defined after usage
#CONSTANT = true
```

⚠️ You haven't seen much more than Entities yet, but the rule is that every construct that has a proper body has a proper context like Functions, Lambdas, Objects, Enums and Structs.

Following the message Entity inside Function does not exist because Function has its own context!

```lua
#CONSTANT = true

message:= "Hi"
"Message is: {message}" ✅ -- Ok, same context

printMessage() => {
  #CONSTANT ? {  ✅ -- Ok, CONSTANT previously defined
    "Message is: {message}" ❌ -- Error: Entity "message" is not defined in printMessage() context
  }
}

printMessage()
```

You can't do this as well (message is inside Function context):

```lua
printMessage() => {
  message:= "Hi"
}

printMessage()

"Message is: {message}" ❌ -- Error: Entity "message" is not defined
```

Nor this (message here is only a Function parameter):

```lua

printMessage(message:string) => {
  "Message is: {message}"  ✅ -- Ok, same context
}

printMessage("Hi")
"Message is: {message}" ❌ -- Error: Entity "message" is not defined
```

You can move the context of an Entity using the Move Intent, but you can't move the context of a Constant.

```lua
message:= "Hi"
"Message is: {message}" ✅ -- Ok, same context

printMessage(message:string) => {
  "Message is: {message}" ✅ -- Ok, context will be moved ahead
}

printMessage() << message

"Message is: {message}" ❌ -- Error: Entity "message" is moved
```

Moving can be an advanced topic, but it's simple in Wide, and that's just cited here for you to know it exists as a subject of Context.

----

## Comments

Wide has 3 ways to comment code:

### Inline Comments

```lua
-- This is a regular comment
```

But can place it anywhere, just in single lines or after code in a line:

```lua
doSomething( -- You can't use anywhere): ❌ Error Unterminated line
    -- No problem here, but previous broken already!
```

### Virtual Syntax Comments

```lua
`final class`.AircraftController </>

-- Calculate total fuel needed
`pure function`calculateFuel(amount:int, efficiency:float) float => {
  | amount * efficiency |
}
```

⚠️ Nothing between backticks is syntax, that's just virtual.

### Multiline Comments

```lua
/*
This is a multiline comment
that can have, as it name implies,
multiple line!
*/
doSomething(/* You can use anywhere */) => {
  /* but don't forget to close it */
}
```

## Union Types

If you have an Entity that might have more than one possible type and you want to just force it, you can use Union Types.

```lua
value:= string | number
value:= 123
value:= "hello"
```

But in some cases it only makes sense when used with Mutables because since when Shadowing Immutables the compiler kills the previous Entity and creates a new one with whatever same or new type you shadow it.

```lua
value:= string | number
value:= 123
value:= "hello"

-- same as:
value:= 123
value:= "hello"
```

Mutables makes more sense since you could mean "restrict it"

```lua
$value:= string | number
$value = "hello"
$value = 123
```

But on more specialized operations Unions came make sense!

```lua
printId(id: number | string) => {
  "Your ID is: {id}"
}

printId(101)
printId("202")
printId({ myID: 22342 }) ❌
```

The separator of the union members is allowed before the first element, so you could also write this:

```lua
printId(
  id:
  | number
  | string
) => {
  "Your ID is: {id}"
}
```

You can check the type:

```lua
printId(id: int | string) => {
  // id string  ? "{id.upper()}" . "{id}"
}
```

⚠️ Check the section "Type Checking" for more information on type checking.

You can also do some interesting things with Type Unions using string literals.

```lua
-- custom type "kind"
:kind = "circle" | "square"

shape:kind = "circle
shape:kind = "square
```

Now look at this:

```lua
-- interface Circle
:Circle <
  kind: "circle"
  radius: int
/>

-- interface Square
:Square <
  kind: "square"
  sideLength: int
/>

-- interface Shape
:Shape = Circle | Square

getArea(shape: Shape) int => {
  shape.kind === "circle" ? {
    | Math.PI * shape.radius ** 2 |
  }
  | shape.sideLength ** 2 |
}
```

If you went go horse, it would be like this:

```lua
-- interface Shape mixing kind
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

A List is created using `[]` symbols and separating values by commas.

List can be homogeneous or heterogeneous.

Some examples:

```lua
temperatures:= [22.5, 23.1, 21.8, 24.0, 12, 34, 45]
sensorReadings:= [10, 12, 9, 11,, 13]
playlist:= ["Song A", "Song B", "Song C"]
tasksQueue:= ["Login", "Process Data", "Logout"]
row1:= ["Alice", 30, "Engineer"]
row2:= ["Bob", 25, "Designer"]
columnAges:= [30, 25, 40]
employee:= ["John", 45, 9999.00, "Developer"]
availableOptions:= ["Option A", "Option B", "Option C"]
allowedPermissions:= ["read", "write", "execute"]
```

In both case the compiler can infer the types, but if you want to be explicit you can use 2 notations: **Union** for multiple types or **Spread** for the repetion.

```lua
temperatures:float|int = [22.5, 23.1, 21.8, 24.0, 12, 34, 45]
sensorReadings:int.. = [10, 12, 9, 11,, 13]
playlist:string.. = ["Song A", "Song B", "Song C"]
tasksQueue:string.. = ["Login", "Process Data", "Logout"]
row1:string | int = ["Alice", 30, "Engineer"]
row2:string | int = ["Bob", 25, "Designer"]
columnAges:int.. = [30, 25, 40]
employee:string | int | float = ["John", 45, 9999.00, "Developer"]
availableOptions:string.. = ["Option A", "Option B", "Option C"]
allowedPermissions:string.. = ["read", "write", "execute"]
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

⚠️ But from now own only One-based index will be used.

**Last Item `..`**

You can just get the last item like so:

```lua
"The song I listen to least is:"
"- {}", playlist..

languages: ["PHP", "Python", "JavaScript", "Rust", "Go", "C++", "Wide"]
"The first language I learned was {}", languages.1
"The last will be {}", language..
```

The symbols `..` are called Extent Intent, and you will see it very soon.

All collections have their items accessed like so.

After presenting the core Data Structures you'll be presented to Destructuring, Ranges, and Slices and this knowledge will be expanded.

### Tuple

A Tuple is created using `()` symbols and separating values by commas.

They can be homogeneous or heterogeneous.

Some examples:

```lua
coordinates:= (10, 20)
location:= (-33.8688, 151.2093)
red:= (255, 0, 0)
paleBlue:= (173, 216, 230)
user:= ("john_doe", 30, "john.doe@example.com")
product:= ("Laptop", 1200.50, 5)
serverConfig:= ("localhost", 8080, "http")
today:= (2025, 5, 6)
gravity:= (0, -9.81, 0)

"Coordinates: {}, {}", coodinates.1, coordinates.2
"Red: R({}), G({}), B({})", red.1, red.2, red.3
```

In both case the compiler can infer the types, but if you want to be explicit you can use 2 notations: **Union** for multiple types or **Spread** for the repetion.

```lua
coordinates:int.. = (10, 20)
location:float.. = (-33.8688, 151.2093)
red:int.. = (255, 0, 0)
paleBlue:int.. = (173, 216, 230)
user:string | int = ("john_doe", 30, "john.doe@example.com")
product:string | float = ("Laptop", 1200.50, 5)
serverConfig:string | int = ("localhost", 8080, "http")
today:int.. = (2025, 5, 6)
gravity:float.. = (0, -9.81, 0)
```

### Set

A Set is created using `{}` symbols and separating values by commas.

They can be homogeneous or heterogeneous.

Some examples:

```lua
evenNumbers:= {2, 4, 6, 8, 10}
dataSet:= {"Alice", 42, true, 3.14}
configValues:= {"enabled", 1, 0.0, false, "42", 42}
daysOff:= {"Saturday", "Sunday"}
fruits:= {"apple", "banana", "mango"}

-- Random results for sets

"This week you'll be off on {}", days_off.1
"I may take a {} to eat now", fruits.2
```

In both case the compiler can infer the types, but if you want to be explicit you can use 2 notations: **Union** for multiple types or **Spread** for the repetion.

```lua
evenNumbers:int.. = {2, 4, 6, 8, 10}
dataSet:string | int | bool | float = {"Alice", 42, true, 3.14}
configValues:string | int | float = {"enabled", 1, 0.0, false, "42", 42}
daysOff:string.. = {"Saturday", "Sunday"}
fruits:string.. = {"apple", "banana", "mango"}
```

### Dictionary

A Dictionary is created using pairs of `key:value` inside `{:}` symbols structure and separating its pair by commas.

They can be homogeneous or heterogeneous.

Some examples:

```lua
-- User profile data
user:= {
  "name": "Alice",
  "age": 30,
  "email": "<alice@example.com>",
  "isActive": True
}

"{} is {}", user.name, user.age

myDict:= {
  "name": "Alice",
  42: "int key",
  true: "bool key",
  (1,2): "tuple key"
}

-- Nested data for a blog post
post:= {
  "title": "Why Wide Rocks",
  "author": {
    "name": "Bob",
    "id": 42
  },
  "tags": ["wide", "programming", "tutorial"],
  "published": true
}

"{} by {}", post.title, post.author.name
"Tags: {}, {}, {}", post.tags.1, post.tags.2, post.tags.3
```

In both case the compiler can infer the types, but if you want to be explicit you can use 2 notations: **Union** for multiple types or **Spread** for the repetion for values, and use Generics for keys.

Somewhat like this:

```lua
entityName{KeyType}:ValueType = { ... }`
```

```lua
-- User profile data
user{string}: string|int|bool = {
  "name": "Alice",
  "age": 30,
  "email": "<alice@example.com>",
  "isActive": true
}

"{} is {}", user.name, user.age

myDict{string|int|bool|tuple}:string = {
  "name": "Alice",
  42: "int key",
  true: "bool key",
  (1,2): "tuple key"
}
```

If you use just tuples as keys:

```lua
routes{string..}:string = {
  ("GET", "/users"): "getUsers",
  ("POST", "/login"): "loginUser"
}
```

### String

A String is created using `""` symbols structure.

String is an Immutable Collection of characters (`char`) that can be accessed like Lists.

Some examples:

```lua
message:= "Hello, Wide!"
name:= "Mary Alice"
```

Accessing parts of string:

```lua
name:= "Mary Alice"
words:= name.split(" ")

initials:= "{}{}", words.1.1, words.2.1
-- initials = "MA"

name:= "Mary Alice Smith"
-- Advanced!
-- Here's the dynamic version using Comprehension Assignment
-- Create list ["M", "A"]
initials ~= (word.1) <~ name.split(" ")

"{}", initials.join("")
-- Output: "MAS"
```

## Destructuring

Destructuring in a way to unpack values from arrays and objects into distinct Entities.

It provides a more concise and readable way to extract data from these Collections.

All Collections in Wide provide support for destructuring at some level.

Depending on the Collection order will not be preserved.

Entities created by destructuring a Collection will cause to create Constant-like Immutable Entities.

**List**

```lua
user:= ["Mary", 35, 10000.00]

{name, age, salary}:= languages

"{name} is {age} years old and makes {salary} monthly"

languages:= ["PHP", "Python", "JavaScript", "Rust", "Go", "C++", "Wide"]

{..language}:= languages

"The first 3 languages to learn this year are:"
"1 - {language.1}"
"2 - {language.2}"
"3 - {language.3}"
```

Entities created at destructuring are all Immutable and can be shadowed.

For Tuples, Sets, and Dictionaries you'll mostly do the same, but Sets won't preserve the order.

**Tuple**

```lua
{name, age, city}:= ("Alice", 25, "New York")

"{name} is {age} years old and lives in {city}"

{..user}:= ("Alice", 25)

"{user.1} is {user.2} years old and ives in {user.3}"
```

**Set**

```lua
lotteryCompetitors:= {"Alice", "Bob", "Charlie", "Diana", "Eve", "Frank"}

{firstWinner, secondWinner, thirdWinner}: lotteryCompetitors

"Winners are:"
" #1 {firstWinner}"
" #2 {secondWinner}"
" #3 {thirdWinner}"

{..winners}: lotteryCompetitors

"Winners are:"
" #1 {winners.1}"
" #2 {winners.2}"
" #3 {winners.3}"
```

**Dictionary**

```lua
post:= {
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
message:= "Hello, Wide!"
"{message.1}" -- H
"{message.8}" -- W

..letter:= message
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

#### Multidimensional Collections

You can have multidimensional collections:

```lua
numbers:[3][3][3] = []
```

That will create an Array-like:

```text
[
  [
    [0, 0, 0], [0, 0, 0], [0, 0, 0]
  ],
  [
    [0, 0, 0], [0, 0, 0], [0, 0, 0]
  ],
  [
    [0, 0, 0], [0, 0, 0], [0, 0, 0]
  ],
]
```

But if you want to set just individual members of the structure.

Per member:

```lua
numbers:[3][3][3] = []

numbers.1.1.1 = 1
numbers.2.2.2 = 2
numbers.3.3.3 = 3
```

Output will be:

```text
[
  [
    [1, 0, 0], [0, 0, 0], [0, 0, 0]
  ],
  [
    [0, 0, 0], [0, 2, 0], [0, 0, 0]
  ],
  [
    [0, 0, 0], [0, 0, 0], [0, 0, 3]
  ],
]
```

Per chunck:

```lua
numbers:[3][3][3] = []

numbers.1.1 = [1]..
numbers.2.2 = [2]..
numbers.3.3 = [3]..
```

⚠️ Notice the `..` is after [].

Output will be:

```text
[
  [
    [1, 1, 1], [0, 0, 0], [0, 0, 0]
  ],
  [
    [0, 0, 0], [2, 2, 2], [0, 0, 0]
  ],
  [
    [0, 0, 0], [0, 0, 0], [3, 3, 3]
  ],
]
```

Per row:

```lua
numbers:[3][3][3] = []

numbers.1 = [1]..
numbers.2 = [2]..
numbers.3 = [3]..
```

Output will be:

```text
[
  [
    [1, 1, 1], [1, 1, 1], [1, 1, 1]
  ],
  [
    [2, 2, 2], [2, 2, 2], [2, 2, 2]
  ],
  [
    [3, 3, 3], [3, 3, 3], [3, 3, 3]
  ],
]
```

Per column:

```lua
numbers:[3][3][3] = []

numbers[1][1][1] = ..[9]
```

⚠️ Notice the `..` is before [].

Output will be:

```text
[
  [
    [9, 9, 9], [0, 0, 0], [0, 0, 0]
  ],
  [
    [9, 9, 9], [0, 0, 0], [0, 0, 0]
  ],
  [
    [9, 9, 9], [0, 0, 0], [0, 0, 0]
  ],
]
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

Every Collection in Wide can be questioned about how many elements it has using the `//` Inclusion Intent by prefixing it with `#`.

```lua
numbers:= [10, 20, 30, 40, 50]

"How many elements in 'numbers'?"
"There are {} elements in 'numbers'", #/numbers/
-- There are 5 elements in 'numbers'
```

And if the Collection has fixed size it works the same way:

```lua
numbers:[5] = [10]

"How many elements in 'numbers'?"
"There are {} elements in 'numbers'", #/numbers/
-- There are 5 elements in 'numbers'
```

Simple count string characters:

```lua
message:= "Hello, Wide!"

"'message' has {} characters", #/message/
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
list:= [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

"{list:..}" -- [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
"{list:1..4}" -- [1, 2, 3, 4]
"{list:3..5}" -- [3, 4, 5]
"{list:7..}" -- [7, 8, 9, 10]
"{list:-3..}" -- [8, 9, 10]
"{list:1..6:2}" -- [1, 3, 5]
"{list:1..:2}" -- [1, 3, 5, 7, 9]
```

```lua
string:= "Hello, Wide!"

"{string:..}" -- ['H', 'e', 'l', 'l', 'o', ',', ' ', W', 'i', 'd', 'e']
"{string:8..11}" -- ['W', 'i', 'd', 'e']
"{string:1..5}" -- ['H', 'e', 'l', 'l', 'o']
"{string:8..}" -- ['W', 'i', 'd', 'e', '!']
```

```lua
tuple:= ('a', 'b', 'c', 'd', 'e')

"{tuple:..}" --  ('a', 'b', 'c', 'd', 'e')
"{tuple:2..4}" --  ('b', 'c', 'd')
"{tuple:1..3}" --  ('a', 'b', 'c')
```

There's more to slices, but that's just a taste for you to meat Ranges after Iterations.

## Positionals

You can change Collections in Wide using Positionals. They are like Slices alike that can change the Collections.

In all examples will be using this list:

```lua
$list := [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

At Birth list is:

```text
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

You can **prepend** to `list`:

```lua
list ..= 0
```

`list` now is:

```text
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

You can **append** to `list`:

```lua
list =.. 10
```

`list` now is:

```text
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

You can `batch-prepend` or `batch-append`:

```lua
list ..= [-2, -1]
list =.. [11, 12]
```

`list` now is:

```text
[-2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```

That's very close to Infinity Syntax of Wide:

```lua
negativeInfinity:= -..
justInfinity:= ...
positiveInfinity:= ..+
```

So when you do `..=` or `=..` you are just giving Limits to a Finite Collection.

Hope that makes sense!

## Positionals

**Positionals** allows you to handle collections in place with simple math operators.

It use Wide One-based indexes.

However, when performing positional transformations, you may use or see a `0` Positional. That doesn't mean it's a real `0` position itself, it's just an alias for a mental read meaning: "Insert/remove/operate" before the start of a Collection. The `0` Positional will make the whole list to be recreated having all its current elements appended after what you passed to `.0` Positional so that what you wanted first to appear in `0` Positional becomes the element at `1` (first) position in that Collection Index.

Now, consider this Immutable List:

```lua
list:= [10, 20, 30, 40, 50]
```

You can just create a new list from appending a new item to the end using `+` method on the list name itself:

```lua
list:= list.+(60)
```

```text
[10, 20, 30, 40, 50, 60]
```

But what if you were to prepend to list? `-1` would mean "from last" and would make it inconsistent.

So `0` Positional solves the problem for prepending:

```lua
list:= list.0.+(5)
```

Now index 1 is 5 not 10:

```text
[5, 10, 20, 30, 40, 50, 60]
```

That's why there's no Zero Index on One-based indexing.

Adding multiple items to a Collection at once is possible.

Imagine you want to create a new list from that appending 7, 8 and 9:

```lua
list:= list.+(70, 80, 90) -- variadic values
-- list:= list.+(..[70, 80, 90]) -- OR collection destructuring
```

Now, its:

```text
[5, 10, 20, 30, 40, 50, 60, 70, 80, 90]
```

However, if that was a Mutable List you could do this:

```lua
$list:= [10, 20, 30, 40, 50]
list += 70, 80, 90 -- variadic values
-- list += ..[70, 80, 90]  -- OR collection destructuring
```

Now let's see a lot of examples that handle most Collections manipulations.

### Inserting Single Item

Appending - don't pass index and just `+` method:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.+(1)
```

Now, its:

```text
[10, 20, 30, 40, 50, 1]
```

Prepending - pass `0` Positional and just `+` method:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.0.+(1)
```

Now, its:

```text
[1, 10, 20, 30, 40, 50]
```

At position - just pass the index and use `=` method:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.1.=(1)
```

Now, its:

```text
[1, 20, 30, 40, 50]
```

### Inserting Multiple Items

Appending - don't pass index and just `+` method:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.+(1, 2, 3) -- variadic values
-- list:= list.+(..[1, 2, 3])  -- OR collection destructuring
```

Now, its:

```text
[10, 20, 30, 40, 50, 1, 2, 3]
```

Prepending - pass `0` Positional and just `+` method:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.0.+(1, 2, 3) -- variadic values
-- list:= list.0.+(..[1, 2, 3])  -- OR collection destructuring
```

Now, its:

```text
[1, 2, 3, 10, 20, 30, 40, 50]
```

At position - just pass the index and use `=` method:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.1.=(1, 2, 3) -- variadic values
-- list:= list.1.=(..[1, 2, 3])  -- OR collection destructuring
```

Now, its:

```text
[1, 2, 3, 20, 30, 40, 50]
```

### Removing Items

All the previous rules apply to removing, you just need to use the `-` method without values for not matching any, or passing one or more values to match them.

Some common cases:

```lua
list:= [10, 20, 30, 40, 50]
list:= list.-() -- remove last
-- [10, 20, 30, 40]

list:= [10, 20, 30, 40, 50]
list:= list.1.-() -- remove first
-- [20, 30, 40, 50]

list:= [10, 20, 30, 40, 50]
list:= list.3.-() -- at index 3
-- [10, 20, 40, 50]

list:= [10, 20, 30, 40, 50]
list:= list.-(20) -- removes item 20
-- [10, 30, 40, 50]

list:= [10, 20, 30, 40, 50]
list:= list.-(10, 30, 50)
-- [20, 40]
```

### Positionals Destructuring

In all cases about you can spread the operations and create new Collections besides the current in use:

```lua
list:= [10, 20, 30]
{old, list} = list.+(40)
```

Now `old` is: [10, 20, 30]
And `new` is: [10, 20, 30, 40]

That's true for all cases, but when removing you have 3 possible entities as result:

```lua
list:= [10, 20, 30]
{removed, old, list} = list.2.-()
```

Now `old` is: [10, 20, 30]
And `new` is: [10, 30]
And `removed` is: 20

### Positionals Math

You can perform some maths on Collections using Positionals:

```lua
list:= [10, 20, 30]
list:= list + 40
```

Now list is: [10, 20, 30, 40]

```lua
list:= [10, 20, 30]
list:= list.0 = 15
```

Now list is: [15, 20, 30]

```lua
list:= [10, 20, 30]
list:= list.2 + 25
```

Now list is: [10, 20, 25, 30]

```lua
list:= [10, 20, 30]
list:= list + 40, 50, 60
```

Now list is: [10, 20, 30, 40, 50, 60]

```lua
list:= [10, 20, 30]
list:= list * 2
```

Now list is: [10, 20, 30, 10, 20, 30]

```lua
list:= [10, 20, 30]
list:= list.1 * 3
```

Now list is: [10, 10, 10, 20, 30]

```lua
list:= [10, 20, 30]
list:= list.1..2 * 3
```

Now list is: [10, 20, 10, 20, 10, 20, 30]

```lua
list:= [10, 20, 30]
list:= list - 10
```

Now list is: [20, 30]

```lua
list:= [10, 20, 30]
list:= list - 10, 30
```

Now list is: [20]

```lua
list:= [10, 20, 30]
list:= -list
```

Now list is: []

```lua
list:= [10, 20, 30]
list:= -list.1
```

Now list is: [20, 30]

```lua
list:= [10, 20, 30]
list:= -list...
```

Now list is: []

```lua
list:= [10, 20, 30]
list:= -list.2..
```

Now list is: [10]

```lua
list:= [10, 20, 30]
list:= -list..2
```

Now list is: [30]

⚠️ Whe working with Positionals subtraction `entity - index` is not valid. Because you can't remove a value from a position. Instead you use slices or destructuring to isolate what you want to remove:

Valid:

```lua
list := list - 0     -- remove all `0`s
list := -list.1..3   -- remove slice 1..3
list := -list.-1     -- remove last element
```

Invalid:

```lua
list.1 - 1           -- ambiguous and unsupported
list.-1 - 0          -- ambiguous and unsupported
```

## Iterations

Wide has a revamped approach to iterating over Collections data.

Iterating in Wide is done with lambdas and mostly an Iterator is implicit.

Following Wide's idea of not having keywords, you'll be able to iterate data without `for`, `while`,  `do-while`, `foreach` in a simple way.

### `~` Iteration Intent

Whenever you see the Iteration Intent `~` (tilde symbol) you can think:

- it has repeation
- it has continuity
- it has recursion
- it has iterator

All Collections in Wide are Iterables and you can iterate over equally.

```lua
list = [1, 2, 3, 4, 5, 6]
list ~ (item) {
  "Item is {item}
}
```

⚠️ Notice that `~` here assumes a Foreach-like meaning.

Enumeration is also implicit:

```lua
list = [1, 2, 3, 4, 5, 6]
list ~ (item) {
  "Item at {item.} is {item}"
  -- Item at 1 is 1
}
```

### Destructive Iterations

You can get the index of the current iteration using `.` after the name of the collection Entity.

```lua
numbers:= [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

~(number = numbers) {
  "Number at #{numbers.} is {number}"
  -- Number at #1 is 1
}

/*
 You haven't been presented to Functions yet,
 but here's a simple Function  to return a squared number
 and inlined to look like a Lambda
*/
squared(number:int) int => number ** 2

-- or passing function to transform directly
~(squared(number) = numbers) {
  "Number at #{numbers.} squared is {number}"
}
```

```lua
uniqueColors:= {"red", "green" , "blue" }

~(color = uniqueColors) {
  "Color is {color}"
}

-- simple Function to make the string upper case.
upper(input:string) => string.upper()

-- or passing function to lambda
~(upper(color) = uniqueColors) {
  "{color}"
}
```

```lua
uniqueColors:= {"red":'R', "green":'G', "blue":'B'}

~({key, value} = uniqueColors) {
  "{key.(capitalize)} is represented by the letter: {value}"
}

~(color = uniqueColors) {
  "Color is {color}"
}
```

The same is true for all other Collections.

### `!` Not Intent

When you see it the Not Intent `!` (exclamation symbol) you may say:

- it is not *(something)*
- it is false *(not true)*
- it can not be
- it modifies *(context, scope, characteristics)*
- it propagates *(intention)*

### Controlled Repetition

Sometimes you may just need to repeat things.

Wide has smart functional built-in structures to iterate recursively until a condition is met or not.

You can also apply some of the knowledge you have with Slices to control even more repetition.

**Interate Until condition is met:**

```lua
$counter:= 1

~(counter <= 10) {
  "Counter value is: {counter}"
  $counter = $counter + 1
}
```

The above example is syntacticaly the same as:

```lua
$counter:= 1

~(counter <= 10).. { -- Extent intent here
  "Counter value is: {counter}"
  $counter = $counter + 1
}
```

**Special Conditions:**

`.1` step into one time at least and ignoring condition once

```lua
~(choice != 'Q').1 {
  "Menu"
  "- Open (O)"
  "- Print (P)"
  "- Quit (Q)"
  -- Some logic here...
}
```

`..3` run the first three iterations only independently if they meet or not the condition

```lua
$counter:= 1

~(counter <= 10)..3 {
  "Counter value is: {counter}"
  $counter = $counter + 1
}
```

`3..` run from third iteration up to end independently if they meet or not the condition

```lua
$counter:= 1

~(counter <= 10) 3.. {
  "Counter value is: {counter}"
  $counter = $counter + 1
}
```

`3..6` run from third iteration up to sixth independently if they meet or not the condition

```lua
$counter:= 1

~(counter <= 10) 3..6 {
  "Counter value is: {counter}"
  $counter += 1
}
```

### `||` Wall Intent

Whenever you see the Wall Intent `||` (2 pipe symbols) you can think:

- It stops flow on Iterators
- It has return value
- It yieds 1 or more values

### `>>` Flow Intent

Whenever you see the Flow Intent `>>` (2 greater than symbols) you can think:

- It allows flow on Iterators
- It pipes values
- It has return value

### Interrupting Repetition

```lua
$counter:= 1

~($counter <= 10) {
  "Counter value is: {counter}"

  $counter == 5 ? {
    "break, please"
    || -- Wall operator used alone in line inside question body
  }

  -- you could do like so:
  ($counter == 5) {
    "break, please!"

    returnValue = 100

    | returnValue | -- Wall operator used as braces return the value
  }

  $counter % 2 == 0 ? {
    "continue, please!"
     >> -- Flow operator used alone in line inside question body
  }

  -- you could do like so:
  ($counter % 2 == 0) {
    "continue, please"

     returnValue = 200

     > returnValue > -- Flow operator used as braces return the value
  }

  $counter++
}
```

### Loop

**Infinite**

```lua
~() {
  "Do something until break"
}
```

**For-like**

```lua
~($i:= 0)($i < 10)($i = $i + 1) {
  "imprima {i}"
}
```

## Ranges

Ranges generate numerical sequences for iteration.

They are based on the concept learned for Slices and Iterations.

Some examples:

**Wide is one-based**

The following example start all at 1

```lua
range:= ~(6)

~(val = range) {
  "{val}" -- 1 2 3 4 5 6
}

-- no need for temporary entity
~(val = (6)) {
  "{val}" -- 1 2 3 4 5 6
}
```

```lua
range:= ~(3..6)
~(val = range) {
  "{val}" -- 3 4 5 6
}

-- no need for temporary entity
~(val = (3..6)) {
  "{val}" -- 3 4 5 6
}
```

```lua
range:= ~(3..10:2)
~(val = range) {
  "{val}" -- 3 5 7 9
}

-- no need for temporary entity
~(val = (3..10:2)) {
  "{val}" -- 3 5 7 9
}
```

## Comprehension Assignment

In Wide, you can construct and populate an entity using a single expression via Comprehension Assignment, using the Meta Intent `~=`.

This combines:

- ~ Iteration
- = Assignment

into a single constructive flow:

```lua
range = 1..10

squares ~= (i) {
  squares.i = i * i
}
```

The i is taken from range (which yields numbers 1 to 10).
Wide automatically connects the nearest iterable to the comprehension loop.

```text
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

```lua
countries = () ~> |
  ["Brazil", "BR"]
  ["Canada", "CA"]
  ["Japan", "JP"]
|

codes ~= (entry) {
  (name, code) := entry
  codes.name = code
}
```

Here entry is each sublist from countries, destructured into name and code.

Output:

```lua
{
  "Brazil": "BR",
  "Canada": "CA",
  "Japan": "JP"
}
```

```lua
range:= ~(1..3)

grid ~= (x, y) {
  grid.x.y = "{x},{y}"
}
```

The comprehension is nested: range is implicitly used for both x and y.

Output:

```text
[
  ["1,1", "1,2", "1,3"],
  ["2,1", "2,2", "2,3"],
  ["3,1", "3,2", "3,3"]
]
```

### Comprehension Flow Binding

The marriage of a generator flow with semantic comprehension, using a minimal yet powerful syntax.

Remember that you can create generators like this in Wide:

```lua
countries()~> |
  ["Brazil", "BR"]
  ["Canada", "CA"]
  ["Japan", "JP"]
|
```

So you can consume it like this:

```lua
codes ~= (entry) {
  (name, code) := entry
  codes.name = code
} <~ countries
```

Now here you can marry them and go full fancy-mode:

```lua
codes ~= (entry) {
  (name, code) := entry
  codes.name = code
} <~> {
  |
    ["Brazil", "BR"]
    ["Canada", "CA"]
    ["Japan", "JP"]
  |
}
```

Notice that `<~>` is both `<~` and `~>`, so that like could be this:

```lua
codes ~= (entry) {
  (name, code) := entry
  codes.name = code
} <~(code)~> {
  |
    ["Brazil", "BR"]
    ["Canada", "CA"]
    ["Japan", "JP"]
  |
}
```

## `?` Question Intent

Every time you want to question your code for anything you use the `?` Question Intent.

As you might guess, Wide has no keywords for them as well.

Some examples:

```lua
name:= "Ada"

name == "Ada" ? {
  "Welcome, Ada!"
}

-- inline
name == "Ada" ? "Welcome, Ada!"
```

```lua
number:= 10

number > 10 ? {
  "{number} is greater than 10"
}

-- inline
number > 10 ? "{number} is greater than 10"
```

This is true for all other Question Intents you'll see.

```lua
name:= "Mary"

name == "Mary" ? {
  "Welcome, Mary!"
}
. {
  "Welcome, Stranger!"
}

-- or
name == "Mary" ? "Welcome, Mary!" . "Welcome, Stranger!"
```

```lua
name:= "Mary"

(name == "Alice") ? {
  "Welcome, Alice!"
}
(name == "Mary") ?? {
  "Welcome, Mary!"
}
(name == "Claire") ?? {
  "Welcome, Claire!"
}
(name == "Diane") ?? {
  "Welcome, Diane!"
}
. {
  "Welcome, Stranger!"
}

-- or inline

(name == "Alice") ? "Welcome, Alice!"
(name == "Mary") ?? "Welcome, Mary!"
(name == "Claire") ?? "Welcome, Claire!"
(name == "Diane") ?? "Welcome, Diane!"
. "Welcome, Stranger!"
```

⚠️ Parentheses are optional!  And `{}` are also optional when inlined like above.

You can also nest Questions:

```lua
name:= "Alice"
authorized:= false

(name == "Alice") ? {
  "Welcome, Alice!"

  (authorized) ? "You are authorized!"
  . "You are NOT authorized!"

} . "Welcome, Stranger!"
```

In the above example, you must use {} to nest, because that could mean totally different logic.

Wide has no null, nil, void, None, Option madness keywords to mean voidness.

If you need to check the existence of a value, you check agains it's state just passing the Entity and using the `?.` symbols together.

```lua
name:string  -- string is a type (alias), not the value
""Welcome, {name ?. "Stranger"}!""
```

That will print:

```text
Welcome, Stranger
```

```lua
name:= "Alice"
""Welcome, {name ?. "Stranger"}!""
```

That will print:

```text
Welcome, Alice!
```

### Question Expressions and Sentences

There are two structural forms of the `?` Question Intent:

A **Question Statement** when used for side-effect or branching.

It's just a logical branching construct, performs evaluation without returning a value.

```lua
user.isLoggedIn ? {
  redirectToDashboard()
}

```

A **Question Expression** when used to resolve a value.

A logical resolving construct, evaluates to a value and can be used inline.

```lua
welcomeText := user.isLoggedIn ? "Welcome back!" . "Please log in"
```

A *Question Statement* used in a returning context (such as inside a function with a returning body) behaves like a Question Expression.

This is known as **Question Morphing** — when a `?` block adapts to its return context.

```lua
getWelcomeText(user:User) => user.isLoggedIn ? "Welcome back!" . "Please log in"
```

So in summary:

- Call `condition ? { ... }` a Question Statement.

- Call `condition ? "Yes" . "No"` a Question Expression.

### Checking the Truthness of An Entity

As you saw in the Type-Values section, you can't cast any type into boolean, just numbers into booleans.

But you can check the truthness of an Entity using the `?..` Truthness Intent.

Just prefix the name of any Entity with that in a Question, and you'll get a true of false value for that.

In the following example Mutables will be used to make clear the Intent, because people will mostly check truthness on Entities that might have changed their states, but it will work the same for Immutables, Contants, Functions, Objects, and anything that returns a value.

```lua
$name:string
$age:int
$salary:double
$isMarried:bool

?..name ? "Has name"
?..age ? "Has age"
?..salary ? "Has salary"
?..isMarried ? "Is Married"
```

The above will print nothing, because all values ended up to be `falsy` values.

```lua
-- ... previous code

$name = "Alice"
$age = 34
$salary = 19999.00
$isMarried = true

?..name ? "Has name"
?..age ? "Has age"
?..salary ? "Has salary"
?..isMarried ? "Is Married"
```

Now it all will print the corresponing questioned text:

```text
Has name
Has age
Has salary
Is Married
```

And of course, if you just want to negate, you use the `!` Not Intent:

```lua
$name:string
$age:int
$salary:double
$isMarried:bool

!?..name ? "Has NOT name"
!?..age ? "Has NOT age"
!?..salary ? "Has NOT salary"
!?..isMarried ? "Is NOT Married"
```

Not it will output, because you negate the question:

```text
Has NOT name
Has NOT age
Has NOT salary
Is NOT Married
```

But you can get more fancy, and do just like so:

```lua
name?.. "Has name" . "Has NOT name"
age?.. "Has age" . "Has NOT age"
salary?.. "Has salary" . "Has NOT salary"
isMarried?.. "Is Married" . "Is NOT married"
```

Now, look how cool it gets with objects:

```lua
.User <
  .name:string
/>

$user:User </>

user?.. "Hello, {user.name}" . "Who are you really?"

$user:= <User name="Alice"/>

user?.. "Hello, {user}" . "Who are you really?"
```

⚠️ A table with all possibilities will be created, because it's vague yet!

### Regular Question Expression 🤣

Regular Expression in Wide is done using the `//` Inclusion Intent.

```lua
 /cat|dog/ entityToMatch
```

```lua
animal:= "bird"

/cat|dog/ animal ? {
  "matched"
}
. "did not match!"


text:= "my dog is a beautiful dog and I love my dog"

~({match} = /cat|dog/ text){
  "{match}"
}
```

You must always pass an entity after the expression:

```lua
~({match} /cat|dog/) {  ❌ -- No entity to match after expression
  "{match}"
}
```

Another way to Question in a *Switch-like*:

```lua
a:= 2

(a) ? {
  1 => {
    "one"
  },
  2 => {
    "two"
    "two again"
  },
  3 => {
    "three"
  },
  4 => {
    "Four"
    >> -- "Flow" operator allows to fall through
  },
  (5, 6, 7) => { -- Fall through implicit, group goes between ().
    "mistery number"
  } -- there's no need for , comma before resolution condition
  . => "other number"  -- cannot end with , comma
}
```

There's no need to use `()` for the question.

Another example:

```lua
day:= 4

day ? {
  (1, 7) => "Weekend!",
  (2, 3, 4, 5, 6 ) => "Weekday!", -- , comma used just to be fancy
  . -- can be empty!
}
```

By default all cases in a *Switch-like* Question stop at `,` comma symbol and doesn't fall through. If wanna to let fall through the next case, you can use the  `>>` Flow Operator.

In the *Switch-like* Question its case doesn't return values, so that if you place `""` after the `=>` you actually will get those same texts printed, so no need for braces.

```lua
a:= 2

(a) ? {
  1 => "one",
  2 => "two" "two again" "two again again",
  3 => "three",
  4 => "Four" >>,
  (4, 5, 6, 7) => {
    "mistery number"
  }
  . => "other number"
}
```

If you want to return a value, you can specialize your Question using Match Expressions:

```lua
item:= 10

message:string = item ? {
 (item == 100) => "It's one hundred",
  = 11 => "It's 11",
  < 10 => {
    -- if you go newline you'll add
    -- || Wall Operator as braces to the end of line that returns
    | "Less than 10" |
  },
  > 10 => "Greater than 10" -- , comma is optional as well
  .  => "It's 10" -- cannot end with , comma as well
  -- . ❌ BUT cannot be empty
}

"{message}"
```

If you want to both return and print you it can you must enclose between `{}` and use the `||` Wall Intent in the final of the returning expression.

You can also give a temporary name for the match expression:

```lua
item:= 10

times10:int = item ? {
  -- create a temporary "eq" name for the match expression case
  (item == 100) {hundred} =>  {
    "It's a hundred"
    | hundred * 100 |
  },
  = 11 {eq} => {
    "It's 11"
    | eq * 10 |
  },
  < 10 {lt} => {
    "Less than 10"
    | lt * 10 |
  },
  > 10 {gt} {
    "Greater than 10"
    | gt * 10 |
  }
  . {
    "It's 10"
    | item * 10 |
  }
}

"{}", message
```

As in the resolution case before, there's no need to name any of those match cases:

```lua
times10:int = item ? {
  -- create a temporary "eq" name for the match expression case
  (item == 100) =>  {
    "It's a hundred"
    | item * 100 |
  },
  = 11 => {
    "It's 11"
    | item * 10 |
  },
  < 10 => {
    "Less than 10"
    | item * 10 |
  },
  > 10 {
    "Greater than 10"
    | item * 10 |
  }
  . {
    "It's 10"
    | item * 10 |
  }
}
```

⚠️ You can also use Regular Expressions in Match Expressions. Just be creative!

You'll soon see Functions, but it's interesting to mark it here. When scoped alone inside a function you can do like so:

```lua
verifyNumber(x:int) string => x ? {
  = 11 => "It's 11"
  < 10 => "Less than 10"
  > 10 => "Greater than 10"
  . => "It's 10"
}

verifyNumber(4)
-- Output: "Less than 10"
```

⚠️ There's more to be added match expression cases. Those are just the bare basics!

## Functions

In its nature Functions are related to Lambdas in Wide, and they are reusable blocks of code that perform specific tasks like most programming languages do.

## Basic Syntax

A Function itself that does nothing other than exist:

```lua
() => {}
```

`=>` Lambda Intent is used to sign that the function signature ended.
`{}` Context Intent is used to create the body of the function.

To invoke a Function you do like so:

```lua
() -- Does nothing
```

⚠️ In Wide ()=> {} alone in a file is the Entry Function used to tell the compiler that file can be used as an Entry point to your program.

Named Function:

```lua
greet() => {}
greet() -- Does nothing
```

Function that prints a message with no return type:

```lua
greet() => {
  "Hello, Wide!" -- No return value, will just print to screen
}

greet() -- Output: Hello, Wide!
```

### Parameters

Function that prints a message based on single parameter:

```lua
greet(name:string) => {}
  "Hello, {name}!" -- Will print a dynamic message on the screen

greet("World") -- Output: Hello, World!
```

### Returning Values

When you create a function like this:

```lua
greet() => {

}
```

It will return an empty `||` Wall by default because there's no return type nor a return value defined in the function.

If you want to check if a function doesn't have a return type, it means you want to check if it returns an empty Wall, but how there's no such a thing, you can just check against `//` Inclusion intent agains the function call alone:

```lua
greet() => {}

// greet() ? "Function doesn't return have a return type and doesn't value"

value = greet

// value ? "Function doesn't return have a return type and doesn't value"

value = greet()

❌ -- Error: cannot match against absence of type on plain Entities name
// value ? "Function doesn't return have a return type and doesn't value"
```

The expression `// greet()` means: **"Match against absence of type."** so you check if the Function DOESN'T HAVE a return type, if not, it returns true. You can lazy check on Entity that's assigned to a Function name, but can't check against a plain Entity name.

You can also check the truthness of if it:

```lua
greet() => {}

?..greet() ?  "Function doesn't return a value"
```

If you need to return value(s) you need use the `||` Wall Intent at the end of the line that you want to return the value(s) or resulting value(s) from an expression.

To return a single value, just enclose that value in between Walls:

```lua
singleReturn() => {
  |10|
}

"{}", singleReturn() -- Output 10
```

To return multiple values, just enclose values separated by commas between Walls:

```lua
mutipleReturns() => {
  |10,20,20|
}

"{}", mutipleReturns() -- Output 10, 20, 30
```

Function that returns a message based single on parameter:

```lua
greet(name:string) string => {
  |"Hello, {name}!"|
}

greet("World") -- Doesn't output anything, just returned

"{}", greet("World") -- Hello, World!


message: greet("World")
"{}", message -- Hello, World!
```

As you saw, the `||` Wall Intent is used to return a value from a Function, but you can inline Functions when using the `=>` Lambda Intent alone. You don't need to use the Return Intent on inlined functions.

```lua
-- Inlined function
greet(name:string) string => "Hello, {name}!"
```

⚠️ Pay attention when inlining a Function that returns a string which the type is inferred by Wide!

This:

```lua
greet(name:string) => "Hello, {name}!" -- Type is inferred to be "string"
```

Is not the same as this:

```lua
greet(name:string) => {
  "Hello, {name}!" -- No : Type Intent here, will just print to screen
}
```

⚠️ **Remember:** If you want to print anything from a Function you must always place the printer line inside the Function body and never inline the function.

Again:

```lua
greet(name:string) => {
  "Hello, {name}!" -- Will print to screen, will just print to screen
}
```

For all other data or structure types it's okay since they can't be printed directly other then inside `""`.

```lua
-- Wide knows when it's another type other then "" and there's no confusion
-- int return inferred (no => "{number * 10}" here)
times10(number:int) => number * 10

result:= times10(10)

"{result}" -- 100
```

Back to the case of default `()` returned on functions without return types, when you HAVE a return type, be it explicit or inferred, you can check the type returned by the function, the value, or the truthness of the returned value:

```lua
sum(n:int, m:int) => {
  |n + m|
}

// sum(1, 1) int ? "It's an int type"

sum(1, 1) == 2 ? "It's 2"

?..sum(1, 1) ? "truthy"
?..sum(0, 0) ? "falsy"
```

**Multiple parameters:**

You separate parameters using `,` commas. Yes! `,` Separation Intent!

```lua
add(n:int, m:int, o:int) => n + m + o

result = add(5, 10, 15) -- You also separate values by commas
"{result}" -- 30
```

**Default parameter value:**

```lua
greet(name:string = "Stranger") => {
  "Hello, {name}!"
}

greet() -- Hello, Stranger
```

When using default parameter values you don't need to pass the Type Intent nor a type, because there's no way to be an Entity declaration.

**Named Parameters:**

```lua
greet(name:string, greeting = "Hello", warm = false) => {
  "{greeting}, {name}!"
  warm ? "You are awesome!"
}

greet("Alice") -- "Hello, Alice"
greet(name: "Alice", greeting: "Hi") -- Hi, Alice!
greet(name: "Alice", warm: true) -- Hello, Alice! \n You are Welcome!
```

⚠️ Parameters without a default value must appear in the same order they have in the Function signature.

```lua
...
greet("Alice", warm: true)
greet("Alice", greeting: "Hi")
```

**Unnamed Parameters**

If don't want to name your parameters you just do so with the  `..` Extent Intent:

```lua
add(..numbers:int) => {
  $sum:= 0

  ~(number = numbers) {
    $sum += number
  }

  |$sum|
}

result = sum(10, 20, 30, 50)
"{result}" -- 100
result = sum(10, 20, 30)
"{result}" -- 50
result = sum(10, 20)
"{result}" -- 30
result = sum(10)
"{result}" -- 10
result = sum()
"{result}" -- 0
```

You can also mix with positional once they come first:

```lua
add(a:int, b:int, ..numbers:int) => {
  $sum:= 0
  ~(number = numbers) {
    $sum += number
  }

  |$sum|
}

-- Just for clarity names were used, but no need!
result:= sum(a:10, b:20, 30, 50)
```

### Changing External Entities

You can change external Entities by using the `$` State Intent after function invokation and passing the entities you want to allow mutate inside:

```lua
funcCall($name) $ $name
```

Some examples:

```lua
$name:= "Mary"
$message:= "Hello"
times:= 10

greet(name = "Stranger", message = "Hello", times = 5) => {
  name:= "Alice"

  ~(times) {
    "{message}, {name}!"
  }
}

"{message}" -- initial value STILL!
"{name}" -- initial value STILL

greet($name) -- Ordinary function call

"{message}" -- initial value STILL!
"{name}" -- initial value STILL

/*
 Here function call will change the outside scope.
*/
greet($name) $ $name

"{message}" -- initial value STILL!
"{name}" -- initial value CHANGED!

greet($name, $message) $ ($name, $message)

"{name}" -- initial value CHANGED!
"{message}" -- initial value CHANGED!
```

There's no way to pass an Immutable!

```lua
greet($name, time:10) $ times ❌ -- Error cannot mutate immutable Entity 'times'!

greet("John", "Hi") $ (name, message) ❌ -- Error cannot mutate immutable Object String
```

**Moving the scope of an Entity:**

You can similarly move the scope of an Entity using the `<<` Move Intent:

```lua
number1:= 10
number2:= 20

add(a:int, b:int) => {
  |a + b|
}

"{number1}"
"{number2}"
sum:= add(number1, number2) << number1 -- number2 moved to sum Function scope
"{sum}"
"{number1}"
"{number2}" ❌ -- Error 'number2' does not exist in this scope
```

And for moving Mutables:

```lua
$number2: 20 -- Mutable now

"{number1}"
"{number2}"
sum:= add(number1, $number2) << $number2 -- $number2 moved to sum Function scope
"{sum}"
"{number1}"
"{number2}" ❌ -- Error '$number2' does not exist in this scope
```

## Lambdas

To create a Lambda in Wide you just create an Entity an assign function to it.

You don't need to use `:=` for lambdas.

Using `{}` will prevent the Lambda from returning the String ""

```lua
fn = () => { "Do nothing" }

fn() -- will print nothing!


msg:= fn()

"{msg}" -- will ouput "Do nothing"
```

When directly creating Lambda as values for Entities, it seems more pleasing and Mathematically correct to use the `=` operator.

```lua
fn = () => { "Do nothing" }
fn()

-- or

fn:= () => { "Do nothing" }
fn()

```

You can use any! Your choice!

Lambda without `{}` return implicit value:

```lua
add = (n:int, m:int) => n + m
```

Lambdas can have parameters:

```lua
greet = (name:string) => { "Hello, {name}!" }

greet("Wide") -- Hello Wide!
```

But when used `{}` and a value must be returned, the `||` Wall intent must be used:

```lua
add = (n:int, m:int) => {
  |n + m|
}
```

Lambdas are just like functions but they have some special powers.

With regular Functions you can't access the outter scope, with Lambdas you can using the `//` Inclusion Intent.

```lua
name:= "Wide"

greet = (greet: string) /name/ => {
  "{greet}, {name}!"
}

greet("Hello") -- Output: Hello, Wide!
```

And of course you can just spread the whole world inside a Lambda:

```lua
greet:= "Hi"
$name:= "Wide"

greet = () /.../ {
  "{greet}, {name}!"
}

greet() -- Output: Hello, Wide!
```

Lamdas can change also the state of Mutable entities alike functions, but just for the parameters used in the `//` Inclusion Intent, not Lambda's signature:

```lua
$name:= "Wide"

greet = (greet: string) /$name/ => {
  $name: "World"
  "{greet}, {name}!"
}

"{name}" -- initial state STILL

greet("Hello") $ $name
"{name}" -- initial state CHANGED
```

Of course, you also can't use Immutables for that!

You can also Move Entities to Lambda Scope if you need that.

```lua
greet("Hello") << $name

"{$name}" ❌ -- Error '$name' does not exist in this scope
```

### Generators

You can create functions that return an Iterator just using the `~` Iteration Intent and using multiple return intent lines.

```lua
generator() ~> {
  |
  1
  2
  3
  |
}
```

You can also inline it with multiple pipes:

```lua
generator() ~> {
  |1|2|3|
}
```

And even go Fancy:

```lua
generator() ~> |1|2|3|
```

And to consume it:

```lua
~(value = generator()) {
    "Value is {value}"
}

-- Will output: 1 2 3
```

You can create a Generator directly for the consumer:

```lua
~(item = () ~> {
    |1|2|3|
}) {
  "{item}"
}
```

⚠️ Notice it does not use `=>` like normal functions but `~>` instead.

You can also create generators directly to consume in Iterators

```lua
~(item = |1|2|3|) {
  "{item}"
}
```

### `@` Event Intent

Whenever you see the Type Intent `@` you can think:

- it has behaviour *(metadata)*
- it has reflection *(metadata)*
- it has asynchronous behaviour *(async/await)*
- it has concurrent behaviour *(processes)*
- it has reactive hehaviour *(live update, assertion related)*
- it has deferred behaviour *(later used, error)*
- or it has event *(you guessed it!)*

## Error Handling

In Wide if you want to control if an Error has happened you just need to capture that event.

If you want to stop execution immediately on error you can use assertion:

```lua
division(n:int, m:int) int => {
  -- condition, message
  @(m == 0, "Cannot divide by {n} by {m}")
  |n / m|
}

division(10, 0) ❌ -- Execution will stop immediatly
```

If you want to capture the error you can propagate using the empty `{}` Context Intent. When you want to check for the error you just prefix the entity name with `@` Event intent.

```lua
division(n:int, m:int) int => {
  @(m == 0, "Cannot divide by {n} by {m}"){}
  |n / m|
}
-- somewhere else in code
n:= 10
m:= 0

-- no need for : Type intent, just assignment.
-- @ will check for the error
@(result) = division(n, m)

result ? {
  "result is {result}"
}
. "{@result}" -- Output the error using the `@`as well
```

You can also check directly agains `@` or destructure:

```lua
@(result) = division(n, m)

!@ ? {
  "Result is {result}"
}

-- or

@{result, error} = division(n, m)

!error ? {
  "Result is {result}"
}
```

So can I get just the error? yep!

```lua
@ = division(n, m)

!@ {
  result = division(n, m)
  "Result is {result}"
}
```

You can also default to a value (in this case 0) using question.

```lua
@(result) = division(n, m))?.0

"{result}"
```

You can also self-capture a whole context for the error using `{}` placing the code inside it.

```lua
printUserData() => {
  -- notice just the error message!
  @("error fetching data") {
    users:= query("select from users")

    ~(user = user) {
      "{user.name}"
    }
  }
}

-- If an error occur it will break execution immediatly
printUserData()
```

What about capture and propagate? Just place an `_` where in the place of a condition.

```lua
fetchUserData() []User => {
  users:[]User

  -- no named condition will do the
  @(_, "error fetching users") {
    users:= query("select name, age from users")
  }

  |users|
}
```

Just destructuring?

```lua
@(result) = fetchUserData()

!@ ? {
  ~({name, age} = users) ? {
    "{name} is {age} years old!"
  }
} . "{@}" -- Will print "error fetching users" -- if an error occur
```

## Async/Await Functions

Wide can handle async/await like in many contexts, but in Functions it's kinda magical!

On Function Declaration you just prefix the name with `@` and it says `async` event started.

On Function Call you just prefix the name with `@` and it says `await` event started.

```lua
@fetchUserData() []User => {
  users:[]User

  !@(
    error,
    "error fetching users"
  ) {
    users:= @query("select name, age from users")
  }

  |users|
}
```

But look how magical things get now checking for Error on an Async Function.

Just pass the error inside () and its an awaited error checking:

```lua
@(fetchUserData()) ? {
  ~({name, age} = users) {
    "{name} is {age} years old!"
  }
}  . "{@}"
```

It's both awaiting and capturing the error Events at the same time with just one Intent!

Same as:

```lua
@result = fetchUserData()

!@ ? {
  ~({name, age} = users) {
    "{name} is {age} years old!"
  }
}  . "{@}"
```

### Concurrency

When you prefix a list with `@[]` you can create a concurrent Context:

```lua
@[
  processOne(),
  processTwo(),
  processThree(),
  {
    "do something in block"
    "that may be useful
  }
]
```

⚠️ You can place it inside a function call like so:

```lua
@[
  processOne(),
  processTwo(),
  processThree(),
  {
    "do something in block"
    "that may be useful
  }
]
myFunc() ❌ -- It would be a bunch of Attributes decorating the function.
```

Just separate by an empty line:

```lua
@[
  processOne(),
  processTwo(),
  processThree(),
  {
    "do something in block"
    "that may be useful
  }
]
✅ -- You are ready to go concurrent now!
myFunc()
```

## Function Special Return Cases

Wide has some special return cases that makes it an HTML-first language.

### HTML Fragment Return `<></>`

When working with Web projects that are HTML-heavy, Wide has some niceties for you!

Wide makes HTML Functional and Reactive by nature on the Web Browser.

The HTML Fragment `<></>` is used to enclose the HTML Function body and has no `{}` in this case.

⚠️ When you are building UI's you can also make your Entities reactively by just prefixing them with `@` Event Intent.

Functional Component `<Main />`

```lua
Main(children:HTML) => <>
  {children}
</>
```

Functional Component `<Greet />`

```lua
Greet(name: string) => <>
  <p>Hello, {name}</p>
</>
```

Functional Component can have body, but for returning, you must enclose the `<></>` Fragment between `||` Wall Intent.

Component `<HomePage />`:

```lua
HomePage() => {
  userName:= "Mary"
  currentDate:= 2025

  -- Function used in button onclick
  (changeUser) => {
    -- When you prefix an Entity with @ is reactive "shadowing", you mean:
    -- "React Asyncronously to it in-place" and update the UI

    @userName:= "Alice" -- Event Intent here makes entity Reactive!

    -- Nothing will happen in the UI, just locally Shadowed
    -- userName: "John" ❌ Error, cannot change Immutable state
  }

  |
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
  |
}
```

## Functional Object Programming 🤣

Here the Functional meets Object-Oriented and they live happy forever!

Wide has full support for advanced object oriented programming, but it has a lot of *Widities*.

### Objects

⚠️ Wide has no keywords but naming is necessary, so English was choosen for naming Entities in Wide and its core Objects, Functions, Types and others.

Every Entity in Wide is an Object behind the scenes.

### Anonymous Objects

Every time you see it `</>` alone you are seeing an object it's an anonymous object:

```lua
$person:= < -- Unnamed Objects is an Anonymous Object
  name:string,
  age:int
/>
```

You can pass default values, if Immutable:

```lua
person:= <
  name:string = "Alice",
  age:int = 34
/>
```

But you could alias that to an immutable, or as a self reference as you'll see very soon:

```lua
<
  name: string,
  age: int
/{$person}>

$person.name = "Alice"
$person.age = 34
```

When aliasing anonymous objects, you are indeed just creating a new variable that can be self referenced. In the case of Anonymous Objects, they can just be used a local variable, so you MUST enclose the name inside `{}`.

```lua
<
  name: string,
  age: int

  .printInfo() => {
    "{}, "",
    $person.name,
    $person.age
  }
/{$person}>

$person.name = "Alice"
$person.age = 34

$person.printInfo()
```

### Resolution Objects

They are objects that you use to create concrete Object Entities and you can resolve them.

You create a concrete object by prefixing its name with `.`:

```lua
.Thing </>
```

And resolve it like this:

```lua
thing:Thing = </>
```

or like this:

```lua
thing: = <Thing/>
```

You can also use an alternative syntax mostly like if it were a constructor function, but not, calling the Object Lambda Constructor:

```lua
thing:Thing = .()
thing:= Thing.()
```

You might be questioning why not `Thing()`? That's because functions are called like so. And using `.()` makes it clear it is an object not a function.

**Adding Functions to Objects**

Objects are Entities that can have their own Entities and Functions.

```lua
.Thing <
  -- this an Object Function
  .doSomething() => {
    "Doing something!"
  }
/>

thing:Thing = </>
thing.doSomething() -- Doing nothing!
```

### [] Meta Intent

Whenever you see the Meta Intent `[]` you can think:

- it is shared data
- it has shared data
- it has exchangable data

Think of it like Entities for Data that only Objects can have.

```lua
.Thing <
  -- This is an Immutable Meta Entity .[do] but you don't need to use []
  .[do]:= true

  -- same as
  .do:= true -- no need for [] when using on per line

  -- this an Object Function
  .doSomething() => {
    .do ? "Do something!"
  }
/>

thing:Thing = </>
thing.do ? thing.doSomething() -- "Do something!"
```

Everything thing from an Object that is not static IS self-referenced using `.` before it's name as in this line:

```lua
--.(doSomething) => {
  .do ? "Do something!"
--}
```

`.do` means: `Thing.do` and that could be done inside the object.

```lua
--.(doSomething) => {
  Thing.do ? "Do something!"
--}
```

### Self aliasing Objects

Objects can also be self-aliased like so:

```lua
.Thing <
  .do:= true
  .doSomething() => {
    Self.do ? "Do something!"
  }
/Self>
```

⚠️ That's not a keyword, you can name it whatever you want, but in this doc it will be called Self.

```lua
.Thing <
  .do:= true
  .doSomething() => {
    this.do ? "Do something!"
  }
/this>
```

And now things can get weird for some and amazing for others:

```lua
.Thing <
  -- Make Meta Entity Mutable
  .$do:bool = true

  .doSomething() => {
    .$do ? "Do something!"
  }
/>
```

When mutable, you can now pass it in the object creation as HTML properties and mutate it at will, since it's Mutable, and when accessing there's no need to use `$`.

```lua
thing:= <Thing do=false />
thing.do ? thing.doSomething()
```

Assigning value from another Entity:

```lua
doSomething:bool = false
thing:= <Thing do=doSomething />
thing.do ? thing.doSomething()
```

### Object static scope

Objects can have static scope internally themselves just removing the (.) accessor when using them.

```lua
.Thing <
  -- This is an ordinary Immutable Entity, so it's static
  do:= true  -- No (.) means

  -- This is an ordinary Function, so it's static
  doSomething() => { -- NO (.)
    do ? "Do something!"
  }
/>
```

The `.` Resolution Intent were removed from Entity and Function Object, and now what to do when resolving outside?

Outside in any case of static resolution you can use the `..` Extent Intent itself, and that's prefered, but when you are using the Object name itself, you can just use a single `.`, this is possible because there's no way for an Object name being redefined.

```lua
Thing..do
Thing..doSomething()
```

But in that case, as you are directly using the Object name, you can just use just one dot.:

```lua
Thing.do
Thing.doSomething()
```

Other languages use `::`, but in Wide it has other purpose, it's used with Traits.

Some examples using static:

```lua
.Thing <
  .do:= true

  .doSomething() => {
    .do ? "Do something!"
  }

  -- static Entity
  newLambdaEntity:Thing = () => <Thing/>

  -- static Function
  newStaticFunction() Thing => () => <Thing/>
/>


thing:= Thing..newLambdaEntity -- Directly to Entity name, can use 2 dots -- preferred!
thing:= Thing.newLambdaEntity -- Directly to Entity name, can also use one
thing.do ? thing.doSomething() -- instance level, MUST use just one dot

thing:= Thing..newStaticFunction() -- Directly to Entity name, can use 2 dots -- preferred!
thing:= Thing.newStaticFunction() -- Directly to Entity name, can also use one
thing.do ? thing.doSomething() -- instance level, MUST use just one dot
```

### Notes on Keyword-less `new`

Wide does not require or support the `new` keyword, because objects are instantiated using `</>`.

But object instantiation can be expressed through a conventional `new()` method or factory-style functions.

The `new()` method is:

- Not a keyword
- Just a callable entity
- Often returns a self-like or related object
- May accept parameters for initialization

Example:

```lua
.Dog <
  new() => () => <Dog/>
  makeSound() => "A dog is barking!"
/>

dog:= Dog.new()
dog.makeSound()

-- or just
Dog..new().makeSound()
```

See why using `..` can have some visual appeal?

Builder style:

```lua
.Animal <
  (.name: string)
>

.Dog <
  new(name: string) => () => <Animal name/>
  makeSound() => "{.name} is barking!"
/>

Dog..new("Marley").makeSound()
```

Factory-style:

```lua
makeDog(name: string) => <Dog name/>

dog := makeDog("Marley")
dog.makeSound()
```

⚠️ Wide supports shorthand prop injection, so `<Animal name/>` implies `name=name`, allowing clean, modern syntax with no loss of clarity.

### Object Internal Grouping

When you have multiple Meta Entities you can just group them using the `[]` Meta Intent:

```lua
.Thing <
  .[ -- public
    entityOne:bool,
    entityTwo:bool,
    entityThree: bool
  ]

  ..[ -- protected
    entityFour:bool,
    entityFive:bool,
    entitySix: bool
  ]

  ...[ -- private
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

thing:Something = </> -- Ok,  no problem!
thing:Thing = </> ❌ -- Error you cannot resolve Extent Object Thing
```

Notice that `Thing` object now uses 2 `..` not 1 `.`!

### Access Transparency

Every object can have 4 ways for you to access them called:

- static *(in Isolation Intent - has no symbol - and doesn't preserve scope characteristics)*
- public *(using `.` preserves scope characteristics)*
- protected *(using `..` preserves scope characteristics)*
- private *(using `...` - local to object)*

⚠️ In this documentation it made sense keep the OOP jargons, but for Wide core it has other names:

- contextual (*static*)
- resolvable (*public*)
- extendable (*protected*)
- individual (*private*)

They mean the same thing as in every OOPL.

Visibility is just how many dots you use:

| Symbol | Level | Meaning             | Phrase                            |
|--------|--------|---------------------|------------------------------------|
| *(none)* | 0      | Static              | **no dot means static**            |
| `.`      | 1      | Public              | **one dot shares it**              |
| `..`     | 2      | Protected           | **two dots guards it**             |
| `...`    | 3      | Private (Self-only) | **three dots hides it**            |

Example of extending an Object:

```lua
.Thing <
  count:int -- static
  .name:string -- public
  ..value:obj -- protected

  ...instance:Thing -- private

  count() int => count -- static
  .name() string => .name -- public
  ..value() obj => .value -- protected
  ...instance() Thing => .instance ?. <Thing /> -- private
/>

-- Thing is extended by Something
.SomeThing ..Thing </>
```

In the above example Something becomes:

```lua
.SomeThing <
  count:int
  .name:string
  ..value:obj
  `...instance:Thing` -- not extended

  count() int: count
  .name() string: .name
  ..value() obj: .value
  `...instance():Thing` -- not extended
/>
```

As you can see only the `...instance` Entity and `...intance()` weren't extended.

What about Enums and Constants that use the `#` symbol? You can create them both, just prefix them with the visibility you want

Look:

```lua
.Network <
  .#INITIAL_STATUS{int} = 0

  .#Status{int} <
    Disconnected = #INITIAL_STATUS
    Connected
    Error
  />
/>

$status:Network.Status = Network.#Status..Disconnect

$status == #INITIAL_STATUS ? {
  $status = Network.#Status..Connected
}
```

### Constructor Object Lambdas

Objects can have constructors that behaves as an Object Lambda.

The concept of **Constructor/Lambda Promotion** is best used here, and when used the Entities you created inside the Object Lambda become Meta Entitities of the enclosing Object.

You must pass the Accessor to mean you want to promote.

Entities without the Acessor won't become Meta Entities and must be used just like ordinary parameters.

The most basic Object Lambda Looks like so:

```lua
.Thing <()/>

thing:Thing = <()/>
thing:= <Thing () />
thing:= Thing.()
```

Promoting Meta Entities from Constructor Lambda

```lua
.Thing <
  (
    .do:bool, -- Has Acessor, is promoted to Meta Entity
    ..what:string, -- Has Acessor, is promoted to Meta Entity
    ...when:string = "Never!", -- Has Acessor, is promoted to Meta
    nothing: false, -- Has NOT, is NOT promoted
  ) => nothing ? "Doing nothing"

  .doSomething() => {
    .do ? "{.what} will be done {.where}"
  }
/>

thing: <Thing (do: true, what: "Something", nothing: true )/>
thing.doSomething()

thing: <Thing (do: true, what: "Something")/>
thing.doSomething()

thing: <Thing (do: true, what: "Nothing", when: "Always!")/>
thing.doSomething()
```

You can use the Lambda Constructor as well, and how that's bound to the Object instance, it says Wide that you want to create a new Object from that Entity's name:

```lua
thing:= Thing.(do: true, what: "Nothing", when: "Always!")
thing.doSomething()
```

But you can make explict you intentions and separate constructor promoted entities line by line:

```lua
.Thing <
  .(do:bool)
  ..(what:string)
  ...(when:string = "Never!")

  -- Object Function
  .doSomething() => {
    .do ? "{.what} will be done {.where}"
  }
/>
```

### Notes on NOT promoted Entities

With NOT promoted Entities you enclose them between parentheses normally and access them like static Entities internally, and you must always have a body when using one or more NOT promoted Entities.

```lua
.Thing <
  (
    entityOne:bool,
    entityTwo:bool,
    entityThree:bool
  ) => {
    entityOne ? "Do One thing"
    entityTwo ? "Do Two thing"
    entityThree ? "Do Three thing"
  }
/>

thing: <Thing (true, true, true) />
```

You can't access them externally:

```lua
thing: <Thing (true, true, true) />
thing.entityOne ❌ Error: entityOne does not exist on object Thing
Thing..entityOne ❌ Error: static entityOne does not exist on object Thing
```

When NOT promoted parameters are used you can also segment it like unnamed params in Functions:

```lua
.Thing <
  (..params:int ) => {
    ~(param = params) {
      "{param}\n"
    }
  }
/>

thing: Thing = <(1, 2, 3, 4)/>

-- or

thing:= <Thing (1, 2, 3, 4)/>
```

Both cases the output will be:

```text
1
2
3
4
```

### Abstract Extent Objects

If want to just blueprint an Object's Intents that provides or not some default behaviour you can abstract placing a `!` Not Intent before the Object's name, its Entities and/or Functions.

Protected, Public, Static Entities and Functions can't be abstracted and just used inside the abstract extent content.

```lua
-- Notice that ".." turned ".!"
.!Thing <
  -- static Entity cannot be abstracted but used in context
  thingName: "Thing"

  .!name:string

  .!instance:obj

  -- static Function cannot be abstracted but used in context
  thingName() => thingName

  -- Notice that "." turned "!"
  .!instance() Thing -- abstract Function doesnt have body

  -- NOT abstract member
  .name() string => {
    |.name ?. thingName()| -- resolvable Function can have body
  }
/>
```

❌ If you don't provide implementation for everything marked as `.!` Wide will break with an error.

This is how Something will look after abstracting an Extent:

```lua
.SomeThing .!Thing <
  -- Notice that now "!" turned "."
  .name:string = "Something"

  -- Notice that now "!" turned "."
  .instance:Something = </>

  -- Notice that now "!" turned "."
  .instance() => Self.instance

  -- Notice that now "!" turned "."
  .name() string => {
    -- not abstract Function can be modified
    |
    .name ?. "How is it possible for me not having a name?"
    |
  }
/Self>
```

### Slot Objects

Wide supports composable slot-based object definitions with named or default render lambdas.

When using objects like HTML tags, you got free slots:

```lua
.Person <
/>
```

same as:

```lua
.Person <
/
  -- enter slot mode if used
  (slot) => slot
/>
```

And that's why you can do this in code:

```lua
<Person></Person>
```

Custom Slot Objects have access to all the members from the Object that creates it on the slot context because they are inside `//` and can have a custom body.

To get them you just use the Object name or the alias.

Slots are like normal lambdas and are enclosed by the `//` Inclusion Intent.

They work like Static Functions and are accessed by `..`.

```lua
.Person <
  (.name:string = "Stranger")
/
  (slot) => {
    slot?.<div id="person-slot">
      <p>"Welcome, {Self.name}"</p>
    </div>
  }
/Self>

 -- No slot content passed, will ouput default static slot content from Object
<Person ("Alice")>
</Person>

 -- With Slot, will output passed slot content to Object
<Person ("Alice")>
  <h1>{person.name}</h1>
  <p>"Hello, {person.name}"</p>
</Person {person}>
```

You can emulate the same behaviour on Functions as well, but in this case you don't need to use the Function name to get the parameters.

Like Objects you get them for free:

```lua
Greet() => {}
```

same as:

```lua
Greet() => {
  -- default return || or output from body

  -- enter slot mode if used
/
  (slot) => slot
/}
```

And that's why you can do this in code:

```lua
<Greet>
  <div>
    "Hello, person!"
  </div>
</Greet>
```

That alone would be senseless!

An useful example using the previous Person object together:

```lua
Greet(name:string) => {
  -- default return || or output from body
  |<p>"Hello, {name} from Function"</p>|

  -- enter slot mode if used
/
  () => <p>"Hello, {name} from Function Slot"</p>
/}

<Person ("Alice")>
  <h1>{person.name}</h1>

  -- no slot, default return or ouputs from body
  <Greet name={person.name} />

  -- using Function slot
  <Greet>
    <p>"Hello, {person..name}"</p>
  </Greet>
</Person {person}>
```

For both Objects and Functions you can't name the default Slot.

But you can have multiple slots, but in this case, they must all be manually called in your code, the default inclusively.

```lua
.Person <
  (.name:string = "Stranger")
/
  (slot) => {
    slot?.<div id="person-slot">
      <p>"Welcome, {Self.name}"</p>
    </div>
  }

  header(slot) => {
    slot?.<header>"My App"</header>
  }

  footer(slot) => {
    slot?.<footer>"My Footer"</footer>
  }
/Self>
```

Now you can do this:

```lua
<Person ("Alice")>
  { Person..header() }
  { Person..() }
  { Person..footer() }
</Person>
```

### !Not Intent: Structural Invocation on slots

All the above cases where done at runtime, but you can access slots at compile time.

Use ! after a function or object name to invoke its slot expansion logic at compile time. This allows components or functions to act as macros without losing runtime behavior.

```lua
println(input:obj, ..args) => {
/
  (slot)=> {
    output:string = ""
    ~(arg = args) {
      output+= input.replace("{}", arg)
    }
  }
/}

println!("{}, {}!", "Hello", "Rust")
```

⚠️ Experimental Feature! 🤣

### Interfaces

Interfaces are usable Objects with empty Functions. You can use them in other Objects. Once used you are forcebly required to implement their Functions' bodies in the Object they are used.

An Interface can use one or more other interfaces.

Interfaces can define constants literals, Meta Entities and Functions for objects.

```lua
:Speaker <
  .speak()
/>

:Mover <
  .move()
/>

:TalkingMover :Speaker :Mover <
  .name: string -- assignable property via interface
/>
-- same as
:TalkingMover :Speaker, Mover </>
```

To use in objects just compose and implement Interface's Functions:

```lua
.Person :Speaker <

  .speak() => {
    "Shit!"
  }
/>

.Robot :Speaker, Mover <

  .speak() => {
    "Bits and Shits!"
  }

  .move() => {
    "Shifting bits >>>>>"
  }
/>

.TalkingCar :TalkingMover <

  .name:string = "Talking Car"

  .speak() => {
    "Beep beep!"
  }

  .move() => {
    "Rolling tyres..."
  }
/>
```

### Traits

Traits are Object that can be used to give Objects new characteristics (traits).

You can use as many traits as you want!

Traits can use interfaces.

Traits can not use Objects.

You create traits using `::` symbols.

```lua
::Hello <
  .sayHello() => {
    "Hello "
  }
/>

::Wide <
  .sayWide() => {
    "Wide!"
  }
/>
```

You can use Traits like this for extending and simulating Multiple Inheritance:

```lua
.HelloWide <
  ::Hello, Wide

  -- Or individually

  ::Hello
  ::Wide

  .exclamation() => "!"
/>

obj:HelloWide = </>
obj.sayHello()
obj.sayWide()
obj.exclamation()
```

**Resolving Conflicts**

```lua
::A <
  .smallTalk() => {
    "a"
  }

  .bigTalk() => {
    "A"
  }
/>

::B <
  .smallTalk() => {
    "b"
  }

  .bigTalk() => {
    "B"
  }
/>

.Talker <
  ::(A, B) {
    B.smallTalk(): A, -- uses A<.smallTalk()/>
    A.bigTalk(): B, -- uses B<.bigTalk()/>
    -- aliasing
    B.bigTalk(): talk -- becomes B<.talk()/>
  }
/>
```

You can change Trait's visibility:

```lua
.Talker <
  ::(A, B) {
    B.smallTalk(): B.., -- just change the Accessor
    A.bigTalk(): A... -- just change the Accessor
  }
/>
```

You can mix conflict resolution and aliasing

```lua
.Talker <
  ::(A, B) {
    B.smallTalk(): A.., -- Like if A<..smallTalk()/>
    A.bigTalk(): B..., -- Like if B<...bigTalk()/>
    B.bigTalk(): ...talk -- like if B<...talk()/>
  }
/>
```

⚠️ Traits allow abstract Functions like Abstract Extent Objects.

⚠️ Traits allow static Static Entities and Static Functions

### Structs

A struct is a user-defined data type that groups types into a single unit.

It's not an Object `</>` so it doesn't uses it.

You create an Struct naming it and placing its structure inside `{}`.

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

Rectangle {
  topLeft: Point
  bottomRight: Point
}
```

Usage:

```lua
point: Point = Point{10, 20}
point: Point = {10, 20}
point: Point = Point{x: 10, y: 20}
point: Point = {x: 10, y: 20}

rectangle: Rectangle = {
  Point {0, 0},
  Point {100, 100}
}
```

When type is inferred it's mandatory to Name the struct, since that would be Set.

```lua
point:= Point{10, 20}

rectangle:= Rectangle{
  Point {0, 0},
  Point {100, 100}
}
```

### Entity Extension Definition

You can extend Objects at Entity definition and not just at Object structural level.

As you'll you are not restrict to use just Object, but other types of extensions like Interfaces, Traits, Enums and Structs are allowed.

For example. Suppose you you want to create a new Object entity anonymously and/or use an already existing named structured Object Entity.

The syntax for Entity Extension Definition is like this:

```lua
entityName.(ExtentObject):= </>
entityName.(ExtentObject):= <ResolutionObject/>
```

That's the same as:

```lua
entityName.ExtentObject:= </>
entityName.ExtentObject:= <ResolutionObject/>
```

But as you can add more that just one, that would be better to just use `.()`:

```lua
entityName.(ExtentObject, AnotherObject):= </>
entityName.(ExtentObject, AnotherObject):= <ResolutionObject/>
```

You can break lines when having too many:

```lua
entityName.(
  ExtentObject,
  AnotherObject,
  YetAnotherObject,
  AndYetAnotherObject
):= </> -- or <ResolutionObject/>
```

When you use other type of Extension you must change the type symbol that it represents.

In this section let's use this 3 named Objects structures:

```lua
.Talker <
  .name:string = "Stranger"
  .talk()=> "{} is talking...", Self.name
/Self>

.Eater <
  .name:string = "Stranger"
  .eat()=> "{} is eating...", Self.name
/Self>

.Person <.[
  name:string
  age:int
]/>
```

You can go bare bones anonymously:

```lua
stranger.Talker:= </>

"{}", stranger.talk() -- Output: Stranger is talking

anotherStranger.(Talker, Eater):= </>

"{}", anotherStranger.talk() -- Output: Stranger is talking
"{}", anotherStranger.eat() -- Output: Stranger is eating
```

But imagine you want to create an anonymous Object that reflects to a person with a given structure like:

```lua
person:= <
  name:string
  age:int
/>
```

And say you want it to extend from `Talk` and/or `Eater`?

```lua
person.(Talker, Eater):= <
  name:string
  age:int
/>

person.name = "Alice"
person.age = 34

"{}", person.talk() -- Output: "Alice is talking..."
"{}", person.eat() -- Output: "Alice is eating..."
```

The same is true for named Objects that has an implemented structure, but that don't extend from Talker nor Eater at structural level and you just want to extend at Entity definition:

```lua
person.(Talker, Eater):= <Person
  name="Alice"
  age=34
/>

"{}", person.talk() -- Output: "Alice is talking..."
"{}", person.eat() -- Output: "Alice is eating..."
```

That gives you a lot of flexibility and power because you don't need to tie your Objects to an implementation immediately when you create them for later use.

All that is true for Iterfaces, Traits, Enums and Structs as well.

In order to keep this section short, no real world examples will be provided, but just a nonsense bunch of possibilities.

```lua
.Object </>
:Interface </>
::Trait </>
#Enum </>
Struct {}

entityName.(Object):= </>

entityName:(Interface):= </>
entityName.(Object):(Interface):= </>

entityName::(Trait):= </>

entityName.(Object):(Interface)::(Trait):= </>

entityName#(Enum):= </>
entityName.(Object)#(Enum):(Interface)::(Trait):= </>

entityName.(Struct):= </>
entityName.(Object).(Struct)#(Enum):(Interface)::(Trait):= </>
```

When you have multiple types of extensions you can separate them all by lines:

```lua

entityName
  .(Object)
  :(Interface):= </>

entityName
  .(Object)
  :(Interface)
  ::(Trait):= </>

entityName
  .(Object)
  #(Enum)
  :(Interface)
  ::(Trait):= </>

entityName
  .(Object)
  .(Struct)
  #(Enum)
  :(Interface)
  ::(Trait):= </>
```

### Flow Extension Entity

When destructuring values like so:

```lua
..values = [1, 2, 3, 4, 5]
```

You can Iterate on values or extract each member by index.

With Flow Extension Entity, you can just pass a Trait to a destructive Entity and iterate over it:

```lua
..Flow Flow -- import Flow trait from Flow Module

..values = [1, 39, 21, 3, 14, 50]
values.map(x => x + 1).filter(x => x > 10)
```

But that unnecessary per se, because Lists would already offer such a feature. But it's interesting to work with Functions returned values:

```lua
getTokens() => {
  | "one", 1, "two", 2, "three", 3 |
}

..Flow Flow -- import Flow trait from Flow module

..tokens::(Flow) := getTokens()

tokens.filter(t => t::(Stringable)).join(", ")
```

In all case, there are some things to be noticed:

- just 1 extension type was used inside `()`, but you can use multiple separated by commas
- the symbol that identifies the extension (`.`, `#`, `:`, `::`) must come in the start of the `()`
- Structs must use `.()` like objects because it doesn't have a special symbol
- you can use Generics

### Conflict Resolution on Entity Extension

When extending Entities using inline Entity Extension Definition, naming conflicts can occur if multiple traits, interfaces, or objects provide members with the same name.

Wide allows you to resolve these conflicts using an explicit resolution block, but with a key restriction:

- Only public members `.` can be inherited or resolved.
- Protected `..` and private `...` members are not allowed in this context.

This design ensures that Entity Extensions are purely public-facing compositions, safe and visible to users, and free from encapsulation complexity.

You resolve conflicts using an aliasing block between `:=` Infer Intent.
After `:` Type Intent and before `=` Assignment Intent:

```lua
entity
  .(ObjectA)
  ::(TraitA, TraitB)
  :{
    ObjectA.name: .objectAName,   -- resolves ObjectA.name as .objectAName()
    TraitA.name(): .traitAName,   -- resolves TraitA.name as .traitAName()
    TraitB.name(): .traitBName    -- resolves TraitB.name as .traitBName()
  } = </>
```

## Generics

In Wide Generics are closely related to the Scope characteristics like you learned before.

You create Generics in Wide using `{}` Context Intent, because guess what? - you are gonna change that!

You can pass the use Generics with Functions, Objects, Interfaces, Traits, Enums, and Structs.

```lua
calculateAverage{T}(a:T, b:T) T => (a + b) / 2

a:int = 32
b:int = 50
average:= calculateAverage{int}(a, b)
average:= calculateAverage(a, b) -- Type can be inferred

c:float = 4.5
d:float = 10.3
average:= calculateAverage{float}(c, d)

❌ -- This would fail int and float
average: calculateAverage{int}(a, c) -- int and float are not the same
```

Example using Object

```lua
.Calculate{T} <
  .average(a:T b:T) T => (a + b) / 2
/>
```

Integers:

```lua
calculator:= <Calculate{int} />
a:int = 32
b:int = 50
average:= calculator.average(a, b)
```

Floats:

```lua
calculator:= <Calculate{float} />
c:float = 4.5
d:float = 10.3
average:= calculator.average(c, d)
```

Both Integers and Floats would fail:

```lua
calculator:= <Calculate{float} />
a:= 32
b:= 50
c:= 4.5
d:= 10.3
average: calculator.average(a, c) ❌ -- Error: int and float on same type is not allowed
```

But you can use Union Types:

```lua
calculator:= <Calculate{int|float} />
a:= 32
b:= 50
c:= 4.5
d:= 10.3
average: calculator.average(a, c) ✅
```

Another example:

```lua
.Stack{T} <
  ...stack: []T

  .push(item: T) => {
    Self.stack.(push item)
  }
/{Self}>

numberStack:Stack = <{Int}/>
stringStack:Stack = <{string}/>

aString:= "A String"
aNumber:= 100
aPerson:= {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
}

stringStack.push(aString)
numberStack.push(aNumber)

❌ -- These would fail!
numberStack.push(aPerson)
numberStack.push(aString)
stringStack.push(aPerson)
stringStack.push(aNumber)
```

Multiple type parameters can be defined within the angle brackets {} when declaring a generic function, interface, trait, enum, struct or object. Each type parameter represents a distinct type that can be specified when the generic is used.

```lua
processData{T, U}(input1: T, input2: U) T, U => {
  |[input1, input2]|
}

result:= processData{int, string}(10, "hello")
--  above result is of type [int, string]
```

Union types (|) allow a generic type to accept values of different types. This is useful when a function or component needs to handle a variety of input types.

```lua
handleInput{T}(input: T) T // T: string | int => {
  |input|
}

strResult:= handleInput("world") -- input is of type string
numResult:= handleInput(20) -- input is of type int
```

Intersection types (&) combine multiple types into one, requiring a value to satisfy all the specified types. This is useful when a generic type needs to have properties or methods from multiple types.

```lua
:HasName <
  .name: string
/>

:HasAge <
  .age: int
/>

processEntity{T}(entity: T) string
// T: HasName & HasAge => {
  |"{entity.name} is {entity.age} years old"|
}

person:= <
  name: "John",
  age: 30
/>

message:= processEntity(person)

"{message}"
```

Type constraints can be used with generics to specify that a type parameter must extend a certain type or implement an interface. This ensures that the generic type has the necessary properties or methods.

```lua
:Printable <
  .print()
/>

printItem{T: Printable}(item: T) => {
  item.print()
}


.Document :Printable <
  .print() => {
    "Printing Document"
  }
/>


doc: <Document/>
printItem(doc)
```

### Enums

Enums are very close to Constants, but you can have behaviour and create it with Generics Type, or compose it with Union.

They are created using `#` prefixed to its name like constants.

They're constants are accessed using the Static context with `..` preferably, but you can access it with a single `.`.

⚠️ You don't use `#` when defining the Type, but when assigning values with them it can make it more explicit you are using enums, so in this examples they will be used.

```lua
-- Numeric enum
#StatusCodes <
  OK = 200
  BadRequest = 400
  Unauthorized -- Auto-incremented to 401
  NotFound = 404
>

requestStatus:StatusCodes = #StatusCodes..OK
-- requestStatus:StatusCodes = StatusCodes..OK

-- or just

requestStatus:= #StatusCodes..OK
-- requestStatus:= StatusCodes..OK

-- String enum
#CardinalDirections <
  North = "North"
  East = "East"
  South = "South"
  West = "West"
/>

currentDirection:= #CardinalDirections..East

-- Heterogeneous enum (must make explict with Generics))
#MixedValues{string|int} <
  StringValue: "string"
  NumberValue: 1
/>

handleResponse(code: StatusCodes) => code ? {
  #StatusCodes..OK => {
    -- Handle successful response
  },
  #StatusCodes..NotFound => {
    -- Handle resource not found
  }
  -- ... other cases
  . => {}
}
```

You can be quite creative with them:

```lua
#Day{int} <
  Sunday = 0,
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday

  clip() => Day ? {
    -- Day.. in the match expresions are not necessary
    -- because Members of Enum are static themselves
    Day..Monday => "Mon",
    Day..Tuesday => "Tue",
    Day..Wednesday => "Wed",
    -- If you aliased you can use anywhere inside like aliased objects
    Self..Thursday => "Thu",
    Self..Friday => "Fri",
    -- No need for Self..
    Saturday => "Sat",
    Sunday => "Sun",
  }
/Self>

"Sunday is {#Day..Sunday}" -- Output 0
"Sunday is {#Day..Sunday.clip()}" -- Output "Sun"

day:Day = #Sunday
day:Day = #Day..Sunday
day:= #Day..Sunday
"Sunday is {day}" -- Output 0
"Sunday is {day.clip()}" -- Output "Sun"
```

Enum members have Lambda Constructors like Objects, so you can push your creativity to the limits and go extremely generic:

```lua
#Message{T} <
  Text(T),
  Binary([]{int}),
  Control(Command),
/>

#Command <
  Ping,
  Disconnect,
/>

process_message{T}(msg: Message{T}) => msg ? {
  #Message..Text(content) => { "Text message: {content}" },
  #Message..Binary(data) => { "Binary message of {data.len()} bytes" },
  #Message..Control(cmd) => cmd ? {
    #Command..Ping => { "Ping received." },
    #Command..Disconnect => { "Disconnecting..." },
  },
}

() => {
  msg1:= #Message..Text(String::from("Hello!"))
  msg2:= #Message..Binary([0xDE, 0xAD, 0xBE, 0xEF])
  msg3:= #Message..Control(Command..Ping)
  msg4:= #Message..Text(123)

  process_message(msg1)
  process_message(msg2)
  process_message(msg3)
  process_message(msg4)
}
```

You can also bind traits to Enums:

```lua
::Serialize <
  -- Somewhere in code...
/>

#Message{T::Serialize} <
  Text(T),
  Binary(Vec{int}),
  Control(Command),
/>
```

### Constant-like Enums

```lua
# Result <
  Success(u8)
  Failure(u16, char)
  Uncertainty
/>
```

Could be just the Union of `Success`, `Failure`, and `Uncertainty` constants:

```lua
# Result = Success{u8} | Failure{u16, char} | Uncertainty
```

😮 That proves WHY enums are just constants grouped in Wide.

So you can use in both cases like so:

```lua
outcome:Result = #Failure(20, 'X')

outcome ? {
    Success {n} => "Success with value: {}", n
    Failure {code, why} => "Fail: {} - {}", code, why
    Uncertainty => "Still waiting..."
}
```

## Attributes

In Wide, **attributes** are metadata-like constructs that can be applied to functions, meta entities, objects, and more — very much like annotations in other languages. But unlike traditional attributes, they are full-fledged **objects** in Wide, with support for inheritance, traits, macros, and default parameters.

Wide attributes are not just markers — they're living pieces of logic you can reason with.

### Attribute Binding

Wide supports annotations (called **attributes**) using a concise and composable syntax.

Attributes are declared using `@[]` Intents and contain one or more calls to functions and/or objects:

```lua
@[route(path: "/aircraft/{id}")]
show(id:int) View => "..."
```

```lua
.Book<
  @[belongsTo(localKey:'author_id')]
  .author:Author

  @[belongsTo(localKey:'collection_id')]
  .collection:BookCollection
/>
```

### Multiple Attributes

You can chain multiple attributes inside the same block separated by commas:

```lua
.Book<
  @[
    belongsTo(localKey: "author_uuid"),
    inverse(inverseKey: "uuid")
  ]
  .[author]:Author
/>
```

### Attribute Inheritance

Attributes can inherit from one another using `:` Interfaces or `::` Traits just like other constructs:

```lua
:HttpRouteAttribute<
  .path:string
/>

:GetRoute :HttpRouteAttribute <
  .method:= "GET"
/>

.BookController <
  @[<GetRoute path:"/books" />]
  .listBooks() => {
    -- list books...
  }
/>
```

This allows base metadata behaviors to be reused and extended without duplication.

### Default Values in Attributes

Attributes support **default parameter values**, making them easier to use:

```lua
.Logged <
  .required:= true
  .roles:= ["user"]
/>

@[<Logged />]
viewDashboard()

@[<Logged required=false, roles=["guest"] />]
previewDashboard()
```

### Traits and Composition in Attributes

Since attributes are objects, they can **implement traits** or even **use other attributes** internally:

```lua
::Auditable<
  .auditLog(message:string) => "..."
/>

:AuditAttribute ::Auditable<
  .logLevel:= "INFO"
/>

@[<AuditAttribute logLevel="DEBUG" />]
deleteItem()
```

This enables **modular attribute logic** through traits.

## Attributes and Macros

Attributes can pair with **compile-time macros**, injecting logic or altering behavior at compile time:

```lua
@[<AutoToString />]
<Person />
```

Use cases include:

- Auto-generating methods (e.g., `toString()`)
- Validations (e.g., required fields)
- Dependency injection markers

## Reflection and Introspection

Wide has a very simple reflective and introspective mechanism using the `@` Event Intent.

You just postfix the name of your Entity with `@..` and you can now get comment tags using `*` and the attributes just using their names.

For example:

```lua
/**
 * @author "Somebody"
 *
 * @param string arg1 The first argument
 * @param string arg2 The second argument
 * @param string arg3 The third argument

 * @returns string
 */
@[attrFunc(value1: "value 01", value2: "value 02", value3: "value 03")]
yourFunc(arg1:string, arg2:string, arg3:string = "arg 03") string => ""
```

Using instropection and reflection at the same time is indistinguishable:

```lua
yourFunc@..*.author.1    -- Output ["Somebody"]
```

```lua
yourFunc@..*.param.1
yourFunc@..*.param.2
yourFunc@..*.param.3
```

Output:

```text
["string", "arg1", "The first Argument"]
["string", "arg2", "The first Argument"]
["string", "arg3", "The first Argument"]
```

```lua
yourFunc@..*.returns
```

Output:

```text
["string"]
```

```lua
yourFunc@..*.param
```

Output:

```text
[
  ["string", "arg1", "The first Argument"]
  ["string", "arg2", "The first Argument"]
  ["string", "arg3", "The first Argument"]
]
```

```lua
yourFunc@..*
```

Output :

```text
{
  param: [
    ["string", "arg1", "The first Argument"]
    ["string", "arg2", "The first Argument"]
    ["string", "arg3", "The first Argument"]
  ],
  returns: [ "string" ]
}
```

```lua
yourFunc@..attrFunc.1
yourFunc@..attrFunc.2
yourFunc@..attrFunc.3
```

Output:

```text
["value1", "string",  "value 01"]
["value2", "string",  "value 02"]
["value3", "string",  "value 03"]
```

```lua
yourFunc@..attrFunc
```

Output:

```text
{
  value1: ["value1", "string",  "value 01"],
  value1: ["value2", "string",  "value 02"],
  value1: ["value3", "string",  "value 03"],
}
```

```lua
yourFunc@..
```

Output:

```text
{
  * : {
    param: [
      ["string", "arg1", "The first Argument"],
      ["string", "arg2", "The first Argument"],
      ["string", "arg3", "The first Argument"]
    ],
    returns: [ "string" ]
  },
  attrFunc: {
    value1: ["value1", "string",  "value 01"],
    value1: ["value2", "string",  "value 02"],
    value1: ["value3", "string",  "value 03"]
  }
}
```

⚠️ If reflected is a Function or Object, you can call or instanciate them.

```lua
.Callback <
  () => {
    "I'm Callback Object"
  }
/>
anotherCallback() => {
  "I'm another callback Function"
}

callback(anotherCallback:fn) => {
  "I'm callback Function"
}

@[callback, Callback]
myFunc() => {}


myFunc@..callback() -- Output: "I'm callback Function"
myFunc@..callback.anotherCallback() -- "I'm another callback Function"
myFunc@..Callback..() -- Output: "I'm Callback Object"
```

⚠️ In the previous as `myFunc@..Callback..()` is called before `myFunc()..` you are calling the static Lambda Constructor and not the default Slot. The default slot `Callback..()` can only be called when inside an HTML like structure.

### Pipe Intent

Pipe operator in wide is `>>` with is itself an Intent.

```lua
userInput:= [12 7 9 33 8]

result:= userInput
  >> .filter(n) => n % 2 = 0
  >> .map(n) => n * n
  >> .sum()
```

In the above example the pipes were used with a built-in List `[]` that implements all those Functions.

The `.` Resolution Intention knows that `>>` Pipe Intent, but if Wide had a resolvable Object called "List", the previous example would be the same like:

```lua
userInput:= [12 7 9 33 8]

result:= userInput
  >> List.filter(n) => n % 2 = 0
  >> List.map(n) => n * n
  >> List.sum()
```

What indeed is internally is like this:

```lua
userInput:= [12 7 9 33 8]

result: userInput
  >> [].filter(n) => n % 2 = 0
  >> [].map(n) => n * n
  >> [].sum()
```

⚠️ Don't use []! It's ugly and unnecessary!

You can go Async with Pipes:

```lua
@fetchURL( "https://example.com/api/data")
  >> parseJSON()
  >> filter( isValid)
  >> map( extractName)
  >> saveToDB()
```

## Infinity

In Wide the Infinity is represented by `...`.

The `..` Extent Intent is a cousing of it.

Wide has 3 symbols for representing Infinity:

`..-` is like a number that's unbelievably small (negative).

`...` is like something that's not even a proper number.

`+..` is like a number that's unbelievably big (positive).

Like other Core Type-Values, you can alias at will:

```lua
{
  -Infinity:...-,
  Infinity:...,
  +Infinity:+..,
}
--or?
{
  -Inf:..-,
  Inf:...,
  +Inf:+..,
}
```

And you can even specify the types you wanna to work with:

```lua
{
  -Infinity:int = ...-,
  Infinity:int = ...,
  +Infinity:int = +..,
}
--or?
{
  -Inf:int = ..-,
  Inf:int = ...,
  +Inf:int = +..,
}
```

## Type Checking

In Wide type checking can be done using the `//` Inclusion Intent.

When reading `//` you can say "when" or "where".

There are 2 basic forms:

```lua
a:float = 3.14
b:int = 3

// a float ? "a is float" . "a is not float"
-- Read: When a is float

// b float ? "b is float" . "b is not float"
-- Read: When b is float
```

Output:

```text
a is float
b is not float
```

But you could also obtain the same result like so:

```lua
/a/ float ? "a is float" . "a is not float"
-- Read: Where a is float

/b/ float ? "b is float" . "b is not float"
-- Read: Where b is float
```

You can construct a negative sentence like so:

```lua
b:int = 3
// b ! float ? "b is not float" -- True!!!
-- /b/ ! float ? "b is not float"
```

That reads: When/Where b is not equal to float

You can also check if the Entity Type like a instanceof operator:

```lua
..Animal < />

.Dog .Animal < />

.Robot < />

// Dog Animal ? "Dog is an Animal" . "Dog is not an Animal"
-- Read: When Dog is Animal

// Robot Animal ? "Robot is an Animal" . "Robot is not an Animal"
-- Read: When Robog is Animal

robot:= <Robot />

// robot ! Animal ? "Robot is not an Animal" -- True!!
-- /robot/ ! Animal ? "Robot is not an Animal" -- True!!
-- When robot is NOT Animal
```

Output:

```text
Dog is an Animal
Robot is not an Animal
Robot is not an Animal
```

You can also batch check multiple entities separating by commas:

```lua
// a, b float -- False, a is int
// Dog, Robot Animal -- False, Robot is not Animal
```

For better readability, you can use any pair or brackets to enclose them:

```lua
// [a, b] float
// (a, b) float
// {a, b} float
```

## Type Casting

In Wide type casting is very simple, just type the variable when using it:

```lua
a:i16 = 12
b:int = 4
c:float = 3.7

"{}", a:i8 + b:i8 + c:i8
```

Output will be: 19

You can also force final result casting (expression-level):

```lua
"{}", (a + b + c):f32
```

You can also use in function calls:

```lua
sum(a:i32, b:i32) i32 => a + b

printSum(a:i32, b:i32) => {
  "Sum is {}", a + b
}

() => {
  x:i64 = 100
  y:i64 = 200

  printSum(x:i32, y:i32)

  result := sum(x:i32, y:i32)
  "Result is {}", result
}
```

⚠️ Type casting expressions must be value-safe. Downcasting is explicit and must obey overflow constraints — otherwise a compile-time or runtime error will occur (depending on safety settings).

Just going creative:

```lua
printSum(a: int | float, b: int | float) => (a, b) ? {
  /a/ float => {
    /b/ float ? "Sum is {}", a + b . "Sum is {}", a + b:i32
  },
  /b/ float => "Sum is {}", a:i32 + b
  . => "Sum is {}", a + b
}

printSum(a: int | float, b: int | float) => (a, b) ? {
  // a float => {
    // b float ? "Sum is {}", a + b . "Sum is {}", a + b:i32
  },
  // b float => "Sum is {}", a:i32 + b
  . => "Sum is {}", a + b
}
```

## Exports and Imports

Wide has a very simple system for importing with `..` and exporting with `&`.

### `&` Extern Intent

Whenever you see the Extern Intent `&` (ampersand symbol) you can think:

- it can be shared
- it can be paired
- it can be exported

### Exporting

You export prefixing what you want to export using the `&` Extern Intent:

```lua
-- ./libs/Zoo.wide file

.Zookeeper <
  (.name:string)
/>

& zoo:= "Blue forest"
& .Animal <
  ...animals: []string

  .add(name:string) => {
    .animals[] = name
  }
/>
& #Status <
  Open = true
  Closed = false
/>
```

### Importing

You import using the `..` Extent Intent passing the path of the file that contains the Entities you just want to import or the name of a core Wide Module.

```lua
-- ./main.wide file

..{zoo} ./libs/Zoo
..{Animal} ./libs/Zoo
..{Status} ./libs/Zoo
-- ..{ZooKeeper} ./libs/Zoo ❌ -- Error: Cannot import not exported entity ZooKeeper

() => {
  zooName:= zoo
  zooStatus:= #Status..Open

  animal: Animal = </>
  animal.add("Giraffe")
  animal.add("Monkey")
  animal.add("Eagle")
}
```

### Grouped Exports and Imports

As many things in Wide you can group exports and imports:

```lua
-- ./libs/Zoo.wide file

-- ... previous code

&{
  zoo,
  Animal,
  Status
}
```

or you could group them:

```lua
-- ./libs/Zoo.wide file

.Zookeeper </*...*//>

&{
  zoo:= "Blue forest"
  .Animal </*...*//>
  #Status </*...*//>
}
```

And you can also name your grouped exports creating a Struct-like export:

```lua
-- ./libs/Zoo.wide file

.Zookeeper </*...*//>

&Zoo {
  zoo:= "Blue forest"
  .Animal </*...*//>
  #Status </*...*//>
}
```

And now you can import each Entity isolated as you already know, or grouped, or named:

```lua
-- ./main.wide file

..{zoo} ./libs/Zoo
..{zoo, Animal} ./libs/Zoo
..{zoo, Animal, Status} ./libs/Zoo

-- named export is imported
..{Zoo} ./libs/Zoo

-- custom-named import
Safari..{
  zoo,
  Animal,
  Status
} ./libs/Zoo

() => {
  -- using named import
  Zoo.zooName:= zoo
  Zoo.zooStatus:= #Status..Open

  Zoo.animal: Animal = </>
  animal.add("Giraffe")
  animal.add("Monkey")
  animal.add("Eagle")

  -- using custom-named import
  Safari.zooName:= zoo
  Safari.zooStatus:= #Status..Open
  Safari.animal: Animal = </>

  -- using normal imports:
  zooName:= zoo
  zooStatus:= #Status..Open

  animal: Animal = </>
  animal.add("Giraffe")
  animal.add("Monkey")
  animal.add("Eagle")
}
```

⚠️ You can reimport at will, Wide just caches it and ignore what's already imported.

### Wide Modules Import

Whenever a module is available in core Wide STL, you can just import any of its members or itself by their names:

```lua
..Math Math

() => {
  -- Direct module call (static): Math's functions are used like a namespace
  values{a=1, b=2}:int
  "Max: {} and Min: {}", Math.max(..values), Math.min(..values)

  -- Trait-dispatch call (dynamic): values group is extended with Math's behavior
  values{a=1, b=2}::(Math):int
  "Max: {} and Min: {}", values.max(), values.min()
}
```

## Operators Overloading

Wide can overload most of its operators when working with Object Entities.

You can define any of these as methods inside objects:

| Operator | Method Name | Primitive Trait  |
| -------- | ----------- | ---------------- |
| `=`      | `=(other)`  | `::Assignable`   |
| `==`     | `==(other)` | `::Comparable`   |
| `<`      | `<(other)`  | `::Orderable`    |
| `>`      | `>(other)`  | `::Orderable`    |
| `<=`      | `<=(other)`  | `::Orderable`    |
| `>=`      | `>=(other)`  | `::Orderable`    |
| `+`      | `+(other)`  | `::Addable`      |
| `-`      | `-(other)`  | `::Subtractable` |
| `*`      | `*(other)`  | `::Multipliable` |
| `/`      | `/(other)`  | `::Divisible`    |
| `%`      | `%(other)`  | `::Modulable`    |
| `+=`      | `+=(other)`  | `::Addable`      |
| `-=`      | `-=(other)`  | `::Subtractable` |
| `*=`      | `*=(other)`  | `::Multipliable` |
| `/=`      | `/=(other)`  | `::Divisible`    |
| `%=`      | `%=(other)`  | `::Modulable`    |

The core Integer Object in Wide is like so:

```lua
.Integer::(
  Assignable,
  Comparable,
  Addable,
  Subtractable,
  Multipliable,
  Divisible,
  Modulable,
  Orderable
) >
  .value: int
/>
```

Because mostly all primitives in Wide is an Object with traits.

```text
1 + 2 + 3
```

is actually:

```lua
Integer.(1)
  .+(Integer.(2))
  .+(Integer.(3))
```

And that's why even this is valid:

```lua
+(+(1)) == 1
```

Because it's:

```lua
Integer.(1).+(Integer.(1)) == Integer.(2)
Integer.(2).+(Integer.(1)) == Integer.(3)
```

You can define visibility, but in this example just public will be used.

The following example is also a good case for grouping members with `[]` Meta Intent.

```lua
.Number <
  -- Here value is promoted to constructor Lambda
  (.value:int)

  .[
    =(other:Number) => Self.value = other.value < 0 ? 0 . other.value
    ==(other:Number) => Self.value == other.value
    <(other:Number) => Self.value < other.value
    >(other:Number) => Self.value > other.value
    +(other:Number) => Self.value + other.value
    -(other:Number) => Self.value - other.value
    *(other:Number) => Self.value * other.value
    /(other:Number) => Self.value / other.value
    %(other:Number) => Self.value % other.value
  ]
/Self>

a:= Number.(2)
b:= Number.(3)
c:= Number.(2)

a:= c

a == b ? "a same value as b" . "a not same value b"
-- Output "a not same value b"

a < b ? "a less than b" . "a not less than b"
-- Output "a less than be"

a > b ? "a greater than be" . "a not greater than b"
-- Output "a not greater than be"

addition:= a + b  -- Result: 5
subtraction:= a - b -- Result: -1
multiplication:= a * b -- Result: 6
division:= (a / b):float -- Result: 0.6666666666666667
modulus:= b % a -- Result: 1
```

You can also access those methods directly once they are public:

```lua
a:= Number.(2)
b:= Number.(3)

result = a.+(b)
```

Once Wide's STL is ready, you'll be able to use Traits from Operator STL.

```lua
..{Addable} Operator

.Object ::Addable <
  .value:int
/>
```
