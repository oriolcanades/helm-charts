# helm-charts

Helm Charts Repository using GitHub Pages

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs) to get started.

### 1. Create a Chart

To create a new chart, use `helm create`:

```bash
helm create mychart
```
---
### 2. Validate the Chart

#### 2.1. Validate the Chart Syntax

Use the Helm command to validate the syntax of the Chart:

```bash
helm lint mychart
```

- This command will check for common errors in the templates and values.yaml. 
- If there are any warnings or errors, Helm will show them to you so you can correct them.

#### 2.2. Render the Templates

Render the templates to verify how the final YAML is generated:

```bash
helm template <chart-name> --values <chart-name>/values.yaml
```

This will generate the Kubernetes manifests that Helm would apply, without deploying them. Check the following points:

- Ensure that the namespaces, resource names, ports, volumes, and configurations are correctly configured.
- Verify that the Spring Boot and PostgreSQL configuration values are in the correct fields (e.g., environment variables, ConfigMaps, Secrets).

---

### 3. 



---

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

# TroubleShooting

---
### Error: open values.yaml: no such file or directory

When running the command `helm template demo --values values.yaml` you may encounter the following error:

```bash
helm template demo --values values.yaml    
Error: open values.yaml: no such file or directory
```

To fix this error, follow these steps:

1. Verify the structure of your Chart. Ensure that the values.yaml file exists in the Chart folder:
    ```text
    <chart-name>/
    ├── charts/
    ├── templates/
    ├── values.yaml
    ├── Chart.yaml
    └── ...
    ```

2. Use the correct path to the values.yaml file. If the values.yaml file is in the Chart folder, you can specify the path as follows:
    ```bash
    helm template . --values ./values.yaml
    ```
    If you are in the charts/ directory (one level up), use:
    ```bash
    helm template demo --values demo/values.yaml
    ```
---
