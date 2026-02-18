# Editor control

Enables layer editing.

**Important:** When editing WFS-layers the `workspace`option must be specified on the `source`. See [Wfs layer configuration](../layers/wfs.md)

Property | Description
---|---
`name` | the name of the control (editor)
`options` | options for the control

Option | Description
---|---
`editableLayers` | Layers that will we handled as editable layers. The name of the layer is used as identifier to get the settings for the layer as defined in layers. Can also be configured on a per layer basis. This will be deprecated in future releases of Origo. Editable can be set as a layer property.
`defaultLayer` | Editable layer that should be chosen as default editable layer.
`autoForm` | If set to true, the attribute form will be displayed automatically after a feature has been drawn. Default is false.
`isActive` | option to set if the editor toolbar should be opened and activated by default. Default is true.
`autoSave` | if edits should be autosaved or not. Defaults to true.
`snap` | option to enable/disable snapping. Default is true.
`snapLayers` | List of layers that should have snapping enabled. Default is editableLayers.
`snapTolerance` | Optional snap tolerance in pixels. Only used when snap is on. Defaults to 10.
`trace` | Boolean. Optional,  When true, features in snap layers are traced when snapped to when drawing new features. Requires snap. Defaults to false.
`traceStyle` | Optional. Name of style for displaying possible trace paths. Defaults to bright green.
`drawTools` | Extra draw tools besides the standard tools for Point, MultiPoint, Line, MultiLine, Polygon and MultiPolygon. The tools are set for each geometry type as key in an object with the tools in an array. Note that the correct geometry type for a line is _LineString_ but in drawTools it is configured as _Line_.
`attributes` | definition of [attributes](../layers/attributes.md) and how they should be presented and validated in editor form. If not provided all available attributes will be shown with a standard template.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`validateOnDraw` | If set to true, the editor prevents drawing invalid geometries (self-intersect). Defaults to false.
`featureList` | If set to true you'll get a list when selecting multiple features. Defaults to true.
`featureListAttributes` | Array of attributes to be showed in the featureList. Default is to just show the feature ID.
`modifyTools` | When true, displays the modify tools toolbar which contains advanced editing tools that are used to modify existing features. Currently the only tool available is split line. Default is false.

Draw tools can be set for each geometry type on editor control level in wich case it adds the configured tools to each layer of that
kind in addition to the default tool. Draw tools can also be set on each layer in which case the default tool is not added unless specified.

drawTool | Description
---|---
`Polygon` | Draws a polygon (default for polygon layers)
`MultiPolygon` | Draws a polygon (default for MultiPolygon layers)
`Line` | Draws a line (default for line layers)
`MultiLine` | Draws a line (default for MultiLine layers)
`Point` | Draws a point (default for point layers)
`MultiPoint` | Draws a point (default for MultiPoint layers)
`box` | Draws a rectangle
_object_ | Specifies a draw tool that needs more configuration

__CopyTool__

Copies a geometry from one vector layer to the currently edited layer.

Property | Description
---|---
`toolName` | Name of the tool. Copy tool has name 'Copy' __Required__
`groups`| Array of group names from which geometries can be copied. Mainly useful for layers which names are not known beforehand.
`layers` | Array of layer names that are possible to copy from

If neither _groups_ nor _layers_ are specified all vector layers can be copied from.


#### Example editor control

```json
{
  "name": "editor",
  "options": {
    "isActive": true,
    "autoSave": false,
    "defaultLayer": "editor_polygon",
    "drawTools": {
      "Polygon": ["box"]
    }
  }
}
```

#### Example polygon and copy tool in layer configuration

```json
{
"drawTools": [
        "Polygon",
        {
          "toolName": "Copy",
          "layers": [ "SketchPoly" ],
          "groups": [ "drag-and-drop-layers" ]
        }
      ]
}
```
