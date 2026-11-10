# Expense Track

Offline-first expense splitting app for Android and iOS.

## Stack

- React Native with Expo SDK 58 and TypeScript
- `expo-sqlite` for local SQLite storage; no login or backend is required
- Integer cents are used for all money calculations

React Native was chosen because this repository already uses Expo, it supports Android and iOS from one TypeScript codebase, and it keeps the fast hot-reload workflow.

## Run

```powershell
npm install
npm start
```

Then press `a` for Android, or scan the QR code with Expo Go. For browser-only preview:

```powershell
npm run web
```

## Try it on a phone

For quick development, install Expo Go, keep the phone and computer on the same Wi-Fi, then run:

```powershell
npm start
```

Scan the QR code. If LAN connection is stuck, press `s` in the Expo terminal and choose Tunnel. Expo Go is only a development preview; the app's SQLite data is stored locally on the phone.

For a standalone Android APK without Expo Go:

```powershell
npm install -g eas-cli
eas login
eas build:configure
eas build -p android --profile preview
```

Open the build link on the Android phone and install the downloaded APK. This requires an Expo account and may wait in the EAS build queue.

The database is created automatically as `expenses.db` on the device. Default categories are Food, Luxury, and Life / Guitar…. Default people are Ryan, Wm, and Derrick.

## Flow

1. Choose or long-press a category on Home.
2. Enter a description and amount with the keypad.
3. Select people, include/exclude Me, and confirm the equal split.
4. Mark shares paid in Debt tracker. Paid records remain in Settled.
5. Use History and People to manage saved data.

`src/split.test.ts` covers remainder-cent rounding. Run it in a Jest-enabled project with:

```powershell
npx jest src/split.test.ts
```
