---
layout: post
title:  "Some Thoughts on Variable Declarations"
date:   2016-06-08 03:04:50 +0000
---


Having gone through training thus far in Java and Ruby, one of the more interesting differences between the two languages has been the strict requirements of variable declarations in Java as opposed to Ruby, which allows variable declaration and reassignment with virtually no restrictions.

For example, take the following code, first written in Java:

List<Dog> dogList = new LinkedList<>();
int numDogs = 0;
Dog puppy = new Dog("Fido", 2);
dogList.add(puppy);
numDogs += 1;

Now take essentially the same program written in Ruby:

dog_list = []
num_dogs = 0
puppy = Dog.new("Fido", 2)
dog_list << puppy
num_dogs += 1

Functionally, the programs do essentially the same thing.  Ruby stores arrays in an ArrayList-style structure by default with standard index calls, so the "[]" data structure is not performing the same function in terms of storing Dog objects or calling them as the Java version, but aside from that factor (which certainly affects efficiency, on a side note) the programs are the same.  Understandably, as everything in coding involves getting things done faster, one might be tempted to say that the Ruby version is superior to Java.  While Ruby allows for rapid development, there are a few advantages to the Java version of this simple program when you consider a more complex system.

First, by requiring variable type declarations, Java builds error throwing into its program to prevent its list from storing illegal information.  In the Ruby version of this program, a programmer from a completely different area of a (theoretically more complex) program could theoretically call on the dog_list array and insert a Cat object with impunity.  While the programmer could solve this issue by throwing in an if block that checks whether the object being pushed to dog_list is actually a Dog, this functionality is built into Java through use of generics.

Similarly, variable declarations prevents the "puppy" variable from being tampered with in the future.  Suppose we pushed puppy into the dog_list / dogList array.  Now, another programmer gains access and changes puppy's object reference to refer to a Cat.  Ruby, theoretically, would accept such a change without issue.  Not only would the variable reassignment work, but the array also would accept the object reference change.  Java, however, would throw two errors from this, one because puppy must be assigned to a Dog object reference, and second because the array uses generics to accept only Dog objects, not Cat objects.

Although a programmer could address this problem in Ruby through encapsulation, such techniques necessary limit the possibilities of whatever program the programmer is building.
