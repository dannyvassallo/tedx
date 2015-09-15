#Middleman Boilerplate

This includes:

1. jQuery
2. Bootstrap
3. Bootstrap Sass Variables
4. Font Awesome
5. Heroku Deployment Config


### Getting Started

------------------------
Clone the repo using the GUI or terminal. To do so in terminal, use the following:
```shell
git clone https://github.com/dannyvassallo/middleman-boilerplate.git
cd middleman-boilerplate
```

From the "middleman-boilerplate" directory, install the gems by running the following:
```shell
bundle install
```

To fire up the server while in the "middleman-boilerplate" directory use this command:
```shell
middleman s
```

If you are having issues with livereload not working fire up the server using:
```shell
middleman s --force-polling --verbose
```

To kill the server use "ctrl+c"

If you find yourself curious as to what directory you are in use the following in terminal:
```shell
pwd
```
It should turn up "middleman-boilerplate"

### Deploying

Create a new app on heroku using heroku-cli. Pass in the following:
```shell
heroku create YOUR-APP-NAME
```

To add an existing repository:
```shell
heroku git:remote -a YOUR-APP-NAME
```

To deploy, commit all changes and pass in:
```shell
git push heroku master
```

To deploy a non-master branch use:
```shell
git push heroku MY-NEW-BRANCH:master
```

###Middleman Helper Methods

------------------------
Create an external link:
```html
<%= link_to 'My Site', 'http://mysite.com' %>
```

Create an internal link:
```html
<%= link_to 'About', '/about.html' %>
```

Link / Image tag for image in images folder:
```html
<% link_to 'http://mysite.com' do %>
  <%= image_tag 'mylogo.png' %>
<% end %>
```

Create a form (example):
```html
<% form_tag '/destroy', :class => 'destroy-form', :method => 'delete' do %>
  <% field_set_tag do %>
    <p>
      <%= label_tag :username, :class => 'first' %>
      <%= text_field_tag :username, :value => params[:username] %>
    </p>
    <p>
      <%= label_tag :password, :class => 'first' %>
      <%= password_field_tag :password, :value => params[:password] %>
    </p>
    <p>
      <%= label_tag :strategy %>
      <%= select_tag :strategy, :options => ['delete', 'destroy'],
          :selected => 'delete' %>
    </p>
    <p>
      <%= check_box_tag :confirm_delete %>
    </p>
  <% end %>
  <% field_set_tag(:class => 'buttons') do %>
    <%= submit_tag "Remove" %>
  <% end %>
<% end %>
```

Text helpers for dummy info:

USAGE:
```html
<%= lorem.sentences 5 %>
```

DIFFERENT METHODS:
```ruby
lorem.sentence      # returns a single sentence
lorem.words 5       # returns 5 individual words
lorem.word
lorem.paragraphs 10 # returns 10 paragraphs 
lorem.paragraph
lorem.date          # accepts a strftime format argument
lorem.name
lorem.first_name
lorem.last_name
lorem.email
```

Placeholder Images:

USAGE:
```html
<%= lorem.image('300x400') %>
```

DIFFERENT METHODS:
```ruby
lorem.image('300x400')
  #=> http://placehold.it/300x400
lorem.image('300x400', :background_color => '333', :color => 'fff')
  #=> http://placehold.it/300x400/333/fff
lorem.image('300x400', :random_color => true)
  #=> http://placehold.it/300x400/f47av7/9fbc34d
lorem.image('300x400', :text => 'blah')
  #=> http://placehold.it/300x400&text=blah
```