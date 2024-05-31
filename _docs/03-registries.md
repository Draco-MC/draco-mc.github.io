---
title: Registries
layout: single
permalink: /docs/registries
---

In Minecraft's startup, most important data relating to the game, such as blocks, items, entities, etc, are all registered into Registries. These allow for content to be added to the game within a central area.
However, issues do occur on a technical basis when dealing with registries and when to register content. Because of this with Draco, you are presented with two options for registring content

| `DeferredRegistry` | `BuiltInRegistries` |
| This is the official method provided by Draco that allows you to defer registring content before the `IRegisterListener` event, it requires register to be done manually once the listener is called, however, it allows for initialization of content before the registry is available for registering content | This method is usually much simpler to interface with and is the vanilla way of doing things, It can from a programmer standpoint make more sense, but comes with the caveat of having issues if initialized before the `IRegisterListener` listener is called. |