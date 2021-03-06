and and or
===

In a comment on [Ruby Stylista](http://www.pathf.com/blogs/2008/10/ruby-stylista/), I mentioned how I use the `and` and `or` keywords in Ruby. To refresh, `and` and `or` work just like `&&` and `||`, only with very low precedence. For example:

	foo = 5 && 10; foo
	  => 10
	foo = (5 && 10); foo;
	  => 10
	foo = 5 and 10; foo
	  => 5
	(foo = 5) and 10; foo
	  => 5

You can see from the examples how the expression is 'grouped' by the very low precedence of `and` and `or`. Since they have such low precedence, I use them to create conditional execution, to tie two imperative statements together. For example, you could write:

	foo = fubar() if do_something()

This reverses the order of execution, putting the clause `do_something()` after `foo = fubar()` even though it will happen in the opposite order. If you wish to write them in temporal order, you can use `and`:

	do_something() and foo = fubar()

This puts "first things first." Likewise you can use `or` to reverse the order of an `unless` statement. Instead of:

	raise 'fubar' unless do_something()

You could write:

	do_something() or raise 'fubar'

Again putting the first thing first. I normally only do this if both clauses are imperative. In other words, I would not rewrite either of these statements because the predicate is a query with no side-effects:

	foo = fubar() if something.blank?
	raise 'fubar' unless something?

The predicate seems less important than the consequent, which suggests that it should come second even though the test is performed first.

---

Recent work:

* "[CoffeeScript Ristretto](http://leanpub.com/coffeescript-ristretto)", "[Kestrels, Quirky Birds, and Hopeless Egocentricity](http://leanpub.com/combinators)" and my [other books](http://leanpub.com/u/raganwald).
* [Cafe au Life](http://recursiveuniver.se), a CoffeeScript implementation of Bill Gosper's HashLife written in the [Williams Style](https://github.com/raganwald/homoiconic/blob/master/2011/11/COMEFROM.md).
* [Katy](http://github.com/raganwald/Katy), a library for writing fluent CoffeeScript and JavaScript using combinators.
* [Method Combinators](https://github.com/raganwald/method-combinators), a CoffeeScript/JavaScript library for writing method decorators, simply and easily. 

---

[Reg Braithwaite](http://braythwayt.com) | [@raganwald](http://twitter.com/raganwald)