# Owner account setup

The app's Owner role is controlled by the private `public.gc_admins` table. There is no client-side admin toggle, and regular users cannot grant themselves a role.

## Provision the owner

1. Create a normal account in Level Collectors and confirm its email.
2. In the Supabase Dashboard for the `gd card game` project, open **SQL Editor**.
3. Replace `OWNER_EMAIL_HERE` in the query below with the exact email used by the account, then run it:

```sql
insert into public.gc_admins (user_id, role)
select id, 'owner'
from auth.users
where lower(email) = lower('OWNER_EMAIL_HERE')
on conflict (user_id) do update set role = 'owner';
```

4. Sign out and back in (or refresh the app). The **Card Creator** navigation item will appear.

If the query inserts zero rows, the account has not been created/confirmed in this project yet, or the email did not match.

## Security notes

- Never add an admin insert policy for normal users.
- Do not expose a Supabase service-role/secret key in the website.
- Only a trusted project owner should run the provisioning SQL.
- New card metadata is stored in `public.gc_level_cards`; screenshots are represented by the `screenshot_url` field.
