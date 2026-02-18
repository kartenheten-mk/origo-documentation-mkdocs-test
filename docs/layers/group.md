# Group
A group layer is a simulated layer that contains several layers. For a user, a group layer looks just like a normal layer in the legend. Sublayers are defined like regular layers, with the exception that their visibility must be explicitly set to true.

Property | Description
---|---
`name` | the unique name (a dummy name) of the layer. White spaces and special characters should be avoided.
`title` | title for the layer visible to the user.
`abstract` | short description of the layer. Adds a text in the legend. Optional.
`type` | type of source for the layer. For group layers the type is GROUP.
`style` | the name of the referenced [style](../styles/basics.md) to be used for the layer. Only visible in the legend, not for styling the layer.
`group` | group the layer belong to. If group is not provided it will not be included in legend.
`opacity` | opacity of the layer. Value between 0 and 1. Default is 1.
`visible` | if the layer should be visible. Default is false.
`extent` | extent of the layer. Map extent is default.
`removable` | Adds a _Remove layer_ option to the layer info menu if set to true. Optional.
`zoomToExtent` | Adds a _Zoom To_ option to the layer info menu if set to true. Optional.
`layers` | the included layers. Defined as normal layers.
`opacityControl` | Adds an opacity slider in the legends extended layer info. Optional, defaults to true.
`css` | Used for adding CSS properties to layer canvas element. Formatted as key/value pairs.

#### Basic example group

```json
{
  "name": "dummy_name",
  "title": "My layer",
  "group": "test",
  "style": "mask",
  "type": "GROUP",
  "layers": [
    {
      "name": "mywfs",
      "title": "My wfs",
      "source": "local_wfs",
      "style": "mask",
      "type": "WFS",
      "visible": true
    },
    {
      "name": "mywfs",
      "title": "My wfs",
      "source": "local_wfs",
      "style": "mask",
      "type": "WFS",
      "visible": true
    }
  ]
}
```
