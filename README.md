# What is it ?

Talenha is a programming language and a rules definition language to construct a DSL with splitters system and transformation rules.

# But, what can I say to someone about Talenha ?

Talenha is a meta-programming language designed to create domain-specific languages (DSLs) through a system of splitters and transformation rules.
It focuses on generating and transforming source code.

# What makes it different

Talenha is not just a programming language.

It is a language for building languages.

It allows you to:

- DSL creation and usage inside the language itself
- text transformation system
- structured parsing with splitters
- code generation oriented design

# How it works ?

Talenha uses a delimited execution model.

## Level 1

It serves for generating code. You can learn the default language, it needs to start with [<<[ and end with ]>>] to write code:

The language operates inside [<<[ ... ]>>] blocks.

example:
<code>
[<<[
  print("ok")
  x = 1,
  if (x = 0) { print("0") } else { print(x) }
  
]>>]  
</code>

The main purpose of Talenha is to generate code.

## Level 2

To generate code, you can use DSL (Domain Specific Language) that you can create yourself.

For example:
<code>
[<<csv[
1,1
1,2
1,3
]>>]
</code>

This DSL can then be processed directly inside Talenha.

# Level 3

It is a csv data. And with Talenha, you can read the csv. Like this:

<code>
[<<[
  u = [&lt;&lt;csv[
1,1
1,2
1,3
]>>],
  
  foreach(e from u) {
    print(u(e,0) ":" u(e,1))
  }
]>>]
</code>



# Level 4

Concatenation of string is obtained with no operator. Now, I show an example of implicit concatenation and arithmetic evaluation rules.

<code>
[<<[

  a = 1,
  b = a a a,
  c = b + 1,
  print(b) // print 111
  print(c) // print 112
  
]>>]  
</code>

# Features


On top of that, you can define custom DSLs using a transpiler system.

## DSL

You can create your own DSL by writing this in Talenha:

<code>
[<<[
  create transpiler python {
    splitter { ... }
    ...
    rule start [ ... ] {
      ....code in talenha... // it handles a variable input that handle a list and who is relevant to your parsing result.
    }
    
  }
]>>]
</code>

## Functions

You can write functions in Talenha.

<code>
[<<[
  fun callMyFunction[global](x) {
    global = 2,
    print(x)
  }
   global = 1,
   callMyFunction(1),
   print(global)
]>>]
</code>

A function is usable in any file in Talenha.

## Sandbox functions

In Talenha, you can write:

<code>
[<<[
   x = sandbox{closure}[global](parameters) {
     ....code...
   },
   
]>>]
</code>

Now, x is a sandbox function. The function can be passed to a function by parameters and you can call your function by using x(params...).

## Select statement

In Talenha, you can write:

<code>
[<<[
  key = "apple",
  select(key) {
    apple  {
      ...code..
    },
    orange {
      ...code...
    }, ...
  }
]>>]
</code>

You can create a switch with the select function.

## Jump statement

In Talenha, you can use jump statement in a select statement.

<code>
[<<[
   x = 1,
   select {
     loop {
       x = x + 1,
       if (x > 10) { jump "stop" } else { jump "loop" }
     },
     stop { print("end") },
     default { jump "loop" }
   }
]>>]
</code>

You can compose exceptions with the help of jump statement.

## Jump as an exception

<code>
[<<[
fun callFunction(x) {
  if (x == 0) { jump "error" }
}

select {
  default {
    callFunction(0)
  },
  error {
    ...handle error...
  }
}
]>>]
</code>

# Concepts

Talenha is inspired by low-level assembly-like thinking applied to text generation and transformation.

The goal is to treat code as structured data that can be parsed, transformed, and regenerated.

# Architecture (high level)

It is a web site with a text editor included and it handles a system folder to write files.

- Web-based editor (IDE-like interface)
- File system abstraction
- AST-based function storage
- MySQL persistence layer for functions and transformations

⚠️ These implementation details are separate from the language core.

# Status

This project is a research-oriented language design focused on code generation and DSL construction. It has been used in experimental environments for code generation in a web-based system.







