# WMS

Property | Description
---|---
`name` | the unique name of the layer used internally and the name of the layer in the WMS service. White spaces and special characters should be avoided. To be able to reuse layers add after the layer name a double underscore plus a suffix to tell them apart.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer shown in the layer info. Optional.
`type` | type of source for the layer. For WMS the type is WMS.
`source` | named source of the layer. The [source](source.md) must be defined with the layers source options.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer.
`format` | the image format used for the layer. Default is 'image/png' unless format is set for the source.
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
`gutter` | gutter setting for the layer. Default is 0.
`featureinfoLayer` | the named layer this layer should use for featureinfo requests. Optional.
`stylePicker` | Adds a dropup with alternative styles in the layer info. Overrides `style` and `hasThemeLegend` and `legendParams`. See [stylePicker](style-picker.md). Optional.
`searchable` | used with includeSearchableLayers in search control.  Can be set to 'always', true (when visible) or false.
`tileGrid` | custom tileGrid for the WMS layer. extent, alignBottomLeft, resolutions and tileSize can be set.
`renderMode` | whether to render the layer tiled ('tile') or single tiled ('image'). Defaults to 'tile'.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.
`attachments`| An [attachment object](attachments.md) containing configuration for displaying attachments
`infoFormat` | Origo's get feature info expects responses in 'application/json' but some WMS servers (f.e. ArcGIS) don't supply it, so it's possible here to request in format 'application/geo+json' or 'application/geojson' if the server response with that format. For Geoserver 'text/html' is valid, within certain limits, see [WMS text/HTML](style-picker.md#texthtml-infoformat-for-wms-layers). Optional.
`htmlSeparator` | A html tag to attempt to separate features via from the getfeatureinfo text/html reply if `infoFormat` is set to `text/html`. Optional.
`hasThemeLegend` | Whether extendedLegend or not. See [WMS autolegend](style-picker.md#automatic-default-legend-style-for-wms-layers). Optional, defaults to false. Has no effect if a [style](../styles/basics.md) is also defined.
`thematicStyling` | Setting `thematicStyling` to true will add buttons to the different thematic styles to be able to turn them on or off. Optional, defaults to false. For WMS layers it has no effect if `hasThemeLegend` isn't also set to true.
`legendParams` | A getLegendGraphic parameters object, see [WMS autolegend](style-picker.md#automatic-default-legend-style-for-wms-layers). Optional, has no effect if a [style](../styles/basics.md) is also defined.
`imageFeatureInfoMode` | Sets the featureinfo mode for this image type layer. Alternatives are `pixel` which will produce feature info if the pixel queried of a feature of a visible layer isn't totally transparent and `visible` which works on transparent styles too. `always` will in addition produce feature info for layers that are not visible. Feature info is dependant upon `queryable` being `true`. If set will override the [map](../configuration/featureinfo-options.md) level option with the same name. If not set the featureinfo behaviour will be decided at the map level. Optional.
`requestMethod` | request method for this layer. Can be set to 'post', otherwise it will be 'get'. Default is 'get'.
`sourceParams` | A object with any additional params that can be added to the source and sent to the WMS server. For example CQL_FILTER can be provided as [cql](http://docs.geoserver.org/latest/en/user/tutorials/cql/cql_tutorial.html) and there by filter on which objects should be included on a Geoserver layer. For a QGIS Server the param FILTER can be used in a similar maner, the syntax should be in OGC filter format. Other server specific params can also be set as DPI, BGCOLOR oc OPACITIES. Optional.

Source options | Description
---|---
`format` | the image format used for the layer unless format is set on layer-level. Default is 'image/png'.
`requestMethod` | request method for this source. Can be set to 'post', otherwise it will be 'get'. If set on layer level this option will be omitted. Default is 'get'.
`url` | url to the wms endpoint
`version` | the OGC WMS version. Default is 1.1.1.
`tileGrid` | custom tileGrid for the WMS source. extent, alignBottomLeft, resolutions and tileSize can be set.
`type` | vendor of the WMS server. Used for functionality that requires different handling depending on the server type. Currently the options are 'Geoserver', 'ArcGIS', 'QGIS'. Optional.
`capabilitiesURL` | url to the capabilities document. Downloads the capabilities document and saves it to `capabilitiesDoc` in the source unless `saveCapabilitiesDoc` is set to false. Also the layers in the map are matched to the document and if they are missing the layer is marked secure and resulting in a lock for the layer in the legend. Optional.
`saveCapabilitiesDoc` | set to false to opt out saving the capabilities document when `capabilitiesURL` is set. Default is true.

#### Basic example WMS

```json
{
  "name": "my_wms",
  "source": "local_wms",
  "title": "My WMS",
  "type": "WMS",
  "style": "mask"
}
```

#### Example with same layer name on different servers

```json
[
  {
    "name": "school__prod",
    "title": "Elementary school",
    "format": "image/png",
    "queryable": false,
    "visible": false,
    "type": "WMS",
    "group": "Elementary",
    "source": "prod",
    "style": "school"
  },
  {
    "name": "school__test",
    "title": "Elementary school",
    "format": "image/png",
    "queryable": false,
    "visible": false,
    "type": "WMS",
    "group": "ElementaryNew",
    "source": "test",
    "style": "school"
  }
]
```

#### Examples with additional source params supplied for a Geoserver and QGIS Server

```json
[
  {
    "name": "example_geoserver",
    "title": "Example Geoserver",
    "format": "image/png",
    "queryable": false,
    "visible": false,
    "type": "WMS",
    "group": "Elementary",
    "source": "geoserver",
    "sourceParams": {
      "CQL_FILTER": "owner = 'me'"
    }
  },
  {
    "name": "example_qgisserver",
    "title": "Example QGIS Server",
    "format": "image/png",
    "queryable": false,
    "visible": false,
    "type": "WMS",
    "group": "Elementary",
    "source": "qgisserver",
    "sourceParams": {
      "FILTER": "mylayer1:\"col1\";mylayer1,mylayer2:\"col2\" = 'blabla''",
      "DPI": "300",
      "BGCOLOR": "0x00FF00"
    }
  }
]
```
