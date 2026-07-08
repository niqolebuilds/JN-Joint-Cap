Storage wired to Firebase Realtime Database. The original file called window.storage.get/set everywhere but never defined it, so nothing was actually persisting. 

I added Firebase (free tier, real-time sync across devices) with an anonymous-auth fallback so it won't crash before you configure it. To activate it:

Go to console.firebase.google.com → Add project (skip Analytics, don't need it).

Build → Realtime Database → Create Database → pick a region close to you.
Build → Authentication → Sign-in method → enable Anonymous.
Realtime Database → Rules tab → paste and publish:

json{ "rules": { "nj-capital": { ".read": "auth != null", ".write": "auth != null" } } }

Project Settings (gear icon) → General → Your apps → click the web icon (</>) → register → copy the firebaseConfig object it gives you.

Send me those values (or paste them yourself into the firebaseConfig block near the top of the <script> section) and it's live — same data, synced, whichever of you opens it.
