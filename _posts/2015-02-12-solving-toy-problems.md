---
title: "Solving Toy Problems"
---

Being able to communicate your thoughts effectively to your interviewers is one of
the most important skills to have as a software engineer. Recently I practiced
whiteboarding with a group of friends at Hack Reactor, and I am writing this blog to
note areas I'm looking to improve in based on the feedback I received.

## Toy Problem:
Given an array of items, identify the first item in an array that appear even number of times.

## Ask questions about inputs, outputs, and anything that is unclear.

Some example questions could be:

1. What can an input array contain? Can they contain strings, arrays, objects, etc?

2. What should we return as an output? For instance, if we are returning a number,
can it be stringified (e.g. '2') or should it just be a number?

3. What should be return when there is no item that appear even number of times?

4. Is there any time or space complexity constraints that we need to be aware of?

These questions not only strengthen your understanding of the problem, but they
also give you more time to think through the problem.

## Diagram it out

Create a diagram to come up with an algorithm to solve the problem. For this
problem, you can draw a simple array like [7, 'hi', 5, 7, 5] and determine how
a program will solve the problem.

## Look for edge cases

Look for more complicated versions of the problem. Depending on what the interviewer
answered for 1 in the questions above, you may have to take care of having inputs
such as [7, {a:1, b:2}, [2, 4, 5], {a:1, b:3}, 9, [2, 4, 5], 11]. Just like before,
diagram it out and determine how a program might solve the problem with this kind of input.

## Pseudocode

If you have a solid understand of the problem by clarifying via questions,
visualizing with diagrams, and being aware of the edge cases, you are well on your
way to dive into writing pseudocode.
