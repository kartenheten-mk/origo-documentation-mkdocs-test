# Mapmenu control

Creates a menu on the top right for controls.

Property | Description
---|---
`name` | the name of the control (mapmenu)
`options` | options for the control

Option | Description
---|---
`isActive` | option to set if the mapmenu should be open on load. Default is false.
`breakPointSize` | sets the breakpoint below which the mapmenu will be closed on load by default. Accepted values are 'xs', 's', 'm', and 'l', corresponding to the breakpoints set in origo.js. Default is 'l' (768px).
`autoHide` | option to set if the mapmenu should close automatically on map click. Accepted values are 'always' (mapmenu is always closed on map click), 'mobile' (mapmenu is closed on map click if map size is 'm' or smaller (see breakpoints in origo.js)) and 'never' (mapmenu is never closed on map click, this is the default setting).
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example mapmenu control

```json
{
  "name": "mapmenu",
  "options": {
    "isActive": true
  }
}
```
