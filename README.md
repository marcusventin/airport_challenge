Airport Challenge
=================

```
        ______
        _\____\___
=  = ==(____MA____)
          \_____\___________________,-~~~~~~~`-.._
          /     o o o o o o o o o o o o o o o o  |\_
          `~-.__       __..----..__                  )
                `---~~\___________/------------`````
                =  ===(_________)

```

## Motivation
This project enables a user to simulate basic airport / airplane interactions

## Features
Airports can instruct airborne planes to land and grounded planes to take off. A random stormy weather variable keeps budding air traffic controllers on their toes though!

## How to Use
Airport methods:
NAME = Airport.new(capacity) - creates a new instance of Airport. Default capacity is set to 5.
.land(plane) - lands a plane at the airport (if there's space!).
.take_off(plane) - launches a plane from the airport (if it's at that airport!).

NAME = Plane.new - creates a new instance of Plane. New planes have their location in the air, which is not very realistic.

.ground - updates a plane's location to ground.

.air - updates a plane's location to air.

Weather.new - rolls the virtual die to determine whether it's sunny or stormy.

## Sample IRB Interaction
% irb \n
3.0.2 :001 > require "./lib/airport" \n
 => true \n
3.0.2 :002 > gatwick = Airport.new \n
 => #<Airport:0x000000014e2e9b50 @capacity=5, @hangar=[]>  \n
3.0.2 :003 > luton = Airport.new \n
 => #<Airport:0x000000014e125788 @capacity=5, @hangar=[]> \n
3.0.2 :004 > and_simple = Plane.new \n
 => #<Plane:0x000000013f826b68 @location=:air> \n
3.0.2 :005 > ex = Plane.new \n
 => #<Plane:0x000000013e82d3d8 @location=:air> \n
3.0.2 :006 > gatwick.land(and_simple) \n
 => [#<Plane:0x000000013f826b68 @location=:ground>] \n
3.0.2 :007 > luton.land(and_simple) \n
/airport_challenge/lib/airport.rb:13:in `land': This plane has already landed! (RuntimeError) \n
	from (irb):7:in `<main>' \n
	from /.rvm/rubies/ruby-3.0.2/lib/ruby/gems/3.0.0/gems/irb-1.3.5/exe/irb:11:in `<top (required)>' \n
	from /.rvm/rubies/ruby-3.0.2/bin/irb:23:in `load' \n
	from /.rvm/rubies/ruby-3.0.2/bin/irb:23:in `<main>' \n
3.0.2 :008 > luton.take_off(and_simple) \n
/Projects/airport_challenge/airport_challenge/lib/airport.rb:22:in `take_off': Your plane is in another airport! (RuntimeError) \n
	from (irb):8:in `<main>' \n
	from /.rvm/rubies/ruby-3.0.2/lib/ruby/gems/3.0.0/gems/irb-1.3.5/exe/irb:11:in `<top (required)>' \n
	from /.rvm/rubies/ruby-3.0.2/bin/irb:23:in `load' \n
	from /.rvm/rubies/ruby-3.0.2/bin/irb:23:in `<main>' \n
3.0.2 :009 > luton.take_off(ex) \n
/Projects/airport_challenge/airport_challenge/lib/airport.rb:21:in `take_off': This plane is already in the air! (RuntimeError) \n
	from (irb):9:in `<main>' \n
	from /.rvm/rubies/ruby-3.0.2/lib/ruby/gems/3.0.0/gems/irb-1.3.5/exe/irb:11:in `<top (required)>' \n
	from /.rvm/rubies/ruby-3.0.2/bin/irb:23:in `load' \n
	from /.rvm/rubies/ruby-3.0.2/bin/irb:23:in `<main>' \n
3.0.2 :010 > gatwick.take_off(and_simple) \n
 => #<Plane:0x000000013f826b68 @location=:air> \n

















Instructions
---------

* Feel free to use google, your notes, books, etc. but work on your own
* If you refer to the solution of another coach or student, please put a link to that in your README
* If you have a partial solution, **still check in a partial solution**
* You must submit a pull request to this repo with your code by 9am Monday morning

Steps
-------

1. Fork this repo, and clone to your local machine
2. Run the command `gem install bundler` (if you don't have bundler already)
3. When the installation completes, run `bundle`
4. Complete the following task:

Task
-----

We have a request from a client to write the software to control the flow of planes at an airport. The planes can land and take off provided that the weather is sunny. Occasionally it may be stormy, in which case no planes can land or take off.  Here are the user stories that we worked out in collaboration with the client:

```
As an air traffic controller 
So I can get passengers to a destination 
I want to instruct a plane to land at an airport

As an air traffic controller 
So I can get passengers on the way to their destination 
I want to instruct a plane to take off from an airport and confirm that it is no longer in the airport

As an air traffic controller 
To ensure safety 
I want to prevent landing when the airport is full 

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

As an air traffic controller 
To ensure safety 
I want to prevent takeoff when weather is stormy 

As an air traffic controller 
To ensure safety 
I want to prevent landing when weather is stormy 
```

Your task is to test drive the creation of a set of classes/modules to satisfy all the above user stories. You will need to use a random number generator to set the weather (it is normally sunny but on rare occasions it may be stormy). In your tests, you'll need to use a stub to override random weather to ensure consistent test behaviour.

Your code should defend against [edge cases](http://programmers.stackexchange.com/questions/125587/what-are-the-difference-between-an-edge-case-a-corner-case-a-base-case-and-a-b) such as inconsistent states of the system ensuring that planes can only take off from airports they are in; planes that are already flying cannot take off and/or be in an airport; planes that are landed cannot land again and must be in an airport, etc.

For overriding random weather behaviour, please read the documentation to learn how to use test doubles: https://www.relishapp.com/rspec/rspec-mocks/docs . There’s an example of using a test double to test a die that’s relevant to testing random weather in the test.

Please create separate files for every class, module and test suite.

In code review we'll be hoping to see:

* All tests passing
* High [Test coverage](https://github.com/makersacademy/course/blob/main/pills/test_coverage.md) (>95% is good)
* The code is elegant: every class has a clear responsibility, methods are short etc. 

Reviewers will potentially be using this [code review rubric](docs/review.md).  Referring to this rubric in advance will make the challenge somewhat easier.  You should be the judge of how much challenge you want this at this moment.

**BONUS**

* Write an RSpec **feature** test that lands and takes off a number of planes

Note that is a practice 'tech test' of the kinds that employers use to screen developer applicants.  More detailed submission requirements/guidelines are in [CONTRIBUTING.md](CONTRIBUTING.md)

Finally, don’t overcomplicate things. This task isn’t as hard as it may seem at first.

* **Submit a pull request early.**

* Finally, please submit a pull request before Monday at 9am with your solution or partial solution.  However much or little amount of code you wrote please please please submit a pull request before Monday at 9am.
