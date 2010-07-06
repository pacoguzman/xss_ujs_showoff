!SLIDE
# Cross Site Scripting XSS #
## SafeBuffers and Rails 3.0 ##
### http://yehudakatz.com/2010/02/01/safebuffers-and-rails-3-0/ ###

!SLIDE bullets incremental
# XSS #

* If a String is html_safe, ERB may insert it unaltered into the output.
* If it is not safe, ERB must first escape it before inserting it into the output.

!SLIDE code

    @@@ ruby
    module ActiveSupport
      class SafeBuffer < String
        ...
      end
    end

!SLIDE
## Rails 2 - unsafe ##

    @@@ ruby
    <%= @post.body %>

## Rails 3 - unsafe ##

    @@@ ruby
    # Devuelven un String marcado como seguro
    <%= raw @post.body %>
    
    <%= @post.body.html_safe %>

!SLIDE
## Rails 2 - safe ##

    @@@ ruby
    <%= h @post.body %>

## Rails 3 - safe ##

    @@@ ruby
    <%= @post.body %>

!SLIDE bullets incremental small transition=fade
# Summary #

* If a plain String is passed into a <%= %>, Rails always escapes it
* If a SafeBuffer is passed into a <%= %>, Rails does not escape it.
   To get a SafeBuffer from a String, call html_safe on it.

* (at compile-time)
* If you use the raw helper in a <%= %>.
* Rails does not escape any part of a template that is not in an ERB tag.

!SLIDE
# Resources #

### http://yehudakatz.com/2010/02/01/safebuffers-and-rails-3-0/ ###
### http://rubyonrails.org/screencasts/rails3/xss-ujs ###