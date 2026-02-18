# Drag-and-drop control

Adds the ability to drag-and-drop GeoJSON, GPX, IGC, KML and TopoJSON files to the map. Note that the layers are only temporarily available, once the map is closed the layers are lost. It is possible to drag-and-drop multiple files at once.

Property | Description
---|---
`name` | the name of the control (draganddrop)
`options` | options for the control

Option | Description
---|---
`featureStyles` | custom styling for the layer.
`groupName` | the name of the group containing the added layers. Defaults to "egna-lager".
`groupTitle` | the title of the group containing the added layers. Used if group doesn't exist. Defaults to "Egna lager".
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`showLegendButton` | show an add-button in the legend. Requires the drag-and-drop control to be added after the legend. Defaults to false.
`styleByAttribute` | style features in the layer based on their `style`-attribute. Defaults to false.
`zoomToExtent` | add zoom to extent option for layer menu. Defaults to true.
`zoomToExtentOnLoad` | zoom to the layer extent when loaded. Defaults to true.

#### Example drag-and-drop control

```json
{
  "name": "draganddrop",
  "options": {
    "groupName": "drag-and-drop-layers",
    "groupTitle": "Drag-and-drop layers",
    "styleByAttribute": true
  }
}
```
