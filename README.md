# DURGAPUR BUZZ — Local Digital Service Hub

Static HTML/CSS/JavaScript website using the existing Firebase project `durgapur-buzz`.

## Deploy
1. Upload `index.html` to the existing GitHub Pages repository (replace the old homepage).
2. In Firebase Console → Firestore Database → Rules, publish the supplied `firestore.rules`.
3. In Firebase Console → Storage → Rules, publish the supplied `storage.rules` if/when you enable Storage uploads.
4. Keep the existing Firebase Authentication Email/Password admin user. Admin access is restricted in the client to the existing Super Admin UID configured in `index.html`.
5. Open the site and click **Admin Login**.

## Admin-managed collections
`services`, `tools`, `government`, `forms`, `businesses`, `blogs`, `notices`, `announcements`, `suggestions`, and `site/settings`.

## Notes
- Existing Firebase project ID, API config, Admin UID, and `site/settings` document are retained.
- The old `news` collection is not deleted or migrated. This build is a local digital service hub, not a news portal.
- Add a title and status when creating content. Use `Published` to show it publicly, `Draft` to keep it hidden, and `Hidden` to temporarily hide it.
- This version accepts image/PDF URLs in content forms. Firebase Storage rules are included for a future upload control; the upload UI is not yet enabled in this build.
- Admin UID checks in the interface are not a substitute for Firestore Rules. Publish the rules before using the new collections.


Admin update: Hero Slider Control is now a separate option under Website Control. Homepage & Website Settings no longer contains the slide editor.


EVENTS SECTION UPDATE
- Added Events section with Active Events and Upcoming Events tabs.
- Admin menu: Content Management > Events. Admin can add/edit/publish/draft/hide/delete events.
- Event fields: title, event type, artist name, date, time, location, description, image URL, event status.
- Firestore rules include events: public reads only published records; admin UID controls writes. Publish included firestore.rules in Firebase Console.
