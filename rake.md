rake db:create
rake db:drop
rake db:seed
rake db:reset
rake db:create_migration NAME=
rake db:migrate
rake db:rollback
rake db:fixtures:load
rake db:migrate:status
rake db:setup
rake db:version
rake db:schema:dump
rake db:schema:load
rake db:schema:cache:clear
rake db:schema:cache:dump
rake db:structure:dump
rake db:structure:load


Migration Steps
$ rake db:create
$ rake db:create_migration NAME=create_artist
$ rake db:migrate && rake db:rollback && rake db:migrate
$ rake db:create_migration NAME=create_venue
$ rake db:migrate && rake db:rollback && rake db:migrate
$ rake db:create_migration NAME=create_event
$ rake db:migrate && rake db:rollback && rake db:migrate
$ rake db:seed
$ pry -r ./app.rb
