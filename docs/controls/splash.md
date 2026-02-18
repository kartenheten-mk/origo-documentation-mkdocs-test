# Splash control

Adds a splash control. It will show a modal window when the map is loaded. The content can defined in the content option or as a html file.

Property | Description
---|---
`name` | the name of the control (splash)
`options` | options for the control

Option | Description
---|---
`title` | modal title text
`url` | url to a html file
`content` | content text of the modal
`hideButton` | adds button to stop the current splash from displaying on subsequent visits to the map. If the content is updated, the splash will be displayed again. Options available are 'visible' (the only option required), 'hideText' and 'confirmText'.
`style` | adds the css style to the splash window.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

#### Example splash control

```json
{
  "name": "splash",
  "options": {
    "url": "examples/splash-content.html",
    "hideButton": {
      "visible": true
    },
    "style": "width: 600px;"
  }
}
```
