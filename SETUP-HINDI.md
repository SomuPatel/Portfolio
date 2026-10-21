# Hindi Setup Guide

1. ZIP extract karo. `index.html`, `profile-photo.jpg` aur `profile-backup.json` GitHub repository ke root mein upload karo. Folder upload nahi hota to ZIP extract karke files select karo; photo root mein honi chahiye.
2. GitHub → Settings → Pages → Deploy from a branch → `main` → `/(root)` → Save.
3. Firebase Authentication → Sign-in method → Email/Password enable karo. Users mein `somu893@portfolio-admin.com` account create karo aur naya strong password set karo.
4. Firestore Database → Rules mein `firestore.rules` ka code paste karke Publish karo.
5. Firebase Authentication → Settings → Authorized domains mein `somupatel.github.io` add karo.
6. Site par Admin Login → ID `Somu893` aur Firebase user ka password.

Admin editor mein poora profile JSON edit hota hai. Valid JSON rakhna; save ke baad document `profiles/main` update hoga.
