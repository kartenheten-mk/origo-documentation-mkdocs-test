# Search control

Adds a search control. The search control requires a search end point to function.

The search control uses autocomplete. Autocomplete suggestions may optionally be grouped with headings, e g with one group of suggestions per layer.

There are several ways to configure how selected search result should be handled.
All options require that `url` and `searchAttribute` are provided.
* Option 1. Feature info is requested from a map service, which is used to get the geometry and attributes. The layer is defined
as an ordinary layer in the layer config section.
   Additional search options required: `geometryAttribute`, `idAttribute` and `layerNameAttribute`
* Option 2. Same as option 1 but for single layer search. `layerName` is defined
as an option and is not included in the search response.
   Additional search options required: `geometryAttribute` and `layerName`
* Option 3. Complete feature info is included in the search result.
   Additional search options required: `geometryAttribute`, `titleAttribute` and `contentAttribute`
* Option 4. This is a single table search. No layer is defined.
   Additional search options required: `geometryAttribute` and `title`
* Option 5. Feature info is shown without selection in the map. This is a simple single table search.
   Additional search options required: `title`, `northing` and `easting`

Property | Description
---|---
`name` | the name of the control (search)
`options` | options for the control

Option | Description
---|---
`url` | url to the search endpoint. Always required.
`queryParameterName` | name of the parameter in the search request containing the query. Default is 'q'.
`searchAttribute` | the attribute that will be queried. Always required.
`northing` | the attribute for northing coordinates. Only if geometryAttribute is not provided.
`easting` | the attribute for easting coordinates. Only if geometryAttribute is not provided.
`title` | title for the popup presenting the search result
`hintText` | placeholder text for the search input. Default is Sök.
`limit` | the max number of suggestions to be displayed. Default is 9.
`minLength` | minimum number of characters to trigger search. Default is 4.
`groupSuggestions` | whether to group autocomplete suggestions or not. Depending on the configuration option used (see above), titles are set using the `title` properties of defined map layers (options 1 and 2), values from the attribute in the result defined by `titleAttribute` (3) or the `title` search control configuration option (4 and 5). Defaults to false.
`geometryAttribute` | geometry attribute is required if northing and easting are not used.
`maxZoomLevel` | maximum zoom level after selection. Default is 2.
`idAttribute` | attribute in the response storing the feature id.
`layerNameAttribute` | attribute in the response storing the layer name. The layer must be defined in the map.
`layerName` | layer defined in map if not included in the search response.
`titleAttribute` | attribute in response storing the featureinfo title.
`contentAttribute` | attribute in response storing the featureinfo content.
`includeSearchableLayers` | whether to include searchable layers in query string or not. Defaults to false.
`searchableDefault` | default value for searchable. 'always', true (searchable when visible) or false. Defaults to false.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`queryType` | if set this value will be passed on as a parameter in the search request like '&t=valueOfQueryType'.
`autocompletePlacement` | placement of the autocomplete suggestions. Can be search, left or floating. Defaults to search.
`searchlistOptions` | object with options for the searchlist. By setting the placement option the searchlist is activated.
`suppressDialog`| boolean, default false. When set to true no popup will be displayed when a search result is selected, it will only be highlighted and zoomed to.

searchList: When the user presses Enter, a new window opens, which can be used to interact with the search results

searchlistOptions | Description
---|---
`placement` | placement of the result. Can be left or floating and is activated by hitting enter (defaults to nothing).
`export` | Make result exportable. Default is false
`exportUrl` | url to export service. Eg "//origoserver/excelcreator"
`exportButtonText` | export button text. Default is "Export".
`exportFilename` | name of exported file. Default is export.xlsx.
`exportExcludedFields` | array of field to exclude in the export. Eg ["GEOM", "label", "value"]
`makeSelectionButton` | show a button to make a selection of the result. Default is false.
`makeSelectionButtonText` | button text. Default is "Använd som urval"
`roundButton` | round or not. Default is false.
`title` | title for the searchlist, defaults to 'Sökresultat för "{{value}}"', {{value}} will be replaced with the search input.


#### Example search response

```json
{
  "NAMN":"Drottninggatan 13",
  "N":6610524.99261475,
  "E":151466.20581054702
}
```

#### Example search control (option 1)

```json
{
  "name": "search",
  "options": {
      "url": "http://localhost:3000/adressok",
      "searchAttribute": "NAMN",
      "layerNameAttribute": "TYPE",
      "idAttribute": "GID",
      "geometryAttribute": "GEOM",
      "hintText": "Sök adress eller platser...",
      "searchlistOptions":{
        "placement": "left"
      }
  }
}
```

#### Example search control (option 2)

```json
{
  "name": "search",
  "options": {
      "url": "http://localhost:3000/adressok",
      "searchAttribute": "NAMN",
      "layerName": "TYPE",
      "geometryAttribute": "GEOM",
      "hintText": "Sök adress eller platser..."
  }
}
```

#### Example search control (option 3)

```json
{
  "name": "search",
  "options": {
      "url": "http://localhost:3000/adressok",
      "searchAttribute": "NAMN",
      "titleAttribute": "TYPE",
      "contentAttribute": "NAMN",
      "geometryAttribute": "GEOM",
      "hintText": "Sök adress eller platser..."
  }
}
```

#### Example search control (option 4)

```json
{
  "name": "search",
  "options": {
      "url": "http://localhost:3000/adressok",
      "searchAttribute": "NAMN",
      "geometryAttribute": "GEOM",
      "title": "Adress",
      "hintText": "Sök adress eller platser..."
  }
}
```

#### Example search control (option 5)

```json
{
  "name": "search",
  "options": {
      "url": "http://localhost:3000/adressok",
      "searchAttribute": "NAMN",
      "northing": "N",
      "easting": "E",
      "title": "Adress",
      "hintText": "Sök adress eller platser..."
  }
}
```
