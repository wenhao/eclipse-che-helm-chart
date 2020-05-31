## Eclipse Che Helm Chart

### Deployment Options

```bash
helm dependency update
```

#### Single User

1. helm install.
    ```bash
    helm upgrade --install <che-release-name> --namespace <che-namespace> --set global.serverStrategy=single-host --set global.ingressDomain=<domain> --set che.workspace.devfileRegistryUrl=<DEVFILE_REGISTRY_URL> --set che.workspace.pluginRegistryUrl=<PLUGIN_REGISTRY_URL> ./
    ```
2. delete the che pod manually.   
3. CORS blocked issue.
    * Install Chrome CORS UnBlock plugin.

* Master: https://che-<che-namespace>.domain
* Workspaces servers: https://server-host.domain

#### Multi User

```bash
helm upgrade --install <che-release-name> --namespace <che-namespace> -f ./values/multi-user.yaml --set global.ingressDomain=<domain> ./
```

* Master: https://che-<che-namespace>.domain
* Keycloak: https://keycloak-<che-namespace>.domain
* Workspaces servers: https://server-host.domain

#### Warning

1. 国内部署或启动Workspace需要拉取很多Docker镜像，需要提前将quay.io/eclipse/所有与Che相关的镜像上传到私有镜像库。

