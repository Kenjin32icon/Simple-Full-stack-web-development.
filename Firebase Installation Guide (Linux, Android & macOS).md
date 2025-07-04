# **Firebase Installation Guide (Linux, Android & macOS)**

This guide covers the installation steps for **Firebase** on **Linux (Ubuntu/Debian-based distros like Linux Mint), Android (Studio), and macOS**, including Firebase CLI and SDK setup.

---

## **🔥 1. Firebase CLI Installation**
The **Firebase Command Line Interface (CLI)** is required for deploying and managing Firebase projects from your terminal.

### **🔹 Linux (Ubuntu/Debian/Linux Mint)**
```bash
# Install Node.js & npm (if not installed)
sudo apt update
sudo apt install nodejs npm

# Install Firebase CLI globally via npm
sudo npm install -g firebase-tools

# Verify installation
firebase --version
```
#### **Troubleshooting**
- If `nodejs` is missing, try:
  ```bash
  curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
  sudo apt install -y nodejs
  ```
- If `firebase` command is not found after install, check Node.js path:
  ```bash
  export PATH="$PATH:/usr/local/bin"
  ```

---

### **🔹 macOS**
```bash
# Install Homebrew (if not installed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Node.js & npm
brew install node

# Install Firebase CLI
npm install -g firebase-tools

# Verify installation
firebase --version
```

#### **Troubleshooting**
- If `firebase` does not work, try:
  ```bash
  source ~/.zshrc  # or ~/.bashrc
  ```

---

### **🔹 Android (Via Android Studio)**
You don’t need Firebase CLI for Android development, but you need to add Firebase to your Android app.

#### **Prerequisites**
- Android Studio (`https://developer.android.com/studio`)
- Google Account (for Firebase Console)

---

## **📲 2. Firebase Setup for Android**
### **Step 1: Create a Firebase Project**
1. Go to **[Firebase Console](https://console.firebase.google.com/)**
2. Click **"Add Project"**, enter a name, and follow instructions.

### **Step 2: Add Firebase to Your Android App**
1. Go to your project in Firebase Console.
2. Click **"Add App"** → Select **Android**.
3. Fill in:
   - **Android Package Name** (`com.yourcompany.appname`)
   - **App Nickname** (optional)
   - **SHA-1 Key** (for Auth, optional)
4. Click **"Register App"**.

### **Step 3: Download `google-services.json`**
1. Download the config file `google-services.json`.
2. Place it in your `app/` folder (`android/app/` for Flutter).

### **Step 4: Add Firebase SDK**
1. Open **`build.gradle (Project Level)`** and add Google services:
   ```gradle
   dependencies {
       classpath 'com.google.gms:google-services:4.4.0'
   }
   ```
2. Open **`build.gradle (App Level)`** and add:
   ```gradle
   apply plugin: 'com.google.gms.google-services'
   dependencies {
       implementation 'com.google.firebase:firebase-analytics'
       implementation 'com.google.firebase:firebase-auth' // Optional
   }
   ```
3. **Sync Gradle** in Android Studio.

---

## **🍎 3. Firebase Setup for iOS (macOS)**
1. Open your Xcode project.
2. Go to **Firebase Console** → **Add App** → **iOS**.
3. Enter **Bundle ID** (e.g., `com.yourcompany.appname`).
4. Download **`GoogleService-Info.plist`** and drag it into Xcode.
5. Install Firebase via CocoaPods:
   ```bash
   pod init
   open Podfile  # Add Firebase pods
   ```
   Example Podfile:
   ```ruby
   target 'YourApp' do
     pod 'Firebase/Analytics'
     pod 'Firebase/Auth'  # Optional
   end
   ```
6. Run:
   ```bash
   pod install
   ```
7. Open `.xcworkspace` in Xcode and run the app.

---

## **📌 Final Steps**
✅ Check Firebase Dashboard for app status.  
✅ Run `firebase login` (for CLI).  
✅ Use `firebase init` in your project directory.  

---

### **💡 Troubleshooting**
| **Issue** | **Solution** |
|-----------|-------------|
| `firebase: command not found` | Check Node.js install (`node -v`) |
| `Failed to fetch` in Linux | Clear npm cache (`npm cache clean -f`) |
| Android build errors | Ensure correct `google-services.json` path |
| iOS `pod install` fails | Update CocoaPods (`sudo gem install cocoapods`) |

---

### **📚 Useful Links**
- [Firebase Docs](https://firebase.google.com/docs)
- [Firebase CLI](https://firebase.google.com/docs/cli)
- [Android Studio Setup](https://developer.android.com/studio)

---

**🎉 Done! You now have Firebase installed on Linux, Android, and macOS.**  
Follow Firebase documentation for specific services (Auth, Firestore, etc.). 🚀
