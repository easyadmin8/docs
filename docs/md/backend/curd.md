# Curd trait引入

后台使用Curd trait, 能大大提高开发效率以及代码的可复用性, 文件位置：`app/admin/traits/Curd.php`

> 默认的CURD方法有：

| 参数      | 说明   |
|---------|------|
| index   | 列表   |
| add     | 添加   |
| edit    | 编辑   |
| delete  | 删除   |
| export  | 导出   |
| modify  | 属性修改 |
| recycle | 回收站  |

# 使用方法

* 只要继承基类 `AdminController` 便会自动引入 `Curd` 中的所有方法

# 覆盖方法修改

> 如果默认的`Curd`不适用你的需求，请复制 `traits/Curd.php` 对应的方法到你的控制器下进行覆盖修改。

# 重写 `index()` 示例

> 在控制器中复制 `curd` 中的 `index` 方法到现有控制器中（不同 `EasyAdmin8` 版本可能略有差异）

```php
    #[NodeAnnotation(title: '列表', auth: true)]
    public function index(Request $request): Json|string
    {
        if ($request->isAjax()) {
            if (input('selectFields')) {
                return $this->selectList();
            }
            list($page, $limit, $where) = $this->buildTableParams();
            $count = self::$model::where($where)->count();
            $list  = self::$model::withoutField('password')
                ->where($where)
                ->page($page, $limit)
                ->order($this->sort)
                ->select()->toArray();
            $data  = [
                'code'  => 0,
                'msg'   => '',
                'count' => $count,
                'data'  => $list,
            ];
            return json($data);
        }
        return $this->fetch();
    }
```



