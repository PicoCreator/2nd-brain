# Dev to CTO - How do I become a 10x developer?

> Instead of trying to be a 10x in everything.
> 
> You should instead aim to be a 100x developer in very specific situations. A 10x developer in some situations, and 1x developer in as many situations as possible. 
> 
> And to know very clearly, where is it you are good at (or inversly, bad at).
> 
> Because, the 10x developer, who is better then every other developer, at everything, is a myth

Unless you work for a really large tech companies, juggling hats, seems to be unavoidable. And I don't mean big hats like front-end, back-end developments. There are many smaller ones like vue.js, react, to language specific ones like java or typescript.

This is sadly an inevitble nature of our industry, as we are constantly inventing new ways to do various things. To the point where we have [over 400 ways just to get a computer to say "Hello World"](https://en.wikibooks.org/wiki/Computer_Programming/Hello_world)

As a result, it is impossible to know everything, let alone be good at everything.
But it is possible, to just know something, that given the right circumstances, slingshots you to be a "rockstar developer"

So lets rewind the clock to over a decade, to one of the biggest events that influenced my career.

And how situations, matter, more then anything else.

## How I became a 100x developer ... as a junior ...

There was an big MNC, who had a custom built java webapplication, and was being used by thousands of employees daily, with over a hundread thousand changes daily.

However there was a problem, with the number of records going in and out of the SQL servers, it was starting to slow down. And we were already upgrading the SQL server to its very limits.

So the obvious solution was to just use memcache to cache some of the results right?

Well. Yes, except that due to some security incidents in the past, and lack of HA... It was effectively banned.

So the team - was constantly fighting and failing to get approval for a memcache on one front. While simultaniously, trying their best at improving the SQL calls, optimize the stack, etc, etc.

This went on for a year, and the team was a losing uphill battle - every 10% improvement they made, was negated by double that in user growth. So things were getting slower and slower.

...

And that was where I appeared. A bright splunky young developer.

I was suppose to make some minor imporvements to the UI (basically junior work)

However, I was very annoyed by the dev server extreamly slow performance (we had loaded in a sanatized version of the production DB, to fix the same issues). 

I also just so happen to have been playing with hazelcast - a brand new, less then 1 year old, java based cluster and caching library that can be started up within the server itself. Something that I had just played with (by luck) for fun. And because there was no special restriction (or approval) on the type of java libraries we can add to our application.

So I did a working prototype, and had a demo, within the same week. For one page in the platform. Where the API calls went from more then 10 seconds, to under a second. And that changed everything ...

- Senior Dev A : Ahh, so you implemented memcache? Sadly, we know about that, and we been trying to get that approved for ages. 
- Me: Oh, but this isn't memcache. Because I could not install it on the company laptop. So I'm caching on the server side using hazelcast
- Senior Dev A : Unfortunately we run multiple API servers in HA mode. So in server caching will have sync issues.
- Me: No worries, hazelcast is able to run as a cluster between our various API servers.
- Senior Dev A : Meaning, we can this working for all pages, and in production without any changes on our servers.
- Senior Dev B : Holy S@#%

Within a month, we had all fully running in production, while ending the number 1 complains from the users, that had haunted the team for over a year.

My team manager, and his boss even off handingly said 
(while treating the team to very expensive food and drinks)

> I knew you we are smart kid, and that why we brought you onboard. But I never expected you to be a 10x, nor a 100x programmer who would help solve our problems overnight (exegerated, but you get the idea).

And went on to slingshot my career within the company. My boss, started listing various teams and projects, with big problems, moved me around to wherever I wanted to "try" repeat the miracle that had occured. (Which by some luck, I was able to do so several more times.... But thats another story)

That really got stuck to me. Because of how it was both simultaniously the truth and a lie...

Because I was an imposter, nothing, but a lucky imposter...

## The lucky imposter : who was a 0.1x developer

I was not a 1x or even a 10x developer at that time. On a technical level I knew less then my teammates. I was literally learning on the job ...

- My peers were able to do front end better then me
- My team, were the one who knew how to optimize SQL (and thought me, thank you!)
- My team, were the one who did the bulk of the work in the actual webapp development.
- My biggest credit, was I did the equivalent of "npm install miracle", and read its manual on how to configure it.

Additionally, my "miracle" solution, in hindsight had lots of issues which I dodged by luck

- Politics: If the company, didnt had its complicated HQ vs Regional politics, and allowed memcache, for my seniors before me - this whole situation would not have happened in the first place. My team was already on the right track (in memory caching, to offload SQL)
- Use Case: The user, rarely ever have multiple users editing the same record, due to the 1-on-1 nature of the data. So much could have gone wrong, if 2 users did a save at the same time, as our caching solution was not transactional safe.
	- We had a hidden, reload cache for this record button, to manually fix this issue if users ever reported it. But this could have gotten way worse in other use cases.
- Stability: Hazelcast was new, and in early days, it would have serious crash / restart issues under load (they have since improved). Which we dodged, because the team already had in place proper HA setup, which allowed such intermittent single server crashes to be gracefully handled. Credit here should go to the team.
- Security: Having an open port, with terrible password, to read all your cached data in your api cluster was a terrible idea. Thankfully someone else, knew how to read the manual and fix that.
- Stack: I would not have attempted to import a java project, if the API stack was built on C#, .Net, or ruby instead. Because I had no experience with their equivalent. (node.js was not out at that time)

And all these were issues i had no idea of at that time. And lucked out on.

- **On a technical level: I was at best a 0.5x**
- **On a buisness impact level: I was a 100x**

Even for subsequent "miracles", it was all about doing that one small thing, in the right place and time. For example...

- I fixed a reporting dashboard performance load issue, for a major user who insisted on real-time reporting. By introducing a 10 minute delay. The team have not considered the possibility of delayed reporting which they were used to (eg. end of day reports), because the user kept using the words "real-time".
- In another case, it was not even technical, sometimes the team already knew the answer. But they could not get the political buy-in, nor were they acknowledged. Until I was airdropped by the boss, and was able to bypass all the middle layers to get what the team needed. (more server, more access, etc.)

I was lucky. I had a handful of one-trick ponies, which would make me a 100x in the right situations, and landed on them.

And in almost all the cases, they were issues dealing with infrastructure, or performance. Which turns out to be what I am really good at.

Its also by some luck, that my managers and bosses, allowed me to choose the problems I wanted to fix. Which is a very rare privallege within the company (as I realise later). This allowed me to maximise my luck to impact ratio. Allowing me to "repeat" the "miracles".

Also overtime and experience, I realised the opposite - I am really slow at front-end development. Which was what I was originally supposed to be doing, before I got swept up in the whole 10x engineer fast-track. 

And having seen how some of my peers went for my generation. I reflect heavily on this, over the years.

## This is also, why senior developers tend to be 10x juniors

Once you start recognizing beyond the engineering generalization. And that everyone has individualized skills which they can be both a 100x at, or 0.1x at.

As such, over the years as I learnt more while moving across many teams and projects. And eventually became a "senior" developer.

I realized that, seniors in general, just have more skills they know they are atleast 1x or 10x at. And will also know what they are bad at. All which they have learn't via trial by fire (experience)

They would proactively, inform their manager, and priotise the tasks accordingly.

It does not mean they know how to do everything, it means they know how to avoid things that will be very unproductive. While ensuring things get done.

And because there is over a 100 ways to solve any one task or problem. They simply know in general more on what not to do.

Juniors on the other hand will struggle, as they lack the experience to know what they are good at or bad at. And to be honest, have no other ways to find out, other then just "try".

Once you understand this, you start to realise its simply about maximising the amount of things you know you can do reliably, or really good at. And to maximise your luck factor in being assigned such tasks over things your are bad at.

---

## How to maximise your luck at a 100x, and 10x

While I did give large credit to luck. Luck is not binary. You can game it. You can increase the amount of situations that aligns with you.

For juniors, and everyone in general : Because you do not know what you do not know.
Keep trying new things in technology and exploring. This will let you know what are things you maybe good at, or bad at.

For not-so-junior, and seniors : Once you have a better idea of what you are good at, make sure to expand the amount of situations where you can perform your best in. This is in part practise, in part research into adjecent technologies to ones your already great at. And start owning it, so that your managers / bosses will know that this is what they should give you instead. Letting you hit those 10x, or 100x situations more frequently.

Find atleast one thing you are really good at, even if its a very small and narrow thing. And build up from there. (some notable example: Regex, Configuring webpack, etc)

For seniors : If you haven't done so, start looking beyond technical. It does not mean you need to be in management. But with your unique technical knowledge of what can be done (or not done). Do play a more active role, in understanding the user or buisness use case. Allowing you to optimize with your managers how to best ensure those 10x, or 100x sucess rate for you and your team.

For those who are job hunting : If you know you are good at something, even if its 10x. Research at dig deeper in your job hunt. Try to find well funded (startup or MNC), who is facing difficulty in the very thing you are good at. Acknowledgingly, this can be hard to pull off - and does involve networking. But if you delibrately place yourself in the right place, and time situation, it maximise the impact for both you, and the company involved.

---

## As a CTO today & team leader today, this still holds - 10x is a myth - everyone is both 100x and 0.1x

Some would think, that the CTO of a UI testing tool (uilicious.com) would be really good with front end technologies.

But this is far from the truth, on average, a fresh hire / junior in the company is typically faster then me in writting frontend components with the modern frontend frameworks (ie. vue.js, react).

In that sense, because im also a manager today. This turns the tables around. Because, it made me realised how toxic and bad the 10x engineer myth is.

Its an oversimplification of labels, and generalization of very unique situations. And IMHO a toxic conception that needs fixin
g.

Because, almost every startup 10x engineer myth, when dug deeper, turned out to have that one individual with that unique knowledge in the right place and time.

A management myth, because most managers "do not understand code", so for them all of it is "about the same". (eg. like how non-tech relatives assumes we are all good at IT support, and can fix their phones and computers, because we work in tech). 

This is a major thing, cause for every one individual who is a 100x at one task, they have a task which would make them a 0.1x as they get stuck into a timesink.

When in reality, its all about training and understanding the individual talents under the team, and placing them in roles and assigning them with task they excel in.

It is about understanding, and recognizing what is it, that each individual is a 100x at, and inversely a 0.1x at a few things. And that it is on the team leader, to oganize the task accordingly to best suite everyone's need.

Its also about realizing, that even if they cannot be a 100x in your situation now, they can potentially be elsewhere in other teams.

---

