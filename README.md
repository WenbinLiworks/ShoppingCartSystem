# ShoppingCartSystem
# Attention : The Sourcecode was lost because of the Disk Cleanup without preparation.<br>And only developer document was left.
### A shoppingCart Management System, with the implementation of interaction between User Interface and Adventureworks2012

### The basic operations on Database(add system admins)
You can grant permission to log in to operate the database in the following ways:
(1) Add login to the server role. For example, by adding a login to the sysadmin server role, the login has full operational rights to all databases.
(2) Map the login to a user of a database, and add the mapped user to the database role with corresponding operation permission.
(3) Mapping a login to a user of a database, granting that user the right to operate on certain database objects.
<br>Among them, method 1 and method 2 are implicit authorization operations, sometimes these methods will grant too many permissions to login. Method 3 is a more detailed authorization operation.

### The final User Interface is as follows:
![userInterface](https://cl.ly/83b6d61af0b6/%255B50f6cb36104351a4de972db0649a0e2c%255D_Image%2525202020-01-16%252520at%2525201.21.06%252520AM.png)
### ShoppingCart Section : Control Plugins and Main window
![](https://cl.ly/884bf3f242e3/Image%2525202020-01-16%252520at%2525201.33.19%252520AM.png)
### ShoppingCart Section : Storing procedure implemented in Sql Query
![](https://cl.ly/7555d15f6cea/Image%2525202020-01-16%252520at%2525201.34.05%252520AM.png)
### Storing procedures for Transaction calling, experimented with Visual Studio Community 2017
![](https://cl.ly/84e354607730/Image%2525202020-01-16%252520at%2525201.39.35%252520AM.png)

#### The details of ProductInventory was similar

## Overview:
 #### In the upper part of the window, input the information of the goods to be put into the shopping cart, and the lower part displays the list of the goods in the current shopping cart (the warehouse inventory list has been added in the experiment). 
 
The "add" button adds the new goods to the shopping cart, and the new goods are displayed in the shopping cart list. The warehouse list refreshes the inventory of the new goods in the shopping cart in real time;
<br><br>"Delete" button will delete the goods in the current line in the shopping cart list from the shopping cart, and the warehouse list will update the line of the corresponding goods.
<br>Update the shopping cart table Sales.ShoppingCartItem and inventory table Production. ProductInventory in the database when Adding and Deleting operations.

<br>The number of items added to the cart is reflected in the inventory, that is, the inventory minus the number of items in the cart. <br>The stored procedure is used to update the two tables and encapsulate the operations in one transaction. <br><br> test the success and failure status of each operation.
