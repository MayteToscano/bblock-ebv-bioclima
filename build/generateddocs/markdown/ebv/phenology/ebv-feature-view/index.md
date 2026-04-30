
# EBV Feature View (Schema)

`syke.ebv.phenology.ebv-feature-view` *v1.0*

Discovery layer: GeoJSON Feature with EBV phenology properties linked to CoverageJSON building blocks via semantic context. Enables map visualization in OGC BB viewer.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# EBV Feature View

Discovery layer for the OGC Building Blocks map viewer. Represents EBV raster coverage metadata as GeoJSON Features with semantically linked properties.

## Why this block exists

The OGC BB viewer only renders GeoJSON Features on its map. The CoverageJSON blocks model the raster correctly but cannot be visualized in the default viewer. This block bridges both worlds:

- **GeoJSON geometry**: Finland bounding box as polygon (for the map)
- **Semantic properties**: Each property is linked via `context.jsonld` to ontology URIs
- **Click → linked descriptions**: When you click a feature on the map, property names link to their definitions in other building blocks

## Properties → Building Block Links

| Property | Ontology URI | Defined in |
|----------|-------------|------------|
| `entity_type` | `ebv:entity_type` | EBV Ontology |
| `year` | `ebv:year` | EBV Ontology |
| `vap_doy` | `ebv:vap_doy` | CovJSON Parameter |
| `mean_doy` | `ebv:mean_doy` | CovJSON NdArray (statistics) |
| `crs` | `covjson:referenceSystem` | CovJSON Reference System |
| `grid_width` | `covjson:axisSize` | CovJSON Axis |
| `sensor` | `prov:wasGeneratedBy` | Data Provenance |
| `algorithm` | `prov:used` | Data Provenance |
| `trend_slope` | `ebv:trend_slope` | Phenology Indicators |

## [→ Interactive CoverageJSON Viewer](../../viewer/)

For full raster visualization with pixel-level click interaction, use the dedicated CoverageJSON viewer.

## Examples

### Finland VAP feature collection (map view)
GeoJSON FeatureCollection for map visualization. Each feature represents one 
annual raster band with Finland bounding box geometry. Properties are semantically 
linked to EBV ontology and CoverageJSON building blocks via context.jsonld.
Click on map features to see linked property descriptions.

#### json
```json
{
  "type": "FeatureCollection",
  "name": "EBV_Phenology_Finland_VAP",
  "features": [
    {
      "type": "Feature",
      "id": "vap-coniferous-2001",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "mean_doy": 106.4,
        "min_doy": 65,
        "max_doy": 138,
        "stddev": 12.5,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[14.10,57.75],[35.23,57.75],[35.23,71.17],[14.10,71.17],[14.10,57.75]]]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2002",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2002,
        "vap_doy": 95,
        "mean_doy": 94.7,
        "min_doy": 64,
        "max_doy": 124,
        "stddev": 8.5,
        "valid_percent": 11.09,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[14.10,57.75],[35.23,57.75],[35.23,71.17],[14.10,71.17],[14.10,57.75]]]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2003",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2003,
        "vap_doy": 111,
        "mean_doy": 111.4,
        "min_doy": 65,
        "max_doy": 134,
        "stddev": 13.9,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[14.10,57.75],[35.23,57.75],[35.23,71.17],[14.10,71.17],[14.10,57.75]]]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2001",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2001,
        "vap_doy": 125,
        "mean_doy": 125.0,
        "min_doy": 88,
        "max_doy": 162,
        "stddev": 14.5,
        "valid_percent": 25.0,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[14.10,57.75],[35.23,57.75],[35.23,71.17],[14.10,71.17],[14.10,57.75]]]
      }
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": [
    {
      "ebv": "https://w3id.org/ogc/hosted/ebv-phenology/"
    },
    "https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/context.jsonld"
  ],
  "type": "FeatureCollection",
  "name": "EBV_Phenology_Finland_VAP",
  "features": [
    {
      "type": "Feature",
      "id": "vap-coniferous-2001",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "mean_doy": 106.4,
        "min_doy": 65,
        "max_doy": 138,
        "stddev": 12.5,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2002",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2002,
        "vap_doy": 95,
        "mean_doy": 94.7,
        "min_doy": 64,
        "max_doy": 124,
        "stddev": 8.5,
        "valid_percent": 11.09,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2003",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2003,
        "vap_doy": 111,
        "mean_doy": 111.4,
        "min_doy": 65,
        "max_doy": 134,
        "stddev": 13.9,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2001",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2001,
        "vap_doy": 125,
        "mean_doy": 125.0,
        "min_doy": 88,
        "max_doy": 162,
        "stddev": 14.5,
        "valid_percent": 25.0,
        "crs": "CRS84",
        "grid_width": 320,
        "grid_height": 200,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "no"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    }
  ]
}
```

#### ttl
```ttl


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: EBV phenology properties for map feature view
type: object
properties:
  entity_type:
    type: string
    description: Forest entity type (Coniferous, Deciduous)
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/entity_type
    x-jsonld-type: '@id'
    x-jsonld-base: https://w3id.org/ogc/hosted/ebv-phenology/
  year:
    type: integer
    description: Observation year
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/year
  vap_doy:
    type: integer
    description: Start of Vegetation Active Period in Day of Year
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/vap_doy
  mean_doy:
    type: number
    description: Mean DOY across valid pixels for this band
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/mean_doy
  min_doy:
    type: integer
    description: Minimum DOY value in this band
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/min_doy
  max_doy:
    type: integer
    description: Maximum DOY value in this band
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/max_doy
  stddev:
    type: number
    description: Standard deviation of DOY values
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/stddev
  valid_percent:
    type: number
    description: Percentage of valid (non-masked) pixels
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/valid_percent
  crs:
    type: string
    description: Coordinate reference system
    x-jsonld-id: https://covjson.org/def/core#referenceSystem
  grid_width:
    type: integer
    description: Number of grid columns
    x-jsonld-id: https://covjson.org/def/core#axisSize
  grid_height:
    type: integer
    description: Number of grid rows
    x-jsonld-id: https://covjson.org/def/core#axisSize
  sensor:
    type: string
    description: Source sensor platform
    x-jsonld-id: http://www.w3.org/ns/prov#wasGeneratedBy
  algorithm:
    type: string
    description: Derivation algorithm
    x-jsonld-id: http://www.w3.org/ns/prov#used
  trend_slope:
    type: number
    description: Linear trend slope in days per year
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/trend_slope
  anomaly:
    type: string
    description: Whether this year is anomalous
    x-jsonld-id: https://w3id.org/ogc/hosted/ebv-phenology/anomaly
required:
- entity_type
- year
- vap_doy
x-jsonld-prefixes:
  ebv: https://w3id.org/ogc/hosted/ebv-phenology/
  covjson: https://covjson.org/def/core#
  prov: http://www.w3.org/ns/prov#
  qudt: http://qudt.org/schema/qudt/

```

Links to the schema:

* YAML version: [schema.yaml](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/schema.json)
* JSON version: [schema.json](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "entity_type": {
      "@context": {
        "@base": "https://w3id.org/ogc/hosted/ebv-phenology/"
      },
      "@id": "ebv:entity_type",
      "@type": "@id"
    },
    "year": "ebv:year",
    "vap_doy": "ebv:vap_doy",
    "mean_doy": "ebv:mean_doy",
    "min_doy": "ebv:min_doy",
    "max_doy": "ebv:max_doy",
    "stddev": "ebv:stddev",
    "valid_percent": "ebv:valid_percent",
    "crs": "covjson:referenceSystem",
    "grid_width": "covjson:axisSize",
    "grid_height": "covjson:axisSize",
    "sensor": "prov:wasGeneratedBy",
    "algorithm": "prov:used",
    "trend_slope": "ebv:trend_slope",
    "anomaly": "ebv:anomaly",
    "ebv": "https://w3id.org/ogc/hosted/ebv-phenology/",
    "covjson": "https://covjson.org/def/core#",
    "prov": "http://www.w3.org/ns/prov#",
    "qudt": "http://qudt.org/schema/qudt/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/context.jsonld)

## Sources

* [OGC API - Features, Part 1, 7.16.2: Feature Response](https://docs.ogc.org/is/17-069r3/17-069r3.html#_response_7)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/MayteToscano/bblock-ebv-bioclima](https://github.com/MayteToscano/bblock-ebv-bioclima)
* Path: `_sources/ebv-feature-view`

