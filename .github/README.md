# GitHub Actions Workflow for Android APK Build

This repository includes a GitHub Actions workflow that automatically builds APK files for the AIProute Android application.

## Workflow Details

- **File**: `.github/workflows/build-apk.yml`
- **Triggers**: Push and Pull Request to `master` or `main` branches
- **Java Version**: JDK 8 (required for legacy Gradle 2.4 compatibility)
- **Artifacts**: Built APK files are uploaded with 30-day retention

## Build Process

The workflow:
1. Sets up JDK 8 environment
2. Configures Android SDK
3. Attempts to install legacy Android SDK components (API 23, build-tools 23.0.0)
4. Builds debug and release APK variants
5. Uploads any successfully built APK files as artifacts

## Legacy Project Considerations

This is a legacy Android project (circa 2015) that uses:
- Gradle 2.4
- Android Build Tools 1.3.0
- Android API 23 (Marshmallow)

Modern CI environments may not have these legacy components readily available, so the workflow includes fallback mechanisms and error handling to ensure it runs successfully even if some builds fail.

## Accessing Built APKs

After a successful workflow run:
1. Go to the "Actions" tab in the GitHub repository
2. Click on the specific workflow run
3. Download the APK artifacts from the "Artifacts" section

## Notes

- The workflow is designed to be resilient to SDK availability issues
- APK files will only be uploaded if the build succeeds
- Build logs provide detailed information about any issues encountered