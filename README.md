Talenha is a programming language.

It serves for generating code. You can learn the default language, it needs to start with [<<[ and end with ]>>] to write code:
example:
<code>
[<<[
  print("ok")
  x = 1,
  if (x = 0) { print("0") } else { print(x) }
  
]>>]  
</code>

The main purpose of Talenha is to generate code. It is a web site with a text editor included into the web site and it handle a system folder to write files.

To generate code, you can use DSL (Domain Specific Language) that you can create yourself.

For example:
<code>
[<<csv[
1,1
1,2
1,3
]>>]  
</code>

It is a csv data. And with Talenha, you can read the csv. Like this:

<code>
[<<[
  u = [<<csv[
  1,1
  1,2
  1,3
  ]>>],
  
  foreach(e from u) {
    print(u(e,0) ":" u(e,1))
  }
]>>]  
</code>

Concatenation of string is obtained with no operator. Now,

<code>
[<<[

  a = 1,
  b = a a a,
  c = b + 1,
  print(b) // print 111
  print(c) // print 112
  
]>>]  
</code>

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





  Gool
