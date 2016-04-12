# Quest 1 - Revisiting Car Makes and Models

Let's make this more realistic. In the Explorer mode version, you had to construct your data in a way that would track generation information for a specific model. Now, let's step that up.

Your models should know the make (Ford), the model (Mustang), the generation (2005-2014 5th Generation Mustang) the trim (GT) and the color options. Keep in mind that trim and color options change between generations. You should be trying to provide the maximum amount of information possible for each section so that if we wanted to present a page on the Mustang as a whole across all generations there would be _something_ to show the user.

## Manufacturer Model
name - string - name of the Manufacturer (Toyota, Chevy)

## Model Model
make_id - number - id pointing to the manufacturer
name - string - name of the car (Mustang, Charger)

## Generation Model
name - number - number representing the generation that model belongs to
model_id - number - id of the model in that generation
start_year - number - the beginning of the range of years for that generation
end_year - number - the end of the range of years for that generation

## Trim Model
name - string - name of the model (GT, SE, etc.)
generation_id - the id of the generation associated with this model

## Color Model
color - string - color of the car
car_id - number - ids of the cars with that color



# Quest 2 - Reddit Clone

You're making a Reddit clone. You need to keep track of subreddits, text posts, link posts, comments and karma. Karma needs to be modeled in a way where users can up/down vote posts and comments, and where you could easily get the total karma for a user for _only link posts_ and _all comments_. You'll need at least 4-6 models to accomplish this depending on whether or not you choose to use polymorphic relationships.

## Subreddits Model
name - string - name of the subreddit
subreddit_name - number - name of the subreddit this subreddit belongs to.  top subreddits will not have this

## Post Model
id - number - unique id
user_id - number - id of the user that made the post
title - string - title of the post
content - string - the content of the post
link_post - boolean - whether or not the post is just a link

## Comments Model
id - number - unique id
post_id - number - id of the post that the comment is related
user_id - number - id of the user that made the comment
comment - string - the content of the commet.

## Karma Model
parent_id - number - id of the post related to the karma
parent_type - string - type of post that the Karma received (post or comment)
user_id - number - id of the user that the karma belongs to
positive - number - amount of positive karma
negative - number - amount of negative karma
