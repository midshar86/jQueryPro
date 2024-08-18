# `jQuery`学习

## 选择器

- 使用`jQuery`选择器选择出来的返回值是一个伪数组

### 基本选择器

- 基本选择器使用`$("CSSSelector")`进行选择,可以实现与`CSS`选择器一致的效果

### 特殊选择器

- 特殊选择器是`jQuery`提供的特有选择器
- `$("div:first")`选择首个`div`元素
- `$("div:last")`选择末尾的`div`元素
- `$("div:eq(index)")`选择下标是第`index`的`div`元素,下标从`0`开始
- `$("div:odd")`选择下标是奇数的元素
- `$("div:even")`选择下表是偶数的元素

### 二次筛选方法

- 兄弟节点
  - `$("div").first()`选择匹配的`div`元素中的第一个
  - `$("div").last()`选择匹配的`div`元素中的最后一个
  - `$("div").eq(index)`选择匹配的`div`元素中指定`index`索引的元素
  - `$("div").next()`选择匹配的`div`元素的下一个相邻元素
  - `$("div").nextAll(argus)`选择匹配的`div`元素之后的所有兄弟元素,如果传递参数,表示还会按照该参数进行筛选
  - `$("div").nextUntil(argus)`选择匹配的`div`元素之后的所有元素直到给定条件的元素(不包含)为止,如果不给定条件,等同于`.nextAll()`方法
  - `$("div").prev()`选择匹配的`div`元素的上一个相邻元素
  - `$("div").prevAll(argus)`选择匹配的`div`元素之前的所有兄弟元素,如果传递参数,表示还会按照该参数进行筛选
  - `$("div").prevUntil(argus)`选择匹配的`div`元素之前的所有元素直到给定条件的元素(不包含)为止,如果不给顶条件,等同于`.prevAll()`方法
  - `$("div").siblings()`选择除自身意外的所有兄弟节点
- 父节点
  - `$("div").parent()`选择`div`元素的父节点
  - `$("div").parents()`选择`div`元素的所有父节点
- 子节点
  - `$("div").children()`选择`div`元素的所有子代节点
  - `$("div").find()`深度选择`div`元素的所有符合条件的后代节点
- 同级索引
  - `$("div").index()`输出当前`div`元素在同级别元素中的索引

## 操作样式

- `$("div").css(attrs)`获取`div`元素`CSS`样式中的`attrs`属性,该方法能够获取内联样式,内部样式表与外部样式表的属性值
- `$("div").css(attrs,value)`为`div`元素设置`attrs`属性,值为`value`,当设置长度单位时,默认为`px`
- `$("div").css({attrs:value})`为`div`元素一次性设置多个`attrs`并且赋值

## 操作类属性

- `$("div").addClass(name)`为当前元素添加`class`属性`name`
- `$("div").removeClass(name)`为当前元素移除`class`属性`name`
- `$("div").hasClass(name)`判断当前元素是否存在`class`属性`name`
- `$("div").toggleClass(name)`切换当前元素的`class`属性`name`

## 操作`Dom`内容

- `$("div").html(content)`以`html`形式获取当前`div`元素的内容,如果设置了参数`content`,代表为当前`div`元素设置内容
- `$("div").text(content)`以纯文本形式获取当前`div`元素的内容,如果设置了参数`content`,代表为当前`div`元素设置内容
- `$("input").val(content)`获取当前输入框中的输入值,如果设置了`content`,那么该输入框的默认值将是`content`

## 操作`Dom`属性

- `attr`
  - `attr`可以操作原生属性,也可以操作用户自定义的属性
  - 通常地,使用`attr`操作`Dom`节点地自定义属性
  - `$("div").attr(name,value)`设置当前`div`元素的`name`属性为`value`值,如果不输入`value`参数,表示获取当前`div`元素的`name`属性,可以操作自定义属性
  - `$("div").removeAttr(name)`移除当前`div`元素的`name`属性,可以操作自定义属性
- `prop`
  - `prop`只能够操作`Dom`节点的原生属性,它无法移除属性
  - `$("div").prop(name,value)`设置当前`div`元素的`name`属性为`value`值,如果不输入`value`参数,表示获取当前`div`元素的`name`属性,无法操作自定义属性
  - 如果确实使用`$("div").prop(customedName,value)`操作了自定义属性,并且设置了`value`值,那么会将该属性挂载到`Dom`对象中,通过`Dom`对象能够访问;同时可以使用`$("div").removeProp(customedName)`在`Dom`对象中移除

## 操作`Dom`元素偏移量

- `offset`
  - 使用`offset`方法获取或设置元素距离文档流左上角的偏移量(无论元素是否有定位属性)
  - `$("div").offset()`获取一个对象,包含元素距离文档流左上角的偏移量
  - `$("div").offset({left:num,top:num})`设置元素距离文档流左上角的偏移量
- `position`
  - 使用`position`方法获取元素距离最近的有定位元素的偏移量
  - `$("div").position()`返回一个对象,包含元素距离最近有定位元素的偏移量
  - 不能够设置偏移量

## 获取`Dom`元素尺寸

- `$("div").width()`,`$("div").height()`获取元素内容区的宽度与高度
- `$("div").innerWidth()`,`$("div").innerHeight()`获取元素内容区与内边距的宽度与高度
- `$("div").outerWidth()`,`$("div").outerHeight()`获取元素内容区,内边距与边框的宽度与高度,当传递参数为`true`时,会获取元素内容区,内边距,边框与外边距的宽度与高度

## 事件绑定

- `$("div").on(evtName,function)`最简单的事件绑定方法,为`div`元素绑定`evtName`事件,并且传入一个事件处理函数
- `$("div").on(evtName,tagName,function)`利用事件委托机制为`div`元素绑定`evtName`事件,第二个参数表示触发事件的标签
- `$("div").on(evtName,params,function(e))`为`div`元素绑定`evtName`事件的同时向事件处理函数中传递参数`params`,`params`==必须以对象形式传递==,在事件处理函数中可以获取到传递的参数
- `$("div").on(evtName,tagName,params,function(e))`使用事件委托机制为`div`元素绑定事件,`tagName`是指定的触发事件的源标签名,`params`是传递的参数,可以是字符串与对象
- `$("div").one()`为当前`div`元素添加一次性事件,参数与上述一致
- `$("div").click(params,function(e))`支持直接使用常见事件名(`mouseenter`,`mouseover`,`mousemove`等)为元素绑定事件,`params`可以作为参数传递给事件处理函数
- `$("div").off(evtName,handlerFun)`解绑当前`div`元素的`evtName`事件绑定的`handlerFun`事件处理函数,如果不传递参数,表示解绑`div`元素上的所有事件

## 设置动画

- 基本动画
  - `$("div").show/hide/toggle(keppTime,type,callback)`为元素添加一个显示/隐藏/切换动画,默认从左上角显示与隐藏
    - `keepTime`以`ms`为单位,表示动画持续的时长
    - `type`可选值`swing`,`linear`,表示动画的显示效果
    - `callback`是一个回调函数,当动画结束之后调用
  - `$("div").slideDown/slideUp/sildeToggle(keepTime,type,callback)`为元素添加一个显示/隐藏/切换动画,默认在垂直方向上显示与隐藏
  - `$("div").fadeIn/fadeOut/fadeToggle(keepTime,type,callback)`为元素添加一个渐隐渐出的动画
  - `$("div").fadeTo(keepTime,target,type,callback)`为元素添加一个渐隐渐出的动画
    - `target`参数表示希望设置的透明度目标`(0~1)`
- 综合动画
  - `$("div").animate(target,keepTime,type,callback)`为元素添加一个综合动画
    - `target`是一个对象,用来设置目标属性
      - 不支持本身无法实现动画的属性
      - 不支持背景色
      - 不支持`CSS3`中`transform`的动画
  - `$("div").stop()`停止当前动画,通常在执行动画之前调用
  - `$("div").finish()`跳过动画直接到达目标状态

## 操作节点

- 创建`Dom`元素
  - `$("<tagName>")`创建以`<`与`>`包裹的`tagName`标签,也可以使用双标签的方式,或者在双标签内部添加内容
- 在`Dom`元素内部添加节点
  - `$(targetDom).append("div")`将`div`节点插入到`targetDom`元素中作为最后一个子节点
  - `$("div").appendTo(targetDom)`将`div`节点插入到`targetDom`元素中作为最后一个子节点
  - `$(targetDom).prepend("div")`将`div`节点插入到`targetDom`元素中作为第一个子节点
  - `$("div").prependTo(targetDom)`将`div`节点插入到`targetDom`元素中作为第一个子节点
- 在`Dom`元素同级添加节点
  - `$(targetDom).before("div")`将`div`节点插入到`targetDom`元素之前作为前一个兄弟节点
  - `$("div").insertBefore(targetDom)`将`div`节点插入到`targetDom`元素之前作为前一个兄弟节点
  - `$(targetDom).after("div")`将`div`节点插入到`targetDom`元素之后作为后一个兄弟节点
  - `$("div").insertAfter(targetDom)`将`div`节点插入到`targetDom`元素之后作为后一个兄弟节点
- 删除`Dom`节点
  - `$("div").remove()`删除`div`节点
  - `$("div").empty()`删除`div`节点中的所有子节点
- 替换`Dom`节点
  - `$("div").replaceWith(targetDom)`使用`targetDom`元素替换所有的`div`节点
  - `$(targetDom).replaceAll("div")`使用`targetDom`元素替换所有的`div`节点
- 克隆`Dom`节点
  - `$("div").clone(true,true)`将`div`节点拷贝,第一个参数用来控制是否将`div`节点绑定的事件进行克隆,第二个参数用来控制是否将`div`的子节点绑定的事件进行克隆

## 使用`ajax`

- 回调函数写法
  - `$.ajax({config})`使用该方法创建一个`ajax`请求
  - `config`的具体配置
    - `url`请求的目标地址
    - `method`请求的方法,默认为`get`方法
    - `headers`设置请求头
    - `data`设置请求体
    - `success(res){}`当请求数据成功后执行的回调函数
    - `error(err){}`当请求数据失败后执行的回调函数
    - `dataType`设置响应数据的格式
    - `timeout`设置超时间`(ms)`
- `Promise`风格
  - `$.ajax({config}).then().catch()`
- `async/await`风格
  - `await $.ajax({config})`
- `get`请求
  - `$.get(url,{params},callback)`向目标`url`单独发起`get`请求,`{params}`表示传递的参数,`callback`是成功的回调函数
  - 可以使用`Promise`与`async/await`风格
- `post`请求
  - `$.post(url,{params},callback)`向目标`url`单独发起`post`请求,`{params}`表示传递的参数,`callback`是成功的回调函数
  - 可以使用`Promise`与`async/await`风格
- `jsonp`请求
  - `$.ajax({config})`也可以使用`$.ajax`发送一个`jsonp`请求
  - `config`的具体配置
    - `url`请求的目标地址,不需要添加`callback`回调函数
    - `dataType:"jsonp"`设置响应数据的格式为`jsonp`
    - `jsonp:callbackName`设置`jsonp`属性,属性值为回调函数的`key`值
    - `callbackName:funName`设置需要执行的函数
    - `sunccess(){}`如果不设置`callback:funName`作为回调函数的定义,`jQuery`会自动生成一个临时函数,并且请求成功后会执行`success`
    - 同样地,支持使用`Promise`的`.then`语法
- 全局钩子函数
  - `$(window).ajaxStart(()=>{})`前置钩子,当一次性发送多个`ajax`请求时,只会在最开始发送前触发一次
  - `$(window).ajaxStop(()=>{})`后置钩子,当一次性发送多个`ajax`请求时,只会在末尾请求发送结束时触发依次
  - `$(window).ajaxSend(()=>)`前置钩子,在每个`ajax`请求发送之前执行
  - `$(window).ajaxSuccess(()=>{})`后置钩子,在每个`ajax`请求响应成功之后执行
  - `$(window).ajaxError(()=>{})`后置钩子,在每个`ajax`请求响应失败之后执行
  - `$(window).ajaxComplete(()=>{})`后置钩子,在每个`ajax`请求成功或失败之后执行
- 异步执行脚本
  - `window.onload=function(){}`原生异步加载脚本方法,当所有的`Dom`节点以及外部资源加载完成后再执行脚本
  - `$(window).ready(()=>{})`全局钩子,当所有的`Dom`加载完成后执行脚本
    - 简写方式`$(function(){})`该函数会在所有的`Dom`加载完成后执行脚本

## 深浅复制

- `$.entend(true,target,originObj1,originObj2,...)`对源对象实现深复制
  - `true`参数表示使用深复制,不添加该参数表示使用浅复制
  - `target`指的是目标对象
  - `originObj1`,`originObj2`等表示多个用来被复制的对象,这些对象都会被拷贝到`target`中

## 多库并存

- 多库并存用来让`jQuery`让渡`$`与`jQuery`作为变量名
- `let own=$.noConflict(true)`设置该方法将会使得`jQuery`不再使用`$`与`jQuery`作为变量名
  - `own`会替代`jQuery`的所有方法
  - `true`参数如果不传递,只会让渡出`$`的使用权,但是仍然可以使用`jQuery`

## 扩展机制

- `$.extend({fn(){}})`使用该方法向`jQuery`中新增一个`$.fn`的方法,可以直接实现调用
- `$.fn.extend({fun(){}})`使用该方法向`jQuery`原型中新增一个`$("div").fn()`方法
  - 一般地,在`jQuery`中,如果希望方法能够进行链式调用,直接在`fun`中返回`this`
