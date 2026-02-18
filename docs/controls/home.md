# Home control

Sets the map extent to the one specified in the options for the control.

Property | Description
---|---
`name` | the name of the control (home)
`options` | options for the control

Option | Description
---|---
`extent` | The extent to zoom to. If no extent is provided the initial extent of the map will be used.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example home control

```json
{
  "name": "home",
  "options": {
    "extent": [134966, 6593080, 176372, 6636922]
  }
}
```
