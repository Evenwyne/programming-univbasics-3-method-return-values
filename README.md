# Print, Puts, and Return Values

## Learning Goals

- Define and distinguish `puts` from `print`
- Identify implicit return values in Ruby syntax
- Recognize the explicit `return` keyword

## Introduction

There are a few ways to output text in Ruby. In previous lessons, we've used the
keyword `puts` in order to display text in the console, but we can also use
`prints`. How are these different? And when should you use one or the other?

Displaying text in the console is not the only type of _return value_ available
to us. When writing code, sometimes we'll want our methods to evaluate code and
_return_ a value, but not display it.

We'll cover how the `puts` and `print`commands display Ruby code to the console,
and the concept of return values in Ruby.

## Define and distinguish `puts` from `print`

The `puts` (short for "out**put s**tring") and `print` commands are both used to
display in the console the results of evaluating Ruby code. The primary
difference between them is that `puts` adds a new line after executing, and
`print` does not.

```ruby
3.times { print "Hello!" }
# > Hello!Hello!Hello!

3.times { puts "Hello!" }
# > Hello!
# > Hello!
# > Hello!
```

The methods `puts` and `print` are a great way to explicitly tell the program to
display specific information. Without these printing methods, Ruby will read the
line, but not print anything out.

## Identify implicit return values in Ruby syntax

By default, Ruby doesn't display any output, however, this doesn't mean that
nothing is happening. Methods like `puts` and `print` allow us to output text to
the console. This is actually different from Ruby's concept of a *return value*.

A _return value_ is the data returned to the program by the execution of a
method, the assignment of a variable, or other anything in Ruby. Everything has
a return value!

For example:

| Code                  | Return Value   |
|-----------------------|----------------|
| `"Hello world"`       | `"Hello world"`|
| `6 + 3`               | `9`            |
| `instructor = "Obama"`| `"Tim"`        |
| `total = 5 + 4`       | `9`            |
| `puts "hello world"`  | `nil`          |
| `print "hello world"` | `nil`          |

You may notice that the `puts` and `print` methods, when run in IRB, print
values on the screen and then display a line that says `=> nil`. This is because
`puts` and `print` may print the value you want, but instead of _returning_ that
value, they display the text but return `nil`.

## Recognize Implicit Return Values in Ruby Syntax

Methods are like vending machines. When you use a vending machine you just put
in two arguments, the number of the item you want to purchase (C7) and your
money. We know about how arguments work, but then your vending machine might do
two things: It will make a noise saying that everything worked (beep, beep!),
and then it gives you the soda. The soda is like the return type, but the sound
effects that you hear when you input the item number isn't something you can
use. `puts` works similarly: it tells you something and that's it.

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

Knowing how methods print and return values is crucial as you'll be using them
constantly in programs both big and small. Knowing the difference between puts
and return will help you avoid a common pitfalls.

Return values are how different parts of your program communicate with one
another. You don't have to worry too much about this for now, but as you start
to build more complicated programs, you'll find that the return value of one
method might be operated on by a subsequent method. Don't forget to watch out
for those `nil`s!

## Resources
["Understanding The Differences Between Puts, Print & P"](https://www.rubyguides.com/2018/10/puts-vs-print/)