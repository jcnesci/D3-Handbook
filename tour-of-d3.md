# A Soso Tour of D3.js

**Table of Contents**
- What is D3?
- The Basics
- Attaching Element to the Page
- Transforming the Data
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

Once you're used to it, D3 is great for taking a bunch of data and throwing it up on the page, to see what it looks like.

At Soso, we use it mainly for 2 things:**
- to quickly **see the data**, get a sense of its shape, and understand what deeper meaning it may hold or what "stories" could emerge from it.
	- this often leads us to the creation of a _dashboard_ to see and browse the data, which is also a great tool for the client.
- to quickly **create a prototype** of a more complex app that want to eventually create.
	- the prototype could be a 1st phase in a large project for which the final product is a robust C++ app.

## Attaching Element to the Page

_WIP: usually SVG, data-join pattern._

## Transforming the Data

_WIP: talk about my most used functions._

### Further Details

The guys at Bocoup wrote a great guide for parsing data in JS. Our parsing tactics are very very similar, so I recommend we use it as a guide for various ways to parse various things.

http://learnjsdata.com/

There are exceptions, however -- I prefer other tactics to theirs on occasion -- and they will be posted here. Feel free to do the same if you notice a better way to do things.

#### Exceptions:
- [Deep Cloning](http://learnjsdata.com/iterate_data.html):
	- for deep cloning, sometimes the lodash deepClone function doesn’t work or takes a really long time to complete. That’s why I’ve taken the habit of using this trick instead:

	```javascript
	patentObjects = JSON.parse(JSON.stringify( iPatentObjects ));
	```

	- it is faster and will in fact deep clone nested objects, IF they are basic types (ints, etc). But it won’t for custom types. **_WARNING: it will mess up Date objects._**
		- [Performance comparison](https://jsperf.com/lodash-copy-vs-json-stringify-parse)
		- Of course, if you know the structure of the object you anticipate cloning, the best solution is to build a custom cloning yourself ([see 2nd answer here](http://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-clone-an-object)) for your object properties, which gives the fastest result. See benchmark.
- [Sorting](http://learnjsdata.com/iterate_data.html):
	- if you have an array of complex objects that you want to reverse the sorting on (ex: it’s in ascending but you want descending) as they say d3.ascending/d3.descending won't work, but you can use the native JS Array.reverse() function:

	```javascript
	filteredPatentObjects.reverse();
	```

#### Benchmarking performance

_WIP: jsperf is cometimes useful_

## Next Steps

_WIP_

### Increasing performance

_WIP: canvas, webgl, pixi.js_

### 3D possibilities

_WIP: webgl, pixi.js, three.js, openVizConf videos about that_

### Using D3 with other frameworks

_WIP: MVC (react.js, link openVizConfVideo, Swizec Teller book), multiple file loading and concurrency with Queue.js, etc._
