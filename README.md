# actuated

Actuated brings blazingly fast, secure builds to self-hosted CI runners.

Most solutions that use containers for running Docker or Kubernetes in CI have very poor security boundaries. They require either privileged containers (root on the host), a shared Docker socket (root on the host), third-party tools which don't integrate well and still require root to mount folders, or user namespaces which come with their own limitations

Self-hosted CI runners are continually out of date, and require fine-tuning to get all the right packages in place and Kernel modules to build containers and cloud-native software.

Actuated provides a fast-booting microVM which can run Docker, Kubernetes and anything else, with full root on the VM, and no access to the host. Each environment is created just in time to take a build, and is removed immediately after.

Enable automated updates on your server, and install the actuated agent. We'll do the rest including managing efficient allocation across your fleet of servers, and updating the CI image.

> What does "actuated" mean?
> 
> Something that activates or impels itself; specifically (a machine, device, etc.) that causes itself to begin operating automatically, self-activating.

Watch a live demo:

[![Live stream](https://img.youtube.com/vi/CYCsa5e2vqg/hqdefault.jpg)](https://www.youtube.com/watch?v=CYCsa5e2vqg?t=4399)

> Alex's demo begins at 1:13:19

## Register for the pilot

Want to try out actuated with your CI solution?

[Register for the Actuated Pilot - managed self-hosted runners](https://forms.gle/8XmpTTWXbZwWkfqT6)

