# omit



{% code title="Hindley-Milner " %}
```text
(k[], T) -> Omit<T, K>
```
{% endcode %}

Returns a partial copy of an object omitting the keys specified.

```typescript
const me = { name: 'xiaoke', age: 18 }
omit(['age'], me)  // { name: 'xiaoke' }
```

{% hint style="danger" %}
在设计实现的过程中，使用 `Object.getOwnPropertyNames` 遍历对象属性。下面的例子：

```javascript
const man = {
  gender: 'male'
}
const me = Object.create(man, {
  name: {
    configurable: true,
    enumerable: true,
    value: 'xiaoke',
    writable: true
  },
  age: {
    configurable: true,
    enumerable: false,
    value: 18,
    writable: true
  }
})

omit(['name'], me)  // { age: 18 }
```

\`\`[`Object.keys` vs `Object.getOwnPropertyNames` vs `for...in` ?](https://github.com/maoxiaoke/xiaokedada/blob/master/assets/Iterate%20Object%20property.png?raw=true)
{% endhint %}

`omit` implements in `Dubhe`, [`Lodash`](https://lodash.com/) and [`Ramda`](https://ramdajs.com/)。

{% tabs %}
{% tab title="Dubhe" %}
```typescript
function omit <T extends PlainObject, K extends keyof T> (names: K[], obj: T): Omit<T, K> {
  const result = {} as any
  Object.getOwnPropertyNames(obj).forEach(props => {
    if (!names.includes(props as K)) {
      result[props] = obj[props]
    }
  })
  return result
}

export default omit
```
{% endtab %}

{% tab title="Lodash" %}
```javascript
empty
```
{% endtab %}

{% tab title="Ramda" %}
```javascript
var omit = _curry2(function omit(names, obj) {
  var result = {};
  var index = {};
  var idx = 0;
  var len = names.length;

  while (idx < len) {
    index[names[idx]] = 1;
    idx += 1;
  }

  for (var prop in obj) {
    if (!index.hasOwnProperty(prop)) {
      result[prop] = obj[prop];
    }
  }
  return result;
});
export default omit;
```
{% endtab %}
{% endtabs %}



