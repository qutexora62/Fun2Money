# FB_Setup.md — Fun2Money Firebase Setup Guide

## 1) Project create karna
1. Firebase Console open karo: `console.firebase.google.com`
2. **Add project** par click karo.
3. Project name me `Fun2Money` likho.
4. Continue karo.
5. Google Analytics optional hai — OFF bhi rakh sakte ho.
6. **Create project** dabao.

## 2) Authentication setup
1. Left sidebar me **Authentication** open karo.
2. **Get started** dabao.
3. **Sign-in method** me jao.
4. **Email/Password** enable karo aur **Save** karo.
5. **Users** tab me **Add user** karo:
   - Email: `admin@fun2money.com`
   - Password: `admin123`
6. User create hone ke baad uska **UID copy** karo. Ye aage admin document me kaam aayega.

## 3) Firestore Database setup
1. Left sidebar me **Firestore Database** open karo.
2. **Create database** dabao.
3. Start ke liye **Test mode** use kar sakte ho.
4. Location me `asia-south1 (Mumbai)` ya `asia-southeast1` select karo.
5. **Enable** karo.

## 4) Realtime Database setup
1. Left sidebar me **Realtime Database** open karo.
2. **Create database** dabao.
3. **Test mode** select karo.
4. Database URL copy karo.
5. Isi URL ko `firebaseConfig.databaseURL` me use karna hai.

## 5) Web app register karna
1. Project settings (gear icon) kholo.
2. **General** tab me jao.
3. **Your apps** section me **Web** app add karo.
4. Nickname: `Fun2Money`
5. **Register app** dabao.
6. Firebase config object copy karo.
7. Jo values milen unhe `admin.html`, `user.html`, `subadmin.html` me paste karo.

## 6) Firestore rules set karna
Firestore Database → **Rules** tab me ye paste karo:

```rules
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /settings/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /paymentUrls/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /socialLinks/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /banners/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /appUpdates/{doc} {
      allow read: if true;
      allow write: if request.auth != null;
    }

    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

> Publish dabao.

## 7) Realtime Database rules set karna
Realtime Database → **Rules** tab me ye paste karo:

```json
{
  "rules": {
    ".read": true,
    ".write": true,
    "presence": {
      "$uid": {
        ".read": true,
        ".write": "auth != null && auth.uid === $uid"
      }
    },
    "notifications": {
      ".read": true,
      ".write": "auth != null"
    }
  }
}
```

> Publish dabao.

## 8) Admin document create karna
1. Firestore Database me **Start collection** dabao.
2. Collection name: `admins`
3. Document ID: step 2 me jo admin UID copy kiya tha, wahi paste karo.
4. Field add karo:
   - `email` = `admin@fun2money.com`
5. Save karo.

## 9) Settings document create karna
1. Firestore me **Start collection** dabao.
2. Collection name: `settings`
3. Document ID: `general`
4. Fields add karo:
   - `signupBonus` = `0`
   - `telegramUrl` = `https://t.me/fun2money`
   - `getKeyUrl` = `https://t.me/fun2money`
   - `appDescription` = `Fun2Money is India's trusted gaming platform`
   - `basePlayerCount` = `0`
   - `bannerTimer` = `4000`
   - `accessKey` = `FN2M-CUTEXXXX`  _(optional but useful for sub-admin login)_
5. Save karo.

## 10) Firebase config replace karna
1. `admin.html`, `user.html`, `subadmin.html` khol lo.
2. Har file me `firebaseConfig` object dhundo.
3. Firebase Console se mili real values paste karo:
   - `apiKey`
   - `authDomain`
   - `projectId`
   - `storageBucket`
   - `messagingSenderId`
   - `appId`
   - `databaseURL`
4. Placeholder values ko replace kar do.

## 11) Files ko host karna
1. Teeno HTML files aur `FB_Setup.md` ko same folder me rakho.
2. Firebase Hosting, Netlify, Vercel, ya kisi bhi static host pe deploy karo.
3. Agar Android WebView app banana hai to in files ko assets folder me rakh sakte ho.

## 12) Testing karna
1. **Admin panel**: `admin@fun2money.com` / `admin123` se login.
2. **User panel**: signup karke login.
3. **Sub-Admin panel**: kisi bhi `@gmail.com` email aur valid access key se login.
4. Tournaments create karo, join karo, winners declare karo, claim test karo.
5. Add cash, withdraw, ban/unban, balance update, broadcast — sab test karo.

## Collections reminder
- `admins`
- `users`
- `profiles`
- `matches`
- `transactions`
- `banners`
- `winners`
- `notifications`
- `socialLinks`
- `settings/general`
- `paymentUrls`
- `subProfiles`
- `subWallets`
- `appUpdates/user`
- `appUpdates/subadmin`
- `joinedMatches`

## Final note
Ye setup Firebase Auth + Cloud Firestore + Realtime Database ke saath connected hai.  
Single-file HTML structure ki wajah se direct deploy aur testing easy ho jata hai.
