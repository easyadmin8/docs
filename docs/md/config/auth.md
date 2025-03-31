# 权限忽略配置

### 登录判断和权限验证忽略配置

``` 
// 可以对整个控制器设置 不需要登录验证
protected bool $ignoreLogin = true;
```

```
/// 对控制器中某个方法设置 绕过中间件登录判断 即不需要登录验证
#[MiddlewareAnnotation(ignore: MiddlewareAnnotation::IGNORE_LOGIN)]
```

```
// 对控制器中某个方法设置 表示节点名称和需要权限验证
#[NodeAnnotation(title: '列表', auth: true)]

```

> 登录和权限验证均在中间件中执行