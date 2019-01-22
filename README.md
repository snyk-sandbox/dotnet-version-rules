# dotnet-version-rules

## NUnit versions

- 2.5.7.10213
- 2.5.9.10348
- 2.5.10.11092
- 2.6.0.12051
- 2.6.0.12054
- 2.6.1
- 2.6.2
- 2.6.3
- 2.6.4
- 2.6.5
- 2.6.6
- 2.6.7
- 2.7.0
- 3.0.0-alpha
- 3.0.0-alpha-2
- 3.0.0-alpha-3
- 3.0.0-alpha-4
- 3.0.0-alpha-5
- 3.0.0-beta-1
- 3.0.0-beta-2
- 3.0.0-beta-3
- 3.0.0-beta-4
- 3.0.0-beta-5
- 3.0.0-rc
- 3.0.0-rc-2
- 3.0.0-rc-3
- 3.0.0
- 3.0.1
- 3.2.0
- 3.2.1
- 3.4.0
- 3.4.1
- 3.5.0
- 3.6.0
- 3.6.1
- 3.7.0
- 3.7.1
- 3.8.0
- 3.8.1
- 3.9.0
- 3.10.0
- 3.10.1
- 3.11.0

## Rules

1. If we have `*` in version it should be resolved to maximum possible.
    1. `*_fix_resolved_to_max` NUnit 2.6.* -> 2.6.7
    2. `*_minor_resolved_to_max` NUnit 2.* -> 2.7.0
    3. `*_major_resolved_to_max` NUnit * -> 3.11.0
2. If we use exact version in PackageReference it is `>=` by default. NUnit 3.6.2 not existing version. It will be resolved to 3.7.0 (nearest bigger). Example `just_version_is_more_or_equal`.
3. If no version in PackageReference. Will be resolved as minimum possible (2.5.7.10213 in our case). Example `no_version_to_min`.
4. NUnit 3.0 -> 3.0.0 (not `alpha`, `beta` or `rc`). So, minimum possible, but not with prefix. Example `ver_to_min`.
5. TargetFramework really affects dependency list. Example `target_with_deps` and `target_without_deps`.
