# ActiveRecordQueryCounter

[![Build Status](https://travis-ci.org/bdurand/active_record_query_counter.svg?branch=master)](https://travis-ci.org/bdurand/active_record_query_counter)
[![Maintainability](https://api.codeclimate.com/v1/badges/21094ecec0c151983bb1/maintainability)](https://codeclimate.com/github/bdurand/active_record_query_counter/maintainability)

This gem injects itself into ActiveRecord to count the number of queries, the number of rows returned, and the amount of time spent on queries within a block.

The intended use is to gather instrumentation stats for finding hot spots in your code.

## Usage

The behavior must be enabled on your database connection adapter from within an initializer.

```ruby
ActiveRecordQueryCounter.enable!(ActiveRecord::ConnectionAdapters::PostgreSQLAdapter)
```

Next you must specify the blocks where you want to count queries.

```ruby
ActiveRecordQueryCounter.count_queries do
  do_something
  puts "Queries: #{ActiveRecordQueryCounter.query_count}"
  puts "Rows: #{ActiveRecordQueryCounter.row_count}"
  puts "Time: #{ActiveRecordQueryCounter.query_time}"
end
```
