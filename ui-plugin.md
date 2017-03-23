# NativeScript 3.0
How do you build custom UI components for the NativeScript framework that wrap native views?
In pre 3.0 it was possible but the development experience was not the best we could offer.
With {N} 3.0 we will be exposing to the public some of the APIs that are essential for such components.
(yep, in pre 3.0 _get/setValue and _createUI were private)

# Class Hierarchy
> Throughout this article you will often see the "Visual Tree" expression&mdash;it refers to the JavaScript abstraction available in the cross-platform modules.

Here is a brief overview of the class hierarchy in the Visual Tree:
```
Observable
├── ViewBase
│   ├── View
```

> Pre 3.0 there were 5 classes - Observable > DependencyObservable > Bindable > ProxyObject > View; The property system was redesigned which collapsed the Observable, DependencyObservable and Bindable classes into Observable and the ProxyObject became obsolete. A new ViewBase was introduced that will be discussed later.

### [Observable](http://docs.nativescript.org/api-reference/classes/_data_observable_.observable.html)
This is the class that implements the [Observer](https://en.wikipedia.org/wiki/Observer_pattern) design-pattern. Every node within the Visual Tree should support the addEventListener/removeEventListener routine, hence the base class.

### [ViewBase](???)
This class provides the backbone of the JavaScript visual tree node implementation, the ViewBase.style object, support for CSS styling, bindable properties and inheritance of certain properties (color, bindingContext to name a few).

### [View](http://docs.nativescript.org/api-reference/classes/_ui_core_view_.view.html)
At an abstract level, *View* describes an object that has visual representation on the screen. It participates in the life-cycle and layout passes. The supports the management of a native UI view including propagation of property values to the native view and event subscriptions for native events.

