---
layout: post
title:      "Refining a Recipe"
date:       2018-07-07 03:37:23 -0400
permalink:  refining_a_recipe
---


I decided that I would take on the task of cleaning up my recipe manager project. I have a lot of goals for this particular project, so maybe I can start out by creating my wishlist:

* Dynamically add ingredients and directions when creating a recipe
* Allow for users to leave comments on recipes and save other recipes as favorites
* Upload pictures for recipes
* Label different types of recipes (entree, side, dessert, etc.)
* Filter recipes (name, ingredients, type)
* Create a shopping list and allow users to add ingredients for a recipe to their list

Okay, so I have to admit that this is pretty ambitious but I love to cook and I would love to have a place to keep all my favorite recipes handy and be able to easily add ingredients I need to a shopping list on my phone. Seems worth the effort, wouldn't you say?

## Step 1
This project was initially fully RoR, but the subsequent iteration of this project required the use of jQuery to kick things up a notch (see what I did there?) on the front-end. I had to render an index page (the list of all items) and a show page (a detailed view of one item) without a page refresh using jQuery. Well, I initially got it working okay, but it didn't always behave as expected and still needs some refactoring. I figured I would start here and work out these bugs before I moved on to something else.

## The Problem
The problem that I needed to address first was how my form was dynamically allowing for additional ingredients. In the first iteration I simply created the form with a fixed number of spaces for ingredients. 

![](https://media.giphy.com/media/cPKWZB2aaB3rO/giphy.gif)

I know, I know...it was ugly. Not only that, it was impractical. If I set the number of possible ingredients at ten, then a simple recipe that only had two or three ingredients would be fine (provided I had a way to make sure empty records weren't being persisted to the database...which I did), but a more complex recipe that had more than ten ingredients couldn't be saved.

# The First Solution
Ideally I wanted a way to use jQuery to access the ingredient node while still using Rails form builder to make sure that the ingredients were still being associated to the recipe being created. The problem that I was running into was the fact that the ingredients were nested associations and not so easy to access. So what I came up with after watching a project feedback session and working with a Learn instructor:

```
var addNewIngredient = function() {
    var $new_ingredients = $("#new_ingredients");
    var ingredientInput = `<name="recipe[ingredients_attributes][][name]">`;
    ingredientInput += `< name="recipe[ingredients_attributes][][quantity]">`
    $new_ingredients.append(ingredientInput);
 }
 ```
 
So...I basically had to see what the form was creating in the actual HTML, and then hijack that and manually insert it into the form. It worked, but it wasn't particularly elegant.
 
 Anothere issue that I noticed was that when I want to edit a recipe, that recipe does not repopulate in the form. I wasn't sure if this was a byproduct of my solution, but that was immaterial; the behavior I was getting was undesirable.
 
 ## The New Solution
 I had avoided using gems because they seemed to be a bit like using a nail gun when a hammer and nail would suffice. I know gems are great tools, but for what I needed a gem was overkill. Well, I have since changed my mind. Slightly. I decided to use the cocoon gem to take care of this issue. So instead of the above code, I now have this:
 
```
app/views/recipes/_form.html.erb

  <h3>Ingredients</h3>
  <div class='form-group'>
    <div id="recipe-ingredients">
      <ol>
      <%= f.fields_for(:recipe_ingredients) do |ri| %>
        <%= render 'recipe_ingredient_fields', f: ri  %>
      <% end %>
      <%= link_to_add_association 'Add Ingredient', f, :recipe_ingredients,
        'data-association-insertion-node' => "#recipe-ingredients ol",
        'data-association-insertion-method' => "prepend",
        :wrap_object => Proc.new {|ri| ri.build_ingredient; ri }, class: "btn btn-default form-button" %>
      </ol>
    </div>
  </div>
```

```
app/views/recipes/_recipe_ingredient_fields.html.erb

<div class="form-inline  clearfix">
  <div class=" form-group nested-fields">
	 <%= f.label :quantity, "Quantity" %>
		<%= f.text_field :quantity, class: 'form-control'%>

		<%= f.fields_for(:ingredient) do |ri_ingredient| %>
		<%= ri_ingredient.label :name, "Name" %>
		<%= ri_ingredient.text_field :name, class: 'form-control'%>
	  <% end %>
		<%= link_to_remove_association "Remove", f, class: "btn btn-default form-button" %>
	</div>
</div>
```

What's happening here? Cocoon is being used to add an association (`:recipe_ingredients`) to the recipe form. It's adding them to the ordered list (ol) of the node with the id (#) of 'recipe-ingredients'. What's more, it's adding these new ingredients before (prepend) the link. The other significant piece to point out is the new partial that I created. This partial uses Rails form builder syntax to create the associated ingredient.

![](https://media.giphy.com/media/rjkJD1v80CjYs/giphy.gif)

## Still Not Done
This was a lot of progress, but there is still a lot of work that needs to be done to make sure that this is working properly. I've seen examples of this at work, so I know it does. But I have to fix some of my models and controllers to make sure everything is in the right place. In retrospect, probably busted out the champagne a bit too soon...

Until next time!
