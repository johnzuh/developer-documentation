<small>Piwik\DataTable\Filter</small>

Limit
=====

Delete all rows from the table that are not in the given offset -&gt; offset+limit range.

Description
-----------

**Basic example usage**

    // delete all rows from 5 -&gt; 15
    $dataTable-&gt;filter(&#039;Limit&#039;, array(5, 10));


Methods
-------

The class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`filter()`](#filter) &mdash; See [Limit](#).

### `__construct()` <a name="__construct"></a>

Constructor.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$table` ([`DataTable`](../../../Piwik/DataTable.md))
    - `$offset`
    - `$limit`
    - `$keepSummaryRow`
- It does not return anything.

### `filter()` <a name="filter"></a>

See [Limit](#).

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$table`
- It does not return anything.
