# 实现一个单例模式？
> 定义：保护代理可以在代理中直接拒绝对对象的访问；虚拟代理可以延迟访问到真正需要的时候，以节省程序开销；缓存代理

> 核心：代理模式可以解决避免对一些对象的直接访问

> 优缺点：代理模式有高度解耦、对象保护、易修改等优点。 同样地，因为是通过“代理”访问对象，因此开销会更大，时间也会更慢。

### 实现
%accordion%保护代理:点击查看%accordion%
```javascript
// 图片懒加载
const originallyImg = {
    setSrc(imgNode, src) {
        imgNode.src = src;
    }
}
// 保护代理
const ProxyImg = {
    setSrc(imgNode, src){
        var img = new Image();
        img.onload = function(){
            originallyImg.setSrc(imgNode, this.src);
        };
        imgNode.src =  "http://s1.bdstatic.com/r/www/cache/mid/static/xueshu/img/logo_4b1971d.gif";
        img.src = src;
    }
}
// 调用方式
let imgNode = document.createElement("img"),
  imgSrc = " https://www.baidu.com/img/xinshouyedong_4f93b2577f07c164ae8efa0412dd6808.gif";
document.body.appendChild(imgNode);
ProxyImg.setSrc(imgNode, imgSrc);
```
%/accordion%

%accordion%缓存代理:点击查看%accordion%
```javascript
// 缓存代理
function add (...arg) {console.info(1)
    return arg.reduce((x, y) => x + y);
}

function proxyFunc (fn) {
    const cache = {};
    return function () {
        const key = [...arguments].join(',');
        if (cache[key]) {
            return cache[key];
        }
        return cache[key] = fn.apply(this, arguments);
    }
}

const proxyAdd = proxyFunc(add);
console.info(proxyAdd(1,2))
console.info(proxyAdd(1,2))
```
%/accordion%

> 虚拟代理 -> [函数防抖节流](/javascript/debounce.html)

***
### 延伸
* 懒加载，合并http请求和缓存。