**Scala Discount Calculator**
This Scala project demonstrates a simple discount calculation system for a list of orders. It applies multiple discount rules to each order and calculates the final price after discounts.


**Features**
* Represents orders as a list of product-quantity pairs (e.g., List("cheese", "12"))

* Defines various discount rules including:

  * Expiration date discount

  * Cheese and wine product discounts

  * Special discount on 23rd March

  * Discounts based on quantity purchased

  * Discounts for app usage and Visa payment (currently hardcoded as false)

* Applies all discount rules and calculates the average of the top two discounts per order

* Calculates and prints:

  * Total price before discount

  * Discount percentage applied

  * Final price after discount

Outputs a grand total for all orders combined


**How It Works**

1- Orders are represented as lists of strings with product name and quantity.

2- Discount rules are functions that take an order and return a discount as a decimal (e.g., 0.10 for 10%).

3- The system calculates all applicable discounts for each order, selects the top two highest discounts, averages them, and applies this average discount to the total price.

4- The program outputs detailed pricing information for each order and the grand total.


**How to Run**

1- Save the Scala code in a file, for example, ScalaDiscount.scala.

2- Compile the code using scalac ScalaDiscount.scala.

3- Run the program using scala Main.


**Code Structure**

Trial: Helper class to manage orders.

Discount_Rules: Contains all discount calculation methods.

Main: Entry point with predefined orders, prices, discount rules, and the main logic for calculating and printing results.
