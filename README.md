# js-skill-Es6

> 超实用的 JavaScript 代码片段（ ES6+ 编写）

## Array 数组

---

> ### Array concatenation (数组拼接)
>
> - 使用 Array.concat() ，通过在 args 中附加任何数组 和/或 值来拼接一个数组

```
 const ArrayConcat = (arr, ...args) => [].concat(arr, ...args);
 // ArrayConcat([1], [1, 2, 3, [4]]) -> [1, 2, 3, [4]]
```

---

> ### Array difference (数组比较)
>
> - 根据数组 b 创建一个 Set 对象，然后在数组 a 上使用 Array.filter() 方法，过滤出数组 b 中不包含的值。

```
const difference = (a, b) => { const s = new Set(b); return a.filter(x => !s.has(x)); };
// difference([1,2,3], [1,2]) -> [3]
```

---

> ### Array includes (数组包含)
>
> - 使用 slice() 来抵消数组/字符串，并且使用 indexOf() 来检查是否包含该值。如果省略最后一个参数 fromIndex ，则会检查整个数组/字符串。

```
const includes = (collection, val, fromIndex=0) => collection.slice(fromIndex).indexOf(val) != -1;
// includes("30-seconds-of-code", "code") -> true
// includes([1, 2, 3, 4], [1, 2], 1) -> false
```

---

> ### Array intersection (数组交集)
>
> - 根据数组 b 创建一个 Set 对象，然后在数组 a 上使用 Array.filter() 方法，只保留数组 b 中也包含的值。

```
const intersection = (a, b) => { const s = new Set(b); return a.filter(x => s.has(x)); };
// intersection([1,2,3], [4,3,2]) -> [2,3]
```

---

> ### Array remove (移除数组中的元素)
>
> - 使用 Array.filter() 和 Array.reduce() 来查找返回真值的数组元素，使用 Array.splice() 来移除元素。 func 有三个参数(value, index, array)。

```
const remove = (arr, func) =>
Array.isArray(arr) ? arr.filter(func).reduce((acc, val) => {
arr.splice(arr.indexOf(val), 1); return acc.concat(val);
}, []): [];
//remove([1, 2, 3, 4], n => n % 2 == 0) -> [2, 4]
```

---

> ### Array sample (数组取样随，机获取数组中的 1 个元素)
>
> - 使用 Math.random() 生成一个随机数，乘以 length，并使用 Math.floor() 舍去小数获得到最接近的整数。这个方法也适用于字符串。

```
const sample = arr => arr[Math.floor(Math.random() * arr.length)];
// sample([3, 7, 9, 11]) -> 9
```

---

> ### Array union (数组合集)
>
> - 用数组 a 和 b 的所有值创建一个 Set 对象，并转换成一个数组。

```
const union = (a, b) => Array.from(new Set([...a, ...b]));
// union([1,2,3], [4,3,2]) -> [1,2,3,4]
```

---

> ### Array without (从数组中排除给定值)
>
> - 使用 Array.filter() 创建一个排除所有给定值的数组。

```
const without = (arr, ...args) => arr.filter(v => args.indexOf(v) === -1);
// without([2, 1, 2, 3], 1, 2) -> [3]
// without([2, 1, 2, 3, 4, 5, 5, 5, 3, 2, 7, 7], 3, 1, 5, 2) -> [ 4, 7, 7 ]
```

---

> ### Array zip (创建一个分组元素数组)
>
> - 使用 Math.max.apply() 获取参数中最长的数组。 创建一个长度为返回值的数组，并使用 Array.from() 和 map-function 来创建一个分组元素数组。 如果参数数组的长度不同，则在未找到值的情况下使用 undefined

```
const zip = (...arrays) => {
const maxLength = Math.max.apply(null, arrays.map(a => a.length));
return Array.from({length: maxLength}).map((_, i) => {
return Array.from({length: arrays.length}, (_, k) => arrays[k][i]);
})
}
//zip(['a', 'b'], [1, 2], [true, false]); -> [['a', 1, true], ['b', 2, false]]
//zip(['a'], [1, 2], [true, false]); -> [['a', 1, true], [undefined, 2, false]]
```

---
