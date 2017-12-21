[![pipeline status](https://git.cnct.io/common-tools/samsung-cnct_solas-chart/badges/master/pipeline.svg)](https://git.cnct.io/common-tools/samsung-cnct_solas-chart/commits/master)

# solas-chart
`solas-chart` is scaffolding for new chart repositories hosted by Samsung CNCT. It
implements our best practices, such as issue and PR templates, commit hooks,
licensing guidelines, and so on.

We use GitLab to implement our CI/CD pipelines. There is one GitLab repository for
each GitHub repository. Each job builds, tests and, then deploys an artifact
to Quay.

SOLAS is also an international maritime treaty to ensure ships comply with
minimum safety standards in construction, equipment and operation.

# Quickstart

- The name of chart repos should be of the form `chart-${NAME}`. For example,
`chart-zabra` is the name of the repo which builds a chart named `zabra`.

- [Create](https://help.github.com/articles/creating-a-new-repository/) a
new empty repo under the [`samsung-cnct`](https://github.com/samsung-cnct)
org using the GitHub GUI, for example https://github.com/samsung-cnct/chart-zabra .

- [Duplicate](https://help.github.com/articles/duplicating-a-repository/)
this repo (https://github.com/samsung-cnct/solas-chart) and push it to the `chart-zabra`
repo you created in the previous step. Note the arguments to clone and push.

```
git clone --bare https://github.com/samsung-cnct/solas-chart.git
cd solas-chart.git
git push --mirror https://github.com/samsung-cnct/chart-zabra.git
cd ..
rm -rf solas-chart.git
```

- Configure CI/CD by following the instructions for
[GitHub](https://github.com/samsung-cnct/solas/blob/master/docs/github.md),
[Quay](https://github.com/samsung-cnct/solas/blob/master/docs/quay.md),
and [GitLab](https://github.com/samsung-cnct/solas/blob/master/docs/gitlab.md).

- Configure [Slack](https://github.com/samsung-cnct/solas/blob/master/docs/slack.md)
notifications.

- [Fork](https://help.github.com/articles/fork-a-repo/) the `chart-zabra` repo
(https://github.com/samsung-cnct/chart-zabra) from `samsung-cnct` and begin
submitting PRs.

# Versioning and Release Process

Chart images are hosted on [Quay](https://quay.io) under "Application". We have the following conventions for versioning:
The general versioning format is `x.y.z-a`.

## alpha
Any image where `a` does not equal 0 is the most recent development version that has passed CI tests. It may change as further adjustments get made. Use at your own risk.

## stable

A release version of a chart image will be of the format `x.y.z-0`. This is considered a fully developed version of the chart.

## Releases

Releases are currently done manually, by pushing a tag to a certain state of master. A release will be cut when it is determined to be useful. Since helm charts may not include a "v" in their version tag, but Github tags require it, the v is removed automatically during the publish stage of the CI run.
