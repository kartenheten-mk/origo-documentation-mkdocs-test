# Source

The `source` option defines named sources that some layer types uses, typically service based sources. Most file based
sources only defines its source in the layer configuration.

Each source is defined as a json object with its
name as object name. This name is used by layers to reference the source.

The options that are available for a source depends on the type of layer and is described under each layer type.



#### Example defining sources

```json
{
  "source": {
    "local_wms": {
      "url": "http://localhost/geoserver/origo/wms"
    },
    "local_wmts": {
      "url": "http://localhost/geowebcache/service/wmts"
    }
  }
}
```
