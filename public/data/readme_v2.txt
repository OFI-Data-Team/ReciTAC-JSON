# ReciTAC JSON v2

This document describes the new JSON data version in `ReciTAC_data.json`.

## Overview

The v2 data is generated based on the existing production JSON as of `2026-03-19`:

- `https://nbremer.github.io/ReciTAC/data/ReciTAC_data.json`

The goal is to preserve the existing structure so it does not break current code that already depends on that JSON format.

The new version keeps the existing JSON structure and adds:

- a top-level `metadata` object
  - `metadata.generation_time`
- bilingual nested fields for selected values

The `metadata` block is placed at the top of the JSON.

## Metadata

Top-level metadata now looks like this:

```json
"metadata": {
  "generation_time": "2026-03-19T13:28:52.506511+00:00"
}
```

## Bilingual Fields

Some fields are now represented as nested language objects instead of only flat `*_EN` or `*_FR` values.

Structure:

```json
"fieldName": {
  "en": "English content",
  "fr": "French content"
}
```

Example:

```json
"storyName": {
  "en": "Land-to-Sea continuum",
  "fr": "À venir -  titre en français"
}
```

If only one language is available, only that language is included.

Example:

```json
"partnerName": {
  "en": "academic and research institutions in Canada (including research hospitals)"
}
```

If both language values are missing, the nested field is not included.

## Update JSON

`updated_v2.json` is for a quick overlook of what was added in the v2 data compared with the base JSON.

## Notes

- The original flat fields such as `*_EN` and `*_FR` are still present
- The new nested bilingual fields are added alongside the original fields
- Some records may contain only `en`
- Some records may contain both `en` and `fr`
- Fields with no available language content are omitted
