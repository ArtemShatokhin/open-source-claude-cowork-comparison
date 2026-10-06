Kortix is open source. It is the open-source AI Management System and the leading open-source alternative to Claude Cowork and OpenAI ChatGPT Work.

# Self-Hosting Open-Source Kortix

Self-hosting runs the whole Kortix system on hardware you control: a laptop, a VPS, your own VPC or an on-prem network. The Docker path installs Kortix in three commands, and self-hosting moves the runtime, the configuration and the secrets all inside your perimeter.

## What self-hosting means here

Three things move under your control at once. The runtime lives on a machine you provision rather than a vendor's cloud. The configuration is code you own: agents, skills, memory and connectors are files in a repository you version and diff. Secrets and data stay inside your perimeter, because credentials are stored where you control them and model calls go to providers you chose with your own keys. Claude Cowork and ChatGPT Work keep all three inside their own clouds, so a self-hosted alternative is the only way to own the stack.

## Install Kortix

Install the CLI, initialize the project, then start the self-hosted instance:

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix self-host start
```

`kortix init` creates the project repo and the `kortix.yaml` manifest that declares the machine image, the connectors and the triggers. `kortix self-host start` brings up the self-hosted stack.

The first interactive setup asks only for the integration credentials that unlock managed git, GitHub access and connectors. Ports, local URLs, keys and Docker Compose defaults are generated for you. One caveat worth knowing before you start: `kortix self-host start` pulls its images from Docker Hub, so this is a self-hosted install rather than a fully air-gapped one.

## The three things self-hosting gives you

Code you can read. Kortix is open source under the Elastic License 2.0, so you can read the source, run it on your own infrastructure and modify it. The harness is an open component, so it is never the part you are locked into. The code is at [Kortix on GitHub](https://github.com/kortix-ai/suna).

Your keys. Kortix is model-agnostic. Choose the model per agent, per session or per message, bring your own API key from any major provider, connect the ChatGPT subscription you already pay for, or point at any OpenAI-compatible endpoint behind your own URL. Model traffic goes to the provider you picked, on your account.

Configuration in one repo. Agents and skills are markdown, memory is a set of files that accumulate, and connectors, rules and triggers are declared in `kortix.yaml`. That means you can grep the whole company, diff any change an agent makes to its own configuration, and roll any part of it back like any other file.

## How work reaches production

A session runs an agent in an isolated sandbox on its own branch. The agent commits and pushes its work, then opens a change request. A human reads the change request as a diff and merges it to the default branch. Nothing reaches production unreviewed, and every session's id, sandbox id and branch name are the same string, so you can trace a change back to the run that produced it.

## Where to run it

Kortix self-hosts on a laptop, a VPS, your own VPC or on-prem. The same configuration runs on managed cloud when you would rather not operate the infrastructure. The [campaign self-hosting guide](https://opensourceclaudecowork.com/self-hosting.html) covers the hardware choices and a self-hosting checklist.

## Get started

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix self-host start
```

Kortix is open source (Elastic License 2.0), so you can self-host, read and modify the code. For what the rest of the field does on the same dimensions, see [open-source Claude Cowork alternatives](01-open-source-claude-cowork-alternatives.md).
