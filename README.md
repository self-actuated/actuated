# actuated

Actuated brings blazingly fast, secure builds to self-hosted CI runners.

## Building containers on self-hosted runners is slow and insecure

Most solutions that use containers for running Docker or Kubernetes in CI have very poor security boundaries. They require either privileged containers (root on the host), a shared Docker socket (root on the host), third-party tools which don't integrate well and still require root to mount folders, or user namespaces which come with their own limitations. We're looking squarely at you: [actions-controller-runtime](https://github.com/actions-runner-controller/actions-runner-controller), Jenkins and GitLab.

## Management is a nightmare

Self-hosted CI runners are continually out of date, and require fine-tuning to get all the right packages in place and Kernel modules to build containers and cloud-native software. You'll also have to spend extra time making sure builds don't conflict, and that they can't cause side effects to system-level packages. What if you need two different version of some software?

If you haven't felt this pain yet, then perhaps you're blissfully unaware or are not updating your packages?

> Are you [running privileged containers](https://learn.snyk.io/lessons/container-runs-in-privileged-mode/kubernetes/) for CI in your organisation? Are you sharing a Docker Socket (just as bad!)? Are you running [Docker in Docker (DIND)](https://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/)? 🙈

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

Would you like to try out Actuated for your team and GitHub Organisation?

[Register for the Actuated Pilot - managed self-hosted runners](https://forms.gle/8XmpTTWXbZwWkfqT6)

## Q&A

Q: How does it work?

Actuated has three main parts:

1. an agent which knows how to run VMs, you install this on your hosts
2. a VM image and Kernel that we build which has everything required for Docker, KinD and K3s
3. a multi-tenant control plane that we host, which tells your agents to start VMs and register a runner on your GitHub organisation

The multi-tenant control plane is run and operated by OpenFaaS Ltd.

Q: What kind of machines do I need for the agent?

You'll need either: a bare-metal host (your own, AWS i3.metal or Equinix Metal), or a VM that supports nested virtualisation such as those provided by GCP and DigitalOcean.

Q: Who is actuated for?

actuated is primarily for software engineering teams who are currently using GitHub Actions. A GitHub organisation is required for installation, and runners are attached to individual repositories as required, to execute builds.

Q: How many builds does a single actuated VM run?

A VM can run at most one build, then it will be destroyed.

Q: What's in the VM image and how is it built?

The VM image will be publicly available in a container registry for you to explore.

Q: Is Actuated going to be free and open-source?

Actuated is commercial software developed by OpenFaaS Ltd. A subscription will be required to use the software. 

The website and documentation are available on GitHub and we plan to release some open source tools in the future for actuated customers. 

Q: Is there a risk that we could get "locked-in" to actuated?

No, you can move back to hosted runners, or self-managed self-hosted runners at any time, but you may run into the problems that actuated sets out to solve.

Q: Why is the brand called "actuated" and "selfactuated"?

The name of the software is actuated, in some places "actuated" is not available, and we liked "selfactuated" more than "actuatedhq" or "actuatedio" because it refers to the hybrid experience of self-hosted runners.

Q: What do I need to change in my workflows?

Very little, just add / set `runs-on: actuated`

Q: Do you have any samples for Docker, KinD, K3s or OpenFaaS?

Glad you asked:

* [AMD64/Intel examples](https://github.com/actuated-samples)
* [AARCH64 / Graviton / Raspberry Pi 4 examples](https://github.com/actuated-samples-arm64)

Follow [@selfactuated on Twitter](https://twitter.com/selfactuated)

