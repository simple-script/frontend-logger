[![license](https://img.shields.io/github/license/simple-script/simple-script.svg)]()
[![Github file size](https://img.shields.io/github/size/simple-script/simple-script/packages/dom/dist/dom.min.js.svg)]()

# Simple Script
Simple script is a javascript micro framework based on components, inspired by the great jQuery library.

| Minified & Gzipped | Minified | Uncompressed |
|--------------------|----------|--------------|
| **2K**                 | 7K       | 22K          |

## Compatibility
- STILL TESTING
- Should work in all modern browsers IE 9 +
- 'on' method does't work in Opera Mini when using the selector parameter

## Examples
**AddClass**
- Adds the specified class to all matched elements
````JS
document.find('div').addClass('first second third');
````

**After**
- Insert content after all matched elements
````JS
document.find('div').after('Hello World!'); // Text
document.find('div').after(document.createElement('div').outerHTML); // Element
````

**Append**
- Insert content to the end of all matched elements
````JS
document.find('h1.hello-world').append(document.createTextNode(' World!')); // Text node
document.find('h1.hello-world').append(document.createElement('div')); // Element
````

**Attr**
````JS
document.find('input').attr('type'); // Returns input type of the first matched element
document.find('input').attr('type', 'submit'); // Sets input type to all matched elements
document.find('input').attr({
    type: 'submit',
    disabled: true
});
````

**Before**
- Insert content before all matched elements
````JS
document.find('div').before('Hello World!'); // Text
document.find('div').before(document.createElement('div').outerHTML); // Element
````

**Children**
- Returns a list of child nodes of the first matched element
````JS
document.find('div').children();
````

**Clone**
````JS
document.find('div').clone(); // Creates a deep copy of the first matched element
document.find('div').clone(true); // Does not clone the child nodes
````

**CSS**
````JS
document.find('div').css('width'); // Returns style style property value
document.find('div').css('font-size', '18px'); // Sets style property value
document.find('div').css({
    'font-size': '18px',
    width: '88px'
});
````

**Data**
````JS
document.find('div').data('somedata') // Returns data attribute value
document.find('div').data('somedata', true) // Sets data attribute value
document.find('div').data({
    first: true,
    second: false
}) // Sets multiple data attributes
````

**Each**
- Iterate over NodeList, Object and Array
- Iterator is helpful object with the isFirst, isLast, isEven, isOdd properties
````JS
document.find('div').each(function (index, iterator) {
    this.remove();
});

['First', 'Second'].each(function (index, value, iterator) {
    // ...
});

{first: '1th value', second: '2th value'}.each(function (index, value, iterator) {
   // ...
});
````

**Eq**
````JS
document.find('button').eq(0); // Returns an element with specified index from NodeList, Array, Object
````

**Find**
- Works exactly the same as document.querySelectorAll but returns Element if there is only one node found
````JS
document.find('button');
````

**First**
- Returns first item fron NodeList, Array and Object
````JS
document.find('button').first();
['First', 'Second'].first();
{first: '1th value', second: '2th value'}.first();
````

**HasClass**
- Returns true if the first matched element has selected class
````JS
document.find('div').hasClass('someclass');
````

**Height**
````JS
document.find('div').height('100px'); // Sets height to all matched elements to 100px
document.find('div').height(); // Returns height of the first matched element (without margin, padding and border width)
````

**Html**
````JS
document.find('div').html(); // Returns html of the first matched element
document.find('div').html(document.createElement('p').outerHTML); // Sets html to all matched elements
````

**Inner Height**
````JS
document.find('div').innerHeight(); // Returns inner height of the first matched element (without margin and border width)
````

**Inner Width**
````JS
document.find('div').innerWidth(); // Returns inner width of the first matched element (without margin and border width)
````

**Is**
````JS
document.find('input').is(':checked'); // Returns true if checkbox element is checked otherwise returns false
document.find('option').is(':selected'); // Returns true if option element is selected otherwise returns false
document.find('div.first').is('.first'); // Returns boolean if element matches selector
````

**Last**
- Returns last item from NodeList, Array or Object
````JS
document.find('button').last();
['First', 'Second'].last();
{first: '1th value', second: '2th value'}.first();
````

**Next**
- Returns the next element after the first matched element
````JS
document.find('div').next();
````

**Off**
- Removes event listener from all matched elements. Is required to use named event handler.
````JS
function someHandler() {...}

document.find('button').off('click', someHandler);
````

**Offset**
- Returns ClientRect object of the first matched element
````JS
document.find('button').offset();
````

**On**
- Attaches an event listener to all matched elements
````JS
function someHandler() {...}

document.find('button').on('click', someHandler);
document.body.on('click', 'button', someHandler); // This works after ajax and on dynamically added elements
````

**OuterHeight**
- Returns outer height of the first matched element (with padding and border)
````JS
document.find('div').outerHeight();
document.find('div').outerHeight(true); // This will include margin
````

**OuterWidth**
- Returns outer width of the first matched element (with padding and border)
````JS
document.find('div').outerWidth();
document.find('div').outerWidth(true); // This will include margin
````

**Parent**
- Returns first parent of the first matched element
````JS
document.find('div').parent();
````

**Prepend**
- Insert content to the beginning of all matched elements
````JS
document.find('h1.hello-world').prepend(document.createTextNode('Hello')); // Text node
document.find('h1.hello-world').prepend(document.createElement('div')); // Element
````

**Prev**
- Returns the previous element before the first matched element
````JS
document.find('div').prev();
````

**Prop**
````JS
document.find('input').prop('checked'); // Returns property of the first matched element
document.find('input').prop('checked', true); // Sets property to all matched elements
document.find('input').prop({
    checked: true
});

function draggable(){...} // Inside function, you will always get sinhle Element object (this)

document.find('input').prop(draggable); // Allows you to create plugins and attach them to elements
````

**Ready**
- Executes callback when DOM is ready
````JS
document.ready(function () {...});
````

**Remove**
- Removes all matched elements
````JS
document.find('div').remove();
````

**RemoveAttr**
- Removes selected attribute from all matched elements
````JS
document.find('div').removeAttr('class id');
````

**RemoveClass**
- Removes selected class from all matched elements
````JS
document.find('div').removeClass('first second');
````

**RemoveData**
- Removes selected data attribute from all matched elements
````JS
document.find('div').removeData('first second');
````

**Text**
````JS
document.find('div').text(); // Returns text of the first matched element
document.find('div').text('Hello World!'); // Sets text to all matched elements
````

**ToggleClass**
- Adds or removes class from all matched elements
````JS
document.find('div').toggleClass('first second');
````

**Val**
````JS
document.find('input').val(); // Returns value of the first matched element
document.find('input').val('Some val'); // Sets value to all matched elements
````

**Width**
````JS
document.find('input').width(); // Returns width of the first matched element (without padding, border and margin)
document.find('input').width('100px'); // Sets width to all matched elements
````

**Wrap**
- Wraps an HTML structure around all matched elements
````JS
document.find('input').wrap(document.createElement('div').addClass('wrapper').outerHTML);
````

**Wrap inner**
- Wraps an HTML structure around the content of all matched elements
````JS
document.find('div').wrapInner(document.createElement('div').addClass('inner').outerHTML);
````
