# MGM Portal — Android App (Capacitor)

Tumhara web portal (`www/`) native Android app mein wrap hota hai.

## Option A — GitHub se APK (Android Studio ki zaroorat nahi)
1. Is folder ko ek naye GitHub repo mein push karo (branch: `main`).
2. Repo ke **Actions** tab mein "Build Android APK" workflow chalega (~5 min).
3. Run khulne par neeche **Artifacts → mgm-portal-debug-apk** download karo.
4. `app-debug.apk` phone mein bhejo aur install karo (Unknown sources allow karna padega).

## Option B — Local (Android Studio + JDK 17 + Node 18+)
```bash
npm install
npx cap add android
npx cap sync android
npx cap open android     # Android Studio khulega → Run ▶ ya Build > Build APK
```

## Web files update karne ke baad
`www/` mein edit karo, phir `npx cap sync android` aur dobara build.

## Icon / splash
`npm i -D @capacitor/assets` → `assets/icon.png` (1024x1024) rakho → `npx capacitor-assets generate --android`

## Notes
- Fonts aur Font Awesome CDN se aate hain, to first load pe internet chahiye.
- `bg.mp4` login background ke liye `www/` mein daalo, warna dark fallback dikhega.
- Play Store ke liye signed **release** build (keystore) chahiye — debug APK sirf testing ke liye hai.
