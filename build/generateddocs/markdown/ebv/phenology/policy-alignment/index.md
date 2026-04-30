
# Policy Alignment (Schema)

`syke.ebv.phenology.policy-alignment` *v1.0*

Maps EBV indicators to GBF, SDGs, IPBES, EU Biodiversity Strategy, Finland NBSAP.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Policy Alignment
GBF Goal A (ecosystem integrity), SDG 15 (life on land), SDG 13 (climate), IPBES, EU Biodiversity 2030, Finland NBSAP.

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: Policy framework alignment
type: object
required:
- frameworks
properties:
  frameworks:
    type: array
    items:
      type: object
      properties:
        name:
          type: string
        alignment_type:
          type: string
          enum:
          - direct
          - indirect
          - supporting
        targets:
          type: array
          items:
            type: string

```

Links to the schema:

* YAML version: [schema.yaml](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/policy-alignment/schema.json)
* JSON version: [schema.json](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/policy-alignment/schema.yaml)

## Sources

* [Kunming-Montreal GBF](https://www.cbd.int/gbf)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/MayteToscano/bblock-ebv-bioclima](https://github.com/MayteToscano/bblock-ebv-bioclima)
* Path: `_sources/policy-alignment`

