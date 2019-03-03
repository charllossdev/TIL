
# jQuery

Why jQuery?


## Array


### $.inArray()

Checks if a value exists in an 'Array'

```javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log($.inArray("Banana", fruits)); // 0
console.log($.inArray("Orange", fruits)); // 1
console.log($.inArray("Apple", fruits)); // 2
console.log($.inArray("Mango", fruits)); // 3
console.log($.inArray("Melon", fruits)); // -1

var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log( $.inArray("Banana", fruits) >=0 ); // true
console.log( $.inArray("Orange", fruits) >=0 ); // true
console.log( $.inArray("Melon", fruits) >=0 ); // false
```

## Selector

### $.on()

http://api.jquery.com/on/

> .on(events[, selector][,data], handler)

Attach an event handler function for one or move events to the selected elements

```JavaScript
$( "#dataTable tbody tr" ).on( "click", function() {
  console.log( $( this ).text() );
});

// dataTable tbody > tr "SELECT Event Function"
$( "#dataTable tbody" ).on( "click", "tr", function() {
  console.log( $( this ).text() );
});
```

#### Multi Event Handler Function
```JavaScript
$("#container") on ( {
  "change"  : function(){...},
  "blur"    : function(){...},
  "click"   : function(){...}
}, ".foo");
```
