# Legend control

Adds a legend control. Legend is added to menu and as a map legend to the map.

Property | Description
---|---
`name` | the name of the control (legend)
`options` | options for the control

Option | Description
---|---
`cls` | option to add css class references to the legend element.
`style` | option to add inline HTML style properties to the legend element.
`expanded` | true or false if the legend should be expanded or collapsed on load. Default is true.
`contentCls` | option to add css class references to the legend content element.
`contentStyle` | option to add inline HTML style properties to the legend content element.
`labelOpacitySlider` | option to use custom label for the opacity slider. Default is 'Opacity'.
`name` | option to set the legend UI component name. Default is 'legend'.
`turnOffLayersControl` | true or false for whether the turn off layers button should be present in the legend or not. Default is false.
`turnOnLayersControl` | true or false for whether the turn on all layers button should be present in the legend or not. Default is false.
`autoHide` | option to set if the legend should close automatically on map click. Accepted values are 'always' (legend is always closed on map click), 'mobile' (legend is closed on map click if map size is 'm' or smaller (see breakpoints in origo.js)) and 'never' (legend is never closed on map click, this is the default setting).
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`searchLayersControl` | option to add search function for layers in the legend. Defaults to false.
`searchLayersMinLength` | specifies the minimum length of how many characters should be entered before search, default is 2.
`searchLayersLimit` | specifies how many matches should be shown, default is 10.
`searchLayersParameters` | specifies the parameters which should be used in the search. Defaults to ['name', 'title'].
`searchLayersPlaceholderText` | specifies the text that should be displayed as placeholder text in search input field. Defaults to 'Sök lager'.
`visibleLayersControl` | true or false for whether the visible layers button should be present in the legend or not. Default is false.
`visibleLayersViewActive` | true or false if the view with visible layers should be active or not from start. Default is false.

#### Example legend control

```json
{
  "name": "legend",
  "options": {
    "expanded": false,
    "turnOffLayersControl": true,
    "contentStyle": {
      "width": "300px"
    }
  }
}
```
