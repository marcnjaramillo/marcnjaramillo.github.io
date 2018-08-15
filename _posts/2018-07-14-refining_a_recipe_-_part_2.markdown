---
layout: post
title:      "Refining a Recipe - Part 2"
date:       2018-07-14 23:38:47 -0400
permalink:  refining_a_recipe_-_part_2
---


Last week I started to work on  cleaning up my recipe manager project. I did this by adding the cocoon gem and tweaking the form for creating a recipe. This involved creating a new partial that would dynamically add the associated ingredient to the form. This week, I made further adjustments to make sure that was working properly and then some. 



## Updating Recipe Controller

First I had to update my models, controllers, and serializers. The first controller I updated was my `Recipe Controller`. I made two changes in my private methods: updated `recipe_params` method and added a `set_recipe` method. The big change in the `recipe_params` method was rearranging the parameters that would be permitted when filling out the recipe form.

```
  def recipe_params
    params.require(:recipe).permit(
      :name,
      :prep_time,
      :cook_time,
      :user_id,
      :search,
      directions_attributes: [:id, :text],
      recipe_ingredients_attributes: [
        :id,
        :quantity,
        ingredient_attributes: [:id, :name]
      ]
    )
  end
```
	
Technically, this isn't an update so much as it is a return to something I had previously written in the first stage of the project. At the time, I was hard-coding *ALL* the ingredients and directions fields in the recipe form. I wanted to make these fields dynamic so that the user could click a button and add or remove fields as needed. I watched a video of Ari doing a project review with someone and they came up with the hijack trick I ended up using because they couldn't figure out how to dynamically add the Rails form helper fields without a gem. I was still struggling with some concepts, and I wasn't that familiar with using gems that weren't used in Learn lessons. I'm more comfortable with using gems now, and I decided to use the cocoon gem I mentioned [in this blog post](http://marcnjaramillo.com/refining_a_recipe).

## Adding Devise

I intially had hesitation about using certain gems, including Devise, but I decided that it was time to get over my discomfort and hangups about using gems. Even though what I had worked fine, I chose to add Devise because it seemed to simplify some of the work I had already done myself. For example, rather than having a `Sessions Controller` and needing to include a bunch of methods that I defined in a `Sessions Helper`, I could use the controllers and methods already built in to Devise. 

## What's Next?

* **Clean up the comments:** Right now, anyone can delete a comment. However, only the recipe owner or the person who added the comment should be able to perform this action. 
* **Ability to add pictures:** I want to include pictures for recipes and also for user avatars. This will make the app a lot more interesting.
* **Rate a recipe:** Users should be able to rate recipes they find and try.
* **Add categories to recipes:** This is something I wanted from the beginning so that people can filter recipes by type.

Stay tuned!




 
 
