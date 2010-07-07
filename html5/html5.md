!SLIDE
# HTML5 by default #

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
# HTML5 helpers #

    @@@ ruby
    module ActionView::Helpers::FormHelper
      # Returns a text_field of type "search".
      def search_field(object_name, method, options = {}); ...; end

      # Returns a text_field of type "tel".
      def telephone_field(object_name, method, options = {}); ...; end

      # Returns a text_field of type "url".
      def url_field(object_name, method, options = {}); ...; end

      # Returns a text_field of type "email".
      def email_field(object_name, method, options = {}); ...; end

      # Returns an input tag of type "number".
      def number_field(object_name, method, options = {}); ...; end

      # Returns an input tag of type "range".
      def range_field(object_name, method, options = {}); ...; end
    end

!SLIDE code smaller
# HTML5 helpers #

    @@@ ruby
    module ActionView::Helpers::FormHelper
      # * Accepts the same options as text_field_tag.
      def search_field_tag(name, value = nil, options = {}); ...; end

      # * Accepts the same options as text_field_tag.
      def telephone_field_tag(name, value = nil, options = {}); ...; end
      alias phone_field_tag telephone_field_tag

      # * Accepts the same options as text_field_tag.
      def url_field_tag(name, value = nil, options = {}); ...; end

      # * Accepts the same options as text_field_tag.
      def email_field_tag(name, value = nil, options = {}); ...; end

      ...
    end

!SLIDE code smaller
# HTML5 helpers #

    @@@ ruby
    module ActionView::Helpers::FormHelper
      ...
      # Creates a number field.
      #
      # ==== Options
      # * <tt>:min</tt> - The minimum acceptable value.
      # * <tt>:max</tt> - The maximum acceptable value.
      # * <tt>:in</tt> - A range specifying the <tt>:min</tt> and
      #   <tt>:max</tt> values.
      # * <tt>:step</tt> - The acceptable value granularity.
      # * Otherwise accepts the same options as text_field_tag.
      #
      # ==== Examples
      #   number_field_tag 'quantity', nil, :in => 1...10
      #   => <input id="quantity" name="quantity" min="1" max="9" />
      def number_field_tag(name, value = nil, options = {}); ...; end

      # * Accepts the same options as number_field_tag.
      def range_field_tag(name, value = nil, options = {}); ...; end
    end

!SLIDE code smaller
# HTML5 helpers #

    @@@ruby
    module ActionView::Helpers::AssetTagHelper
      #   <%= favicon_link_tag %>
      #   <link href="/favicon.ico?4649789979" rel="shortcut icon" type="image/vnd.microsoft.icon" />
      def favicon_link_tag(source='/favicon.ico', options={}); ...; end

      def video_path(source); ...; end

      def audio_path(source); ...; end

      #  video_tag("trailer")  # =>
      #    <video src="/videos/trailer" />
      def video_tag(sources, options = {}); ...; end

      #  audio_tag("sound")  # =>
      #    <audio src="/audios/sound" />
      def audio_tag(source, options = {}); ...; end
    end

!SLIDE code
# Error Messages Deprecated #

### Use - [Dynamic Form](http://github.com/rails/dynamic_form "Dynamic Form") ###

    @@@ ruby
    module ActionView::Helpers
      module ActiveModelHelper
        # input form error_messages_for error_message_on
      end
      module ActiveModelFormBuilder
        # error_messages error_message_on
      end
    end

### http://github.com/rails/dynamic_form

!SLIDE
# Rails EDGE #
## Removed textlize and markdown helpers ##

!SLIDE bullets incremental smaller
# Templates #

* Save your templates as UTF-8 so you do not need to do anything else for things to "just work"

* Erb implementation Erubis

!SLIDE
# Resources #

### http://github.com/rails/dynamic_form
