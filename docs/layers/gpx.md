# GPX

Property | Description
---|---
`name` | the unique name of the layer used internally. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For GPX source the type is GPX.
`source` | url to the layer.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`queryable` | if featureinfo should be enabled for the layer. Default is true.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`legend` | if the layer should be included in the map legend. Default is true.
`attribution` | attribution for the layer shown in the footer. Used for copyright text or any other information. Optional.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`minScale` | the minmum scale the layer is visible. Optional.
`maxScale` | the maximum scale the layer is visible. Optional.
`attributes` | definition of [attributes](attributes.md) and how they should be presented in featureinfo. If not provided all available attributes will be shown with a standard template.
`layerType` | option to set how the vector layer should be rendered. The options are cluster, [image](https://openlayers.org/en/latest/apidoc/ol.source.ImageVector.html) or vector. Default is vector.
`clusterStyle` | the style to be used for clustered features. Is required if layerType cluster is used.
`clusterOptions` | options for clustering. See the settings page for details.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`featureinfoTitle` | attribute to be used instead of the title property as the title for the popup/sidebar. Optional.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`exportable`| Adds a _Export layer_ option to the layer info menu if set to true. Optional.
`exportFormat`| String or array of formats for file export if exportable is true. Can be set to geojson, gpx or kml. Defaults to geojson.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.
`headers` | Used for setting headers that should be included in the request of the GPX. Formatted as a object with key/value pairs for the headers. Can be used for setting which type to accept or add a apikey.
`attachments`| An [attachment object](attachments.md) containing configuration for editing and displaying attachments

#### Basic example GPX

```json
{
  "name": "mygpx",
  "title": "My gpx",
  "source": "data/mygpx.gpx",
  "style": "line",
  "type": "GPX"
}
```
