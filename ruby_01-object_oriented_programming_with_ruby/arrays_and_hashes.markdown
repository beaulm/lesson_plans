---
title: Arrays & Hashes
length: 90
tags: ruby, arrays, hashes, data structures
---

## Learning Goals

* Develop a mental model to understand Arrays
* Develop a mental model to understand Hashes
* Gain some familiarity with common array and hash methods

## Structure

* 5 - Warmup
* 25 - Introducing Arrays
* 5 - Break
* 25 - Introducing Hashes
* 5 - Break
* 25 - Practicing with Arrays & Hashes

## Lesson

### Warmup

For this lesson your warmup is to build things. You have less than five minutes to:

* Take your five paper cups and use a marker to number them "0" through "4"
* Take four of your wooden beads and tie a white hanger tag around each of them
* Leave your remaining beads in a pile

### Arrays

Arrays are the most fundamental collection type in programming. Just about every language has them. Arrays are collections of data where each element is addressed by an arbitrary number called the *index* or *position*.

Let's model some of the core concepts.

*NOTE*: When doing these exercises in irb/pry, you'll want to first define a `Bead` class by running the instruction `class Bead; end` in that irb/pry session.

1. Lay down your large piece of paper and write `data` in large letters. This is the name of your collection. How many elements are in your collection so far?
2. Put the empty `0` cup on the paper. If you now fetched the value inside `data[0]`, what would you get back?
3. Store a bead into the zero cup, the equivalent of maybe `data[0] = Bead.new`. What would you expect the answer of `data.count` to be?
4. We can explicitly set the value of another cup. Add `data[1] = Bead.new`. That does note change the answer to `data.first`, but does change `data.last`. Why?
5. The "shovel" operator (`<<`) adds an element to the end of an existing array. Pretend you ran `data << Bead.new`. How many beads are in the array in total?
6. It turns out that "shovel" is just syntactic sugar for the method named `push`. Pretend you ran `data.push(nil)`. How does that affect your array? What is the value of `data.count` now?
7. Sometimes you want to add an element to the *beginning* of an array. You do that with `data.unshift(Bead.new)`. But wait a minute. You can't add the cup with marker `4` to the beginning of `data`. What do you do?
8. You can also insert data into a specific location. Say you ran `data.insert(3, Bead.new)`. How does that change things?
9. You can remove the last element of an array by running `data.pop`. Do that now.
9. If you run `.shuffle` on an array it creates a copy of the array with the values shuffled in random order. But you only have enough cups for one array. How about you run `data = data.shuffle`?
10. There's a ton you can do with *enumerable* methods. But the fundamental enumerator is the method `each`. On the side of your paper, write the output for this code: `data.each{|b| puts "Bead Size: #{b.size}mm"}` and guess the size of each bead in millimeters

Got it? Here are the important concepts you've seen:

* You can directly assign a value to a location in an array using `[]`
* You can access the value stored at a position by using `[]`
* You can add an element to the end of an array with `<<` or `.push`
* You can remove an element from the end of an array with `.pop`
* You can add an element to the front of an array with `.unshift`. (*Note*: though not included above, `.shift` pulls off the front element)
* The `insert` method takes two arguments: first is the position where you want to insert the data, the second is the data to be inserted
* `shuffle` returns a copy of your array with the elements randomly jumbled up
* `each` is an *enumerable* method which takes a block parameter and runs that block once for *each* element in the collection.

For a little different explanation / further reading, check out the [arrays section of Ruby in 100 Minutes](http://tutorials.jumpstartlab.com/projects/ruby_in_100_minutes.html#7.-arrays).

### Introducing Hashes

Hashes are the second most important data structure in Ruby. Like an Array, a Hash is a data structure used for representing a _collection_ of things. But whereas an Array generally represents a **list** of things (ordered, identified by numeric position), we use a Hash to represent a collection of *named* values. In a Hash, we can insert arbitrary data by labeling it with an identifying name (we'll look at what kind of names get used in a moment) and later retrieve it using the same name.

Some languages call their Hashes *dictionaries* for this reason -- you look up a word (the label) to retrieve its definition (the data or value with which the label was associated). 

#### Arts & Crafts

For this section, we'll walk through performing some common Hash operations both in code using IRB and in a physical model using some basic supplies.

You'll need these supplies:

1. A small bag
2. A handful of small labels with strings attached
3. A handful of beads with holes in the middle that you can thread a label through

Follow along with the instructor as you walk through the following operations:

1. Creating a new hash
2. Adding a new key/value pair to a hash using `[]=`
3. Reading the value of a key from a hash using `[]` and using `fetch`
4. Contemplating the egalitarian nature of a Hash as an unordered society
5. Attempting to set a value for a key that already exists -- consider uniqueness of the keys in a hash
6. Retrieving a list of keys from the hash
7. Retrieving a list of values from a hash
8. Counting the number of key/value pairs in a hash
9. Enumerating a hash using `each`

For these examples, consider using a hash called data and a simple `Bead` class to represent the beads we're inserting into the hash.

```ruby
class Bead
end

data = {} # or data = Hash.new
data["T"] = Bead.new # set a value in the hash
data["T"]
data.fetch("T")
data["U"]
data.fetch("U")
bead_one = Bead.new
bead_two = Bead.new
data["T"] = bead_one
data["T"] == bead_one # => true
data["T"] = bead_two
data["T"] == bead_one # => false (keys in a hash are unique)
data.values
data.keys
data.count
data.each do |key, value|
  puts "Key is: #{key} and Value is: #{value}"
end
```

#### Discussion -- Relative Simplicity of a Hash

There aren't nearly as many useful methods on hashes as there are on arrays. Mostly we just store things in there and fetch them out later using the key.

#### Takeaways

* You create a hash with `data = {}` or `data = Hash.new`
* Hashes contain key-value pairs. The key is the name that used to find the data. The value is the data that the pair stores.
* You can assign a key-value pair with bracket notation like `data[some_key] = some_value`
* Key names must be unique. If you already had a key named `"X"` then said `data["X"] = new_value` then you would *not* be creating a second key with the name `"X"`. You would be replacing the old value associated with `"X"` with the `new_value` (discarding the old value).
* You can run `.each` on a hash and it's sometimes a valuable things to do -- but it's a bit weird/unpredictable because hashes are unordered

### Practicing with Arrays and Hashes

Read through the [Hashes section of Ruby in 100 Minutes](http://tutorials.jumpstartlab.com/projects/ruby_in_100_minutes.html#8.-hashes) to pickup a bit more.

Unfortunately that's the end of Arts & Crafts time, boohoo. Fire up that `irb` and run the through the same sequences of steps for both an Array and a Hash to see if your mental model matches up with the real results in code.

*Bonus mind bending*: What if you store an array inside an array? A hash inside an array? An array as the data in a hash? Some unholy mishmash of all these things?
