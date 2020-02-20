# ShoppingCartSystem
# Attention : The Sourcecode was lost because of the Disk Cleanup without preparation.<br>And only developer document was left.
### A shoppingCart Management System, with the implementation of interaction between User Interface and Adventureworks2012

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

### Some related coding about Transaction
```
BEGIN TRAN TRAN_MONEY --开始事务

DECLARE @TRAN_ERROR INT;
SET @TRAN_ERROR=0;
BEGIN TRY
    UPDATE ACCOUNT SET AMOUNT=AMOUNT-520 WHERE NAME='xxx'
     SET @tran_error = @tran_error + @@ERROR;
    UPDATE ACCOUNT SET AMOUNT=AMOUNT+520 WHERE NAME='yyy'
     SET @tran_error = @tran_error + @@ERROR;
END TRY
BEGIN CATCH
    PRINT '出现异常，异常编号：'+CONVERT(VARCHAR,ERROR_NUMBER())+
          '异常消息:'+ERROR_MESSAGE();
          SET @TRAN_ERROR+=1;
END CATCH
IF(@TRAN_ERROR>0)
BEGIN
  --有异常 回滚事务；
  ROLLBACK TRAN;
  PRINT '转账失败，取消交易';
END
ELSE
BEGIN
  --没有异常，提交事务
   COMMIT TRAN;
   PRINT '转账成功!'
END
```
To avoid SQL INJECTION
```
 string constr = "Data Source=zxtiger;Initial Catalog=itcastcn;Integrated Security=True";
            using (SqlConnection con = new SqlConnection(constr))
            {
            /*
            Add arguments 
            */
                string sql = "select count(*) from UserLogin where LoginId=@uid and LoginPwd=@pwd";
                using (SqlCommand cmd = new SqlCommand(sql, con))
                {
                    ////在执行之前告诉Command对象@uid与@pwd将来用谁来代替
                    ////为变量@uid与@pwd赋值
                    //cmd.Parameters.AddWithValue("@uid", txtUid.Text.Trim());
                    //cmd.Parameters.AddWithValue("@pwd", txtPwd.Text);
                    #region MyRegion
                    //SqlParameter p1 = new SqlParameter("@uid", txtUid.Text.Trim());
                    //cmd.Parameters.Add(p1);

                    //SqlParameter p2 = new SqlParameter("@pwd", txtPwd.Text);
                    //cmd.Parameters.Add(p2);
                    #endregion

                    
                    SqlParameter[] pms = new SqlParameter[] { 
                    new SqlParameter("@uid", txtUid.Text.Trim()),
                    new SqlParameter("@pwd", txtPwd.Text)
                    };
                    cmd.Parameters.AddRange(pms);


```
