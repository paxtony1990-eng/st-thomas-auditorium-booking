# St. Thomas C.S.I. Church — Auditorium Booking

A responsive static website for auditorium booking enquiries, connected to Supabase.

## Supabase
- Project ref: jnlesierxgzkcyrwhvcb (Mumbai)
- Table: public.auditorium_bookings
- Row Level Security: enabled
- Public visitors can submit pending booking requests; approved dates are visible
- Parish administrators need an Auth user with app_metadata.role = admin

## Admin setup
In Supabase Dashboard → Authentication → Users, create the parish admin login. Then run the following in SQL Editor after replacing the email:

```sql
update auth.users
set raw_app_meta_data = coalesce(raw_app_meta_data, '{}'::jsonb) || '{"role":"admin"}'::jsonb
where email = 'PARISH-ADMIN-EMAIL-HERE';
```

Admin login route: /admin

## Hosting
This is plain static HTML; no build step is required. On Render choose a Static Site:
- Build command: leave empty
- Publish directory: .
- Repository: paxtony1990-eng/st-thomas-auditorium-booking
- Branch: main

The Supabase publishable key is used in the browser; never add a service-role or secret key to frontend code.

## Launch checklist
Confirm auditorium capacity, facilities, permitted event types, rates, deposits, office contact details and cancellation rules. Replace the illustrative hero photo with an authorised image of the church/auditorium. Test with a visitor account and an administrator account. No online payment collection is implemented.
