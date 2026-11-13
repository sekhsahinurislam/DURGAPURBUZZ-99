# DURGAPUR BUZZ – Independent Facebook Posts + Reading UI

## What changed
- Facebook links are now independent posts, not attached to a regular news article.
- Admin panel has a separate **Facebook Posts** tab.
- Admin can add a title, required Facebook post URL, optional thumbnail URL, and optional short note; edit and delete posts.
- Homepage has a separate **ফেসবুক থেকে / Facebook Updates** section.
- Refined mobile-first typography, card spacing, article line-height, and responsive layout for easier reading.
- Existing Firebase Auth, News, site settings, logo, ticker, and footer credit are retained.

## Required Firestore Rules update
Open Firebase Console → Firestore Database → Rules. Add the `facebookPosts` match block from the included `firestore.rules` file, then click **Publish**. Do not remove the existing `news` or `site` rules.

```javascript
match /facebookPosts/{postId} {
  allow read: if resource.data.status == "published" || isAdmin();
  allow create, update, delete: if isAdmin();
}
```

## Deploy
1. Extract this ZIP.
2. Replace the repository's `index.html` with the included `index.html`.
3. Commit the change to GitHub Pages.
4. Publish the Firestore Rules addition above.
5. Open the Admin panel → Facebook Posts to publish independent Facebook links.

Facebook links open the original Facebook post in a new tab. This does not import Facebook post text automatically.
