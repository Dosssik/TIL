---
title: 🔬 Code Quality
---

### Detekt


For Kotlin Multiplatform projects Detekt (`v1.23.8`) won't automatically exclude build folders from scanning (and end up failing with incorrect style for generated code 🤨).
The solution is to exclude it manually:

```kotlin title="build.gradle.kts" linenums="1"
tasks.withType<Detekt>().configureEach {
    exclude { element ->
        element.file.path.contains("/build/generated/")
    }
}

```
