# Shopping Cart Implementation

This is a Python class implementation of a shopping cart for a web application, built to work with Django. It manages cart functionality using session storage, allowing users to add, remove, and calculate totals for products in their cart.

## Features
- **Session-based Cart**: Stores cart data in the user's session.
- **Add Products**: Add products to the cart with specified quantities.
- **Remove Products**: Delete individual products from the cart.
- **Clear Cart**: Remove the entire cart.
- **Iteration Support**: Iterate over cart items with product details and calculated totals.
- **Total Calculation**: Compute the total price of items in the cart.
- **Item Count**: Get the number of unique items in the cart.

## Requirements
- Python 3.x
- Django (for session management and ORM)
- A `Product` model with fields: `id`, `off_price`

## Installation
1. Ensure you have Django installed:
   ```bash
   pip install Django


Place the cart.py file in your Django project directory (e.g., within your app folder).
Ensure your Django project has a Product model defined in product.models.


Usage
Example

from cart import Cart

# Initialize cart with a request object
cart = Cart(request)

# Add a product to the cart
cart.add(pk=1, qty=2)  # Adds product with ID 1, quantity 2

# Iterate over cart items
for item in cart:
    print(item['product'], item['qty'], item['total'])

# Get total price
total = cart.total()
print(f"Total: {total}")

# Delete a product
cart.delete(id="1")

# Clear the cart
cart.remove()
Methods
__init__(self, request): Initializes the cart with the user's session.
__iter__(self): Yields cart items with product details and calculated totals.
add(self, pk, qty): Adds a product to the cart or updates its quantity.
save(self): Marks the session as modified to persist changes.
remove(self): Deletes the entire cart from the session.
delete(self, id): Removes a specific product from the cart.
count(self): Returns the number of unique items in the cart.
total(self): Calculates the total price of all items in the cart.
Assumptions
The Product model has an id and off_price field.
The session middleware is enabled in your Django settings (django.contrib.sessions.middleware.SessionMiddleware).
Prices are stored as strings in the cart and converted to integers for calculations.
Notes
Ensure proper error handling for cases like invalid product IDs or quantities in a production environment.
The cart stores product IDs and prices in the session, so price changes in the database won't reflect in the cart until updated.
This implementation assumes integer quantities and prices for simplicity.
License
This project is licensed under the MIT License - see the  file for details.