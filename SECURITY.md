# Security Policy

## Reporting a vulnerability

If you believe you have found a security vulnerability in the Ingo Money Android SDK, please report it
privately — **do not open a public issue.**

- Contact your Ingo Money representative and ask to be connected with the mobile security team. Include a
  description, the affected version, and reproduction steps.
- We aim to acknowledge reports within a reasonable timeframe and will coordinate a fix and disclosure.

Please do not include real credentials, customer data, tokens, or license keys in a report.

## Supported versions

Security fixes are provided for the current supported line only. `7.3.x` is the supported line; versions
before it are no longer supported. Upgrade to the latest release to receive fixes.

## Verifying what you resolved

This SDK is distributed **only** through Ingo's canonical GitHub Packages registry:

```
https://maven.pkg.github.com/Ingo-Money/Ingo-Money-Android
```

GitHub Packages requires an authenticated read (a classic `read:packages` PAT) even for public packages, so
artifacts are served from an access-controlled registry over HTTPS, and Gradle verifies each artifact's
Maven SHA checksum on download. Resolve `com.ingo.sdk:*` **only** from the URL above — a look-alike
coordinate or mirror served from anywhere else should be treated as untrusted.

For defense-in-depth, enable **Gradle dependency verification** to pin the exact checksums you expect and
fail the build on any mismatch:

```
./gradlew --write-verification-metadata sha256 help
```

This writes `gradle/verification-metadata.xml`; commit it so every subsequent resolve of the Ingo, MiSnap,
and FraudForce artifacts is checksum-pinned. (Note: unlike the iOS SDK's per-framework Apple code signature,
Android AARs are not individually publisher-signed — integrity rests on the canonical access-controlled
registry plus Gradle checksum verification.)
