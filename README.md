# Game Packs Index

Central registry for game packs. This repository contains the `index.json` file that lists all available game packs.

## How It Works

The companion app fetches `index.json` from this repository to discover available game packs. Users can then install packs directly from the in-app browser.

## Adding a New Pack

1. Create a new repository for your game pack (see [pack-league](https://github.com/Lucidiac/pack-league) as a template)
2. Set up GitHub Actions to build and release your pack
3. Submit a PR to this repository adding your pack to `index.json`

## Index Schema

```json
{
  "version": 1,
  "updated_at": "ISO8601 timestamp",
  "packs": [
    {
      "id": "unique-pack-id",
      "game_id": 1,
      "name": "Full Game Name",
      "short_name": "Short",
      "description": "Description of what this pack does",
      "icon_url": "URL to pack icon (256x256 PNG)",
      "repo": "github.com/org/repo",
      "maintainers": ["@github-username"],
      "latest": {
        "version": "semver version",
        "released_at": "ISO8601 timestamp",
        "min_app_version": "minimum companion app version",
        "artifacts": {
          "platform": {
            "daemon_url": "URL to daemon binary",
            "daemon_sha256": "SHA256 checksum",
            "frontend_url": "URL to frontend bundle",
            "frontend_sha256": "SHA256 checksum"
          }
        }
      },
      "categories": ["category1", "category2"],
      "features": ["feature1", "feature2"]
    }
  ]
}
```

## Supported Platforms

- `darwin-arm64` - macOS Apple Silicon
- `darwin-x64` - macOS Intel
- `win32-x64` - Windows 64-bit
- `linux-x64` - Linux 64-bit

## Review Process

All PRs to this repository are manually reviewed to ensure:
- Pack follows the expected structure
- Artifact URLs are valid and accessible
- Checksums match the actual files
- No malicious code or behavior
