# OSM
A tiled layer from the OpenStreetMap tile server. Source is OpenLayers default and not configurable.

Property | Description
---|---
`name` | the unique name of the layer used internally. White spaces and special characters should be avoided.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For OpenStreetMap layer the type is OSM.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer. Only visible in the legend, not for styling the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.

#### Basic example OSM

```json
{
  "name": "my_osm_layer",
  "title": "OpenStreetMap",
  "group": "background",
  "type": "OSM",
  "style": "mask"
}
```
