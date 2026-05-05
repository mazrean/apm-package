---
applyTo: "**/*.{kt,kts}, AndroidManifest.xml"
---

# Android conventions

- Build via the Gradle wrapper (`./gradlew`). Never invoke a system Gradle.
- Pin the JDK and the `android-cli` mise plugin in `mise.toml`. SDK platforms / build-tools are then installed via `android sdkmanager`.
- For Compose UI, follow the per-feature `tech-compose-*` skills (e.g. `tech-compose-design-tokens`, `tech-compose-canvas-animation`).
- For HCE / NFC / WebView surfaces, follow the per-feature `tech-android-*` skills.
- The `android-cli` Agent Skill orchestrates project creation, deployment, SDK management.
