# ShoppingCartSystem
 A shoppingCart Management System, with the implementation of interaction between User Interface and Adventureworks2012


### 实验内容:
 窗口的上方输入将要放入购物车的货品的信息，下方显示当前购物 车的货品的列表(实验中增加了仓库库存列表)。“Add” 按钮将新的货 品添加到购物车中，购物车列表中显示新增的货品，仓库列表实时 刷新购物车新增商品后对应商品的库存; <br>“Delete” 按钮将购物车列 表中当前行的货品从购物车中删除, 仓库列表更新相应商品所在行。
<br>添加与删除操作时更新数据库中的购物车表 Sales.ShoppingCartItem 和库存表 Production.ProductInventory。购 物车中增加货品的数量反映在库存中，即库存中减去购物车的货品 数。
<br> 使用存储过程完成两个表的更新操作，并将操作封装在一个事务中。 ➢ 测试每个操作的成功与失败状态。