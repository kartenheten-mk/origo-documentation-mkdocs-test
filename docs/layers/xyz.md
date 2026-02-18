# XYZ

Property | Description
---|---
`name` | the unique name of the layer used internally. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For XYZ the type is XYZ.
`layerURL` | path to the image tiles. Can be a absolute path or relative used along with the source url.
`source` | named source of the layer. Can be a absolute path or relative used along with the layerURL. Optional if layerURL is set.
`style` | the name of the referenced [style](../styles/basics.md) to be used for styling the legend. Must be an image and if omitted a generic background map image will be used.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`attribution` | attribution for the layer shown in the footer. Used for copyright text or any other information. Optional.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default if tileGrid is not set.
`minScale` | the minmum scale the layer is visible. Optional.
`maxScale` | the maximum scale the layer is visible. Optional.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`tileGrid` | If layers tilegrid differs from the map. Optional.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.

Source options | Description
---|---
`url` | url to the xyz endpoint. Used with or instead of layerURL. Optional if layerURL is set.
`tileGrid` | custom tileGrid for the XYZ source. extent, alignBottomLeft, resolutions and tileSize can be set.

#### Basic example XYZ

```json
{
  "name": "my_xyz",
  "title": "My XYZ",
  "type": "XYZ",
  "layerURL": "./data/xyz/{z}/{x}/{y}.png",
  "style": "background-map",
  "maxScale": 50000
}
```
