# Publish monitors in Monte Carlo

[CircleCI Orb](https://circleci.com/docs/orb-intro) commands to publish [Monte
Carlo](https://www.montecarlodata.com/) monitors using [Monte Carlo
CLI](https://docs.getmontecarlo.com/docs/monitors-as-code).

The CLI requires Python 3.7 or higher in base container.

It is also necessary to have `MCD_DEFAULT_API_ID` and `MCD_DEFAULT_API_TOKEN`
env variables with your [API key
credentials](https://docs.getmontecarlo.com/docs/using-the-cli#setting-up-the-cli)
configured. A great way of doing this is using a [CircleCI
context](https://circleci.com/docs/contexts).

See [examples](src/orb.yaml#L9)
