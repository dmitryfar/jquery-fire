jquery-fire
===========

JQuery event messaging like in AlloyUI.




**jQuery.fire()** or **$.fire()**

**jQuery.on()** or **$.on()**


## Fire

#### Fire simple event

```javascript
$.fire("simpleEvent");
```

#### Fire data event

```javascript
$.fire("testEvent", "textstring");
$.fire("testEvent", {a: ["n=1", "m=1"]});
$.fire("testEvent", ["n=1", "m=1", 234]);
```

#### Fire multiple data event

```javascript
$.fire("multpleDataEvent", "n1", "n2", "n3");
```

#### Fire once event

```javascript
jQuery.fireOnce("fireOnceEvent", {"n": "1"});
```

## Catch

#### Catch simple event

```javascript
jQuery.on("simpleEvent", function(event) {
	console.log("simple event", event._type);
});
```

#### Catch data event

```javascript
jQuery.on("testEvent", function(event, data) {
	console.log("%o: %o, data: %o", this._type, event, data);
	if (typeof data == 'function') {
		data.call(this, "WORLD", "!!!");
		data.apply(this, ["my ", "friend."]);
	} else {
		// something else
	}
});

var abcFnc = function(text1, text2){
	var event = this;
	console.log("-- Hello, " + text1 + text2 + " --");
};

$.fire("testEvent", abcFnc);
```

#### Catch multiple data event

```javascript
jQuery.on("multpleDataEvent", function(event, data1, data2, data3, data4) {
	console.log("%o: %o, data1: %o, data2: %o, data3: %o, data4: %o", this._type, event, data1, data2, data3, data4);
});
```
or 
```javascript
jQuery.on("multpleDataEvent", function(event) {
	console.log("%o: %o, details: %o", event._type, event, event.details);
});
```

#### Catch once
With many fires it wil be catched just once

```javascript
jQuery.on("fireOnceEvent", function(event, data) {
	console.log("%o, event.n: %o, data.n: %o", this._type, event.n, data.n);
});

jQuery.fireOnce("fireOnceEvent", {"n": "1"});
jQuery.fireOnce("fireOnceEvent", {"n": "2"});
jQuery.fireOnce("fireOnceEvent", {"n": "3"});
```


