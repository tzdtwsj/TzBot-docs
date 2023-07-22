# 插件API
> 注意：本API所有实现都在命名空间`tzdtwsj\TzBot`里，当需要调用时需要在调用前使用`use tzdtwsj\TzBot;`代码进行引用该命名空间，或者调用这些函数时在函数名前面加上`\tzdtwsj\TzBot\`，例如`\tzdtwsj\TzBot\RegisterPlugin(...)`
---
# 注册插件
函数原型：  
`RegisterPlugin( string $name, string $description, array $version=array(1,0,0), array $order_description=array() )`  
$name：string  
插件的名字  
$description：string  
插件的介绍  
$version：array( int , int , int )  
插件的版本（可选），如果不传入版本，那么版本将会默认设为1,0,0  
$order\_description：array()  
插件的其他信息（可选），关联数组，可传入项目地址，插件作者等，例如 array("author"=>"作者")  
返回值：成功时返回true，失败时抛出异常  
# 注册一个命令
函数原型：  
`RegisterCmd( string $command, string $usage, callable $func, bool $can_get_for_help=true, int $permission=0, bool $must_at=false, bool $group=true, bool $private=true )`  
$command：string  
命令的触发名  
$usage：string  
命令的用法  
$func：callable  
命令的具体实现，下文会提到此参数  
$can\_get\_for\_help：bool  
[可选]命令是否显示在"帮助"列表里，默认为true，也就是能  
$permission：int  
[可选]命令的执行权限，默认为0，说明所有用户均可触发   
$must\_at：bool  
[可选]必须要at才能触发命令，默认为false，当私聊时本选项无效  
$group：bool  
[可选]命令是否能在群聊被使用，默认为true  
$private：bool  
[可选]命令是否能在私聊被使用，默认为true
> 注意：$group和$private不能同时为false，否则会抛出异常

返回值：注册成功会返回true，失败时抛出异常

命令具体实现：function($mp){}
在运行时会传入$mp，此变量的数据类型是[MessageParam](/PluginsDocs/var.md#messageparam-%e4%bf%a1%e6%81%af%e6%95%b0%e6%8d%ae%e7%b1%bb%e5%9e%8b)  

此API的示例用法：  
```php
use tzdtwsj\TzBot;
RegisterCmd("测试", "测试插件", function($mp){
    SendMsg($mp,"这是测试消息\n机器人QQ号：".$mp['mydata']['user_id']."\n触发此命令的QQ号：".$mp['user_id'],true,false);
}, true, -1, false, true, true );
```
