react-highcharts
================

[![Build Status](https://travis-ci.org/kirjs/react-highcharts.svg?branch=master)](https://travis-ci.org/kirjs/react-highcharts)

Highcharts component for react.

## Demos
[react-highcharts](http://kirjs.github.io/react-highcharts/) 
| [react-highcharts/more](http://kirjs.github.io/react-highcharts/more.html)
| [react-highcharts/highstock](http://kirjs.github.io/react-highcharts/highstock.html)
| [react-highcharts/highmaps](http://kirjs.github.io/react-highcharts/highmaps.html)

You can find the full code for the examples [here](https://github.com/kirjs/react-highcharts/tree/master/demo)

To run the demo:

 1. run:
    ```bash
    git clone https://github.com/kirjs/react-highcharts.git
    npm install
    npm run demo
    ```
 2. Point your browser at http://localhost:8080

## Installation
```bash
npm install react-highcharts --save
```

## Usage
#### Webpack/Browserify
```bash
npm install react-highcharts highcharts react --save
```

```jsx
var React = require('react');
var ReactHighcharts = require('react-highcharts'); // Expects that Highcharts was loaded in the code. 

var config = {
  /* HighchartsConfig */
};
React.render(<ReactHighcharts config = {config}></ReactHighcharts>, document.body);
```

#### Accessing Highcharts API After Render
For access to methods & properties from the Highcharts library you can use `ReactHighcharts.Highcharts`.
For example, the Highcharts options are available via `ReactHighcharts.Highcharts.getOptions()`.

Highcharts provides an API for manipulating a chart after the initial render. See the **Methods and Properties** in [the documentation](http://api.highcharts.com/highcharts). Here's how you access it:

```jsx
class MyComponent extends React.Component {
  componentDidMount() {
    let chart = this.refs.chart.getChart();
    chart.series[0].addPoint({x: 10, y: 12});
  }

  render() {
    return <ReactHighcharts config={config} ref="chart"></ReactHighcharts>;
  }
}
```

#### Limiting Highchart Rerenders
Rerendering a highcharts graph is expensive. You can pass in a `isPureConfig` option to the `ReactHighcharts` component, which will keep the highcharts graph from being updated so long as the provided `config` is [referentially equal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators) to its previous value.

#### Rendering on the server with node
See this [recipe](https://github.com/kirjs/react-highcharts/blob/master/recipes.md#rendering-react-highcharts-on-node)

## Using highmaps
```javascript
var ReactHighmaps = require('react-highcharts/ReactHighmaps');
```

* see [the demo](http://kirjs.github.io/react-highcharts/highmaps.html)

## Using highstock ([demo](http://kirjs.github.io/react-highcharts/highstock.html))
```javascript
var ReactHighstock = require('react-highcharts/ReactHighstock')
```

## Using highcharts modules/add-ons like exporting, data, etc.
Use `highcharts-more` npm package. 
```javascript
var ReactHighcharts = require('react-highcharts')
require('highcharts-more')(ReactHighcharts.Highcharts)
```

You can find the full list list [here](https://github.com/kirjs/publish-highcharts-modules/blob/master/modules.md)
* see [the demo](http://kirjs.github.io/react-highcharts/more.html)

## For Contributors
#### Running tests
Run `npm tests`

#### Running demo
Run `npm run demo`

#### Using with React@0.13 
```bash
npm install react-highcharts@^3.0.0 --save
```
