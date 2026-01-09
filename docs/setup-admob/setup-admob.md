# AdMob Banner Setup Guide

Quick guide to configure AdMob banner ads with your own AdMob account and ad unit IDs.

## Prerequisites

- Google AdMob account ([Create one](https://admob.google.com/))
- App registered in AdMob Console
- AdMob App ID (Android & iOS)
- Banner Ad Unit IDs (Android & iOS)

## Getting Your AdMob IDs

1. **Create AdMob Account**: Go to [Google AdMob](https://admob.google.com/) and sign in
2. **Add Your App**: In AdMob Console → **Apps** → **Add App**
   - Enter app name and package/bundle ID
   - Copy the **App ID** (format: `ca-app-pub-XXXXXXXXXXXXXXXX~XXXXXXXXXX`)
3. **Create Banner Ad Unit**: **Ad units** → **Add ad unit** → Select **Banner**
   - Copy the **Ad Unit ID** (format: `ca-app-pub-XXXXXXXXXXXXXXXX/XXXXXXXXXX`)
   - Repeat for both platforms (or use same ID for both)

## Configuration Files

Update these 3 files:

1. **`lib/app/services/ads_config.dart`** - Main configuration
2. **`android/app/src/main/AndroidManifest.xml`** - Android App ID
3. **`ios/Runner/Info.plist`** - iOS App ID (add if missing)

## Step-by-Step Setup

### Step 1: Update `ads_config.dart`

Replace the placeholder values with your AdMob IDs:

```dart
class AdsConfig {
  // Test IDs (Google's test IDs - don't change)
  static const String _androidBannerAdUnitId = 'ca-app-pub-3940256099942544/6300978111';
  static const String _iosBannerAdUnitId = 'ca-app-pub-3940256099942544/2934735716';

  // App IDs - Replace with your IDs
  static const String _androidAppId = 'ca-app-pub-YOUR_ANDROID_APP_ID~XXXXXXXXXX';
  static const String _iosAppId = 'ca-app-pub-YOUR_IOS_APP_ID~XXXXXXXXXX';

  // Production Banner IDs - Replace with your IDs
  static const String _androidBannerAdUnitIdProd = 'ca-app-pub-YOUR_ANDROID_PUB_ID/YOUR_BANNER_ID';
  static const String _iosBannerAdUnitIdProd = 'ca-app-pub-YOUR_IOS_PUB_ID/YOUR_BANNER_ID';

  // Set to false for production
  static const bool _isTestMode = false;
  
  // ... rest of file unchanged
}
```

### Step 2: Update `AndroidManifest.xml`

Find the AdMob App ID meta-data (around line 38-41) and replace:

```xml
<meta-data
    android:name="com.google.android.gms.ads.APPLICATION_ID"
    android:value="ca-app-pub-YOUR_ANDROID_APP_ID~XXXXXXXXXX"/>
```

### Step 3: Update `Info.plist` (iOS)

Add the AdMob App ID inside the `<dict>` tag:

```xml
<key>GADApplicationIdentifier</key>
<string>ca-app-pub-YOUR_IOS_APP_ID~XXXXXXXXXX</string>
```

## Test Mode vs Production

- **Test Mode** (`_isTestMode = true`): Uses Google's test IDs, shows test ads, no revenue
- **Production** (`_isTestMode = false`): Uses your production IDs, shows real ads, generates revenue

⚠️ **Always test with test mode first. Only switch to production when ready to publish.**

## Verification

1. **Test Mode**: Set `_isTestMode = true`, run app → Should see test ads on Home page and Game screen
2. **Production**: Set `_isTestMode = false`, use your IDs, run app → Should see real ads
3. **Console Logs**: Look for `"Banner ad loaded successfully"` or error messages
4. **AdMob Dashboard**: Check **Ad units** → Verify requests/impressions are recorded

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Ads not showing | Check `_isTestMode` setting, verify IDs are correct, ensure internet connection |
| Failed to load | Verify all IDs copied correctly (no typos), check ad unit is active in AdMob Console |
| Test ads not showing | Ensure `_isTestMode = true`, using Google's test IDs |
| iOS ads not working | Verify `GADApplicationIdentifier` in `Info.plist`, rebuild app after changes |

## Where Ads Are Displayed

- **Home Page** (`lib/app/modules/home/views/home_view.dart`) - Bottom of screen
- **Chess Game Screen** (`lib/app/modules/play_chess/views/play_chess_view.dart`) - Bottom of screen

## Quick Checklist

Before publishing:

- [ ] AdMob account approved
- [ ] App registered in AdMob Console
- [ ] Production IDs in `ads_config.dart`
- [ ] `_isTestMode = false` for production
- [ ] Android App ID in `AndroidManifest.xml`
- [ ] iOS App ID in `Info.plist`
- [ ] Test ads working
- [ ] Production ads working

## Support

- [AdMob Help Center](https://support.google.com/admob)
- [Flutter AdMob Plugin](https://pub.dev/packages/google_mobile_ads)
- Check console logs for specific error messages

---

**Version:** 1.0 | **Last Updated:** 2024
