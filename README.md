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


## Multi-level Directory Setup

This build adds `directoryCategories` and `directoryItems` Firestore collections. Publish categories and listings from Admin Panel. Categories support unlimited nesting through `parentId`. Public website queries only published documents. The included `firestore.rules` allows public reads of published category/listing documents and Admin-only writes for these collections. Replace the Firestore rules in Firebase Console with the included rules before using the new directory tools.

UI refinement: WhatsApp submission is a fixed bottom-right + button. The form does not ask for submitter name or phone; users can suggest another person's/provider's details. Global back/ghost button contrast has been increased.

Admin panel update (2026-11-15):
- Implemented missing Sub-Category Management and Directory Listing Management handlers (CRUD) that were referenced by the menu but not defined, which caused those menu options not to open.
- Added standalone Featured Management under Website Control, backed by the `featuredItems` Firestore collection.
- Simplified Hero Slider Control to exactly three image URL fields and a 3/6/9-second interval selector.
- Added `featuredItems` to Firestore rules for public published reads and admin-only writes.
- Verified JavaScript syntax with Node.js and ZIP integrity.
