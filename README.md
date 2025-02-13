# ActiveAdmin::Globalize
Makes it easy to translate your resource fields.

### :warning: Unmaintained :warning:

This is still mostly unmaintained. I just removed specific version requirements for `activeadmin` and `globalize` – meaning this won't block you from updating but it doesn't guarantee it will still work. I've done some minor tweaks to make it run ok with activeadmin 2.9.0 which is enough for me now.

## Installation

```ruby
gem "activeadmin-globalize", git: 'https://github.com/YANOUSHek/activeadmin-globalize.git', branch: 'master'
```
We still need to use GitHub because ActiveAdmin is still in active development
and there's no released gem compatible with Rails 4.

## Your model

```ruby
active_admin_translates :title, :description do
  validates_presence_of :title
end
```
## Editor configuration

```ruby
# if you are using Rails 4 or Strong Parameters:
permit_params translations_attributes: [:locale, :title, :content]


index do
  # ...
  translation_status
  # ...
  default_actions
end

form do |f|
  # ...
  f.translated_inputs "Translated fields", switch_locale: false do |t|
    t.input :title
    t.input :content
  end
  # ...
end
```
If `switch_locale` is set, each tab will be rendered switching locale.

## Friendly ID

If you want to use Friendly ID together with Globalize, please take a look
at the `activeadmin-seo` gem.

## Hints

To use the dashed locale keys as 'pt-BR' or 'pt-PT' you need to convert a string
to symbol (in application.rb)

  config.i18n.available_locales = [:en, :it, :de, :es, :"pt-BR"]

