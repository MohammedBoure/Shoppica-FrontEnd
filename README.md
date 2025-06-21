# Admin Dashboard Layout for E-Commerce Platform

## Overview
This document outlines the design of a comprehensive admin dashboard for an e-commerce platform, utilizing the provided APIs. The dashboard is structured into main pages covering essential functionalities such as user management, product management, orders, discounts, reviews, addresses, and a Point of Sale (POS) system. Each page uses multiple APIs as needed, with descriptions of their purpose and links to related pages. The admin has full permissions, including access to APIs that do not require authentication or are intended for regular users, as admins are essentially users with elevated privileges.

---

## Dashboard Structure

### 1. Main Dashboard
- **Description**: Provides an overview of platform performance, including total sales, user count, new orders, and top-selling products. Contains quick links to other pages.
- **APIs Used**:
  - `/orders` (GET): Retrieve total orders and sales analytics.
  - `/users` (GET): Display the number of registered users.
  - `/products` (GET): Show top-selling products.
  - `/reviews` (GET): Display recent reviews.
- **Links to Other Pages**:
  - User Management
  - Product Management
  - Order Management
  - Review Management
  - Point of Sale (POS)

### 2. User Management
- **Description**: Allows viewing, adding, editing, and deleting users. Supports searching users by ID, email, or username, and validating passwords.
- **APIs Used**:
  - `/users` (GET): Retrieve paginated list of users.
  - `/users/<user_id>` (GET, PUT, DELETE): View, update, or delete a user.
  - `/users/email/<email>` (GET): Search user by email.
  - `/users/username/<username>` (GET): Search user by username.
  - `/users/<user_id>/validate-password` (POST): Validate user password.
  - `/users` (POST): Register a new user (for manual addition).
- **Links to Other Pages**:
  - User Details (to view addresses, orders, or cart).
  - Address Management (to manage user addresses).
  - Order Management (to view user orders).

### 3. User Details
- **Description**: Displays detailed information about a specific user, including personal info, addresses, orders, cart items, and discount usages.
- **APIs Used**:
  - `/users/<user_id>` (GET): View user information.
  - `/admin/addresses/user/<user_id>` (GET): View user addresses.
  - `/orders/user/<user_id>` (GET): View user orders.
  - `/admin/cart_items/user/<user_id>` (GET): View user cart items.
  - `/discount_usages/user/<user_id>` (GET): View user discount usages.
- **Links to Other Pages**:
  - Address Management
  - Order Management
  - Cart Management

### 4. Address Management
- **Description**: Allows viewing, editing, and deleting user addresses, with the option to add new addresses.
- **APIs Used**:
  - `/admin/addresses` (GET): Retrieve paginated addresses.
  - `/admin/addresses/user/<user_id>` (GET): View addresses for a specific user.
  - `/addresses/<address_id>` (GET, PUT, DELETE): Retrieve, update, or delete an address.
  - `/addresses` (POST): Add a new address.
- **Links to Other Pages**:
  - User Details

### 5. Category Management
- **Description**: Enables creating, updating, and deleting categories, with a tree view of categories (parent and subcategories).
- **APIs Used**:
  - `/categories` (GET, POST): List or create categories.
  - `/categories/<category_id>` (GET, PUT, DELETE): View, update, or delete a category.
  - `/categories/parent` (GET): List categories by parent ID.
- **Links to Other Pages**:
  - Product Management (to add products to categories).
  - Category Discount Management

### 6. Product Management
- **Description**: Allows adding, editing, and deleting products, including managing associated images. Products can be filtered by category.
- **APIs Used**:
  - `/products` (GET, POST): List or add products.
  - `/products/<product_id>` (GET, PUT, DELETE): View, update, or delete a product.
  - `/products/category/<category_id>` (GET): List products by category.
  - `/products/<product_id>/images` (POST, GET): Add or view product images.
  - `/products/images/<image_id>` (GET, PUT, DELETE): View, update, or delete a product image.
- **Links to Other Pages**:
  - Category Management
  - Product Discount Management
  - Review Management

### 7. Review Management
- **Description**: Allows viewing, editing, and deleting reviews, with filtering by product.
- **APIs Used**:
  - `/reviews` (GET): Retrieve paginated reviews.
  - `/reviews/<review_id>` (GET, PUT, DELETE): View, update, or delete a review.
  - `/reviews/product/<product_id>` (GET): List reviews for a specific product.
- **Links to Other Pages**:
  - Product Management

### 8. Order Management
- **Description**: Allows viewing, editing, and deleting orders, with details on order items and payments.
- **APIs Used**:
  - `/orders` (GET): Retrieve paginated orders.
  - `/orders/<order_id>` (GET, PUT, DELETE): View, update, or delete an order.
  - `/orders/user/<user_id>` (GET): List orders for a specific user.
  - `/order_items/order/<order_id>` (GET): List order items for an order.
  - `/order_items/<order_item_id>` (GET, PUT, DELETE): Manage an order item.
  - `/payments/order/<order_id>` (GET): List payments for an order.
- **Links to Other Pages**:
  - User Details
  - Payment Management

### 9. Payment Management
- **Description**: Allows viewing, editing, and deleting payments, linked to orders.
- **APIs Used**:
  - `/payments` (GET): Retrieve paginated payments.
  - `/payments/<payment_id>` (GET, PUT, DELETE): View, update, or delete a payment.
  - `/payments/order/<order_id>` (GET): List payments for a specific order.
- **Links to Other Pages**:
  - Order Management

### 10. Discount Management
- **Description**: Allows creating, editing, and deleting discounts (general, product, category), with tracking of discount usages.
- **APIs Used**:
  - `/discounts` (GET, POST): List or add general discounts.
  - `/discounts/<discount_id>` (GET, PUT, DELETE): Manage a general discount.
  - `/product_discounts` (GET, POST): List or add product discounts.
  - `/product_discounts/<discount_id>` (GET, PUT, DELETE): Manage a product discount.
  - `/category_discounts` (GET, POST): List or add category discounts.
  - `/category_discounts/<discount_id>` (GET, PUT, DELETE): Manage a category discount.
  - `/discount_usages` (GET): List discount usages.
  - `/discount_usages/discount/<discount_id>` (GET): List usages for a specific discount.
- **Links to Other Pages**:
  - Product Management
  - Category Management

### 11. Point of Sale (POS)
- **Description**: Enables direct sales from a physical store, allowing order creation, item addition, discount application, and payment recording. Interacts directly with the database.
- **APIs Used**:
  - `/products` (GET): List available products.
  - `/products/<product_id>` (GET): View product details.
  - `/categories` (GET): Filter products by category.
  - `/orders` (GET, POST): Create or view orders.
  - `/order_items` (POST): Add items to an order.
  - `/discounts/code/<code>` (GET): Validate a discount code.
  - `/discount_usages` (POST): Record discount usage.
  - `/payments` (POST): Record a payment.
  - `/users` (GET): Search for a user (to link order to existing user).
  - `/users` (POST): Create a new user if not found.
  - `/addresses` (GET, POST): Add or select an address for the order.
- **Links to Other Pages**:
  - Order Management (to track recorded orders).
  - User Details (to manage customer accounts).
  - Discount Management

### 12. Cart Management
- **Description**: Allows viewing and managing user carts, with options to edit or delete items.
- **APIs Used**:
  - `/admin/cart_items` (GET): Retrieve paginated carts.
  - `/admin/cart_items/user/<user_id>` (GET): View cart for a specific user.
  - `/cart/items/<cart_item_id>` (GET, PUT, DELETE): View, update, or delete a cart item.
  - `/cart/items` (POST, GET): Add or view cart items.
- **Links to Other Pages**:
  - User Details
  - Product Management

---

## General Notes
- **User Experience**: The dashboard should be user-friendly with robust filtering and search tools on each page.
- **Security**: Admin permissions are verified for each API request to prevent unauthorized access.
- **POS Integration**: The POS page is designed for speed and supports instant sales, with options to add new customers or apply discounts during checkout.
- **Pagination**: All lists (users, products, orders, etc.) support pagination for performance optimization.
- **Navigation**: Links between pages facilitate seamless navigation, e.g., moving from user details to their orders or addresses.

This layout covers all required functionalities and ensures comprehensive and efficient platform management. For further details on a specific page or additional features, please provide clarification.



# Public-Facing Interactive Interface Layout for E-Commerce Platform

## Overview
This document outlines the design of the public-facing interactive interfaces for an e-commerce platform, utilizing the provided APIs. The interface is structured into pages tailored for general users (public or authenticated), covering essential functionalities such as user authentication, browsing products, managing carts, placing orders, applying discounts, submitting reviews, and managing user profiles. Each page leverages relevant APIs, with descriptions of their purpose and links to related pages. The design assumes that authenticated users have access to session-based APIs, while public users can access non-authenticated endpoints.

---

## Interface Structure

### 1. Homepage
- **Description**: The main landing page showcasing featured products, categories, and promotions. It allows users to browse products and categories without authentication and provides quick access to login/register.
- **APIs Used**:
  - `/products` (GET): Retrieve a paginated list of active products (e.g., for featured products).
  - `/categories` (GET): List all categories for browsing.
  - `/categories/parent` (GET): Display top-level categories or categories by parent ID.
  - `/product_discounts/valid/<product_id>` (GET): Show valid discounts for featured products.
  - `/category_discounts/valid/<category_id>` (GET): Show valid discounts for categories.
- **Links to Other Pages**:
  - Product Listing
  - Category Listing
  - Product Details
  - Login/Register
  - Cart

### 2. Login/Register Page
- **Description**: Allows users to log in, register, or log out. Provides forms for authentication and account creation.
- **APIs Used**:
  - `/login` (POST): Authenticate user and start a session.
  - `/users` (POST): Register a new user.
  - `/logout` (POST): Log out the current user (requires authentication).
- **Links to Other Pages**:
  - Homepage (after login/register)
  - User Profile (after login)
  - Cart (after login)

### 3. Product Listing
- **Description**: Displays a paginated list of active products, with filters for categories and search functionality. Users can view discounts for products or categories.
- **APIs Used**:
  - `/products` (GET): Retrieve paginated active products.
  - `/products/category/<category_id>` (GET): List active products in a specific category.
  - `/product_discounts/valid/<product_id>` (GET): Retrieve valid discounts for products.
  - `/category_discounts/valid/<category_id>` (GET): Retrieve valid discounts for a category.
- **Links to Other Pages**:
  - Product Details
  - Category Listing
  - Cart (for adding products)

### 4. Category Listing
- **Description**: Displays a hierarchical view of categories (parent and subcategories) for browsing products. Users can filter products by category.
- **APIs Used**:
  - `/categories` (GET): Retrieve paginated list of all categories.
  - `/categories/parent` (GET): List categories by parent ID (or top-level categories).
  - `/category_discounts/valid/<category_id>` (GET): Show valid discounts for categories.
- **Links to Other Pages**:
  - Product Listing
  - Product Details (via products in a category)

### 5. Product Details
- **Description**: Shows detailed information about a specific product, including images, reviews, and available discounts. Users can add the product to their cart.
- **APIs Used**:
  - `/products/<product_id>` (GET): Retrieve details of a specific active product.
  - `/products/<product_id>/images` (GET): List all images for the product.
  - `/products/images/<image_id>` (GET): Retrieve a specific product image.
  - `/reviews/product/<product_id>` (GET): List reviews for the product.
  - `/product_discounts/valid/<product_id>` (GET): Show valid discounts for the product.
  - `/cart/items` (POST): Add the product to the cart (requires authentication).
- **Links to Other Pages**:
  - Cart (after adding product)
  - Review Submission (if authenticated)
  - Product Listing

### 6. Cart
- **Description**: Displays the authenticated user's cart items, allowing them to update quantities, remove items, or proceed to checkout. Users can apply discount codes.
- **APIs Used**:
  - `/cart/items` (GET): Retrieve all cart items for the authenticated user.
  - `/cart/items/<cart_item_id>` (GET, PUT, DELETE): View, update quantity, or delete a specific cart item.
  - `/cart/items` (POST): Add a new item to the cart.
  - `/discounts/code/<code>` (GET): Validate a discount code.
  - `/discounts/valid/<code>` (GET): Retrieve a valid discount by code.
  - `/discount_usages` (POST): Record usage of a discount (during checkout).
- **Links to Other Pages**:
  - Checkout
  - Product Listing
  - Product Details

### 7. Checkout
- **Description**: Allows users to review their cart, select or add a shipping address, apply discounts, and make a payment to place an order.
- **APIs Used**:
  - `/cart/items` (GET): Display cart items for review.
  - `/addresses/me` (GET): Retrieve all addresses for the authenticated user.
  - `/addresses` (POST): Add a new address for the order.
  - `/discounts/code/<code>` (GET): Validate a discount code.
  - `/discount_usages` (POST): Record discount usage.
  - `/orders` (POST): Create a new order.
  - `/order_items` (POST): Add items to the order (handled during order creation).
  - `/payments` (POST): Record a payment for the order.
- **Links to Other Pages**:
  - Order Confirmation
  - Address Management
  - Cart

### 8. Order Confirmation
- **Description**: Displays confirmation details after a successful order, including order summary, payment status, and shipping address.
- **APIs Used**:
  - `/orders/<order_id>` (GET): Retrieve details of the placed order.
  - `/order_items/order/<order_id>` (GET): List items in the order.
  - `/payments/order/<order_id>` (GET): Retrieve payment details for the order.
  - `/addresses/<address_id>` (GET): Show the selected shipping address.
- **Links to Other Pages**:
  - Order History
  - User Profile

### 9. Order History
- **Description**: Shows a list of the authenticated user's past and current orders, with details for each order.
- **APIs Used**:
  - `/orders/user/<user_id>` (GET): Retrieve all orders for the authenticated user.
  - `/orders/<order_id>` (GET): View details of a specific order.
  - `/order_items/order/<order_id>` (GET): List items in a specific order.
  - `/payments/order/<order_id>` (GET): View payments for a specific order.
- **Links to Other Pages**:
  - Order Confirmation (for order details)
  - User Profile

### 10. User Profile
- **Description**: Allows authenticated users to view and update their personal information, manage addresses, and view discount usages.
- **APIs Used**:
  - `/me` (GET): Retrieve current authenticated user’s details.
  - `/users/<user_id>` (PUT): Update user information (self).
  - `/addresses/me` (GET): List all addresses for the authenticated user.
  - `/addresses/<address_id>` (GET, PUT, DELETE): View, update, or delete a specific address.
  - `/addresses` (POST): Add a new address.
  - `/discount_usages/user/<user_id>` (GET): View discount usages for the authenticated user.
- **Links to Other Pages**:
  - Address Management
  - Order History
  - Logout (via Login/Register page)

### 11. Address Management
- **Description**: Allows authenticated users to view, add, edit, or delete their shipping addresses.
- **APIs Used**:
  - `/addresses/me` (GET): Retrieve all addresses for the authenticated user.
  - `/addresses/<address_id>` (GET, PUT, DELETE): View, update, or delete a specific address.
  - `/addresses` (POST): Add a new address.
- **Links to Other Pages**:
  - User Profile
  - Checkout

### 12. Review Submission
- **Description**: Allows authenticated users to submit or update reviews for products they have purchased.
- **APIs Used**:
  - `/reviews` (POST): Submit a new review.
  - `/reviews/<review_id>` (PUT, DELETE): Update or delete an existing review (if authored by the user).
  - `/reviews/product/<product_id>` (GET): View existing reviews for context.
- **Links to Other Pages**:
  - Product Details
  - User Profile

---

## General Notes
- **User Experience**: The interface is designed to be intuitive, with search and filter options for products and categories, and clear navigation for authenticated users.
- **Public vs. Authenticated Access**: Non-authenticated users can browse products, categories, and reviews, but actions like adding to cart, submitting reviews, or placing orders require authentication.
- **Security**: Session-based APIs (e.g., `/cart/items`, `/orders`) ensure that only authenticated users can access or modify their data.
- **Pagination**: Product, category, and review listings support pagination for performance with large datasets.
- **Navigation**: Links between pages (e.g., from Product Details to Cart or Review Submission) ensure a seamless user journey.
- **Discount Handling**: Users can apply valid discount codes during checkout, with validation via `/discounts/valid/<code>`.

This layout provides a comprehensive and user-friendly interface for public and authenticated users, covering all necessary e-commerce functionalities using the provided APIs. For additional features or specific page details, please provide further clarification.