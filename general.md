
CRUD Actions:

index
create
new
edit
show
update
destroy


Dependent Destroy:

|parent model|

class User < ActiveRecord::Base
    has_many :posts, dependent: :destroy
end

Paths:

Run rake routes
Find the relevant line from the results
Take the "Prefix" from that line, and append path. That's your method name!
Check to see if there's any dynamic routing in the "URI Pattern"
If there is any dynamic routing, pass an argument to the path helper method telling it which entry in the database you're talking about.

/events/new
redirect_to new_event_path
/events/:id/edit
edit_event_path(73)
my_event = Event.first
edit_event_path(my_event.id)
edit_event_path(my_event)

<%= link_to 'Edit', edit_event_path(@event) %>
<%= link_to 'Edit', edit_event_path(@event), class: "button", id: "awesome-edit-link" %>


Forms:

<%= form_for(@book) do |f| %>
 <div class="field">
   <%= f.label :author %><br />
   <%= f.text_field :author %>
 </div>

 <div class="field">
   <%= f.label :title %><br />
   <%= f.text_field :title %>
 </div>

 <div class="actions">
   <%= f.submit %>
 </div>
<% end %>

Nested Resources:
|nest reviews under products|

Rails.application.routes.draw do
 resources :products, only: [:index, :show] do
   resources :reviews, only: [:index, :new, :create]
 end
end

Rails.application.routes.draw do
 resources :products, only: [:index, :show] do
   resources :reviews, only: [:index, :new, :create]
 end

 resources :reviews, only: [:show] do
   resources :comments, only: [:index, :new, :create]
 end
end

|shallow nesting|

Rails.application.routes.draw do
 resources :products, only: [:index, :show] do
   resources :reviews, only: [:index, :new, :create]
 end

 resources :reviews, only: [:show]
end
