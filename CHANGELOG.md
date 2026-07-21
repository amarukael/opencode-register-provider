# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.3] - 2026-07-21

### Fixed
- **Robust JSONC parser** - Better handling of corrupt config files
- **BOM detection** - Automatically remove Byte Order Mark if present
- **Control character removal** - Strip invalid control characters from config
- **Better error messages** - Helpful suggestions when config is corrupted
- **Auto-backup suggestion** - Guides user to backup corrupt file before fix

### Changed
- Enhanced `loadConfig()` with better error handling and diagnostics
- Improved error messages with actionable suggestions

## [1.0.2] - 2026-07-21

### Added
- CLI flags support: `--version`, `-v`, `--help`, `-h`
- Auto-fix trailing commas in JSONC parser
- Better JSONC compatibility (supports trailing commas in config files)

### Fixed
- JSONC parser now properly handles trailing commas
- Improved error messages for config parsing

## [1.0.1] - 2026-07-21

### Fixed
- Critical bug: corrected encoding typo from 'utf-0' to 'utf-8' in saveAuthConfig
- This was causing "Bad control character" JSON parse errors

## [1.0.0] - 2026-07-21

### Added
- Initial release
- Interactive CLI for registering OpenAI-compatible providers
- Auto-fetch models from `/v1/models` endpoint
- Flexible model selection (comma-separated, range, or all)
- JSONC support with fallback to JSON
- Auto-generate `opencode.jsonc` config
- Auto-save credentials to `~/.local/share/opencode/auth.json`
- Smart config file detection (local and global)
- Overwrite protection for existing providers
- Comprehensive error handling and user-friendly messages
