# ["1", "2", "3"].map(parseInt) 返回值是什么？
```javascript
    var new_array = arr.map(function callback(currentValue[, index[, array]]) {
    // Return element for new_array 
    }[, thisArg])
```
%accordion%点击查看结果%accordion%
```javascript
1, NaN, NaN
```
%/accordion%
***
延伸：
* map语法
* parseInt(string, radix) 当未指定radix时，不同的实现会产生不同的结果，通常认为其值默认为10