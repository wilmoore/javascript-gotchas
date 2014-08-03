# Object Property Access

When accessing a property of a JavaScript object, by default, if the property is not defined directly on the object, but rather on it's immediate or ancestor prototype object, the first value found will be returned.

```javascript
var assert = require('assert');

var database = {
    username: "",
    password: ""
};

var oracle = Object.create(database);

// this should throw an exception; however, it does not.
assert("username" in oracle);
```

In the example above, the assertion `assert("username" in oracle)` should result in a thrown exception; however, it does not. This is because the `in` operator returns an answer only after having traversed the entire prototype chain looking for the property in question. In this case, the `username` property is provided by the `username` property defined on the `database` object which is assigned as the prototype for the `oracle` object.

Sometimes, this is what you want; however, in some cases you actually want to know if a property has been set directly on the object. In this case, you'll want to use [Object.prototype.hasOwnProperty](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty).

```javascript
var assert = require('assert');

var database = {
    username: "",
    password: ""
};

var oracle = Object.create(database);

// this throws an exception as expected.
assert(oracle.hasOwnProperty("username"));
```

In the example above, the assertion `assert(oracle.hasOwnProperty("username"))` fails as expected. This is due to the fact that `Object.prototype.hasOwnProperty` does not traverse the entire prototype chain looking for the property in question. It only checks the specified object.

```javascript
var assert = require('assert');

var database = {
    username: "",
    password: ""
};

var oracle = Object.create(database);
oracle.username = "scott";
oracle.password = "tiger";

// this succeeds silently as expected.
assert(oracle.hasOwnProperty("username"));
```
