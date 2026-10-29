
# Route (Schema)

`ogc.demo.route` *v0.1*

A route: a road or path, described as a feature with a length in metres and a line geometry.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Route

A **route** is a road or path that can be followed from one place to another.

In this model a route is an ordinary OGC *feature* (so it can be shared and mapped like any other), with:

- a **geometry** made of one or more lines (`MultiLineString`), so a route can have several segments;
- a **`length`** in metres (required, greater than zero);
- an optional **`name`**.

See the example for a short route in Valencia, Spain.

## Examples

### Riverside route in Valencia
A short route of two separate segments, with its length in metres.
#### json
```json
{
  "type": "Feature",
  "id": "valencia-turia-1",
  "geometry": {
    "type": "MultiLineString",
    "coordinates": [
      [[-0.3763, 39.4699], [-0.3702, 39.4725], [-0.3651, 39.4780]],
      [[-0.3600, 39.4810], [-0.3549, 39.4864], [-0.3490, 39.4915]]
    ]
  },
  "properties": {
    "name": "Turia riverside route",
    "length": 2850
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://avillar.github.io/bblocks-routes-demo/build/annotated/demo/route/context.jsonld",
  "type": "Feature",
  "id": "valencia-turia-1",
  "geometry": {
    "type": "MultiLineString",
    "coordinates": [
      [
        [
          -0.3763,
          39.4699
        ],
        [
          -0.3702,
          39.4725
        ],
        [
          -0.3651,
          39.478
        ]
      ],
      [
        [
          -0.36,
          39.481
        ],
        [
          -0.3549,
          39.4864
        ],
        [
          -0.349,
          39.4915
        ]
      ]
    ]
  },
  "properties": {
    "name": "Turia riverside route",
    "length": 2850
  }
}
```

#### ttl
```ttl
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix ns1: <http://www.opengis.net/def/dataType/OGC/1.1/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://example.com/routes/valencia-turia-1> a geojson:Feature ;
    rdfs:label "Turia riverside route" ;
    ns1:length 2850 ;
    geojson:geometry [ a geojson:MultiLineString ;
            geojson:coordinates ( ( ( -3.763e-01 3.94699e+01 ) ( -3.702e-01 3.94725e+01 ) ( -3.651e-01 3.9478e+01 ) ) ( ( -3.6e-01 3.9481e+01 ) ( -3.549e-01 3.94864e+01 ) ( -3.49e-01 3.94915e+01 ) ) ) ] .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
title: Route
description: A route is a GeoJSON feature with a MultiLineString geometry and a length
  in metres.
type: object
allOf:
- $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/geo/features/feature/schema.yaml
- properties:
    geometry:
      properties:
        type:
          const: MultiLineString
    properties:
      type: object
      required:
      - length
      properties:
        length:
          type: number
          exclusiveMinimum: 0
          description: Length of the route, in metres.
          x-jsonld-id: http://www.opengis.net/def/dataType/OGC/1.1/length
        name:
          type: string
          description: Human-readable name of the route.
          x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  required:
  - geometry
  - properties
x-bblocks-metadata:
  itemIdentifier: ogc.demo.route
  register: https://avillar.github.io/bblocks-routes-demo/build/register.json
  version: '0.1'
  dateOfLastChange: '2026-10-29'

```

Links to the schema:

* YAML version: [schema.yaml](https://avillar.github.io/bblocks-routes-demo/build/annotated/demo/route/schema.json)
* JSON version: [schema.json](https://avillar.github.io/bblocks-routes-demo/build/annotated/demo/route/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "Feature": "geojson:Feature",
    "FeatureCollection": "geojson:FeatureCollection",
    "GeometryCollection": "geojson:GeometryCollection",
    "LineString": "geojson:LineString",
    "MultiLineString": "geojson:MultiLineString",
    "MultiPoint": "geojson:MultiPoint",
    "MultiPolygon": "geojson:MultiPolygon",
    "Point": "geojson:Point",
    "Polygon": "geojson:Polygon",
    "features": {
      "@container": "@set",
      "@id": "geojson:features"
    },
    "type": "@type",
    "id": "@id",
    "properties": "@nest",
    "geometry": {
      "@context": {
        "coordinates": {
          "@container": "@list",
          "@id": "geojson:coordinates"
        }
      },
      "@id": "geojson:geometry"
    },
    "bbox": {
      "@container": "@list",
      "@id": "geojson:bbox"
    },
    "links": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "rdfs:seeAlso"
    },
    "length": "http://www.opengis.net/def/dataType/OGC/1.1/length",
    "name": "rdfs:label",
    "geojson": "https://purl.org/geojson/vocab#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "oa": "http://www.w3.org/ns/oa#",
    "dct": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://avillar.github.io/bblocks-routes-demo/build/annotated/demo/route/context.jsonld)

## Sources

* [OGC API - Features, Part 1: Core (Feature Response)](https://docs.ogc.org/is/17-069r3/17-069r3.html#_response_7)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/avillar/bblocks-routes-demo](https://github.com/avillar/bblocks-routes-demo)
* Path: `_sources/route`

