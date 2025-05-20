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

Welcome to a Web-first **Intent-Oriented Programming**.

Wide is a symbol-based, declarative, paradigm-unifying programming language designed to feel natural, composable, and deeply readable.

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

But you can be very expressive with the language!

**Dijkstra's Algorithm?**

```lua
() => {
  .Node <
    (
      .$id: string
      .$edges: Map{string, int}
    )
  />

  Graph: Map{string, Node} = {
    "A": <Node (id: "A", edges: { "B": 2, "C": 4 }) />,
    "B": <Node (id: "B", edges: { "C": 1, "D": 7 }) />,
    "C": <Node (id: "C", edges: { "D": 3 }) />,
    "D": <Node (id: "D", edges: {}) />
  }

  dijkstra(start: string) => {
    $distances: Map{string, int} = {}
    $visited: Set{string} = {}

    Graph.keys().forEach(id => {
      $distances[id] = ...
    })

    $distances[start] = 0

    ~($visited.size() < Graph.keys().count()) {
      $unvisited = Graph.keys().filter(id => !$visited.has(id))

      current = $unvisited.reduce((min, id) => {
        $distances[id] < $distances[min] ? id : min;
      })

      node = Graph[current]
      distance = $distances[current]

      node.edges.keys().forEach(neighbor => {
        weight = node.edges[neighbor]
        total = distance + weight
        (total < $distances[neighbor]) ? {
          $distances[neighbor] = total
        }
      })

      $visited.add(current)
    }

    $distances;
  }

  result:= dijkstra("A")
  result.keys().map(nodeId => {
    "Distance from A to {nodeId}: {result[nodeId]}"
  })
}
```

**Bellman-Ford Algorithm?**

```lua
() => {
  Edge <(
    .$from: string
    .$to: string
    .$weight: int
  )/>

  Graph: List{Edge} = [
    <Edge (from: "A", to: "B", weight: 4) />,
    <Edge (from: "A", to: "C", weight: 5) />,
    <Edge (from: "B", to: "C", weight: -3) />,
    <Edge (from: "B", to: "D", weight: 6) />,
    <Edge (from: "C", to: "D", weight: 2) />
  ]

  Nodes: Set{string} = Graph.reduce((acc, e) => {
    acc.add(e.from)
    acc.add(e.to)
    acc;
  }, Set{})

  bellman_ford = (start: string) => {
    $dist: Map{string, int} = {}
    Nodes ~ (n) {
      $dist[n] = +..
    }
    $dist[start] = 0

    $passes = Nodes.size - 1
    ~ (0..$passes) {
      Graph ~ (edge) {
        $u = edge.from
        $v = edge.to
        $w = edge.weight
        ~ ($dist[$u] != +.. && $dist[$u] + $w < $dist[$v]) {
          $dist[$v] = $dist[$u] + $w
        }
      }
    }

    $hasNegativeCycle: bool = false
    Graph ~ (edge) {
      $u = edge.from
      $v = edge.to
      $w = edge.weight

      ~ ($dist[$u] != +.. && $dist[$u] + $w < $dist[$v]) {
        $hasNegativeCycle = true
      }
    }

    {
      distances: $dist,
      negativeCycle: $hasNegativeCycle
    };
  }

  result = (bellman_ford "A")
  (result)
}
```

**Floyd-Warshall Algorithm?**

```lua
() => {

  Nodes: List{string} = ["A", "B", "C", "D"]

  INF:int = +..

  Graph: Map{string, Map{string, int}} = {
    "A": { "A": 0, "B": 3, "C": INF, "D": 7 },
    "B": { "A": 8, "B": 0, "C": 2, "D": INF },
    "C": { "A": 5, "B": INF, "C": 0, "D": 1 },
    "D": { "A": 2, "B": INF, "C": INF, "D": 0 }
  }

  floyd_warshall = () => {
    $dist: Map{string, Map{string, int}} = {}

    Nodes ~ (i) {
      $dist[i] = {}
      Nodes ~ (j) {
        $dist[i][j] = Graph[i][j] ?? INF
      }
    }

    Nodes ~ (k) {
      Nodes ~ (i) {
        Nodes ~ (j) {
          $ik = $dist[i][k]
          $kj = $dist[k][j]
          $ij = $dist[i][j]
          ~ ($ik != INF && $kj != INF && $ik + $kj < $ij) {
            $dist[i][j] = $ik + $kj
          }
        }
      }
    }

    $dist;
  }

  result = (floyd_warshall)
  (result)
}
  ```

**Tarjan's Algorithm?**

  ```lua
() => {
  Node <(
    .$id: string
    .$edges: List{string}
  )/>

  Graph: Map{string, Node} = {
    "A": <Node (id: "A", edges: ["B"]) />,
    "B": <Node (id: "B", edges: ["C"]) />,
    "C": <Node (id: "C", edges: ["A", "D"]) />,
    "D": <Node (id: "D", edges: ["E"]) />,
    "E": <Node (id: "E", edges: ["F"]) />,
    "F": <Node (id: "F", edges: ["D", "G"]) />,
    "G": <Node (id: "G", edges: []) />
  }

  tarjan = () => {
    $index: int = 0
    $stack: List{string} = []
    $onStack: Set{string} = {}
    $indexes: Map{string, int} = {}
    $lowLinks: Map{string, int} = {}
    $components: List{List{string}} = []

    strongConnect = (v: string) => {
      $indexes[v] = $index
      $lowLinks[v] = $index
      $index += 1

      $stack.push(v)
      $onStack.add(v)

      Graph[v].edges ~ (w) {
        (!($indexes.has(w))) >> (
          (strongConnect w)
          $lowLinks[v] = $lowLinks[v].min($lowLinks[w])
        )

        $onStack.has(w) >> (
          $lowLinks[v] = $lowLinks[v].min($indexes[w])
        )
      }

      ($lowLinks[v] == $indexes[v]) >> (
        $component: List{string} = []

        ~ (true) {
          $w = $stack.pop()
          $onStack.delete($w)
          $component.push($w)
          ($w == v) || ()
        }

        $components.push($component)
      )
    }

    Graph.keys() ~ (v) {
      (!($indexes.has(v))) >> (strongConnect v)
    }

    $components;
  }

  result = (tarjan)
  (result)
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
| " | string  | "hello", "sweet potatoes", "How are you?" |
| 0 | int | 1, 10, 100, 999 |
| 0.0 | float | 20.5%, -5.6°C, 10.9km |
| 0.00 | double | Pi(π)3.14159265358979323846, -23.5505200 lat, -46.6333094 lng |
| () | fn \| lambda | (add), (subtract), (print), (click)  |
| <> | obj | Person, Vehicle, Dropdown, Box, Header, Provider |

Their Intent is both the type and the value they default to,
with exception to the Boolean `?` and the Object `<>`, most values mean exactly what they read.

Yes, the name of the type is that internally.

In wide you can create a **Custom Type** opening a context or not and where to place it and just naming it and prefixing with the `:` Type Intent:

```lua
:string
```

But that would serve no purpose! It's lost in the vaccumm of nonsense!

For core Wide **Type-Values** you can give it the type you want it to be:

```lua
"":string
```

⚠️ That's an Aliased Type-Value.

You can also create a type by assigning a type-value with the `=` Assignment Intent to a custom type.

```lua
:char = ''
:string = ""
:int = 0
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

You can even go more specialized mixing anything that might represent a type grouping them all together.

Besides not having keywords in its syntax, some words are impossible to avoid when talking to types, and as you can **alias** types, and in order to help newcomers and professionals with parity with other languages, Wide has built-in aliases for them in plain English:

```lua
?:bool {
  0:false
  1:true
}
'':char
"":string
0:int
0.0:float
0.00:double
():fn
</>:obj
```

Those words are not syntax, they are English words the compiler knows by default they were aliased. You can rename at any time just using the core Wide types as of the previous table and examples or from already English aliased types.

In the case of `?:bool`, it aliased it's possible values because they are also Type-Values. If that's the case, you use `{}` a context for them and follow the same pattern.

***Wide is made in Brazil***, so types could be aliased like so:

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
():funcal
</>:objeto
```

⚠️ Wide is able to understand both English and Portuguese alias in this case.

### Rules for Aliasing

When creating aliases you can't create them anywhere.

They must be the first lines of code if there are no imports, or the first lines of code after the imports if there are imports.

They can't be inside the Entry function nor elsewhere.

## Entry function

You haven't been presented to them yet, but Wide has an entry function - more properly a lambda - that signs to the compiler where to start the file first execution entry point.

That's like so:

```lua
() => {

}
```

Whatever you place before it is structural code that you can reuse inside the Entry function.

⚠️ When you see `{}` anywhere its very Intent is to bind itself as a **context** for anything. It's called **Context Intent**. A context can be used to create different things, but you don't need to memorize them all as you learn, they'll get so implicit into your head that you will understand them as you go.

⚠️❌ From now own, other than very specific, the Entry Function may not be  used for fragment code samples.

Back to custom types. This how you would do that for `:string` cited previously:

```lua
:string = ""
:Text = string

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

If you need to print `""` double quotes inside a string you just use 2 pairs double quotes instead of one.

```lua
() => {
  ""Hello, "Wide"!""
}
```

That will output:

```text
Hello, "Wide"!
```

### Interpolation

You can use curly braces inside those quotes `"{}"` to dinamically output values inside text output or just to compose dynamic strings of text:

```lua
() => {
  name:= "Wide"
  "Hello, {name}!"

  price:= 9.99
  "It's ${9.99}."
}
```

Those lines will output:

```text
Hello, Wide!

It's, $9.99.
```

### Printing Entity Type

Wheneven you wanna know the type of an Entity you enclose the Entity name with `:` and you can get its type name:

```lua
() => {
  number:= 10
  name:= "Alice"
  isActive:= true

  "{:number:}" -- int
  "{:name:}" -- string
  "{:isActive:}" -- bool
}
```

### Printing Entity Name

Wheneven you wanna know the name of an Entity:

- `:<ENTITY>:` prints the name of an Entity
- `::<ENTITY>::` prints the name of the value of an Entity in case it's been aliased.

```lua
() => {
  number:= 10
  "{:<number>:} value is {number}" -- number value is 10

  name:= "Alice"
  "{:<name>:} is {name}" -- name is Alice

  isActive:= true
  "{:<isActive>: is {isActive}" -- isActive is 1
  "{:<isActive>: is {::<isActive>::}" -- isActive is true
}
```

## Immutable, Mutable, and Constant Entities

In wide you everything you name is an Entity, Functions and Objects inclusive.

When talking about Entities you might read just Immutable, Mutable or Constant not having the need to write down nor say "Entity". In this guide, there will be cases when the word Entity will be ommited on purpose.

### Notes on "Variables"

Some people say that there's not such a thing like Immutables and Mutables, that they are all "variables" at the end, and that Wide can't call'em "Entities"

Yes, at the end - in Assembly that's true.

But wide is not Assembly!

### Immutable Entities

As talked previously, Wide has **Entities** that work like variables or contants in other programming languages.

By default Entities are immutable:

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

Yes, but it makes no sense if you never assign them a value and just use the default provided by the type system! If you try to do so you'll get a compiler warning and this code will be removed when compiled if not used. So don't waste yours nor yours computer energy doing that!

You can create a new Entity with the same name by **Shadowing** it, but as you already know, the previous will cease to exist in order for the new to live. Besides that you can also change the initial type when shadowing:

```lua
value:= 123
value:= "Alice"
```

But remember, you can reassign Immutables:

```lua
value:= 123
value= "Alice" ❌ -- Error: Entity value cannot be reassigned
```

### `$` State Intent

When you see it the State Intent `$` (dolar symbol) you may say:

- it can mutate
- it can change *(something)*

⚠️ *You have already been presented to the `$` State Intent when learned about Mutable Entities, as it is a more complex intent, placing this section there would make things unnecessarily overheaded.*

Wide has no concept of `null`, `nullptr`, `nil`, `void`, `None` nor `Option` exposed to you because is implicit when you want to change anything in Wide.

It's possible because every entity in Wide has a default state — which makes it always valid, but not necessarily populated.

As you'll see later, you just need to check agains that!

### Mutable Entities

If you want to be able to change an Entity's state, you can create it as a **Mutable Entity** by  prefixing its name with the `$` State Intent. Yes, it's intent is to say to you that you'll pay a price for that! Convenient?

```lua
$name:= "John"
$age:= 34
$salary:= 10000.00
```

The same rules of assignment for Immutable Entities also apply here:

- You can't create entities without types and values
- You shoudln't create entities that won't be used

But you can change their values!

```lua
$name:= "John"
$age:= 34
$salary:= 10000.00

$name = "Mary"
$age = 58
$salary = 20000.00
```

Did you notice that you don't use the `:` Intent here just the `=` Assignment Intent?

And what would happen if the entity doesn't exist and I don't use the `:` Intent? You got it right! A reassignment!

That's because you can only shadow Immutables, Mutables you reassign.

To print them, you don't need to pass the `$` symbol, but you can if you wish.

```lua
$name = "Mary"
$age = 62
$salary = 20000.00

"{name} is {age} old. Salary: {$salary}"
```

### Grouped Entities

Whenever you want to define multiple Entities, you can just group them.

Doing so will cause to create a Homogeneous Record.

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

Or go indexed (you'll see indexing very soon)

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

Wide automatically binds utility methods to Entity Groups based on type.

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

⚠️ Noticed that when using methods you just used one dot? That's because you are calling the Object corresponding to the data type itself, not the static context of the group.

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

Enums are closely related to Enums, with the main difference that enums enclose their constants with `</>` and can have Generics in their name and Functions to behave on selection.

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
    amount * efficiency;
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

If you have a Entity that might have more than one possible type and you want to just force it, you can use Union Types.

```lua
value:= string | number
value:= 123
value:= "hello"
```

But it some cases it only makes sense when used with Mutables because since when Shadowing Immutables the compiler kills the previous Entity and creates a new one with whatever same or new type you shadow it.

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
  :id: == string  ? "{id.upper()}" . "{id}"
}
```

⚠️ To check a type in Wide you just surround the Entity with `:ENTITY:` and check equality with the type alias in a Question case. You can use it in Match Expression!

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
    Math.PI * shape.radius ** 2;
  }
  shape.sideLength ** 2;
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

A List is created using `[]` symbols.

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
coordinates:= (10, 20)
location:= (-33.8688, 151.2093)
red:= (255, 0, 0)
paleBlue:= (173, 216, 230)
user:= ("john_doe", 30, "john.doe@example.com")
product:= ("Laptop", 1200.50, 5)
serverConfig:= ("localhost", 8080, "http")
today:= (2025, 5, 6)
gravity:= (0, -9.81, 0)

"Coordinates: {coodinates.1}, {coordinates.2}"
"Red: R({red.1}), G({red.2}), B({red.3})"
```

### Set

A Set is created using `{}` symbols.

Some examples:

```lua
roles:= {"admin", "editor", "viewer"}
productSkus:= {"A123", "B456", "C789"}
visitedUrls:= {"https://example.com", "https://openai.com", "https://github.com"}
daysOff:= {"Saturday", "Sunday"}
enabledFeatures:= {"dark_mode", "notifications", "auto_save"}
bannedUsers:= {"troll123", "spammer99", "bad_actor"}
tags:= {"python", "webdev", "tutorial"}
fruits:= {"apple", "banana", "mango"}
registeredIps:= {"192.168.1.10", "192.168.1.11", "10.0.0.2"}

-- Random results for sets

"This week you'll be off on {days_off.1}"
"I may take a {fruits.2} to eat now"
```

### Dictionary

A Dictionary is created using `{:}` symbols structure.

Some examples:

```lua
-- User profile data
user:= {
  "name": "Alice",
  "age": 30,
  "email": "<alice@example.com>",
  "isActive": True
}

"{user.name} is {user.age}"

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

"{post.title} by {post.author.name}"
"Tags: {post.tags.1}, {post.tags.2}, {post.tags.3}
```

### String

A String is created using `""` symbols structure.

Some examples:

```lua
message:= "Hello, Wide!"
name:= "Mary Alice"
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
numbers:= [10, 20, 30, 40, 50]

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
message:= "Hello, Wide!"

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

Enumeration is also implicit:

```lua
list = [1, 2, 3, 4, 5, 6]
list ~ (item) {
  "Item at {item.} is {item}"
  -- Item at 1 is 1
  "Item at {item[]} is {item}"
  -- Item at 0 is 1
}
```

### Destructive Iterations

You can get the index of the current iteration using `.` or `[]` after the name of the collection Entity.

```lua
numbers:= [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

~(number = numbers) {
  "Number at #{numbers.} is {number}"
  -- Number at #1 is 1
  -- "Number at #{numbers[]} is {number}"
  -- Number at #0 is 1
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

### Interrupting Repetition

```lua
$counter:= 1

~($counter <= 10) {
  "Counter value is: {counter}"

  $counter == 5 ? {
    "break, please!"
    || -- Wall operator used alone in line inside question body
  }

  -- you could do like so:
  ($counter == 5) || (
    "break, please!"
  )

  $counter % 2 == 0 ? {
    "continue, please!"
     >> -- Flow operator used alone in line inside questoin body
  }

  -- you could do like so:
  ($counter % 2 == 0) >> (
    "continue, please"
  )

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

**Wide one-based style**

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

**Classic Zero-based index**

```lua
range:= ~([6])
~(val = range) {
  "{val}" -- 0 1 2 3 4 5
}

-- no need for temporary entity
~(val = ([6])) {
  "{val}" -- 0 1 2 3 4 5
}
```

```lua
range:= ~([3:6])
~(val = range) {
  "{val}" -- 3 4 5
}

-- no need for temporary entity
~(val = ([3:6])) {
  "{val}" -- 3 4 5
}
```

```lua
range:= ~([3:10:2])

~(val = range) {
  "{val}" -- 3 5 7 9
}

-- no need for temporary entity
~(val = ([3:10:2])) {
   "{val}" -- 3 5 7 9
}
```

⚠️ In this documentation Wide syntax will use just One-based indexes.

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

⚠️ Parentheses are optional! `{}` are optional when no body make visibility bad.

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
    -- ';' to the end of line that returns
    "Less than 10";
  },
  > 10 => "Greater than 10" -- , comma is optional as well
  .  => "It's 10" -- cannot end with , comma as well
  -- . ❌ BUT cannot be empty
}

"{message}"
```

If you want to both return and print you it can you must enclose between `{}` and use the `;` Return Intent in the final of the returning expression.

You can also give a temporary name for the match expression:

```lua
item:= 10

times10:int = item ? {
  -- create a temporary "eq" name for the match expression case
  (item == 100) {hundred} =>  {
    "It's a hundred"
    hundred * 100;
  },
  = 11 {eq} => {
    "It's 11"
    eq * 10;
  },
  < 10 {lt} => {
    "Less than 10"
    lt * 10;
  },
  > 10 {gt} {
    "Greater than 10"
    gt * 10;
  }
  . {
    "It's 10"
    item * 10;
  }
}

"{message}"
```

As in the resolution case before, there's no need to name any of those match cases:

```lua
times10:int = item ? {
  -- create a temporary "eq" name for the match expression case
  (item == 100) =>  {
    "It's a hundred"
    item * 100;
  },
  = 11 => {
    "It's 11"
    item * 10;
  },
  < 10 => {
    "Less than 10"
    item * 10;
  },
  > 10 {
    "Greater than 10"
    item * 10;
  }
  . {
    "It's 10"
    item * 10;
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

⚠️ In Wide ()=> {} alone in a file is the Entry Function.

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
greet(name:string) => {} -- No return type
  "Hello, {name}!" -- No return value, will just print to screen

greet("World") -- Output: Hello, World!
```

### `;` Return Intent

The `;` Return Intent is used to mean that a value must be return.
It's the only place where it's used in Wide.

**Returning Values:**

To return values you use the `;` Return Intent at the end of the line that you want to return the value or resulting value from an expression.

Function that returns a message based single on parameter:

```lua
greet(name:string) string => {
  "Hello, {name}!";
}

greet("World") -- Doesn't output anything, just returned

""{greet("World")}"" -- Hello, World!


message: greet("World")
"{message}" -- Hello, World!
```

As you saw, the `;` Return Intent is used to return a value from a Function, but you can inline Functions when using the `=>` Lambda Intent alone. You don't need to use the Return Intent on inlined functions.

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

  $sum;
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

  sum;
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
  a + b;
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

But when used `{}` and a value must be returned, the `;` Return intent must be used:

```lua
add = (n:int, m:int) => {
  n + m; -- ; return intent
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
    1;
    2;
    3;
}

~(value = generator()) {
    "Value is {value}"
}

-- Will output: 1 2 3
```

You can go really fancy!

```lua
~(item = () ~> {
    1;
    2;
    3;
}) {
  "{item}"
}
```

⚠️ Notice it does not use `=>` like normal functions but `~>` instead.

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
division(n:int, m:int) int => {
  -- condition, message
  @(m == 0, "Cannot divide by {n} by {m}")
  n / m;
}

division(10, 0) ❌ -- Execution will stop immediatly
```

If you want to capture the error you can propagate using the empty `{}` Context Intent. When you want to check for the error you just prefix the entity name with `@` Event intent.

```lua
division(n:int, m:int) int => {
  @(m == 0, "Cannot divide by {n} by {m}"){}
  n / m;
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

  users;
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

  users;
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

## Function Special Return Cases

### HTML Fragment Return `<></>`

When working with Web projects that are HTML-heavy, Wide has some niceties for you!

Wide makes HTML Functional and Reactive by nature on the Web Browser.

The HTML Fragment `<></>` is used to enclose the HTML Function body no `{}` in this case.

⚠️ When you are building UI's you can also make your Entities reactive by just prefixing them with `@` Event Intent.

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

Functional Component can have body and return HTML Fragment.

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
  </>;
}
```

## Functional Object Programming 🤣

Here the Functional meet Object-Oriented and they live happy forever!

You are gonna be presented to the most important concepts of Wide Objects and how they can help your Intentions to Model real world scenarios.

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

### Resolution Objects

They are objects that you use to create concrete Object Entities and you can resolve them.

You create a concrete object by prefixing its name with `.`:

```lua
.Thing </>

thing:Thing = </>

-- or

thing: = <Thing/>
```

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
  .do:= true -- no need for []

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
/{Self}>
```

⚠️ That's not a keyword, you can name it whatever you want. Very likely `Self` will become standard convention mostly because like in Python and Rust.

```lua
.Thing <
  .do:= true
  .doSomething() => {
    this.do ? "Do something!"
  }
/{this}>
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

When mutable, you now can pass it in the object creation as HTML properties and mutate it at will, since it's Mutable, and when accessing there's no need to use `$`.

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

Objects can have static scope removing the (.) accessor on naming and usage.

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

The `.` Resolution Intent were removed from Entity and Function Object, what now when used outside?

Angry Birds mode! Outside you use the `..` Extent Intent (there's a phylosophical theory behind that, but let's skip that for now!)

```lua
Thing..do
Thing..doSomething()
```

But that's by design because other language that use `.` may not make the distinction between static. PHP and Rust use `::`, but in Wide it has other purpose: Traits!

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


thing:= Thing..newLambdaEntity -- not a function nor meta entity
thing.do ? thing.doSomething()

thing:= Thing..newStaticFunction() -- not a meta entity
thing.do ? thing.doSomething()
```

### Keyword-less `new`

Wide does not require or support the `new` keyword. Instead, object instantiation is expressed through a conventional `new()` method or factory-style functions.

The `new()` method is:

- Not a keyword
- Just a callable entity
- Often returns a self-like or related object
- May accept parameters for initialization

#### Example

```lua
.Dog <
  new() => () => <Dog/>
  makeSound() => "A dog is barking!"
/>

dog:= Dog..new()
dog.makeSound()

-- or just
Dog..new().makeSound()
```

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

  #[ -- private
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
- private *(using `#` - local to object)*

⚠️ In this documentation it made sense keep the OOP jargons, but for Wide core it has other names:

- contextual (*static*)
- resolvable (*public*)
- extendable (*protected*)
- individual (*private*)

They mean the same thing as in every OOPL.

Example of extending an Object:

```lua
.Thing <
  count:int -- static
  .name:string -- public
  ..value:obj -- protected

  #instance:Thing -- private

  count() int => count -- static
  .name() string => .name -- public
  ..(value) obj => .value -- protected
  #(instance) Thing => .instance ?. <Thing /> -- private
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
  `#instance:Thing` -- not extended

  count() int: count
  .name() string: .name
  ..value() obj: .value
  `#instance():Thing` -- not extended
/>
```

As you can see only the `#instance` Entity and `#intance()` weren't extended.

Somethings to notice:

**#1**
Static Entities or Functions are accessed without `.` Intent but with `..`.

**#2**
Non-static Entities or Functions are accessed with only one `.` Intent independent of their characteristic (`.`,`..`,`#`).

**#2**
When used inside an Object `.` Intent means both *Self* but never *static*.

**3**
Entities and Function can have the same name because `()` makes their distinction.

Special notice is due to the `#` private symbol. In Wide you can define constants and Enums using them. But how could you create constants inside Objects? At the end all you need is an Immutable Meta Entity or Immutable Static Entity to reproduce constants. But what about Enums? Yes! You can create them both, and the syntax gets clear enough for you that they are not a private members.

Look:

```lua
.Network {
  -- Constant
  #INITIAL_STATUS{int} = 0

  -- Enum
  #Status{int} <
    Disconnected = #INITIAL_STATUS
    Connected
    Error
  >

  -- cannot be used outside
  #privateMember:= true
  #anotherPrivate: string = "ok"
  #[
    groupedPrivateMember1:int = 1
    groupedPrivateMember2:int = 2
  ]
}

$status:Network.Status = Network.#Status..Disconnect

$status == #INITIAL_STATUS ? {
  $status = Network.#Status..Connected
}
```

⚠️ It's clear that `#INITIAL_STATUS` constant and `#Status` Enum are not a Private Entities.

The constant MUST be create using Generics and you can only use `=` Assignment Intent.

The Enumeration MUST be created using Generics and itself has `</>` body.

### Constructor Object Lambdas

Objects can have constructors that behaves as an Object Lambda.

The concept of **Constructor/Lambda Promotion** can be used, and when done the Entities you created inside the Object Lambda become Meta Entitities of the enclosing Object.

You must pass the Accessor to mean you want to promote.

Entities without the Acessor won't become Meta Entities and must be used just like ordinary parameters.

The most basic Object Lambda Looks like so:

```lua
.Thing <()/>

thing:Thing = <()/>

-- or

thing:= <Thing () />
```

Promoting Meta Entities from Constructor Lambda

```lua
.Thing <
  (
    .do:bool, -- Has Acessor, is promoted to Meta Entity
    ..what:string, -- Has Acessor, is promoted to Meta Entity
    #when:string = "Never!", -- Has Acessor, is promoted to Meta
    nothing: false, -- Has NOT, is NOT promoted
  ) => nothing ? "Doing nothing"

  .(doSomething) => {
    .do ? "{.what} will be done {.where}"
  }
/>

thing: <Thing (do: true, what: "Something", nothing: true )/> -- Doing nothing
thing.(doSomething) -- Something will be done Never!

thing: <Thing (do: true, what: "Something")/>
thing.(doSomething) -- Something will be done Never!

thing: <Thing (do: true, what: "Nothing", when: "Always!")/>
thing.(doSomething) -- Nothing will be done Always!
```

But you can make explict you intentions and separate constructor promoted entities line by line:

```lua
.Thing <
    #(when:string = "Never!")
    .(do:bool)
    ..(what:string)

    -- Object Function
    .(doSomething) => {
        .do ? "{.what} will be done {.where}"
    }
/>
```

**NOT promoted Entities**

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
      "{param}"
    }
  }
/>

thing: Thing = <(1, 2, 3, 4)/>

-- or

thing:= <Thing (1, 2, 3, 4)/>
```

### Abstract Extent Objects

If want to just blueprint an Object's Intents that provides or not some default behaviour you can abstract placing a `!` Not Intent before the Object's name, its Entities and/or Functions.

Protected, Public, Static Entities and Functions can't be abstracted and just used inside the abstract extent content.

```lua
-- Notice that ".." turned ".!"
.!Thing <
  -- static Entity cannot be abstracted but used in context
  thingName: "Thing"

  -- Notice that "." turned "!"
  !name:string

  -- Notice that "." turned "!"
  !instance:obj

  -- static Function cannot be abstracted but used in context
  thingName() => thingName

  -- Notice that "." turned "!"
  !instance() Thing -- abstract Function doesnt have body

  .name() string => {
    .name ?. (thingName); -- resolvable Function can have body
  }
/>
```

❌ If you don't provide implementation for everything marked as `!` Wide will break with an error.

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
    .name ?. "How is it possible for me not having a name?";
  }
/{Self}>
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
  -- default return ; or output from body

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
  -- default return ; or output from body
  <p>"Hello, {name} from Function"</p>;

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

  .(speak) => {
    "Shit!"
  }
/>

.Robot :Speaker, Mover <

  .(speak) => {
    "Bits and Shits!"
  }

  .(move) => {
    "Shifting bits >>>>>"
  }
/>

.TalkingCar :TalkingMover <

  .name:string = "Talking Car"

  .(speak) => {
    "Beep beep!"
  }

  .(move) => {
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
  .(sayHello) => {
    "Hello "
  }
/>

::Wide <
  .(sayWide) => {
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
  .(smallTalk) => {
    "a"
  }

  .(bigTalk) => {
    "A"
  }
/>

::B <
  .(smallTalk) => {
    "b"
  }

  .(bigTalk) => {
    "B"
  }
/>

.Talker <
  ::(A, B) {
    B.smallTalk(): A, -- uses A.smallTalk()
    A.bigTalk(): B -- uses B.bigTalk()
    -- aliasing
    B.bigTalk(): talk -- becomes B.talk()
  }
/>
```

You can change Trait's visibility:

```lua
.Talker <
  ::(A, B) {
    B.smallTalk(): B.., -- just change the Accessor
    A.bigTalk(): A# -- just change the Accessor
  }
/>
```

You can mix conflict resolution and aliasing

```lua
.Talker <
  ::(A, B) {
    B.(smallTalk): A.., -- Like if A..smallTalk()
    A.(bigTalk): B# -- Like if B#bigTalk()
    B.(bigTalk): #talk -- like if B#talk()
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
  .average( a:T b:T) T => (a + b) / 2
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
  #stack: []T

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
processData({T, U} input1: T, input2: U) T, U => {
  [input1, input2];
}

result:= processData{int, string}(10, "hello")
--  above result is of type [int, string]
```

Union types (|) allow a generic type to accept values of different types. This is useful when a function or component needs to handle a variety of input types.

```lua
handleInput{T}(input: T) T // T: string | int => {
  input;
}

strResult:= handleInput("world") -- strResult is of type string
numResult:= handleInput(20) -- numResult is of type int
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
  "{entity.name} is {entity.age} years old";
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

Enums are very close to Constants, but you can have behaviour and create it with Generics Type.

They are created using `#` prefixed to its name.

They're constants are accessed using the Static context with `..`.

⚠️ You don't use `#` when defining the Type, but when assigning values with them it makes it more explicit you are using enums, so in this examples they will be used.

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
  msg1:= #Message..Text(String::from("Hello!"));
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
#Serialize <
  -- Somewhere in code...
/>

#Message{T::Serialize} <
  Text(T),
  Binary(Vec{int}),
  Control(Command),
/>
```

## Attributes in Wide Language

In Wide, **attributes** are metadata-like constructs that can be applied to functions, meta entities, objects, and more — very much like annotations in other languages. But unlike traditional attributes, they are full-fledged **objects** in Wide, with support for inheritance, traits, macros, and default parameters.

Wide attributes are not just markers — they're living pieces of logic you can reason with.

### Attribute Binding in Wide

Wide supports annotations (called **attributes**) using a concise and composable syntax.

Attributes are declared using `@{}` Intents and contain one or more calls to functions and/or objects:

```lua
@{
  route(path: "/aircraft/{id}")
}
show(id:int) View => "..."
```

```lua
.Book<
  @{
    belongsTo(localKey:'author_id')
  }
  .author:Author

  @{
    belongsTo(localKey:'collection_id')
  }
  .collection:BookCollection
/>
```

### Multiple Attributes

You can chain multiple attributes inside the same block separated by commas:

```lua
.Book<
  @{
    belongsTo(localKey: "author_uuid"),
    inverse(inverseKey: "uuid")
  }
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
  @{
    <GetRoute path:"/books" />
  }
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

@{
  <Logged />
}
viewDashboard()

@{
  <Logged required=false, roles=["guest"] />
}
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

@{
  <AuditAttribute logLevel="DEBUG" />
}
deleteItem()
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

- Auto-generating methods (e.g., `toString()`)
- Validations (e.g., required fields)
- Dependency injection markers

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
