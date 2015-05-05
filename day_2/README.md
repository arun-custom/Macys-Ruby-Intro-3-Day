#Ruby Continued

##Warmup
- Go through the arrays section of RubyMonk [here](https://rubymonk.com/learning/books/1-ruby-primer/chapters/1-arrays/).

##Array Methods

####.shift
- `.shift` will remove the first element of the array and return it.

```ruby
my_array = [1, 2, 3, 4]

my_array.shift # => 1
```

####.unshift
- `.unshift` will prepend objects to the front of the array, moving other elements upward.

```ruby
my_array = ["a", "b", "c"]

my_array.unshift("insert") # => ["insert", "a", "b", "c"]
```

####.take
- `.take` will return the first `n` elements of an array.

```ruby
my_array = [1, 2, 3, 4]

my_array.take(3) # => [1, 2, 3]
```

####.push
- `.push` will append an object to the end of an array.

```ruby
my_array = [1, 2, 3, 4]

my_array.push(5) # => [1, 2, 3, 4, 5]
```

####.pop
- `.pop` will remove the last element of the array and return it.

```ruby
my_array = [1, 2, 3, 4]

my_array.pop # => [1, 2, 3]
```

####.sort
- `.sort` will compare items in the array and sort them using the <=> operator.

```ruby
my_array = [1, 4, 2, 3]

my_array.sort # => [1, 2, 3, 4]
```

##Array Exercise
- Open the RubyMonk [array tutorial](https://rubymonk.com/learning/books/1-ruby-primer).
- Try these problems:
	- Find the length of strings in an array
	- Find the frequency of a string in a sentence
	- Select random elements from an array
	- Find non-duplicate values in an array
	- Check if all elements in an array are Fixnum
- Bonus: Try the "sort the words in a given sentence" challenge.

##Control Flow in Ruby
- Control flow allows you to direct the flow of the application depending on conditions.
- This follows the general flow of if - else with some nuances in the syntax.
- Let's take a simple example:

```ruby
name = "Arun"

if name == "Arun"
	puts "Hello Arun!"
elsif name == "Bob"
	puts "Hello Bob!"
end
```

##In-Class Lab
- Complete [rubymonk control structures subchapter](https://rubymonk.com/learning/books/1-ruby-primer/chapters/8-control-structures/).
- Complete [rubymonk objects and methods subchapter](https://rubymonk.com/learning/books/1-ruby-primer/chapters/6-objects/).

##Loops in Ruby
- There are a wide variety of loops in Ruby that make it versatile.
- There are a few different use cases for these loops, but mostly it just gives you flexibility.
- Let's look at a few examples.

#####Regular for loop
- For loops work with ranges.
- As a reminder, the two dots (..) mean inclusive of the last number, and the three dots (...) mean exclusive.

```ruby
for i in 0..5
	puts "Value of local variable is #{i}"
end
```

#####While loop
- While loops execute while a certain condition remains true.

```ruby
x = 100

while x > 0            
	x -= 1
	puts "This loop will run #{x} more times"
end
```

#####Until loop with global variables
- Until loops are similar to while loops with slightly different syntax.

```ruby
$i = 0
$num = 5

until $i > $num  do
	puts "Inside the loop i = #$i"
	$i += 1
end
```

#####Until with begin

```ruby
$i = 0
$num = 5

begin
	puts("Inside the loop i = #$i" )
	$i +=1;
end until $i > $num
```

#####Operation count
- These methods are usually reserved for if you need to perform an operation an exact number of times.

```ruby
10.times do |i|
	puts "Number is at #{i}"
end
```

#####Upto
- Upto is similar to times but is less popular.

```ruby
1.upto(3) do |i| 
	puts i * 2
end
```

##In-Class Lab
- We will be practicing iterators and loops.
- Complete the following [Ruby Monk iterators challenge](https://rubymonk.com/learning/books/1-ruby-primer/chapters/1-arrays/lessons/3-arrays-iteration).

##Arrays and Iterators Lab
- In this lab we will be practicing using iterators in combination with arrays to produce the results we are looking for.
- Let's start with these two arrays:

```ruby
user_names = ["Bob Jones", "Cindy Smith", "Kelsey Scott"]

user_emails = ["bob@gmail.com", "csmith@yahoo.com", "kscott@hotmail.com"]
```

- First let's start by using both loops and iterators to merge the two together.
- Your goal is to use two different approaches to merge the two arrays together so that the final structure looks like this:

```ruby
[
	["Bob Jones", "bob@gmail.com"],
	["Cindy Smith", "csmith@yahoo.com"],
	["Kelsey Scott", "kscott@hotmail.com"]
]
```

- Your goal is to replicate this effect with at least two implementations.
- After you finish this we will take it a step further and use our various iterators and loops to create a proper hash from this data.
- Your goal is to create a final structure that looks like this:

```ruby
[
	{
		name: "Bob Jones",
		email: "bob@gmail.com"
	},
	{
		name: "Cindy Smith",
		email: "csmith@yahoo.com"
	},
	{
		name: "Kelsey Scott",
		email: "kscott@hotmail.com"
	}
]
```