# Qwelium GitHub Login Setup

Qwelium uses Supabase Auth with GitHub OAuth. The browser-side integration is already in `auth.html`.

## One-time provider setup

1. Open the Supabase dashboard for project `iaodvouartweshehcjhv`.
2. Go to **Authentication → Providers → GitHub**.
3. Copy the Supabase callback URL shown there. It should be:

   `https://iaodvouartweshehcjhv.supabase.co/auth/v1/callback`

4. Open GitHub **Settings → Developer settings → OAuth Apps → New OAuth App**.
5. Use:
   - **Application name:** Qwelium
   - **Homepage URL:** `https://recgoblingu-lgtm.github.io/Qwelium/`
   - **Authorization callback URL:** the Supabase callback URL above
6. Copy the GitHub OAuth Client ID and generate a Client Secret.
7. Back in Supabase, enable GitHub and paste the Client ID and Client Secret, then save.
8. In Supabase **Authentication → URL Configuration**, add this redirect URL:

   `https://recgoblingu-lgtm.github.io/Qwelium/auth.html`

Do not put the GitHub Client Secret or a Supabase service-role key in this repository. Only the Supabase publishable key belongs in browser code.

## What the integration does

- `auth.html` starts GitHub OAuth with `signInWithOAuth()`.
- Supabase persists and refreshes the browser session.
- After login, Qwelium stores the display name and avatar locally for the existing static pages and redirects to `home.html`.
- `auth.html?logout=1` signs the user out and clears the compatibility values.
- `index.html` redirects to `auth.html` so old links continue to work.
