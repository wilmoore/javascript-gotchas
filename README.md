# JavaScript Gotchas

Over the years, I've kept notes on many JavaScript gotchas. These pitfalls range from those that are likely to stifle the uninitiated to those that make even seasoned JavaScripters slap themselves in shame for falling for a JavaScript prank that she has taken for granted.

## TODOS

- `this == global` if you do not use `new Ctor` or you do not use the trick `if !(this instanceof Ctor) return new Ctor(arguments)`
- `arguments` is not an array but can be converted into an array with `array.prototype.slice.call(arguments)`
- [Underscore + ES5-shim](https://github.com/es-shims/es5-shim/blob/master/es5-shim.js#L425-L464) -- always run your unit and integration tests with minified/optimized code (same as production) so you don't miss subtle bugs (like es5-shim + underscore issue).
- [IEs don’t recognize the difference between array holes and explicitly enumerable but undefined properties.](https://github.com/es-shims/es5-shim/issues/114#issuecomment-21700755)
- [JScript DontEnum Bug](https://developer.mozilla.org/en/docs/ECMAScript_DontEnum_attribute#JScript_DontEnum_Bug)
- [A safer Object.keys compatibility implementation](http://whattheheadsaid.com/2010/10/a-safer-object-keys-compatibility-implementation)
- [onScroll event on IE8](http://facebook.github.io/react/docs/working-with-the-browser.html#cross-browser-issues)
