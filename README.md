# Random::Formatter

This library formats generated random numbers in many manners.  When
<tt>'random/formatter'</tt> is required, several methods are added to empty core
module <tt>Random::Formatter</tt>, making them available as Random's instance
and module methods.

<tt>'random/formatter'</tt> is automatically required by SecureRandom.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'random-formatter'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install random-formatter

## Usage

Generate random hexadecimal strings:

```ruby
require 'random/formatter'

prng = Random.new
prng.hex(10) #=> "a170a3c41a89733899ba"
prng.hex(10) #=> "09f0ebd4197f4dd4aad9"
prng.hex(13) #=> "a2c57c4a5c4fdb5743ea6a8f0d"

Random.hex(10) #=> "538aa111119998b64bda"
Random.hex(10) #=> "66e341f9e2da4392ab8c"
Random.hex(13) #=> "2a2e973d5e2d4f3949b0fa613e"

SecureRandom.hex(10) #=> "52750b30ffbc7de3b362"
SecureRandom.hex(10) #=> "92b15d6c8dc4beb5f559"
SecureRandom.hex(13) #=> "39b290146bea6ce975c37cfc23"
```

Generate random base64 strings:

```ruby
prng.base64(10)         #=> "EcmTPZwWRAozdA=="
prng.base64(10)         #=> "KO1nIU+p9DKxGg=="
Random.base64(4)        #=> "bsQ3fQ=="
SecureRandom.base64(12) #=> "7kJSM/MzBJI+75j8"
```

Generate random binary strings:

```ruby
prng.random_bytes(10)         #=> "\016\t{\370g\310pbr\301"
Random.random_bytes(6)        #=> "\xA1\xE6Lr\xC43"
SecureRandom.random_bytes(10) #=> "\323U\030TO\234\357\020\a\337"
```

Generate alphanumeric strings:

```ruby
prng.alphanumeric(10)     #=> "S8baxMJnPl"
Random.alphanumeric(10)   #=> "aOxAg8BAJe"
SecureRandom.alphanumeric #=> "g8SWR7zbPK"

prng.alphanumeric         #=> "TmP9OsJHJLtaZYhP"

prng.alphanumeric(4,  chars: [*"0".."9"])  #=> "2952"
prng.alphanumeric(10, chars: [*"!".."/"]) #=> ",.,++%/''."
```

Generate UUIDs:

```ruby
prng.uuid         #=> "2d931510-d99f-494a-8c67-87feb05e1594"
Random.uuid       #=> "bad85eb9-0713-4da7-8d36-07a8e4b00eab"
SecureRandom.uuid #=> "f14e0271-de96-45cc-8911-8910292a42cd"

prng.uuid_v4      #=> "62936e70-1815-439b-bf89-8492855a7e6b"
prng.uuid_v7      #=> "0188d4c3-1e74-7085-b14f-ef6415dc6f31"
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/ruby/securerandom.

