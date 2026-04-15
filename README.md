# module-marketing

HARNESS module: campaigns, lead tracking, and review management.

## Entity Contract

- **Produces:** (none)
- **Consumes:** client, content-asset, social-post

## Tools

| Tool | Description |
|------|-------------|
| create-campaign | Assemble content assets into a marketing campaign |
| track-leads | Log a new lead from social media or web |
| send-followup | Send a follow-up message to a lead or client |
| request-review | Send a review request to a completed-job client |

## Hooks

- `PostClientCreated` -> `add-to-drip-campaign`: Adds new clients to the drip campaign.
- `JobCompleted` -> `schedule-review-request`: Schedules a review request after job completion.

## Cron

- `daily-lead-followup` (weekdays 8am): Check for leads needing follow-up.
- `weekly-review-requests` (Mondays 9am): Send review requests for recently completed jobs.

## Config

| Key | Default | Description |
|-----|---------|-------------|
| drip_campaign_enabled | true | Enable automatic drip campaigns |
| followup_delay_days | 3 | Days before first follow-up |
| review_request_after_days | 7 | Days after job completion to request review |
| review_platforms | google,yelp | Platforms to request reviews on |

## Setup

Bootstrap with HARNESS:

```bash
HARNESS_LOCAL=/path/to/HARNESS bash /path/to/HARNESS/bin/harness-init
```
