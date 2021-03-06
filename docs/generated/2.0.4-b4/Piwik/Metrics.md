<small>Piwik\</small>

Metrics
=======

This class contains metadata regarding core metrics and contains several related helper functions.

Of note are the `INDEX_...` constants. In the database, metric column names
in [DataTable](/api-reference/Piwik/DataTable) rows are stored as integers to save space. The integer
values used are determined by these constants.

Properties
----------

This class defines the following properties:

- [`$mappingFromIdToName`](#$mappingfromidtoname)
- [`$mappingFromIdToNameGoal`](#$mappingfromidtonamegoal)
- [`$mappingFromNameToId`](#$mappingfromnametoid)

<a name="$mappingfromidtoname" id="$mappingfromidtoname"></a>
<a name="mappingFromIdToName" id="mappingFromIdToName"></a>
### `$mappingFromIdToName`

#### Signature

- Its type is not specified.


<a name="$mappingfromidtonamegoal" id="$mappingfromidtonamegoal"></a>
<a name="mappingFromIdToNameGoal" id="mappingFromIdToNameGoal"></a>
### `$mappingFromIdToNameGoal`

#### Signature

- Its type is not specified.


<a name="$mappingfromnametoid" id="$mappingfromnametoid"></a>
<a name="mappingFromNameToId" id="mappingFromNameToId"></a>
### `$mappingFromNameToId`

#### Signature

- Its type is not specified.


Methods
-------

The class defines the following methods:

- [`getVisitsMetricNames()`](#getvisitsmetricnames)
- [`getMappingFromIdToName()`](#getmappingfromidtoname)
- [`getDefaultMetricTranslations()`](#getdefaultmetrictranslations)
- [`getDefaultMetrics()`](#getdefaultmetrics)
- [`getDefaultProcessedMetrics()`](#getdefaultprocessedmetrics)
- [`getReadableColumnName()`](#getreadablecolumnname)
- [`getMetricIdsToProcessReportTotal()`](#getmetricidstoprocessreporttotal)
- [`getDefaultMetricsDocumentation()`](#getdefaultmetricsdocumentation)
- [`getPercentVisitColumn()`](#getpercentvisitcolumn)

<a name="getvisitsmetricnames" id="getvisitsmetricnames"></a>
<a name="getVisitsMetricNames" id="getVisitsMetricNames"></a>
### `getVisitsMetricNames()`

#### Signature

- It does not return anything.

<a name="getmappingfromidtoname" id="getmappingfromidtoname"></a>
<a name="getMappingFromIdToName" id="getMappingFromIdToName"></a>
### `getMappingFromIdToName()`

#### Signature

- It does not return anything.

<a name="getdefaultmetrictranslations" id="getdefaultmetrictranslations"></a>
<a name="getDefaultMetricTranslations" id="getDefaultMetricTranslations"></a>
### `getDefaultMetricTranslations()`

#### Signature

- It does not return anything.

<a name="getdefaultmetrics" id="getdefaultmetrics"></a>
<a name="getDefaultMetrics" id="getDefaultMetrics"></a>
### `getDefaultMetrics()`

#### Signature

- It does not return anything.

<a name="getdefaultprocessedmetrics" id="getdefaultprocessedmetrics"></a>
<a name="getDefaultProcessedMetrics" id="getDefaultProcessedMetrics"></a>
### `getDefaultProcessedMetrics()`

#### Signature

- It does not return anything.

<a name="getreadablecolumnname" id="getreadablecolumnname"></a>
<a name="getReadableColumnName" id="getReadableColumnName"></a>
### `getReadableColumnName()`

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$columnIdRaw`

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="getmetricidstoprocessreporttotal" id="getmetricidstoprocessreporttotal"></a>
<a name="getMetricIdsToProcessReportTotal" id="getMetricIdsToProcessReportTotal"></a>
### `getMetricIdsToProcessReportTotal()`

#### Signature

- It does not return anything.

<a name="getdefaultmetricsdocumentation" id="getdefaultmetricsdocumentation"></a>
<a name="getDefaultMetricsDocumentation" id="getDefaultMetricsDocumentation"></a>
### `getDefaultMetricsDocumentation()`

#### Signature

- It does not return anything.

<a name="getpercentvisitcolumn" id="getpercentvisitcolumn"></a>
<a name="getPercentVisitColumn" id="getPercentVisitColumn"></a>
### `getPercentVisitColumn()`

#### Signature

- It does not return anything.

