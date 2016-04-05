
gem "factory_girl_rails", "~> 4.0"

Gemfile
--------
group :test, :development do
  gem "rspec-rails"
  gem "factory_girl_rails"
end

bundle
rails generate rspec:install

spec/factories/recipes.rb
-------------------------
FactoryGirl.define do
  factory :recipe do
    name "MyString"
    description "MyText"
    instructions "MyText"
    servings 1
    cooking_time 1
  end
end


rails_helper.rb
----------------
RSpec.configure do |config|
  config.include FactoryGirl::Syntax::Methods
end


 original spec
 --------------
 require "rails_helper"

 RSpec.describe Recipe do
   describe ".quick_recipes" do
     it "returns recipes with a cooking time less than 30 min" do
       first_quick_recipe = FactoryGirl.create(:recipe, cooking_time: 5)
       second_quick_recipe = FactoryGirl.create(:recipe, cooking_time: 4)
       long_recipe = FactoryGirl.create(:recipe, cooking_time: 240)

       results = Recipe.quick_recipes

       expect(results).to include(first_quick_recipe)
       expect(results).to include(second_quick_recipe)
       expect(results).to_not include(long_recipe)
     end
   end
 end

 Multiple Records
 ----------------
 require "rails_helper"

RSpec.describe Recipe do
  describe ".quick_recipes" do
    it "returns recipes with a cooking time less than 30 min" do
      quick_recipes = create_list(:recipe, 2, cooking_time: 5)
      slow_recipes = create_list(:recipe, 3, cooking_time: 240)

      results = Recipe.quick_recipes

      quick_recipes.each do |quick_recipe|
        expect(results).to include(quick_recipe)
      end

      slow_recipes.each do |slow_recipe|
        expect(results).to_not include(slow_recipe)
      end
    end
  end
end

Sequences
---------
FactoryGirl.define do
  factory :recipe do
    sequence(:name) { |n| "Brussels Sprouts with Bacon #{n}" }
    description "The best side-dish, ever."
    instructions "Brussels + Bacon + Heat"
    servings 4
    cooking_time 45
  end
end

> first_recipe = FactoryGirl.create(:recipe)
