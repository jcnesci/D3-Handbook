# D3-Handbook

## Examples

- Classic dataviz
	- http://www.nytimes.com/interactive/2012/02/13/us/politics/2013-budget-proposal-graphic.html
	- https://cryptowat.ch
	- http://www.nytimes.com/interactive/science/space/keplers-tally-of-planets.html
- Interactive art projects
	- http://drones.pitchinteractive.com/
	- http://www.therefugeeproject.org/
- Technically impressive
	- http://bost.ocks.org/mike/algorithms/

## What is D3?

[D3.js](http://d3js.org/) is a Javascript library.
D3 is for binding data to DOM elements.
It can be used for generating [basic charts](https://github.com/mbostock/d3/wiki/Gallery#basic-charts).
It can be used for [animating things](http://bl.ocks.org/mbostock/1256572).
It can be used for generating advanced charts too (like [maps](http://bl.ocks.org/r4vi/4185745), [force-layouts](http://bl.ocks.org/mbostock/929623), and many other [weird chart types](http://bost.ocks.org/mike/uberdata/)).

## Parsing Data

The guys at Bocoup wrote a great guide for parsing data in JS. Our parsing tactics are very very similar, so I recommend we use it as a guide for various ways to parse various things.

http://learnjsdata.com/

There are exceptions, however -- I prefer other tactics to theirs on occasion -- and they will be posted here. Feel free to do the same if you notice a better way to do things.

### Exceptions:
- [Deep Cloning] (http://learnjsdata.com/iterate_data.html):
	- for deep cloning, sometimes the lodash deepClone function doesn’t work or takes a really long time to complete. That’s why I’ve taken the habit of using this trick instead:
```javascript
patentObjects = JSON.parse(JSON.stringify( iPatentObjects ));
```

	it is faster and will in fact deep clone nested objects, IF they are basic types (ints, etc). But it won’t for custom types.
		- Performance comparison:
			- https://jsperf.com/lodash-copy-vs-json-stringify-parse
			- Of course, if you know the structure of the object you anticipate cloning, the best solution is to build a custom cloning yourself ([see 2nd answer](http://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-clone-an-object)) for your object properties, which gives the fastest result. See benchmark.
	- [Sorting](http://learnjsdata.com/iterate_data.html):
	- if you have an array of complex objects that you want to reverse the sorting on (ex: it’s in ascending but you want descending) as they say d3.ascending/d3.descending won't work, but you can use the native JS Array.reverse() function:
```javascript
filteredPatentObjects.reverse();
```


## Benchmarking performance
