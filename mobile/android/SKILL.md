---
name: android
description: Comprehensive Android development skills including Jetpack Compose, CameraX, Navigation, Performance, Testing, and more. Use when building Android applications, migrating legacy code, or implementing platform-specific features.
license: See LICENSE.txt
metadata:
  author: Google LLC (original) | Agent Skills Collection
  source: https://github.com/android/skills
  keywords:
  - Android
  - Jetpack Compose
  - CameraX
  - Navigation
  - Performance
  - Testing
  - Wear OS
  - XR
  - Security
  - Play
  - Identity
  - DevTools
  - Profiler
---

# Android Development Skills

This directory contains AI-optimized, modular instructions and resources to help LLMs better understand and execute specific patterns that follow the best practices and guidance on Android development.

## Available Skills

### Core Development
| Skill | Path | Description |
|-------|------|-------------|
| **Jetpack Compose** | `jetpack-compose/` | Modern declarative UI toolkit including theming, adaptive layouts, and XML migration |
| **Navigation** | `navigation/` | Navigation Component 3 with type-safe destinations |
| **Theming & Styles** | `jetpack-compose/theming/styles/` | Compose theming patterns and design systems |

### Platform Features
| Skill | Path | Description |
|-------|------|-------------|
| **CameraX** | `camera/camerax/` | Camera development with CameraX, ML Kit integration, and Media3 |
| **Wear OS** | `wear/wear-compose-m3/` | Wear-specific Compose patterns and Material 3 |
| **XR/AR/VR** | `xr/` | Extended reality development with Jetpack Compose Glimmer |
| **Device AI** | `device-ai/appfunctions/` | On-device AI and ML integration |

### Quality & Performance
| Skill | Path | Description |
|-------|------|-------------|
| **Testing** | `testing/testing-setup/` | Android testing setup and best practices |
| **Performance/R8** | `performance/r8-analyzer/` | R8 code shrinking and optimization |
| **Profilers** | `profilers/` | Android profiling tools and techniques |

### Security & Identity
| Skill | Path | Description |
|-------|------|-------------|
| **Identity** | `identity/verified-email/` | Email verification and digital credentials |
| **Intent Security** | `security/android-intent-security/` | Secure Android intent handling |

### Build & Distribution
| Skill | Path | Description |
|-------|------|-------------|
| **AGP 9 Upgrade** | `build/agp/agp-9-upgrade/` | Android Gradle Plugin 9 migration guide |
| **Play** | `play/` | Google Play publishing and distribution |

### Developer Tools
| Skill | Path | Description |
|-------|------|-------------|
| **Android CLI** | `devtools/android-cli/` | Command-line tools for Android development |
| **Edge-to-Edge** | `system/edge-to-edge/` | Edge-to-edge UI implementation |

## Quick Reference

### Jetpack Compose Patterns
```kotlin
// Immutable builder pattern (CameraX style)
val config = recorder.prepareRecording(context, opts)
    .withAudioEnabled()  // Chain methods
    .withVideoEnabled()

// Compose theming
@Composable
fun MyTheme(content: @Composable () -> Unit) {
    MaterialTheme(
        colorScheme = darkColorScheme(),
        content = content
    )
}
```

### Testing Best Practices
- Use **Fakes** over Mocks (especially for CameraX interfaces)
- Use **Google Truth** assertions over JUnit
- Always define explicit `@RunWith` for test classes

### Performance Tips
- Use R8 for code shrinking and optimization
- Profile with Android Studio profilers
- Handle thermal states for sustained performance

## Resources

- [Official Android Documentation](https://developer.android.com/docs)
- [Jetpack Compose Guide](https://developer.android.com/compose)
- [CameraX Documentation](https://developer.android.com/camera)
- [Navigation Documentation](https://developer.android.com/navigation)

## License

This collection includes skills from the [android/skills](https://github.com/android/skills) repository by Google LLC, licensed under Apache License 2.0. See individual skill directories for details.
