# tanvrit-sdk · commerce

> Inventory, coupons, discounts, wallets, and transaction management for commerce applications.

[![Maven](https://img.shields.io/badge/maven.tanvrit.com-1.0.12-blue)](https://maven.tanvrit.com)
![KMP](https://img.shields.io/badge/Kotlin_Multiplatform-7_targets-blueviolet)

## Install

### Option A — Tanvrit Gradle plugin _(recommended)_

```kotlin
// settings.gradle.kts
pluginManagement {
    repositories { maven { url = uri("https://maven.tanvrit.com") } }
}
```

```kotlin
// build.gradle.kts
plugins { id("com.tanvrit.sdk") version "1.0.12" }

tanvrit {
    version = "1.0.12"
    modules = listOf("commerce")
}
```

### Option B — Direct dependency

```kotlin
// settings.gradle.kts
dependencyResolutionManagement {
    repositories { maven { url = uri("https://maven.tanvrit.com") } }
}
```

```kotlin
// build.gradle.kts  (KMP)
kotlin {
    sourceSets {
        commonMain.dependencies {
            implementation("com.tanvrit:commerce:1.0.12")
        }
    }
}
```

## Targets

| Platform | Artifact |
|----------|----------|
| Android | `commerce-android` |
| Iosarm64 | `commerce-iosarm64` |
| Iossimulatorarm64 | `commerce-iossimulatorarm64` |
| Iosx64 | `commerce-iosx64` |
| Jvm | `commerce-jvm` |
| Js | `commerce-js` |
| Wasm Js | `commerce-wasm-js` |

## Quick start

```kotlin
// Inventory
val inventory = InventoryHandler.shared()
inventory.retrieveProducts(businessId = "biz-001") { products ->
    println("Products: \${products?.size}")
}

// Coupons
val couponHandler = CouponHandler.shared()
val discount = couponHandler.calculateDiscountAmount(coupon, originalPrice = 1000L)

// Wallet balance
val wallet = WalletHandler.shared()
wallet.retrieveWallet(userId = "user-001") { w ->
    println("Balance: \${w?.balance}")
}
```

## Resources

- **Full SDK source:** [tanvrit/sdk](https://github.com/tanvrit/sdk)
- **All modules:** [maven.tanvrit.com](https://maven.tanvrit.com)
- **Issues:** [tanvrit/sdk/issues](https://github.com/tanvrit/sdk/issues)
