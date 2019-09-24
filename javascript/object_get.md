# 获取对象路径处的值_.get(object, 'a.b.c', 'default');
> Gets the value at path of object. If the resolved value is
undefined, the defaultValue is returned in its place.

### 结果
%accordion%点击查看结果%accordion%
```javascript
var object = { 'a': { 'b': { 'c': 3 } } };
function get(object, path, defaults) {
    if (object === null) return defaults;
    let index = 0;
    const arr = path.split('.');
    while (arr[index] && object[arr[index]]) {
        object = object[arr[index]];
        index += 1;
    }
    return index && index === arr.length ? object : undefined;
};
console.info(get(object, 'a.b.c'));
```
%/accordion%


***
### 延伸
* lodash _.get方法了解
* 结构取值const {a:{b:{c}}} = object;
* try catch