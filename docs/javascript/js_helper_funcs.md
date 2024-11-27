# JavaScript Helper Functions

The following are global JavaScript functions that are used by WebLOAD and can be used to perform specific tasks.

### Methods

#### DebugMessage(str)

Print message to log. Like InfoMessage() but logs only when running in WebLOAD Recorder, not in Console

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | to log |

#### DecodeString(s)

Decoding function - reverse of EncodeString

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to unescape |

See:

*   [EncodeString](global.html#EncodeString)

**Returns:**

\- decoded string

#### DecodeStringUnix(s)

Decoding function - reverse of EncodeString + convert end-of-line from unix to dos format

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to unescape |

See:

*   [EncodeString](global.html#EncodeString)

**Returns:**

\- decoded string

#### DecodeStringWin(s)

Decoding function - reverse of EncodeStringWin

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to unescape |

See:

*   [EncodeStringWin](global.html#EncodeStringWin)

**Returns:**

\- decoded string

#### EncodeString(s)

Encoding function - escape given string, replace special chars with %xx notaion. Similar to 'escape', except that it convert space to "+" (not %20), "/" to "%2F" and "+" to "%2B"

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to escape |

**Returns:**

\- escaped string

#### EncodeStringWin(s)

Encoding function - escape given string, replace special chars with %xx notaion. Similar to 'EncodeString', but converts linux style \\n to windows style \\r\\n

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to escape |

**Returns:**

\- escaped string

#### SleepEvery(millis)

SleepEvery a certain multiple number of milliseconds has passed since the beginning of the session. Can be used to synchronize virtual users session for intervals.

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `millis` | number | time in milliseconds from session start to repeatedly wait before resuming |

**Example**

```js
SleepUntil(5000); //wait until a multiple of 5 seconds have passed, for example, if called at 00:02 seconds into the session, will wait to 00:05, if call at 00:06 will wait until 00:10
```

#### SleepUntil(millisFromBeginning)

SleepUntil a certain number of milliseconds has passed since the beginning of the session. Can be used to synchronize virtual users session start.

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `millisFromBeginning` | number | time in milliseconds from session start to wait before resuming |

See:

*   [SleepEvery](global.html#SleepEvery)

**Example**

``` javascript
SleepUntil(5000); //wait until 5 seconds have passed
```

#### addTransactionsToMDC()

When called, will cause all transactions to be automatically added to MDC

See:

*   [putMDC](global.html#putMDC)

#### assertEquals(expected, actual, messageopt)

JUnit like helper function - compare actal and expected and throw an error in they are different

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `expected` | \*  |     | value to be compared to |
| `actual` | \*  |     | actual value |
| `message` | string | <optional> | custom message to show if values don't match |

#### assertFalse(expr, messageopt)

JUnit style assert that expression is false

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `expr` | boolean |     | expression to check |
| `message` | string | <optional> | custom message |

#### assertNotEquals(expected, actual, messageopt)

JUnit like helper function - compare actal and expected and throw an error in they are the same

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `expected` | \*  |     | value to be compared to |
| `actual` | \*  |     | actual value |
| `message` | string | <optional> | custom message to show if values are the same |

#### assertTrue(expr, messageopt)

JUnit style assert that expression is true

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `expr` | boolean |     | expression to check |
| `message` | string | <optional> | custom message |

#### clearMDC()

Clear content of MDC (Mapped Diagnostic Context)

See:

*   [putMDC](global.html#putMDC)

#### closeAllWebSockets(ws\_prefixopt, from\_idxopt, to\_idxopt)

Close all WebSocket objects

**Parameters:**

| Name | Type | Attributes | Default | Description |
| --- | --- | --- | --- | --- |
| `ws_prefix` | string | <optional> | ws  | prefix of var name |
| `from_idx` | number | <optional> | 1   |     |
| `to_idx` | number | <optional> | 20  |     |

**Example**

```
//will close all WebSocket objects named "ws1" to "ws20"
 closeAllWebSockets();
```

#### decodeXML(str)

Decoding function - reverse of encodeXML

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encode |

See:

*   [encodeXML](global.html#encodeXML)

**Returns:**

decoded string

#### decodeXmlAtt(str)

Decoding function - reverse of encodeXmlAtt

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | encoded string to decode |

See:

*   [encodeXmlAtt](global.html#encodeXmlAtt)

**Returns:**

\- decoded string

**Example**

```
//returns "abc:/egf="
decodeXmlAtt("abc&#x3a;&#x2f;egf\&#x3d;")
```

#### decodeXmlAttEsc(str)

Decoding function - converts XML attribute format (&#x??;) to URL encoding format (%??)

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | encoded string to decode |

**Returns:**

\- decoded string

#### decodeXmlAttNum(str)

Decoding function - decodes XML Attribute in numeric format

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | encoded string to decode |

**Returns:**

\- decoded string

**Example**

```
//returns "\"strategy\""
decodeXmlAttNum("&#34;strategy&#34;")
```

#### encodeURIComponentLower(s)

Encoding function - Similar to encodeURIComponent but uses lower-case letters

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to escape |

**Returns:**

\- escaped string

#### encodeXML(str)

Encoding function - encodes XML tags

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encode |

**Returns:**

encoded string

#### encodeXMLbroken(str)

Encoding function - like encodeXML but > is not replaced, only < and &

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string |     |

See:

*   [encodeXML](global.html#encodeXML)

**Returns:**

encoded string

#### encodeXmlAtt(str)

Encodeing function - encode an XML Attribute.

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encoded |

**Returns:**

\- encoded string

**Example**

```
//returns "pcdshort&#x3a;&#x2f;M0szu5jMrfDvCVJp71LcecoFE5s\&#x3d;"
encodeXmlAtt("pcdshort:/M0szu5jMrfDvCVJp71LcecoFE5s=")
```

#### encodeXmlAttEsc(str)

Encoding function - coverts escaped string to XML attribute escaped string

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encoded |

**Returns:**

\- encoded string

**Example**

```
//returns "a&#x2b;b"
encodeXmlAttEsc( "a%2Bb")
```

#### escapeAug(str)

Encoding function - vairation of escape. Also encodes @ / and ~

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encoded |

**Returns:**

\- encoded string

#### escapeLower(str)

Encoding function - this is similar to 'escape', but uses lower case character, i.e. equals (=) sign is '%3d' instead of '%3D'

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to escape |

**Returns:**

\- encoded string

#### escapeSiebel(str)

Encoding function - vairation of escape. Only escape %, :, /, +, =. Space encoded as +. Used by Siebel

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encoded |

**Returns:**

\- encoded string

#### escapeV2(str)

Encoding function - vairation of escape. Also encodes / and ~

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | string to encoded |

**Returns:**

\- encoded string

#### escapeXPath(path)

For XPath - make the given string valid for XPath expressions - escaping quotes if needed

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `path` | string | to escape |

**Returns:**

escaped path

#### escapeXmlBroken(s)

Encoding function - decodes and escapes XML tags

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to encode |

**Returns:**

encoded string

**Example**

```
//returns "%3Csome%40Tag%3E"
escapeXmlBroken("&lt;some@Tag&gt;")
```

#### extractAllValues()

extractAllValues() Returns array of all values matching the prefix/suffix.

**Example**

```
// returns: ["aaa", "bbb"]
extractAllValues("<td>","</td>","<tr><td>aaa</td><td>bbb</td></tr>");
```

#### extractHeaderValue(prefix, suffix, header\_name)

Extract a value from the given HTTP Header name

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `prefix` | string | optional, return value after this prefix. Use "" to start from beginning |
| `suffix` | string | optional, return value before this suffix. Use "" to return until the end |
| `header_name` | string | name of HTTP header to search |

**Returns:**

\- value of header of null if not found

#### extractJSPath(expr, src)

Extract value using JSPath https://www.npmjs.com/package/jspath To test, use http://www.jsonquerytool.com/ with type: JSPath (dfilatov 0.4.0)

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `expr` | string | expresion to use |
| `src` | string \| JSON | string to extract from (needs to be JavaScrint object, or a JSON string that can converted to it) |

**Returns:**

extracted value or null if not found

#### extractJsonValue(path, source)

Get value from JSON using a simple path - path.to.item

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `path` | string | dot delimited path to item |
| `source` | string | String containing JSON string |

See:

*   [extractJSPath](global.html#extractJSPath) - more full featured expressions

**Returns:**

value at specified path or null of not found

#### extractRegExpTemplate(reStr, srcopt, templateopt)

Extract based on regular expression, from src, with possible template - number enclosed in $ for capturing group

**Parameters:**

| Name | Type | Attributes | Default | Description |
| --- | --- | --- | --- | --- |
| `reStr` | string |     |     | string with RegExp expression |
| `src` | string | <optional> | document.wlSource | source to search at |
| `template` | string | <optional> |     | template to use the extracted values with |

**Returns:**

extracted value, or null if not found

**Examples**

```
//returns:"54321"
extractRegExpTemplate ( "foo=(.*?)&", "foo=54321&")
```

```
//returns: "templated-54321-answer"
extractRegExpTemplate ( "foo=(.*?)&", "the foo=54321&abcde&zzzz", "templated-$1$-answer")
```

#### extractSiebelArrayValue(idx, prefix, suffix, source, instance)

Extact a value from Siebel 'star' array, in format \`length@value..\`

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `idx` | number | index of item in array to return. can be negative, so -1 is last one. |
| `prefix` | string | prefix to look in source for start of array |
| `suffix` | string | suffix to look in source for start of array |
| `source` | string | source of data to look for. To get value from HTTP response use document.wlSource |
| `instance` | number | occurence of prefix/suffix to find the array in the source |

**Returns:**

value extracted or null if not found.

**Example**

```
var str = "`array`10*first_item11*second_item`";
//returns "first_item"
extractSiebelArrayValue(0, "`array`", "`", str, 1)
```

#### extractValue(prefix, suffix, str, orderopt, left\_offsetopt, right\_offsetopt)

Extracts a value from a string having a prefix and a suffix

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `prefix` | string |     | text before value to extract to find |
| `suffix` | string |     | text after value to extract to find |
| `str` | string |     | string to look for. Mostly this will be document.wlSource to look in previous http response |
| `order` | number | <optional> | which occurence to return. Default is first (1). Negative value means from end, so -1 is last. |
| `left_offset` | number | <optional> | number of chars from left to remove from returned value. |
| `right_offset` | number | <optional> | number of chars from right to remove from returned value. |

**Returns:**

value extracted, or null is not found

**Example**

```
//return xx
extractValue("a","b","axxb")
```

#### extractValueByLength(prefix, len, str, order, left\_offset, right\_offset)

Extracts a value from a string having a prefix with the specified length.

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `prefix` | string | String to search |
| `len` | number | length of value to return, after the prefix |
| `str` | string | string to search in. Mostly document.wlSource |
| `order` | number | How many times to look for prefix |
| `left_offset` | number | number of character before/after the left boundry to return (before: negative value) |
| `right_offset` | number | number of character before/after the rigth boundry to return (before: negative value) |

**Returns:**

extract value or null if not found

**Examples**

```
//return "4321"
extractValueByLength("abc$", 4, "xxabc$4321xxx")
```

```
//return  "$4444$"
extractValueByLength("abc$", 4, "xxabc$4321abc$4444$xxx", 2, -1, 1)
```

#### extractXPath(expr, source)

Extract from XML using XPath expression

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `expr` | string | XPath expresion. For example "/bookstore/book\[1\]/title" |
| `source` | string | XML string to search for |

**Returns:**

extracted value or null is not found

#### extractXmlValue(tagName, index, source)

Extract tag value from XML string

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `tagName` | string | tag to search |
| `index` | number | which occurence to return |
| `source` | string | XML string |

**Returns:**

tag value

#### fail(message)

JUnit style fail - throw error

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `message` | \*  | to throw |

#### getCorrelationValue(varName, func) → {object}

Get value previously extracted

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `varName` | string | variable name to extract |
| `func` | function | conversion/encoding function if needed |

**Returns:**

stored correlation value

Type

object

#### getMDC(nameopt)

Return value in MDC (Mapped Diagnostic Context)

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `name` | string | <optional> | item to return, if omiited all values are returned |

See:

*   [putMDC](global.html#putMDC)

**Returns:**

value or all values

#### pollCorrelationValue(varName, func, timeout) → {object}

Get value previously extracted, wait for it if it does not exist. Useful in async situations.

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `varName` | string | variable name to extract |
| `func` | function | conversion/encoding function if needed |
| `timeout` | number | number of milliseconds to wait before timing out. Default to 30 seconds. |

**Returns:**

value expected, or null if it did not exist

Type

object

#### printMDC()

Print (InfoMessage) content of MDC (Mapped Diagnostic Context)

See:

*   [putMDC](global.html#putMDC)

#### putMDC(name, value)

Sets given name=value in MDC (Mapped Diagnostic Context). Contents of MDC will be displayed if error happens in the script. Useful to debug issues

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `name` | string | name of parameter |
| `value` | string | value to set |

**Example**

```
//will log the user name in case of error
putMDC("username", users_username.getValue() );
```

#### removeMDC(name)

Remove items from MDC (Mapped Diagnostic Context)

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `name` | string |     |

See:

*   [putMDC](global.html#putMDC)

#### setCorrelationValue(varName, extractedValue, originalValueopt, errorFuncopt)

Store extracted correlation value for future use. Validate it against the recorded value. Use getCorrelationValue() to retrieve the value.

**Parameters:**

| Name | Type | Attributes | Description |
| --- | --- | --- | --- |
| `varName` | string |     | name of correlation value to set |
| `extractedValue` | string |     | the value to store |
| `originalValue` | string | <optional> | original (recorded) value to compare (only first 200 chars are compared) |
| `errorFunc` | string \| number | <optional> | function used to log not found errors. Default is WarningMessage. Can be degined globally using 'correlationErrorFunc'. If given value is a number constant, for example 'WLMinorError' then it also triggers Full Error Details to be logged |

See:

*   [getCorrelationValue](global.html#getCorrelationValue)

#### setCorrelationValueSilent()

Like setCorrelationValue() but does not show a WarningMessage() when not extracted.

#### unescapeUnix(s)

Decoding function - reverse of escape + convert end-of-line from unix to dos format

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `s` | string | string to unescape |

**Returns:**

\- decoded string

#### unescapeXMLbroken(str)

Decoding function - reverse of escapeXmlBroken

**Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| `str` | string | encoded string to decode |

**Returns:**

\- decoded string

#### uuidv4() → {string}

Generate v4 UUID Universally unique identifier

**Returns:**

Generated ID

Type

string