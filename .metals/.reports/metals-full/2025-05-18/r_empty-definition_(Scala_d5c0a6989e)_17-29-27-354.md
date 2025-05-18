error id: file:///D:/Scala/scala.scala:`<none>`.
file:///D:/Scala/scala.scala
empty definition using pc, found symbol in pc: `<none>`.
semanticdb not found
empty definition using fallback
non-local guesses:

offset: 1668
uri: file:///D:/Scala/scala.scala
text:
```scala

import java.time.LocalDate
class Trial
{

    val order_components= List()
    val orders_List =List(order_components)
    // how i imagined it :
    // order_list = ( (apple,1)  ,  (cheese,2)  ,  (carrot,3)  )

    def append(orders_List: List[List[String]], newOrder:String,newOrder_quantity:String) :List[List[String]] =
    {
        // i want to append the new order to the orders_List
        val newOrderList = List(newOrder,newOrder_quantity)
        orders_List :+ newOrderList
    }
}

class Discount_Rules
{
    def expire_date(): Int =
    {
        val current_day = java.time.LocalDate.now().getDayOfMonth
        val expire_days = 30
        val days_remaining = expire_day - current_day
        if (days_remaining < 30)
        {
            return (30 - days_remaining)/100
        }
        else
        {
            0 //got zero discount 
        }
    }
    def cheese_wine(order: String): Double =
    {
        if (order == "cheese" )
        {
            return  0.1 
        }
        else if (order == "wine")
        {
            return 0.05
        }
        else
        {
            return  0.0
            
        }


    }
    def on_23rd_of_march(): Double =
    {
        val current_date = java.time.LocalDate.now()
        if (current_date.getDayOfMonth == 23 && current_date.getMonthValue == 3)
        {
            return 0.5
        }
        else
        {
            return 0.0
        }
        
    }
    def product_package(amount: String): Double =
    {

        val amt = amount.toInt
        if (amount > 15)
        {
            return  0.1@@5
        }
        else if (amount > 10)
        {
            return 0.1
        }
        else if (amount > 5)
        {
            return  0.05
        }
        else
        {
            return  0.0
        }
    }
    def through_app(app_flag:Boolean,amount: String): Double =
    {
        val amount = amount.toInt
        if (app_flag == true)
        {
            val rounded_amount =((amount-1)/5)+1
            return rounded_amount * 5/100

        }
        else
        {
            return 0.0
        }

    }
    def through_visa(visa_flag:Boolean): Double =
    {
        if (visa_flag == true)
        {
            return  0.05
        }
        else
        {
            return 0.0
        }
    }
}

//make sure to use vals only before suggesting
object Main
{

  val discount = new Discount_Rules()

  // Define rules as functions that accept order: List[String]
  val rules: List[(List[String]) => Double] = List(
    (_: List[String]) => discount.expire_date_(),
    order => discount.cheese_wine_(order.headOption.getOrElse("")),
    (_: List[String]) => discount.on_23rd_of_march_(),
    order => discount.product_package_(order.lift(1).getOrElse("0")),
    order => discount.through_app_(false, order.lift(1).getOrElse("0")),
    (_: List[String]) => discount.through_visa_(false)
  )


  def main(args: Array[String]): Unit =
    {
        val orders_List: List[List[String]] = List(
        List("cheese", "12"),
        List("wine", "3"),
        List("apple", "20")
        )

        val discountsPerOrder: List[Double] = orders_List.map 
        { order =>
        val discounts = rules.map(rule => rule(order)).filter(_ > 0)
        val topTwo = discounts.sorted(Ordering[Double].reverse).take(2)
        if (topTwo.isEmpty) 0.0 else topTwo.sum / topTwo.size

        }

        discountsPerOrder.foreach(d => println(f"Discount: $d%.2f"))
    }
}
```


#### Short summary: 

empty definition using pc, found symbol in pc: `<none>`.