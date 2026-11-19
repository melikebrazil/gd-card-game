# Owner account setup

The Owner role is controlled by the database table `public.gc_admins`. There is no client-side admin toggle, and regular users cannot grant themselves a role.

## Provision the owner

1. Create a normal Level Collectors account and confirm it.
2. In the Supabase Dashboard for the `gd card game` project, open **SQL Editor**.
3. Replace `YOUR_APP_USERNAME` with the exact Level Collectors username, then run:

```sql
insert into public.gc_admins (user_id, role)
select p.id, 'owner'
from public.gc_profiles p
join auth.users u on u.id = p.id
where lower(p.username) = lower('YOUR_APP_USERNAME')
on conflict (user_id) do update set role = 'owner';
```

4. Sign out and back in (or refresh the app). The **Card Creator** navigation item will appear.

If zero rows are inserted, create and confirm the account first and check the username spelling.

## Security notes

- Never add an admin insert policy for normal users.
- Do not expose a Supabase service-role/secret key in the website.
- Only a trusted project owner should run the provisioning SQL.
- New card metadata is stored in `public.gc_level_cards`; screenshots are stored as a `screenshot_url` value.
