# isNil

{% code title="Hindley-Milner " %}
```text
* -> boolean
```
{% endcode %}

Check if the input value is  `undefined` or `null`.

```typescript
 isNil(null) // true
 isNil(undefined) // true
 isNil(void 0) // true
 isNil(0) // false
```

{% hint style="info" %}
[What is the difference between `undefined` and `void 0`?](https://stackoverflow.com/questions/5716976/javascript-undefined-vs-void-0)
{% endhint %}

`isNil` implements in `Dubhe`, [`Lodash`](https://lodash.com/) and [`Ramda`](https://ramdajs.com/)。

{% tabs %}
{% tab title="Dubhe" %}
```typescript
const isNil: (value: any) => boolean = (value) => {
  return value === undefined || value === null
}

export default isNil
```
{% endtab %}

{% tab title="Lodash" %}
```javascript
function isNil(value) {
  return value == null
}

export default isNil
```
{% endtab %}

{% tab title="Ramda" %}
```javascript
var isNil = _curry1(function isNil(x) { return x == null; });
export default isNil;
```
{% endtab %}
{% endtabs %}

