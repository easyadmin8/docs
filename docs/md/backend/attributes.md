# 控制器属性

后台`所有`控制器都应该需要去继承该基类`common/controller/AdminController.php`
> 基类`AdminController`会复用 `Curd` 自动生成
>
> `index` `add` `edit` `delete` `export` `modify` 六个方法
> 查看[Curd相关介绍](md/backend/controller/curd)
>
> 可以在现有控制器中自己覆盖重写

> 目前系统内部默认的属性有：

| 参数                | 说明       | 类型    | 默认                                                            |
|-------------------|----------|-------|---------------------------------------------------------------|
| model             | 当前模型对象   | model | null                                                          |
| sort              | 列表排序规则   | array | ['id' => 'desc']                                              |
| allowModifyFields | 允许修改的字段  | array | ['status', 'sort', 'remark', 'is_delete', 'is_auth', 'title'] |
| noExportFields    | 不导出的字段信息 | array | ['delete_time', 'update_time']                                |
| selectWhere       | 下拉选择条件   | array | []                                                            |