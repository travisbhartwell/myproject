# MyProject

MyProject is a project task runner written as a Command Group for [MyCmd](https://github.com/travisbhartwell/mycmd/). Project tasks are defined using shell scripts.

MyProject started as an implementation of the [Scripts to Rule Them All](https://github.blog/engineering/scripts-to-rule-them-all/) pattern or a [run.sh script](https://www.oilshell.org/blog/2020/02/good-parts-sketch.html#semi-automation-with-runsh-scripts). It started as a [project.sh script](https://github.com/travisbhartwell/mycmd/blob/0349ece30a3211bab9aeb8bd7696c0e918ca53ed/project.sh) in many of my projects, but then was converted into part of [MyCmd](https://github.com/travisbhartwell/mycmd/), where tasks were defined in a `myproject` shell script, and executed with `mycmd project run <task name>`.

With this implementation that is separate from, but depending on MyCmd, tasks are defined in one or more files in a `myproject` directory.

## Development Blog

Read the development log for MyCmd and MyProject [here](https://iam.travishartwell.net/mycmd/).

## Installing MyProject

MyProject requires [MyCmd](https://github.com/travisbhartwell/mycmd) to run. If not installing MyProject with Homebrew or Mise, you will have to follow the [MyCmd Installation Instructions](https://github.com/travisbhartwell/mycmd/blob/main/README.md#installation) first before installing MyProject.

The following installation mechanisms are listed in order of preference.

### Installation with Homebrew

I have created a [Homebrew Tap](https://github.com/travisbhartwell/homebrew-mycmd/) with [Homebrew](https://brew.sh) formulas for MyCmd and MyProject. To install MyProject (which will also install MyCmd as a dependency), do the following:

```shell
brew tap travisbhartwell/mycmd
brew install myproject
```

Or:

```shell
brew install travisbhartwell/mycmd/myproject
```

Please note the caveat displayed when installing MyProject with Homebrew, as it currently requires you to set the `MYCMD_SEARCH_PATH` environment variable in your shell.

### Installation with Mise

You can also install MyCmd and MyProject with [Mise](https://mise.jdx.dev). To manage installing MyProject and properly setting `MYCMD_SEARCH_PATH` automatically, I have created a Mise Tool Plugin, [myproject-tool-plugin](https://github.com/travisbhartwell/myproject-tool-plugin). If you have Mise installed and configured, you can install MyCmd, add the MyProject tool plugin, and then install MyProject with the following:

``` shell
mise use -g github:travisbhartwell/mycmd
mise plugin install myproject https://github.com/travisbhartwell/myproject-tool-plugin
mise use -g myproject
```

Using this method does not require manual setting of the `MYCMD_SEARCH_PATH` environment variable like the other methods do.

### Installation From a Release Tarball

Get the latest release from the [releases page](https://github.com/travisbhartwell/myproject/releases/latest). Download the GZipped Tarball attached to the release and untar it. It is recommended to put this in `$HOME/.local/share`. For example, if you have downloaded the first release version, you would do the following:

``` shell
mkdir -p $HOME/.local/share && 
  cd $HOME/.local/share &&
  tar xvf ~/Downloads/myproject-0.01.tar.gz
```

This will untar the release contents into `$HOME/.local/share/myproject-0.01`. To make this available via MyCmd, you will need to set the `MYCMD_SEARCH_PATH` environment variable to the `mycmd` directory within it, like this:

``` shell
export MYCMD_SEARCH_PATH=$HOME/.local/share/myproject-0.01/mycmd
```

### Installation From a Git Checkout

You could also use a Git checkout, but as MyProject is still in active development, note that the [main branch](https://github.com/travisbhartwell/myproject/tree/main) isn't guaranteed to always be in a working state. If you do use a git checkout, it is suggested that you use one of the [tags](https://github.com/travisbhartwell/myproject/tags). Tag names prefixed with `snapshot-` are interim snapshot releases, and tag names prefixed with `v` are release versions. Again, doing this in `$HOME/.local/share` is suggested. So, for example, to do a git checkout of the initial release, `v0.01`:

``` shell
mkdir -p $HOME/.local/share && 
  cd $HOME/.local/share &&
  git clone --branch v0.01 https://github.com/travisbhartwell/myproject.git 
```

To make this available via MyCmd, you will need to set the `MYCMD_SEARCH_PATH` environment variable to the `mycmd` directory within the git checkout, like this:

``` shell
export MYCMD_SEARCH_PATH=$HOME/.local/share/myproject/mycmd
```

## Testing After Installation

To verify that MyCmd and MyProject are installed and set up properly, you can run the following:

``` shell
mycmd myproject --help
```

It should output something similar to the following:

```
mycmd myproject version 0.01

MyProject Command Group Library

The MyProject Project Task Runner

The following child command groups are defined:

Group Name        Description
⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯
git               MyProject Git Command Group Library
project-info      MyProject Project Info Command Group Library

The following child commands are defined:

Command Name      Description
⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯
run               Run one or more tasks defined by the current MyProject task definition directory.
```

## License

MyProject is licensed under the [MIT license](LICENSE.md) and includes other open source software developed by contributors to their respective projects.

These libraries used for testing MyProject included in the `testing/vendor` subdirectory have their own licenses, acknowledged here:
* `shunit2`: Licensed under the [Apache License 2.0](https://github.com/kward/shunit2/blob/master/LICENSE). The project repository is at <https://github.com/kward/shunit2>.
