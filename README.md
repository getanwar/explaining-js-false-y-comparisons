-SPECS-

In the ES5 spec, clauses 11.9.3.4-5 say:

> If Type(x) is Number and Type(y) is String, return the result of the comparison x == ToNumber(y).

> If Type(x) is String and Type(y) is Number, return the result of the comparison ToNumber(x) == y.

Clauses 11.9.3.6-7:

> If Type(x) is Boolean, return the result of the comparison ToNumber(x) == y.

> If Type(y) is Boolean, return the result of the comparison x == ToNumber(y).

Clauses 11.9.3.8-9:

> If Type(x) is either String or Number and Type(y) is Object, return the result of the comparison x == ToPrimitive(y).

> If Type(x) is Object and Type(y) is either String or Number, return the result of the comparison ToPrimitive(x) == y.

Note: In `==` comparison, coerce will happen until both become same type.

---

#### `"0" == null;`

Observe: String and null is being compared

According to spec only null = undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `"0" == undefined;`

Observe: String and undefined is being compared

According to spec only null = undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `"0" == false;`

Observe: String and Boolean is being compared

Coercion: Boolean `false` is coerced to Number resulting `0`

Read: `"0" == 0`

Observe: String and Number is being compared

Coercion: String `"0"` is coerced to Number resulting 0

Read: `0 == 0`

Observe: Type matched - value matched 

Result: `true`

---

#### `"0" == NaN;`

Observe: String and Number is being compared. Or more appropriately, NaN is never equal to itself or any other value

Coercion: String `"0"` is coerced to Number resulting `0`

Read: `0 == NaN`

Observe: Type matched or more appropriately, NaN is never equal to itself or any other value

Result: `false`

---

#### `"0" == 0;`

Observe: String and Number is being compared

Coercion: String `"0"` is coerced to Number resulting `0`

Read: `0 == 0`

Observe: Type matched - value matched

Result: `true`

---

#### `"0" == "";`

Observe: Two Strings are being compared

Coercion: No coercion happens

Observe: Type matched - value mismatched

Result: `false`

---

#### `false == null;`

Observe: Boolean and null is being compared

According to spec only null == undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `false == undefined;`

Observe: Boolean and undefined is being compared

According to spec only null == undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `false == NaN;`

Observe: Boolean and Number is being compared. Or more appropriately, NaN is never equal to itself or any other value

Coercion: Boolean `false` is coerced to Number resulting `0`

Read: `0 == NaN`

Observe: Type matched or more appropriately, NaN is never equal to itself or any other value

Result: `false`

---

#### `false == 0;`

Observe: Boolean and Number is being compared

Coercion: Boolean `false` is coerced to Number resulting `0`

Read: `0 == 0`

Observe: Type matched - value matched

Result: `true`

---

#### `false == "";`

Observe: Boolean and String is being compared

Coercion: Boolean `false` coerced to Number resulting `0`

Read: `0 == ""`

Observe: Number and String is being compared

Coercion: String `""` coerced to Number resulting `0`

Read: `0 == 0`

Observe: Type matched - value matched

Result: `true`

---

#### `false == [];`

Observe: Boolean and Array (Object) is being compared

Coercion 1: Boolean `false` is coerced to Number resulting `0`

Coercion 2: Object is coerced using ToPremitive abstruct method resulting `""`

Read: `0 == ""`

Observe: Number and String is being compared

Coercion: String `""` is coerced to Number resulting `0`

Read: `0 == 0`

Observe: Type matched - value matched

Result: `true`

---

#### `false == {};`

Observe: Boolean and Object is being compared

Coercion 1: Boolean `false` coerced to Number resulting `0`

Coercion 2: Object is coerced using ToPremitive abstruct method resulting `"[object Object]"`

Read: `0 == "[object Object]"`

Observe: Number and String is being compared

Coercion: String `"[object Object]"` is coerced to Number resulting `NaN`

Read: `0 == NaN`

Observe: Type matched or more appropriately, `NaN` is never equal to itself or any other value

Result: `false`

---

#### `"" == null;`

Observe: String and null is being compared

According to spec only null == undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `"" == undefined;`

Observe: String and undefined is being compared

According to spec only null == undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `"" == NaN;`

Observe: String and Number is being compared. Or more appropriately, `NaN` is never equal to itself or any other value

Coercion: String `""` is coerced to Number resulting `0`

Read: `0 == NaN`

Observe: Type matched or more appropriately, `NaN` is never equal to itself or any other value

Result: `false`

---

#### `"" == 0;`

Observe: String and Number is being compared

Coercion: String `""` is coerced to Number resulting `0`

Read: `0 == 0`

Observe: Type matched - value matched

Result: `true`

---

#### `"" == [];`

Observe: String and Array (Object) is being compared

Coercion: Object is coerced using ToPremitive abstruct method resulting `""`

Read: `"" == ""`

Observe: Type matched - value matched

Result: `true`

---

#### `"" == {};`

Observe: String and Object is being compared

Coercion: Object is coerced using ToPremitive abstruct method resulting `"[object Object]"`

Read: `"" == "[object Object]"`

Observe: Type matched - value mismatched

Result: `false`

---

#### `0 == null;`

Observe: Number and null is being compared

According to spec only null == undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `0 == undefined;`

Observe: Number and undefined is being compared

According to spec only null == undefined or vise-versa

Coercion: No coercion happens

Result: `false`

---

#### `0 == NaN;`

Observe: Type matched or more appropriately, `NaN` is never equal to itself or any other value

Result: `false`

---

#### `0 == [];`

Observe: Number and Array (Object) is being compared

Coercion: Object is coerced using ToPremitive abstruct method resulting `""`

Read: `0 == ""`

Observe: Number and String is being compared

Coercion: String `""` is coerced to Number resulting `0`

Read: `0 == 0`

Observe: Type matched - value matched

Result: `true`

---

#### `0 == {};`

Observe: Number and Object is being compared

Coercion: Object is coerced using ToPremitive abstruct method resulting `"[object Object]"`

Read: `0 == "[object Object]"`

Observe: Number and String is being compared

Coercion: String `"[object Object]"` is coerced to Number resulting `NaN`

Read: `0 == NaN`

Observe: Type matched or more appropriately, `NaN` is never equal to itself or any other

Result: `false`

---

Note: Underlying JavaScript engine may or may not follow exactly the same steps. I wanted to describe it as easy as hell.

### Credit
[YDKJS](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch4.md#false-y-comparisons)
