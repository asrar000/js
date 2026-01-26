# JavaScript: NaN, undefined, and null Rules

## 1. Rules with Numbers

1. **NaN with numbers**
   - Any operation of `NaN` with a number will return `NaN`.

2. **undefined with numbers**
   - Any operation of `undefined` with a number will return `NaN`.

3. **null with numbers**
   - Any operation of `null` with a number is treated as `0`.

```js
NaN + 5        // NaN
undefined + 5  // NaN
null + 5       // 5
```

---

## 2. Rules with Strings

### Definitions
- **Empty strings:** `""`, `"   "` and equivalents
- **Non-empty strings:** `"abc"`, `"   abc"`, `"   abc   "`, `"asdasd  "`, etc.

### Rules
1. **String concatenation (`+`)**
   - Values are converted to strings and concatenated.

```js
"" + null        // "null"
" " + undefined  // " undefined"
"abc" + NaN      // "abcNaN"
```

2. **Other string operations (`-`, `*`, `/`, `%`)**
   - Values are converted to numbers.
   - `NaN` and `undefined` → `NaN`
   - `null` → `0`
   - Non-empty strings that cannot convert to number → `NaN`

```js
"" - null       // 0
"abc" - null    // NaN
"   " * undefined // NaN
```

---

## 3. Interactions Between NaN, undefined, and null

- Interaction with itself or each other generally produces `NaN`, **except** `null` with itself → `0`.

```js
NaN + undefined  // NaN
null + null      // 0
```

---

## 4. Boolean Conversion

```js
Boolean(NaN)        // false
Boolean(undefined)  // false
Boolean(null)       // false
```

---

## 5. Comparisons

| Comparison | Result | Explanation |
|------------|--------|-------------|
| NaN == NaN | false  | NaN ≠ anything |
| NaN === NaN | false | NaN ≠ anything, strict check |
| NaN != NaN | true   | Not equal is true |
| NaN !== NaN | true  | Strict not equal is true |
| undefined == undefined | true | Same primitive |
| undefined === undefined | true | Same primitive, strict |
| undefined != undefined | false | Not equal false |
| undefined !== undefined | false | Strict not equal false |
| null == null | true | Same primitive |
| null === null | true | Same primitive, strict |
| null != null | false | Not equal false |
| null !== null | false | Strict not equal false |
| NaN == undefined | false | NaN ≠ anything |
| NaN === undefined | false | NaN ≠ anything, strict |
| NaN != undefined | true | Not equal true |
| NaN !== undefined | true | Strict not equal true |
| NaN == null | false | NaN ≠ anything |
| NaN === null | false | NaN ≠ anything, strict |
| NaN != null | true | Not equal true |
| NaN !== null | true | Strict not equal true |
| undefined == null | true | Loose equality rule |
| undefined === null | false | Different types |
| undefined != null | false | Not equal false |
| undefined !== null | true | Strict not equal true |
