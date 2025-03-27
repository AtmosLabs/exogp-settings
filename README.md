# ExoGP Settings

This repository contains configuration files for ExoGP services.

## Files

Configuration files are located in the `docs` directory:
- `docs/live.json`: Production configuration settings
- `docs/staging.json`: Staging environment configuration settings

## Usage

Access the configuration files directly via GitHub Pages:
```
https://planetatmos.github.io/exogp-settings/live.json
https://planetatmos.github.io/exogp-settings/staging.json
```

## Core Hours Configuration

The configuration defines core hours for each region. Times are stored as minutes since midnight UTC:
- 0 = 00:00 UTC
- 720 = 12:00 UTC
- 1380 = 23:00 UTC

Region schedules:
- NA East (1): 00:00-03:00 UTC (0-180 minutes)
- Europe (2): 19:00-22:00 UTC (1140-1320 minutes)
- LATAM (4): 23:00-02:00 UTC (1380-120 minutes)
- Singapore (7): 12:00-15:00 UTC (720-900 minutes)
- NA West (9): 03:00-06:00 UTC (180-360 minutes)
- Hong Kong (10): 12:00-15:00 UTC (720-900 minutes)

### Schema

```json
{
  "version": "string",
  "settings": {
    "coreHours": {
      "active": boolean,
      "regions": {
        [regionId: string]: {
          "startMinutes": number,  // Minutes since midnight UTC (0-1439)
          "endMinutes": number,    // Minutes since midnight UTC (0-1439)
          "active": boolean
        }
      }
    }
  }
}
```

Note: For times that cross midnight (e.g., 23:00-02:00), the endMinutes will be less than startMinutes.
This indicates that the time period crosses into the next day.

## Development

This repository includes:
- JSON linting with pre-commit hooks
- Node.js v20.11.1 (via .nvmrc)

To validate JSON files locally:
```bash
npm run lint:json
```

Note: The `/docs` directory is used for GitHub Pages hosting.
