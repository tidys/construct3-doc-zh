plugin.js是插件中比较重要的配置

# 插件常量

```
const PLUGIN_ID = "MyCompany_MyAddon";
const PLUGIN_VERSION = "1.0.0.0";
const PLUGIN_CATEGORY = "general";
```

## PLUGIN_ID
插件的唯一标识，必须和`addon.json`中的值相同，请尽量避免反复修改

## PLUGIN_VERSION
插件版本号，必须和`addon.json`中的值相同

## PLUGIN_CATEGORY
插件的类别，当创建一个新的对象类型时，会显示
可选的值为：
- data-and-storage
- form-controls
- general
- input 
- media 
- monetisation
- platform-specific
- web
- other

## 插件的主类
```
class MyCustomPlugin extends SDK.IPluginBase {
    constructor () {
        super(PLUGIN_ID);
        this._info.setName("hello plugin");
    }
}
SDK.Plugins.MyCompany_MyAddon = MyCustomPlugin;
const PLUGIN_CLASS = MyCustomPlugin;

```

同样的，你需要在`type.js`、 `instance.js`中，同步更新以下内容：

在构造函数中，插件的配置是通过`this._info`设置的，这是一个[IPluginInfo]()的接口


当选中插件实例时，插件属性会出现在属性栏，你需要这样设置属性：
```
this._info.SetProperties([
	new SDK.PluginProperty("integer", "test-property", 0)
]);
```
