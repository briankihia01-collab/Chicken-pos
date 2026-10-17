SHARP-BOY POS - SETUP (works from a phone)

1. HOST IT: go to app.netlify.com, sign up, Add new project > Deploy manually, choose this zip.
   Open the address Netlify gives you in Chrome > menu > Install app.
2. FIREBASE (free): console.firebase.google.com > Add project > turn Analytics off.
   - Build > Authentication > Get started > Email/Password > Enable. Users tab > Add user (one per worker).
   - Build > Firestore Database > Create database. Rules tab: paste the rules below, then Publish:
       rules_version = '2';
       service cloud.firestore {
         match /databases/{database}/documents {
           match /{document=**} { allow read, write: if request.auth != null; }
         }
       }
   - Project settings (gear) > Your apps > Web (</>) > register. Copy the firebaseConfig block.
3. CONNECT: in the app, Items tab > Sync between phones > paste the block > Connect. Sign in.
   Then tap "Copy worker link" and send it to workers on WhatsApp. They open it, install the app and sign in.
   If sign-in is refused, add your Netlify address under Authentication > Settings > Authorized domains.
4. PLAY STORE (optional): pwabuilder.com with your Netlify address; use store-listing.txt for the text.
