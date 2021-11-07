# gio-embed

GIOUI is a golang based GUI platform at https://github.com/gioui 

**gio-embed** is based on the open standard https://oembed.com/, and allows GIOUI Widgets ( and hence functionality ) to be loaded and embedded into the Canavs at runtime.

These can come from your servers, or any other Servers. A example Registry of providers is at https://oembed.com/providers.json, however, it is likely that a Well Known URI standard will be created for GIOIO embeddable Widgets, as well as a JSONSchema to describe them.

The aim is that an GIOUI Embedd Widget is exactly the same as a standard GIOUI widget in terms of its golang code. 
A GIOUI loader that deals with loading and displaying a GIOUI Embed Widget that has been compiled to WASM needs to be developed.
The GIOUI Embed Widget can then be compiled to WASM and exposed via a Web Server for the GIOUI Loader to load and embed into the App.

## Features

- Lowers size of initial download.

- Allows Modularity in that Apps can be constructed as MicroServices, to build large applications out of other GIOUI Widgets.

- Allows discovery at runtime, allowing different functionality and/or data to be provided based on different Contexts such as Feature Flags, Locale, or anything. 
  - Here is a simple Feature Flags golang system that could mate with this at: https://github.com/thomaspoignant/go-feature-flag

## Examples

Any Widget can be loaded this way, but simple examples are:

- Chat
- Video Player
- etc

## Backend 

One loose coupled way is to use an SSR server such as at https://github.com/yuriizinets/kyoto to enable simple Go Templates to be involved in the request for a GIOUI Widget as needed, such that they can be easily configured on the Server without recompiling.

This also allows Contextual loading of data from the backend specific to the User at Runtime.


## Screen Loading

Relies on the Intersection Web API at https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API, to know when to load, allowing late binding, and avoiding large initialy downloads.

https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility provides analytics also.

GIOUI Web apps can now control when and where the GIOUI Embedded Widgets are displayed.

This late loading functionality can be used not just in Web, but also Native apps.

Native apps can use a WebView or they can employ the an embededed WASM Runtime. The Webview is the initialy roadmap target, and then the WASM based loaded.


## Screen Positioning

All GIOUI Widgets must output their dimensions, as the same contract is used for this. 

## Prior art

https://pkg.go.dev/github.com/Doist/unfurlist#section-readme
- Open Graph and oEmbed supported

https://github.com/dyatlov/go-oembed

https://github.com/widnyana/oembed



