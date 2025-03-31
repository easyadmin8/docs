# 富文本编辑器初始化

* 系统默认内置了 `ueditor` `ckeditor4` `wandEditor` `easyMDE` 编辑器, 推荐使用 `wandEditor`
* 在`class`引入`editor`样式即可完成初始化操作。
* 可以使用`rows`来控制编辑器的高度。

> 代码示例

```html

<div class="layui-col-xl7 layui-col-lg7 layui-col-md12 layui-col-sm12 layui-col-xs12">
    <div class="layui-form-item layui-form-text">
        <label class="layui-form-label">商品描述</label>
        <div class="layui-input-block">
            {:editor_textarea('','describe')}
        </div>
    </div>
</div>
```

