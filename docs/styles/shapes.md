# Shapes

### Fill

A fill style can be defined with the OpenLayers options for a [Fill](https://openlayers.org/en/latest/apidoc/module-ol_style_Fill-Fill.html).

#### Fill example

```json
{
  "fill": {
    "color": "rgba(0,0,0,0.5)"
  }
}
```

### Stroke

A stroke style can be defined with the OpenLayers options for a [Stroke](https://openlayers.org/en/latest/apidoc/module-ol_style_Stroke-Stroke.html).

#### Stroke example

```json
{
  "stroke": {
    "color": "rgba(0,0,0,1.0)",
    "width": 2
  }
}
```

### Circle

A circle style can be defined with the OpenLayers options for a [Circle](https://openlayers.org/en/latest/apidoc/module-ol_style_Circle-CircleStyle.html). Radius defaults to 7.

#### Circle example

```json
{
  "circle": {
    "radius": 16,
    "stroke": {
      "color": "rgba(0,0,0,1)",
      "width": 5
    },
    "fill": {
      "color": "rgba(255,255,255,0.9)"
    }
  }
}
```

### Square

A square style can be defined with the help of a subset of OpenLayers [RegularShape](https://openlayers.org/en/latest/apidoc/module-ol_style_RegularShape-RegularShape.html). Rotation attribute defaults to 0, value should be set in radian. Scale attribute defaults to no scaling factor, preferred to use radius to control size of style object. Radius defaults to 7.

#### Square example

```json
{
  "square": {
    "radius": 7,
    "stroke": {
      "color": "rgba(0,0,0,1)",
      "width": 1,
      "lineDash": [1, 2]
    },
    "fill": {
      "color": "rgba(255,255,0,0.9)"
    },
    "rotation": 0.5
  }
}
```

### Triangle

A triangle style can be defined with the help of a subset of OpenLayers [RegularShape](https://openlayers.org/en/latest/apidoc/module-ol_style_RegularShape-RegularShape.html). Rotation attribute defaults to 0, value should be set in radian. Scale attribute defaults to no scaling factor, preferred to use radius to control size of style object. Radius defaults to 7.

#### Triangle example

```json
{
  "triangle": {
    "radius": 7,
    "stroke": {
      "color": "rgba(0,0,0,1)",
      "width": 1
    },
    "fill": {
      "color": "rgba(0,255,0,0.9)"
    },
    "rotation": 0.5
  }
}
```

### Star

A star style can be defined with the help of a subset of OpenLayers [RegularShape](https://openlayers.org/en/latest/apidoc/module-ol_style_RegularShape-RegularShape.html). Scale attribute defaults to no scaling factor, preferred to use radius to control size of style object. Radius defaults to 7.

#### Star example

```json
{
  "star": {
    "radius": 7,
    "stroke": {
      "color": "rgba(0,0,0,1)",
      "width": 1
    },
    "fill": {
      "color": "rgba(0, 0, 255, 0.9)"
    },
    "scale": 1.5
  }
}
```

### Pentagon

A pentagon style can be defined with the help of a subset of OpenLayers [RegularShape](https://openlayers.org/en/latest/apidoc/module-ol_style_RegularShape-RegularShape.html). Scale attribute defaults to no scaling factor, preferred to use radius to control size of style object. Radius defaults to 7.

#### Pentagon example

```json
{
  "pentagon": {
    "radius": 10,
    "stroke": {
      "color": "rgba(0,0,0,1)",
      "width": 1
    },
    "fill": {
      "color": "rgba(0, 0, 255, 0.9)"
    }
  }
}
```

### Cross

A cross style can be defined with the help of a subset of OpenLayers [RegularShape](https://openlayers.org/en/latest/apidoc/module-ol_style_RegularShape-RegularShape.html). Scale attribute defaults to no scaling factor, preferred to use radius to control size of style object. Radius defaults to 7.

#### Cross example

```json
{
  "cross": {
    "radius": 7,
    "stroke": {
      "color": "rgb(255, 0, 255)",
      "width": 2
    }
  }
}
```

### X

A x style can be defined with the help of a subset of OpenLayers [RegularShape](https://openlayers.org/en/latest/apidoc/module-ol_style_RegularShape-RegularShape.html). Scale attribute defaults to no scaling factor, preferred to use radius to control size of style object. Radius defaults to 7.

#### X example

```json
{
  "x": {
    "radius": 7,
    "stroke": {
      "color": "rgb(1, 222, 252)",
      "width": 2
    }
  }
}
```
