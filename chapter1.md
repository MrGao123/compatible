## 1.innerText

> 兼容情况：火狐4.5以下版本不支持

```js
    //兼容实现
    function innerText(obj) {
        if (obj.innerText) {
             return obj.innerText;  
        }
        return obj.textContent;
    }
```

## 2.nextElementSibling/previousElementSibling

> 兼容情况：IE8及以下不兼容

```js
    //兼容实现：nodeType：1-元素节点 2-属性节点 3-文本节点 8-注释节点 9-document
    
    function nextElementSinling(obj){
        if (obj.nextElementSibling) {
            return obj.nextElementSibling;
        }
        var elems = obj.nextSiblings;
        for (var i = 0; i < elems.length; i++) {
            if (elems.nodeType !== 1) {
                return elems;
            }
        }
        return null;
    }
```

## 3.trim()

> 兼容情况：IE8以下不兼容

```js
    function trim(str) {
        if (str.trim) {
            return sre.trim();
        }
        var reg = /^\s | \s$/
        return str.replace(reg,"");
    }  
```

## 4.绑定事件操作：
* W3C标准：addEventListener
* IE：attachEvent
* 
    两者区别：前者事件类型不需要加"on"前缀，并且事件处理函数中的this指向触发对象；

    后者事件类型需要加“on”前缀，并且事件处理函数内部的this指向window。

```js
    //兼容实现
    function addEventListener(obj,type,callback) {
        if (obj.addEventListener) {
            obj.addEventListener(type,callback);
        } else {
            obj.attachEvent("on"+type,callback.call(obj));
        }            
    }
```

## 5.事件解绑
* W3C标准：removeEventListener
* IE：detachEvent

```js
    //兼容实现
    function removeEventListener(obj, type, fnName){
        if (obj.removeEventListener) {
            obj.removeEventListener(type, fnName);
        } else {
            obj.detachEvent(type, fnName);
        }        
    }
```

