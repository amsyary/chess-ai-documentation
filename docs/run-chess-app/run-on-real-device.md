---
sidebar_position: 2
sidebar_label: Run on Real Device
---

# Run Chess AI Game on Real Device

This guide will help you run the Chess AI Game on a real Android or iOS device for testing and development purposes.

## Prerequisites

Before running the app on a real device, make sure you have:

1. **Flutter SDK** properly configured
2. **Chess AI Game project** set up and dependencies installed
3. **USB cable** to connect your device
4. **Developer options** enabled on your device

## Android Device Setup

### Step 1: Enable Developer Options

1. Open **Settings** on your Android device
2. Scroll down and tap **About phone** (or **About device**)
3. Find **Build number** and tap it **7 times**
4. You'll see a message saying "You are now a developer!"

### Step 2: Enable USB Debugging

1. Go back to main **Settings**
2. Look for **Developer options** (usually under System or Additional settings)
3. Enable **USB debugging**
4. Enable **Install via USB** (if available)

### Step 3: Connect Device

1. Connect your Android device to your computer using a USB cable
2. On your device, you might see a prompt asking to "Allow USB debugging"
3. Check **Always allow from this computer** and tap **OK**

### Step 4: Verify Device Connection

Open terminal/command prompt and run:
```bash
flutter devices
```

You should see your Android device listed. If not, try:
```bash
# Check if device is detected by ADB
adb devices

# If device shows as "unauthorized", disconnect and reconnect USB cable
```

### Step 5: Run the App

1. **Using VS Code**:
   - Select your device from the device list (bottom status bar)
   - Press **F5** or go to **Run > Start Debugging**

2. **Using Command Line**:
   ```bash
   cd path/to/chess_ai_game
   flutter run
   ```

3. **Using Android Studio**:
   - Select your device from the device dropdown
   - Click the **Run** button (▶️)

## iOS Device Setup

### Step 1: Prerequisites

1. **macOS** computer (required for iOS development)
2. **Xcode** installed from the App Store
3. **iOS device** running iOS 11.0 or later
4. **Apple Developer Account** (free account works for development)

### Step 2: Configure Xcode

1. Open **Xcode**
2. Go to **Xcode > Preferences > Accounts**
3. Add your Apple ID by clicking the **+** button
4. Sign in with your Apple ID

### Step 3: Set up Signing

1. Open the Chess AI Game project in Xcode:
   ```bash
   open ios/Runner.xcworkspace
   ```
2. Select **Runner** in the project navigator
3. Go to **Signing & Capabilities** tab
4. Select your team from the dropdown
5. Change the **Bundle Identifier** to something unique (e.g., `com.yourname.chessaigame`)

### Step 4: Trust Developer on Device

1. Connect your iOS device to your Mac
2. On your device, go to **Settings > General > VPN & Device Management**
3. Find your developer app certificate
4. Tap **Trust** and confirm

### Step 5: Run the App

```bash
cd path/to/chess_ai_game
flutter run
```

Or use Xcode to build and run the project.

## Troubleshooting

### Android Issues

#### Device not detected
```bash
# Restart ADB server
adb kill-server
adb start-server

# Check device connection
adb devices
```

#### Permission denied
- Ensure USB debugging is enabled
- Try different USB cable or port
- Restart both device and computer

#### Build fails
```bash
# Clean and rebuild
flutter clean
flutter pub get
flutter run
```

### iOS Issues

#### Code signing error
- Verify Apple Developer account is added to Xcode
- Check Bundle Identifier is unique
- Ensure device is registered in your developer account

#### Device not trusted
- Go to device Settings > General > VPN & Device Management
- Trust your developer certificate

#### Build errors
```bash
# Clean iOS build
cd ios
rm -rf build/
cd ..
flutter clean
flutter pub get
flutter run
```

## Testing on Real Device

### Performance Testing

Real devices provide the most accurate performance metrics:

1. **Chess AI Response Time**: Test how quickly the AI responds to moves
2. **Animation Smoothness**: Verify piece movements and board animations
3. **Memory Usage**: Monitor app memory consumption during gameplay
4. **Battery Impact**: Check how the app affects device battery life

### Feature Testing

Test all Chess AI Game features on the real device:

1. **AI Gameplay**:
   - Test different difficulty levels
   - Verify AI move calculations are accurate
   - Check game save/load functionality

2. **Multiplayer**:
   - Test online multiplayer connectivity
   - Verify real-time move synchronization
   - Check game invitations and matchmaking

3. **Puzzles**:
   - Test puzzle loading and solving
   - Verify hint system works correctly
   - Check progress tracking

4. **Settings**:
   - Test theme changes
   - Verify language switching
   - Check music and sound effects

5. **Device-Specific Features**:
   - Test haptic feedback (if supported)
   - Verify notifications work correctly
   - Check app icon and splash screen

### Different Screen Sizes

Test the app on devices with different screen sizes:
- **Small screens** (5-inch phones)
- **Large screens** (6+ inch phones)
- **Tablets** (if supported)

Verify that:
- Chess board scales appropriately
- UI elements are properly positioned
- Text remains readable
- Touch targets are appropriately sized

## Deployment Preparation

Once testing is complete on real devices:

1. **Performance Optimization**:
   - Profile the app for memory leaks
   - Optimize AI calculation algorithms
   - Minimize app size and loading times

2. **Final Testing**:
   - Test on multiple device models
   - Verify compatibility with different Android/iOS versions
   - Test with poor network conditions

3. **Release Build**:
   ```bash
   # Build release APK for Android
   flutter build apk --release
   
   # Build release IPA for iOS
   flutter build ios --release
   ```

Your Chess AI Game is now ready for distribution to app stores or beta testing with real users!