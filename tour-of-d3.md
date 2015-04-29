# A Soso Tour of D3.js

**Table of Contents**
- What is D3?
- The Basics
- Attaching Elements to the Page
- Transforming the Data
- Transitioning & Animating the Data
- Graphs built into D3
- Performance Limits
- Next Steps


## What is D3?

[D3.js](http://d3js.org/) is a Javascript library.
D3 is for binding data to DOM elements.
It can be used for generating [basic charts](https://github.com/mbostock/d3/wiki/Gallery#basic-charts).
It can be used for [animating things](http://bl.ocks.org/mbostock/1256572).
It can be used for generating quite advanced charts too (like [maps](http://bl.ocks.org/r4vi/4185745), [force-layouts](http://bl.ocks.org/mbostock/929623), and many other [weird chart types](http://bost.ocks.org/mike/uberdata/)).

As I explain things, I will often refer to Scott Murray's fantastic (and free!) online book, [found here](http://chimera.labs.oreilly.com/books/1230000000345/index.html).


## The Basics

D3 is many things, but also isn't many things.
- It can **load data** files in the browser so you can use it for your graphs/etc.
- It can **attach** elements to the browser's DOM based on that data.
- It can **transform** you data in many ways so it's ready to produce graphs.
- It can **transition** your elements between states, in reaction to user input, and **animate** those elements.

At Soso, we use it mainly for 2 things:
- to quickly **see the data**, get a sense of its shape, and understand what deeper meaning it may hold or what "stories" could emerge from it.
	- this often leads us to the creation of a _dashboard_ to see and browse the data, which is also a great tool for the client.
- to quickly **create a prototype** of a more complex app that want to eventually create.
	- the prototype could be a 1st phase in a large project for which the final product is a robust C++ app.

Once you're used to it, D3 really is great for taking a bunch of data and throwing it up on the page, to see what it looks like.


## Attaching Elements to the Page

_WIP: usually SVG, data-join pattern._


## Transforming the Data

_WIP: talk about my most used functions. My must-have libraries (underscore, moment)._

### Further Details

The guys at Bocoup wrote a great guide for parsing data in JS. Our parsing tactics are very very similar, so I recommend we use it as a guide for various ways to parse various things.

http://learnjsdata.com/

There are exceptions, however -- I prefer other tactics to theirs on occasion -- and they will be posted here. Feel free to do the same if you notice a better way to do things.

#### Exceptions:
- [Deep Cloning](http://learnjsdata.com/iterate_data.html):
	- for collection of objects with only basic property types (ints, strings, etc -- but not Date objs, and other complex types), that can also be nested (ie. "deep"), use:

	```javascript
	var deepPrimitiveCopy = JSON.parse(JSON.stringify( dataObject ));
	```

	- for collection with complex property types, that is not nested (ie. not "deep") use lodash:

	```javascript
	var shallowCopy = _.clone(dataObject);
	```

	- for collection with complex property types, that is nested (ie. "deep") use lodash:

	```javascript
	var deepCopy = _.clone(dataObject, true);
	// or
	var deepCopy = _.cloneDeep(dataObject);
	```

	- NB:
		- [Performance comparison](https://jsperf.com/lodash-copy-vs-json-stringify-parse)
		- [All-time quickest cloning method](http://stackoverflow.com/a/5344074/2543345) is to write your own custom cloner, if you know in advance what the structure of the data will be like.

- [Sorting](http://learnjsdata.com/iterate_data.html):
	- if you have an array of complex objects that you want to reverse the sorting on (ex: it’s in ascending but you want descending) as they say d3.ascending/d3.descending won't work, but you can use the native JS Array.reverse() function:

	```javascript
	filteredPatentObjects.reverse();
	```

#### Benchmarking performance

_WIP: jsperf is cometimes useful_


## Transitioning & Animating the Data

_WIP_


## Graphs built into D3

_WIP_


## Performance Limits

_WIP_


## Next Steps

_WIP_

### Increasing performance

_WIP: canvas, webgl, pixi.js_

### 3D possibilities

_WIP: webgl, pixi.js, three.js, openVizConf videos about that_

### Using D3 with other frameworks

_WIP: MVC (react.js, link openVizConfVideo, Swizec Teller book), multiple file loading and concurrency with Queue.js, etc._

### Potentially useful libraries

_WIP: MISO, NVD3, etc? see scott murray's book for more._

