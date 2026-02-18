# VECTORTILE
A vector tile layer.

Property | Description
---|---
`name` | the unique name of the layer used internally. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For vector tiles service the type is VECTORTILE.
`source` | named source of the layer. The [source](source.md) must be defined.
`layerURL` | url to the service added to the source url. Mandatory unless layerName and gridset is set. E.g. layerName@gridset@format/{z}/{x}/{-y}.format
`layerName` | the layer name on the webserver, used to build the layerUrl. Mandatory unless layerUrl is set.
`gridset` | the gridset defined on the webserver, used to build the layerUrl. Mandatory unless layerUrl is set.
`format` | format fot the vector tiles. Valid are topojson, geojson and pbf. Mandatory.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`attribution` | attribution for the layer shown in the footer. Used for copyright text or any other information. Optional.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`tileGrid` | custom tileGrid for the vector tile layer. extent, alignBottomLeft, resolutions and tileSize can be set.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.

Source options | Description
---|---
`url` | url to the vector tiles endpoint. E.g. http://yourhost/geoserver/gwc/service/tms/1.0.0/
`tileGrid` | custom tileGrid for the vector tile source. extent, alignBottomLeft, resolutions and tileSize can be set.

#### Basic example VECTORTILE

```json
{
  "name": "my_vector_tiles",
  "source": "vector tiles source",
  "title": "My vector tiles",
  "type": "VECTORTILE",
  "style": "customstyle",
  "layerName": "my_vector_tiles",
  "gridset": "my_gridset",
  "format": "pbf"
}
```
