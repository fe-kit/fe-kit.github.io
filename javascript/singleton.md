# 实现一个单例模式？
> 定义：保证一个类仅有一个实例，并提供一个访问它的全局访问点

> 核心：确保只有一个实例，并提供全局访问

### 实现
%accordion%点击查看%accordion%
```javascript
function getSingleton(fn) {
    let instance = null;
    return function () {
        if (!instance) {
            instance = fn.apply(this, arguments);
        }
        return instance;
    }
}

// 调用单例
function manager(name) {
    this.name = name;
}
manager.prototype.getName = function() {
    return this.name;
}
const singleManager = getSingleton(function(name){
    return new manager(name);
})

singleManager('a').getName();// a
singleManager('b').getName();// a
singleManager('c').getName();// a
```
%/accordion%


***
### 延伸
* 一般用于全局缓存，比如全局window，唯一登录浮窗等
* 如果一个类负责连接数据库的线程池、日志记录逻辑等等，此时需要单例模式来保证对象不被重复创建，以达到降低开销的目的。
