# DURGAPUR BUZZ — HTML + Firebase (GitHub Pages)

This is a single-file static website. No Node.js, Next.js, Vercel, build command, or Firebase Storage is required.

## Files
- `index.html` — complete responsive news website, public pages, language menu, Firebase admin login and dashboard.
- `firestore.rules` — restricts writes to the single Super Admin UID.
- `README.md` — setup guide.

## GitHub Pages deployment (mobile-friendly)
1. Create a NEW public GitHub repository, for example `durgapur-buzz`.
2. Open the repository and choose **Add file → Upload files**.
3. Extract this ZIP on your device first. Upload the three files from inside the extracted folder (`index.html`, `firestore.rules`, `README.md`) to the repository root. Do not upload the ZIP itself.
4. Commit the files to the `main` branch.
5. Open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
6. Wait for GitHub Pages to publish. Your site will be at `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/`.

## Firebase setup
The Firebase web config for project `durgapur-buzz` is already in `index.html`.
1. In Firebase Console → Authentication → Sign-in method, enable **Email/Password**.
2. In Authentication → Users, create your admin user. Its UID must be exactly:
   `QdERp0w3SAaS18UWc7qkjIXZmii2`
   If the UID differs, the website will reject the login and the rules will deny writes.
3. Create a **Cloud Firestore** database.
4. Open Firestore → Rules, replace the rules with the complete contents of `firestore.rules`, and Publish.
5. Firebase Console → Authentication → Settings → Authorized domains: add `YOUR-USERNAME.github.io` (the host only, no path).
6. No Firebase Storage setup is needed.

## Admin
Open your published site and use the three-dot menu → Admin Login.
The Admin can create/edit/delete news, publish or save drafts, choose featured stories, and change the logo URL, breaking news, contact email, social links and tagline.

## News fields
News is stored in `news` collection. `site/settings` stores website settings.
Use publicly accessible direct image URLs (ending in .jpg/.png/.webp, or a provider's direct image URL). Video URL is saved and displayed as a link. No file upload is performed.

## Important
- GitHub Pages is static hosting. Firebase Authentication and Firestore provide the dynamic features.
- The Firebase API key in a browser app is not a password. Firestore Rules are the security boundary.
- Keep the Admin UID in both `index.html` and `firestore.rules` consistent.
- A single-file HTML app uses hash-free article view interactions and client-side search; search engines may index the homepage more reliably than individual article content.
