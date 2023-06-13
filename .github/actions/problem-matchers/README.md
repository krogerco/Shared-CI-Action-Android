# Problem Matchers Action

This action adds problem matchers that scan the job log for errors and warnings from Gradle, Kotlin, and Android Lint. Any detected lines will be highlighted in the job log and an Annotation will be created, making it easier to see the problems when a job goes wrong.

## Usage

To use, just run this action before any step in a job that runs an Android build. The matchers will remain applied for the rest of the job.

```yaml
jobs:
  build:
    steps:
      - name: Problem Matchers
        uses: Shared-CI-Action-Android/problem-matchers
      - name: Build
        run: ./gradlew build
```
