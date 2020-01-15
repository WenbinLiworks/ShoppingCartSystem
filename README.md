# ShoppingCartSystem
# Attention : The Sourcecode was lost because of the Disk Cleanup without preparation.<br>And only developer document was left.
### A shoppingCart Management System, with the implementation of interaction between User Interface and Adventureworks2012

### The final User Interface is as follows:
![userInterface](https://cl.ly/83b6d61af0b6/%255B50f6cb36104351a4de972db0649a0e2c%255D_Image%2525202020-01-16%252520at%2525201.21.06%252520AM.png)


## 实验内容:
 #### In the upper part of the window, input the information of the goods to be put into the shopping cart, and the lower part displays the list of the goods in the current shopping cart (the warehouse inventory list has been added in the experiment). 
 
The "add" button adds the new goods to the shopping cart, and the new goods are displayed in the shopping cart list. The warehouse list refreshes the inventory of the new goods in the shopping cart in real time;
<br><br>"Delete" button will delete the goods in the current line in the shopping cart list from the shopping cart, and the warehouse list will update the line of the corresponding goods.
<br>Update the shopping cart table Sales.ShoppingCartItem and inventory table Production. ProductInventory in the database when Adding and Deleting operations.

<br>The number of items added to the cart is reflected in the inventory, that is, the inventory minus the number of items in the cart. <br>The stored procedure is used to update the two tables and encapsulate the operations in one transaction. <br><br> test the success and failure status of each operation.
