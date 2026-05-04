# Metrics Knowledge Base

This folder contains CartChief's metric definitions, reporting schedules, and analytical frameworks.

## File Structure

```
metrics/
├── README.md (this file)
├── kpi-definitions.md
├── reporting-schedule.md
├── dashboard-links.md
├── anomaly-thresholds.md
└── historical-logs/
    ├── daily/
    ├── weekly/
    └── monthly/
```

## Usage

CartChief reads these files to:
- Understand what metrics to track
- Know when and where to report
- Apply consistent definitions across reports
- Detect anomalies using defined thresholds

## Security Note

This folder may contain historical logs with business-sensitive data. 
Ensure it's properly git-ignored in production deployments.