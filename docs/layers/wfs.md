# WFS

Property | Description
---|---
`name` | the unique name of the layer used internally and the name of the layer in the wfs service. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`id` | the id or ids used to identify the layers in the map server. White spaces and special characters should be avoided.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For WFS source the type is WFS.
`source` | named source of the layer. The [source](source.md) must be defined.
`projection` | set projection (e g to "EPSG:4326") to request features in another reference system and Origo will handle the transformation. The proj4Defs has to be configured in index.json unless it's EPSG:4326 or 3857.
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
`stylePicker` | Adds a dropup with alternative styles in the layer info. An array of styles defined with title, style and clusterStyle. See [stylePicker](style-picker.md). Optional.
`geometryName` | geometry attribute name. Default is geom.
`geometryType` | geometry type for the layer.
`filter` | filter provided as [cql](http://docs.geoserver.org/latest/en/user/tutorials/cql/cql_tutorial.html). Optional.
`strategy` | the ol.loadingstrategy for the layer. Can also be set on source. The options are tile, bbox or all. Default is bbox.
`requestMethod` | request method for this layer. Can be set to 'post', otherwise it will be 'get'. Default is 'get'.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`featureinfoTitle` | attribute to be used instead of the title property as the title for the popup/sidebar. Optional.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`exportable`| Adds a _Export layer_ option to the layer info menu if set to true. To ensure all features in a layer is exported, `strategy` should be set to `all`. Optional.
`exportFormat`| String or array of formats for file export if exportable is true. Can be set to geojson, gpx or kml. Defaults to geojson.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.
`attachments`| An [attachment object](attachments.md) containing configuration for editing and displaying attachments
`isTable`| Bool that indicates if the geometry should be ignored. Implies _visible_. Only useful when layer is a child in related layers. Optional. defaults to `false`
`relatedLayers`| Array of [relatedLayers](related-layers.md) objects defining child layers. Optional
`thematicStyling`| Setting `thematicStyling` to true will add buttons to the different thematic styles to be able to turn them on or off. Optional, defaults to false.

**Source options**

The following options are available for the `source` configuration for WFS.

Name | Type | Required | Description
---|---|---|---
`url` | string | Yes | Url to the wfs endpoint
`strategy` | string | No | The ol.loadingstrategy for the layer. Can also be set on layer. The options are tile, bbox or all. Default is bbox.
`requestMethod` | string | No | Request method for this source. Can be set to 'post', otherwise it will be 'get'. If set on layer level this option will be omitted. Default is 'get'.
`clusterOptions` | string | No | Options for clustering. See the settings page for details.
`workspace`| string | Only when editing | Name of the Wfs feature type namespace. Should match the configuration of the server.
`prefix`| string | No | Prefix to add to Wfs transaction. May be needed to match server's configuration in certain circumstances.
`capabilitiesURL` | url to the capabilities document. Downloads the capabilities document and saves it to `capabilitiesDoc` in the source unless `saveCapabilitiesDoc` is set to false. Also the layers in the map are matched to the document and if they are missing the layer is marked secure and resulting in a lock for the layer in the legend. Optional.
`saveCapabilitiesDoc` | set to false to opt out saving the capabilities document when `capabilitiesURL` is set. Default is true.

#### Basic example WFS

```json
{
  "name": "mywfs",
  "title": "My wfs",
  "group": "test",
  "source": "local_wfs",
  "style": "mask",
  "type": "WFS"
}
```
#### Filter example WFS

```json
{
  "name": "mywfs",
  "title": "My wfs",
  "group": "test",
  "source": "local_wfs",
  "style": "mask",
  "type": "WFS",
  "filter": "type = 'urban'"
}
```
#### Multiple layers filter example WFS

```json
[
  {
    "name": "my_custom_name__1",
    "id": "name_on_server",
    "title": "Urban",
    "group": "Urban group",
    "source": "mapserver_wfs",
    "style": "urbanStyle",
    "type": "WFS",
    "filter": "type = 'urban'"
  },
  {
    "name": "my_custom_name__2",
    "id": "name_on_server",
    "title": "Parklands",
    "group": "Parklands group",
    "source": "mapserver_wfs",
    "style": "parklandsStyle",
    "type": "WFS",
    "filter": "type = 'parklands'"
  }
]
```
