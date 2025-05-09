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

The configuration defines core hours for each region using 24-hour UTC time:

Region schedules:
- NA East (1): 00:00-03:00 UTC
- Europe (2): 18:00-21:00 UTC
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
          "startHour": number,  // Hour in UTC (0-23)
          "endHour": number,    // Hour in UTC (0-23)
          "active": boolean
        }
      }
    }
  }
}
```

Note: For times that cross midnight (e.g., 23:00-02:00), the endHour will be less than startHour.
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
