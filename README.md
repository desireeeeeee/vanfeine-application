# VAN'&FEINE WEB APPLICATION
Welcome to the VAN'&FIENE web application READNE.md. This file outlines the project background, requirements, app features, and instructions on how to use the customer and vendor servers :)

## Table of Contents
* [Background](background)
* [Technolgies](#technologies)
* [VAN'&FIENE Customer Server](#VAN'&FEINE-Customer-Server)
* [Customer App Instructions](#Customer-App-Instruction)
* [VAN'&FEINE Vendor Server](#VAN'&FEINE-Vendor-Server)
* [Vendor App Instructions](#Vendor-App-Instruction)

## Background
This fullstack web development project was developed by the Caffeine Addicts in INFO30005 Web Information Technologies. 

The project required the design and and development of a web app for VAN'&FEINE, a new startup company operating in Melbourne. VAN'&FEINE runs a fleet of food trucks that work as popup cafes.

Our vendors drive around Melbourne, parking wherever they think there are customers. They have no fixed schedul and are mobile and flexible. Some vendors tend to go to the same places each day, while others are more random, or try to park near big events like sporting matches and university open days.

While our vans don’t have fixed locations, their current location is very important to our customers, who need to be able to find nearby vans when they’re hungry. We make this information available to customers via a web app. To save time, the app also allows registered customers to order their snacks in advance of arriving at the van.

The application is deployed across two servers:
1. Customer Server: https://caffeine-addicts-webapp.herokuapp.com 
2. Vendor Server: https://caffeine-addicts-vendor-webapp.herokuapp.com/vendor

The servers have different features and functions, however, work in conjuction to faciliate order requests and fulfilment. Complete descriptions of the customer and vendor requirements, and instructions on how to use each application are found below.

## Technologies
The technolgies utilised in this project include 
- Languages: JavaScript, HTML, CSS
- Runtime: Node.js
- Framework: Express
- Database: MongoDB
- Deployment: Heroku

## VAN'&FIENE Customer Server
Access the customer server through https://caffeine-addicts-webapp.herokuapp.com 

Create your own account or login as a sample customer using: </br>
email: homersimpson@gmail.com <br />
password: homersimpson123 <br />

Send order requests to to "Coffee 'n' Chill" or "Mocha Mood" if you would like to test the vendor order fulfilment functions on the vendor server. See the "VAN'&FIENE Vendor Server" section for vendor login details. 

For further details on the customer application requirements, features, and functions, see below.

Note: enable location services on your browser to experience the full application offering.

### Customer Requirement Quickview
- [x] signup
- [x] login
- [x] logout
- [x] view closest open vans 
- [x] select van to order from
- [x] view menu
- [x] view one menu item
- [x] add menu item to cart
- [x] view cart
- [x] place order/checkout
- [x] view unfulfilled order details
- [x] update placed order
- [x] cancel placed order
- [x] view fulfilled order details
- [x] view complete order history

### Requirement Background
When a customer opens their app, they first need to see where the nearest vans are. To do this, the app needs to get the customer’s location, access current van locations from the database, calculate the three nearest vans, and display their details. 

After the customer chooses the van they want to purchase from (it won’t necessarily be the closest one) a menu should appear which lists all the snacks available. Every van offers the same menu, because we are a chain - but customers order from a specific van.

To find a van and see the menu, customers don’t need to be logged in. But to proceed beyond this point and place an order, they need to log in. (If a prospective customer doesn’t already have an account, they’ll need to register and create one.) 

Use good security practices such as authentication and session management to handle logins and registrations and to appropriately restrict access to features and data.

Having seen the menu, a logged-in customer can now place an order. An order consists of one or more snacks. When the customer has entered their order details, ask them to confirm, then save the order in the database and make it visible to the chosen vendor, who must now prepare the snacks. Orders need to be timestamped, because we give customers a 20% discount if snacks are not ready in 15 minutes. Once an order has been placed, customers may want to monitor its status, such as whether it has been fulfilled and is ready for pickup.

Customers tend to change their mind a lot, and we need to design for this. We allow customers to change or cancel their order within 10 minutes of placing it and before it is fulfilled: after that they must pay for the original order. A cancelled order should be invisible to customer and vendor, but not deleted from the database, as we must keep track of this behaviour. Changing an order may involve adding or subtracting items or changing any of the quantities. If a customer changes their order, the timestamp is reset and their 10-minute change window starts again. 

Payment is automatically handled by an external payments system, so you don’t need to implement payment in your app.

### Customer App Instructions
#### Login
To test the customer application, create your own account using the sign up funtion or login with credentials:

email: homersimpson@gmail.com <br />
password: homersimpson123 <br />

Successful login will load a homepage and navigation bar with additional features. Unsuccessful login display a message stating wrong username or password.

#### Signup
Enter your chosen first name, last name, email, and password and press "Signup". If the email is not already registered a new customer account will be created, otherwise alerting that a user with the given email already exists.

#### Logout
Ends the customers authenticated session and redirects to the customer homepage.

#### View/Select Vans
ensure your location services is enabled in the browser to view the map and see the closest vans to you ***

Select a van to order from either from clicking the pin icon on the map or the list of vans.

#### Complete Menu
Beverage and snack options are available on the menu tab of the navigation bar

#### One Menu Item
Click the name of one food on the menu page to view the details of that specific item. If the user is not logged in there will be a message stating tat only logged in users can add items to cart.

If the user is logged in, an option to add an item to cart is visible.

#### Cart
The cart tab on the navigation bar shows the menu items logged in customers have in their cart. Customers can remove items and change the quantities before submitting their order. Clicking "checkout" submits the order and redirects the user to an order summary receipt page.

#### Pending Order Details/Receipt Page
Displays details of the submitted order contents and the van to pick up from. There is a timer denoting the time available to update or cancel their unfulfilled order.

#### Complete Order History
Lists the users order history.

#### Completed Order Details
Displays details of the submitted order contents and the van to pick up from. If an order was discounted, it will show on the page.

## VAN'&FEINE Vendor Server
Access the vendor server through https://caffeine-addicts-vendor-webapp.herokuapp.com/vendor/login 

Experience the app by logging as vendor Coffee 'n' Chill  using: <br />
email: coffeenchill@gmail.com </br>
password: coffeenchill123 </br>

or Mocha Mood: <br />
email: mochamood@gmail.com <br />
password: mochamood123 </br>


You will be able to view and fufil any orders sent to this van.

For further details on the vendor application requirements, features, and functions, see below.

Note: enable location services on your browser to experience the full application offering.

### Vendor Requirement Quickview
- [x] login
- [x] logout
- [x] open van for business
- [x] close van for business
- [x] update message and location
- [x] view all pending orders
- [x] view one pending order details
- [x] mark order as "ready"
- [x] mark order as collected
- [x] view all completed orders
- [x] view one completed order details

### Requirement Background
The vendors log in using the van email.

When a vendor has parked and is ready to start selling, they need to send their location to the database and mark themselves as open-for- business. Allow them to enter a short text address (e.g. “on Grattan st outside Melbourne Uni”). At the same time, have the app capture their geo-location. When they leave this location to drive somewhere else or quit for the day, allow the vendor to mark this in the database.
 
Vendors need a screen with a list of their van’s outstanding orders, i.e. orders which have been placed but not yet fulfilled. This list needs to be in time order, with the older, more urgent orders at the top.

The vendor needs to be able to click on an order in the list to display the details of that order, including the order number, customer’s given name, the items that were ordered, and how many minutes remain before a discount must be awarded.

Once an order is fulfilled (the snacks are prepared), the vendor needs to be able to click a button to mark this, and when the customer picks up the snacks, the vendor needs to be able to mark this too. Fulfilled orders need to be shows as such in the vendor’s order list, while picked-up orders should disappear from the list – though they are not deleted from the database, and should be easily findable again in case customers return to discuss their order. If the 20% discount for late fulfillment was applied, make sure you record this.

### Vendor App Instructions
#### Login
To test the vendor application in conjunction with the customer application, send customer orders to the Coffee 'n Chill van and utilise the following link
https://caffeine-addicts-vendor-webapp.herokuapp.com/vendor/login and login to access the vendor app:

email: coffeenchill@gmail.com <br />
password: coffeenchill123

or <br />

email: mochamood@gmail.com <br />
password: mochamood123


Successful login will load a homepage and navigation bar with additional features. Unsuccessful login display a message stating wrong username or password.

#### Open Van for Business
If the van is closed it will not appear on the map or list on the customer application. An option to write a message and describe location will be available on the vendor homepage when logged in. Once the "open for business" button is clicked, the van will open, it's location will be set to your current location and appear on the customer application. Ensure to "close van" before logging out to reset the van location to its default position for the next user.

#### Update Van Location and Message
If the van is open an option to "update message and location" is availble on the homepage. Submitting the new message and location will also set the van lovation to your current location.

#### Close Van
If the van is open an option to "close for business" will appear on the homepage. This option removes the van from the customer application and resets the set location to its default position to the University of Melbourne. 

#### Pending Orders
To view all pending orders follow the click on the "Pending Orders" tab on the navigation bar (/vendor/van/pendingOrders). Outstanding orders will display on the page with a timer denoting the remaining time to fulfil an order before it is discounted. If an order is marked as "ready for collection", an option to mark order as "collected" will be visible. Collected orders are sent to the Completed Orders page.

#### One Pending Order
To view the details of one pending order click the "View Details" button. This displays the contents of the order, details of the customer who placed it, and the time remaining to fulfil without incurring a discount. "Ready to Collect" marks the order as ready to be collected on the Pending Orders page and "Back to All Orders" returns to the Pending Orders Page. 

#### Completed Orders
The "Completed Orders" tab on the navigation bar (/vendor/van/completedOrders) displays all orders marked as "collected". Details of each completed order can be accessed through "View Details".

#### One Completed Order
This displays the details of the order including the order contents, customer information and the final price of the order.

#### Logout
"Logout" ends the users authenticated session and sends them back to the login. Ensure to close the van for business to ensure that the van location resets to its default position. 
