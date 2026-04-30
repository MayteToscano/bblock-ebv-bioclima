
# Data Provenance (Schema)

`syke.ebv.phenology.data-provenance` *v1.0*

W3C PROV lineage: sensor, algorithm, workflow, agents.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Data Provenance
MODIS Terra L1B → FSC/NDWI → VAP. Agent: Kristin Böttcher (SYKE).

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: W3C PROV data provenance
type: object
properties:
  sensor:
    type: string
  platform:
    type: string
  algorithm:
    type: object
    properties:
      name:
        type: string
      version:
        type: string
  agent:
    type: object
    properties:
      name:
        type: string
      institution:
        type: string

```

Links to the schema:

* YAML version: [schema.yaml](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/data-provenance/schema.json)
* JSON version: [schema.json](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/data-provenance/schema.yaml)

## Sources

* [W3C PROV-O](https://www.w3.org/TR/prov-o/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/MayteToscano/bblock-ebv-bioclima](https://github.com/MayteToscano/bblock-ebv-bioclima)
* Path: `_sources/data-provenance`

