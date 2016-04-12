# Instructions

In each section below, you'll have some data described to you. List the models you would create, the fields those models would have, the data type for each field and a description of what the field is for. For example, if I said I wanted to model a todo, I might write something like:

## Todo Model
1. item - string - the actual description of what they want to do
2. completed - boolean - the status of whether it's completed or not
3. user_id - integer - the id for the user who owns this todo
4. created_at - datetime - when the todo was created

NOTE! For all of these, assume you have a User model that represents the person logged into the website.



# Quest 1 - Medium Clone

Let's start with an easy one. I've provided you with the minimum number of models, you just need to provide the field information. If you can think of additional normalized data that needs another model, don't feel restricted by what's here.

You're creating a simple Medium clone where people can write blog posts and comment on other people's blog posts. You want to have enough information to show the latest blog posts, blog posts for specific authors, and blog posts for specific categories. Categories and Authors need to match exactly for us to do this, so we'll make them their own models.

## Blog Post Model
id - number - unique identifier of that post
user_id - number - unique identifier of the user that posted the blog
title - string - the title of the post
created_at - number - when the blog post was created
updated_at - number - when the blog post was last updated
content - string - the content inside of the article
category - string - the categories that the post belongs to

## Comment Model
id - number - unique identifier of that comment
post_id - number - the post that the comment is associated with
user_id - number - unique identifier of the user that posted the comment
comment - string - the comment that the user had made
created_at - number - when the comment was created
updated_at - number - when the comment was last updated

## Author Model
id - number - unique identifier of that user
profile_image - string - the path to the image for the author's profile picture
name - string - the name of the author

## Category Model
name - string - name of the category

## Likes Model
post_id - number - shows which post the like is attached to
user_id - number - shows which user the like is attached to
created_at - number - when the like was created

## Image Model
image - number - the path to the images that could be used in the article
post_id - the post that the image will be featured
order - number - the order of the images (first could be the hero image)

## Bookmarks Model
user_id - number - the user who is doing the bookmarking
post_id - number - the post they are bookmarking
created_at - number - when the bookmark was created

## Article Read Model - could tell a user if they've read that Article (visited that post)
user_id - number - the user who had read the Article
post_id - number - the post of the article that the user had read
created_at - number - when the article was visited



# Quest 2 - Twitter Clone

You're creating a Twitter clone. People can create tweets, follow other people and have followers. Keep in mind, unlike the blog post example where a comment is a separate entity, tweets responding to other tweets are still just tweets. Also, think about how Twitter turns a tweet into useful information. Do you think they scan tweets for @mentions and hashtags, or are they storing that kind of thing as additional fields? What models do we need to recreate Twitter?

## Tweet Model
id - number - the unique identifier of the tweet
user_id - number - the user who made the tweet
content - string - the 144 characters of the tweet
created_at - number - when the tweet was made
updated_at - number - when the tweet was updated
media - string - the media (video, gif, image, or link) to add to the tweet
retweet_id - number - can be null but could contain the id that would point to another tweet
reply_id - number - the id of the tweet that this tweet is a reply to

## Hashtag Model
name - string - the name of the hashtag
post_id - number - the id of the posts using that

## Mentions Model
user_id - the id of the user who is mentioning another user
mentioned_user_id - the id of the user who had been mentioned
tweet_id - number - the id of the tweet that had the mention

## Likes Model
post_id - number - the post that is being liked
user_id - number - the user who is liking the post

## Followers Model
follower_id - number - the user who is following another user
followed_id - number - the user who is being followed



# Quest 3 - Car Makes and Models

You're building a site that associates data with specific variations of specific cars. You need to break the data down from the manufacturer to the specific model. In other words, you need to model in such detail that the system knows that a 2007 Mustang and a 2013 Mustang are the _same_ thing (from the 5th Generation, 2005-2014), but that a 2015 Mustang is different from both of those. The car models should also know general information about the cars.

## Manufacturer Model
name - string - name of the Manufacturer (Toyota, Chevy)

## Model Model
make_id - number - id pointing to the manufacturer
name - string - name of the car (Mustang, Charger)

## Generation Model
name - number - number representing the generation that model belongs to
model_id - number - id of the model in that generation
start_year
end_year

## Trim Model
name - string - name of the model (GT, SE, etc.)
generation_id - the id of the generation associated with this model



# Quest 4 - DC Comics

You've used the Marvel API quite a bit. Let's model a comic site of our own for DC. You'll need to think about the fact that there are characters (the superheroes), comics (the actual issues), series (the collections of issues), events (which consist of many issues), artists, writers, et cetera. This is an incredibly deep rabbit hole. Create at least 5 models that would be able to provide enough information for someone to build all of our Marvel apps, but in the DC universe.

## Character Model
id - number - unique identifier
name - string - name of the character
image - string - link to an image of the character
description - string - text describing the character's story and origins

## Powers Model
id - number - unique identifier
name - string - name of the power
description - string - text describing the power

## Character Powers Model
id - number - unique identifier
character_id - number - id of the character who has that power
power_id - number - id of the power

## Comic Model
id - number - unique identifier
name - string - name of the comic
issue - number - issue number
cover - string - link to the image of the cover of the comic
description - string - text describing the comic's story

## Appearances Model
id - number - unique identifier
character_id - number - ids of the characters in the comics
comic_id - number - ids of the comics

## Series Model
id - number - unique identifier
name - string - name of the series
image - string - link to the image representing the series
description - string - text describing the series' story

## Comic Series Model
id - number - unique identifier
comic_id - number - ids of each of the comics in the series
series_id - number - id of the series

## Events Model
id - number - unique identifier
name - string - name of the event
image - string - link to the image representing the event
description - string - text describing the event's story

## Series Event Model
id - number - unique identifier
series_id - number - id for each of the series in the event
event_id - number - id of the events

## Artist Model
id - number - unique identifier
name - string - name of the artist
image - string - link to an image of the artist

## Comic Artists Model
id - number - unique identifier
comic_id - number - ids of all of the comics for that artist
artist_id - number - ids of all of the artists

## Writer Model
id - number - unique identifier
name - string - name of the writer
image - string - link to an image of the writer

## Comic Writers Model
id - number - unique identifier
comic_id - number - ids of all of the comics for that writer
writer_id - number - ids of all of the writers
