<small>Piwik\DataTable\Filter</small>

AddColumnsProcessedMetricsGoal
==============================

Adds the following columns to a DataTable using metrics that already exist:  - **revenue_per_visit**: total goal and ecommerce revenue / nb_visits - **goal_%idGoal%_conversion_rate**: the conversion rate.

Description
-----------

There will be one of
                                     these columns for each goal that exists
                                     for the site.
- **goal_%idGoal%_nb_conversions**: the number of conversions. There will be one of
                                    these columns for each goal that exists
                                    for the site.
- **goal_%idGoal%_revenue_per_visit**: goal revenue / nb_visits. There will be one of
                                       these columns for each goal that exists
                                       for the site.
- **goal_%idGoal%_revenue**: goal revenue. There will be one of
                             these columns for each goal that exists
                             for the site.
- **goal_%idGoal%_avg_order_revenue**: goal revenue / number of orders or abandoned
                                       carts. Only for ecommerce order and abandoned cart
                                       reports.
- **goal_%idGoal%_items**: number of items. Only for ecommerce order and abandoned cart
                           reports.

Adding the **filter_update_columns_when_show_all_goals** query parameter to
an API request will trigger the execution of this Filter.

Note: This filter must be called before [ReplaceColumnNames](#) is called.


Constants
---------

This class defines the following constants:

- [`GOALS_MINIMAL_REPORT`](#GOALS_MINIMAL_REPORT) &mdash; Process main goal metrics: conversion rate, revenue per visit
- [`GOALS_OVERVIEW`](#GOALS_OVERVIEW) &mdash; Process main goal metrics, and conversion rate per goal
- [`GOALS_FULL_TABLE`](#GOALS_FULL_TABLE) &mdash; Process all goal and per-goal metrics

Methods
-------

The class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`filter()`](#filter) &mdash; Adds the processed metrics.

### `__construct()` <a name="__construct"></a>

Constructor.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$table` ([`DataTable`](../../../Piwik/DataTable.md))
    - `$enable`
    - `$processOnlyIdGoal`
- It does not return anything.

### `filter()` <a name="filter"></a>

Adds the processed metrics.

#### Description

See [AddColumnsProcessedMetrics](#AddColumnsProcessedMetrics) for
more information.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$table`
- It does not return anything.
