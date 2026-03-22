# tanvrit/commerce

Commerce primitives: product catalogs, cart, orders, and payment integrations.

## Supported Targets

| Target | Artifact suffix | Notes |
|--------|----------------|-------|
| Android | `-android` | minSdk 24+ |
| iOS arm64 (device) | `-iosarm64` | Native |
| iOS x64 (simulator, Intel) | `-iosx64` | Native |
| iOS Simulator arm64 | `-iossimulatorarm64` | Native |
| JVM (Ktor server / desktop) | `-jvm` | Java 11+ |
| WasmJS | `-wasmjs` | Experimental |
| JS (IR) | `-js` | Experimental |

## Prerequisites

This module depends on: [core](https://github.com/tanvrit/core), [auth](https://github.com/tanvrit/auth), [storage](https://github.com/tanvrit/storage).

Add those modules to your build before adding `commerce`.

## Install

Add the GitHub Packages repository to your `settings.gradle.kts`:

```kotlin
maven {
    url = uri("https://maven.pkg.github.com/tanvrit/commerce")
    credentials {
        username = (project.findProperty("gpr.user") as String?) ?: System.getenv("GITHUB_ACTOR") ?: ""
        password = (project.findProperty("gpr.key") as String?) ?: System.getenv("GITHUB_TOKEN") ?: ""
    }
}
```

Add the dependency:

```kotlin
// JVM / Ktor server / desktop
implementation("com.tanvrit:commerce-jvm:0.0.2")

// Android
implementation("com.tanvrit:commerce-android:0.0.2")

// KMP commonMain
implementation("com.tanvrit:commerce:0.0.2")
```

## GitHub Packages Authentication

GitHub Packages requires a token even for public packages.

1. Create a [GitHub Personal Access Token](https://github.com/settings/tokens) with `read:packages` scope.
2. Add to `~/.gradle/gradle.properties`:

```properties
# ~/.gradle/gradle.properties
gpr.user=YOUR_GITHUB_USERNAME
gpr.key=YOUR_GITHUB_PAT_WITH_READ_PACKAGES
```

## Koin Setup

Register the module with Koin at application start:

```kotlin
import org.koin.core.context.startKoin
import com.tanvrit.commerce.di.CommerceModule

startKoin {
    modules(CommerceModule())
}
```

## Quick Start

```kotlin
// Get the shared network client (Koin must be started first)
val network = CommerceNetwork.shared()
```

## Version & Changelog

Current version: **0.0.2**

See [Releases](https://github.com/tanvrit/commerce/releases) for the full changelog.

---

## Part of the Tanvrit SDK

This module is part of the [Tanvrit Platform](https://tanvrit.com).

All SDK modules: [`core`](https://github.com/tanvrit/core) · [`storage`](https://github.com/tanvrit/storage) · [`auth`](https://github.com/tanvrit/auth) · [`business`](https://github.com/tanvrit/business) · [`commerce`](https://github.com/tanvrit/commerce) · [`communication`](https://github.com/tanvrit/communication) · [`social`](https://github.com/tanvrit/social) · [`ui`](https://github.com/tanvrit/ui) · [`commerceui`](https://github.com/tanvrit/commerceui) · [`commerceapp`](https://github.com/tanvrit/commerceapp)
