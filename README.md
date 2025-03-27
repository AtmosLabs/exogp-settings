# ExoGP Settings

This repository contains configuration files for ExoGP services.

## Files

Configuration files are located in the `settings` directory:
- `settings/live.json`: Production configuration settings
- `settings/staging.json`: Staging environment configuration settings

## Usage

Access the configuration files directly via GitHub Pages:
```
https://planetatmos.github.io/exogp-settings/settings/live.json
https://planetatmos.github.io/exogp-settings/settings/staging.json
```

## Core Hours Configuration

The configuration defines core hours for each region:

- NA East (1): 00:00-03:00 UTC
- Europe (2): 19:00-22:00 UTC
- LATAM (4): 23:00-02:00 UTC
- Singapore (7): 12:00-15:00 UTC
- NA West (9): 03:00-06:00 UTC
- Hong Kong (10): 12:00-15:00 UTC

### Schema

```json
{
  "version": "string",
  "settings": {
    "coreHours": {
      "active": boolean,
      "regions": {
        [regionId: string]: {
          "startTime": "HH:mm:ssZ",
          "endTime": "HH:mm:ssZ",
          "active": boolean
        }
      }
    }
  }
}
```

## Development

This repository includes:
- JSON linting with pre-commit hooks
- Node.js v20.11.1 (via .nvmrc)

To validate JSON files locally:
```bash
npm run lint:json
