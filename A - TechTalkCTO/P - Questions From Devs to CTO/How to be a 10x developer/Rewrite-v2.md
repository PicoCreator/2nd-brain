# Dev to CTO - How do I become a 10x developer?

The idea of a 10x developer, who is better than every other developer at everything, is a myth. 

Instead, you should strive to be a 100x developer in very specific situations, a 10x developer in some, and a 1x developer in as many as possible. It's important to be aware of the areas you excel at and the areas that you may need to work on.

Unless you work for a large tech company, it's likely you'll be wearing multiple hats. On a daily basis, you'll need to be able to switch between front-end, back-end, and language-specific development, such as Java or TypeScript. This is due to the ever-changing nature of our industry and the sheer number of ways to achieve the same tasks - [like printing “Hello World” in over 400 different programming languages.](https://en.wikibooks.org/wiki/Computer_Programming/Hello_world)

It's impossible to be good at everything, but it is possible to be great at something. 

To illustrate this, I will share a story from over a decade ago which was a life-changing moment that had a huge impact on my career. 

## How I Became a 100x Developer - as a Junior

I worked at a large MNC and was part of a team that was struggling to keep up with demand. We had built a custom Java web application that thousands of employees were using daily, but the number of records going in and out of the SQL servers was slowing it down. We had already upgraded the SQL server to its limits so the obvious solution was to use memcache to cache some of the results. 

Unfortunately, memcache had been banned due to some security incidents in the past and the lack of HA. The team had been trying to get approval for memcache for over a year, but were losing an uphill battle as every 10% improvement was negated by double that in user growth.

This is where I came in. 

I had no idea on their past 1 year of struggle, I had been brought onboard as a junior developer to help make some minor improvements to the UI, while the seniors focused on performance.

However because, I was very annoyed by the slow performance of the dev server. And I had been playing with Hazelcast - a brand new Java-based server clustering and caching library.

I decided to use it as an alternative to memcache. And was able to get it running on the application, which had no special restrictions nor special approval requirement, that blocked previous solution.

I had a working prototype with a demo ready within the same week. For one page in the platform, the API calls went from more than 10 seconds to under a second. It was a game-changer.

My team manager and his boss treated the team to expensive food and drinks, with my manager saying he had never expected me to be a 10x or 100x programmer who could solve their problems overnight. 

And that statement struck me hard.

Because I was an imposter – nothing but a lucky imposter.

## The Lucky Imposter – Who Was a 0.1x Developer

Technically, I was not a 1x or even a 10x developer. I knew less than my teammates, and I was learning on the job. 

My peers could do front end better than me and the team knew how to optimize SQL (and taught me, thank you!). My biggest credit was that I was able to do the equivalent of “npm install miracle” and read its manual on how to configure it. 

In hindsight, there were many issues I had dodged by luck. 
- Politics (which blocked memcache in the first place)
- Use case (we had no write contention safety, meaning if 2 edits happen in the same ms, cache will be badly updated. Thankfully, this rarely ever happens)
- Stability (v1 of hazelcast crashes like crazy, thankfully the API server was designed to be deployed in HA mode, so this was an annoyance to infra team at worst)
- Security (Having an open port to all data on the api server in a cluster, was a bad idea on my part, and a very junior mistake, until another senior thankfully read the docs on how to secure it)
- Language stack (if the server was in Python, .NET, C# or Ruby, I would have no idea how to even include a local cluster cache)

I was lucky to have a handful of one-trick ponies, which made me a 100x in the right situations. Which were only possible because of the foundational work put in place by the rest of the team.

I was also lucky that my managers and bosses allowed me to choose the problems I wanted to fix, as they fast-tracked me, and threw me across multiple teams to "fix their problems". While allowing me to maximize my luck-to-impact ratio and repeat the “miracles”.

With experience, I also realised the opposite – I am slow at front-end development. This was what I was originally supposed to be doing before I was fast-tracked as a 10x engineer and it made me reflect a lot over the years. As it could have been the path I would have been stuck at by luck.

It also struck me that in hindsight, having "mastered" hazelcast, and various other technologies. How much it would have failed for other teams, even in the same organization, were it not for the unique situation, and safeguards, which should have been credited to the rest of the team.

I struck lucky, as a junior, if anything else.

## This is why Senior Developers Tend to be 10x Junior Developers

Once we look beyond the generalizations of engineering, it becomes clear that everyone has their own individual skills, which can range from 100x to 0.1x.

Over the years, as I moved across many teams and projects, I eventually became a “senior” developer. During this time, I realized that seniors generally have more skills, and know what they are good at and bad at. They are able to proactively inform their managers, and prioritize tasks accordingly. This doesn’t mean they know how to do everything, but it means they know what not to do.

Juniors, on the other hand, struggle with this as they lack the experience to know what they are good at or bad at. There isn’t an easy way to find this out other than to just “try”.

Once this is understood, it becomes apparent that it’s all about maximizing the amount of things you know you can do reliably and really well. It’s also about maximizing your luck factor when it comes to being assigned tasks, and ensuring you’re not stuck with things you’re bad at.

In a way for juniors, their progress will depend heavily on the alignment of their luck and skillset. For seniors, they had more (but not full) control, on how to stear their progress.

Which meant that in this case : Luck isn’t binary. You can increase the amount of situations that align with you.

## How to Maximize Your Situation Luck at 100x and 10x

For everyone, but especially for juniors and those just starting out, the best thing to do is to keep trying new things in technology and exploring. This will help you figure out what you’re good at and what you’re bad at.

For those who have a better idea of what they are good at, the next step is to expand the amount of situations where they can perform their best. This involves some practice and research into adjacent technologies to the ones they already know. Once you become great at something, make sure to own it so your managers and bosses know that this is what they should give you. This will increase the chances of hitting those 10x or 100x situations more frequently.

Find at least one thing you’re really good at, even if it’s a very small and narrow thing. Build up from there. (Some notable examples include regex and configuring webpack.)

For seniors, if you haven’t done so already, start looking beyond the technical aspects of development. This doesn’t mean you have to move into management. But with your unique technical knowledge, you can play a more active role in understanding the user or business use case. This will allow you to optimize with your managers to ensure 10x or 100x success rates for you and your team.

For those who are job hunting, if you know you’re good at something, even if it’s 10x, do some research and dig deeper into your job hunt. Try to find a well-funded startup or MNC that is facing difficulty in the exact thing you’re good at. While this can be difficult to pull off and does involve some networking, if you place yourself in the right place and time, it will maximize the impact for both you and the company involved.

## As a CTO and Team Leader Today, This Still Holds - 10x Is a Myth - Everyone Is Both 100x and 0.1x

Some may think that the CTO of a UI testing tool such as Uilicious.com would be really good with front-end technologies. However, this is far from the truth. On average, a fresh hire or junior in the company is typically faster than me when it comes to writing front-end components with modern front-end frameworks such as Vue.js or React.

This has changed my perspective as a manager. It showed me how toxic and bad the 10x engineer myth is. It’s an oversimplification of labels and generalization of very unique situations. It’s a toxic misconception that needs to be fixed. 

Almost every startup 10x engineer myth, when looked into deeper, turns out to have an individual with unique knowledge in the right place and time. And was able to avoid the tasks they were a 0.1x at. 

In my case, it was focusing on infrastructure over frontend development, who I have other team members who are 1000x times better then me at.

This is a major issue because for every individual who is 100x at one task, there’s a task which makes them 0.1x as they get stuck in a time sink. It’s about understanding and recognizing what each individual is 100x at, and what they’re 0.1x at. 

And this is significantly harder then it sounds on paper. There are many things you will not know till you have tried it before. Or are given the time and opportunity, to hone and master the skillsets involved in those specific situations. There are also many things, especially new technologies, where no one is good at it, and is all about taking the risk and a chance.

It’s the team leader’s job to organize tasks accordingly to best suit everyone’s needs. And if that is not possible, it's also about understanding that even if someone can’t be 100x in your situation now, they can potentially be elsewhere in other teams.

And its on every individual developer, to figure out what they are good and bad at, and to communicate that to their team accordingly.

PS: If you have not made any new year's resolutions. Perheps this could be it !