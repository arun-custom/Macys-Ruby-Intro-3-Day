#Ruby Continued

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

```ruby
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