# Use Triggers to Automatically Update Your Supabase Tables

[Video link](https://www.egghead.io/lessons/supabase-use-triggers-to-automatically-update-your-supabase-tables?pl=supabase-84e58958)

<TimeStamp start="1:04" end="1:09">

If you want to know more about triggers you can review this [documentation](https://supabase.io/blog/2021/07/30/supabase-functions-updates#postgresql-triggers).

</TimeStamp>

<TimeStamp start="1:13" end="1:33">
  
Documentation on creating public user tables has been [moved here](https://supabase.io/docs/guides/auth/managing-user-data). Supabase has also removed triggers from this doc but you can still use them.
  
</TimeStamp>

<TimeStamp start="3:20" end="3:30">

The code should look like this: 

```sql
-- inserts a row into public.user
create function public.handle_new_user()
returns trigger as $$
begin
  insert into public.user (id)
  values (new.id)
  return new;
end;
$$ language plpgsql security definer;
-- trigger the function every time a user is created
create trigger on_auth_user_create
  after insert on auth.users
  for each row execute procedure public.handle_new_user();
```

</TimeStamp>

<TimeStamp start="4:11" end="4:20">

Remember we are using this trigger with the purpose of allowing `public.user` table have access `auth.users` table. We need a trigger since these two tables have different schemas. 

</TimeStamp>