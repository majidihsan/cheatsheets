Helpful link
https://www.launchacademy.com/codecabulary/learn-rails/how-to-create-a-rails-app
http://www.blainekendall.com/uploads/RubyOnRails-Cheatsheet-BlaineKendall.pdf

Setting Up:
------------
rails new (-) --database=postgresql --skip-test-unit --skip-turbolinks
$ cd (-)
bundle install
bundle check
$ git init
$ git add -A
$ git commit -m 'Initial commit’
$ rake db:create
$ rails g migration
$ rails g controller
$ rails g model


Rails Commands:
--------------

Server
$ rails s

Console
$ rails c

Migrate
$ rails g migration (-)

Setup
$ rake db:setup

Reset
$ rake db:reset

Verify Rollback
$ rake db:migrate && rake db:rollback && rake db:migrate
