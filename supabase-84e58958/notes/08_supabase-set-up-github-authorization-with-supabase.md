# Set up GitHub Authorization with Supabase

[Video link](https://www.egghead.io/lessons/supabase-set-up-github-authorization-with-supabase?pl=supabase-84e58958)

<TimeStamp start="0:30" end="0:35">

```js
const Auth = () => {
  return null
}

export default Auth
```

</TimeStamp>


<TimeStamp start="0:40" end="0:45">

```js
import Auth from '../components/auth'

<Auth />
```

</TimeStamp>

<TimeStamp start="0:55" end="1:05">

```js
const Auth = () => {
  return <div>
    <button>Log in with GitHub</button>
  </div>
}
```

</TimeStamp>

<TimeStamp start="1:25" end="1:30">

[Supabase api](https://supabase.io/docs/guides/api)

</TimeStamp>

<TimeStamp start="2:20" end="2:30">

```js
const signInWithGithub = async () => {
  let { user, error } = await supabase.auth.signIn({
    provider: 'github'
  })
}
```
</TimeStamp>

<TimeStamp start="2:45" end="2:52">

```js
<Auth supabase={supabase} />
```

</TimeStamp>

<TimeStamp start="3:55" end="4:05">

```js
const signInWithGithub = () => {
  supabase.auth.signIn({ provider: 'github' })
}
```

</TimeStamp>

<TimeStamp start="4:14" end="4:20">

```js
<button onClick={signInWithGithub}>Log in with GitHub</button>
```

</TimeStamp>
