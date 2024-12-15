# Format versioning

Versioning of the FEF format is heavily inspired by the [Semantic Versioning](https://semver.org/) specification with minor modifications.

## Version format

The version format is a sequence of three numbers separated by dots. The numbers are:
1. Major version
2. Minor version
3. Micro version (patch)

The version format is `MAJOR.MINOR.MICRO`.

Major version is incremented when non-backwards compatible changes are made to the format. If the major version is 0, no backwards compatibility is guaranteed.

Minor version is incremented when backwards compatible but non-forward compatible changes are made to the format.

Micro version is incremented when backwards and forwards compatible changes are made to the format.

## Compatibility of changes

### Backwards compatible changes

Two versions are backwards compatible if a file created in accordance with the older version is valid according to the newer version. By valid it is meant that the file can be parsed and the data can be extracted from it.

### Forward compatible changes

Two versions are forward compatible if a file created in accordance with the newer version is valid according to the older version. By valid it is meant that the file can be parsed and the data can be extracted from it.

If the newer version added some non-critical data to the file (e.g. a new metadata field) and the older version can ignore this data, the versions are forward compatible.

## 0.x.x versions

Versions with major version 0 are considered unstable and no compatibility is guaranteed. The minor and micro versions are subjectively selected to reflect *big* and *small* changes respectively, but no strict rules are enforced.