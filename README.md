![Ruby](http://ruby.gbaptista.com/assets/icons/ruby-24-82bb448ce050909d418384dab9eac0d45206d57e91974d7fdef8dcd8cd3662a7.png) ![Love](http://ruby.gbaptista.com/assets/icons/heart-24-32727c879e61bc07a0ed0ae911c9dcd6363b27c7705f7ede2f3557c1c3f41c77.png) Ruby Online Coding
=================
[http://ruby.gbaptista.com](http://ruby.gbaptista.com)

This repository is currently used for [issue tracking](https://github.com/gbaptista/ruby.gbaptista.com/issues) and you can also contribute to the official demos:

## Ruby Demos

#### Default snippets:

- Playground: [What time is it?](#what-time-is-it)
- Test Suite: [MiniTest](#minitest) - [Unit tests: Class](#unit-tests-class-1)
- Regular Expression: [Dummy email finder](#dummy-email-finder)

#### All demos:

* [Playground](#playground)
  - [What time is it?](#what-time-is-it)
  - [I love Ruby](#i-love-ruby)
  - [The famous Hello World](#the-famous-hello-world)
  - [The Greeter class](#the-greeter-class)
  - [The cities Array](#the-cities-array)
  - [Current Ruby infos](#current-ruby-infos)

* [Regular Expression](#regular-expression)
  - [Dummy email finder](#dummy-email-finder)
  - [Dummy url finder](#dummy-url-finder)

* [Test::Unit](#testunit)
  - [Behaviour Description](#behaviour-description)
  - [Unit tests: Empty template](#unit-tests-empty-template)
  - [Unit tests: Methods](#unit-tests-methods)
  - [Unit tests: Class](#unit-tests-class)

* [RSpec](#rspec)
  - [Behaviour Description](#behaviour-description-1)
  - [Spec tests: Empty template](#spec-tests-empty-template)
  - [Spec tests: Methods](#spec-tests-methods)
  - [Spec tests: Class](#spec-tests-class)

* [MiniTest](#minitest)
  - [Behaviour Description](#behaviour-description-2)
  - [Unit tests: Empty template](#unit-tests-empty-template-1)
  - [Unit tests: Methods](#unit-tests-methods-1)
  - [Unit tests: Class](#unit-tests-class-1)
  - [Spec tests: Empty template](#spec-tests-empty-template-1)
  - [Spec tests: Methods](#spec-tests-methods-1)
  - [Spec tests: Class](#spec-tests-class-1)

### Playground

_Ruby Version: **2.3.1**_

#### What time is it?

Playground Code:
```ruby
puts 'What time is it?'

puts "\n"

puts Time.now.strftime("%H:%M:%S (Time zone: '%Z')")
```
Snippet: [6QMxDw](http://ruby.gbaptista.com/playground/6QMxDw?demo=true)

#### I love Ruby

Playground Code:
```ruby
# Output "I love Ruby"
say = "I love Ruby"
puts say

# Output "I *LOVE* RUBY"
say['love'] = "*love*"
puts say.upcase

# Output "I *love* Ruby"
# five times
5.times { puts say }
```
Snippet: [iQ2K4Q](http://ruby.gbaptista.com/playground/iQ2K4Q?demo=true)

#### The famous Hello World

Playground Code:
```ruby
# The famous Hello World
# Program is trivial in
# Ruby. Superfluous:
#
# * A "main method"
# * Newline
# * Semicolons
#
# Here is the Code:

puts "Hello World!"
```
Snippet: [fP8daA](http://ruby.gbaptista.com/playground/fP8daA?demo=true)

#### The Greeter class

Playground Code:
```ruby
# The Greeter class
class Greeter
  def initialize(name)
    @name = name.capitalize
  end

  def salute
    puts "Hello #{@name}!"
  end
end

# Create a new object
g = Greeter.new("world")

# Output "Hello World!"
g.salute
```
Snippet: [aHi04A](http://ruby.gbaptista.com/playground/aHi04A?demo=true)

#### The cities Array

Playground Code:
```ruby
# Ruby knows what you
# mean, even if you
# want to do math on
# an entire Array
cities  = %w[ London
              Oslo
              Paris
              Amsterdam
              Berlin ]
visited = %w[Berlin Oslo]

puts "I still need " +
     "to visit the " +
     "following cities:",
     cities - visited
```
Snippet: [hCUAFA](http://ruby.gbaptista.com/playground/hCUAFA?demo=true)

#### Current Ruby infos

Playground Code:
```ruby
puts "Current Ruby infos:\n\n"

puts "Version:      #{RUBY_VERSION}"
puts "Patch Level:  #{RUBY_PATCHLEVEL}"
puts "Release Date: #{RUBY_RELEASE_DATE}"
puts "Platform:     #{RUBY_PLATFORM}"
```
Snippet: [DmsM-g](http://ruby.gbaptista.com/playground/DmsM-g?demo=true)

### Regular Expression
_Ruby Version: **2.3.1**_

#### Dummy email finder

Pattern:
```
(?<name>\w+)\@(?<domain>\w+\.\w+)
```

Text String:
```
Lorem ipsum dolor sit@amet.br, consectetur adipiscing elit.
Nulla a quam sed@magna.com dictum dignissim in a ante.
Donec sed dictum mauris. In in tellus@nec.io eros bibendum.
```

Snippet: [pfnmVA](http://ruby.gbaptista.com/regex/pfnmVA?demo=true)

#### Dummy url finder

Pattern:
```
https?:\/\/[\w|\.|-]+
```

Text String:
```
Lorem ipsum dolor http://r.lvm.io, consectetur adipiscing elit.
Nulla a quam http://ruby-lang.org dictum dignissim in a ante.
Donec sed dictum mauris. In in tellus eros bibendum.
```

Snippet: [8Efj4w](http://ruby.gbaptista.com/regex/8Efj4w?demo=true)

### Test::Unit
_Ruby Version: **2.3.1**_ | _Test::Unit Version: **3.2.0**_ | _Cucumber Version: **2.4.0**_

#### Behaviour Description
Plain Text Behaviour Description:
```gherkin
Feature: Showcase the simplest possible Cucumber scenario
  In order to verify that cucumber is
    installed and configured correctly
  As an aspiring BDD fanatic
  I should be able to run this scenario and see
    that the steps pass (green like a cuke)

  Scenario: Cutting vegetables
    Given a cucumber that is 30 cm long
    When I cut it in halves
    Then I have two cucumbers
    And both are 15 cm long
```

Test Code:
```ruby
Given /^a cucumber that is (\d+) cm long$/ do |length|
  @cucumber = MyCucumber.new(color: 'green', length: length.to_i)
end

When /^I (?:cut|chop) (?:it|the cucumber) in (?:halves|half|two)$/ do
  @choppedCucumbers = [
    { color: @cucumber.color, length: @cucumber.length / 2 },
    { color: @cucumber.color, length: @cucumber.length / 2 }
  ]
end

Then /^I have two cucumbers$/ do
  assert_equal(@choppedCucumbers.length, 2)
end

Then /^both are (\d+) cm long$/ do |length|
  @choppedCucumbers.each do |cuke|
    assert_equal(cuke[:length], length.to_i)
  end
end
```

Source Code:
```ruby
class MyCucumber
  attr_reader :color
  attr_reader :length

  def initialize(color: nil, length: 0)
    @color  = color
    @length = length
  end
end
```

Playground Code:
```ruby
puts MyCucumber.new(color: 'green', length: 2).color
```

Snippet: [7a0Gpg](http://ruby.gbaptista.com/test/7a0Gpg?demo=true)

#### Unit tests: Empty template

Test Code:
```ruby
class MyTest < Test::Unit::TestCase
  def test_something
    assert_true(true)
  end
end
```

Snippet: [1t1Z2g](http://ruby.gbaptista.com/test/1t1Z2g?demo=true)

#### Unit tests: Methods

Test Code:
```ruby
class TestMethods < Test::Unit::TestCase
  def test_add
    assert_equal(4, sum(2, 2))
    assert_equal(8, sum(5, 3))
  end

  def test_multiply
    assert_equal(6,  multiply(3, 2))
    assert_equal(32, multiply(4, 8))
  end
end
```

Source Code:
```ruby
def sum(x, y)
  x + y
end

def multiply(x, y)
  x * y
end
```

Playground Code:
```ruby
puts "2 + 2 = #{sum(2, 2)}"
puts "\n"
puts "3 x 2 = #{multiply(3, 2)}"
```

Snippet: [xMee8g](http://ruby.gbaptista.com/test/xMee8g?demo=true)

#### Unit tests: Class
Test Code:
```ruby
class TC_GreeterTest < Test::Unit::TestCase
  def test_say_hello
    assert_equal(
      Greeter.say_hello(%w(Lorem Ipsum Dolor)),
      [
        'Hello Lorem!',
        'Hello Ipsum!',
        'Hello Dolor!'
      ]
    )
  end
end
```

Source Code:
```ruby
class Greeter
  def self.say_hello(customers)
    customers.map do |customer|
      "Hello #{customer}!"
    end
  end
end
```

Playground Code:
```ruby
puts Greeter.say_hello(%w(Lorem Ipsum Dolor))
```

Snippet: [v8fzNg](http://ruby.gbaptista.com/test/v8fzNg?demo=true)

### RSpec

_Ruby Version: **2.3.1**_ | _RSpec Version: **3.5.0**_ | _Cucumber Version: **2.4.0**_

#### Behaviour Description
Plain Text Behaviour Description:
```gherkin
Feature: Showcase the simplest possible Cucumber scenario
  In order to verify that cucumber is
    installed and configured correctly
  As an aspiring BDD fanatic
  I should be able to run this scenario and see
    that the steps pass (green like a cuke)

  Scenario: Cutting vegetables
    Given a cucumber that is 30 cm long
    When I cut it in halves
    Then I have two cucumbers
    And both are 15 cm long
```

Test Code:
```ruby
Given /^a cucumber that is (\d+) cm long$/ do |length|
  @cucumber = MyCucumber.new(color: 'green', length: length.to_i)
end

When /^I (?:cut|chop) (?:it|the cucumber) in (?:halves|half|two)$/ do
  @choppedCucumbers = [
    { color: @cucumber.color, length: @cucumber.length / 2 },
    { color: @cucumber.color, length: @cucumber.length / 2 }
  ]
end

Then /^I have two cucumbers$/ do
  expect(@choppedCucumbers.length).to eq(2)
end

Then /^both are (\d+) cm long$/ do |length|
  @choppedCucumbers.each do |cuke|
    expect(cuke[:length]).to eq(length.to_i)
  end
end
```

Source Code:
```ruby
class MyCucumber
  attr_reader :color
  attr_reader :length

  def initialize(color: nil, length: 0)
    @color  = color
    @length = length
  end
end
```

Playground Code:
```ruby
puts MyCucumber.new(color: 'green', length: 2).color
```

Snippet: [RMMXfA](http://ruby.gbaptista.com/test/RMMXfA?demo=true)

#### Spec tests: Empty template

Test Code:
```ruby
RSpec.describe 'MyTest' do
  context 'test something' do
    it { expect(true).to be_truthy }
  end
end
```

Snippet: [SbY5Ag](http://ruby.gbaptista.com/test/SbY5Ag?demo=true)

#### Spec tests: Methods

Test Code:
```ruby
RSpec.describe 'Some Methods' do
  context '#sum' do
    it 'sum x + y' do
      expect(sum(5, 3)).to eq(8)
    end
  end

  context '#multiply' do
    it 'multiply x * y' do
      expect(multiply(4, 8)).to eq(32)
    end
  end
end
```

Source Code:
```ruby
def sum(x, y)
  x + y
end

def multiply(x, y)
  x * y
end
```

Playground Code:

```ruby
puts "2 + 2 = #{sum(2, 2)}"
puts "\n"
puts "3 x 2 = #{multiply(3, 2)}"
```

Snippet: [WX-LHQ](http://ruby.gbaptista.com/test/WX-LHQ?demo=true)

#### Spec tests: Class

Test Code:
```ruby
RSpec.describe Greeter do
  context '#say_hello' do
    it 'say hello to all customers' do
      expect(
        described_class.say_hello(%w(Lorem Ipsum Dolor))
       ).to eq(['Hello Lorem!', 'Hello Ipsum!', 'Hello Dolor!'])
    end
  end
end
```

Source Code:
```ruby
class Greeter
  def self.say_hello(customers)
    customers.map do |customer|
      "Hello #{customer}!"
    end
  end
end
```

Playground Code:
```ruby
puts Greeter.say_hello(%w(Lorem Ipsum Dolor))
```

Snippet: [vnK8ZA](http://ruby.gbaptista.com/test/vnK8ZA?demo=true)

### MiniTest

_Ruby Version: **2.3.1**_ | _MiniTest Version: **5.9.0**_ | _Cucumber Version: **2.4.0**_

#### Behaviour Description

Plain Text Behaviour Description:
```gherkin
Feature: Showcase the simplest possible Cucumber scenario
  In order to verify that cucumber is
    installed and configured correctly
  As an aspiring BDD fanatic
  I should be able to run this scenario and see
    that the steps pass (green like a cuke)

  Scenario: Cutting vegetables
    Given a cucumber that is 30 cm long
    When I cut it in halves
    Then I have two cucumbers
    And both are 15 cm long
```

Test Code:
```ruby
Given /^a cucumber that is (\d+) cm long$/ do |length|
  @cucumber = MyCucumber.new(color: 'green', length: length.to_i)
end

When /^I (?:cut|chop) (?:it|the cucumber) in (?:halves|half|two)$/ do
  @choppedCucumbers = [
    { color: @cucumber.color, length: @cucumber.length / 2 },
    { color: @cucumber.color, length: @cucumber.length / 2 }
  ]
end

Then /^I have two cucumbers$/ do
  assert_equal(@choppedCucumbers.length, 2)
end

Then /^both are (\d+) cm long$/ do |length|
  @choppedCucumbers.each do |cuke|
    assert_equal(cuke[:length], length.to_i)
  end
end
```

Source Code:
```ruby
class MyCucumber
  attr_reader :color
  attr_reader :length

  def initialize(color: nil, length: 0)
    @color  = color
    @length = length
  end
end
```

Playground Code:
```ruby
puts MyCucumber.new(color: 'green', length: 2).color
```

Snippet: [w0h8lQ](http://ruby.gbaptista.com/test/w0h8lQ?demo=true)

#### Unit tests: Empty template

Test Code:
```ruby
class MyTest < Minitest::Test
  def test_something
    assert true
  end
end
```

Snippet: [h4pl7w](http://ruby.gbaptista.com/test/h4pl7w?demo=true)

#### Unit tests: Methods

Test Code:
```ruby
class TestSomeMethods < Minitest::Test
  def test_add
    assert_equal 4, sum(2, 2)
    assert_equal 8, sum(5, 3)
  end

  def test_multiply
    assert_equal 6,  multiply(3, 2)
    assert_equal 32, multiply(4, 8)
  end
end
```

Source Code:
```ruby
def sum(x, y)
  x + y
end

def multiply(x, y)
  x * y
end
```

Playground Code:
```ruby
puts "2 + 2 = #{sum(2, 2)}"
puts "\n"
puts "3 x 2 = #{multiply(3, 2)}"
```

Snippet: [6jecVg](http://ruby.gbaptista.com/test/6jecVg?demo=true)

#### Unit tests: Class

Test Code:
```ruby
class TestMeme < Minitest::Test
  def setup
    @meme = Meme.new
  end

  def test_that_kitty_can_eat
    assert_equal "OHAI!", @meme.i_can_has_cheezburger?
  end

  def test_that_it_will_not_blend
    refute_match /^no/i, @meme.will_it_blend?
  end
end
```

Source Code:
```ruby
class Meme
  def i_can_has_cheezburger?
    "OHAI!"
  end

  def will_it_blend?
    "YES!"
  end
end
```

Playground Code:
```ruby
puts Meme.new.i_can_has_cheezburger?
```

Snippet: [68p2CQ](http://ruby.gbaptista.com/test/68p2CQ?demo=true)

#### Spec tests: Empty template

Test Code:
```ruby
describe 'MyTest' do
  describe 'something' do
    it { true.must_equal true }
  end
end
```

Snippet: [9URkrQ](http://ruby.gbaptista.com/test/9URkrQ?demo=true)

#### Spec tests: Methods

Test Code:
```ruby
describe 'Some Methods' do
  describe '#sum' do
    it 'sum x + y' do
      sum(5, 3).must_equal 8
    end
  end

  describe '#multiply' do
    it 'multiply x * y' do
      multiply(4, 8).must_equal 32
    end
  end
end
```

Source Code:
```ruby
def sum(x, y)
  x + y
end

def multiply(x, y)
  x * y
end
```

Playground Code:
```ruby
puts "2 + 2 = #{sum(2, 2)}"
puts "\n"
puts "3 x 2 = #{multiply(3, 2)}"
```

Snippet: [FL8FQg](http://ruby.gbaptista.com/test/FL8FQg?demo=true)

#### Spec tests: Class

Test Code:
```ruby
describe Meme do
  before do
    @meme = Meme.new
  end

  describe "when asked about cheeseburgers" do
    it "must respond positively" do
      @meme.i_can_has_cheezburger?.must_equal "OHAI!"
    end
  end

  describe "when asked about blending possibilities" do
    it "won't say no" do
      @meme.will_it_blend?.wont_match /^no/i
    end
  end
end
```

Source Code:
```ruby
class Meme
  def i_can_has_cheezburger?
    "OHAI!"
  end

  def will_it_blend?
    "YES!"
  end
end
```

Playground Code:
```ruby
puts Meme.new.will_it_blend?
```

Snippet: [w3MIdw](http://ruby.gbaptista.com/test/w3MIdw?demo=true)
