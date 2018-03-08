# node-validation-helper

`node-validation-helper` is a set of simple data validation and conversion tools for string input data that uses [Validator.js](https://www.npmjs.com/package/validator)

# [Installation](#installation)
<a name="installation"></a>

```shell
npm install @dealerslink/node-validation-helper
```

# [Usage](#usage)
<a name="usage"></a>

```js
const validationHelper = require('@dealerslink/node-validation-helper');

console.log(validationHelper.validate('1.23', 'float'));
console.log(validationHelper.validate('qwerty', 'float'));
console.log(validationHelper.validate('qwerty', 'string'));
console.log(validationHelper.convert('1.23', 'float'));
console.log(validationHelper.strToBool('yes'));
console.log(validationHelper.strToBool('True'));
```

# [API Reference](#api)
<a name="api"></a>

## validationHelper.validate(value, type [, options]) ⇒ boolean
Test is the string `value` is of the `type` specified. Additional [Validator.js](https://www.npmjs.com/package/validator) `options` may be passed for added constraints.

| Type | Desc | Options |
| ---- | ---- | ------- |
| `'int'`, `'integer'` |  Integer Values | Y |
| `'float'` | Floating Point Values | Y |
| `'bool'`, `'boolean'` | Boolean values | N |
| `'email'`, | Email addresses | Y |
| `'currency'` | Currency values (*e.g. '1.23', '$30', '€12,73'*) | Y |
| `'uuid'` | v1, v2, or v4 UUID values | N |
| `'url'` | Url values (*e.g. 'http://google.com'* ) | Y |
| `'fqdn'` | Fully-qualified Domain Name (*e.g. 'docs.google.com'*) | Y |
| `'apikey'` | A [`uuid-apikey`](https://www.npmjs.com/package/uuid-apikey) APIKey value  (e.g. 'ZYXWVTS-9876543-ABCDEFG-1234567') | N |
| `'string'` | String Values | N |
| `'any'` | Any possible value | N |

```js
validationHelper.validate('1.23', 'float');
```

**Output**:
```
true
```

## validationHelper.convert(value, type) ⇒ mixed
Attempts to convert the provided string `value` to the `type` specified. If the `type` is unknown, then the original `value` is returned.  The `type` can be `int`, `float`, or `bool`. For `int` and `float` values `NaN` is returned if the value can not be converted.

```js
validationHelper.convert('1234', 'int');
```

**Output**:
```
1234
```

## validationHelper.strToBool(str) ⇒ boolean
Converts the string value to a boolean. `true`, `yes`, `1` return a value `true`. All other value return `false`.
