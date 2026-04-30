
# Phenology Indicators (Schema)

`syke.ebv.phenology.phenology-indicators` *v1.0*

Temporal trend analysis, anomaly detection, change points derived from multi-temporal EBV coverage.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Phenology Indicators
Trends (-0.45 d/yr), anomalies (2001, 2007, 2015), change points. Depends on CovJSON Coverage.

## Examples

### Coniferous VAP linear trend
Advancing phenology -0.45 d/yr (p=0.05)
#### json
```json
{"indicator_type":"linear_trend","coverage_id":"finland-vap-coniferous","ebv_entity":"Coniferous","trend":{"slope":-0.45,"r_squared":0.35,"p_value":0.05},"anomalous_years":[2001,2007,2015],"interpretation":{"climate_signal":"advancing","confidence":"medium","summary":"Green-up advancing ~0.45 d/yr, consistent with spring warming."}}

```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: Phenology temporal indicators
type: object
required:
- indicator_type
properties:
  indicator_type:
    type: string
    enum:
    - linear_trend
    - anomaly_index
    - change_point
    - acceleration
  coverage_id:
    type: string
  ebv_entity:
    type: string
  trend:
    type: object
    properties:
      slope:
        type: number
      r_squared:
        type: number
      p_value:
        type: number
  anomalous_years:
    type: array
    items:
      type: integer
  interpretation:
    type: object
    properties:
      climate_signal:
        type: string
      confidence:
        type: string
      summary:
        type: string

```

Links to the schema:

* YAML version: [schema.yaml](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/phenology-indicators/schema.json)
* JSON version: [schema.json](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/phenology-indicators/schema.yaml)


# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/MayteToscano/bblock-ebv-bioclima](https://github.com/MayteToscano/bblock-ebv-bioclima)
* Path: `_sources/phenology-indicators`

