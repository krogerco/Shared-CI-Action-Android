# Native Platform Github Actions

Ground Kontrol has provided custom wrappers around public actions/sets of actions for common steps in a Github workflow for Android projects

All of these actions are used in our own [reusable workflows](https://github.com/krogertechnology/kap-np-android-workflows). Anyone is free to use the workflows provided there or actions provided here.

## Actions
- [Build](.github/actions/build)
    - Uses `gradle/gradle-build-action@v2` and calls `assemble`
    - Inputs:
        - Java Version - 11 is recommended
- [Code Lint](.github/actions/code-lint)
    - Runs [ktlint](https://github.com/pinterest/ktlint) with the specified version
    - Inputs:
        - ktlint version, e.g. `0.46.1`
- [Commit Lint](.github/actions/commit-lint)
    - Runs [commitlint](https://www.npmjs.com/package/@commitlint/cli) against commits to ensure they meet requirements and to protect the `Determine Version` and `Release` steps
    - Inputs:
        - NodeJS Version - 18 is recommended
- [Determine Version](.github/actions/determine-version)
    - Uses [Semantic Release](https://github.com/semantic-release/semantic-release) to determine if the new commits should trigger a release
    - Used by Ground Kontrol to protect the `Release` step
    - Inputs:
        - NodeJS Version - 18 is recommended
- [Instrumented Tests](.github/actions/instrumentation-test)
    - Runs Instrumented tests for an Android project
    - Inputs:
        - Java Version - 11 is recommended
        - API Level - The Android API level of the emulator to use
- [Problem Matchers](.github/actions/problem-matchers)
    - Adds [Problem Matchers](https://github.com/actions/toolkit/blob/main/docs/problem-matchers.md) which highlight build errors and warnings in the job log and create annotations for them.
- [Publish](.github/actions/publish)
    - Run `gradle publish` for your project
    - Inputs:
        - Java Version - 11 is recommended
- [Release](.github/actions/release)
    - Uses [Semantic Release](https://github.com/semantic-release/semantic-release) to create a release/tag on github of the version calculated using pror releases and new commits
    - Inputs:
        - NodeJS Version - 18 is recommended
- [Unit Tests](.github/actions/unit-tests)
    - Runs `gradle test jacocoTestReport`
        - Currently coupled to jacoco for test coverage. Please [reach out](https://teams.microsoft.com/l/channel/19%3a84c93131b09a414e807260913441f8d6%40thread.skype/Android?groupId=22436d9e-3df2-4bff-be35-074608859941&tenantId=8331e14a-9134-4288-bf5a-5e2c8412f074) if this is a problem for you
    - Inputs:
        - Java Version - 11 is recommended
        - Test Command - What gradle task to run your tests, e.g. `test --stacktrace`
