# rb-codemod-react-proptypes-upgrade
script to find all types of imports of prop types and replace


```
#! /usr/bin/env ruby
# `find . -name \*js | xargs ./replace.rb`
require 'pp'

#puts ARGV[0]
ARGV.each do |arg|
  begin
    lines = File.read(arg).split("\n")

    matches = lines.any? do |line|
      line.match(/(import .*\{.*)PropTypes(.*\} from 'react';)/)
    end

    if matches
      puts arg
    end
  rescue ArgumentError
    puts "Argument error #{arg}"
  end
end
```
