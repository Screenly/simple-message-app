[![Version](https://img.shields.io/github/v/release/Screenly/simple-message-app)](https://github.com/Screenly/simple-message-app/releases/latest)

# Simple Message App

![Simple Message App Preview](/screenshots/1920x1080.webp)

## Getting Started

```bash
bun install
```

## Deployment

Create and deploy the Edge App:

```bash
screenly edge-app create --name simple-message-app --in-place
bun run deploy
screenly edge-app instance create
```

### Releasing

Pushes to `main` deploy to stage automatically. To release to production, tag a commit on `main` and push the tag (the workflow refuses tags not on `main`):

```bash
git checkout main && git pull
git tag v26.10.0
git push origin v26.10.0
```

Then publish a GitHub Release whose notes list the pull requests merged since the previous release. Add `--draft` to review the notes before publishing:

```bash
gh release create v26.10.0 --verify-tag --generate-notes --title v26.10.0
```

## Configuration

The app accepts the following settings via `screenly.yml`:

| Setting             | Description                                                                                                                                                                                                                 | Type     | Default              |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | -------------------- |
| `enable_analytics`  | Enable or disable Sentry and Google Analytics integrations                                                                                                                                                                  | optional | `true`               |
| `message_body`      | The main text content displayed in the message body card                                                                                                                                                                    | required | _(default text)_     |
| `message_header`    | The headline text displayed prominently on the left side                                                                                                                                                                    | required | `Simple Message App` |
| `override_locale`   | Override the default locale using a [BCP&nbsp;47](https://developer.mozilla.org/en-US/docs/Web/Localization/Locale_identification_and_negotiation#locale_identifiers) locale tag (e.g., `en`, `en-GB`, `fr`, `fr-CA`, `de`) | optional | `en`                 |
| `override_timezone` | Override the default timezone using an [IANA time zone identifier](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (e.g., `Europe/London`, `America/New_York`). Defaults to the system timezone if left blank | optional | -                    |
| `tag_manager_id`    | Google Tag Manager container ID to enable tracking and analytics                                                                                                                                                            | optional | `GTM-P98SPZ9Z`       |

## Development

```bash
bun install      # Install dependencies
bun run dev      # Start development server
```

## Testing

```bash
bun run test:unit
```

## Screenshots

Generate screenshots at all supported resolutions:

```bash
bun run screenshots
```

Screenshots are saved to the `screenshots/` directory.
