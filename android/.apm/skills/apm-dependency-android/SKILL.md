---
name: apm-dependency-android
description: Lists the CLI tools that must appear in mise.toml for any repo depending on apm-plackage/android. Use when bootstrapping or auditing an Android repo's mise.toml.
---

# Android package — mise dependencies

```toml
[tools]
java = "openjdk-21"
android-cli = "latest"
```

## Notes

- `android-cli` is the mise plugin that wraps `cmdline-tools` + `sdkmanager` + `avdmanager`. It exposes the `android` CLI used by the `android-cli` Agent Skill.
- `java = "openjdk-21"` matches AGP 8.x targets. Older repos may need `"openjdk-17"`.
- Builds use the in-tree Gradle wrapper (`./gradlew`); do not pin `gradle` itself in mise.
- After installing, accept SDK licenses with `android sdkmanager --licenses` and install the platforms / build-tools the project needs (e.g. `android sdkmanager "platforms;android-34" "build-tools;34.0.0"`).
- Set `ANDROID_HOME` only if your tooling needs it explicitly — the `android-cli` plugin sets it for the mise-managed shell automatically.
