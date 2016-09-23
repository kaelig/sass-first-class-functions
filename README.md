# First class functions in Sass 3.5.0

[Sass 3.5.0 introduces first-class functions](https://medium.com/@kaelig/sass-first-class-functions-6e718e2b5eb0#.qwhfp297u)
with a new function: `get-function($name)`

Release notes: http://blog.sass-lang.com/posts/809572-sass-35-release-candidate

Release notes don't show any code using `get-function`,
so let's see how it actually works…

## Get started

Either read the contents of [index.scss](index.scss) and [index.css](index.css), or play around with it locally:

1. Clone this repository
1. cd into it
1. Install Sass 3.5.0 RC: `bundle install`
1. Run the Sass watcher: `bundle exec sass index.scss:index.css --watch --sourcemap=none`
1. Play around with it!

## Making sense out of first-class functions

This is the way we've called function so far:

```scss
@function foo($x) { @return $x; }
foo('bar'); // -> 'bar'

// DEPRECATED: WILL BREAK IN Sass 4.0.0
call('foo', 'bar'); // -> 'bar'
```

Specifying a function name to `call` is deprecated, and
won't work in Sass 4.0.0, so what's the new way?

### Calling functions in Sass 3.5.0 and up

As of Sass 3.5.0, you need to call functions by passing `get-function`.

```scss
@function foo($x) { @return $x; }
call(get-function('foo'), 'bar'); // -> 'bar'

call(
	get-function('foo'),
	'It works :)');
call(
	get-function(foo),
	'(even without quotes)');
```

### Assigning a function to a variable

```scss
call(
	$foo,
	'You can now assign a function to a variable');
$foo: get-function(foo);
call($foo, 'bar'); // -> 'bar'
```

Unfortunately, `$foo('bar')` does not work.

It will fail to compile and you'll get this error:

> Error: get-function("foo") isn't a valid CSS value.

## License

Public domain.
