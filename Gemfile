source "https://rubygems.org"

ruby "2.2.4" if ENV["HEROKU"]

require "json"
require "open-uri"
versions = JSON.parse(::URI.open("https://pages.github.com/versions.json").read)

gem "github-pages", versions["github-pages"]
gem "webrick" if RUBY_VERSION >= "3"

group :tests do
  gem "html-proofer"
end
