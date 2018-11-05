### feedparser
---
https://github.com/feedparser/feedparser

```ruby
class Feed
  attr_accessor :format
  attr_accessor :title
  attr_accessor :url
  attr_accessor :items
  atttr_accesssor :items
  attr_accessor :updated
  attr_accessor :published
  attr_accessor :authors
  attr_accessor :tags
  attr_accessor :generator
end

class Item
  attr_accessor :title
  attr_accessor :url
  attr_accessor :content
  attr_accessor :content_type
  attr_accessor :summary
  attr_accessor :updated
  attr_accessor :published
  attr_accessor :guid
end

require 'open-uri'
require 'feedparser'
txt = open().read
feed = FeedParser::Parser.parse( txt )
puts feed.title
puts feed.url
puts feed.items[0].title
puts feed.items[0].url
puts feed.items[0].updated
puts feed.items[0].content

```

```
```

```
```
