# Changelog

All the project changes should be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Do not edit the NEW_VERSION and VERSION_DATE fields, they will be updated automatically by the Github Action script.

## [<NEW_VERSION>] - <VERSION_DATE>
### Added
- Meta Attribution Fix GTM variable template: fallback campaign source (`facebook`) or medium (`organic`) when `fbclid` is present and both `utm_source` and `utm_medium` are missing
- Template preview help: create one variable for `campaign_source` and one for `campaign_medium` in the GA4 config tag Shared event settings; the variable returns undefined when `fbclid` is missing or a UTM is already on the URL
- Unit tests for custom source and medium values, UTM letter case, empty `fbclid`, UTMs without `fbclid`, whitespace UTMs, and an unknown output mode
### Changed
- Removed the Recommended setup section from the variable template
