#Introduction to Ruby Syntax

##A Little About Ruby
- To practice using Ruby we can use the Interactive Ruby (IRB) tool.
- Everything is an object.
- Everything that is manipulated is an object, and the results of those manipulations are objects.
- To compare to JS, you have prototypes on objects, such as array functions like .map or .reduce that you can call on instances of array objects.
- In Ruby everything is an object and you'll be able to use object methods on it all.

Let's take a look at some examples:

```
puts "Arun Sood".length
puts "Arun".index("A")
puts 35.even?
```

- We can tell that everything is an object, because everything has a "class":

```
"Arun Sood".class #String
4.class #Fixnum
[].class #Array
Object.class #Class
```

- Something like this `message = "Hello World"` is essentially the equivalent of `message = String.new("Hello World")`.

- There is little conversion of type:

####JS

```
console.log("Hello " + 4 + 2); //Hello 42
```

####Ruby

```
puts "Hello " + 4 + 2 #no implicit conversion of Fixnum into String
```

##Modules Versus Objects

####Modules
- Modules are like libraries.
- Usually used for containing a bunch of "helper" functions that you can call throughout your program.
- Great example is the [Math module](http://www.ruby-doc.org/core-2.1.4/Math.html) built into Ruby:

```
Math.sqrt(9) #3.0
```

####Objects
- Ruby is a proper object-oriented language.
- "Classes" wrap methods that are related to that object.
- Instead of prototypes in JS that relate to some object, we have classes that encapsulate methods.
- Classes can also inherit from other classes - this is called extension. We will get to this later.

```
class Car
	def initialize(color, make, model)
		@color = color
		@make = make
		@model = model
	end
	
	def drive
		puts "We are now driving!"
	end
	
	def paint(new_color)
		@color = new_color
		puts @color
	end
	
	def describe_car
		puts "We are driving in the #{@color} #{@make} #{@model}"
	end
end

Car.new("Red", "Honda", "Civic").paint("Blue")
```

##Getting User Data in IRB
- Ruby has a method called `gets` that allows you to retrieve data from the user typing into the console.
- This method is similar to `prompt` in JS.
- In order to prevent the input from receiving a new line each time you must call the `.chomp` method:

```
message = gets.chomp
```
##In-Class Lab #1
- We will create a simple string conversion tool that take in a string and alters it using our string class methods.
- First, write one `gets` statement that will take a string from our user.
- Create a class called `ConvertString` that will wrap our methods.
- Create an initializer that will set the given string to a class variable.
- Create 4 different methods that will apply 4 string class methods to the inputted string. You can reference them [here](http://www.ruby-doc.org/core-2.1.4/String.html).
- Output the resulting string to the console using `puts`.
- Instantiate the class using each of these methods.

##In-Class Lab #2
- Let's create a simple calculator using the Ruby Math module.
- First, write two `gets` statements that will take 2 numbers from our user.
- Create a class called `Calculator` that will wrap all of our methods.
- Create an `initializer` method that takes in the 2 numbers and sets them as class variables.
- Write at least 4 methods that perform different math operations and output the result using `puts`. You can reference them [here](http://www.ruby-doc.org/core-2.1.4/Math.html).
- Instantiate your class using each of these 4 methods.
- Bonus: As a bonus you can create a simple `if else` statement that will choose which method to pick based on a third `gets` input. We will talk about this in the afternoon so you will have to look this up.
- Bonus 2: Create another method that uses one of the Math constants in your operation.

## Hashes

- Hashes are just a key-value data structure.
- Let's make one:

```ruby
book_ratings = {
	"Stranger in a Strange Land" => 3,
	"2001: A Space Odyssey" => 5,
	"The Hitchhiker's Guide to the Galaxy" => 4,
	"War and Peace" => 5,
	"I, Robot" => 4
}
```

What if we wanted to get fancy?

```ruby
books_by_author = {
	"Asimov, Isaac" => {
		"I, Robot" => 4,
		"Foundation" => 5,
		"Foundation and Empire" => 5
	},
	"Tolstoy, Leo" => {
		"War and Peace" => 4,
		"Anna Karenina" => 5,
		"The Death of Ivan Ilyich" => 4
	},
	"Adams, Douglas" => {
		"The Hitchhiker's Guide to the Galaxy" => 4
	},
	"Heinlein, Robert" => {
		"Stranger in a Strange Land" => 3
	},
	"Clarke, Arthur, C." => {
		"2001: A Space Odyssey" => 5
	}
}
```

- What is one possible issue that you can think of with the above?
- Generally, you don't want to have very hard to manipulate long hash keys.
- So, let's go to something more straightforward.
- An actual use for hashes might be to count things, in, let's say a category. Let's consider a bookshelf, again, but this time, just count the number of books that are on the shelf, per genre:

```ruby
books_by_genre = {
	"pulp" => 3,
	"scifi" => 10,
	"nonfic" => 10,
	"comedy" => 4,
	"tragedy" => 5,
	"romance" => 0
}
```

##A Few Hash Use Cases

#####Let's find out all the genres:

```ruby
books_by_genre.keys
```

#####Let's find out the numbers of books, without the categories:

```ruby
books_by_genre.values
```

#####Let's see if the hash contains a certain genre:

```ruby
books_by_genre.include? "pulp"
```

#####How about deleting a genre entirely? I hate pulp. Easy:

```ruby
books_by_genre.keep_if do |k,v| 
	["scifi", "nonfic", "comedy", "tragedy", "romance"].include? k
end
```

#####or, a cleaner method:
```ruby
books_by_genre.reject { |k,v| k == "pulp" }
```

##Ruby "Mutator" and "Test" Methods
- Let's take a look at `books_by_genre` again.
- Was it modified?
- What if you use the `reject!` version?
- Do you see the pattern of having `?` and `!` at the end of method names?

##Accessing a Hash and Reassigning Values
- Let's take a look at this case:

```ruby
books_by_genre["pulp"] = 1000
```

- Reassigning to a hash key that already exists, doesn't create a new hash key with that value. Hash keys are unique. Collisions are overriden.
- What if we tried to use dot notation like in JavaScript?

```ruby
books_by_genre.pulp
> NoMethodError: undefined method `pulp' for #<Hash:0x00000105b03f28>
```

- To Access hash values you can either use the bracket with a string syntax like this:

```
books_by_genre["pulp"]
```

Or you can use the symbol syntax:

```
books_by_genre[:pulp]
```

## Some hash iterators

### Exercise: Let's output our hash with `.each`
#### Questions: Look it up, can you pass just the element to `.each`? What are the two parameters that you can pass to the block? What happens if you just pass one?

### Exercise: Map `books_by_genre` to an array of mini-hashes, where each mini-hash in the array contains something like: 

```ruby
[{ "pulp" => 3}, { "scifi" => 10 }, ... ]
```