# First class functions in Sass 3.5.0

Sass 3.5.0 introduces first-class functions
with a new function: `get-function($name)`

Release notes: http://blog.sass-lang.com/posts/809572-sass-35-release-candidate

Release notes don't show any code using get-function,
so let's see how it actually works…

## Get started

Either read the contents of [index.scss](index.scss) and [index.css](index.css), or play around with it locally:

1. Clone this repository
1. cd into it
1. Install Sass 3.5.0 RC: `bundle install`
1. Run the Sass watcher: `bundle exec sass index.scss:index.css --watch --sourcemap=none`
1. Play around with it!
