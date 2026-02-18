# About control

Adds an about map control. A button is added to the mapmenu. On button click, a splash popup will show general info about the map. By default, the button is displaced in the mapmenu.

Property | Description
---|---
`name` | the name of the control (about)
`options` | options for the control

Option | Description
---|---
`icon` | optional, defaults to `#ic_help_outline_24px`. Other icons are possible.
`buttontext` | the button text shown in the menu
`title` | popup header text
`content` | popup content text
`placement` | option where the button is displayed. Optional, defaults to ["menu"]. ["screen"] or both are possible
`style` | option to control the size of the splash popup. Optional, defaults to `modal`. `modal-full` is possible.
`hideWhenEmbedded` | if set to true, the control is not displayed when the map is embedded. Defaults to false

#### Example about control

```json
{
  "name": "about",
  "options": {
    "buttontext": "Om Origo",
    "title": "Om Origo",
    "content": "<p>Origo är ett ramverk för webbkartor. Ramverket bygger på JavaScript-biblioteket OpenLayers 3...</p>"
  }
}
```
