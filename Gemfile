source "https://rubygems.org"

# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
#gem "jekyll", "~> 3.8.3"

# This is the default theme for new Jekyll sites. You may change this to anything you like.
#gem "minima", "~> 2.0"
gem "minimal-mistakes-jekyll"

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
gem "github-pages", group: :jekyll_plugins

# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.6"
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.0" if Gem.win_platform?

# added on 13/10/2018
gem 'jekyll-include-cache'

# added on 14/10/2018
# https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/installation.md
gem 'jekyll-seo-tag'

# Error: 2020-01-19
# https://talk.jekyllrb.com/t/error-repo-pages-info-and-connectionfailed-in-layouts-default-html/3793
# jekyll 3.8.5 | Error:  uninitialized constant Faraday::Error::ConnectionFailed
# Did you mean?  Faraday::ConnectionFailed
#  ~/Documents/Projects/GitPage   master ● ?  ↵ 1  bundle exec jekyll server                                     1 ↵  2199  10:52:37
# Configuration file: /Users/doosanjung/Documents/Projects/GitPage/_config.yml
#             Source: /Users/doosanjung/Documents/Projects/GitPage
#        Destination: /Users/doosanjung/Documents/Projects/GitPage/_site
#  Incremental build: disabled. Enable with --incremental
#       Generating...
# Invalid theme folder: _sass
#       Remote Theme: Using theme mmistakes/minimal-mistakes
#        Jekyll Feed: Generating feed for posts
#    GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
#    GitHub Metadata: Error processing value 'repo_pages_info':
#   Liquid Exception: uninitialized constant Faraday::Error::ConnectionFailed Did you mean? Faraday::ConnectionFailed in /_layouts/default.html
# jekyll 3.8.5 | Error:  uninitialized constant Faraday::Error::ConnectionFailed
# Did you mean?  Faraday::ConnectionFailed
gem "faraday", "< 1.0"