# Framer JS notebook

My self learning notes on using Framer with plain JS instead of CoffeeScript.

Quick clarification:
- **Framer** is the MacOS-exclusive software that you've surely heard about.
- The **Framer Library** is the engine running behind the scenes. It's an open source project and that's what these notes are about.

## Who is this for?
- Anyone who feels comfortable with Framer and curious to try it with plain JS flavor.
- Anyone wanting to try Framer on Windows. However, if you want to use CoffeeScript, then check [this guide](http://www.prototypingwithframer.com/framer-on-windows-with-atom/).
- Anyone who enjoys tinkering with prototyping tools.

## Set up the Framer Library

### [~~~ Download ~~~](https://builds.framerjs.com/latest/Framer.zip)
^ That's the always-up-to-date & stable build, directly from the official 'builds' subdomain.

1. Unzip the file and you'll get this folder:
```
Project/
  framer/
  images/
  app.js
  index.html
```
2. Open **index.html** in a WebKit browser.

3. **app.js** is your playground. Enjoy!

Tip: Set your workspace just like Framer.

![](workspace.jpg)

# Notes and snippets

#### ToDo: Add more examples

- **[Console Log](#console-log)**
- **[Scroll Component](#scroll-component)**
- **[Page Component](#page-component)**
- **[Flow Component](#flow-component)**


## Console Log

> Framer (CoffeeScript)
```javascript
print "Check, please"
```
> Framer Library (JS)
```javascript
console.log("Check, please");
```

## Scroll Component
> Framer Library (JS)
```javascript
// Scroll Component Example
Framer.Extras.Hints.disable()

app = new Layer({
	name: "App",
	width: 750, height: 1334,
	scale: 0.5
})
app.center()

myScroll = new ScrollComponent({
	width: 750, height: 1334,
	parent: app,
	scrollHorizontal: false
})

placeholderContent = new Layer({
	width: 750,
	height: 2500,
	backgroundColor: "skyblue",
	parent: myScroll.content
})

myScroll.on(Events.Move, function(){
	console.log("Scroll: " + myScroll.scrollY)
})
```
[Back to top](#notes-and-snippets)

## Page Component
> Framer Library (JS)
```javascript
// Page Component
var pageCount = 8;
var gutter = 60;

app = new Layer({
	name: "App",
	width: 750, height: 1334,
	scale: 0.5,
	backgroundColor: null
})
app.center()

myPageComponent = new PageComponent({
	width: 750, height: 1334,
	parent: app,
	scrollVertical: false,
	clip: false
})

for (var i = 0; i < pageCount; i++) {
	page = new Layer({
		name: "Page " + i,
		size: myPageComponent.size,
		x: (myPageComponent.width + gutter) * i,
		backgroundColor: "#00AAFF",
		hueRotate: i * 20,
		parent: myPageComponent.content
	});
	page.onClick(function() {
		console.log("Clicked: " + this.name);
		myPageComponent.snapToPage(this);
	});
}
```
[Back to top](#notes-and-snippets)

## Flow Component
> Framer Library (JS)
```javascript
// Flow Component Example
Framer.Extras.Hints.disable()

app = new Layer({
	name: "App",
	width: 750, height: 1334,
	scale: 0.5,
	backgroundColor: null
})
app.center()

screenA = new Layer({
	size: app.size,
	backgroundColor: "#00AAFF",
	parent: app
});

screenB = new Layer({
	size: app.size,
	backgroundColor: "#FFCC33",
	image: Utils.randomImage(),
	parent: app
});

// States
screenA.states = {
	scaleBack: {
		scale: 0.95
	},
	scaleDefault: {
		scale: 1
	}
};
screenA.states.animationOptions = {
	curve: "ease-in-out",
	time: 0.2
}

// Flow
flow = new FlowComponent({
	size: app.size,
	parent: app
})

flow.showNext(screenA);

// Events
screenA.onClick(function() {
	screenA.animate("scaleBack");
	flow.showOverlayBottom(screenB);
	console.log("Show Screen B");
});

screenB.onClick(function() {
	screenA.animate("scaleDefault");
	flow.showPrevious();
	console.log("Show Screen A again");
});
```
[Back to top](#notes-and-snippets)


---

I'll continue updating these notes.

I'm using the good old ES5 for now, but that's one of the goals of this experiment: **to try to replicate prototypes on ES5 and ES6. This is just for fun & learning.**

[@72mena](https://twitter.com/72mena)