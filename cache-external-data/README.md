# `cache-external-data` action

This action caches the *ExternalData* that is fetched via the corresponding
CMake functionality.

## Action parameters

The action has one optional parameter
- `store-key-base`: A base key for storing the cached data. It will be suffixed
  with the current date and defaults to `external-data`
