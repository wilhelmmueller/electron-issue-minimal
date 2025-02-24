# Electron CastLabs Bug Reproduction

## ❓ **Issue Description**

When running the Electron CastLabs fork (`electron@32.3.1+wvcus`) on macOS, the app crashes immediately with the following error:

```
dyld[25591]: Library not loaded: @rpath/Electron Framework.framework/Electron Framework
  Referenced from: <4C4C4425-5555-3144-A10C-37A913CAB71C> /Users/username/TestRepos/electron-issue-minimal/node_modules/electron/dist/Electron.app/Contents/MacOS/Electron
  Reason: tried: '/Users/username/TestRepos/electron-issue-minimal/node_modules/electron/dist/Electron.app/Contents/Frameworks/Electron Framework.framework/Electron Framework' (no such file), '/Users/username/TestRepos/electron-issue-minimal/node_modules/electron/dist/Electron.app/Contents/Frameworks/Electron Framework.framework/Electron Framework' (no such file)
/Users/username/TestRepos/electron-issue-minimal/node_modules/electron/dist/Electron.app/Contents/MacOS/Electron exited with signal SIGABRT
```

This issue does **not** occur with:
- `electron@32.3.0+wvcus` (CastLabs fork) ✅
- `electron@32.3.1` (Official Electron release) ✅

The problem seems specific to the CastLabs fork version `32.3.1+wvcus` and appears to occur in all subsequent versions after `32.3.1+wvcus` as well.

---

## 🛠️ **Steps to Reproduce**

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd electron-issue-minimal
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Run the app:
   ```bash
   npm start
   ```

4. Observe the crash on startup with `electron@32.3.1+wvcus`.

5. (Optional) Downgrade Electron CastLabs version to `32.3.0+wvcus` to verify that the issue does not occur:
   ```bash
   npm install electron@32.3.0+wvcus --save-dev
   npm start
   ```

---

## ⚙️ **Environment Information**

- **Electron Version:** 32.3.1+wvcus (CastLabs fork) ❌
- **Electron Version:** 32.3.0+wvcus (CastLabs fork) ✅
- **Node.js Version:** v22.14.0 (LTS)
- **macOS Version:** Sequoia 15.3.1

---

## 📋 **Expected Behavior**

The app should launch without any errors, similar to how it behaves on `32.3.0+wvcus`.

---

## 🐛 **Actual Behavior**

The app crashes immediately with a `dyld` error related to loading the Electron Framework.

---


## 💡 **Additional Notes**

- This issue does **not** occur with the official Electron version `32.3.1`.
- The bug appears to be specific to macOS Sequoia (15.3.1).

