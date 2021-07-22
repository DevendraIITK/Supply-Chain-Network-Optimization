# Supply-Chain-Network-Optimization
Network Explanation:
In this project we have a supply chain network for which we have to minimize the total cost to fulfill the customer demand. In this network we have 5 suppliers who provide 4 type of raw material to 3 factories to produce 4 type of product. These 3 factories fulfill the demand of 4 customers for 4 types of product.
Here we will minimize the cost assuming the all 3 factories comes under one owner. The solution of this problem gives raw material to be ordered from supplier and the final products to be delivered to customers from a factory. 
Data Given:
1.	We have data of supplier stock available for different raw material. The data is in units of raw material.
	Material A	Material B	Material C	Material D
Supplier A	20	20	0	0
Supplier B	25	50	0	0
Supplier C	0	10	70	40
Supplier D	0	0	20	50
Supplier E	30	0	0	40
2.	  We have per unit cost of raw material from different supplier. 
	Material A	Material B	Material C	Material D
Supplier A	20	80		
Supplier B	25	75		
Supplier C		60	210	70
Supplier D			190	50
Supplier E	15			60
3.	We have per unit raw material shipping cost from particular supplier to particular factory.
	Factory A	Factory B	Factory C
Supplier A	20	40	200
Supplier B	60	20	190
Supplier C	300	40	80
Supplier D	20	40	150
Supplier E	200	50	70




4.	 We have data of no of units of raw materials required to produce a product.
	Material A	Material B	Material C	Material D
Product A	5	3		
Product B			2	5
Product C		7	9	
Product D	3	2	4	15
5.	 We have production capacity of different factories for different products.
	Factory A	Factory B	Factory C
Product A	6	2	7
Product B	4	8	
Product C		6	
Product D	3		10
6.	Cost of producing one unit of a product in a factory is given in below table. Cost is in $/unit.
	Factory A	Factory B	Factory C
Product A	140	130	150
Product B	80	90	
Product C		20	
Product D	30		25
7.	Demand of a customer for a product is given in below table.
	Customer A	Customer B	Customer C	Customer D
Product A	7	3		
Product B			2	
Product C				4
Product D	1		3	4
8.	We have per unit shipping cost of final product from a factory to a customer.
	Customer A	Customer B	Customer C	Customer D
Factory A	50	70	30	10
Factory B	90	20	40	15
Factory C	10	80	100	150




Assumptions:
This problem is the mimic of actual supply chain network optimization problem in which we have to minimize total cost in fulfilling customer demand. Because of this reason the data set is small and following assumptions are there:
•	We assume that demand and stock is given in per week.
•	Here we are not taking into consideration of lead time. We assumed that whatever raw material factories order is delivered instantaneously, similarly final product is also delivered in no time.
•	Not considered the time taken to manufacture the product, assumed zero.
•	Assumed that all raw material and final product are of same size that is why considering transportation cost per unit same  for any product or raw material.
Solution methodology and model formulation:
To solve this optimization problem we minimize total cost which consists of raw material purchasing cost, transportation cost of raw material, production cost, and transportation cost of final product. We use ortools for solving this problem.
Model formulation:
Decision variables:
Oijk : no of units of ordered to supplied I of material j by factory k.
Dijk : no of units delivered from factory I of product j to customer k.
Pij : no of units produced by factory I of product j.
Constants:
Sij : stock of supplier I for material j (in units).
RCij : raw material cost of material j possessed by supplier i.
SCRij : cost of shipping raw material from supplier I to factory j (in $/unit).
PRij : no of units of material j required to produce one unit of product i.
PCPij : production capacity of factory j for product i.
PCij : production cost of product I by factory j (in $/unit).
DEij : demand of product I by customer j.
SCPij : cost of shipping product from factory I to customer j (in $/unit).
Objective function:


Constraints:
1.	 This constraint tells relation between Pij and Dijk variables. Total production from factory I of product j that is Pij must be more than or equal to sum of product j delivered from factory I to all customers that is sum(Dijk over k).

Result:
On solving this problem in python we got optimal solution. Demand of all the customers is fulfilled. Total cost to all factories is $49315. Cost breakup for all factories is as follows:
	Cost(in $)	Units Delivered
Factory A	12785	10
Factory B	14260	7
Factory C	22270	7
From above table owner can know that factory A need minimum money to operate and also fulfill more customers demand.
Value of other parameters like how much units of raw material ordered, how much units of a product sent to a customer, are printed in code itself.  
Scope of amendment in model:
Here our main target is the demand of customer should be fulfilled but if this is not the case we can have a model in which we cannot send customer more than his demand but can send lesser units and our objective will be to maximize the total profit by selling those units.
