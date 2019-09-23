# [typeof null, null instanceof Object]表达式的返回值是什么？

```javascript
    [typeof null, null instanceof Object]
```
%accordion%点击查看结果%accordion%
```javascript
["object", false]
```
%/accordion%
***
延伸：
* 基本类型 Boolean Number String Null Undefined BigInt Symbol
* null(薛定谔的对象) 与 undefined的区别
    * 是一个字面量，它不像undefined 是全局对象的一个属性。null 是表示缺少的标识，指示变量未指向任何对象
    * Number(null)输出为0, Number(undefined)输出为NaN
* typeof instanceof Object.getPrototypeOf()  