---
title: Packaged RSCs
drawings:
  persist: false
# theme: geist
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
# transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# OpenAuth Stuff

Lil Bro | @thdxr

---
layout: image
image: /assets/dax.jpeg
backgroundSize: 100%
backgroundPosition: center
class: object-contain
---

---
layout: center
---

# So... OpenAuth?

---
layout: center
---

<li><b>Universal</b>: You can deploy it as a standalone service or embed it into an existing application. It works with any framework or platform.</li>
<li><b>Self-hosted</b>: It runs entirely on your infrastructure and can be deployed on Node.js, Bun, AWS Lambda, or Cloudflare Workers.</li>
<li><b>Standards-based</b>: It implements the OAuth 2.0 spec and is based on web standards. So any OAuth client can use it.</li>
<li><b>Customizable</b>: It comes with prebuilt themeable UI that you can customize or opt out of.</li>

---
layout: center
---

# "But do you want your auth data open?"

---
layout: image
image: /assets/clerk.png
backgroundSize: 70%
backgroundPosition: center
class: object-contain
---

---
layout: image
image: /assets/clerk2.png
backgroundSize: 60%
backgroundPosition: center
class: object-contain
---

---
layout: image
image: /assets/better.png
backgroundSize: 100%
backgroundPosition: center
class: object-contain
---

---
layout: center
---

# Ha ha ... funny

---
layout: intro
---

<span class="line-through">

# OpenAuth

</span>

# RSCs as "shippable" fullstack components

Fran Zekan | @Zeko369

<!-- ---

# Hi

<li v-click>Engineer from Croatia</li>

<li v-click>Work for Unidy</li>

<li v-click>Do triathlons (see ya'll for the run tomorrow)</li> -->

---
layout: center
---

# Engineer from 🇭🇷

---
layout: image
image: /assets/me.webp
backgroundSize: 60%
backgroundPosition: center
class: object-contain
---

---
layout: image
image: /assets/unidy.png
backgroundSize: 100%
backgroundPosition: center
class: object-contain
---

---
layout: center
class: text-center
---

# "Shippable" "fullstack" "components"

<!-- <div class="mt-12!" v-click>

> "Idea of bundling a piece of functionality into a SHARABLE <i>thing</i>"

</div> -->

---
layout: image
image: /assets/bootstrap.png
backgroundSize: 70%
backgroundPosition: center
class: object-contain
---

<!-- # "Shippable" "fullstack" "components" -->

<!-- <img src="/assets/bootstrap.png"> -->

---
disabled: true
---

# Packaging? What?

"wp-plugins with a bunch of git changes"

---
layout: center
disabled: true
---

# Yeah... not the most ideal

---
layout: center
---

# "component"

---

````md magic-move {lines: true}
```tsx
const Post  = React.createClass({
  getInitialState() {
    return { loading: true, data: null };
  },

  componentDidMount() {
    fetch(`http://company.com/api/posts/${this.props.id}`)
      .then(response => response.json())
      .then(data => this.setState({ loading: false, data }));
  },

  render() {
    if (this.state.loading) {
      return h('div', {}, 'Loading...');
    }

    return (
      h('div', {},
        this.state.data.map(post =>
          h('p', {}, post.title)
        )
      )
    );
  }
});
```

<!-- ```tsx
class Post extends React.Component {
  constructor(props) {
    super(props);
    this.state = { loading: true, data: null };
  }

  componentDidMount() {
    fetch(`http://company.com/api/posts/${this.props.id}`)
      .then(response => response.json())
      .then(data => this.setState({ loading: false, data }));
  }

  render() {
    if (this.state.loading) {
      return <div>Loading...</div>;
    }

    return (
      <div>
        {this.state.data.map(post => <p key={post.id}>{post.title}</p>)}
      </div>
    );
  }
}
``` -->

```tsx
function Post(props) {
  const [loading, setLoading] = useState(true);
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(`http://company.com/api/posts/${props.id}`)
      .then(response => response.json())
      .then(data => {
        setData(data);
        setLoading(false);
      });
  }, [props.id]);

  if (loading) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      {data.map(post => <p key={post.id}>{post.title}</p>)}
    </div>
  );
}
```
<!-- 
```tsx {all|1,12|5,7-9,13-14|4,16}
import css from 'who-still-uses-modules.module.css'

const Post() {
  const like = useLikeMutation();
  const { data } = usePostQuery();

  if(!data) {
    return <h1>Loading...</h1>
  }

  return (
    <div style={css.container}>
      <h1>{data.title}</h1>
      <p>{data.body}</p>

      <button onClick={like.mutate}>Like</button>
    </div>
  )
}
``` -->
````

---
layout: center
---

# We've been doing this for a while and it's dope

---
layout: image
image: /assets/forgetting.jpeg
backgroundSize: 20em 70%
---

---
layout: center
---

# "fullstack"?

---
layout: center
class: text-center
---

# Anyone here a rails/django dev?

<!-- (or heard of rails engines / django apps) -->

---

<LightOrDark>
  <template #dark>
    <img src="/assets/engine1-l.png" class="max-w-80% max-h-80% object-contain m-x-auto">
  </template>
  <template #light>
    <img src="/assets/engine1.png" class="max-w-80% max-h-80% object-contain m-x-auto">
  </template>
</LightOrDark>

---

<LightOrDark>
  <template #dark>
    <img src="/assets/engine2-l.png" class="max-w-80% max-h-80% object-contain m-x-auto">
  </template>
  <template #light>
    <img src="/assets/engine2.png" class="max-w-80% max-h-80% object-contain m-x-auto">
  </template>
</LightOrDark>

---
layout: image
image: /assets/wordpress.png
backgroundSize: 70%
backgroundPosition: center
class: object-contain
---

<!--
Powers 43.5% of web?
-->

---
layout: center
---

# "mini app" OR "fullstack component"

---
disabled: true
---

# "Fullstack component"

<ul class="mt-10">
  <li v-click> View (template / style) </li>
  <li v-click> Interactivity (Client JS) </li>
  <li v-click> Server fetching </li>
  <li v-click> Server mutations </li>
  <!-- <li v-click> DB? </li> -->
</ul>

---
layout: center
---

# Cool... can we do this in react?

---
layout: image
image: /assets/can.jpg
backgroundSize: 100%
backgroundPosition: center
class: object-contain
---

---

<!-- # Simple remix example -->

```tsx{*|4-6|14|18-19|20-22|8-11}
import { Form, useLoaderData, json, LoaderFunction  } from 'react-router-idk-ai-wrote-this';
import { db } from '../db';

export const loader = async ({ request, params }) => {
  return json({ post: await db.getPostById(params.postId) });
};

export const action = async ({ request, params }) => {
  await db.likePost(params.postId);
  return json({ ok: true });
};

export default function PostPage() {
  const { post } = useLoaderData();

  return (
    <div>
      <h2>{post.title}</h2>
      <p>{post.content}</p>
      <Form method="post">
        <button type="submit">Like ({post.likeCount})</button>
      </Form>
    </div>
  );
}
```

---
layout: center
---

# Epic right?

---
layout: center
---

# But... how do you share this?

---
layout: center
---

# Like this? 🤔

```tsx
export { loader, action, Component as default } from '@rsc-things/post-renderer'
```

---
layout: image
image: /assets/re-export.png
backgroundSize: 70%
backgroundPosition: center
class: object-contain
---

---
layout: center
---

# But what about overriding things? <span v-click="1">🫣</span>

````md magic-move {lines: true}
```tsx
import { Component } from '@rsc-things/post-renderer'
export { loader, action } from '@rsc-things/post-renderer'

export default function Page() {
  const data = useLoaderData();

  return (
    <div>
      <h1>My Container for {data.post.title}</h1>
      <Component>
    </div>
  )
}
```

```tsx
import { Component, loader as rootLoader, mergeLoaders } from '@rsc-things/post-renderer'
export { action } from '@rsc-things/post-renderer'

export const loader = () => {
  return mergeLoaders(
    rootLoader,
    async () => {
      return prisma.likes.count({ where: { postId: 123 } });
    }
  )
}

export default function Page() {
  const data = useLoaderData();

  return (
    <div>
      <h1>My Container for {data.post.title}</h1>
      <Component>
    </div>
  )
}
```
````

---
layout: center
---

# 🤔

---
layout: center
---

# Abstraction problem?

---
disabled: true
---

# Abstraction problem?

<ul class="mt-10">
  <li>✅ View (template / style) </li>
  <li>✅ Interactivity (Client JS) </li>
  <li v-click>🫣 Server fetching </li>
  <li v-click>🫣 Server mutations </li>
  <!-- <li v-click>🤔 DB? </li> -->
</ul>

---
layout: center
class: text-center
---

# React Server Components <br/> React Server Functions/Actions

---
layout: center
---

```tsx
import { PostRender } from '@rsc-things/post-render'

export default function Page({ params }) {
  return <PostRender id={params.postId} />
}
```

---
layout: center
---

```tsx{*|4|12-13|14-16|5-8}
import { db } from '../db';

export const PostRender = async ({ id }) => {
  const post = await db.getPostById(id)
  const action = async () => {
    'use server'
    await db.likePost(id)
  }

  return (
    <div>
      <h2>{post.title}</h2>
      <p>{post.content}</p>
      <form action={action}>
        <button type="submit">Like ({post.likeCount})</button>
      </form>
    </div>
  );
}
```

---
layout: center
---

````md magic-move {lines: true}

```tsx{1,5,7}
import { PostRender, PostFallback } from '@rsc-things/post-render'

export default function Page() {
  return (
    <Suspense fallback={<PostFallback/>}>
      <PostRender />
    </Suspense>
  )
}
```

```tsx
import { PostRender, PostFallback } from '@rsc-things/post-render'

export default function Page() {
  return (
    <div>
      <h1>My title</h1>

      <Suspense fallback={<PostFallback/>}>
        <PostRender />
      </Suspense>
    </div>
  )
}
```

```tsx
import { PostRender, PostFallback } from '@rsc-things/post-render'

export default async function Page({params}) {
  const postTitle = await getPost(params.postId)

  return (
    <div>
      <h1>My title</h1>

      <Suspense fallback={<PostFallback/>}>
        <PostRender />
      </Suspense>
    </div>
  )
}
```

```tsx
import { PostRender, PostFallback } from '@rsc-things/post-render'

export default async function Page({params}) {
  const postTitle = await getPost(params.postId)
  const share = async () => {
    'use server'

    // do something
  }

  return (
    <div>
      <h1>My title</h1>

      <Suspense fallback={<PostFallback/>}>
        <PostRender />
      </Suspense>
    </div>
  )
}
```

```tsx
// react-router soon™️ support
import { PostRender, PostFallback } from '@rsc-things/post-render'

export const loader = () => {
  return {
    post: <PostRender />
  }
}

export default function Page() {
  const data = useLoaderData();

  return (
    <div>
      <h1>My title</h1>

      {data.post}
    </div>
  )
}
```
````

---
layout: center
---

# Ok, anything in the wild doing this?

---
layout: center
---

`bun add notion-rsc`

---
layout: center
---

````md magic-move {lines: true}

```tsx{1|3-7|10}
import { createNotionComponents } from 'notion-rsc'

const { NotionPost } = createNotionComponents(
  process.env.NOTION_API_KEY,
  process.env.NOTION_DB_ID
)

export default function async PostPage({ params }) {
  return (
    <NotionPost id={params.slug} />
  )
}
```

<!-- ```tsx{3,14-18}
import { createNotionComponents } from 'notion-rsc'

const { NotionPost, getPosts } = createNotionComponents(
  process.env.NOTION_API_KEY,
  process.env.NOTION_DB_ID
)

export default function async PostPage({ params }) {
  return (
    <NotionPost id={params.slug} />
  )
}

export const getStaticParams = async () => {
  const posts = await getPosts();
  return posts.map(post => ({ slug: post.slug }))
}
``` -->

````

---
layout: center
class: text-center
---

# Any non "blogy" examples

Maybe some _proper_ interaction with the server?

---
layout: center
---

# Aha, glad you asked

---
layout: center
---

# How about file uploads to S3?

<!--
skaterboy from california
-->

---
layout: center
---

```tsx{*|3|4-7}
<input
  type="file"
  onChange={async (event) => {
    const presignedUrl = generatePresignedUrl(
      process.env.NEXT_PUBLIC_AWS_PRIVATE_KEY, // TODO: Make this secure
      process.env.NEXT_PUBLIC_AWS_BUCKET
    )
    
    const formData = new FormData();
    formData.append("file", event.target.value);

    const res = await fetch(presign, {
      method: "POST",
      body: formData,
    });

    setUrl((await res.json())["url"])
  }}
/>
```

---
layout: center
---

<img src="/assets/the-what.jpg" class="max-w-80% max-h-80% object-contain m-x-auto">

---
layout: center
---

```tsx{5}
<input
  type="file"
  onChange={async (event) => {
    const presignedUrl = generatePresignedUrl(
      process.env.NEXT_PUBLIC_AWS_PRIVATE_KEY, // TODO: Make this secure
      process.env.NEXT_PUBLIC_AWS_BUCKET
    )
    
    const formData = new FormData();
    formData.append("file", event.target.value);

    const res = await fetch(presign, {
      method: "POST",
      body: formData,
    });

    setUrl((await res.json())["url"])
  }}
/>
```

---
layout: center
---

<img src="/assets/stop.png" class="max-w-80% max-h-80% object-contain m-x-auto">

---
layout: center
---

```tsx{12}
// /app/page.tsx
'use client'

export default function Page() {
  const [url, setUrl] = useState<string>();

  return (
    <>
      <input
        type="file"
        onChange={async (event) => {
          const presign = await fetch('/api/get-presigned-url').then(res => res.text());

          // bla bla send to S3
          const res = await fetch(presign, { method: "POST", body: formData });

          setUrl((await res.json())["url"])
        }}
      />

      {url && <img src={url} />}
    </>
  )
}
```

---
layout: center
---

```tsx
// /app/api/get-presigned-url/route.ts
export const GET = async () => {
  // some aws code... to generate a presigned url
  // safe to use private keys here

  // GPT didn't work on the plane when I was writing this demo

  return Response.text(`trust-me-bro-this-is-the-url`)
}
```

---
layout: center
disabled: true
---

```tsx{14-17}
// /app/page.tsx
'use client'

export default function Page() {
  const [url, setUrl] = useState<string>();

  return (
    <>
      <input
        type="file"
        onChange={async (event) => {
          const presign = await fetch('/api/presigned').then(res => res.text());

          // make formData -> send to S3
          const res = await fetch(presign, { method: "POST", body: formData });

          setUrl((await res.json())["url"])
        }}
      />

      {url ? <img src={url} /> : <h2>Upload image...</h2>}
    </>
  )
}
```

---
layout: center
---

# Ok, so how do you share this?

---
layout: center
---

`/api/get-presigned-url`

---
layout: center
---

# React Server Actions

<v-click>
"functions"

... I hate the nameing
</v-click>
---
layout: center
---

```tsx{1,8}
import { Upload } from "@rsc-uploader/package";

export default function Page() {
  const [url, setUrl] = useState<string>();

  return (
    <div>
      <Upload onUpload={setUrl} />

      {url ? <img src={url} /> : <h2>Upload image...</h2>}
    </div>
  );
}
```

---
layout: center
---

```tsx{*|4,10}
'use client'

// uploader.client.tsx
import { getPresignedUrl } from './action.server.ts'

export const Upload = (props) => {
  <input
    type="file"
    onChange={async (event) => {
      const presign = await getPresignedUrl();

      // make formData -> send to S3
      const res = await fetch(presign, { method: "POST", body: formData });

      props.onUpload((await res.json())["url"];)
    }}
  />
}
```

---
layout: center
---

```tsx{2,4}
// action.server.ts
'use server'

export const getPresignedUrl = async () => {
  // some aws code... to generate a presigned url
  // safe to use private keys here

  // GPT didn't work on the plane when I was writing this demo

  return `trust-me-bro-this-is-the-url`
}
```

---

# More...

<li v-click>Start a stripe checkout session</li>
<li v-click>Add to cart shopify button</li>
<li v-click>NPM/GITHUB/... style embeddable badges</li>
<li v-click>"Embedded apps"</li>
<li class="pl-8!" v-click>Embedded DB query engine (i.e. blazer for rails)</li>
<li class="pl-8!" v-click>Dashboard for calling predefined tasks in prod (i.e. Maintenance Tasks gem for rails)</li>
<li class="pl-8!" v-click>Monitor for your background jobs</li>

<span v-click="4" class="absolute bottom-14 text-center text-gray-500">Yes all of these are rails examples</span>

---
layout: center
disabled: true
---

# Where / why?

---
layout: center
disabled: true
---

# Where?

<v-click>

### Sadly... only next for now

But Remix and TanStack Start soon™️

</v-click>

---
layout: center
---

# Why?

---
layout: center
---

# Great DX ❤️

---
layout: center
---

# All the RSC goodies

---
layout: center
---

# But...

---
layout: center
---

# Next.js only 😞

---
layout: center
---

# Server Functions?

---
layout: center
---

# Lazy RSC? 

---
layout: center
---

# Generic "redirect" / "cookies" utils

---
layout: center
class: text-center
---

# Great idea, great tech... <v-click>def not there yet</v-click>

---
layout: center
class: text-center
---

# Thank you!

Twitter/GitHub - @Zeko369, Instagram/Strava - Fran Zekan
