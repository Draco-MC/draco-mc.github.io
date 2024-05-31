---
title: Listeners
layout: single
permalink: /docs/listeners
---

Listeners are interfaces that call a method implemented within a class when an event occurs. Listeners are an essential piece of Draco and are very simple, highly flexible, and allow for mods outside of the Standard Library to have their own listeners that other mods can use

To use a listener, simply implement it and have it's method in question, here's an example with `IRegisterListener`

```kotlin
class RegisterEvent : IRegisterListener {
    override fun register() {
        // Registry related code goes here, see the Registries section for more info
    }
}
```

Listeners have an order of presidence in which they are called, that order goes:<br>
`COMMON` Listeners<br>
`SERVER` & `CLIENT` Listeners<br>
This order will always stay true and is done to ensure that the `IRegisterListener` listener is called in the correct order
{: .notice--info}