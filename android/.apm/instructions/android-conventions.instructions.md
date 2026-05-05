---
applyTo: "**/*.{kt,kts}, AndroidManifest.xml"
---

# Android conventions

- Build via the Gradle wrapper (`./gradlew`). Never invoke a system Gradle.
- Pin JDK and Android SDK command-line tools in `mise.toml`.
- For Compose UI, follow the per-feature `tech-compose-*` skills (e.g. `tech-compose-design-tokens`, `tech-compose-canvas-animation`).
- For HCE / NFC / WebView surfaces, follow the per-feature `tech-android-*` skills.
- The `android-cli` Agent Skill orchestrates project creation, deployment, SDK management.
