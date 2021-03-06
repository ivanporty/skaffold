---
title: "CLI References"
linkTitle: "CLI References"
weight: 110
---

Skaffold command-line interface provides the following commands:


End-to-end pipelines:

* [skaffold run](#skaffold-run) - to build & deploy once
* [skaffold dev](#skaffold-dev) - to trigger the watch loop build & deploy workflow with cleanup on exit

Pipeline building blocks for CI/CD:

* [skaffold build](#skaffold-build) - to just build and tag your image(s)
* [skaffold deploy](#skaffold-deploy) - to deploy the given image(s)
* [skaffold delete](#skaffold-delete) - to cleanup the deployed artifacts

Getting started with a new project:

* [skaffold init](#skaffold-init) - to bootstrap skaffold.yaml
* [skaffold fix](#skaffold-fix) - to upgrade from

Utilities:

* [skaffold help](#skaffold-help) - print help
* [skaffold version](#skaffold-version) - get Skaffold version
* [skaffold completion](#skaffold-completion) - setup tab completion for the CLI
* [skaffold config](#skaffold-config) - manage context specific parameters
* [skaffold diagnose](#skaffold-diagnose) - diagnostics of skaffold works in your project


## Global flags

| Flag | Description |
|------- |---------------|
|`-h, --help`| Prints the HELP file for the current command.|
|`-v, --verbosity LOG-LEVEL` | Uses a specific log level. Available log levels are `info`, `warn`, `error`, `fatal`. Default value is `warn`.|

## Global environment variables

| Flag | Description |
|------- |---------------|
|`SKAFFOLD_UPDATE_CHECK`|Enables checking for latest version of the skaffold binary. By default it's `true`. |


## Skaffold commands

<!--
******
To edit this file above edit index_header - the rest of the file is autogenerated by cmd/skaffold/man
******
-->

### skaffold build

Builds the artifacts

```
Usage:
  skaffold build [flags]

Flags:
  -d, --default-repo string          Default repository value (overrides global config)
  -f, --filename string              Filename or URL to the pipeline file (default "skaffold.yaml")
  -n, --namespace string             Run deployments in the specified namespace
  -o, --output *flags.TemplateFlag   Format output with go-template. For full struct documentation, see https://godoc.org/github.com/GoogleContainerTools/skaffold/cmd/skaffold/app/cmd#BuildOutput (default {{range .Builds}}{{.ImageName}} -> {{.Tag}}
                                     {{end}})
  -p, --profile stringArray          Activate profiles by name
  -q, --quiet                        Suppress the build output and print image built on success
      --skip-tests                   Whether to skip the tests after building
      --toot                         Emit a terminal beep after the deploy is complete

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_DEFAULT_REPO` (same as --default-repo)
* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_NAMESPACE` (same as --namespace)
* `SKAFFOLD_OUTPUT` (same as --output)
* `SKAFFOLD_PROFILE` (same as --profile)
* `SKAFFOLD_QUIET` (same as --quiet)
* `SKAFFOLD_SKIP_TESTS` (same as --skip-tests)
* `SKAFFOLD_TOOT` (same as --toot)

### skaffold completion

Output skaffold shell completion for the given shell (bash or zsh)

```
Usage:
  skaffold completion SHELL [flags]

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:


### skaffold config

A set of commands for interacting with the skaffold config.

```
Usage:
  skaffold config [command]

Available Commands:
  list        List all values set in the global skaffold config
  set         Set a value in the global skaffold config
  unset       Unset a value in the global skaffold config

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")

Use "skaffold config [command] --help" for more information about a command.


```
Env vars:


### skaffold delete

Delete the deployed resources

```
Usage:
  skaffold delete [flags]

Flags:
  -d, --default-repo string   Default repository value (overrides global config)
  -f, --filename string       Filename or URL to the pipeline file (default "skaffold.yaml")
  -n, --namespace string      Run deployments in the specified namespace
  -p, --profile stringArray   Activate profiles by name
      --skip-tests            Whether to skip the tests after building
      --toot                  Emit a terminal beep after the deploy is complete

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_DEFAULT_REPO` (same as --default-repo)
* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_NAMESPACE` (same as --namespace)
* `SKAFFOLD_PROFILE` (same as --profile)
* `SKAFFOLD_SKIP_TESTS` (same as --skip-tests)
* `SKAFFOLD_TOOT` (same as --toot)

### skaffold deploy

Deploys the artifacts

```
Usage:
  skaffold deploy [flags]

Flags:
  -d, --default-repo string   Default repository value (overrides global config)
  -f, --filename string       Filename or URL to the pipeline file (default "skaffold.yaml")
      --images strings        A list of pre-built images to deploy
  -l, --label stringArray     Add custom labels to deployed objects. Set multiple times for multiple labels.
  -n, --namespace string      Run deployments in the specified namespace
  -p, --profile stringArray   Activate profiles by name
      --skip-tests            Whether to skip the tests after building
      --tail                  Stream logs from deployed objects
      --toot                  Emit a terminal beep after the deploy is complete

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_DEFAULT_REPO` (same as --default-repo)
* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_IMAGES` (same as --images)
* `SKAFFOLD_LABEL` (same as --label)
* `SKAFFOLD_NAMESPACE` (same as --namespace)
* `SKAFFOLD_PROFILE` (same as --profile)
* `SKAFFOLD_SKIP_TESTS` (same as --skip-tests)
* `SKAFFOLD_TAIL` (same as --tail)
* `SKAFFOLD_TOOT` (same as --toot)

### skaffold dev

Runs a pipeline file in development mode

```
Usage:
  skaffold dev [flags]

Flags:
      --cleanup                   Delete deployments after dev mode is interrupted (default true)
  -d, --default-repo string       Default repository value (overrides global config)
  -f, --filename string           Filename or URL to the pipeline file (default "skaffold.yaml")
  -l, --label stringArray         Add custom labels to deployed objects. Set multiple times for multiple labels
  -n, --namespace string          Run deployments in the specified namespace
      --port-forward              Port-forward exposed container ports within pods (default true)
  -p, --profile stringArray       Activate profiles by name
      --skip-tests                Whether to skip the tests after building
      --tail                      Stream logs from deployed objects (default true)
      --toot                      Emit a terminal beep after the deploy is complete
      --trigger string            How are changes detected? (polling or manual) (default "polling")
  -w, --watch-image stringArray   Choose which artifacts to watch. Artifacts with image names that contain the expression will be watched only. Default is to watch sources for all artifacts
  -i, --watch-poll-interval int   Interval (in ms) between two checks for file changes (default 1000)

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_CLEANUP` (same as --cleanup)
* `SKAFFOLD_DEFAULT_REPO` (same as --default-repo)
* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_LABEL` (same as --label)
* `SKAFFOLD_NAMESPACE` (same as --namespace)
* `SKAFFOLD_PORT_FORWARD` (same as --port-forward)
* `SKAFFOLD_PROFILE` (same as --profile)
* `SKAFFOLD_SKIP_TESTS` (same as --skip-tests)
* `SKAFFOLD_TAIL` (same as --tail)
* `SKAFFOLD_TOOT` (same as --toot)
* `SKAFFOLD_TRIGGER` (same as --trigger)
* `SKAFFOLD_WATCH_IMAGE` (same as --watch-image)
* `SKAFFOLD_WATCH_POLL_INTERVAL` (same as --watch-poll-interval)

### skaffold diagnose

Run a diagnostic on Skaffold

```
Usage:
  skaffold diagnose [flags]

Flags:
  -f, --filename string   Filename or URL to the pipeline file (default "skaffold.yaml")

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_FILENAME` (same as --filename)

### skaffold fix

Converts old skaffold.yaml to newest schema version

```
Usage:
  skaffold fix [flags]

Flags:
  -f, --filename string   Filename or URL to the pipeline file (default "skaffold.yaml")
      --overwrite         Overwrite original config with fixed config

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_OVERWRITE` (same as --overwrite)

### skaffold init

Automatically generate skaffold configuration for deploying an application

```
Usage:
  skaffold init [flags]

Flags:
  -a, --artifact stringArray   '='-delimited dockerfile/image pair to generate build artifact
                               (example: --artifact=/web/Dockerfile.web=gcr.io/web-project/image)
      --compose-file string    Initialize from a docker-compose file
  -f, --filename string        Filename or URL to the pipeline file (default "skaffold.yaml")
      --force                  Force the generation of the skaffold config
      --skip-build             Skip generating build artifacts in skaffold config

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_ARTIFACT` (same as --artifact)
* `SKAFFOLD_COMPOSE_FILE` (same as --compose-file)
* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_FORCE` (same as --force)
* `SKAFFOLD_SKIP_BUILD` (same as --skip-build)

### skaffold run

Runs a pipeline file

```
Usage:
  skaffold run [flags]

Flags:
  -d, --default-repo string   Default repository value (overrides global config)
  -f, --filename string       Filename or URL to the pipeline file (default "skaffold.yaml")
  -l, --label stringArray     Add custom labels to deployed objects. Set multiple times for multiple labels.
  -n, --namespace string      Run deployments in the specified namespace
  -p, --profile stringArray   Activate profiles by name
      --skip-tests            Whether to skip the tests after building
  -t, --tag string            The optional custom tag to use for images which overrides the current Tagger configuration
      --tail                  Stream logs from deployed objects
      --toot                  Emit a terminal beep after the deploy is complete

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_DEFAULT_REPO` (same as --default-repo)
* `SKAFFOLD_FILENAME` (same as --filename)
* `SKAFFOLD_LABEL` (same as --label)
* `SKAFFOLD_NAMESPACE` (same as --namespace)
* `SKAFFOLD_PROFILE` (same as --profile)
* `SKAFFOLD_SKIP_TESTS` (same as --skip-tests)
* `SKAFFOLD_TAG` (same as --tag)
* `SKAFFOLD_TAIL` (same as --tail)
* `SKAFFOLD_TOOT` (same as --toot)

### skaffold version

Print the version information

```
Usage:
  skaffold version [flags]

Flags:
  -o, --output *flags.TemplateFlag   Format output with go-template. For full struct documentation, see https://godoc.org/github.com/GoogleContainerTools/skaffold/pkg/skaffold/version#Info (default {{.Version}}
                                     )

Global Flags:
  -v, --verbosity string   Log level (debug, info, warn, error, fatal, panic) (default "warning")


```
Env vars:

* `SKAFFOLD_OUTPUT` (same as --output)
