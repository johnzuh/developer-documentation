<small>Piwik</small>

Url
===

Provides URL related helper methods.

Description
-----------

This class provides simple methods that can be used to parse and modify
the current URL. It is most useful when plugins need to redirect the current
request to a URL and when they need to link to other parts of Piwik in
HTML.

### Examples

**Redirect to a different controller action**

    $url = Url::getCurrentQueryStringWithParametersModified(array(
        &#039;module&#039; =&gt; &#039;UserSettings&#039;,
        &#039;action&#039; =&gt; &#039;index&#039;
    ));
    Url::redirectToUrl($url);

**Link to a different controller action in a template**

    $url = Url::getCurrentQueryStringWithParametersModified(array(
        &#039;module&#039; =&gt; &#039;UserCountryMap&#039;,
        &#039;action&#039; =&gt; &#039;realtimeMap&#039;,
        &#039;changeVisitAlpha&#039; =&gt; 0,
        &#039;removeOldVisits&#039; =&gt; 0
    ));
    $view = new View(&quot;@MyPlugin/myPopup&quot;);
    $view-&gt;realtimeMapUrl = $url;
    echo $view-&gt;render();


Methods
-------

The class defines the following methods:

- [`getCurrentUrl()`](#getCurrentUrl) &mdash; Returns the current URL.
- [`getCurrentUrlWithoutQueryString()`](#getCurrentUrlWithoutQueryString) &mdash; Returns the current URL without the query string.
- [`getCurrentUrlWithoutFileName()`](#getCurrentUrlWithoutFileName) &mdash; Returns the current URL without the query string and without the name of the file being executed.
- [`getCurrentScriptPath()`](#getCurrentScriptPath) &mdash; Returns the path to the script being executed.
- [`getCurrentScriptName()`](#getCurrentScriptName) &mdash; Returns the path to the script being executed.
- [`getCurrentScheme()`](#getCurrentScheme) &mdash; Returns the current URL&#039;s protocol.
- [`getCurrentHost()`](#getCurrentHost) &mdash; Returns the current host.
- [`getCurrentQueryString()`](#getCurrentQueryString) &mdash; Returns the query string of the current URL.
- [`getArrayFromCurrentQueryString()`](#getArrayFromCurrentQueryString) &mdash; Returns an array mapping query paramater names with query parameter values for the current URL.
- [`getQueryStringFromParameters()`](#getQueryStringFromParameters) &mdash; Converts an an array of parameters name =&gt; value mappings to a query string.
- [`redirectToReferrer()`](#redirectToReferrer) &mdash; Redirects the user to the referrer.
- [`redirectToUrl()`](#redirectToUrl) &mdash; Redirects the user to the specified URL.
- [`getReferrer()`](#getReferrer) &mdash; Returns the HTTP_REFERER header, or false if not found.
- [`isLocalUrl()`](#isLocalUrl) &mdash; Returns true if the URL points to something on the same host, false if otherwise.

### `getCurrentUrl()` <a name="getCurrentUrl"></a>

Returns the current URL.

#### Signature

- It is a **public static** method.
- _Returns:_ eg, `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`
    - `string`

### `getCurrentUrlWithoutQueryString()` <a name="getCurrentUrlWithoutQueryString"></a>

Returns the current URL without the query string.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$checkTrustedHost`
- _Returns:_ eg, `&quot;http://example.org/dir1/dir2/index.php&quot;` if the current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`.
    - `string`

### `getCurrentUrlWithoutFileName()` <a name="getCurrentUrlWithoutFileName"></a>

Returns the current URL without the query string and without the name of the file being executed.

#### Signature

- It is a **public static** method.
- _Returns:_ eg, `&quot;http://example.org/dir1/dir2/&quot;` if the current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`.
    - `string`

### `getCurrentScriptPath()` <a name="getCurrentScriptPath"></a>

Returns the path to the script being executed.

#### Description

The script file name is not included.

#### Signature

- It is a **public static** method.
- _Returns:_ eg, `&quot;/dir1/dir2/&quot;` if the current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`
    - `string`

### `getCurrentScriptName()` <a name="getCurrentScriptName"></a>

Returns the path to the script being executed.

#### Description

Includes the script file name.

#### Signature

- It is a **public static** method.
- _Returns:_ eg, `&quot;/dir1/dir2/index.php&quot;` if the current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`
    - `string`

### `getCurrentScheme()` <a name="getCurrentScheme"></a>

Returns the current URL&#039;s protocol.

#### Signature

- It is a **public static** method.
- _Returns:_ `&#039;https&#039;` or `&#039;http&#039;`
    - `string`

### `getCurrentHost()` <a name="getCurrentHost"></a>

Returns the current host.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$default`
    - `$checkTrustedHost`
- _Returns:_ eg, `&quot;example.org&quot;` if the current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`
    - `string`

### `getCurrentQueryString()` <a name="getCurrentQueryString"></a>

Returns the query string of the current URL.

#### Signature

- It is a **public static** method.
- _Returns:_ eg, `&quot;?param1=value1&amp;param2=value2&quot;` if the current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;`
    - `string`

### `getArrayFromCurrentQueryString()` <a name="getArrayFromCurrentQueryString"></a>

Returns an array mapping query paramater names with query parameter values for the current URL.

#### Signature

- It is a **public static** method.
- _Returns:_ If current URL is `&quot;http://example.org/dir1/dir2/index.php?param1=value1&amp;param2=value2&quot;` this will return: ``` array( &#039;param1&#039; =&gt; string &#039;value1&#039;, &#039;param2&#039; =&gt; string &#039;value2&#039; ) ```
    - `array`

### `getQueryStringFromParameters()` <a name="getQueryStringFromParameters"></a>

Converts an an array of parameters name =&gt; value mappings to a query string.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$parameters`
- _Returns:_ eg. `&quot;param1=10&amp;param2[]=1&amp;param2[]=2&quot;`
    - `string`

### `redirectToReferrer()` <a name="redirectToReferrer"></a>

Redirects the user to the referrer.

#### Description

If no referrer exists, the user is redirected
to the current URL without query string.

#### Signature

- It is a **public static** method.
- It does not return anything.

### `redirectToUrl()` <a name="redirectToUrl"></a>

Redirects the user to the specified URL.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$url`
- It does not return anything.

### `getReferrer()` <a name="getReferrer"></a>

Returns the HTTP_REFERER header, or false if not found.

#### Signature

- It is a **public static** method.
- It can return one of the following values:
    - `string`
    - `Piwik\false`

### `isLocalUrl()` <a name="isLocalUrl"></a>

Returns true if the URL points to something on the same host, false if otherwise.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$url`
- _Returns:_ True if local; false otherwise.
    - `bool`
