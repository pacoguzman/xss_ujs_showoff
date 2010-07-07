!SLIDE
# UJS #
## Código javascript en ficheros javascript no en etiquetas html
## Lo enlazamos con data-attributes (via HTML5)


!SLIDE code
# UJS #

    @@@ html
    <!DOCTYPE html>
    <html>
    <head>
      ....
      <%= csrf_meta_tag %>
      ...
    </head>
      ...
    </html>

!SLIDE code smaller
# CSRF_META_TAG #

    @@@ ruby
    module ActionView::Helpers::CsrfHelpers
      def csrf_meta_tag
        if protect_against_forgery?
          %(<meta name="csrf-param" content="#{Rack::Utils.escape_html(request_forgery_protection_token)}"/>\\n
            <meta name="csrf-token" content="#{Rack::Utils.escape_html(form_authenticity_token)}"/>).html_safe
        end
      end
    end

    # HTML
    <!DOCTYPE html>
    <html>
    <head>
      ....
      <meta name="csrf-param" content="request_forgery_protection_token"/>
      <meta name="csrf-token" content="form_authenticity_token"/>
      ...
    </head>
      ...
    </html>    

!SLIDE bullets incremental
# Data attributes #

* data-remote

* data-method

* data-confirm

* data-disable-with

!SLIDE smaller
# link_to_remote #

## Rails 2 ##

    @@@ html
    <%= link_to_remote 'Show', :url => post %>
    # javascript dentro de onclick
    <a href="/posts/1" onclick="new Ajax.Request("/post/1", {
    asynchronous:true, evalScripts:true, parameters:'authenticity_token=' +
    encodeURIComponent('9sk..44d')}); return false;">Show</a>

## Rails 3 ##

    @@@ html
    <%= link_to 'Show', post, :remote => true %>
    <a href="/posts/1" data-remote="true">Show</a>

!SLIDE smaller
# remote_form_for #

## Ocurre lo mismo ##

## Rails 2 ##

    @@@ html
    <% remote_form_for(@post) do |f| %>
    # javascript dentro de onsubmit

## Rails 3 ##

    @@@ html
    <%= form_for(@post, :remote => true) do |f| %>
    <form action="/posts" class="new_post" data-remote="true"
      id="new_post" method="post">

!SLIDE smaller

# link_to method :delete #

## Rails 2 - Rails 3 ##

    @@@html
    <%= link_to 'Destroy', post, :method => :delete %>

## Rails 2 ##
## javascript dentro de onclick ##

## Rails 3 ##

    @@@html
    <a href="/posts/1" data-method="delete" rel="nofollow">Destroy</a>

### si utilizamos :method => :put también tenemos rel="nofollow" ###

!SLIDE smaller

# link_to method :delete with confirm #

## Rails 2 - Rails 3 ##

    @@@html
    <%= link_to 'Destroy', :method => :delete,
                           :confirm => "Are you sure?" %>

## Rails 2 ##
## javascript dentro de onclick ##

## Rails 3 ##

    @@@html
    <a href="/posts/1" data-confirm="Are you sure?"
      data-method="delete" rel="nofollow">Destroy</a>

!SLIDE smaller
# submit and :disable_with => "Please wait..." %>

## Rails 2 ##
    @@@ html
    <%= f.submit 'Create Post', :disable_with => 'Please wait...' %>
    # 4 líneas de javascript en onclick

## Rails 3 ##

    @@@ html
    <%= f.submit :disable_with => 'Please wait...' %>
    <input data-disable-with="Please wait..."
      id="post_submit" name="commit" type="submit" value="Create Post" />

!SLIDE
# Javascript en Rails 3 #

## El comportamiento se añade mediante el fichero ##
## Rails.root/public/javascript/rails.js ##

## Version Prototype o jQuery ##

!SLIDE

# Se puede utilizar en rails 2 #

## Como Teambox ##

!SLIDE smbullets incremental smaller
# Faltan cosinas ¿? #

## Deprecated methods ##

* link_to_remote (*)
* remote_form_for (*)
* observe_field
* observe_form
* form_remote_tag (*)
* button_to_remote
* submit_to_remote (*)
* link_to_function
* periodically_call_remote

## (*) partially supported using the :remote => true option ##

!SLIDE smbullets smaller

## Si quieres pasar otros callbacks ya te lo tienes que currar con puro javascript  ##

* :loading
* :success
* :failure
* :complete

## http://www.simonecarletti.com/blog/2010/06/unobtrusive-javascript-in-rails-3/ ##

# [Vamos a verlo!](http://www.simonecarletti.com/blog/2010/06/unobtrusive-javascript-in-rails-3/ "unobtrusive javascript in rails 3") #

!SLIDE
# Resources

## [Upgrading rails 2 to rails 3](http://www.simonecarletti.com/blog/2010/06/upgrading-rails-2-to-rails-3)
## [Unobtrusive Javascript Technique](http://www.simonecarletti.com/blog/2010/06/unobtrusive-javascript-technique)
## [Unobtrusive Javascript In Rails 3](http://www.simonecarletti.com/blog/2010/06/unobtrusive-javascript-in-rails-3)
## [Rails 3 Tutorials](http://blog.envylabs.com/2010/05/rails-3-tutorials/)
## http://github.com/rails/jquery-ujs
## http://github.com/rails/prototype-ujs 
