# Fullscreen control

Adds a button that will open an embedded map in fullscreen mode in a new tab/window. This is a default control.

Property | Description
---|---
`name` | the name of the control (fullscreen)
`options` | options for the control

Option | Description
---|---
`target` | String. Id of the target container element. Default is the main navigation toolbox (top left).
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example fullscreen control

```json
{
  "name": "fullscreen",
  "options": {
      "hideWhenEmbedded": true
  }
}
```
