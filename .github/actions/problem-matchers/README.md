# Problem Matchers Action

This action adds Problem Matchers that scan the job log for errors and warnings from Gradle, Kotlin, Dagger, and Android Lint. Any detected lines will be highlighted in the job log and an Annotation will be created, making it easier to see the problems when a job goes wrong. 

For more info about Problem Matchers, see: https://github.com/actions/toolkit/blob/main/docs/problem-matchers.md  

## Usage

To use, just run this action before any step in a job that runs an Android build. The matchers will remain applied for the rest of the job.

```yaml
jobs:
  build:
    steps:
      - name: Problem Matchers
        uses: krogerco/Shared-CI-Action-Android/.github/actions/problem-matchers@<latest-version>
      - name: Build
        run: ./gradlew build
```
