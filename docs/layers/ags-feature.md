# AGS_FEATURE
A vector layer created with an ArcGIS Server feature service.

Property | Description
---|---
`name` | the unique name of the layer used internally. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`id` | the id of the layer in ArcGIS Server.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For ArcGIS Server feature service the type is AGS_FEATURE.
`source` | named source of the layer. The [source](source.md) must be defined.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend. Optional.
`editable` | if the layer should be editable or not. Requires the editor control. Defaults to false. Optional.
`allowedEditOperations` | List of available edit tools. Possible values are: _updateAttributes_, _updateGeometry_, _create_, _delete_. Only applies if layer is editable. Defaults to all. Optional.
`queryable` | if featureinfo should be enabled for the layer. Default is true.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`legend` | if the layer should be included in the map legend. Default is false.
`attribution` | attribution for the layer shown in the footer. Used for copyright text or any other information. Optional.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`minScale` | the minmum scale the layer is visible. Optional.
`maxScale` | the maximum scale the layer is visible. Optional.
`attributes` | definition of [attributes](attributes.md) and how they should be presented in featureinfo. If not provided all available attributes will be shown with a standard template.
`layerType` | option to set how the vector layer should be rendered. The options are cluster, [image](https://openlayers.org/en/latest/apidoc/ol.source.ImageVector.html) or vector. Default is vector.
`clusterStyle` | the style to be used for clustered features. Is required if layerType cluster is used.
`clusterOptions` | options for clustering. See the settings page for details.
`geometryName` | geometry attribute name. Default is geom.
`filter` | filter are used with query filter [where](http://resources.arcgis.com/en/help/rest/apiref/query.html). Optional.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`featureinfoTitle` | attribute to be used instead of the title property as the title for the popup/sidebar. Optional.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.
`attachments`| An [attachment object](attachments.md) containing configuration for editing and displaying attachments

Source options | Description
---|---
`url` | url to the ArcGIS Server endpoint
`clusterOptions` | options for clustering. See the settings page for details.

#### Basic example AGS_FEATURE

```json
{
  "name": "my_ags_feature",
  "id": "0",
  "source": "local_ags_feature",
  "title": "My ags feature",
  "type": "AGS_FEATURE",
  "style": "mask"
}
```
#### Filter example AGS_FEATURE

```json
{
  "name": "my_ags_feature",
  "id": "0",
  "source": "local_ags_feature",
  "title": "My ags feature",
  "type": "AGS_FEATURE",
  "style": "mask",
  "filter": "type='urban'"
}
```
