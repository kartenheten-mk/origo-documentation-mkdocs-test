# WMTS

Property | Description
---|---
`name` | the unique name of the layer used internally and the name of the layer in the WMTS service. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For WMTS the type is WMTS.
`source` | named source of the layer. The [source](source.md) must be defined.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`queryable` | if featureinfo should be enabled for the layer. Default is true.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`legend` | if the layer should be included in the map legend. Default is false.
`attribution` | attribution for the layer shown in the footer. Used for copyright text or any other information. Optional.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`minScale` | the minmum scale the layer is visible. Optional.
`maxScale` | the maximum scale the layer is visible. Optional.
`attributes` | definition of [attributes](attributes.md) and how they should be presented in featureinfo. If not provided all available attributes will be shown with a standard template.
`format` | the image format to use. Default is image/png.
`featureinfoLayer` | the named layer this layer should use for featureinfo requests. Optional.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`wmtsStyle` | WMTS layer style, if applicable.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.
`attachments`| An [attachment object](attachments.md) containing configuration for displaying attachments

Source options | Description
---|---
`url` | url to the wmts endpoint
`matrixSet` | the named matrixSet if provided for the source. Default matrixSet is the matrixSet created for the map and depends on the map resolutions.
`matrixIdsPrefix` | the named prefix for tileMatrix. Default matrixIdsPrefix is the maps projection code.
`resolutions` | Array of resolutions. Defaults to map resolutions.
`origin` | Origin of the gridset. Defaults to topleft corner of the projections extent.
`tileSize` | Array of tileSizes. Defaults to [256,256].


#### Basic example WMTS

```json
{
  "name": "my_wmts",
  "source": "local_wmts",
  "title": "My WMTS",
  "type": "WMTS",
  "style": "mask"
}
```
