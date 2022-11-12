# [WIP] GRASS GIS Extension Specification

- **Title:** grass
- **Identifier:** <https://stac-extensions.github.io/grass/v1.0.0/schema.json>
- **Field Name Prefix:** grass
- **Scope:** Item, Collection, Catalog
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @cwhite911

This document explains the GRASS GIS Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

GRASS GIS metadata...

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example "GRASS Location"](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
  - [Collection example "GRASS Mapset"](examples/PERMANENT.json): Shows the basic usage of the extension in a STAC Collection
  - [Catalog example "GRASS database"](examples/catalog.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## GRASS Metadata Commands

Candidate GRASS commands for metadata production:

- [x] g.region - Region Boundaries
- [x] g.proj - CRS information
- [x] *.info - Basic metadata
- [x] *.out.color - Exports color table
- [x] t.rast.colors - Export temporal raster color table
- [ ] r.describe - Range of category values
- [x] *.category - Category information
- [x] *.univar - Univariate statistics
- [x] t.*.univar - Temporal univariate Statistics
- [x] *.stats - General statistics
- [ ] *.report - Report statistics
- [x] r.out.png - Export raster thumbnail

Once a spec is agreed upon we can develop a GRASS module `*.out.stac` to generate a grassdata STAC.

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [x] Catalogs
- [x] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [x] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name           | Type                      | Description |
| -------------------- | ------------------------- | ----------- |
| grass:type           | string [grassdata, location, mapset, raster, vector, strds] | **REQUIRED**. The GRASS GIS object type |
| grass:datatype       | string                    | The GRASS datatype (e.g. CELL, FCELL, DCELL, etc..) (r.info datatype) |
| grass:description    | string                    | GRASS GIS Processing metadata (r.info metadata) |
| grass:comments       | string                    | (r.info comments) |
| grass:creator        | string                    | (r.info creator) |
| grass:ewres          | \[number]                 | The east west spatial resolution (r.info ewres) |
| grass:nsres          | \[number]                 | The north south spatial resolution (r.info nsres) |
| grass:cols           | \[number]                 | The number of columns in the raster (r.cols nsres) |
| grass:location       | string                    | The name of the GRASS location (i.e., project) |
| grass:mapset         | string                    | The name of the GRASS mapset (i.e., sub-project) |
| grass:map            | string                    | (r.info map) |
| grass:maptype        | string                    | (r.info maptype) |
| grass:min            | \[number]                 | The min data value (r.info min)  |
| grass:max            | \[number]                 | The max data value (r.info max) |
| grass:ncats          | \[number]                 | The max data value (r.info ncats) |
| grass:semantic_label | string                    | The semantic_label (r.info semantic_label) |
| grass:source1        | string                    | The source1 value (r.info source1) |
| grass:source2        | string                    | The source1 value (r.info source1) |
| grass:color_table    | string                    | *.colors.out  |

### Additional Field Information

#### template:new_field

This is a much more detailed description of the field `template:new_field`...

<!-- ### XYZ Object

This is the introduction for the purpose and the content of the XYZ Object...

| Field Name  | Type   | Description |
| ----------- | ------ | ----------- |
| x           | number | **REQUIRED**. Describe the required field... |
| y           | number | **REQUIRED**. Describe the required field... |
| z           | number | **REQUIRED**. Describe the required field... |

## Relation types

The following types should be used as applicable `rel` types in the
[Link Object](https://github.com/radiantearth/stac-spec/tree/master/item-spec/item-spec.md#link-object).

| Type                | Description |
| ------------------- | ----------- |
| fancy-rel-type      | This link points to a fancy resource. | -->


## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
