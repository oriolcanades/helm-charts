# helm-charts

Helm Charts Repository using GitHub Pages

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

``` bash
helm repo add <alias> https://<orgname>.github.io/helm-charts
```

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.
You can then run `helm search repo<alias>` to see the charts.

To install the <chart-name> chart:

```bash
    helm install my-<chart-name> <alias>/<chart-name>
```

To uninstall the chart:

```bash
    helm delete my-<chart-name>
```

To generate the index.yaml file, run the following command:

```bash
helm repo index
```

The charts will be published to a website with URL like this: `https://<orgname>.github.io/helm-charts`.

## Release GitHub Actions

The above configuration uses `@helm/chart-releaser-action` 
to turn your GitHub project into a self-hosted Helm chart repo. 
It does this - during every push to main - by checking each chart in your project, and whenever there's a new chart version, creates a corresponding GitHub release named for the chart version, adds Helm chart artifacts to the release, and creates or updates an index.yaml file with metadata about those releases, which is then hosted on GitHub pages.

## Links
- [The Chart Repository Guide](https://helm.sh/docs/topics/chart_repository/)
- [GitHub Actions Workflow for the Chart Repository](https://helm.sh/docs/howto/chart_releaser_action/)
- [Tutorial: Turning a GitHub Repo Into a Helm Chart Repo](https://www.harness.io/blog/helm-chart-repo)
