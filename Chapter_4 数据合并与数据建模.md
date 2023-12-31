# 数据合并与数据建模

数据混合就是在视图创建后附加另一个数据源的聚合查询，类似于 Excel 中两个数据透视表的匹配关联

数据关系也是默认包含聚合的查询，在构建数据源阶段实现，而数据混合在构建视图阶段实现。

## 并集、连接

并集：

* 方法：手动拖曳，通配符（*）匹配
* 查看：数据源页面编辑并集，工作表页面查看表名称的描述
* 异常处理：合并不匹配的字段

数据连接：

* 关系和连接的区别：
  * 关系：
    * 显示为逻辑表之间的灵活关系线
    * 需要您选择两个逻辑表之间的匹配字段
    * 不需要您选择联接类型
    * 使关联表中的所有行和列数据在数据源中可能可用
    * 在数据源中和分析期间保留每个表的详细级别
    * 在多个详细级别创建独立域。在数据源中，表不会合并在一起。
    * 在分析期间，根据正在使用的字段自动创建相应的联接。
    * 不会重复聚合值（当性能选项设置为“多对多”时）
    * 保留不匹配的度量值（当性能选项设置为“某些记录匹配”时）
  * 连接：
    * 在物理表之间显示时带有维恩图图标
    * 需要您选择联接类型和联接子句。
    * 联接的物理表将合并到具有固定数据组合的单个逻辑表中
    * 可能会删除不匹配的度量值
    * 如果字段处于不同的详细级别，则可能会导致聚合值重复
    * 支持需要单个数据表的方案，例如数据提取筛选器和聚合
* 并集和连接的区别
  * 相同点：生成一个完整、独立的数据源
  * 不同点：
    * 并集要优先于连接
    * 连接可以跨数据源，但是并集只能来自于同一数据源

## 数据混合

聚合层面的数据连接，又称为数据混合

1. 实现
   1. 主数据源建立聚合
   1. 建立辅助数据源
   1. 确认 / 编辑数据混合关系
   1. 跨数据源聚合查询

2. 数据混合的逻辑
   * 本质上是跨数据源的聚合查询
   * 数据混合相当于“左查询”
   * 数据混合生成的是随主视图变化和匹配字段调整而变化的、临时查询的数据表（逻辑表）
   * 优点：
     * 减少数据冗余，改善查询性能，对于大批量数据的表较为友好
     * 当两个数据源的表在不同级别时，较为适用
     * 可以保持两个数据源的独立性
     * 当跨数据源的连接中有不支持的特殊数据库类型时

## 数据关系

数据模型，就是基于数据分析的需求而建立的各种物理表的之间的相互关系，以逻辑表的关系代替物理表的连接。借助于数据关系，原来的数据连接面板就由单一的物理层，变成了逻辑层和物理层两层结构。

## 构建数据模型

# 数据合并与数据建模

数据混合就是在视图创建后附加另一个数据源的聚合查询，类似于 Excel 中两个数据透视表的匹配关联

数据关系也是默认包含聚合的查询，在构建数据源阶段实现，而数据混合在构建视图阶段实现。

## 并集、连接

并集：

* 方法：手动拖曳，通配符（*）匹配
* 查看：数据源页面编辑并集，工作表页面查看表名称的描述
* 异常处理：合并不匹配的字段

数据连接：

* 关系和连接的区别：
  * 关系：
    * 显示为逻辑表之间的灵活关系线
    * 需要您选择两个逻辑表之间的匹配字段
    * 不需要您选择联接类型
    * 使关联表中的所有行和列数据在数据源中可能可用
    * 在数据源中和分析期间保留每个表的详细级别
    * 在多个详细级别创建独立域。在数据源中，表不会合并在一起。
    * 在分析期间，根据正在使用的字段自动创建相应的联接。
    * 不会重复聚合值（当性能选项设置为“多对多”时）
    * 保留不匹配的度量值（当性能选项设置为“某些记录匹配”时）
  * 连接：
    * 在物理表之间显示时带有维恩图图标
    * 需要您选择联接类型和联接子句。
    * 联接的物理表将合并到具有固定数据组合的单个逻辑表中
    * 可能会删除不匹配的度量值
    * 如果字段处于不同的详细级别，则可能会导致聚合值重复
    * 支持需要单个数据表的方案，例如数据提取筛选器和聚合
* 并集和连接的区别
  * 相同点：生成一个完整、独立的数据源
  * 不同点：
    * 并集要优先于连接
    * 连接可以跨数据源，但是并集只能来自于同一数据源

## 数据混合

聚合层面的数据连接，又称为数据混合

1. 实现
   1. 主数据源建立聚合
   1. 建立辅助数据源
   1. 确认 / 编辑数据混合关系
   1. 跨数据源聚合查询

2. 数据混合的逻辑
   * 本质上是跨数据源的聚合查询
   * 数据混合相当于“左查询”
   * 数据混合生成的是随主视图变化和匹配字段调整而变化的、临时查询的数据表（逻辑表）
   * 优点：
     * 减少数据冗余，改善查询性能，对于大批量数据的表较为友好
     * 当两个数据源的表在不同级别时，较为适用
     * 可以保持两个数据源的独立性
     * 当跨数据源的连接中有不支持的特殊数据库类型时

## 数据关系

数据模型，就是基于数据分析的需求而建立的各种物理表的之间的相互关系，以逻辑表的关系代替物理表的连接。借助于数据关系，原来的数据连接面板就由单一的物理层，变成了逻辑层和物理层两层结构。

## 构建数据模型

数据关系不仅仅是在数据源阶段实现了数据的聚合匹配，更重要的是把并集、连接和混合的理念融合在一起，构建了稳定的数据模型。

Tableau 默认按照多对多的关系来查询，不过多对多的查询意味着消耗更新多的性能。

在数据关系是一对多时，在视图中进行分析 一 在 多 中的数据时（比如一个客户在订单明细中的订单量），会先将 多 聚合到基数为 一 的数据源层次。，再生成具体查询的过程。