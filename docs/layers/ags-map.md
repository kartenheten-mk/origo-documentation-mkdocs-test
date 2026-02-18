# AGS_MAP
A tiled layer created with an ArcGIS Server map service.

Property | Description
---|---
`name` | the unique name of the layer used internally. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`id` | the id of the layer in ArcGIS Server.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For ArcGIS Server map service the type is AGS_TILE.
`source` | named source of the layer. The [source](source.md) must be defined.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`queryable` | if featureinfo should be enabled for the layer. Default is true.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`renderMode` | can be either image or tile. Default is tile.
`legend` | if the layer should be included in the map legend. Default is false.
`attribution` | attribution for the layer shown in the footer. Used for copyright text or any other information. Optional.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`minScale` | the minmum scale the layer is visible. Optional.
`maxScale` | the maximum scale the layer is visible. Optional.
`attributes` | definition of [attributes](attributes.md) and how they should be presented in featureinfo. If not provided all available attributes will be shown with a standard template.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`tileGrid` | custom tileGrid for the AGS tile layer. extent, alignBottomLeft, resolutions and tileSize can be set.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.
`attachments`| An [attachment object](attachments.md) containing configuration for displaying attachments
`imageFeatureInfoMode` | Sets the featureinfo mode for this image type layer. Alternatives are `pixel` which will produce feature info if the pixel queried of a feature of a visible layer isn't totally transparent and `visible` which works on transparent styles too. `always` will in addition produce feature info for layers that are not visible. Feature info is dependant upon `queryable` being `true`. If set will override the [map](../configuration/featureinfo-options.md) level option with the same name. If not set the featureinfo behaviour will be decided at the map level. Optional.

Source options | Description
---|---
`url` | url to the ArcGIS Server endpoint
`tileGrid` | custom tileGrid for the AGS tile source. extent, alignBottomLeft, resolutions and tileSize can be set.

#### Basic example AGS_MAP

```json
{
  "name": "my_ags_tile",
  "id": "0",
  "source": "local_ags_tile",
  "title": "My ags tile",
  "type": "AGS_MAP",
  "renderMode": "image",
  "style": "mask"
}
```
