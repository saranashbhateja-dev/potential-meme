# JEE OS 4.3.0 — Adaptive Lecture Planner

This build uses the supplied JEE curriculum and preserves the existing UI, sequential chapter planner, revision system, DPP/practice tracking, Supabase cloud sync, and Android build workflow. The test system is absent from the visible app.

## Curriculum
- Start date: **29 October 2026**
- Physics: 31 chapters / 196 lectures
- Chemistry: 33 chapters / 257 lectures
- Mathematics: 30 chapters / 205 lectures
- Total: **94 chapters / 658 lectures**
- The chapter order, lecture counts, and URLs are copied from the supplied data file.

## Daily plan
Every study day schedules four total lectures by default, including Sundays. When all three subjects have unfinished lectures, the planner assigns one lecture to each and allocates the extra slot to the subject with the largest fraction of its syllabus remaining. It preserves the configured subject display order and chapter order. The daily target can be changed to 3, 4, 5, or 6 total lectures in Settings. Each scheduled lecture has its own persistent DPP checkbox, plus one date-specific practice checkbox for each subject.

## Revision
The six-cycle spaced revision system is retained. Revision starts after all lectures in a chapter are completed. The test system is removed from the visible app; old test data may remain in backups/cloud snapshots for backward compatibility, but no tests are scheduled or displayed.

## Desktop launch (Windows)
1. Install Node.js 22 or newer.
2. Extract this ZIP to a writable folder.
3. Run `start.bat`.
4. The app opens at `http://127.0.0.1:3000`. Do not open `index.html` directly.

## Supabase cloud sync
The app retains the Supabase project URL and publishable key from the existing project. Sign in using the same account on desktop and Android to sync progress. State is saved locally first and then synchronized to `jeeo_cloud_state`; row-level security remains scoped to the authenticated user. This release retains the existing curriculum ID so lecture progress is preserved. Older saved settings without `dailyTotal` migrate to the four-lecture default, and the scheduler cache version forces the new plan to regenerate.

For safety, only the Supabase publishable key is used in the client; never put a service-role key in this app.

## Android APK
The GitHub Actions workflow builds a debug APK on push to `main` or via **Actions → Build JEE OS 4.3 APK → Run workflow**. Download the artifact named `JEE-OS-4.3-debug-apk`. The APK is built by GitHub Actions; this ZIP does not contain a prebuilt APK.


## Version 4.3.0 adaptive four-lecture planner

The Settings tab supports theme, accent color, interface density, text size, total daily lecture target (3–6; default 4), subject order, optional rest days, plan start date, exam date, and revision buffer. Sundays remain study days by default. Settings are included in JSON backups and the cloud snapshot. See `PATCH-NOTES-ADAPTIVE-4-LECTURES.txt`.
