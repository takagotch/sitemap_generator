### sitemap_generator
---
https://github.com/kjvarga/sitemap_generator

```sh
gem install sitemap_generator
ruby sitemap.rb

gem install 'sitemap_generator'
gem 'sitemap_generator'

rake sitemap:refresh


```

```ruby
#sitemap.rb
require 'rubygems'
require 'sitemap_generator'
SitemapGenerator::Sitemap.default_host = 'http://ex.com'
SitemapGenerator::Sitemap.create do
  add '/home', :changefreq => 'daily', :priotiry => 0.9
  add '/contact_us', :changefreq => 'weekly'
end
SitemapGenerator::Sitemap.ping_search_engines


require 'sitemap_generator'
#config/sitemap.rb
sitemap::refresh CONFIG_FILE="path/to/sitemap.rb"
#config/environment.rb
config.gem 'sitemap_generator'

SitemapGenerator.verbose = false
SitemapGenerator::Sitemap.search_engines
SitemapGenerator::Sitemap.ping_search_engines(newengine: 'http://newengine.com/ping?url=%s')
SitemapGenerator::Sitemap.default_host = 'http://ex.com'
SitemapGenerator::Sitemap.ping_search_engines
SitemapGenerator::Sitemap.ping_search_engines('http://ex.com/sitemap.xml.gz')
# config/schedule.rb
every 1.day, :at => '5:00 am' do
  rake "-s sitemap:refresh"
end
#public/rbots.txt
Sitemap: http://www.ex.com/sitemap.xml.gz

SitemapGenerator::Interpreter.send :include, RoutingHelper

require 'capistrano/sitemap_generator'

set :sitemap_roles, :web

sitemap:create
sitemap:refresh
sitemap:clean
# public/shared/
SitemapGenerator::Sitemap.sitemaps_path = 'shared/'

SitemapGenerator::Sitemap.create_index = true
SitemapGenerator::Sitemap.create_index = false
SitemapGenerator::Sitemap.crate_index = :auto

SitemapGenerator::Sitemap.adapter = sitemapGenerator::AwsSdkAdapter.new('s3_bucket',
  aws_access_key_id: 'AAAAAAAAAAA',
  aws_secret_access_key: 'sssssss',
  aws_region: 'us-east-1'
)

SitemapGenerator::Sitemap.default_host = "http://www.ex.com/"
SitemapGenerator::Sitemap.sitemaps_host "http://s3.amazonaws.com/sitemap-generator/"
SitemapGenerator::Sitemap.public_path = 'tmp/'
SitemapGenerator::Sitemap.sitemaps_path = 'tmp/'
SitemapGenerator::Sitemap.sitemaps_path = 'sitemaps/'
SitemapGenerator::Sitemap.adpter = SitemapGenerator::WaveAdpter.new


Sitemap: http://s3.amazonaws.com/sitemap-genertor/sitemaps/sitemap.xml.gz


%w(google bing apple).each do |subdomain|
  SitemapGenerator::Sitemap.default_host = "https://#{subdomain}.mysite.com"
  SitemapGenerator::Sitemap.sitemaps_path = "sitemaps/#{subdomain}"
  SitemapGenerator::Sitemap.create do
    add '/home'
  end
end


#config/google_sitemap.rb
SitemapGenerator::Sitemap.default_host = "https://google.mysite.com"
SitemapGenerator::Sitemap.sitemaps_path = "sitemaps/google"
SitemapGenerator::Sitemap.create do
  add '/home'
end
#config/apple_sitemap.rb
SitemapGenerator::Sitemap.default_host = "https://apple.mysite.com"
SitemapGenerator::Sitemap.sitemaps_path = "sitemaps/apple"
SitemapGenerator::Sitemap.create do
  add '/home'
end
#config/bing_sitemap.rb
SitemapGenerator::Sitemap.default_host = "https://bing.mysite.com"
SitemapGenerator::Sitemap.sitemaps_path = "sitemaps/bing"
SitemapGenerator::Sitemap.create do
  add '/home'
end
```
```
rake sitemap:refresh CONFIG_FILE="config/google_sitemap.rb"
rake sitemap:refresh CONFIG_FILE="config/apple_sitemap.rb"
rake sitemap:refresh CONFIG_FILE="config/bing_sitemap.rb"
# config/sitemap.rb
rake sitemap:refresh CONFIG_FILE="config/geo_sitemap.rb"

rake sitemap:refresh:no_ping
```
```
SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create do
  add '/welcome'
end
```
```
#public/sitemap.xml.gz
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:image="http://www.google.com/schemas/sitemap-image/1.1 xmlns="http://www.sitemap.org/schmas/sitemap/0.9" xmlns:vieo="http://www.google.com/schemas/sitemap-video/1.1" xsi:schemaLocation="http://www.sitemaps.org/schmas/sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
  <url>
    <loc>http:/www.ex.com/</loc>
    <lastmode>2011-05-21T00:03:38+00:00</lastmod>
    <changefreq>always</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>http://www.ec.com/welcome/</loc>
    <lastmod>2011-05-21T00:03:38+00:00</lastmod>
    <changefreq>weekly</changefrea>
    <priority>0.5</priority>
  </url>
</urlset>
```

```
SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create_index = true
SitemapGenerator::Sitemap.create do
  add '/welcome'
end

<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9 xsi:shemaLocation="http://www.sitemap.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/siteindex.xsd" >
</sitemapindex>

SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create do
  add '/contact_us'
  Content.find_each do |content|
    add content_path(content), :lastmod => content.updated_at
  end
end


add '/contact_us', :changefreq => 'montyly'

add content_path(content), :lastmod => content.updated_at
add '/login', :host => 'https://securehost.com'
add '/about', :priority => 0.75
add '/about', :expires => Time.now + 2.weeks
add_to_index '/mysitemap1.xml.gz', :host => 'http://sitemaphostingserver.com'

SitemapGenerator::Sitemap.default_host = "http://www.ex.com/"
SitemapGenerator::Sitemap.create do
  add_to_index '/mysitemap1.xml.gz'
  add_to_index '/mysitemap2.xml.gz'
end

SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.namer = SitemapGenerator::SimpleNamer.new(:sitemap, :start => 4)
SitemapGenerator::Sitemap.create do
  (1..3).each do |i|
    add_to_index "sitemap#{i}.xml.gz"
  end
  add '/home'
  add '/another'
end


SitemapGenerator::Sitemap.default_host = 'http://ex.com'
SitemapGenerator::Sitemap.sitemaps_path = 'sitemaps/'


SitemapGenerator::Sitemap.create(
    :default_host => 'http://ex.com',
    :sitemaps_path => 'sitemaps/') do
  add '/home'
end


SitemapGenerator::Sitemap.create(:default_host => 'http://example.com') do
  group(:filename => :somegroup, :sitemaps_path => 'sitemaps/') do
    add '/home'
  end
end


SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create do
  add '/rss'
  
  group(:sitemaps_path => 'en/', :filename => :english) do
    add '/home'
  end
  
  group(:sitemaps_path => 'fr/', :filename => :french) do
    add '/maison'
  end
end


SitemapGenerator::Sitemap.verbos = true
SitemapGenerator::Sitemap.default_host = "http://www.google.com"
SitemapGenerator::Sitemap.create do
  odds = group(:filename => :odds)
  evens = group(:filename => :evens)
  (1..20).each do |i|
    if(i % 2) == 0
      evens.add i.to_s
    else
      odds.add i.to_s
    end
  end
  odds.finalize!
  evens.finalize!
end


SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :news => {
    :publication_name => "Example",
    :publication_language => "en",
    :title => "My Article",
    :keywords => ",u article, articles about myself",
    :stock_tickers => "SAO:PETR3",
    :publication_date => "2011-08-22",
    :access => "Subscription",
    :genres => "PressRelease"
  })
end


SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitempaGenerator::Sitemap.create do
  add('/index.html', :images => [{
    :loc => 'http://www.ex.com/image.png',
    :title => 'Image' }])
end


SitemapGenerator::Sitemap.default_host = ""
SitemapGenerator::Sitemap.create do
  add('/index.html', :video => {
    :thumbnail_loc => 'http://www.example.com/video1_thumbnail.png',
    :title => 'Title',
    :description => 'Description',
    :content_loc => 'http://www.ex.com/cool_video.mpg',
    :tags => %w[one two three],
    :category => 'Category'
  })
end


SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create do
  add('/blog/post', :pagemap => {
    :dataobjects => [{
      :type => 'document',
      :id => 'hibachi',
      :attributes => [
        { :name => 'name', :value => 'Dragon' },
        { :name => 'review', :value => '3.5' }
      ]
    }]
  })
end


SitemapGenerator::Sitemap.default_host = "http:/www.ex.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :alternate => {
    :href => 'http://www.ex.de/index.html',
    :lang => 'de',
    :nofollow => true
  })
end



SitemapGenerator::Sitemap.default_host = "http://www.ex.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :mobile => true)
end

```
