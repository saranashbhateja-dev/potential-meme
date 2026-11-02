# Build notes

- New storage key isolates local progress from previous JEE OS versions.
- New curriculum IDs are namespaced `J26P`, `J26C`, and `J26M` to prevent accidental legacy row matches.
- Start date fixed to 2026-10-29 for a fresh install; it remains editable in Settings.
- Fixed two lectures per subject per study day; Sunday rest/test day preserved.
- DPP remains lecture-specific; daily subject practice remains date-specific.
- Supabase cloud snapshot must have `curriculumId: jeeos-2026-10-29-v1` to be loaded by this build. An older snapshot is not imported into the new curriculum.
- The existing Supabase schema in `SUPABASE-SCHEMA.sql` includes `jeeo_cloud_state` and RLS policies.
