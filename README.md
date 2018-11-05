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
txt = open( 'http://openfootball.github.io/feed.xml' ).read
feed = FeedParser::Parser.parse( txt )
puts feed.title
puts feed.url
puts feed.items[0].title
puts feed.items[0].url
puts feed.items[0].updated
puts feed.items[0].content

txt = open( 'http://openfootball.github.io/feed.json' ).read
feed = FeedParser::Parser.parse( txt )
puts feed.items[0].title
puts feed.items[0].url
puts feed.items[0].url
puts feed.items[0].updated
puts feed.items[0].content_text

require 'microformats'
text =<<HTML
<article class="h-entry">
  <h1 class="p-name">Microformats are amazing</h1>
  <p>Published by
    <a class="p-author h-card" href="http://example.com">!. Developer</a>
      on <time class="dt-published" datetime="2018-11-06 12:00:00">18<sup>th</sup> June 2018</time>
  <p class="p-summary">In which I extoll the virtues of using microformats.</p>
  <div class="e-content">
    <p>Blah blah blah</p>
  </div>
</article>
HTML
feed = FeedParser::Parser.parse( text )
puts feed.format
puts feed.items.size
puts feed.items[0].authors.size
puts feed.items[0].content_html
puts feed.items[0].content_text
puts feed.items[0].title
puts feed.items[0].summary
puts feed.items[0].published
puts feed.items[0].authors[0].name

require 'open-uri'
require 'feedparser'
require 'erb'
FEED_URLS = [
  'http://vienna-rb.at/atom.xml',
  ''http://www.ruby-lang.org/en/feeds/atom.xml,
  'http://www.ruby-lang.org/en/feeds/news.rss',
  'http://oepnfootball.github.io/feed.json'
]
items = []
FEED_URLS.each do |url|
  feed = FeedPrser::Parser.parse( open( url ).read )
  items += feed.items
end
FEED_ITEM_TEMPLATE = <<EOS
<% items.each do |item| %>
  <div class="item">
    <h2><a href="<%= item.url %><%= item.title %>"></a></h2>
    <div><%= item.content %></div>
    </div>
  </div>
<% end %>
EOS
puts ERB.new( FEED_ITEM_TEMPLATE ).result
```

```sh
ruby ./planet.rb
gem install feedparser
```

```
<div class="item">
  <h2><a href="http://vienna-rb.at/blog-/2018/11/06/picks/">Picks / what the vienna.rb team thinks is worth sharing this week</h2>
  <div>
  <h3></h3>
  <p></p>
```
