---
sidebar_position: 5
sidebar_label: Signed APK
---
# Create Signed APK for Android

This guide will walk you through the process of creating a signed APK for your Flutter Android application. A signed APK is required for publishing your app to the Google Play Store or distributing it outside of debug mode.

## Prerequisites

Before you begin, make sure you have:
- Java Development Kit (JDK) installed on your system
- Flutter SDK properly configured
- Your Flutter project ready for release

## Step 1: Create a Keystore using Java Keytool

First, you need to create a keystore file that will be used to sign your APK. Open your terminal or command prompt and run the following command:

```bash
keytool -genkey -v -keystore upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```

**Command breakdown:**
- `-genkey`: Generates a key pair
- `-v`: Verbose output
- `-keystore upload-keystore.jks`: Creates a keystore file named "upload-keystore.jks"
- `-keyalg RSA`: Uses RSA algorithm
- `-keysize 2048`: Sets key size to 2048 bits
- `-validity 10000`: Key valid for 10000 days
- `-alias upload`: Sets the alias name as "upload"

When you run this command, you'll be prompted to enter:
1. **Keystore password**: Choose a strong password and remember it
2. **Key password**: You can use the same password as the keystore
3. **Personal information**: Fill in the required fields (name, organization, etc.)

**Important:** Keep your keystore file and passwords secure! You'll need them for all future updates to your app.

## Step 2: Create key.properties File

Create a file named `key.properties` in your Flutter project's `android/app/` directory with the following content:

```properties
storePassword=upload
keyPassword=upload
keyAlias=upload
storeFile=C:/Users/DcWhale/upload-keystore.jks
```

**Property descriptions:**
- `storePassword`: The password you set for your keystore
- `keyPassword`: The password you set for your key (usually the same as store password)
- `keyAlias`: The alias name you used when creating the keystore (in this case "upload")
- `storeFile`: The full path to your keystore file

**Note:** Replace the file path with the actual location where you saved your `upload-keystore.jks` file.

### Security Considerations

- **Never commit** the `key.properties` file to version control
- Add `android/app/key.properties` to your `.gitignore` file
- Store your keystore file in a secure location
- Consider using environment variables for production builds

## Step 3: Build the Signed APK

Now you can build your signed APK using the Flutter CLI:

```bash
flutter build apk
```

For a release build with optimizations:

```bash
flutter build apk --release
```

To build APK for specific architectures (reduces file size):

```bash
# Build for ARM64 devices (most modern Android devices)
flutter build apk --target-platform android-arm64

# Build for both ARM32 and ARM64
flutter build apk --split-per-abi
```

## Step 4: Locate Your Signed APK

After the build completes successfully, you'll find your signed APK in:

```
build/app/outputs/flutter-apk/app-release.apk
```

If you used `--split-per-abi`, you'll find multiple APK files:
- `app-arm64-v8a-release.apk` (for 64-bit ARM devices)
- `app-armeabi-v7a-release.apk` (for 32-bit ARM devices)
- `app-x86_64-release.apk` (for 64-bit x86 devices)

## Troubleshooting

### Common Issues

1. **"Keystore file not found"**
   - Verify the `storeFile` path in `key.properties`
   - Use absolute paths with forward slashes

2. **"Wrong keystore password"**
   - Double-check your passwords in `key.properties`
   - Ensure you're using the correct keystore file

3. **"Key not found"**
   - Verify the `keyAlias` matches what you used when creating the keystore
   - List aliases in your keystore: `keytool -list -v -keystore upload-keystore.jks`

### Verification

To verify your APK is properly signed:

```bash
# Check APK signature
jarsigner -verify -verbose -certs build/app/outputs/flutter-apk/app-release.apk

# Or use apksigner (part of Android SDK)
apksigner verify build/app/outputs/flutter-apk/app-release.apk
```

## Best Practices

1. **Backup your keystore**: Store copies in secure, separate locations
2. **Document your signing process**: Keep records of passwords and procedures
3. **Test thoroughly**: Install and test the signed APK on physical devices
4. **Use ProGuard**: Enable code obfuscation for production releases
5. **Version management**: Increment version codes for each release

## Next Steps

After creating your signed APK:
1. Test the APK on various devices
2. Upload to Google Play Console for distribution
3. Set up automated signing for CI/CD pipelines
4. Consider App Bundle format for Play Store optimization

Your signed APK is now ready for distribution!