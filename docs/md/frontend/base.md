# 必看基础信息

系统做了一些封装，先查看此文档会有效解决你的疑问

#后台控制器与JS的绑定

* 控制器中JS的目录对应为：`public/static/admin/js`
* 文件命名为: `小写+下划杠`
* `控制器`的每一个`方法`对应JS的`Controller`对象的一个`属性`
* 每一个JS文件都需要引入`admin`模块，并执行监听` ea.listen();`;

> 例子

* 控制器对应的PHP文件`app/admin/controller/mall/Cate.php`
* 控制器对应的JS文件`public/static/admin/js/mall/cate.js`
* 每一个控制里面的`方法`对应js里面的`属性`就会自动进行加载

```js
define(["jquery", "easy-admin"], function ($, ea) {

    var init = {
        table_elem: '#currentTable',
        table_render_id: 'currentTableRenderId',
        index_url: 'mall.cate/index',
        add_url: 'mall.cate/add',
        edit_url: 'mall.cate/edit',
        del_url: 'mall.cate/del',
        export_url: 'mall.cate/export',
        modify_url: 'mall.cate/modify',
    };

    var Controller = {

        index: function () {
            ea.table.render({
                init: init,
                modifyReload: true,
                cols: [[
                    {type: "checkbox"},
                    {field: 'id', width: 80, title: 'ID'},
                    {field: 'sort', width: 80, title: '排序', edit: 'text'},
                    {field: 'title', minWidth: 80, title: '分类名称'},
                    {field: 'image', minWidth: 80, title: '分类图片', search: false, templet: ea.table.image},
                    {field: 'remark', minWidth: 80, title: '备注信息'},
                    {field: 'status', title: '状态', width: 85, search: 'select', selectList: {0: '禁用', 1: '启用'}, filter: 'status', templet: ea.table.switch},
                    {field: 'create_time', minWidth: 80, title: '创建时间', search: 'range'},
                    {
                        width: 250,
                        title: '操作',
                        templet: ea.table.tool,
                        operat: ['edit', 'delete']
                    }
                ]],
            });

            ea.listen();
        },
        add: function () {
            ea.listen();
        },
        edit: function () {
            ea.listen();
        },
    };
    return Controller;
});
```

## `js` 相关字段详解

> 请结合 `layui` 官方文档查看 [https://layui.dev/docs/2/table](https://layui.dev/docs/2/table#options.cols)
>
> 更多案例可参考
>
> [goods.js](https://gitee.com/easyadmin8/EasyAdmin8/blob/main/public/static/admin/js/mall/goods.js)
>
> [log.js](https://gitee.com/easyadmin8/EasyAdmin8/blob/main/public/static/admin/js/system/log.js)

```js
toolbar:[{}]                     // 表格上方的工具按钮 可查看上方案例

cols: [{
    field: 'title',              // 字段
    title: '分类名称',            // 标题
    hide: false,                 // 是否在表格中隐藏该字段 默认 false 
    width: 80,                   // 长度
    minWidth: 80,                // 最小长度
    searchValue: '',             // 搜索中的默认值 
    search: true,                // 是否在搜索框内显示改字段搜索  true false  select=>下拉选择  range=>时间组件 xmSelect=>下拉多选
    searchOp: '=',               // php 中 where 的搜索条件 '='=>等于 '%*%'=>模糊查询(like) 'in'=>区间
    selectList: {},              // 当 search='select' 下拉选择的选项
    sort: true,                  // 是否支持排序
    edit: 'text',                // 是否可以直接在表格中修改
    filter: 'xxx',               // 设置 lay-filter 的属性值
    operat: [{}],                // 自定义扩展属性
    templet: function (d) {      // https://layui.dev/docs/2/table/#cols.templet
    },
}]
```