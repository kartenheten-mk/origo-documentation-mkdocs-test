# Scalepicker control

Adds a scalepicker control that allows the user to change the map scale using a dropdown list of predefined scales. The available scales are determined by the resolutions specified in index.json.

Property | Description
---|---
`name` | the name of the control (scalepicker)
`options` | options for the control

Option | Description
---|---
`buttonPrefix` | text to show before the scale value on the control button
`listItemPrefix` | text to show before the scale value in the dropdown list
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example scalepicker control

```json
{
  "name": "scalepicker",
  "options": {
    "buttonPrefix": "Scale: ",
    "listItemPrefix": "Scale: "
  }
}
```
