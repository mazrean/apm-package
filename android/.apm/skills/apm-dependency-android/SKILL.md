---
name: apm-dependency-android
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/android. Use when bootstrapping or auditing an Android repo's mise.toml.
---

# Android package — mise dependencies

```toml
[tools]
java = "21"
"aqua:android-sdk-cmdline-tools" = "latest"
```

## Notes

- `java = "21"` matches AGP 8.x targets. Adjust to `17` for older repos.
- Builds use the in-tree Gradle wrapper (`./gradlew`); do not pin `gradle` itself.
- After installing the SDK command-line tools via mise, accept licenses with `sdkmanager --licenses` and install required platforms (`platforms;android-34`, `build-tools;34.0.0`).
- Set `ANDROID_HOME` in `mise.toml` `[env]` if needed.
