JEE OS 3.1.0 — Supabase cloud sync + Android APK

Cloud sync
- Uses the existing Supabase project configured in app.js.
- Sign in with the same email/password on desktop and Android.
- Local progress is saved immediately. Cloud snapshot sync is debounced and retries on later changes/online events.
- Realtime subscriptions propagate newer snapshots to other active devices.
- The new jeeo_cloud_state table is protected by per-user RLS. No service-role key is included in the client.
- First sign-in with no snapshot imports the legacy jeeo_* data into a snapshot and leaves legacy rows intact.
- Concurrent offline edits are last-write-wins; reconnect devices before switching between them.

Android APK
- The repository contains a GitHub Actions workflow at .github/workflows/build-apk.yml.
- Push this folder's contents to a GitHub repository, then open Actions > Build Jee OS APK > Run workflow.
- Download the Jee-OS-debug-apk artifact and extract app-debug.apk.
- The APK uses the same Supabase project and account, provided the device has network access and the user signs in.
- This ZIP does not include a prebuilt APK. A local Android SDK is required for a local build; the current build environment has Java/Node but no Android SDK.
