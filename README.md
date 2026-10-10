# Burrito

Small groups of neighbors, a real plan, a text. You just show up.

## What's here

- `index.html` — the whole landing page. Static, no build step. Signups post straight to Supabase REST.

## Backend

- Supabase project `burrito` (ref `yvfuljjwmtakaowbpexs`, us-west-1).
- Table `public.signups`. Row level security on. The anon key can only insert
  `first_name, phone, neighborhood, profile, referred_by`; it cannot read, update or delete.
- Phone numbers are unique on digits only, so `(415) 555-0100` and `+14155550100` are the same person.
- Operator columns (`phone_verified`, `events_invited`, `events_attended`, `notes`) are only writable from the dashboard or with the service key.

## Reading signups

Supabase dashboard → Table editor → `signups`, or:

```sql
select created_at, first_name, phone, neighborhood, referred_by, phone_verified from public.signups order by created_at desc;
```

## Deploy

GitHub Pages from `main`, root. Any push to `main` is live within a minute.
