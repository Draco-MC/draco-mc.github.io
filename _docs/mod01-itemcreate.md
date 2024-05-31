---
title: Create an Item
layout: single
permalink: docs/itemcreate
---

Creating a Custom Item is the simpliest modification that you can do with Minecraft, and is also a good demostration of how to use Draco to mod the game. First start with an inital template for modding the game. Afterwards you'll need to create a deferred registry

```kotlin
class ItemRegisterEvent : IRegistryListener {
    companion object {
        @JvmStatic
        val ITEM_REGISTRY = DeferredRegistry.create(Registries.ITEM,"example") // Replace example with your Mod ID
    }
}
```

Now you have a deferred registry ready, Make sure the class in question is also a registered `COMMON` listener in your `draco.json` file.

Afterwards to create a basic item, you can simply create an entry for it

```kotlin
class ItemRegisterEvent : IRegistryListener {
    companion object {
        @JvmStatic
        val ITEM_REGISTRY = DeferredRegistry.create(Registries.ITEM,"example") // Replace example with your Mod ID
        @JvmStatic
        val EXAMPLE_ITEM = ITEM_REGISTRY.register("example_item") {
            Item(Item.Properties())
        }
    }
}
```

This creates a deferred registry entry for the example item, afterwards you'll need to manually register it, which is as simple as doing

```kotlin
class ItemRegisterEvent : IRegistryListener {
    companion object {
        @JvmStatic
        val ITEM_REGISTRY = DeferredRegistry.create(Registries.ITEM,"example") // Replace example with your Mod ID
        @JvmStatic
        val EXAMPLE_ITEM = ITEM_REGISTRY.register("example_item") {
            Item(Item.Properties())
        }
    }
    
    override fun register() {
        ITEM_REGISTRY.register()
    }
}
```

When registring content, **ORDER MATTERS**! In this example, the register listener was put in the same class as the registry stuff, however it is actually recommended that you have just one common register listener that registers all of the `DeferredRegistries` in the correct order, as this will prevents errors from occuring. A similar thing should also be done with client-specific registration where it should have a single register listener bound for the client that registeres all of the client-specific content in the correct order.
{: .notice--warning}

Now your item is registered! If you use the `/give` command, you'll notice that it is now available