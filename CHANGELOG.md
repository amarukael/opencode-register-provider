# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
