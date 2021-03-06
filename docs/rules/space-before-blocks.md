---
title: ESLint
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Require Or Disallow Space Before Blocks (space-before-blocks)

Consistency is an important part of any style guide.
While it is a personal preference where to put the opening brace of blocks,
it should be consistent across a whole project.
Having an inconsistent style distracts the reader from seeing the important parts of the code.

## Rule Details

This rule will enforce consistency of spacing before blocks. It is only applied on blocks that don’t begin on a new line.

This rule takes one argument. If it is `"always"` then blocks must always have at least one preceding space. If `"never"`
then all blocks should never have any preceding space. The default is `"always"`.

The following patterns are considered warnings when configured `"always"`:

```js
if (a){
    b();
}

if (a) {
    b();
} else{
    c();
}

function a(){}

for (;;){
    b();
}

try {} catch(a){}
```

The following patterns are not considered warnings when configured `"always"`:

```js
if (a) {
    b();
}

function a() {}

for (;;) {
    b();
}

try {} catch(a) {}
```

The following patterns are considered warnings when configured `"never"`:

```js
if (a) {
    b();
}

function a() {}

for (;;) {
    b();
}

try {} catch(a) {}
```

The following patterns are not considered warnings when configured `"never"`:

```js
if (a){
    b();
}

function a(){}

for (;;){
    b();
}

try{} catch(a){}
```

## When Not To Use It

You can turn this rule off if you are not concerned with the consistency of spacing before blocks.

## Related Rules

* [space-after-keywords](space-after-keywords.html
* [brace-style](brace-style.html

## Version

This rule was introduced in ESLint 0.9.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/space-before-blocks.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/space-before-blocks.md)
