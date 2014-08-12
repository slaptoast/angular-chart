# angular-chart [![Build Status](https://travis-ci.org/maxklenk/angular-chart.svg?branch=master)](https://travis-ci.org/maxklenk/angular-chart) [![Coverage Status](https://coveralls.io/repos/maxklenk/angular-chart/badge.png?branch=master)](https://coveralls.io/r/maxklenk/angular-chart?branch=master) [![Dependency Status](https://gemnasium.com/maxklenk/angular-chart.svg)](https://gemnasium.com/maxklenk/angular-chart)

angular-chart is a [AngularJS](https://github.com/angular/angular.js) directive, which is build on top of [c3](https://github.com/masayuki0812/c3) a [d3](https://github.com/mbostock/d3)-based chart library.

## Usage

You can get it from [Bower](http://bower.io/):
```sh
bower install angular-chart
```

Add everything to your index.html:
```html
<link rel="stylesheet" href="bower_components/c3/c3.css" />

<script src="bower_components/angular/angular.js"></script>
<script src="bower_components/d3/d3.js"></script>
<script src="bower_components/c3/c3.js"></script>
<script src="bower_components/angular-chart/angular-chart.js"></script>
```

And specify the directive in your module dependencies:
```javascript
angular.module('myApp', ['angularChart'])
```

Add the corresponding data in your controller:
```javascript
$scope.dataset = {
  'schema': [{
    'name': 'day',
    'type': 'datetime',
    'format': '%Y-%m-%dT%H:%M:%S'
  }, {
    'name': 'sales',
    'type': 'double'
  }, {
    'name': 'income',
    'type': 'double'
  }],
  'records': [{
    'day': '2013-01-02T00:00:00',
    'sales': 13461.295202,
    'income': 12365.053
  }]
};

$scope.options = {
  rows: [{
    name: 'income',
    type: 'bar'
  }, {
    name: 'sales'
  }],
  xAxis: {
    name: 'day',
    displayFormat: '%Y-%m-%d %H:%M:%S'
  }
};
```

Then you are ready to use the directive in your view:
```html
<div ng-controller="Controller">
  <angularchart
    dataset="dataset"
    options="options">
  </angularchart>
</div>
```

### Options

The following attributes define the chart itself and how to display the data.

---
#### rows : Object (required)
Defines the columns which should be displayed in the chart. Each row can contain the following:

---
##### rows.name : String (required)
The column name which identifies the value in each record.

---
##### rows.type : String
Possible values: `line, spline, bar, scatter`


---
#### type : String
Possible values: `line, spline, bar, scatter, bar, donut`
Defines which kind of chart should be rendered. The value will be the default for `rows.type`.


---
#### xAxis : Object (required)
Defines which column to use and how to display it:

---
##### xAxis.name : String (required)
The column name which identifies which value should be shown on the xAxis.

---
##### xAxis.displayFormat : String | Function
If the xAxis displays a timestamp the format of if can be defined by passing a String which follows the [Time Formatting of D3](https://github.com/mbostock/d3/wiki/Time-Formatting). Alternatively a custom function can be passed.
Sample: `function (x) { return x.getFullYear(); }`

---
#### groups : Object
Stacks bar together, [like in this example](http://c3js.org/samples/chart_bar_stacked.html).

---
#### subchart : Object
Defines the subchart.

---
##### show : boolean
If `true` a subchart for zooming is displayed.

---
#### selection : Object
Defines which Items can be selected and are currently selected.

---
##### selection.enabled : Boolean
Allows selection of chart elements. Default: `false` 

---
##### selection.multiple : Boolean
Allows selection of multiple chart elements if selection is enabled at all. Default: `false` 

---
##### selection.selected : Array
Contains an array with all selected points of the chart:

Multichart (line, spline, bar, scatter):
```
{
  value: VALUE,
  id: COLUMN_NAME,
  index: X_AXIS_INDEX
}
```

Pie-, Dountchart: _(Currently adding a selection in the Array will not add the selection in the chart)_
```
{
  id: COLUMN_NAME,
  values: [ALL_COLUMN_VALUES]
}
```


## Development [![Stories in Ready](https://badge.waffle.io/maxklenk/angular-chart.png?label=ready&title=Ready)](https://waffle.io/maxklenk/angular-chart) [![Gitter chat](https://badges.gitter.im/maxklenk/angular-chart.png)](https://gitter.im/maxklenk/angular-chart)


We use Karma and jshint to ensure the quality of the code. The easiest way to run these checks is to use grunt:
```sh
npm install -g bower grunt-cli
npm install
grunt
```


## Contributing

Please submit all pull requests the against develop branch. Make sure it passes the CI [![Build Status](https://travis-ci.org/maxklenk/angular-chart.svg?branch=develop)](https://travis-ci.org/maxklenk/angular-chart) and add tests to cover your code [![Coverage Status](https://coveralls.io/repos/maxklenk/angular-chart/badge.png?branch=develop)](https://coveralls.io/r/maxklenk/angular-chart?branch=develop). Thanks!

## Authors

**Max Klenk**

+ http://github.com/maxklenk



## Copyright and license

	The MIT License

	Copyright (c) 2014 Max Klenk

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in
	all copies or substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
	THE SOFTWARE.