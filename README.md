# Publish monitors in Monte Carlo

[CircleCI Orb](https://circleci.com/docs/orb-intro) commands to publish [Monte
Carlo](https://www.montecarlodata.com/)
[monitors](https://docs.getmontecarlo.com/docs/monitors-as-code#monitor-configuration-reference)
using [Monte Carlo CLI](https://docs.getmontecarlo.com/docs/monitors-as-code).

The CLI requires Python 3.10 or higher in base container.

## Commands

| Command | What it does | Credentials |
|---|---|---|
| `publish-monitors` | Applies the configuration | required |
| `validate-monitors` | Compiles the configuration locally | **none** |
| `validate-monitors-remote` | Reports the changes that would be applied | required |

`publish-monitors` and `validate-monitors-remote` need `MCD_DEFAULT_API_ID` and
`MCD_DEFAULT_API_TOKEN` env variables with your [API key
credentials](https://docs.getmontecarlo.com/docs/using-the-cli#setting-up-the-cli)
configured. A great way of doing this is using a [CircleCI
context](https://circleci.com/docs/contexts).

## Validating pull requests

Use `validate-monitors` on pull requests. It runs `montecarlo monitors compile`,
which performs no API call and therefore needs no credentials, so the job can
run on any branch without granting it a context.

`validate-monitors-remote` catches more — invalid field names, unknown domains,
missing tables — but it needs credentials to do so. Any job that provides them
also exposes them to the code of the branch being built, so `--dry-run` is not a
safety boundary on its own. Restrict it to branches you trust.

See [examples](src/orb.yaml#L9)
