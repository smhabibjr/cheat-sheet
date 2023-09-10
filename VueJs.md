## Table of Contents

- [Basics and core concepts](#Basics-and-core-concepts)
    - [Data and methods](#Data-and-methods)
    - [Instance Lifcycle Hooks](#Instance-Lifcycle-Hooks)
- [Template Syntax](#Template-syntax)
    - [Interpolation](#Interpolation)
    - [Attribute Bindings](#attribute-bindings)
    - [Some of the most commonly used directives](#Some-of-the-most-commonly-used-directives)
    - [Events and modifiers](#Events-and-modifiers)
    - [Computed Caching vs Methods](#Computed-Caching-vs-Methods)
    - [Computed vs Watched Property](#Computed-vs-Watched-Property)

## Basics and core concepts

### Vue app instance

A Vue app instance is the basic building block of a Vue.js application. It is an object that represents a single Vue component and its associated data and methods.

Note: in vue instance, you need to pass in an options object that defines the component's properties, such as its data, template, and methods.

### Data and methods

When a Vue instance is created, it adds all the properties found in its data object to Vue’s reactivity system. When the values of those properties change, the view will “react”, updating to match the new values.

````
new Vue({
    data() {
        return {
         name: "john doe"
        }
       },
       methods: {
    greet: function(event) {
      // `event` is the native DOM event
      alert(event.target.tagName);
    }
  }
    })
    .$mount("#appRoot")
````
### Instance Lifcycle Hooks

Each Vue instance goes through a series of initialization steps when it’s created - for example, it needs to set up data observation, compile the template, mount the instance to the DOM, and update the DOM when data changes. Along the way, it also runs functions called lifecycle hooks, giving users the opportunity to add their own code at specific stages.

For example, the created hook can be used to run code after an instance is created:

new Vue({
  data: {
    a: 1
  },
  created: function () {
    console.log('a is: ' + this.a)
  }
})
There are also other hooks which will be called at different stages of the instance’s lifecycle, such as mounted, updated, and destroyed.

## Template Syntax

### Interpolation

Interpolation is a way to insert dynamic data into a Vue template. It is done using double curly braces ({{ }}). For example:

´´´´
<span>Message: {{ msg }}</span> //Text interpolation
<p> This is a p element <h1> This is a h1 element inside p element </h1> </p>  // Raw HTML interpolation
<div v-bind:id="dynamicId"></div> // v-bind directive
<a v-bind:href="url"> ... </a>  
Note: Here href, id are the argument, which tells the v-bind directive to bind the element’s href attribute to the value of the expression url.
{{ ok ? 'YES' : 'NO' }} // one single js expression

´´´´

### Attribute Bindings
```
    <img :style="{width: 100 + 'px', height: 60 + 'px' }" v-bind:src="logoImage" class="" alt="">
```
```
v-text="flipped ? '' : cards[index].front"
```

### Some of the most commonly used directives

````
v-if: Conditionally render an element.
v-show: Hide or show an element depending on a condition.
v-for: Loop through an array and render an element for each item.
v-bind: Bind the value of an element to a data property.
v-on: Attach an event listener to an element.
````
### Events and modifiers

````
Events

click: The click event is triggered when the user clicks on an element.
mouseover: The mouseover event is triggered when the user's mouse cursor enters an element.
mouseout: The mouseout event is triggered when the user's mouse cursor exits an element.
keydown: The keydown event is triggered when the user presses a key on the keyboard.
keyup: The keyup event is triggered when the user releases a key on the keyboard.
submit: The submit event is triggered when the user submits a form.

Modifiers

.once: The .once modifier ensures that the event handler is only called once, even if the event is triggered multiple times.
.prevent: The .prevent modifier prevents the default behavior of the event. For example, the default behavior of the click event is to open a link in a new tab. The .prevent modifier would prevent this from happening.
.stop: The .stop modifier stops the propagation of the event. This means that the event will not be passed on to any parent elements.
.capture: The .capture modifier makes the event handler be called before the event is handled by any parent elements.
````

### Computed Caching vs Methods

the difference is that computed properties are cached based on their reactive dependencies. A computed property will only re-evaluate when some of its reactive dependencies have changed.

### Computed vs Watched Property

Vue does provide a more generic way to observe and react to data changes on a Vue instance: watch properties. When you have some data that needs to change based on some other data, it is tempting to overuse watch - especially if you are coming from an AngularJS background.


<sup align="right"><a href="#table-of-contents">Go to top</a></sup>

#### Connect with me

[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/smhabibjr) 
[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/smhabibjr) 
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/c/HabibJr)
[![Medium](https://img.shields.io/badge/Medium-12100E?logo=medium&logoColor=white)](https://medium.com/@smhabibjr)
