# Bookmarks control

Adds a bookmarks control. Clicking the button opens a panel with a list of bookmarks. Clicking a bookmark will pan and zoom to the coordinates and zoomLevel specified in the config file. The bookmarks panel is movable.

Property | Description
---|---
`name` | the name of the control (bookmarks)
`options` | options for the control

Option | Description
---|---
`title` | the title shown in the bookmarks panel, also sets the tooltip text. Defaults to `Bokmärken`.
`isActive` | sets whether the control should be active (open) on map load. Defaults to `false`.
`maxZoom` | sets the general zoom level. This zoom level is used if no zoom level is set on the bookmark. Defaults to `15` (or highest available zoom level).
`duration` | sets the duration of the pan and zoom animation in milliseconds. Defaults to `300`.
`items` | list of bookmarks. Configured as an array of objects.
`hideWhenEmbedded` | if set to true, the control is not displayed when the map is embedded. Defaults to `false`.

Items options | Description
---|---
`title` | title of the bookmark.
`coordinates` | array of point coordinates.
`zoomLevel` | target zoom level for the specific bookmark. Optional.

#### Example Bookmarks control

```json
{
  "name": "bookmarks",
  "options": {
    "title": "Bookmarks",
    "isActive": true,
    "duration": 1000,
    "items": [
      {
        "name": "Hudiksvall",
        "coordinates": [1904063, 8794995]
      },
      {
        "name": "Karlstad",
        "coordinates": [1503136, 8262205]
      },
      {
        "name": "Sigtuna",
        "coordinates": [1986473, 8315061],
        "zoomLevel": 10
      }
    ]
  }
}
```
