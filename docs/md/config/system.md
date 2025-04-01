# 系统配置

### env配置说明

> 后台模块配置说明`EASYADMIN`

| 参数                | 说明          | 类型     | 默认               | 
|-------------------|-------------|--------|------------------|
| ADMIN             | 后台路径        | string | admin            |
| CAPTCHA           | 后台验证码开关     | bool   | true             |
| IS_DEMO           | 是否为演示环境     | bool   | false            |
| STATIC_PATH       | 静态资源路径      | bool   | /static          |
| OSS_STATIC_PREFIX | OSS静态文件路径前缀 | bool   | static_easyadmin |

> 配置示例

``` dotenv
APP_DEBUG=true

# 后台系统日志开关
APP_ADMIN_SYSTEM_LOG=true

DEFAULT_TIMEZONE=Asia/Shanghai

DB_TYPE=mysql
DB_HOST=127.0.0.1
DB_NAME=easyadmin8
DB_USER=root
DB_PASS=root
DB_PORT=3306
DB_CHARSET=utf8mb4
DB_PREFIX=ea8_

# 限流器开关 如果为true 需要服务器支持redis
RATE_LIMITING_STATUS=false

# Redis配置
REDIS_HOST=127.0.0.1
REDIS_PORT=6379
REDIS_PASSWORD=
REDIS_PREFIX=
REDIS_DATABASE=0

# 后台配置项组
[EASYADMIN]

# 后台地址后缀名称
ADMIN=admin

# 后台登录验证码开关
CAPTCHA=false

# 是否为演示环境
IS_DEMO=false

# CDN配置项组
CDN=
EXAMPLE=true

# 是否开启CSRF过滤 
IS_CSRF=false

# 静态文件路径前缀
STATIC_PATH=/static

# OSS静态文件路径前缀
OSS_STATIC_PREFIX=static_easyadmin
```

# 超管配置

> 超管不受权限控制，默认获取所有权限

###超管账号配置

配置文件位置：`app/common/constants/AdminConstant.php`

```php
<?php

namespace app\common\constants;

/**
 * 管理员常量
 * Class AdminConstant
 * @package app\common\constants
 */
class AdminConstant
{

    /**
     * 超级管理员，不受权限控制
     */
    const SUPER_ADMIN_ID = 1;

}
```

* 修改常量：SUPER_ADMIN_ID `管理员对应ID`