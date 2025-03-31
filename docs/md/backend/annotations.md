# 注解权限

> 注解权限只能获取后台的控制器，也就是该`app/admin/controller`下

# 控制器注解权限

> 控制器类注解 `#[ControllerAnnotation(title: '商城商品管理')]`

* 注解类： `service/annotation/ControllerAnnotation`
* 作用范围： `整个控制器`
* 参数说明：
    * `title` 控制器的名称（必填）
    * `auth` 是否开启权限控制，默认为true （选填，Enum:`{true, false}`）

### 示例

> 备注：注解前请先引用`use app\admin\service\annotation\ControllerAnnotation;`

```php
<?php

namespace app\admin\controller\mall;

use app\admin\model\MallCate;
use app\common\controller\AdminController;
use app\admin\service\annotation\ControllerAnnotation;
use app\admin\service\annotation\NodeAnnotation;
use think\App;

#[ControllerAnnotation(title: '商品分类管理')]
class Cate extends AdminController
{

    public function __construct(App $app)
    {
        parent::__construct($app);
        self::$model = MallCate::class;
    }

}
```

# 方法节点注解权限

> 方法节点类注解tag `#[NodeAnnotation(title: '商城商品管理')]`

* 注解类： `service/annotation/NodeAnnotation`
* 作用范围： `控制器中的某个方法`
* 参数说明：
    * `title` 方法节点的名称（必填）
    * `auth` 是否开启权限控制，默认为true （选填，Enum:`{true, false}`）

### 示例

> 备注：注解前请先引用`use app\admin\service\annotation\NodeAnnotation;`

```php
<?php

namespace app\admin\controller\mall;

use app\admin\model\MallCate;
use app\common\controller\AdminController;
use app\admin\service\annotation\ControllerAnnotation;
use app\admin\service\annotation\NodeAnnotation;
use think\App;

#[ControllerAnnotation(title: '商品分类管理')]
class Cate extends AdminController
{

    public function __construct(App $app)
    {
        parent::__construct($app);
        self::$model = MallCate::class;
    }
    
    #[NodeAnnotation(title: '列表', auth: true)]
    public function index(Request $request): Json|string
    {
      // ...
    }
}
```

# 更新权限节点

* 菜单 - 系统管理 - 节点管理 - 更新节点