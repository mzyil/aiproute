# Android 15 Compatibility Upgrade Notes

This document outlines the changes made to upgrade AIProute for Android 15 (API level 35) compatibility.

## Changes Made

### Build Configuration Updates

1. **Android Gradle Plugin**: Updated from 1.3.0 to 8.5.2
2. **Gradle Wrapper**: Updated from 2.4 to 8.7
3. **Compile SDK**: Updated from 23 to 35 (Android 15)
4. **Target SDK**: Updated from 19 to 35 (Android 15)
5. **Minimum SDK**: Updated from 19 to 21 (Android 5.0) for better library compatibility

### Repository Updates

- Added Google Maven repository
- Added Maven Central repository
- Kept JCenter for backward compatibility

### AndroidX Migration

1. **Dependencies**: Migrated from Android Support Library to AndroidX
   - `com.android.support:appcompat-v7:23.0.0` → `androidx.appcompat:appcompat:1.7.0`
   - `com.android.support:support-v4:23.0.0` → `androidx.legacy:legacy-support-v4:1.0.0`
   - Added Material Design Components: `com.google.android.material:material:1.12.0`

2. **Source Code Updates**:
   - Updated imports from `android.support.v7.app.AppCompatActivity` to `androidx.appcompat.app.AppCompatActivity`
   - Updated DialogFragment imports to use AndroidX fragments
   - Updated FragmentManager usage to use `getSupportFragmentManager()`

### Gradle Properties

Added AndroidX migration settings:
- `android.useAndroidX=true`
- `android.enableJetifier=true`
- `android.nonTransitiveRClass=true`

### Java Compatibility

- Updated source and target compatibility to Java 11
- Enabled parallel builds for better performance

## Version Bump

- Version code: 1 → 2
- Version name: 0.1 → 0.2

## Testing Recommendations

1. Test on Android 15 devices or emulators
2. Verify WiFi routing functionality still works correctly
3. Test fragment dialogs (SSID selection)
4. Verify settings activity functionality
5. Test auto-start on boot functionality

## Notes

- The minimum SDK was increased to API 21 (Android 5.0) to ensure better compatibility with modern libraries
- All legacy Android Support Library references have been migrated to AndroidX
- The app should now be compatible with Android 15 while maintaining backward compatibility to Android 5.0+
