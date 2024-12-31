# MyProject

MyProject is a project task runner written as a Command Group for [MyCmd](https://github.com/travisbhartwell/mycmd/). Project tasks are defined using shell scripts.

MyProject started as an implementation of the [Scripts to Rule Them All](https://github.blog/engineering/scripts-to-rule-them-all/) pattern or a [run.sh script](https://www.oilshell.org/blog/2020/02/good-parts-sketch.html#semi-automation-with-runsh-scripts). It started as a [project.sh script](https://github.com/travisbhartwell/mycmd/blob/0349ece30a3211bab9aeb8bd7696c0e918ca53ed/project.sh) in many of my projects, but then was converted into part of [MyCmd](https://github.com/travisbhartwell/mycmd/), where tasks were defined in a `myproject` shell script, and executed with `mycmd project run <task name>`.

With this implementation that is separate from, but depending on MyCmd, tasks are defined in one or more files in a `myproject` directory.

## Development Blog

Read the development log for MyCmd and MyProject [here](https://iam.travishartwell.net/mycmd/).

## License

MyProject is licensed under the [MIT license](LICENSE.md) and includes other open source software developed by contributors to their respective projects.

These libraries used for testing MyProject included in the `testing/vendor` subdirectory have their own licenses, acknowledged here:
* `shunit2`: Licensed under the [Apache License 2.0](https://github.com/kward/shunit2/blob/master/LICENSE). The project repository is at <https://github.com/kward/shunit2>.
