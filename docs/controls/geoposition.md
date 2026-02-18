# Geoposition control

Adds a button that when clicked centers and zooms the map to the current position. Clicking the button a second time will activate the tracking mode (if `enableTracking` has been set to `true`).

Property | Description
---|---
`name` | the name of the control (geoposition)
`options` | options for the control

Option | Description
---|---
`active` | Boolean. Whether the control should be activated on map load or not. Defaults to false.
`panTo` | Boolean. Whether to pan to users position or not. Defaults to true.
`zoomLevel` | Integer. Specifies the zoom level that will be used when a position has been aquired. If it is not specified, the map will be zoomed to the fourth closest resolution. This option has no effect if panTo is set to false.
`enableTracking` | Boolean. Option to enable tracking mode. When enabled and activated, the map will continuously center on the user's position. Defaults to false.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example geoposition control

```json
{
  "name": "geoposition",
  "options": {
      "zoomLevel": 15
  }
}
```
