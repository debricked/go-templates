<img src="https://debricked.com/build/images/blueLogo.d39f7709.svg" alt="debricked" width="50%"  align="top"/>  

# Go templates
Here you find templates for integrating your Go repository with us.

In order for us to analyse all dependencies in your Go project, a file containing the resolved dependency tree has to be created prior to scanning.

This can be done by running `go mod graph` followed by `go mod list go list -mod=readonly -e -m all` and storing the outputs with an empty newline between the sections in a file called `.debricked-go-dependencies.txt`.  
All examples in this repository generates that tree file.  
The command that is run prior to scanning is:
```sh
printf "$(go mod graph)\n\n$(go list -mod=readonly -e -m all)" > .debricked-go-dependencies.txt
```
### Performance tip
Does your `.debricked-go-dependencies.txt` take a long time to create?  
Make sure to **cache** `.debricked-go-dependencies.txt` or the `~/.cache/go-build` & `~/go/pkg/mod` directories between runs where your build is the same!

Different CI/CD tools offer different support for this. Below you can find docs on how set this up:
- GitHub Actions: [docs](https://github.com/actions/cache/blob/main/examples.md#go---modules)
- CircleCI: [docs](https://circleci.com/docs/2.0/caching/)
- BuildKite: [docs](https://github.com/buildkite-plugins/docker-compose-buildkite-plugin#artifacts) (In BuildKite docker volumes comes in handy)
- GitLab CI/CD: [docs](https://docs.gitlab.com/ee/ci/caching/#cache-go-dependencies)
- Azure Pipelines: [docs](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/caching?view=azure-devops#golang)

## GitHub Actions [![Debricked scan](https://github.com/debricked/go-templates/actions/workflows/debricked.yml/badge.svg)](https://github.com/debricked/go-templates/actions/workflows/debricked.yml)
- Add Debricked token variable. [Read more](https://debricked.com/docs/integrations/ci-build-systems/github.html#github-actions)
- [See template](.github/workflows/debricked.yml)

## CircleCI [![CircleCI](https://circleci.com/gh/debricked/go-templates/tree/main.svg?style=svg)](https://circleci.com/gh/debricked/go-templates/tree/main)
- Add Debricked token variable. [Read more](https://debricked.com/docs/integrations/ci-build-systems/circle-ci.html)
- [See template](.circleci/config.yml)

## BuildKite [![Build status](https://badge.buildkite.com/8b441a3d5fefd8724607a1ef4b4df7bd08b68a53269785beea.svg)](https://buildkite.com/debricked/go-templates)
- Add Debricked token variable. [Read more](https://buildkite.com/docs/pipelines/environment-variables#defining-your-own)
- [See template](.buildkite/pipeline.yml)

## GitLab CI/CD
- Add Debricked token variable. [Read more](https://debricked.com/docs/integrations/ci-build-systems/gitlab.html#integrating-using-an-access-token)
- [See template](.gitlab-ci.yml)

## Azure Pipelines
- Add Debricked token variable. [Read more](https://debricked.com/docs/integrations/ci-build-systems/azure-devops.html)
- [See template](azure-pipelines.yml)

## Argo Workflows
- Add Debricked token variable. [Read more](https://debricked.com/docs/integrations/ci-build-systems/argo-workflows.html)
- [See template](argo.yml)

## Travis CI
- Add Debricked token variable. [Read more](https://debricked.com/docs/integrations/ci-build-systems/travis.html)
- [See template](.travis.yml)
