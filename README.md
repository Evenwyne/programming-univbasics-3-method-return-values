# Return Values

## Learning Goals

- Identify implicit return values in Ruby syntax
- Recognize the explicit `return` keyword

## Introduction

As you learned when studying _expressions_, Ruby returns a value when it
_evaluates_ an _expression_. This is called, suitably, the return value of an
expression.

_Methods_ also have return values. Let's study how they work.

## Identify Implicit Return Values in Ruby Syntax

Ruby uses something called _implicit return_ which means that the last
expression in a method's _implementation_ is the return value of the method
itself.

```ruby
def a_method(a, b)
  puts "hi"
  a + b
end

a_method(1,2) #=> 3
```

In the _implementation_, we didn't have to assign the return value to a
variable. All you have to do is put an expression right before the `end` and
ruby will evaluate it. In other programming languages like JavaScript ***you
must*** explicitly say:

```javascript
{
 ...
 return 1 + 2
}
```

But Ruby likes for you to be able to type less and realizes that in most
methods there's a return value. So you don't have to type the word `return`.
Yay!

Be very careful. Recall that the return value of `puts` and `print` is `nil`.

***A VERY COMMON BUG FOR NEW RUBYISTS IS THE FOLLOWING:***

```ruby
def a_method(a,b)
  puts "I got #{a}"
  puts "I got #{b}"
  sum = a + b
  puts "I got #{sum}"
end

a_method(2,3) #=> nil
```

It's very easy to see the error here, especially if you pay attention to the
return values of your expressions. The return value of `puts` is always `nil`!


| Code                  | Return Value   |
|-----------------------|----------------|
| `"Hello world"`       | `"Hello world"`|
| `6 + 3`               | `9`            |
| `instructor = "Tim"`  | `"Tim"`        |
| `total = 5 + 4`       | `9`            |
| `puts "hello world"`  | `nil`          |
| `print "hello world"` | `nil`          |

> **Moment for Meta-Learning**: If these return values are surprising or don't
> make sense, test things out in IRB and / or review lessons in Programming as
> Conversation Part 1.

As you might recall from Programming as Conversation 2: `p` prints _as well as
returns the input_. That might be the right tool, depending on your situation.

## Recognize the Explicit `return` Keyword

Speaking of _explicit_ return like in JavaScript (and Java, and Python for that
matter!) Ruby _does_ have an explicit return command. Rubyists typically use it
to exit early from a method with a specific return value.

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
case, `"Martha Stewart"`), and then stop the remainder of the lines won't even
be seen!

The explicit use of the `return` keyword is generally avoided by many Rubyists,
but there are instances where you might want to use `return` instead of relying
on implicit returns. In the following method, we create a variable `name`.

"Interrupting" explicit returns are often used to shortcut long processes,
particularly when working with large collections of data. To see the value of
this, we'll need to learn more about collection data types, but that's the
subject of our next module.

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

* ["Understanding The Differences Between Puts, Print & P"](https://www.rubyguides.com/2018/10/puts-vs-print/)
