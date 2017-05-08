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

## Notes & Snippets

#### ToDo: Add lots of examples

Console Log Example

> Framer (CoffeeScript)
```javascript
print "Check, please"
```
> Framer Library (JS)
```javascript
console.log("Check, please");
```

---

I'll continue updating these notes.

I'm using the good old ES5 for now, but that's one of the goals of this experiment: **to try to replicate prototypes on ES5 and ES6. This is just for fun & learning.**

[@72mena](https://twitter.com/72mena)