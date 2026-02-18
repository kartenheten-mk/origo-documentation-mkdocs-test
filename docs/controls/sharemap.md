# Sharemap control

Creates a shareable link to the map. Current extent and zoom, visible layers and the map pin (if applicable) will be shared. If a feature in the map is selected, the id of the feature will be in the link making the map zoom to it on load. This goes for WFS, Geojson, Topojson and AGS Feature layers. The sharemap control also comes with the option to save map state on the server (requires Origo Server). A saved map state is retrieved with an ID instead of an URL. Adds a button to the mapmenu. **NOTE** - requires mapmenu control.

Property | Description
---|---
`name` | the name of the control (sharemap)
`options` | options for the control

Option | Description
---|---
`storeMethod` | Should be set to `saveStateToServer` in order to utilize the save-to-server feature.
`serviceEndpoint` | URL to the Origo Server service endpoint, for example `https://www.mydomain.com/mapstate`.
`loadMapStateIdMethod` | Controls how a saved map state (mapStateId) is loaded from the server, "path" (default) or "query".
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`icon` | icon for the menuitem in the menu. Defaults to "#ic_screen_share_outline_24px".
`title` | title for the menuitem in the menu. Defaults to "Dela karta".

#### Example sharemap control

```json
{
  "name": "sharemap"
}
```
