# auth
| Endpoint  | Method | Auth Required | Description                         | Status Codes        |
| --------- | ------ | ------------- | ----------------------------------- | ------------------- |
| `/login`  | `POST` | ❌             | Authenticate user and start session | `200`, `400`, `401` |
| `/me`     | `GET`  | ✅             | Get current authenticated user      | `200`, `401`, `404` |
| `/logout` | `POST` | ✅             | Logout the current user             | `200`, `401`        |


# user
| Endpoint                             | Method   | Auth Required  | Description                | Status Codes               |
| ------------------------------------ | -------- | -------------- | -------------------------- | -------------------------- |
| `/users`                             | `POST`   | ❌              | Register a new user        | `201`, `400`, `500`        |
| `/users/<user_id>`                   | `GET`    | ✅ (Self/Admin) | Get user by ID             | `200`, `403`, `404`        |
| `/users/email/<email>`               | `GET`    | ✅ (Self/Admin) | Get user by email          | `200`, `403`, `404`        |
| `/users/username/<username>`         | `GET`    | ✅ (Self/Admin) | Get user by username       | `200`, `403`, `404`        |
| `/users/<user_id>`                   | `PUT`    | ✅ (Self/Admin) | Update user by ID          | `200`, `400`, `403`        |
| `/users/<user_id>`                   | `DELETE` | ✅ Admin        | Delete user by ID          | `200`, `403`, `404`        |
| `/users`                             | `GET`    | ✅ Admin        | Get all users (paginated)  | `200`, `403`               |
| `/users/<user_id>/validate-password` | `POST`   | ✅ (Self/Admin) | Validate a user's password | `200`, `400`, `401`, `403` |


# adresse
| Endpoint                          | Method   | Auth Required | Description                                        | Status Codes                      |
| --------------------------------- | -------- | ------------- | -------------------------------------------------- | --------------------------------- |
| `/addresses`                      | `POST`   | ✅ Session     | Add a new address for the authenticated user       | `201`, `400`, `403`, `500`        |
| `/addresses/me`                   | `GET`    | ✅ Session     | Get all addresses for the current user             | `200`, `403`, `500`               |
| `/addresses/<address_id>`         | `GET`    | ✅ Session     | Get a specific address (owner or admin only)       | `200`, `403`, `404`, `500`        |
| `/addresses/<address_id>`         | `PUT`    | ✅ Session     | Update an address (owner or admin only)            | `200`, `400`, `403`, `404`, `500` |
| `/addresses/<address_id>`         | `DELETE` | ✅ Session     | Delete an address (owner or admin only)            | `200`, `403`, `404`, `500`        |
| `/admin/addresses/user/<user_id>` | `GET`    | ✅ Admin       | Get all addresses for a specific user (admin only) | `200`, `403`, `500`               |
| `/admin/addresses`                | `GET`    | ✅ Admin       | Get a paginated list of all addresses (admin only) | `200`, `403`, `500`               |


# categories
| Endpoint                    | Method   | Auth Required | Description                                                 | Status Codes               |
| --------------------------- | -------- | ------------- | ----------------------------------------------------------- | -------------------------- |
| `/categories`               | `POST`   | ✅ Admin       | Create a new category                                       | `201`, `400`, `403`, `500` |
| `/categories/<category_id>` | `GET`    | ❌             | Get category by ID                                          | `200`, `404`               |
| `/categories/parent`        | `GET`    | ❌             | Get categories by parent ID (or top-level if not specified) | `200`                      |
| `/categories/<category_id>` | `PUT`    | ✅ Admin       | Update an existing category                                 | `200`, `400`, `403`        |
| `/categories/<category_id>` | `DELETE` | ✅ Admin       | Delete a category by ID                                     | `200`, `403`, `404`        |
| `/categories`               | `GET`    | ❌             | Get all categories (paginated)                              | `200`                      |

# products
| Endpoint                           | Method   | Auth Required | Description                           | Status Codes               |
| ---------------------------------- | -------- | ------------- | ------------------------------------- | -------------------------- |
| `/products`                        | `POST`   | ✅ Admin       | Add a new product with optional image | `201`, `400`, `403`, `500` |
| `/products/<product_id>`           | `GET`    | ❌             | Get product by ID (only if active)    | `200`, `404`, `500`        |
| `/products/category/<category_id>` | `GET`    | ❌             | Get all active products in a category | `200`, `500`               |
| `/products`                        | `GET`    | ❌             | Get all active products (paginated)   | `200`, `500`               |
| `/products/<product_id>`           | `PUT`    | ✅ Admin       | Update a product (fields and image)   | `200`, `400`, `403`, `500` |
| `/products/<product_id>`           | `DELETE` | ✅ Admin       | Delete a product by ID                | `200`, `403`, `404`, `500` |
| `/products/<product_id>/images`    | `POST`   | ✅ Admin       | Upload a new image for a product      | `201`, `400`, `403`, `500` |
| `/products/<product_id>/images`    | `GET`    | ❌             | Get all images for a product          | `200`, `500`               |
| `/products/images/<image_id>`      | `GET`    | ❌             | Get a product image by its ID         | `200`, `404`, `500`        |
| `/products/images/<image_id>`      | `PUT`    | ✅ Admin       | Update an existing product image      | `200`, `400`, `403`, `500` |
| `/products/images/<image_id>`      | `DELETE` | ✅ Admin       | Delete a product image by ID          | `200`, `403`, `404`, `500` |



# reviews
| Endpoint                        | Method   | Auth Required | Description                                   | Status Codes               |
| ------------------------------- | -------- | ------------- | --------------------------------------------- | -------------------------- |
| `/reviews`                      | `POST`   | ✅ Session     | Add a new review (user or admin)              | `201`, `400`, `403`, `500` |
| `/reviews/<review_id>`          | `GET`    | ❌             | Get review by ID (public access)              | `200`, `404`               |
| `/reviews/product/<product_id>` | `GET`    | ❌             | Get all reviews for a product (public access) | `200`                      |
| `/reviews/<review_id>`          | `PUT`    | ✅ Session     | Update a review (user or admin)               | `200`, `400`, `403`, `404` |
| `/reviews/<review_id>`          | `DELETE` | ✅ Session     | Delete a review (user or admin)               | `200`, `403`, `404`        |
| `/reviews`                      | `GET`    | ✅ Admin       | Get all reviews (paginated)                   | `200`, `403`               |

# Cart Items
| Endpoint                           | Method   | Auth Required  | Description                                         | Status Codes                      |
| ---------------------------------- | -------- | -------------- | --------------------------------------------------- | --------------------------------- |
| `/cart/items`                      | `POST`   | ✅ Session      | Add a new item to the authenticated user's cart     | `201`, `400`, `403`, `500`        |
| `/cart/items`                      | `GET`    | ✅ Session      | Get all cart items for the authenticated user       | `200`, `403`, `500`               |
| `/cart/items/<cart_item_id>`       | `GET`    | ✅ Session/User | Get a specific cart item (owner or admin only)      | `200`, `403`, `404`, `500`        |
| `/cart/items/<cart_item_id>`       | `PUT`    | ✅ Session/User | Update quantity of a specific cart item             | `200`, `400`, `403`, `404`, `500` |
| `/cart/items/<cart_item_id>`       | `DELETE` | ✅ Session/User | Delete a specific cart item (owner or admin only)   | `200`, `403`, `404`, `500`        |
| `/admin/cart_items/user/<user_id>` | `GET`    | ✅ Admin        | Get all cart items for a specific user (admin only) | `200`, `403`, `500`               |
| `/admin/cart_items`                | `GET`    | ✅ Admin        | Get all cart items (paginated, admin only)          | `200`, `403`, `500`               |



# Orders 
| Endpoint                 | Method   | Auth Required | Description                                              | Status Codes               |
| ------------------------ | -------- | ------------- | -------------------------------------------------------- | -------------------------- |
| `/orders`                | `POST`   | ✅ Session     | Add a new order (only for the same user or admin)        | `201`, `400`, `403`, `500` |
| `/orders/<order_id>`     | `GET`    | ✅ Session     | Get a specific order (owner or admin only)               | `200`, `403`, `404`        |
| `/orders/user/<user_id>` | `GET`    | ✅ Session     | Get all orders for a specific user (owner or admin only) | `200`, `403`               |
| `/orders/<order_id>`     | `PUT`    | ✅ Admin       | Update an existing order (admin only)                    | `200`, `400`, `403`        |
| `/orders/<order_id>`     | `DELETE` | ✅ Admin       | Delete an order by ID (admin only)                       | `200`, `403`, `404`        |
| `/orders`                | `GET`    | ✅ Admin       | Get all orders (paginated, admin only)                   | `200`, `403`               |

# Order Items
| Endpoint                        | Method   | Auth Required | Description                                                    | Status Codes               |
| ------------------------------- | -------- | ------------- | -------------------------------------------------------------- | -------------------------- |
| `/order_items`                  | `POST`   | ✅ Admin       | Add a new order item (admin only)                              | `201`, `400`, `403`, `500` |
| `/order_items/<order_item_id>`  | `GET`    | ✅ Session     | Get a specific order item (owner or admin only)                | `200`, `403`, `404`        |
| `/order_items/order/<order_id>` | `GET`    | ✅ Session     | Get all order items for a specific order (owner or admin only) | `200`, `403`, `404`        |
| `/order_items/<order_item_id>`  | `PUT`    | ✅ Admin       | Update an existing order item (admin only)                     | `200`, `400`, `403`        |
| `/order_items/<order_item_id>`  | `DELETE` | ✅ Admin       | Delete an order item by ID (admin only)                        | `200`, `403`, `404`        |
| `/order_items`                  | `GET`    | ✅ Admin       | Get all order items (paginated, admin only)                    | `200`, `403`               |


# Payments 
| Endpoint                     | Method   | Auth Required | Description                                                 | Status Codes               |
| ---------------------------- | -------- | ------------- | ----------------------------------------------------------- | -------------------------- |
| `/payments`                  | `POST`   | ✅ Session     | Add a new payment (authenticated users only)                | `201`, `400`, `403`, `500` |
| `/payments/<payment_id>`     | `GET`    | ✅ Session     | Get a specific payment (authenticated users only)           | `200`, `403`, `404`        |
| `/payments/order/<order_id>` | `GET`    | ✅ Session     | Get all payments for a specific order (authenticated users) | `200`, `403`               |
| `/payments/<payment_id>`     | `PUT`    | ✅ Admin       | Update an existing payment (admin only)                     | `200`, `400`, `403`        |
| `/payments/<payment_id>`     | `DELETE` | ✅ Admin       | Delete a payment by ID (admin only)                         | `200`, `403`, `404`        |
| `/payments`                  | `GET`    | ✅ Admin       | Get all payments (paginated, admin only)                    | `200`, `403`               |

# discounts
| Endpoint                   | Method   | Auth Required | Description                                                       | Status Codes               |
| -------------------------- | -------- | ------------- | ----------------------------------------------------------------- | -------------------------- |
| `/discounts`               | `POST`   | ✅ Admin       | Create a new discount                                             | `201`, `400`, `403`, `500` |
| `/discounts/<discount_id>` | `GET`    | ✅ Admin       | Retrieve a discount by its ID                                     | `200`, `403`, `404`, `500` |
| `/discounts/code/<code>`   | `GET`    | ✅ User        | Retrieve a discount by its code (session required)                | `200`, `403`, `404`, `500` |
| `/discounts/valid/<code>`  | `GET`    | ✅ User        | Retrieve a valid (active, unexpired, usable) discount by its code | `200`, `403`, `404`, `500` |
| `/discounts/<discount_id>` | `PUT`    | ✅ Admin       | Update an existing discount                                       | `200`, `400`, `403`, `500` |
| `/discounts/<discount_id>` | `DELETE` | ✅ Admin       | Delete a discount                                                 | `200`, `403`, `404`, `500` |
| `/discounts`               | `GET`    | ✅ Admin       | Retrieve all discounts (paginated)                                | `200`, `403`, `500`        |


# Discount Usages
| Endpoint                                  | Method   | Auth Required | Description                                             | Status Codes               |
| ----------------------------------------- | -------- | ------------- | ------------------------------------------------------- | -------------------------- |
| `/discount_usages`                        | `POST`   | ✅ Session     | Add a new discount usage (for authenticated users only) | `201`, `400`, `403`, `500` |
| `/discount_usages/<usage_id>`             | `GET`    | ✅ Admin       | Get a discount usage by ID (admin only)                 | `200`, `403`, `404`, `500` |
| `/discount_usages/discount/<discount_id>` | `GET`    | ✅ Admin       | Get all usages for a specific discount (admin only)     | `200`, `403`, `500`        |
| `/discount_usages/user/<user_id>`         | `GET`    | ✅ Session     | Get all usages for a specific user (must match session) | `200`, `403`, `500`        |
| `/discount_usages/<usage_id>`             | `DELETE` | ✅ Admin       | Delete a discount usage by ID (admin only)              | `200`, `403`, `404`, `500` |
| `/discount_usages`                        | `GET`    | ✅ Admin       | Get paginated list of all discount usages (admin only)  | `200`, `403`, `500`        |

# Product Discounts
| Endpoint                                  | Method   | Auth Required | Description                                                     | Status Codes               |
| ----------------------------------------- | -------- | ------------- | --------------------------------------------------------------- | -------------------------- |
| `/product_discounts`                      | `POST`   | ✅ Admin       | Create a new product discount                                   | `201`, `400`, `403`, `500` |
| `/product_discounts/<discount_id>`        | `GET`    | ✅ Admin       | Retrieve a discount by its ID                                   | `200`, `403`, `404`, `500` |
| `/product_discounts/product/<product_id>` | `GET`    | ❌ Public      | Get all discounts for a specific product                        | `200`, `400`, `500`        |
| `/product_discounts/valid/<product_id>`   | `GET`    | ❌ Public      | Get valid (active and current) discounts for a specific product | `200`, `400`, `500`        |
| `/product_discounts/<discount_id>`        | `PUT`    | ✅ Admin       | Update a product discount                                       | `200`, `400`, `403`, `500` |
| `/product_discounts/<discount_id>`        | `DELETE` | ✅ Admin       | Delete a product discount                                       | `200`, `403`, `404`, `500` |
| `/product_discounts`                      | `GET`    | ✅ Admin       | Get all product discounts (paginated)                           | `200`, `403`, `500`        |


# Category Discounts
| Endpoint                                          | Method   | Auth Required | Description                                                   | Status Codes               |
| ------------------------------------------------- | -------- | ------------- | ------------------------------------------------------------- | -------------------------- |
| `/category_discounts`                             | `POST`   | ✅ Admin       | Add a new category discount                                    | `201`, `400`, `403`, `500` |
| `/category_discounts/<discount_id>`               | `PUT`    | ✅ Admin       | Update an existing category discount                           | `200`, `400`, `403`, `404`, `500` |
| `/category_discounts/<discount_id>`               | `GET`    | ✅ Admin       | Get a specific category discount by ID                         | `200`, `403`, `404`, `500` |
| `/category_discounts/category/<category_id>`      | `GET`    | ❌ Public      | Get all discounts for a specific category                      | `200`, `500`               |
| `/category_discounts/valid/<category_id>`         | `GET`    | ❌ Public      | Get valid discounts for a specific category                    | `200`, `500`               |
| `/category_discounts/<discount_id>`               | `DELETE` | ✅ Admin       | Delete a category discount by ID                               | `200`, `403`, `404`, `500` |
| `/category_discounts`                             | `GET`    | ✅ Admin       | Get paginated list of all category discounts (admin only)     | `200`, `403`, `500`        |




