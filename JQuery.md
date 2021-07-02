# JQuery基础知识

-----------------------------

**1. 基础语法**

   ```javascript
   $(this).hide() //隐藏当前元素
   
   $("p").hide() //隐藏所有 <p> 元素
   
   $("p.test").hide() //隐藏所有 class="test" 的 <p> 元素
   
   $("#test").hide() //隐藏 id="test" 的元素
   ```

   

**2. 当页面的DOM都加载完之后便会执行以下的方法。**

```javascript
$(document).ready(function(){
   //执行代码 
});

$(function(){
   执行代码 
});
```

3. 把从后台传过来的JSON对象转换为JSON。（传过来的JSON对象是用{}包起来的语句块，需要先转为JSON格式）

```javascript
let dataBoj = eval（"("+data+")"）
```

4. 待延迟对象(DeffertObject)完成后再执行done里面的方法

```javascript
$(function () { 
    $.when( DeffertObject ).done(
    function(x) { method(); } 
    );
})
```

