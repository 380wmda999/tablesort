tablesort
---

A small & simple sorting component for tables written in Javascript.

[![Build Status](https://travis-ci.org/tristen/tablesort.png?Zeqckz55oF1LjKHEqHT7)](https://travis-ci.org/tristen/tablesort)

### Basic usage

``` html
<script src='tablesort.min.js'></script>
<script>
  new Tablesort(document.getElementById('table-id'));
</script>
```
### Sort Types

* strings
* numbers
* currency
* Basic dates in `dd/mm/yy` or `dd-mm-yy` format. Years can be 4 digits. Days and Months can be 1 or 2 digits.
* Dot separated values. E.g. IP addresses or version numbers.
* Filesizes. E.g. "5.35 K", "10 MB", "12.45 GB", "4.67 TiB"

### Additional options

#### Ascending/Descending
You can pass in options as a second parameter. Currently one option is supported: `descending: true`. By default, sort is set to ascending.

``` js
new Tablesort(document.getElementById('table-id'), {
  descending: true
});
```

#### Exclude columns or rows
For columns or rows that do not require sorting, you can add a class of `no-sort` to a columns `th` or a `tr` element.
``` html
<th class='no-sort'>Name</th>

<tr class='no-sort'>
  <td>1</td>
  <td>Gonzo the Great</td>
  <td>12-2-70</td>
  <td>Radishes</td>
  <td>$0.63</td>
</tr>
```

#### Override data that is sorted on
Sometimes text inside cells is not normalized. Using a `data-sort` attribute you can use optional data to sort on.

``` html
<tr>
  <td>1</td>
  <td data-sort='1357656438'>01/08/13 @ 8:47:18am EST</td>
</tr>
<tr>
  <td>2</td>
  <td data-sort='1078673085'>3/7/2004 @ 9:24:45 EST</td>
</tr>
```

#### Default sort on tablesort initialization
It is possible to automatically sort the table once you create a Tablesort instance by adding `sort-default` class.

``` html
<th class='sort-default'>Name</th>
```

#### Refresh sort on appended data
Tablesort supports sorting when new data has been added. Simply call the refresh method.

``` js
var table = document.getElementById('table-id');
var sort = new Tablesort(table);

// Make some Ajax request to fetch new data and on success:
sort.refresh();
```

[See homepage for example](http://tristen.ca/tablesort/demo/#refresh)

### Node/Browserify

``` js
// npm install tablesort
var tablesort = require('tablesort');

tablesort(el, options);
```

### Ender support
Add `tablesort` as an internal chain method to your [Ender](https://github.com/ender-js/Ender/) compilation.

``` js
// ender add tablesort

$('.table').tablesort();
```

### Default style
Add the styling below to your CSS or roll with your own.

``` css
th.sort-header::-moz-selection { background:transparent; }
th.sort-header::selection      { background:transparent; } 
th.sort-header {
  cursor:pointer;
  }
th.sort-header::-moz-selection,
th.sort-header::selection {
  background:transparent;
  }
table th.sort-header:after {
  content:'';
  float:right;
  margin-top:7px;
  border-width:0 4px 4px;
  border-style:solid;
  border-color:#404040 transparent;
  visibility:hidden;
  }
table th.sort-header:hover:after {
  visibility:visible;
  }
table th.sort-up:after,
table th.sort-down:after,
table th.sort-down:hover:after {
  visibility:visible;
  opacity:0.4;
  }
table th.sort-up:after {
  border-bottom:none;
  border-width:4px 4px 0;
  }
```

### Building

Tablesort relies on [Grunt](http://gruntjs.com) as its build tool. Simply run `grunt` to package code
from any contributions you make to `src/tablesort.js` before submitting pull requests.

### Licence

MIT

### Tests

```sh
npm test
```

### Bugs?

[Create an issue](https://github.com/tristen/tablesort/issues)
