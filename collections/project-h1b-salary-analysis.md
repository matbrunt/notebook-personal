<App {...state}
startTicker={::this.startTicker} startParticles={::this.startParticles} stopParticles={::this.stopParticles} updateMousePos={::this.updateMousePos}
/>

In case you were wondering, that {::this.startTicker} syntax comes from ES2016. It’s equivalent to {this.startTicker.bind(this)}. Enable stage-0 in your Babel config to use it.


*D3 creating a rectangle*

	d3.select("svg")
	  .append("g")
	  .attr("transform", "translate(50, 20)")
	  .append("rect")
	  .attr("width", 100)
	  .attr("height", 200);

*Same code in React*

	render() {
	  return (
	    <svg>
	      <g transform="translate(50, 20)"> <rect width="100" height="200" />
	      </g>
	    </svg>
	  );
	}

https://github.com/Swizec/react-d3js-step-by-step/tree/master/src

componentWillMount runs just before React inserts the component into the DOM
componentWillUpdate runs just before React updates the DOM component.
Both get called on any prop change or `setState` call.

All d3 layouts let you define a `.value()` which lets the layout know how to get the correct value from your data
`.value((d) => d.some.deep.value)`.

Scales are mathmatical functions that map a domain to a range.
Domain tells the scale the extent of the data, range tells the scale the extent of our drawing area.

A linear scale with domain[0, 100] and a range [1, 2] for scale(50) will return 1.5.

Scales don't care about the object they are applied to, they only care about mapping a domain to a range.

[Changes between D3 v3 and v4](https://github.com/d3/d3/blob/master/CHANGES.md)
[D3 v4 API reference](https://github.com/d3/d3/blob/master/API.md)

Median household salary is a good proxy for cost of living in an area.

What is the best city to live in for an H1B visa? Answer this by looking for the highest average individual salary above local household median.