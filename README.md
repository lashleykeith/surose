# surose
This is the documentation for our marketplace app.

We are going to give you an overview of the main parts of the program that make the application work. 

### models.py (The Brain)
The models.py file in Surose/core/ directory represents the brain of the application.  In this file we see the code that allows us to store categories of data in memory by the creation of `classes`.  These classes represent the different types of data entries we use in our application.

Here are three of the main classes.
1. **User**:  (From line 8) This class represents users of your application, storing information such as username, email, and password hashes. You can think of it as the "memory center" of your application, storing vital information about the individuals interacting with your system.

2. **Product**: (From line 52) Represents the products available in your application, including details like name, description, price, and availability. It serves as the "inventory" of your application, storing data about the products your users can browse, add to their carts, and purchase.

3. **ProductOrder**: (From line 93) This class captures information about orders placed by users, including details like the user who placed the order, the products ordered, quantities, and total price. It acts as the "transaction record" of your application, keeping track of purchases made by users.

These all store data so that it can be used by the program.

### views.py (The Muscular System)
The views.py file in the Surose/core/ directory represents the brain of the application.  In this file, we see the code uses functions that allow us to move and manipulate the data we have in the models.py file.  This can be likened to the muscular system as it gives us the power to change the information from the data entries to produce the results we need in our application.

Here are three of the main functions.
1. **product_cart_add(request, product_id)**: (From line 184) This function is responsible for adding a specified product to the user's cart. It takes the `product_id` as a parameter and updates the user's cart accordingly. Think of it as the "muscle" that executes the action of adding items to the cart when prompted.

2. **product_cart_delete(request, cart_id)**: (From line 223)Handles the removal of a product from the user's cart. It takes the `cart_id` as input and removes the corresponding item from the cart. This function acts as the "muscle" that performs the action of removing items from the cart when instructed.

3. **account_order_detail(request, order_id)**: (From line 521) Retrieves and displays the details of a specific order identified by `order_id`. It fetches the relevant order information from the database and presents it to the user. This function serves as the "muscle" responsible for retrieving and rendering detailed order information when requested.

### urls.py (The Nervous System)

The views.py file in the Surose/core/ directory represents the brain of the application.  In this file, we see the code uses routes we call paths to initiate actions  These paths represent the communication of data and actions from one part of the application to another.  These paths execute the movements of the functions in views.py.

1. **path('product/checkout/', views.product_checkout, name='product_checkout')**:  (From line 13)   Represents the route for initiating the checkout process. When a user navigates to this URL, it triggers the `product_checkout` function in `views.py`, allowing users to proceed with the purchase of items in their cart. Think of it as the "nerve pathway" that guides users to the checkout process.

2. **path('account/order/payment/', views.account_order_payment, name='account_order_payment')**:  (From line 28) Defines the route for handling payment processing for orders. When users reach this URL, they are directed to the `account_order_payment` function, which facilitates payment transactions, such as entering payment details and completing the purchase. This pathway acts as the "nerve route" guiding users through the payment process.

3. **path('account/messages/', views.account_message_list, name='account_message_list')**:  (From line 41) Represents the route for accessing the list of messages in the user's account. When users visit this URL, they are directed to the `account_message_list` function, which retrieves and displays the messages associated with their account. Think of it as the "nerve pathway" that leads users to view their messages within the application.

By expanding on these classes, routes, and functions, you can enhance the functionality of your Django application, providing users with a richer and more intuitive experience.


Here are some additional classes, functions, and routes(paths) that are in this application.  These will give you greater detail about what this application does.


### Additional Classes in models.py

4. **ProductReview**:  (From line 81) Represents reviews submitted by users for products. It includes fields like the user who submitted the review, the product being reviewed, the rating, and the review content. This class serves as the "feedback center" of your application, allowing users to share their experiences with products.

5. **ProductOrder**:  (From line 93) Stores information about bulk orders placed by users or manufacturers. It includes details such as the user or manufacturer placing the order, the products ordered in bulk, quantities, and delivery information. This class acts as the "wholesale management" system of your application, handling large-scale product orders.

6. **ChatMessage**:   (From line 133) Captures messages exchanged between users within the application. It includes fields like sender, receiver, timestamp, and message content. This class serves as the "communication hub" of your application, facilitating user-to-user interactions and notifications.



### Additional Functions in views.py

4. **account_bulk_order_list(request, manufacturer_username=None)**:  (From line 579) Displays a list of bulk orders, optionally filtered by manufacturer username. It retrieves bulk order information from the database and presents it to the user. This function acts as the "bulk order viewer," allowing users to track large-scale product orders.

5. **product_review_create(request, product_id)**:  (From line 148) Handles the creation of product reviews submitted by users. It validates and processes review submissions, associating them with the corresponding product. This function serves as the "review creator," enabling users to share feedback and ratings for products.

6. **account_payout(request)**:  (From line 619) Manages payout requests initiated by users, such as transferring earnings or funds to their bank accounts. It handles payout processing and updates the user's account balance accordingly. This function acts as the "financial management tool," facilitating transactions between users and the platform.

7. **account_message_detail(request, username)**:  (From line 654) Retrieves and displays detailed information about messages exchanged with a specific user identified by their username. It fetches message history from the database and presents it to the user. This function serves as the "message viewer," allowing users to review past conversations with other users.

### Additional Routes in urls.py

4. **path('account/bulk/order/list/', views.account_bulk_order_list, name='account_bulk_order_list')**:   (From line 32) Represents the route for accessing the list of bulk orders. Users can navigate to this URL to view their bulk order history. This pathway serves as the "bulk order archive" route, providing access to past bulk order records.

5. **path('product/review/create/<product_id>/', views.product_review_create, name='product_review_create')**: (From line 20) Defines the route for submitting product reviews. Users can access this URL to submit feedback and ratings for specific products. This pathway acts as the "review submission" route, facilitating user-generated product reviews.

6. **path('account/payout/', views.account_payout, name='account_payout')**:  (From line 40) Represents the route for initiating payout requests. Users can visit this URL to request the transfer of their earnings or funds to their designated bank accounts. This pathway serves as the "payout initiation" route, enabling users to manage their finances.

7. **path('account/message/<username>/', views.account_message_detail, name='account_message_detail')**: (From line 42) Defines the route for accessing detailed message history with a specific user. Users can navigate to this URL to view their past conversations with the specified user. This pathway acts as the "message history viewer" route, facilitating communication between users.
