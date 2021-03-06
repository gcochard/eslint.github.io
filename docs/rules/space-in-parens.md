---
title: ESLint
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow or enforce spaces inside of parentheses (space-in-parens)

Some style guides require or disallow spaces inside of parentheses:

```js
foo( 'bar' );
var x = ( 1 + 2 ) * 3;

foo('bar');
var x = (1 + 2) * 3;
```

## Rule Details

This rule will enforce consistency of spacing directly inside of parentheses, by disallowing or requiring one or more spaces to the right of `(` and to the left of `)`. In either case, `()` will still be allowed.

### Options

There are two options for this rule:

* `"always"` enforces a space inside of parentheses
* `"never"` enforces zero spaces inside of parentheses (default)

Depending on your coding conventions, you can choose either option by specifying it in your configuration:

```json
"space-in-parens": [2, "always"]
```

#### always

When `"always"` is set, the following patterns are considered warnings:

```js
foo( 'bar');
foo('bar' );
foo('bar');

var foo = (1 + 2) * 3;
(function () { return 'bar'; }());
```

The following patterns are not warnings:

```js
foo();

foo( 'bar' );

var foo = ( 1 + 2 ) * 3;
( function () { return 'bar'; }() );
```

#### never

When `"never"` is used, the following patterns are considered warnings:

```js
foo( 'bar');
foo('bar' );
foo( 'bar' );

var foo = ( 1 + 2 ) * 3;
( function () { return 'bar'; }() );
```

The following patterns are not warnings:

```js
foo();

foo('bar');

var foo = (1 + 2) * 3;
(function () { return 'bar'; }());
```

#### Exceptions

An object literal may be used as a third array item to specify exceptions, with the key `"exceptions"` and an array as the value. These exceptions work in the context of the first option. That is, if `"always"` is set to enforce spacing, then any "exception" will *disallow* spacing. Conversely, if `"never"` is set to disallow spacing, then any "exception" will *enforce* spacing.

The following exceptions are available: `["{}", "[]", "()", "empty"`].

For example, given `"space-in-parens": [2, "always", { "exceptions": ["{}"] }]`, the following would be warnings:

```js
foo( {bar: 'baz'} );
foo( 1, {bar: 'baz'} );
```

And the following patterns would *not* be warnings:

```js
foo({bar: 'baz'});
foo( 1, {bar: 'baz'});
```

Or, given `"space-in-parens": [2, "never", { "exceptions": ["{}"] }]`, the following would be warnings:

```js
foo({bar: 'baz'});
foo(1, {bar: 'baz'});
```

And the following patterns would *not* be warnings:

```js
foo( {bar: 'baz'} );
foo(1, {bar: 'baz'} );
```

Given `"space-in-parens": [2, "always", { "exceptions": ["[]"] }]`, the following would be warnings:

```js
foo( [bar, baz] );
foo( [bar, baz], 1 );
```

And the following patterns would *not* be warnings:

```js
foo([bar, baz]);
foo([bar, baz], 1 );
```

Or, given `"space-in-parens": [2, "never", { "exceptions": ["[]"] }]`, the following would be warnings:

```js
foo([bar, baz]);
foo([bar, baz], 1);
```

And the following patterns would *not* be warnings:

```js
foo( [bar, baz] );
foo( [bar, baz], 1);
```

Given `"space-in-parens": [2, "always", { "exceptions": ["()"] }]`, the following would be warnings:

```js
foo( ( 1 + 2 ) );
foo( ( 1 + 2 ), 1 );
```

And the following patterns would *not* be warnings:

```js
foo(( 1 + 2 ));
foo(( 1 + 2 ), 1 );
```

Or, given `"space-in-parens": [2, "never", { "exceptions": ["()"] }]`, the following would be warnings:

```js
foo((1 + 2));
foo((1 + 2), 1);
```

And the following patterns would *not* be warnings:

```js
foo( (1 + 2) );
foo( (1 + 2), 1);
```

The `"empty"` exception concerns empty parentheses, and works the same way as the other exceptions, inverting the first option.

For example, given `"space-in-parens": [2, "always", { "exceptions": ["empty"] }]`, the following pattern would be a warning:

```js
foo( );
```

And the following pattern would *not* be a warning:

```js
foo();
```

Or, given `"space-in-parens": [2, "never", { "exceptions": ["empty"] }]`, the following pattern would be a warning:

```js
foo();
```

And the following pattern would *not* be a warning:

```js
foo( );
```

You can include multiple entries in the `"exceptions"` array. For example, given `"space-in-parens": [2, "always", { "exceptions": ["{}", "[]"] }]`, the following patterns would be warnings:

```js
bar( {bar:'baz'} );
baz( 1, [1,2] );
foo( {bar: 'baz'}, [1, 2] );
```

And the following pattern would *not* be warnings:

```js
bar({bar:'baz'});
baz( 1, [1,2]);
foo({bar: 'baz'}, [1, 2]);
```

## When Not To Use It

You can turn this rule off if you are not concerned with the consistency of spacing between parentheses.

## Related Rules

* [space-in-brackets](space-in-brackets.html

## Version

This rule was introduced in ESLint 0.8.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/space-in-parens.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/space-in-parens.md)
