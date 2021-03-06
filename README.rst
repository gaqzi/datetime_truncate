==================
datetime_truncate
==================

This module truncates a datetime object to the level of precision that
you specify, making everything higher than that zero (or one for day
and month).

It is based on PostgreSQL's DATE_TRUNC_.

Installation:
-------------

You can install from pypi!

.. code-block::

    pip install datetime_truncate


Usage:
------

.. code-block::

    >>> from datetime_truncate import truncate
    >>> truncate(datetime(2012, 2, 4, 12, 24, 50, 234), 'second')
    datetime(2012, 2, 4, 12, 24, 50)
    >>> truncate(datetime(2012, 2, 4, 12, 24, 50), 'minute')
    datetime(2012, 2, 4, 12, 24)
    >>> truncate(datetime(2012, 2, 4, 12, 24, 50), '5_minute')
    datetime(2012, 2, 4, 12, 20)
    >>> truncate(datetime(2012, 2, 4, 12, 24, 50), '19_minute')
    datetime(2012, 2, 4, 12, 19)
    >>> truncate(datetime(2012, 2, 4, 12, 24), 'hour')
    datetime(2012, 2, 4, 12)
    >>> truncate(datetime(2012, 2, 4, 12, 24), 'day')
    datetime(2012, 2, 4)
    >>> truncate(datetime(2012, 2, 4, 12, 24), 'week')
    datetime(2012, 1, 30)
    >>> truncate(datetime(2012, 2, 4, 12, 24), 'month')
    datetime(2012, 2, 1)
    >>> truncate(datetime(2012, 2, 4, 12, 24), 'quarter')
    datetime(2012, 1, 1)
    >>> truncate(datetime(2012, 8, 18, 12, 25), 'half_year')
    datetime(2012, 7, 1)
    >>> truncate(datetime(2012, 8, 18, 12, 25), 'year')
    datetime(2012, 1, 1)

There are also sugar functions available on the form:

* `truncate_second`
* `truncate_minute`
* `truncate_nth_minute`
* `truncate_hour`
* `truncate_day`
* `truncate_week`
* `truncate_month`
* `truncate_quarter`
* `truncate_half_year`
* `truncate_year`

Changes
=======

`1.1.0`_ - 2017-10-19
---------------------

* Added truncate to nth minute of the hour, so if you want to
  truncate to every third minute you do: `truncate(dt, '3_minute')` or
  with some more sugar on top; `truncate_nth_minute(dt, 3)`
* Fixed bugs with truncate quarter and half_year, thanks `@thegrymek`_!

.. _1.1.0: https://github.com/gaqzi/datetime_truncate/compare/1.0.1...1.1.0
.. _@thegrymek: https://github.com/thegrymek

.. _DATE_TRUNC: http://www.postgresql.org/docs/9.1/static/functions-datetime.html#FUNCTIONS-DATETIME-TRUNC
