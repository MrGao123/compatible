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

## 2.nextElementSibling

> 兼容情况：IE8及以下不兼容

```js
    function nextElementSinling(obj){
        if (obj.nextElementSibling) {
            return obj.nextElementSibling;
        }
        var elems = obj.nextSiblings;
        for (var i = 0; i < elems.lengthl; i++) {
            if (elems.nodeType !== 1) {
                return elems;
            }
        }
    }
```

