# Return Values

## Learning Goals

- Identify implicit return values in Ruby syntax
- Recognize the explicit `return` keyword

## Introduction

To display content in the console we can use `puts` and `print`. However, they don't
give a _return value_. When writing code, sometimes we'll want our methods to
evaluate code and _return_ a value &mdash; not just output text, but return it to the
the place that invoked the method.

We'll cover the concept of return values in Ruby, and how this actually differs
from `puts` and `print` commands.

## Identify Implicit Return Values in Ruby Syntax

Methods like `puts` and `print` allow us to output text to the console. This is
actually different from Ruby's concept of a _return value_.

A _return value_ is the data returned to the program by the execution of a
method, the assignment of a variable, or, generally, the evaluation of any
expression in Ruby. In Ruby, wherever there's an expression, there's a
return value. Everything has a return value!

For example, try pasting these lines into IRB (make sure to include the
double-quotes around the strings):

| Code                  | Return Value   |
|-----------------------|----------------|
| `"Hello world"`       | `"Hello world"`|
| `6 + 3`               | `9`            |
| `instructor = "Tim"`  | `"Tim"`        |
| `total = 5 + 4`       | `9`            |
| `puts "hello world"`  | `nil`          |
| `print "hello world"` | `nil`          |


Ruby still returns a value after evaluation, even though it we didn't "do"
anything. It returns the value of the last executed instruction,
which, in these examples, may have been a string declaration, variable
declaration, a calculation, or a call to `puts`.

However, when we use `puts` and `print` methods in IRB, you can see the output
on the screen _and_ a line displayed after it that says `=> nil`. This is because
`puts` and `print`  print the value you want, but instead of _returning_ that
value, they return `nil`. This means that the method has not returned a value.

Some people think it's strange that `puts` and its friends don't have a return
value. But what would that be? That the human at the end of the screen saw the
value and paid attention to it? It kind of makes sense, from a certain point of
view.

## Recognize Implicit Return Values in Ruby Syntax

Methods are like vending machines. When you use a vending machine you just put
in two arguments, the number of the item you want to purchase (C7) and your
money. We know about how arguments work, but then your vending machine might do
two things: It will make a noise saying that everything worked (beep, beep!),
and then it gives you the soda. The soda is like the return type, but the sound
effects that you hear when you input the item number isn't something you can
use. Similarly to the "beep beep", `puts` tells you something happened, to your
senses (your ears) but it's not what returns back, that's the delicious, fizzy
soda.

Every method in Ruby returns a value by default. This returned value will be the
value of the last statement.

For example, let's look at this method called `restaurant`:

```ruby
def restaurant
  restaurant_name = "Guy's American Kitchen & Bar"
  cuisine = "american"
  motto = "Welcome to Flavor Town!"
end
```

The return value of the `restaurant` method would be `"Welcome to Flavor Town!"`
because that was the last statement evaluated.

Say you're a chef, like Guy Fieri. To make a method that just prints your name
and returns `nil`, you could write:

```ruby
def print_name
  puts "Guy Fieri"
end
```

To write a method that returns your name but doesn't print anything, you could write:

```ruby
def return_name
  "Guy Fieri"
end
```

To both print and return your name, you could write:

```ruby
def print_and_return_name
  puts "Guy Fieri"
  "Guy Fieri"
end
```
If you accidentally switched the order of the lines inside the method:

```ruby
def broken_print_and_return_name
  "Guy Fieri"
  puts "Guy Fieri"
end
```

The method would instead print "Guy Fieri" and return `nil`. This is because the
last line that was evaluated was `puts ...` and the return value of a `puts`, as
seen in the table above, is always `nil`.

**PUZZLE**: Keep in mind that `p` _does_ return what it output. How would that
change these return values?

## Recognize the Explicit `return` Keyword

There is one other way to return a value from a method, and that is to use the
`return` keyword.

Let's take a look:

```ruby
def stylish_chef
  best_hairstyle = "Guy Fieri"
  return "Martha Stewart"
  "Guy Fieri"
end
```

What do you expect the return value of the above method to be? Using IRB, copy
and paste the above method and call it.

You may have expected the return value to be "Guy Fieri". His name is the last
line of the method. *However*, the return value of the above method is actually
`=> Martha Stewart`!

The `return` keyword will disrupt the execution of your method. If you employ
it, your method will return whatever you have explicitly told it to (in this
case, `"Martha Stewart"`), and then stop.

The explicit use of the `return` keyword is generally avoided by many Rubyists,
but there are instances where you might want to use `return` instead of relying
on implicit returns. In the following method, we create a variable `name`.

## Conclusion

Knowing how methods return values is crucial as you'll be using them constantly
in programs both big and small. Knowing the difference between `puts` and
`print`, and return values will help you avoid a common pitfalls.

Return values are how different parts of your program communicate with one
another. You don't have to worry too much about this for now, but as you start
to build more complicated programs, you'll find that the return value of one
method might be operated on by a subsequent method. Don't forget to watch out
for those `nil`s!

## Resources
["Understanding The Differences Between Puts, Print & P"](https://www.rubyguides.com/2018/10/puts-vs-print/)
