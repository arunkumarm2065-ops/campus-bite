# CampusBite — Firebase Live Demo (No Storage)

This version uses Firebase Authentication + Cloud Firestore + Firebase Hosting. It does not use Firebase Storage.

## 1. Firebase Authentication
Enable **Authentication → Sign-in method → Email/Password**.

Create the first Admin manually in Authentication:
- Email: `admin@campusbite.app`
- Password: choose your own password (6+ characters)

In Firestore create a document:
- Collection: `users`
- Document ID: the Admin user's Firebase Auth UID
- Fields:
  - `username`: `admin`
  - `name`: `CampusBite Admin`
  - `role`: `admin`

## 2. Firestore
The app seeds the default menu and settings automatically after the first authenticated session.

Paste `firestore.rules` into Firestore → Rules and Publish.

These rules are designed for a student/demo project. Production security should move stock changes, account provisioning, refunds, and privileged actions to trusted server code/custom claims.

## 3. Website
Use `index.html` as the site entry file. The Firebase configuration is already included for project `campus-bite-d350e`.

## 4. No Storage
Food images use an image URL instead of Firebase Storage. You can also leave the image URL blank and use the built-in food emoji.

## 5. Live multi-device behavior
- Admin adds a student → student account is created in Firebase Authentication + Firestore.
- Student can immediately log in from another phone/laptop.
- Menu, stock, orders, special opening times, parcel fee, reports, reviews and notifications are synced through Firestore listeners.
- Owner can manage menu/stock, parcel charge and order/refund status.

## 6. Hosting
If using Firebase CLI:
`firebase login`
`firebase use campus-bite-d350e`
`firebase deploy --only firestore:rules,hosting`

Or host the same `index.html` on another static host; Firestore/Auth still provide the shared data layer.
