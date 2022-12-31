![Image of a rockstar (not a developer)](./austin-neill-sxxnM-tRlVg-unsplash.jpg)

# Dev to CTO - How do I become a 10x developer?

The idea of a 10x developer, or a rockstar developer, being better than every other developer at everything, is a myth.

Instead, you should strive to be a 100x developer in very specific situations, a 10x developer in some, and a 1x developer in as many situations as possible. It's important to be aware of the areas you excel at and the areas that you may need to work on.

Unless you work for a large tech company, it's likely you'll be wearing multiple hats. On a daily basis, you'll need to be able to switch between front-end, back-end, and language-specific development, such as Java or TypeScript. This is due to the ever-changing nature of our industry and the sheer number of ways to achieve the same tasks - [like printing “Hello World” in over 400 different programming languages.](https://en.wikibooks.org/wiki/Computer_Programming/Hello_world)

![XKCD commic, on why there are so many standards in software dev](./xkcd-standards.png)

It's impossible to be good at everything, but it is possible to be great at something.

To elaborate, I'd like to share a story from over a decade ago which was a life-changing moment that had a huge impact on my career.

## How I Became a 100x Developer - as a Junior

I worked with a large MNC and was part of a team that was struggling to keep up with demand.

They had built a custom Java web application that thousands of employees were using daily, but as the number of records going in and out of the SQL servers scaled up. Things were slowing down. They had already upgraded the SQL server to its limits and needed new solutions. An obvious one was to use memcache to cache some of the results.

Unfortunately, memcache had been banned due to some security incidents in the past and the lack of HA. The managers had been trying to get approval for memcache for over a year but failed. Meanwhile, the devs fought an uphill battle as every 10% improvement was negated by double that in user growth.

This is where I came in, and joined.

I had no idea about their past 1 year of struggle and had been brought on board as a junior developer to help make some minor improvements to the UI, while the seniors focused on performance.

However because, I was very annoyed by the slow performance of the dev server. And I had been playing with Hazelcast - a brand new Java-based server clustering and caching library.

I decided to use it as an alternative to memcache. And was able to get it running on the application, which had no special restrictions or special approval requirements, that killed all previous solution.

I had a working prototype with a demo ready within the same week. For one page in the platform, the API calls went from more than 10 seconds to under a second. It was a game-changer.

The whole team jumped on board, and within a month, we had a "clustering solution which is definitely not memcache" in production.

As my team manager and his boss treated everyone to a banquet, my manager said to me, that when he brought me on board as a smart kid, he had never expected me to be a 10x or 100x programmer who could solve their problems overnight.

And that statement struck me hard.

Because I was an imposter – nothing but a lucky imposter.

![Image of an imposter, in among us the game](./imposter.jpeg)

## The Lucky Imposter – Who Was a 0.1x Developer

Technically, I was not a 1x or even a 10x developer. I knew less than my teammates, and I was learning on the job.

My peers could do the front end better than me and the team knew how to optimize SQL (and taught me, thank you!). My biggest credit was that I was able to do the equivalent of “npm install miracle” and read its manual on how to configure it.

In hindsight, there were many issues I had dodged by luck.

In hindsight, there were many issues I had dodged by luck. 
- Politics (which blocked memcache in the first place)
- Use case (we had no write contention safety, meaning if 2 edits happen in the same ms, cache will be badly updated. Thankfully, this rarely ever happens)
- Stability (v1 of hazelcast crashes like crazy, thankfully the API server was designed to be deployed in HA mode, so this was an annoyance to infra team at worst)
- Security (Having an open port to all data on the api server in a cluster, was a bad idea on my part, and a very junior mistake, until another senior thankfully read the docs on how to secure it)
- Language stack (if the server was in Python, .NET, C# or Ruby, I would have no idea how to even include a local cluster cache)

I was lucky to have a handful of one-trick ponies, which made me 100x in the right situations. Which were only possible because of the foundational work put in place by the rest of the team.

I was also lucky that my managers and bosses allowed me to choose the problems I wanted to fix, as they fast-tracked me, and threw me across multiple teams to "fix their problems". While allowing me to maximise my luck-to-impact ratio and repeat the “miracles”.

With experience, I also realised the opposite – I am slow at front-end development. This was what I was originally supposed to be doing before I was fast-tracked as a 10x engineer and it made me reflect a lot over the years. As it could have been the path I would have been stuck on.

It also struck me that in hindsight, having "mastered" hazelcast, and various other technologies. How much it would have failed for other teams, even in the same organisation, were it not for the unique situation, and safeguards, which should have been credited to the rest of the team.

I struck lucky, as a junior, if anything else.

![How professional engineers, have different standards](./professional-experience-engineer.jpeg)

## This is why Senior Developers Tend to be 10x Junior Developers

Once we look beyond the generalisations of engineering, it becomes clear that everyone has their skills, which can range from 100x to 0.1x.

Over the years, as I moved across many teams and projects, I eventually became a “senior” developer. During this time, I realised that seniors generally have more skills, and know what they are good and bad at. They can proactively inform their managers, and prioritise tasks accordingly. This doesn’t mean they know how to do everything, but it means they know what not to do.

Juniors, on the other hand, struggle with this as they lack the experience to know what they are good at or bad at. There isn’t an easy way to find this out other than to just “try”.

Once this is understood, it becomes apparent that it’s all about maximising the number of things you know you can do reliably and well. It’s also about maximising your luck factor when it comes to being assigned tasks, and ensuring you’re not stuck with things you’re bad at.

In a way for juniors, their progress will depend heavily on the alignment of their luck and skillset. Seniors, had more (but not full) control, over how to steer their progress.

In this case: Luck isn’t binary. You can increase the number of situations that align with you.

![Image of a pair of dice, representing luck](./lucas-santos-XIIsv6AshJY-unsplash.jpg)

## How to Maximise Your Situation Luck at 100x and 10x

For everyone, but especially for juniors and those just starting out, the best thing to do is to keep trying new things in technology and exploring. This will help you figure out what you’re good at and what you’re bad at.

For those who have a better idea of what they are good at, the next step is to expand the number of situations where they can perform their best. This involves some practice and research into adjacent technologies to the ones they already know. Once you become great at something, make sure to own it so your managers and bosses know that this is what they should give you. Which will increase the chances of hitting those 10x or 100x situations more frequently.

Find at least one thing you’re good at, even if it’s a very small and narrow thing. Build up from there. (Some notable examples include regex and configuring webpack.)

For seniors, if you haven’t done so already, start looking beyond the technical aspects of development. This doesn’t mean you have to move into management. But with your unique technical knowledge, you can play a more active role in understanding the user or business use case. This will allow you to optimise with your managers to ensure 10x or 100x success rates for you and your team.

For those who are job hunting, if you know you’re good at something, even if it’s 10x, do some research and dig deeper into your job hunt. Try to find a well-funded startup or MNC that is facing difficulty in the exact thing you’re good at. While this can be difficult to pull off and does involve some networking, if you place yourself in the right place and time, it will maximise the impact for both you and the company involved.

These are all things, you can do slowly over time, to improve the luck factor. And deliver that 10x experience more consistently.

> Special shout out to read swyx article on how to create luck : https://www.swyx.io/create-luck/

![Team of people, holding lego figs together](./vlad-hilitanu-1FI2QAYPa-Y-unsplash.jpg)

## As a CTO and Team Leader Today, This Still Holds - 10x Is a Myth - Everyone Is Both 100x and 0.1x

Some may think that the CTO of a UI testing tool such as Uilicious.com would be good with front-end technologies. However, this is far from the truth. Our average fresh hire or junior in the company is typically faster than me the CTO when it comes to writing front-end components with modern front-end frameworks such as Vue.js or React.

This has changed my perspective as a team leader/manager. It showed me how toxic and bad the 10x engineer myth is. It’s an oversimplification of labels and generalisation of very unique situations. It’s a toxic misconception that needs to be fixed.

Almost every startup 10x engineer myth, when looked into deeper, turns out to have an individual with unique knowledge in the right place and time. And was able to avoid the tasks they were 0.1x at.

In my case, it was focusing on infrastructure over front-end development. Where instead, I have other team members who are 1000x times better at doing frontend development.

This is an important realisation as a manager because, for every individual who is 100x at one task, there’s a task that makes them 0.1x as they get stuck in a time sink. It’s about understanding and recognising what each individual is 100x at, and what they’re 0.1x at.

While this sounds very straightforward, this is significantly harder in practice.

There are many things a team leader or developer will not know till they have tried it before. Or are given the time and opportunity, to hone and master the skillsets involved in those specific situations. There are also many things, especially new technologies, that no one is good at it, and is all about taking risk and a chances.

It’s the team leader’s job to organise tasks accordingly to best suit everyone’s needs. And if that is not possible, it's also about understanding that even if someone can’t be 100x in your situation now, they can potentially be elsewhere in other teams.

And is on every individual developer, to figure out what they are good and bad at, and to communicate that to their team accordingly.

So to death with the 10x Engineer Myth, Long live the 100x Engineer in specific situations

PS: If you have not made any new year's resolutions. Perhaps increasing your luck surface area could be it!

~ 🖖 live long and prosper  
Eugene Cheah: CTO of [**uilicious.com**](http://uilicious.com)

---

Image credits
- Austin Neill - rockstar image : https://unsplash.com/photos/sxxnM-tRlVg
- XKCD - comic on standards : https://xkcd.com/927/
- CenturiiC - Comic on experienced engineers : https://twitter.com/CenturiiC/status/1566060367825883136
- Lucas Santos - Dice picture : https://unsplash.com/photos/XIIsv6AshJY
- Vlad Hilitanu - Lego figs : https://unsplash.com/photos/1FI2QAYPa-Y