# Draw control

Adds a draw control. Drawlayers can be exported or stored with the mapstate functionality. It is also possible to import GeoJSON-layers. To change what colors to style features with, use the palette-setting in the map config.

Property | Description
---|---
`name` | the name of the control (draw)
`options` | options for the control

Option | Description
---|---
`buttonText` | title for link in mapMenu. Default is 'Rita'
`drawTools` | what extra tools to add. See example for valid values. Object, default is {}
`exportable` | layer setting. Boolean, default is true
`groupName` | the group will be created if it doesn't exist. Default is 'none'
`groupTitle` | title for the group, groupName must also be set. Default is 'Ritlager'
`draggable` | make the group draggable (if created by this control). Boolean, default is true
`isActive` | activate the control at start. Boolean, default is false
`layerTitle` | name of layer. Default is 'Ritlager'
`multipleLayers` | if the user should be able to add multiple draw layers. Boolean, default is false
`placement` | placement of the activate button. Can be screen or menu. Array, default is ['menu']
`queryable` | layer setting. Boolean, default is false
`removable` | layer setting. Boolean, default is true
`showAttributeButton` | if true the user can add a popuptext to the feature. Boolean, default is false
`showDownloadButton` | add downloadbutton in the toolbar. Boolean, default is false
`showSaveButton` | only useful when using the draw control along with a service. Boolean, default is false
`zoomToExtent` | add button to layer menu. Boolean, default is true
`extraMarkers` | contains a list of custom markers, which can be used for point symbols. Array with objects that has properties `name`, `title`, `type`, `src` and `scale` (only for 'image' type). The `type` of marker can be 'svg' for scalable vector graphics icons or 'image' for raster images. The `src` of the markers should for svg markers be an inline SVG code, while for image markers, it can be a URL or a Base64 encoded image. The inline SVG code should include placeholders where appropriate $height$, $width$, $strokeColor$ and $fillColor$ to make it possible to control the size and colors of the SVG.

#### Example draw control

```json
{
"name": "draw",
"options" : {
  "buttonText": "Rita",
  "drawTools": {
     "Polygon": ["freehand", "box"],
     "LineString": ["freehand"]
  },
  "showAttributeButton": true,
  "showDownloadButton": true,
  "showSaveButton": true,
  "multipleLayers": true,
  "queryable": false,
  "removable": true,
  "exportable": true,
  "layerTitle": "Ritlager",
  "groupTitle": "Ritlåda",
  "groupName": "rit"
}
```

#### Example configuration of extraMarkers

```json
"options" : {
        "extraMarkers": [
          {"name":"dricksvatten","title":"Dricksvatten","type":"svg","src":"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' height='$height$' width='$width$' viewBox='0 0 20.13 20.13'><path stroke='$strokeColor$' fill='$fillColor$' class='cls-2' d='M7.6,1.49H.85V4.34H6.68V6.05H9.94V3.83A2.34,2.34,0,0,0,7.6,1.49ZM5.17,8.13a.75.75,0,0,0-.12.41L6,17.83l0,.59h8.93l.05-.59.9-9.29a.69.69,0,0,0-.13-.41A.71.71,0,0,0,15.29,8H5.66A.76.76,0,0,0,5.17,8.13ZM15,11.84c-5,3.26-4-1.05-9,.28L5.66,8.54h9.63Z' id='path11' /></svg>"},
          {"name":"hus","title":"Hus","type":"image","scale": 0.6,"src":"https://example.com/img/building.png"}
        ]
}
```
