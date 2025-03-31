# 表名规范

> 好的表命名规范会让你开发起来更加心情开朗，下面是一些建议：

### 命名规则 `前缀 + 模块名 + 表标识`

* 例如`系统`模块：
    * ea8_system_admin
    * ea8_system_config
* 例如`博客`模块：
    * ea8_blog_user
    * ea8_blog_config

#字段规范

* 字段名使用 `下划线风格`
* 字段一定要清晰, 尽量 `避免使用缩写` 命名
* 字段类型要符合使用场景、长度设置合理
* 设置索引优化检索
* `create_time`、`update_time`、`delete_time` 三个字段以 `int|datetime` 类型保存时间信息