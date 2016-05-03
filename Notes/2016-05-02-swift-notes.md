---
layout: post
title: Swift学习笔记
---

# Swift Learning Notes
---
>Swift can be thought of as Objective-C reimagined using modern concepts and safe programming patterns. In Apple's own words, Swift is like Objective-C without
the C. Chris Lattner, the creator of Swift, said Swift took language ideas from Objective-C, Rust, Haskell, Ruby, Python, C#, CLU, and far too many others to list. At WWDC 2014, Apple really stressed that Swift was safe by default. Swift was designed to eliminate many common programming errors, making applications more secure and less prone to bugs. Swift 2 added two additional core features to the language—availability and error handling—which are designed to make it even easier to write safe code.

## Getting started with Playgrounds

>Playgrounds are interactive work environments that let us write code and see
the results immediately.

## How does Playgournds open the debug area

You can open it manually by pressing the shift + command + Y keys together. The debug area is so userful.

## Swfit Language Syntax

### Comments

Writing comments in Swift code is a little different from writing comments in Objective-C code. 

**Double slash \\\\** for single line comments
**/\* and \*/** for multi line comments

What has changed is how we document the parameters and the return value. To document any parameter, we use the :parm:  eld, and for the return value, we use the :return:  eld.

### Semicolons
The semicolons are optional in Swift;

### Parentheses
The parentheses around conditional statements are optional

### Curly Braces
The the curly bracket is required after statements

### An assignment operator does not return a value
In Swift, this statement is not valid. Using an assignment operator (=) in a conditional statement (if and while) will throw an error. 

### Spaces are optional in conditional and assignment statements
For both conditional (if and while) and assignment (=) statements, the white spaces are optional.

