# Shared-CI-Action-Android

Shared actions used by Kroger's GitHub actions.

## Actions
- [Build](.github/actions/build)
    - Uses `gradle/gradle-build-action@v2` and calls `assemble`
    - Inputs:
        - Java Version - 17 is recommended
- [Code Coverage](.github/actions/code-coverage)
    - Runs [kover-report](https://github.com/mi-kas/kover-report) with the specified inputs.
    - Inputs:
        - Coverage Counter Type - Report counter type used to calculate coverage metrics. Possible values are: INSTRUCTION, LINE or BRANCH.
        - Gradle Command - The gradle command to execute to generate the code coverage report
        - Java Distribution - The distribution of Java to use
        - Java Version - 17 is recommended
        - Min Coverage Changed Files - The minimum code coverage that is required to pass for changed files
        - Min Coverage Overall - The minimum code coverage that is required to pass for overall project
        - Path - Path to the generated code coverage file
        - Title - Title for the pull request comment
        - Token - Github token to use when adding commits to the pull request
        - Update Comment - Update the coverage report comment instead of creating a new one. Requires title to be set.
- [Code Lint](.github/actions/code-lint)
    - Runs [ktlint](https://github.com/pinterest/ktlint) with the specified version.
    - Inputs:
        - ktlint version, e.g. `0.46.1`
        - Java Version - 17 is recommended
- [Commit Lint](.github/actions/commit-lint)
    - Runs [commitlint](https://www.npmjs.com/package/@commitlint/cli) against commits to ensure they meet requirements and to protect the `Determine Version` and `Release` steps.
    - Inputs:
        - NodeJS Version - 18 is recommended
        - Commitlint Version - 17+ is recommended
- [Determine Version](.github/actions/determine-version)
    - Uses [Semantic Release](https://github.com/semantic-release/semantic-release) to determine if the new commits should trigger a release.
    - Inputs:
        - NodeJS Version - 18 is recommended
        - Semantic Release Version - 21+ recommended
        - Conventional Changelog Version - 5+ recommended
- [Gradle Task](.github/actions/gradle-task)
    - Uses `gradle/gradle-build-action@v2` and calls the Gradle Command input.
    - Inputs:
        - Gradle Command - The gradle task to execute
        - Java Distribution - The distribution of Java to use
        - Java Version - 17 is recommended
        - Setup Android SDK - Whether or not to run `android-actions/setup-android@v2` before executing the Gradle Command task.
- [Instrumented Tests](.github/actions/instrumentation-test)
    - Runs Instrumented tests for an Android project.
    - Inputs:
        - Java Version - 17 is recommended
        - API Level - The Android API level of the emulator to use
        - Instrumented Test Script - Script to run to execute instrumented tests, e.g. `./gradlew connectedCheck`
- [Problem Matchers](.github/actions/problem-matchers)
    - Adds [Problem Matchers](https://github.com/actions/toolkit/blob/main/docs/problem-matchers.md) which highlight build errors and warnings in the job log and create annotations for them.
- [Publish](.github/actions/publish)
    - Runs `gradle publish` for your project.
    - Inputs:
        - Java Version - 17 is recommended
- [Release](.github/actions/release)
    - Uses [Semantic Release](https://github.com/semantic-release/semantic-release) to create a release/tag on github of the version calculated using prior releases and new commits.
    - Inputs:
        - NodeJS Version - 18 is recommended
        - Semantic Release Version - 21+ recommended
        - Conventional Changelog Version - 5+ recommended
- [Unit Tests](.github/actions/unit-tests)
    - Uses `gradle/gradle-build-action@v2` and calls the Test Command input. Test results are published using `mikepenz/action-junit-report@v3`.
    - Inputs:
        - Java Version - 17 is recommended
        - Test Command - The gradle task to run your tests, e.g. `test`
