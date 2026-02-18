# Scale control

Adds a scale control that will show an approximation of the current scale in text.

Property | Description
---|---
`name` | the name of the control (scale)
`options` | options for the control

Option | Description
---|---
`scaleText` | text to show before the scale value.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example scale control

```json
{
  "name": "scale",
  "options": {
    "scaleText": "1:"
  }
}
```
