# WSL \(Windows Subsystem for Linux\) \[Beta\]

Yep, you get it right we also have WSL support!

{% embed url="https://github.com/kf5i/k3ai/pull/20" %}

This feature is currently in **\[beta**\] so we are looking for initial feedback. If you have any issue please let us know: [**open issue**](https://github.com/kf5i/k3ai/issues/new?assignees=&labels=bug%2C+needs-triage&template=bug_report.md&title=)\*\*\*\*

{% include style="warning"
**Note: GPU is not currently supported in k3ai withing WSL. The reason is simply that GPU capability is still in development by NVIDIA and Microsoft so we will wait for it to reach a more stable grade.**
%}

## Quick Start

The Windows Subsystem for Linux lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or the dual-boot setup.

### Step 1

Install any Linux distro supported in WSL. For a quick how-to please follow the guide at [**https://docs.microsoft.com/en-us/windows/wsl/install-win10**](https://docs.microsoft.com/en-us/windows/wsl/install-win10)\*\*\*\*

### Step 2

Once ready simply run the following command:

```bash
curl -sfL https://raw.githubusercontent.com/kf5i/k3ai/wsl/install | bash -s -- --wsl --pipelines
```

{% include style="warning"
**Note:** the command above is slightly different from the other commands we typically use. It will change to the usual once the feature will be merged in the main code.
%}

### \(Optional\) Step 3

Once the installation is finished you may run any other plugin as usual, but with the **--skipk3s**  flag. As an example the Tensorflow Serving - ResNet:

```bash
curl -sfL https://get.k3ai.in | bash -s -- --skipk3s --plugin_tfs-resnet
```

The following plugins are immediately supported:

* Argo
* Kubeflow pipelines
* Tensorflow Serving - Resnet 

## Troubleshooting

If you re-login in your WSL session after a "wsl --shutdown" or simply because you restarted/shutdown your computer the k3ai environment will not automatically restart.

We created a utility file for you to re-start k3ai every time. In order to do so execute in WSL:

```bash
startk3s
```

wait for a couple of minutes for the cluster to restart all the pods and you're good to go.
