# actuated

Actuated brings blazingly fast, secure builds to self-hosted CI runners.

## Building containers on self-hosted runners is slow and insecure

Most solutions that use containers for running Docker or Kubernetes in CI have very poor security boundaries. They require either privileged containers (root on the host), a shared Docker socket (root on the host), third-party tools which don't integrate well and still require root to mount folders, or user namespaces which come with their own limitations.

## Management is a nightmare

Self-hosted CI runners are continually out of date, and require fine-tuning to get all the right packages in place and Kernel modules to build containers and cloud-native software. You'll also have to spend extra time making sure builds don't conflict, and that they can't cause side effects to system-level packages. What if you need two different version of some software?

If you haven't felt this pain yet, then perhaps you're blissfully unaware or are not updating your packages?

## Self-managed runners are inefficient and overprovisioned

Self-hosted runners are typically overprovisioned meaning you're spending too much money, because you never know how many jobs you'll have to run at once.

The GitHub Actions runner has no idea how to efficiently distribute jobs across your build machines.

## Hands-free, VM-level isolation

Actuated provides a fast-booting microVM which can run Docker, Kubernetes and anything else you need, with full root on the VM, and no access to the host. Each environment is created just in time to take a build, and is removed immediately after.

We maintain a VM image that is updated regularly, so you don't have to install SDKs, runtimes or language packs on your build machines.

Just enable automated updates on your server then install the actuated agent. We'll do the rest including managing efficient allocation across your fleet of servers, and updating the CI image.

And actuated will run your jobs efficiently across a fleet of hosts, or a single machine. They each need to be either bare-metal hosts (think: AWS, Equinix Metal, etc), or support nested virtualization (a feature available on GCP and DigitalOcean)

> What does "actuated" mean?
> 
> Something that activates or impels itself; specifically (a machine, device, etc.) that causes itself to begin operating automatically, self-activating.

Watch a live demo:

[![Live stream](https://img.youtube.com/vi/CYCsa5e2vqg/hqdefault.jpg)](https://www.youtube.com/watch?v=CYCsa5e2vqg?t=4399)

> Alex's demo begins at 1:13:19

## Register for the pilot

Want to try actuated with GitHub Actions for your team?

[Register for the Actuated Pilot - managed self-hosted runners](https://forms.gle/8XmpTTWXbZwWkfqT6)

## GitHub Actions samples for Docker / KinD / K3s and OpenFaaS

* [AMD64/Intel examples](https://github.com/actuated-samples)
* [AARCH64 / Graviton / Raspberry Pi 4 examples](https://github.com/actuated-samples-arm64)

Follow [@selfactuated on Twitter](https://twitter.com/selfactuated)
