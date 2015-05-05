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

##Class Inheritance
- Methods can be shared from one class to another via inheritance.
- Inheritance in Ruby classes in done through the `<` operator.
- Let's take a simple example:

```ruby
class Bird  
	def preen
		puts "I am cleaning my feathers."
	end
	
	def fly
		puts "I am flying."
	end
end  
  
class Penguin < Bird
	def fly
		puts "Sorry. I'd rather swim."
	end
end  
  
animal = Penguin.new  
animal.preen  
animal.fly 
```

- In this example, the Penguin class inherits from Bird.
- Any method that is defined in the Bird class is now available in any **instance** of Penguin.

##Introduction to HTTP Requests
- In Ruby requests are handled through cURL.
- While you can create cURL requests straight from Ruby, using gems (third-party modules) is the preferred way.
- [HTTParty](https://github.com/jnunemaker/httparty) is one of the most widely-used.
- Since this is third-party code we will need to first download it and require it in the project:

```ruby
gem install httparty
```

- In order to use this new module in our project we will have to require it:

```ruby
require 'httparty'
```

- With the module required, we can now call each of the class methods it provides:

#####GET request

```ruby
HTTParty.get("URL here")
```

#####POST request

```ruby
HTTParty.post("URL here", 
	query: {
		name: "Arun's Wine",
		region: "California"
	}
```

##Using JSON Data in Ruby
- In order to actually use the JSON data that comes back from the API we need to parse it.
- Ruby has a built-in method called `JSON.parse`.
- Can you guess the structure of this method? How can we use it this way?

```
response = HTTParty.get("URL here")

json_response = JSON.parse(response.body)
```

##JSON API Exercise Part 1 - GET
- In this exercise we will practice using HTTParty to make requests to an API.
- We will start with the GET request.
- Step 1: Make a GET request out to `http://daretodiscover.herokuapp.com/wines`.
- Step 2: Parse the response body into JSON.
- Step 3: Create puts statements for each wine hash that will print each hash to the terminal.
- Step 4: Practice accessing hash values by now looping through the data and outputting each key and value to the terminal in a human-friendly way.
- Step 5: Repeat this process with a different loop or iterator.
- Step 6: Make sure that all of your logic from the above falls within a class.

##JSON API Exercise Part 2 - POST
- In this exercise we will practice using the POST HTTP method to create a new wine record.
- Step 1: Make a POST request out to `http://daretodiscover.herokuapp.com/wines` with wine data of your choice. Pay attention to what the keys should be called. This method should be inside of your class you created in part 1.
- Step 2: Call the method you created in part 1 to pull all of the wine records after the post request is finished.
- Bonus: Refactor the GET and POST requests using HTTParty into your own modules.