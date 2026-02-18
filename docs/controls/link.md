# Link control

Adds a button to the mapmenu that when clicked opens a new browser tab with the specified url. By default, the button is displaced in the mapmenu.

Property | Description
---|---
`name` | the name of the control (link)
`options` | options for the control

Option | Description
---|---
`icon` | optional, defaults to `#ic_launch_24px`. Other icons are possible.
`title` | sets the link title of the control.
`url` | sets the address for the link.
`placement` | option where the button is displayed. Optional, defaults to ["menu"]. ["screen"] or both are possible.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example link control

```json
{
  "name": "link",
  "options": {
      "title": "Origo",
      "url": "https://github.com/origo-map/origo"
  }
}
```
