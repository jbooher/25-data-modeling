For epic mode, we're going to design an Amazon clone.

# Quest 1 - Products

You're building something like Amazon. You have an incredibly large number of products. These products have all of the descriptive information required to convince people to buy them, a price, and the ability to have a temporarily reduced price.

They can belong to many categories, and those categories have a hierarchy (so like, Entertainment -> Video Games -> Xbox One would be three categories that are related).

They have many reviews from users. These reviews have a rating. The products have an aggregate rating representing the average of all of these.

Products can have any number of images.

## Item Model
id - number - unique identifier
name - string - name of the item
description - string - description of the item
inventory - number - amount remaining in inventory

## Price Model
item_id - number - id of the item to whom the price belongs.
price - number - the price of the item
sale - boolean - determines whether the sale is currently going
sale_price - number - how much the item costs while it is on sale

## Image Model
item_id - number - the item that the images are linked to
images - string - links to the images included with the item
order - number - order of the images (0 could be the main, large image)

## Categories Model
name - string - name of the category
category_name - string - name of the category that this category belongs to (top category would not have a value)

## Reviews Model
id - number - unique identifier
item_id - number - id of the item this review is for
user_id - number - id of the user who wrote the review
review - string - the content of the review

## Ratings Model
review_id - number - the id of the review this is a rating for
user_id - number - id of the user who made the rating
rating - number - (1 - 5 based on how helpful the rating is)

# Quest 2 - The Cart

You have products. Now you need a place to hold them while the user is waiting to buy them. Keep in mind, the user can buy more than one of a product.

## Cart Model
user_id - number - the user to whom the cart belongs
item_id - number - the id of each item in the cart
quantity - number - the amount of that item that you have in your cart
price_id - number - id of the price for that item
total - number - amount of the total prices plus quantity in cart

# Quest 3 - User Information

To make the customer's life easier, we need more complex information about them. We want to store their shipping and billing addresses, as well as some payment information. Keep in mind with payment information, you want to store some information to show the user, but we never want to store it all in plain text. If you use fields for sensitive information like a password or a credit card number, note in your design that it should be encrypted.

## User Model
id - number - unique identifier
first_name - string - first name of the user
last_name - string - last name of the user
image - string - link to the image of the user's profile picture
shipping_address - string - shipping address of the user
billing_address - string - billing address of the user
username - string - user's screen name used on the website
password - string - encrypted storage of the user's password
credit_card - number - encrypted storage of the user's credit card
expiration_date - number - encrypted storage of the user's credit_card expiration
cc_last4 - number - last 4 of the user's credit card to help the identify the correct card

# Quest 4 - Completed Orders

Once they've completed their purchase, you need to permanently save it. In addition to saving mock information like was their payment successful, you'll need to track the actual monetary value of all of these things--how much did they pay and for what. If someone buys a product on sale and returns it later, you need to know not to refund the full price.

## Order Model
id - number - unique identifier
user_id - number - id of the user who made the order
item_id - number - id of each item in the order
price_id - number - id of the price for that item
total - number - total of the order
shipped_to - string - address where the order was shipped
