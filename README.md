# SQL-Database-Queries-For-Pizzeria
Created entire database from scratch for a local pizzeria. Generated data, created a barker-notation model, created the database using phpmyadmin, then answered important managerial questions through SQL queries. Lastly, presented all the information with answers to the queries which will help the business sustain and grow itself. Presentation component was ranked the highest in the class with 97% grade. 


Sample SQL Managerial Question:

What is the sum total of meaningful orders coming in from each service method and on average how much discount is being offered for each?

Rationale:
Is SkipTheDishes providing enough of a benefit to CC Pizza with regards to revenue generation and how much discount is necessary for each delivery method. 

Query:
SELECT customer_order.Service_method, 
(SUM(customer_order.Total_order_amount)) AS "Total Meaningful Order Amount ($)", 
(AVG(customer_order.Discount)) AS "AVG Discount ($)"
from customer_order 
WHERE customer_order.Total_order_amount>=20 
GROUP BY customer_order.Service_method
ORDER by (SUM(customer_order.Total_order_amount)) DESC;

Question 1 results:
![image](https://user-images.githubusercontent.com/71670899/116816714-13457b80-ab31-11eb-9a0d-62fb8c11836a.png)


Explanation:
This query serves to identify the number of meaningful orders that are coming in from each service method. The reason why the meaningful threshold is above $20 is because CC wants to make sure customers are buying pizza (typically $20+) and not just other small items (drinks, snacks) from these service methods. CC also included discounts in the query to see what the average amount being discounted was for each service method. The greater the discount, the greater the potential promotional cost to convert customers. With these results, CC understood that not only is SkipTheDishes bringing in a significantly large number of meaningful orders, but it also has a lower corresponding average discount compared to the in-house delivery service. 

The reason for this may be because SkipTheDishes is an established channel with many customers often relying on it for convenience rather than discounts. All in all, with ~$10,000 more of meaningful orders coming from SkipTheDishes compared to in-house delivery service, this new service method seems to be a great addition to CC’s pizzeria and should most likely be maintained for the future. However, to make a more conclusive decision, the service fee and costs must also be analyzed for SkipTheDishes.
