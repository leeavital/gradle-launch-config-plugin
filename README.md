gradle-launch-config-plugin
===========================
[![Circle CI](https://circleci.com/gh/palantir-baseline/gradle-launch-config-plugin.svg?style=shield)](https://circleci.com/gh/palantir-baseline/gradle-launch-config-plugin)
[![GitHub license](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://raw.githubusercontent.com/palantir-baseline/gradle-launch-config-plugin/develop/LICENSE)

A Gradle Plugin that creates `.launch` files for Eclipse and Run Configurations for IntelliJ for your project's
`JavaExec` tasks.

Usage
-----
1. [Apply the plugin](https://plugins.gradle.org/plugin/baseline.launch-config)
2. Call the respective IDE commands (i.e. `./gradlew idea` or `./gradlew eclipse`)
3. Optional. You can add the `launchConfig` block to specify the `JavaExec` tasks to be used to generate the `.launch`
files for Eclipse and run configurations for IntelliJ.

```
launchConfig {
    excludedTasks 'run'
}
```

The `launchConfig` block offers the following options:
 * (optional) `includedTasks` a set of `JavaExec` tasks to be used by the plugin to generate the `.launch` files for
 Eclipse and the run configurations for IntelliJ. If it not specified, all `JavaExec` tasks are included except
 for the ones specified in `excludedTasks`.
 * (optional) `excludedTasks` a set of `JavaExec` tasks that are excluded from the launch file or the run configuration
 creation.

Tasks
-----
The tasks are only added if their matching IDE plugin is applied.

- `eclipseLaunchConfig` - creates `.launch` files. Triggered when `:eclipseProject` is called.
- `cleanEclipseLaunchConfig` - deletes the generated `.launch` files. Triggered when `:cleanEclipseProject` is called.
- `ideaLaunchConfig` - generates the XML in the IDEA workspace. Triggered when `:ideaWorkspace` is called.

Contributing
------------
Before working on the code, if you plan to contribute changes, please read the [CONTRIBUTING](CONTRIBUTING.md) document.


License
-------
This project is made available under the [Apache 2.0 License][license].


[license]: http://www.apache.org/licenses/LICENSE-2.0
