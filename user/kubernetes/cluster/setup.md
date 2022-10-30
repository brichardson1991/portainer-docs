# Setup

You can make changes to your environment's Kubernetes configuration by selecting **Cluster** from the menu then selecting **Setup**.

<figure><img src="../../../.gitbook/assets/2.15-k8s-cluster-setup.gif" alt=""><figcaption></figcaption></figure>

## Networking

### Allow users to use external load balancer

{% hint style="info" %}
To use this feature, you need to ensure that your cloud provider allows you to create load balancers. Using this feature may incur costs from your cloud provider.
{% endhint %}

Enabling the load balancer feature will allow users to expose applications they deploy over an external IP address assigned by their cloud provider.

### Ingress controllers

Configuring ingress controllers will allow users to expose applications they deploy over a HTTP route.

Portainer auto detects and lists any Ingress Classes defined in the cluster and are allowed by default. As an admin you may choose to disable Ingress Classes as needed.

<figure><img src="../../../.gitbook/assets/2.16-k8scluster-setup-networking (1).png" alt=""><figcaption></figcaption></figure>

Enable the **Configure ingress controller availability per namespace** toggle under **More settings** to be able control Ingress Class availability further at the namespace level.

Enabling **Allow Ingress class to be set to "none"** will let users create ingress objects without specifying any Ingress Class. This is useful for Kubernetes implementations where there is no `IngressClass` defined in the cluster.

## Change Window Settings

This setting allows you to specify a window within which [automatic updates](../applications/manifest.md#automatic-updates) to your applications can be applied.

{% hint style="warning" %}
If this setting is enabled and an update is made to an application outside of this window, it will not be applied.
{% endhint %}

<figure><img src="../../../.gitbook/assets/2.15-k8s-cluster-setup-changewindow.png" alt=""><figcaption></figcaption></figure>

## Security

### Restrict access to the default namespace

By default, a Kubernetes cluster will instantiate a default namespace when provisioning the cluster to hold the default set of pods, services, and deployments used by the cluster. If this option is enabled, the only users with the power to run applications in the default namespace are Portainer administrators.

<figure><img src="../../../.gitbook/assets/2.15-k8s-cluster-setup-security.png" alt=""><figcaption></figcaption></figure>

## Resources and Metrics

### Allow resource over-commit

Enabling this feature lets you allocate more resources to namespaces than are physically available in the cluster.

{% hint style="warning" %}
**Enable** resource over-commit if you need to assign more resources to namespaces than are physically available in the cluster. This may lead to unexpected deployment failures if there are insufficient resources to meet the demand.

**Disable** resource over-commit (highly recommended) if you are only able to assign resources to namespaces that are less (in aggregate) than the cluster total, minus any system-resource reservation.
{% endhint %}

### Enable features using metrics server

{% hint style="info" %}
&#x20;Ensure that the Kubernetes [metrics server](https://kubernetes.io/docs/tasks/debug-application-cluster/resource-metrics-pipeline/#metrics-server) or [Prometheus](https://github.com/kubernetes-sigs/prometheus-adapter) is running inside your cluster.
{% endhint %}

Enabling this feature will allow users to use specific features that leverage the metrics server component.

<figure><img src="../../../.gitbook/assets/2.15-k8s-cluster-setup-resources.png" alt=""><figcaption></figcaption></figure>

## Available storage options

Select which storage options will be available for use when deploying applications. Take a look at your storage driver documentation to figure out which access policy to configure, and whether or not the volume-expansion capability is supported.

<figure><img src="../../../.gitbook/assets/2.15-k8s-cluster-setup-storage.png" alt=""><figcaption></figcaption></figure>