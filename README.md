# Stillman Towing LLC – Earnings Tracker

Professional Android app for tracking roadside assistance / towing call revenue, driver pay, company remainder, daily goals, weekly reports, and expenses.

**Package:** `com.stillmantowing.earnings`  
**Min SDK:** 26 (Android 8.0)  
**Target SDK:** 34  
**Default settings:** Daily goal $450 · Driver pay 20% · Week = Monday–Sunday

---

## Features

1. **Daily Dashboard** – Goal progress bar (turns green at $450+), revenue, call count, driver pay, company remainder, remaining-to-goal.
2. **Add / Edit / Delete Calls** – Amount (required), job #, customer/motor club, vehicle, notes. Automatic driver-pay split using the percentage set in Settings.
3. **Close Out Day** – Saves a permanent daily summary; calls stay in the database.
4. **Weekly Report** – Mon–Sun totals, average, days goal reached, daily breakdown.
5. **Expenses** – Insurance, Fuel, Repairs & Maintenance, Other. Shows estimated profit (company remainder − expenses).
6. **Settings** – Business name, daily goal, driver pay %, CSV export.
7. **Local SQLite (Room)** – All data survives app restarts and phone reboots. No internet required.

---

## How to build the APK (on your computer)

### Prerequisites
1. Install **Android Studio** (Hedgehog 2023.1.1 or newer recommended):  
   https://developer.android.com/studio
2. During setup, install the Android SDK (API 34) and accept licenses.

### Steps

1. **Download / copy this entire folder** (`StillmanTowingApp`) to your computer.

2. Open **Android Studio** → **File → Open** → select the `StillmanTowingApp` folder (the one that contains `settings.gradle.kts`).

3. Wait for Gradle sync to finish (Android Studio will download dependencies the first time).

4. Connect your Android phone via USB **or** use an emulator.
   - On the phone: enable **Developer options** → **USB debugging**.

5. Build a debug APK you can install:
   - Menu: **Build → Build Bundle(s) / APK(s) → Build APK(s)**
   - When finished, click **locate** in the notification.
   - The APK will be at:  
     `app/build/outputs/apk/debug/app-debug.apk`

6. **Install on phone**
   - Copy `app-debug.apk` to the phone and open it, **or**
   - In Android Studio click the green **Run** button (▶) with your device selected.

7. (Optional) **Release / signed APK** for long-term use:
   - **Build → Generate Signed Bundle / APK**
   - Create a new keystore (keep the passwords safe).
   - Choose APK → release → finish.
   - Install the signed APK the same way.

### Command-line build (if you have the SDK & Gradle wrapper)

```bash
cd StillmanTowingApp
# First time only – create the wrapper jar if missing:
# (Android Studio does this automatically when you open the project)
./gradlew assembleDebug
# APK: app/build/outputs/apk/debug/app-debug.apk
```

---

## Project structure

```
StillmanTowingApp/
├── app/
│   ├── build.gradle.kts
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/stillmantowing/earnings/
│       │   ├── MainActivity.kt          # Navigation + bottom bar
│       │   ├── StillmanApp.kt
│       │   ├── data/                    # Room entities, DAOs, Repository
│       │   ├── ui/screens/              # Dashboard, Calls, Reports, Expenses, Settings…
│       │   ├── ui/theme/                # Dark black/gray/green theme
│       │   └── viewmodel/MainViewModel.kt
│       └── res/
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

---

## Using the app

| Screen     | What you do |
|-----------|-------------|
| **Dashboard** | See today’s numbers & progress bar. Tap **+ ADD CALL**. Tap **CLOSE OUT DAY** at end of shift. |
| **Calls**     | List of all calls (today + past). Tap a call to edit or delete. |
| **Reports**   | This Week tab + Past Days (closed-out summaries). Tap a day to see its calls. |
| **Expenses**  | Add fuel, insurance, repairs, etc. See estimated profit. |
| **Settings**  | Change goal ($450 default), driver % (20% default), business name. Export CSV. |

Driver pay is calculated as `call amount × (driver % ÷ 100)`.  
Company remainder = call amount − driver pay.  
Expenses are **not** auto-deducted; they only appear in the profit estimate when you enter them.

---

## Data & privacy

- Everything is stored in a local Room/SQLite database on the device.
- No accounts, no cloud, no analytics.
- Use **Settings → Export to CSV** to back up your records (opens the system share sheet so you can save to Google Drive, email, etc.).

---

## Future updates

Open the project in Android Studio, change code or defaults, then rebuild the APK.  
Suggested improvements you can add later: photo attachment per call, PDF invoice, multi-driver support, cloud backup.

---

**Stillman Towing LLC Earnings Tracker** – built for real roadside work.
