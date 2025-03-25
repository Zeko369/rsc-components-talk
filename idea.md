> Hi

About me for 25s

> "packaging" worked before

big vendor folder

CDN links

copy pasting JS inits into <script> tags

> yeah... not ideal

> then came "components"

Components allowed you to bring in
-> layout / template
-> interactivity (JS)
-> styling

> This was amazing, and it's still one of the most enticing parts of "components" architectures 

> But, react components are limited to client side... or are they?

> let's take a look at how others do this?
-> rails engine
-> give example of a blog, models, controllers, views, helpers...

> Ok let's see how we'd do this in react land

> Let's pick remix
-> example of loader / action for comment / pass DBs / render in view

> Hmm this is really nice, but how to make this portable? you make a remix package with 3 exports?

> I mean this could in theory work... but not the most ergonomic thing

> So what's the problem
-> we have an abstraction for templating/styling/interacting
But how do we load server data?
How do we call server

> RSCs / React Server Actions (functions*)

Let's go back to our example

-> moves DB call to RSC

-> ok, ok, this is starting to look nice

-> what about commenting?

-> action 🔥

-> but how to pass our own db / migrations?
  => drizzle example with entites

> 👀 so this is possible?

> Yeah, this is importable from npm

-> notion-rsc

> Ok, but besides a dumb commenting example, what else could we build with this?
-> glad you asked

> Ever done file uploads?
-> there is a really good product used by the react community by the skater boi from california
-> but sometimes you need to use your own buckets / have other requirements

> So what do we need to build this

> I mean we can just make a react component that generates presigned key on the client and then po...
=> STOP

> yeah, ok, let's move that to the server
=> action -> client -> button

> What else?
How about a stripe handling UI?
-> pass user email and then render go to checkout / go to billing screen

> So where / why / how?
-> well sadly, only next right now
-> but remix and TS soon

> But why?
-> you could get a similar thing by mounting a few endpoints / doing manual prefetching?

-> well I started asking myself something similar after working on this talk
-> RSC is some great tech, streaming SSR, packaging server actions, less boilerplate, less data sent, faster hydration

but it has issues

=> Still locked into Next appDir
  -> despite the fact I've used this for years in prod, still don't think it's the correct solution for a lot of cases
=> Still no "server functions"
=> Still no "lazy load RSC on demand"
=> some problems if you wanna build a package
  => there is currently no "revalidate this RSC" / "redirect(/foo)" and similar generic helpers that would work everywhere

-> Right now packaged RSCs are just a more native way the [...api] packaging we've been doing
