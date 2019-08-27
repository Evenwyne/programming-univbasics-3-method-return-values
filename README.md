# Return Values

## Learning Goals

- Identify implicit return values in Ruby syntax
- Recognize the explicit `return` keyword

## Introduction

As you learned when studying _expressions_, Ruby returns a value when it
_evaluates_ an _expression_. This is called the return value of an expression.

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

a_method(1,2) #=> 3 (the return value of a + b when a is set to 1 and b is set to 2)
```

As opposed to _implicit return_ there is _explicit return_. If Ruby required
_explicit return_, the previous method would look like:

```ruby
def a_method(a, b)
  puts "hi"
  return a + b
end

a_method(1,2) #=> 3 (the return value of a + b when a is set to 1 and b is set to 2)
```

In the _implementation_, we don't have to use the `return` keyword for the
result of the final expression to be passed back.

> **DANGER!** Recall that the return value of `puts` and `print` is `nil`.
> Because of this, sometimes you'll "see" what you expect to return
> thanks to `puts`, **but** the method _actually_ returns `nil` because
> `puts` returns `nil`!

```ruby
def a_method(a,b)
  puts "I got #{a}"
  puts "I got #{b}"
  sum = a + b
  puts "I got #{sum}"
end

a_method(2,3) #=> nil
```

If you pay attention to the return values of your expressions, you will see the
error here. The return value of `puts` is always `nil`!

| Code                  | Return Value   |
|-----------------------|----------------|
| `"Hello world"`       | `"Hello world"`|
| `6 + 3`               | `9`            |
| `instructor = "Tim"`  | `"Tim"`        |
| `total = 5 + 4`       | `9`            |
| `puts "hello world"`  | `nil`          |
| `print "hello world"` | `nil`          |

> **Moment for Meta-Learning**: If these return values are surprising or don't
> make sense, test things out in IRB and/or review lessons in Programming as
> Conversation Part 1.

The `p` method prints _as well as returns the input_. Depending on your code,
that might be the right tool to avoid this "surprise."

## Recognize the Explicit `return` Keyword

While  JavaScript, Java and Python require _explicit return_, , Ruby _does not_.
Given that, why is there a `return` keyword at all? Rubyists typically use it to
exit early from a method.

Let's take a look:

```ruby
def stylish_chef
  return "Martha Stewart"
  "Guy Fieri"
end
```

What do you expect the return value of the above method to be? Using IRB, copy
and paste the above method and call it.

You may have expected the return value to be "Guy Fieri." His name is the last
line of the method. *However*, the return value of the method is actually
`=> Martha Stewart`!

The `return` keyword will "short-circuit" the execution of your method. If you employ
it, your method will return whatever you have explicitly told it to (in this
case, `"Martha Stewart"`) ***and then skip over the remaining code in the method***.

Explicit return is often used to avoid slow or costly calculations. For example,
updating all the data about the NYSE stock market is very computationally demanding.
In the method that starts doing such an update, you might want to "guard" against
doing that work by testing whether or not it's the weekend (when the NYSE is closed).

```ruby
def get_stock_market_data(date)
  return nil if is_a_weekend?(date)
  # Imagine an expensive, slow calculation hereafter
end
```

## Conclusion

Knowing how methods return values is crucial since you'll be using them constantly
in programs both big and small. Knowing the difference between `puts` and
`print`, and return values will help you avoid a common pitfall.

Return values are how different parts of your program communicate with one
another. You don't have to worry too much about this for now, but as you start
to build more complicated programs, you'll find that the return value of one
method might be operated on by a subsequent method. Don't forget to watch out
for those `nil`s!

## Resources

* ["Understanding The Differences Between Puts, Print & P"](https://www.rubyguides.com/2018/10/puts-vs-print/)
