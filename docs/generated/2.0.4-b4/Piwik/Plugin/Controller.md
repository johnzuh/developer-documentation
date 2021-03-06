<small>Piwik\Plugin\</small>

Controller
==========

Base class of all plugin Controllers.

Plugins that wish to add display HTML should create a Controller that either
extends from this class or from ControllerAdmin. Every public method in
the controller will be exposed as a controller method and can be invoked via
an HTTP request.

Learn more about Piwik's MVC system [here](/guides/mvc-in-piwik).

### Examples

**Defining a controller**

    class Controller extends \Piwik\Plugin\Controller
    {
        public function index()
        {
            $view = new View("@MyPlugin/index.twig");
            // ... setup view ...
            return $view->render();
        }
    }

**Linking to a controller action**

    <a href="?module=MyPlugin&action=index&idSite=1&period=day&date=2013-10-10">Link</a>

Properties
----------

This abstract class defines the following properties:

- [`$pluginName`](#$pluginname) &mdash; The plugin name, eg.
- [`$strDate`](#$strdate) &mdash; The value of the **date** query parameter.
- [`$date`](#$date) &mdash; The Date object created with ($strDate)[#strDate] or null if the requested date is a range.
- [`$idSite`](#$idsite) &mdash; The value of the **idSite** query parameter.
- [`$site`](#$site) &mdash; The Site object created with [$idSite](/api-reference/Piwik/Plugin/Controller#$idsite).

<a name="$pluginname" id="$pluginname"></a>
<a name="pluginName" id="pluginName"></a>
### `$pluginName`

The plugin name, eg.

`'Referrers'`.

#### Signature

- It is a `string` value.

<a name="$strdate" id="$strdate"></a>
<a name="strDate" id="strDate"></a>
### `$strDate`

The value of the **date** query parameter.

#### Signature

- It is a `string` value.

<a name="$date" id="$date"></a>
<a name="date" id="date"></a>
### `$date`

The Date object created with ($strDate)[#strDate] or null if the requested date is a range.

#### Signature

- It can be one of the following types:
    - [`Date`](../../Piwik/Date.md)
    - `null`

<a name="$idsite" id="$idsite"></a>
<a name="idSite" id="idSite"></a>
### `$idSite`

The value of the **idSite** query parameter.

#### Signature

- It is a `int` value.

<a name="$site" id="$site"></a>
<a name="site" id="site"></a>
### `$site`

The Site object created with [$idSite](/api-reference/Piwik/Plugin/Controller#$idsite).

#### Signature

- It is a [`Site`](../../Piwik/Site.md) value.

Methods
-------

The abstract class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`getDateParameterInTimezone()`](#getdateparameterintimezone) &mdash; Helper method that converts `"today"` or `"yesterday"` to the specified timezone.
- [`setDate()`](#setdate) &mdash; Sets the date to be used by all other methods in the controller.
- [`getDefaultAction()`](#getdefaultaction) &mdash; Returns the name of the default method that will be called when visiting: index.php?module=PluginName without the action parameter.
- [`renderReport()`](#renderreport) &mdash; Convenience method that creates and renders a ViewDataTable for a API method.
- [`getLastUnitGraph()`](#getlastunitgraph) &mdash; Returns a ViewDataTable object that will render a jqPlot evolution graph for the last30 days/weeks/etc.
- [`getLastUnitGraphAcrossPlugins()`](#getlastunitgraphacrossplugins) &mdash; Same as [getLastUnitGraph()](/api-reference/Piwik/Plugin/Controller#getlastunitgraph), but will set some properties of the ViewDataTable object based on the arguments supplied.
- [`getUrlSparkline()`](#geturlsparkline) &mdash; Returns a URL to a sparkline image for a report served by the current plugin.
- [`setMinDateView()`](#setmindateview) &mdash; Sets the first date available in the period selector's calendar.
- [`setMaxDateView()`](#setmaxdateview) &mdash; Sets the last date available in the period selector's calendar.
- [`setGeneralVariablesView()`](#setgeneralvariablesview) &mdash; Assigns variables to [View](/api-reference/Piwik/View) instances that display an entire page.
- [`setBasicVariablesView()`](#setbasicvariablesview) &mdash; Assigns a set of generally useful variables to a [View](/api-reference/Piwik/View) instance.
- [`setHostValidationVariablesView()`](#sethostvalidationvariablesview) &mdash; Checks if the current host is valid and sets variables on the given view, including:
- [`setPeriodVariablesView()`](#setperiodvariablesview) &mdash; Sets general period variables on a view, including:  - **displayUniqueVisitors** - Whether unique visitors should be displayed for the current                               period.
- [`redirectToIndex()`](#redirecttoindex) &mdash; Helper method used to redirect the current HTTP request to another module/action.
- [`getDefaultWebsiteId()`](#getdefaultwebsiteid) &mdash; Returns default site ID that Piwik should load.
- [`getDefaultDate()`](#getdefaultdate) &mdash; Returns default date for Piwik reports.
- [`getDefaultPeriod()`](#getdefaultperiod) &mdash; Returns default period type for Piwik reports.
- [`checkTokenInUrl()`](#checktokeninurl) &mdash; Checks that the token_auth in the URL matches the currently logged-in user's token_auth.
- [`getCalendarPrettyDate()`](#getcalendarprettydate) &mdash; Returns a prettified date string for use in period selector widget.
- [`getEvolutionHtml()`](#getevolutionhtml) &mdash; Calculates the evolution from one value to another and returns HTML displaying the evolution percent.

<a name="__construct" id="__construct"></a>
<a name="__construct" id="__construct"></a>
### `__construct()`

Constructor.

#### Signature


<a name="getdateparameterintimezone" id="getdateparameterintimezone"></a>
<a name="getDateParameterInTimezone" id="getDateParameterInTimezone"></a>
### `getDateParameterInTimezone()`

Helper method that converts `"today"` or `"yesterday"` to the specified timezone.

If the date is absolute, ie. YYYY-MM-DD, it will not be converted to the timezone.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$date` (`string`) &mdash;

      <div markdown="1" class="param-desc"> `'today'`, `'yesterday'`, `'YYYY-MM-DD'`</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$timezone` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The timezone to use.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It returns a [`Date`](../../Piwik/Date.md) value.

<a name="setdate" id="setdate"></a>
<a name="setDate" id="setDate"></a>
### `setDate()`

Sets the date to be used by all other methods in the controller.

If the date has to be modified, this method should be called just after
construction.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$date` ([`Date`](../../Piwik/Date.md)) &mdash;

      <div markdown="1" class="param-desc"> The new Date.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It returns a `void` value.

<a name="getdefaultaction" id="getdefaultaction"></a>
<a name="getDefaultAction" id="getDefaultAction"></a>
### `getDefaultAction()`

Returns the name of the default method that will be called when visiting: index.php?module=PluginName without the action parameter.

#### Signature

- It returns a `string` value.

<a name="renderreport" id="renderreport"></a>
<a name="renderReport" id="renderReport"></a>
### `renderReport()`

Convenience method that creates and renders a ViewDataTable for a API method.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$apiAction`

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>

<ul>
  <li>
    <div markdown="1" class="parameter">
    _Returns:_  (`string`|`void`) &mdash;
    <div markdown="1" class="param-desc">See `$fetch`.</div>

    <div style="clear:both;"/>

    </div>
  </li>
</ul>
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; if `$pluginName` is not an existing plugin or if `$apiAction` is not an existing method of the plugin&#039;s API.

<a name="getlastunitgraph" id="getlastunitgraph"></a>
<a name="getLastUnitGraph" id="getLastUnitGraph"></a>
### `getLastUnitGraph()`

Returns a ViewDataTable object that will render a jqPlot evolution graph for the last30 days/weeks/etc.

of the current period, relative to the current date.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$currentModuleName` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The name of the current plugin.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$currentControllerAction` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The name of the action that renders the desired report.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$apiMethod` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The API method that the ViewDataTable will use to get graph data.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It returns a [`ViewDataTable`](../../Piwik/Plugin/ViewDataTable.md) value.

<a name="getlastunitgraphacrossplugins" id="getlastunitgraphacrossplugins"></a>
<a name="getLastUnitGraphAcrossPlugins" id="getLastUnitGraphAcrossPlugins"></a>
### `getLastUnitGraphAcrossPlugins()`

Same as [getLastUnitGraph()](/api-reference/Piwik/Plugin/Controller#getlastunitgraph), but will set some properties of the ViewDataTable object based on the arguments supplied.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$currentModuleName` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The name of the current plugin.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$currentControllerAction` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The name of the action that renders the desired report.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$columnsToDisplay` (`array`) &mdash;

      <div markdown="1" class="param-desc"> The value to use for the ViewDataTable's columns_to_display config property.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$selectableColumns` (`array`) &mdash;

      <div markdown="1" class="param-desc"> The value to use for the ViewDataTable's selectable_columns config property.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$reportDocumentation` (`bool`|`string`) &mdash;

      <div markdown="1" class="param-desc"> The value to use for the ViewDataTable's documentation config property.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$apiMethod` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The API method that the ViewDataTable will use to get graph data.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It returns a [`ViewDataTable`](../../Piwik/Plugin/ViewDataTable.md) value.

<a name="geturlsparkline" id="geturlsparkline"></a>
<a name="getUrlSparkline" id="getUrlSparkline"></a>
### `getUrlSparkline()`

Returns a URL to a sparkline image for a report served by the current plugin.

The result of this URL should be used with the [sparkline()](/api-reference/Piwik/View#twig) twig function.

The current site ID and period will be used.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$action` (`string`) &mdash;

      <div markdown="1" class="param-desc"> Method name of the controller that serves the report.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$customParameters` (`array`) &mdash;

      <div markdown="1" class="param-desc"> The array of query parameter name/value pairs that should be set in result URL.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>

<ul>
  <li>
    <div markdown="1" class="parameter">
    _Returns:_  (`string`) &mdash;
    <div markdown="1" class="param-desc">The generated URL.</div>

    <div style="clear:both;"/>

    </div>
  </li>
</ul>

<a name="setmindateview" id="setmindateview"></a>
<a name="setMinDateView" id="setMinDateView"></a>
### `setMinDateView()`

Sets the first date available in the period selector's calendar.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$minDate` ([`Date`](../../Piwik/Date.md)) &mdash;

      <div markdown="1" class="param-desc"> The min date.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$view` ([`View`](../../Piwik/View.md)) &mdash;

      <div markdown="1" class="param-desc"> The view that contains the period selector.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="setmaxdateview" id="setmaxdateview"></a>
<a name="setMaxDateView" id="setMaxDateView"></a>
### `setMaxDateView()`

Sets the last date available in the period selector's calendar.

Usually this is just the "today" date
for a site (which varies based on the timezone of a site).

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$maxDate` ([`Date`](../../Piwik/Date.md)) &mdash;

      <div markdown="1" class="param-desc"> The max date.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$view` ([`View`](../../Piwik/View.md)) &mdash;

      <div markdown="1" class="param-desc"> The view that contains the period selector.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="setgeneralvariablesview" id="setgeneralvariablesview"></a>
<a name="setGeneralVariablesView" id="setGeneralVariablesView"></a>
### `setGeneralVariablesView()`

Assigns variables to [View](/api-reference/Piwik/View) instances that display an entire page.

The following variables assigned:

**date** - The value of the **date** query parameter.
**idSite** - The value of the **idSite** query parameter.
**rawDate** - The value of the **date** query parameter.
**prettyDate** - A pretty string description of the current period.
**siteName** - The current site's name.
**siteMainUrl** - The URL of the current site.
**startDate** - The start date of the current period. A [Date](/api-reference/Piwik/Date) instance.
**endDate** - The end date of the current period. A [Date](/api-reference/Piwik/Date) instance.
**language** - The current language's language code.
**config_action_url_category_delimiter** - The value of the `[General] action_url_category_delimiter`
                                           INI config option.
**topMenu** - The result of `MenuTop::getInstance()->getMenu()`.

As well as the variables set by [setPeriodVariablesView()](/api-reference/Piwik/Plugin/Controller#setperiodvariablesview).

Will exit on error.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$view` ([`View`](../../Piwik/View.md)) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It returns a `void` value.

<a name="setbasicvariablesview" id="setbasicvariablesview"></a>
<a name="setBasicVariablesView" id="setBasicVariablesView"></a>
### `setBasicVariablesView()`

Assigns a set of generally useful variables to a [View](/api-reference/Piwik/View) instance.

The following variables assigned:

**debugTrackVisitsInsidePiwikUI** - The value of the `[Debug] track_visits_inside_piwik_ui`
                                    INI config option.
**isSuperUser** - True if the current user is the super user, false if otherwise.
**hasSomeAdminAccess** - True if the current user has admin access to at least one site,
                         false if otherwise.
**isCustomLogo** - The value of the `[branding] use_custom_logo` INI config option.
**logoHeader** - The header logo URL to use.
**logoLarge** - The large logo URL to use.
**logoSVG** - The SVG logo URL to use.
**hasSVGLogo** - True if there is a SVG logo, false if otherwise.
**enableFrames** - The value of the `[General] enable_framed_pages` INI config option. If
                   true, [View::setXFrameOptions()](/api-reference/Piwik/View#setxframeoptions) is called on the view.

Also calls [setHostValidationVariablesView()](/api-reference/Piwik/Plugin/Controller#sethostvalidationvariablesview).

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$view` ([`View`](../../Piwik/View.md)) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="sethostvalidationvariablesview" id="sethostvalidationvariablesview"></a>
<a name="setHostValidationVariablesView" id="setHostValidationVariablesView"></a>
### `setHostValidationVariablesView()`

Checks if the current host is valid and sets variables on the given view, including:

- **isValidHost** - true if host is valid, false if otherwise
- **invalidHostMessage** - message to display if host is invalid (only set if host is invalid)
- **invalidHost** - the invalid hostname (only set if host is invalid)
- **mailLinkStart** - the open tag of a link to email the super user of this problem (only set
                      if host is invalid)

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$view` ([`View`](../../Piwik/View.md)) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="setperiodvariablesview" id="setperiodvariablesview"></a>
<a name="setPeriodVariablesView" id="setPeriodVariablesView"></a>
### `setPeriodVariablesView()`

Sets general period variables on a view, including:  - **displayUniqueVisitors** - Whether unique visitors should be displayed for the current                               period.

- **period** - The value of the **period** query parameter.
- **otherPeriods** - `array('day', 'week', 'month', 'year', 'range')`
- **periodsNames** - List of available periods mapped to their singular and plural translations.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$view` ([`View`](../../Piwik/View.md)) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; if the current period is invalid.

<a name="redirecttoindex" id="redirecttoindex"></a>
<a name="redirectToIndex" id="redirectToIndex"></a>
### `redirectToIndex()`

Helper method used to redirect the current HTTP request to another module/action.

This function will exit immediately after executing.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$moduleToRedirect` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The plugin to redirect to, eg. `"MultiSites"`.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$actionToRedirect` (`string`) &mdash;

      <div markdown="1" class="param-desc"> Action, eg. `"index"`.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$websiteId` (`int`|`null`) &mdash;

      <div markdown="1" class="param-desc"> The new idSite query parameter, eg, `1`.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$defaultPeriod` (`string`|`null`) &mdash;

      <div markdown="1" class="param-desc"> The new period query parameter, eg, `'day'`.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$defaultDate` (`string`|`null`) &mdash;

      <div markdown="1" class="param-desc"> The new date query parameter, eg, `'today'`.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$parameters` (`array`) &mdash;

      <div markdown="1" class="param-desc"> Other query parameters to append to the URL.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="getdefaultwebsiteid" id="getdefaultwebsiteid"></a>
<a name="getDefaultWebsiteId" id="getDefaultWebsiteId"></a>
### `getDefaultWebsiteId()`

Returns default site ID that Piwik should load.

_Note: This value is a Piwik setting set by each user._

#### Signature


<ul>
  <li>
    <div markdown="1" class="parameter">
    _Returns:_  (`bool`|`int`) &mdash;
    <div markdown="1" class="param-desc"></div>

    <div style="clear:both;"/>

    </div>
  </li>
</ul>

<a name="getdefaultdate" id="getdefaultdate"></a>
<a name="getDefaultDate" id="getDefaultDate"></a>
### `getDefaultDate()`

Returns default date for Piwik reports.

_Note: This value is a Piwik setting set by each user._

#### Signature


<ul>
  <li>
    <div markdown="1" class="parameter">
    _Returns:_  (`string`) &mdash;
    <div markdown="1" class="param-desc">`'today'`, `'2010-01-01'`, etc.</div>

    <div style="clear:both;"/>

    </div>
  </li>
</ul>

<a name="getdefaultperiod" id="getdefaultperiod"></a>
<a name="getDefaultPeriod" id="getDefaultPeriod"></a>
### `getDefaultPeriod()`

Returns default period type for Piwik reports.

#### Signature


<ul>
  <li>
    <div markdown="1" class="parameter">
    _Returns:_  (`string`) &mdash;
    <div markdown="1" class="param-desc">`'day'`, `'week'`, `'month'`, `'year'` or `'range'`</div>

    <div style="clear:both;"/>

    </div>
  </li>
</ul>

<a name="checktokeninurl" id="checktokeninurl"></a>
<a name="checkTokenInUrl" id="checkTokenInUrl"></a>
### `checkTokenInUrl()`

Checks that the token_auth in the URL matches the currently logged-in user's token_auth.

This is a protection against CSRF and should be used in all controller
methods that modify Piwik or any user settings.

**The token_auth should never appear in the browser's address bar.**

#### Signature

- It does not return anything.
- It throws one of the following exceptions:
    - [`Piwik\NoAccessException`](../../Piwik/NoAccessException.md) &mdash; If the token doesn&#039;t match.

<a name="getcalendarprettydate" id="getcalendarprettydate"></a>
<a name="getCalendarPrettyDate" id="getCalendarPrettyDate"></a>
### `getCalendarPrettyDate()`

Returns a prettified date string for use in period selector widget.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$period` ([`Period`](../../Piwik/Period.md)) &mdash;

      <div markdown="1" class="param-desc"> The period to return a pretty string for.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It returns a `string` value.

<a name="getevolutionhtml" id="getevolutionhtml"></a>
<a name="getEvolutionHtml" id="getEvolutionHtml"></a>
### `getEvolutionHtml()`

Calculates the evolution from one value to another and returns HTML displaying the evolution percent.

The HTML includes an up/down arrow and is colored red, black or
green depending on whether the evolution is negative, 0 or positive.

No HTML is returned if the current value and evolution percent are both 0.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$date` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The date of the current value.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$currentValue` (`int`) &mdash;

      <div markdown="1" class="param-desc"> The value to calculate evolution to.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$pastDate` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The date of past value.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$pastValue` (`int`) &mdash;

      <div markdown="1" class="param-desc"> The value in the past to calculate evolution from.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>

<ul>
  <li>
    <div markdown="1" class="parameter">
    _Returns:_  (`string`|`Piwik\Plugin\false`) &mdash;
    <div markdown="1" class="param-desc">The HTML or `false` if the evolution is 0 and the current value is 0.</div>

    <div style="clear:both;"/>

    </div>
  </li>
</ul>

