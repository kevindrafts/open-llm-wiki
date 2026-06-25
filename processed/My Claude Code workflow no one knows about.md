---
title: "My Claude Code workflow no one knows about"
source: "https://www.youtube.com/watch?v=YiitvyQGbkc"
author:
  - "[[Greg Isenberg]]"
published: 2026-04-13
created: 2026-05-09
description: "I sit down with Amir, who's back on the pod, and we walk through the full stack of taking a business idea from zero to a validated, A/B-tested landing page i..."
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=YiitvyQGbkc)

## Transcript

### Intro and Episode Preview

**0:00** · Amir is back on the pod. Thank you. Uh by the end of this episode, what are people going to learn? Today we're going to cover three aspects of building business, using new tools to actually build out landing pages, and then using other tools like humble to actually create high converting landing pages and running experiments.

**0:18** · So, we're going to cover how to actually use idea browser to build the right amount of context and planning to come up with an idea and build a landing page behind it, validate it, refine a design using paper design, and then going into humbulics and then running an experiment and tracking data to then come back and keep optimizing for conversions.

**0:36** · And you're going to commit to giving all the sauce. You're not holding back.

**0:40** · Raw. We're going to go going to go through everything, all the sauce. By the end of this, you're going to learn what it takes to take an idea, validate it, refine it, build a landing page with a nice design that's not vibe coded, and then get the right data to make some money.

**0:53** · Okay? Cuz there's a lot of tutorials that sort of promise that, right? But then you end up with like a purple vibe coded landing page.

**1:00** · Do I ever let you down?

**1:01** · No, you don't.

**1:01** · I don't let you down. That's true. There you go.

**1:04** · All right. Let's let's go. Let's get into it.

**1:06** · All right. So, Idea browser came out with something really cool um I really like which is basically you can now directly connect idea browser to cloud code as an MCP.

**1:23** · What's really interesting about it is you know you guys used to focus a lot on finding the right idea and then building it. But what was missing was how do you track the natural progression of how the business is evolving over time with the right context and documents to then come back and reference and say, "Okay, cool.

**1:39** · Like this is the idea I had. Here's how I started with ICP positioning. Now I want to come back and refine this or help me figure out um kind of what to pitch for or who to go after as my customers." So I was playing around with Jordan earlier today. We were on a live stream and we found this really cool idea which was an AI sparring partner for B2B sales teams.

**1:57** · The idea was how do we build a tool that kind of essentially helps reps practice on prospects on real time and get them to essentially go through simulations of being like, you know, going through a sales call and getting feedback on what they can improve on. We put together a quick landing page. We made some designs and then got some data in there and started tracking it. So, for today's episode, we're going to build on top of this.

**2:22** · We're going to refine the messaging. We're going to go through some sections on the website, refine the copy and design, show you how to use paper for that, and then also uh yeah, get some experiments and AB testing in there.

### Building a Growth Strategy with Idea Browser

**2:32** · Cool.

**2:33** · Um so what I so what we have so far is we have this one specific file which is uh like um offer definition and talk tracks that tells you who your your target customer is, the transformation, the offer, the value, competitive positioning. What's really cool is you guys also have skills in here which you can use to then build on top of the idea.

**2:54** · Um, so I actually want to use the lead magnet legend here, this specific skill to build the specific lead landing page site um to kind of get someone to come sign up and you know go through this process. So we're going to open up terminal and we already have all the MCPS connected. So if I go to MCP you can see I have idea browser, I have paper, all that. We're going to go through it. So, I'm going to say connect to idea idea browser MCP. Um, look at my AI B2B sparring partner project.

**3:25** · Pull the right context. Then use the lead magnet skill to create a By the way, I just got to say this cuz people are going to hate on you for the comments. In the comments, you type your your prompts. You don't use voice. Listen, I love Whisper Flow, but tell me how I'm going to do this while I'm doing the pod. Okay. All right. Just just you got to bear with me here.

**3:51** · Okay. So, when you're at home, are you using Whisper Flow or are you still typing?

**3:54** · I am. So, I'm using I usually use Whisper Flow when I'm initially starting a project or some some session and it's like a long It depends on honestly on the context of how much information I'm going to put in the terminal. But yeah, no, I got Whisper Flow, you know. Okay. I'm I'm up to date with the tools.

**4:10** · So what we're doing right now is we've pulled the right project context and so like we have context right here that's built as a file and then um we're then we also have a growth strategy that we worked on earlier and then from there we're going to uh build out a lead magnet specifically for this idea. So we have this AI B2B sparring partner. Um what's really cool is you got have you guys have this like activity streak to keep building on kind of your business.

**4:36** · And that's like the biggest problem these days. Like everyone can build landing pages. Everyone has ideas. How do you actually like know where to get customers? How do you actually grow it?

**4:45** · And that's the next kind of gap that we're all trying to solve for right now.

**4:49** · Well, yeah. I think uh we've all tried the vibe coding tools. We've all built stuff.

**4:54** · Um I do think that having the right idea is important.

**4:58** · Um finding the right niche is important.

**5:00** · But you know, the other thing is just like how do you get customers?

**5:05** · uh to to honestly just give you confidence to keep going.

**5:08** · Exactly.

**5:09** · Yeah.

**5:10** · Yeah.

**5:10** · Yeah. And and we're gonna eventually get there and I think you guys do a really good job of this and I'm not like promoting like I'm promoting idea browser don't get me wrong but I wasn't you know I'm actually using this tool myself now because that was kind of the biggest gap I had myself like with Humbolty was like okay cool I have all these great ideas and I've been understanding who our customer is and trying to get customers through trial and error.

**5:31** · And I was telling Jordan Jordan earlier I was like I wish I had idea bowseres sooner right so that I can come back and use these specific skills to um to understand okay cool what is the right growth strategy because a lot of what you guys have has been fully refined and we were going through this earlier today and it was interviewing me and asking me questions and I was like this is so impressive I wish I had humbalytics for this specifically so that I can come back and say okay cool like humb to go after director of marketings in this specific field with this kind of messaging and yeah so kudos

**6:00** · to you guys for building a really cool product with this and I think a lot of people now can actually use this to build the idea and then also help build the business as well. Um so we going back to cloud code we were connected to MCP we have built out the lead magnet which is basically five objections that kill fright software deals. So we actually niched down we built this AI BDB sparring partner in the fright software industry and it's going to say you're going to want to create a PDF guide um give them all Yep. So this is great. Okay, cool.

### Designing Landing Pages in Paper

**6:30** · So we we have the idea of the lead magnet and it should now actually save the file in here. Let's go back. Boom.

**6:39** · Now we have the file. So this is really cool. Like you have context of the ideas it came with and it's added here. Um now we're going to come back and use the the scale. I got to come back here. We have the where is this? The landing page architect. using and basically what we're going to do now is for the people that don't know paper is it's a really

**7:03** · cool tool where essentially it's connected so I'm going to take a step back typically with Figma you had designers creating static assets in Figma landing page designs and then handing off to engineering teams right the missing gap was now we have a lot of people that are building landing pages and websites with cloud code directly in code and refining it through there and then losing track of like what they're iterating on and not having the ability to be able to kind of refine this.

**7:26** · So with paper, what you're able to do is actually um have an interface connected to cloud code where you're ideulating creating iterations of iterations directly in the design and then coming up with like what direction you want to go with and then having it in code. So it's kind of like the intermediary step that we were missing before where people are just directly building in code and you know you can use paper. Or are there any other competitors that people use or just or just stick to paper?

**7:56** · I mean, so Figma just recently came out with their birectional ACP. MC ACP.

**8:01** · I'm in your world, man.

**8:03** · Totally.

**8:03** · Yeah.

**8:03** · MCP. Um uh where you can both design like uh you can take a design and build it to code or code to design to go birectional, which this is essentially what paper already is. Um, but I just feel like um, the tooling and the interface and the experience on paper is a lot nicer in my opinion and it just works a lot better. So, we're we're now connected to we've we've captured the lead magnet.

**8:26** · We have the landing page scale architect being added as well with the offer that we want to have and now we want to actually build out the page using paper. So, while that's going through it, I want to talk about kind of how you can refine your designs as well.

### Refining Copy, Layout, and Components in Paper

**8:42** · So often times you see people with kind of these vibecoded designs and they're not entirely sure how to actually go with like the right direction of building out a design system. What I typically like to do is always give Claude um a reference image of an existing design that I like. So, for example, I'll go into um an existing site or have some bookmarks of sites I like and I'll take the screenshots and I'll drop it into cloud and I'll say extrapolate like the key design elements from these pages and help me create a design system.

**9:12** · So, what you're seeing right now for example is a design system that I've created using cloud based on reference images so that we can kind of reference back into for future sessions.

**9:23** · So if I want to come back and create a new section or new component my landing page, I can say reference design style guide as like the basis as you're creating new components so that you have that consistency. Um now I want to show an example like again a lot of people have this misconception that vibe coded design is bad. This has all been fully vivecoded. We built all these animations, all these components using claude and doesn't seem that way. It seems very polished, very well refined.

**9:50** · And the way to do that is you refine it through paper and then give example components and illustrations from other websites or libraries to build on top of. So for example, um I use this tool quite a lot. It's called Tail Arc Tail Pro and they have a lot of great existing blocks and illustrations that you can use and you can actually install these and use it as a reference. So I'll go back into paper and I'll show you kind of how Oh, nice.

**10:16** · Right now, we're seeing Cloud Code design and build directly in paper on what this lead magnet looks like, which is really cool.

**10:26** · Really, really cool. I love the little kind of section by section it's building out.

**10:34** · So, I think this is perfect. Actually, this is a great segue to that. So, we're going to let it build out the landing page. Then, I'm going to show you how you can actually use tail arc as a reference point to then improve the design of this. So, so it goes from something like this to something a little bit more tailored like like this for example.

**10:52** · By the way, there's an ant on the table just there. Do we do we let the ant watch your your your demonstration or do we you know or do we sort of move him aside? What do you think?

**11:05** · I think we'll just we'll give him put him put him in I mean where do we put him?

**11:09** · Um I mean I I have nothing against the Yeah, he's chilling.

**11:13** · He's chilling.

**11:13** · He's getting the direct sauce. Yeah, he's we can give the ant some sauce, you know.

**11:17** · Here's a napkin in case.

**11:18** · Yeah.

**11:22** · Um, okay, cool. So, we're building out the section, which is pretty cool. Now, like a lot of people say, "Okay, cool.

**11:27** · Like, why don't I just build this directly in code? Why do I have to actually use paper?" The idea is that you can use paper to help build out different variations. So, if I want to try different layouts, I can just do it directly in here, make some refinements myself, especially for designers. I think this is super powerful for designers that want to just jump in and start changing things themselves without having to kind of use cloud code again or existing components they have. So we'll let this finish then I want to show you some examples of what I've also created in paper to show you that what's what's possible if you keep refining it and go through it go through it.

**11:59** · Perfect. So we're all done here. Now what does this look like in actual real practice if you spend time refining this. So this is all designed in paper.

**12:08** · Um, I've given the design style guide I have in Humbolytics. I've said here's the components you have and use these components to refine it. So, I actually build out some of these sections in here and then port it over to code. I or I even use it to create static assets that I want to use in ads, in thumbnails, whatever it is. This is all purely you like built using cloud. Now, how do you go back to actually refine the design here? Um, so what I do typically is I'll go into Tail Arc and find a section that I like.

**12:40** · So we have this like content area section. I'll go into um let's go into content right here. Okay, cool. I like I like this. I like this right here. Or maybe yeah, we'll use this one. Cool. So I'll go back in the terminal and I'll say install this tail arc component and use it for the content section in the lead magnet first.

**13:05** · Design it in paper and then we just need to pull the API key for tail arc. Cool.

**13:14** · I've actually never heard of tail arc.

**13:16** · Really?

**13:16** · Yeah.

**13:17** · Yeah. It's it's just another UI library.

**13:19** · I mean I'm not sure who's behind it. I think it's like an indie founder or something like that.

**13:23** · Looks clean.

**13:24** · Yeah.

**13:24** · Super clean. It's the way to go, you know. Kudos or shout out to whoever built this. I think it's a indie person. So, whoever it is, you've done a great job. Keep keep doing it.

**13:33** · Um, yeah, I'm a fan. I'm I'm a big fan. They got taste, that's for sure. So, what we're doing right now, we're just installing Tail Arc so that we can like install the right components here.

**13:45** · And um, yeah, what's special about this is that you can take those components that I showed you earlier. So if we're going to, for example, we're going to do the content one, this one specifically, and I can just drop it in as well, a screenshot to say like install this, use this component, and then I'll go back into paper and say like use it for this section here.

**14:07** · What's also interesting uh is, you know, showing tail arc, showing idea browser, the MCP, it's sort of a glimpse into like the future of software, right? Like you're not in the past we would go and just use SAS, right? Yeah, now it's like the work is getting done in the terminal.

**14:24** · Nailed it to again. It's becoming the interface for work for everything. You know, if you remember our first episode cursor was Yeah. Like you were you were right.

**14:32** · So you said what? I think your exact words were something like like Yeah. B I I think the mistake I made was I I I said cursor. That's what you said.

**14:42** · Yeah.

**14:42** · Cursor is the interface of work or it's the future of interface of work. I would say now terminal. The terminal is interface of work. We were, you know, we were very, you know, we were early. We were early. We were early. Like we're like, "Yo, markdowns are going to become a thing. You're going to do all your work in cursor, all of it in terminal."

**14:58** · People thought we were crazy.

**14:59** · Yeah. Yeah. Like here we are today, man. Everyone, you know, and we're showing you this and someone probably listening to this is probably like, "You guys are crazy."

**15:08** · 100%. Yeah, you know, uh, another thing for example was like you're now seeing people building out markdown pages on their websites to make it easier for agents to access, right? You look at what's happening now. People are giving agents wallets. What's going on here?

**15:22** · They're giving out wallets. They're giving them um emails, inboxes, stuff like that. So, it's insane to see um Yeah, yeah, it's it's insane to see kind of the evolution of that. And we're seeing actually tangent um I have a thesis. The thesis is that more agents are going to actually visit uh websites than humans.

**15:48** · Mhm.

**15:48** · I mean that's that's I'm 100% certain of that. It's not even you know I saw that Gartner had a research report that said 20% of commerce will on the internet by 2030 will be agents. meaning like agents are buying things.

**16:06** · Um, you know that the the tail or what's the the how do I say this? Basically where it's all where it's going is agents doing more and more things. So obviously yeah there's just there's going to be way more agents than humans. Therefore there's going to be way more consumption of agents of products.

**16:23** · Yeah. And it's like the multiplier effect too, right? Because you have people running multiple open claws or multiple agents. Exactly.

**16:29** · On behalf of one person and who was it? There was a report saying I don't know if they were serious but they're saying yeah we should put a tax on a we should put a tax on agents right because it's like yeah it's making us more productive there's a whole think about human beings right like if you have a if you if you're running a company and you want to hire someone you have to pay payroll tax on that person right so of course then you know governments

**16:57** · are going to be like well it's kind of like you're hiring a person Therefore, there should be some taxes that, you know, agents have to pay.

**17:06** · There there's an arbitrage opportunity right there, right? Like you you as a single human now have an army of agents working for you on your behalf. They're a multiplier effect of what your income is or whatever it is that you're doing more productive.

**17:18** · Yeah. Where's like, you know, you're making more money. Yeah. I wouldn't be surprised at some point we have some agent tax. It's like on on your taxes like list out the agents you have. But um but anyways, uh back to kind of talking about the future of web. Yeah.

**17:31** · Like we're also seeing right now um more websites being built to be agent friendly, right? Firecraw fire uh cloud for came out with their um endpoint to be able to crawl websites to give access to agents to be able to get the data they need. And you know we actually had our website built in web flow. Then we migrated to framework and now we fully built in custom code. Why? Because we wanted to be able to use the agent as our CMS.

**17:58** · So use cloud code to directly update our CMS and the act ability to give access to other tools to like quickly ship changes, run tests, give access to our agents and MCPS which is you can now kind of do with web phone framework but it's not as open as you want it to be essentially.

**18:16** · So makes sense.

**18:17** · Yeah, that's kind of the the the thought process behind it. Let's go back. Okay, nice. So yeah, we're getting a much nicer refined design here. Um, and then if we wanted to, we can go back and like maybe find more components to drop. So, um, let's look at like maybe So, one of the things I really liked about your website, the Humble Litics website, is like the animations were really good.

**18:39** · Yeah.

**18:40** · How do you think about like if we wanted to like update the designs here to be a little more animated, how would we do that?

**18:48** · Yeah.

**18:48** · So, I So, right now we're doing right now. So, I basically went into here. Um, so this one has a very subtle animation. I copied this component and I dropped it back into terminal in cloud code. I said, "Hey, add the section and then add a subtle animation." And the goal like I always say like you don't want to overanimate things. It's interesting to see how like agents respond to constraints and guard rails, especially around like, hey, make subtle changes, subtle animation, subtle design refinements.

**19:17** · I'm actually very intentional with that word when I use it with agents because like if you say improve the design, it's so broad and generic. Whereas you say, "Hey, work on refining the design. Make sure you have consistent layouts and themes and keep it subtle enough to make sure there's like cohesiveness across the entire page." I find that prompt works a lot better than just saying improve the design.

**19:37** · Keep it subtle, stupid.

**19:39** · Yeah, keep it subtle. Exactly. Exactly.

**19:41** · There you go. Um, so you know, while that's happening, I'll say when you're done, make the changes in the code and push it and tell me the URL for it and add a section on the homepage to the lead magnet. Cool. We already have the site right now and um, we're going to now add that lead magnet section.

### Deploying Landing Page and Adding HumbleLytics Analytics

**20:08** · So, we were actually earlier today with Jordan and I in the live stream, we're building out the home section, the hero section, and we started working on the steps below it.

**20:15** · But now what we're going to do is build a lead magnet page using what we just covered in paper and the designs. Um, and then yeah, we're going to push it live to the website and then run some get some analytics in there and run some experiments to see what drives more conversions.

**20:29** · Cool.

**20:29** · Cool.

**20:30** · Yeah.

**20:30** · And then like for the audience, like keep in mind like we're doing this really really quickly. We're speed running through this, you know. Um, obviously like if you look at this design, it's a lot more refined than what it would be. Typically, I would spend a couple hours going through this, going through specifically like different illustrations or blocks or sections. I just want to cover like the key principles of how I approach it and then you can come back and like use these different components to refine each individual section. Any questions, thoughts?

**20:56** · Yeah, I think uh I was just just thinking about this like we we all have these this you know expectations that you're going to like one prompt something, two prompt something, three prompt. So I'm happy you said that it's probably going to take a couple hours if you really do want to get it dialed.

**21:12** · So I I just I don't want people to go through this whole process and be like well when air did it look so so much better. Well, air amir first of all you had the library so that was helping but also you know it takes time right it takes a lot of time like we yeah we I mean it doesn't take a lot of time if you think about it just takes like imag you know if air from 2017 saw this

**21:39** · oh like and heard that and heard that you said it took a lot of time you'd be like what is air on no yeah no but it takes time it takes some amount of It takes time, taste, and skill to know what you got to do and how to do it, right? It's like we've we made it so easy to achieve the tasks. How do you give the agents the right direction and approach to say here's how you need to do it?

**22:03** · The taste taste is what we know we've been talking about a lot.

**22:06** · Yeah.

**22:07** · And and direction, right? Like this particular component needs subtle animation. Here's a reference of that.

**22:14** · Exactly. Exactly. Like I built this component from scratch. not from scratch. Off an existing component that was I think let's actually find it.

**22:24** · So you found a component here.

**22:26** · Exactly.

**22:26** · So I found a component here.

**22:28** · We're going to find it cuz I know I'll tell you where it is. So like this is for example right here. Okay. So we had this component and this is it right here. I I ported this one over but I said add a sol animation to switch through it for example or or this analytics query right here.

**22:44** · So this one is this one right now that specific component I think it was it was one of these one of these cards essentially and yeah I took it and I said hey based on this component oh right here this one it was this one and I turned it into this which is you know I think it looks great.

**23:09** · Yeah.

**23:09** · Yeah.

**23:09** · Yeah.

**23:09** · So cool. So, we we've we've built out the design of the guide page in here. Um, and now we're going to see if it's live on the website. So, let's push this and then we're going to go to guide. Boom. So, now we have it. We have the sections here. Okay. So, now let's get some analytics in here to see how many people actually could sign up for this lead magnet.

**23:33** · So, I just want to say one thing. This lead magnet looks gorgeous. Like, think about this lead magnet. looks better than 99.99999% of lead magnets that exist. Right? So people listening to this like this is uh think think about you know don't just create one lead magnet, right? Like every few weeks create new lead magnets, optimize your lead magnets and you're going to be able to outperform because you're going to know how to do and create gorgeous looking lead magnets.

**24:04** · Exactly.

**24:04** · And we did we did this in like 30 minutes. Again, like you get the right components, the right direction. You can do some research on the best ones, port them over as reference styles, and then make that refinement. So, right now, while you were going through it, I found this kind of decent component. I was like, why don't we just try this design instead and add it? So, let's see what happens.

**24:21** · Yeah.

**24:22** · Okay, cool. It's going to adopt it and it's going to have that split split layout. All right, so we've got this lead magnet. We'll wait while it's refining the design. We're going to come back and essentially get some analytics installed and look at some click tracking form submissions and run some experiments to see if I were to change this headline headline for example um

**24:41** · what would this look like and you know what would increase more form submissions for our leads and we we use this approach at uh humble we just started actually where we built like an autonomous CRO agent where we have direct skills and MCPs connected to a cloud so we directly connect to our track our analytics and experimentation tool, our marketing site, which is why we ported over to custom code. We wouldn't have been able to do this through Webflow and then we have Google Ads.

**25:06** · The idea is how can we spin up multiple subpages that are personalized campaigns like personalized campaign landing pages based on the campaigns we have. So, like if I'm running a a a painoint campaign on Google Ads and I have five adsets, I want each one to have its own personalized landing page and I want to AB test each individual landing page to see what headline resonates the most or what layout for example. Um, you're able to do this with the custom code site really quickly with cloud code.

**25:35** · With framer or web flow, you have to create the pages, create the sections, come back and update it. You know what I mean? So that's kind of the whole thesis we're talking about earlier where it's like the feature of websites is custom code and the agent is the CMS and then you have it running and you can even set up like um uh so what we do is we have like a cron job now directly in cloud code because they support automated tasks to say every week go into um like run this specific task. So what we have is Google ads directly connect to cloud through the API.

**26:01** · We have three cloud scales a paid media manager that pulls data from meta and Google. We have a CRO optimizer that runs AB tests and then we have a funnel report that just gives us a report of like here's how many users you had signed up. It connects to stripe chart mobile all the different tools that we have and then we have humbalytics that essentially hits our endpoint to give you recommendations actually uses fire crawl to scrape the pages and then um uh

**26:27** · helps you kind of say okay here's what you need to optimize for helps you run the experiment all through cloud and then it manages the manages the like the results for you. I mean that is just so cool that we live in a world where you can do that.

**26:41** · I know. Yeah. Yeah. And the best part is you can actually use this with idea browser to pull all that context and save it as a file back into idea browser.

**26:50** · Jordan and I were talking about this like yo we can do this now. Like imagine you do a weekly report. You pull all the data you add it into idea browser and now Idea browser has contest of like how growth has been over time which is which is sort of the unlock right.

**27:05** · Yeah. Yeah.

**27:06** · You know, if you have that, you're just going to get better results. You're going to compound and that's like how you can compete in Right.

**27:15** · Yeah.

**27:15** · Exactly. Um, so we just added the the component to the like we installed this new component, but I realized the mistake we made was we got rid of the form, so we're adding it back in. But yeah, like the to your point, uh, we actually before this, we were tracking all the context directly in Obsidian as well. So we have a master like performance log.

**27:36** · Yeah.

**27:36** · It says like here's how this AB tested.

**27:38** · Here's how much money it made. Here's what you need to improve on. And we just come back to this context. So we have this all set up now. We have this landing page. And let's go back to the homepage and maybe run an an experiment on this homepage to see if we can increase clickthrough rates. So what I'll do is I'll spin up cloud again. And then we're going to go into so with Humbolytics you can just go directly to the API create an API key get your property details and instructions to hit the cloud.

**28:05** · Uh but what it you know you get the basic analytics you would typically see where people are visiting from traffic you know the channels everything you want if you're looking to like run paid ad campaigns you get full attribution directly in here so you can see exactly what channels are making you money. You can have heat maps to see scroll depth, what people are clicking on, the full experience. You can even create funnels. So, for example, if you want to go like, you know, from page to guide, you can even run it. It'll show you what people went through his steps.

**28:35** · Um, and then you can run AB experiments.

**28:37** · So, we have zero right now. We're going to use Claude to actually run an experiment. So, we're just going to copy this. just gonna and then we're going to have a we have a dedicated skill for this but I thought just to show people the steps. So using this approach create an AB experiment no code type for the headline suggest what the headline so you have a skill for this?

### Running A/B Experiment on the Headline

**29:06** · We do.

**29:06** · Yeah.

**29:07** · Yeah.

**29:07** · I I'll share the link afterwards that people can use where essentially we'll help you get set up with like comolytics, run experiments, get recommendations. But we have endpoints right now that you can hit to say okay like tell your agent or cloud code hit the specific endpoint the recommendations endpoint and it'll actually scrape your site pull traffic insights pull all the existing data you have in homalytics and even idea browser and then give you a very detailed report on here's what you should like focus on for your landing page or what you should test.

**29:35** · Yeah.

**29:36** · Nice. So it's pulling insights based on analytics. We have a 40% average scroll 25% bounce rate. Here's the page content. Here's what your control should be and then here's what you should be what should be the variant. Okay, cool. We should now go back into experiments.

**29:51** · We now have an AB test running directly through here, which is crazy. It's actually insane. And we did this without even deploying change cuz our script dynamically updates the content on the site without you having to go to your developers and say, "Hey, like can you can you create this new page or push it for us?" So, this is what we had. If I refresh this maybe a couple times because it's like it's distributing traffic. Let's see.

**30:15** · Right.

**30:16** · There we go.

**30:18** · Every lost deal started with an objection your rep wasn't ready for.

**30:22** · Honestly, not bad.

**30:23** · Pretty fire.

**30:24** · Yeah. But here's the cool thing. We just launched an experiment.

**30:27** · Yeah.

**30:28** · And it automatically updated the page without pushing code. And now you're tracking to see how this headline will actually impact conversions. Yeah. So if I click this for example, you know, and then let's say we go back to control. So this is right now showing. Okay, now we're on control and we go back in here. We can see exactly how conversion is doing.

**30:50** · So it's still pretty early. So it's going to like not have any good data to show, but it's showing you even what people are clicking on directly and telling you how the test is doing.

**30:58** · Insane.

**30:59** · Yeah.

**30:59** · Insane.

**31:00** · It's also insane that like I don't know anyone who's doing this.

**31:04** · Yeah, I know. Yeah. Yeah. We we I think this this stack right here um what I showed between going from idea to refining in paper then analyzing optimizing for this like if you're a go to market person or marketing person and use a stack you're unstoppable. Yeah. So we're we're we're doing this at scale now. We're running a bunch of paid meta ads Google ads directly connected pulling all the context creating personalized pages and seeing like what's what's making money.

**31:30** · I mean there's also an opportunity to actually take this stack and sell this as a service right like how many businesses you know would would pay 5 10 15 20 grand a month if you can actually be doing this for them like probably a lot. Yeah, we so we actually have a couple customers that work with us and say, "Hey, like we'll pay you like 5k, 10k a month. Can you just run right?

**31:55** · Can you just use your software and then run it for us?" Yeah. Yeah. Yeah. Because like you can connect meta ads directly in here, Google ads, get full revenue attribution and then they say, "Hey, like just tell us like where where our top funnel spend should be." And so it's almost like we're seeing this now too like managed service.

**32:10** · Yeah, makes sense.

**32:11** · Yeah.

**32:11** · Yeah. So yeah, we've I feel like we've covered a lot, right? We went from an idea that we had in idea browser to um to like now having relevant context.

**32:22** · So we can even come back and say like in the terminal say you know using idea browser MCP add this info uh to the context. So we can come back and actually add this as a file right. Um so we went from idea to designing something in paper to building a new landing page to then having analytics and experiments behind it.

**32:43** · Crazy.

### The Arbitrage Opportunity and Closing Thoughts

**32:44** · What a time to be alive, my friend.

**32:45** · What a time to be alive. All right. Was that Was that saucy?

**32:47** · That was saucy, man. I like I would be real with you. Like if this I've I've never seen anyone do this this fast with this stack.

**32:59** · Yeah.

**32:59** · Yeah. Yeah. If it it sometimes I yearn to be an employee again and like go to micro marketing so I can just take this and just blow people's mind away because it's like it's so much fun. Like I wish we had a million dollar monthly spend so I can just dabble with these tools and just show them what's possible.

**33:17** · Yeah. What's going through my mind is like there's a lot of arbitrage.

**33:20** · Insane, right? Like if you if you can, you know, if you get have good ideas, if you get, you know, source of good ideas and you can AB test them and you can be creating beautiful websites, you know, lead magnets, that sort of thing. and you have access to 7 billion people who have, you know, internet connections and and their credit cards attached to it. Like there's arbitrage and I remember I remember when the Facebook ad platform first came out.

**33:51** · Oh yeah.

**33:51** · And you know the average click I think back then was 5 cents a click.

**33:58** · So meaning like you can create an ad and I was at the time working with these social gaming companies. So, I would say like, "Hey, you know, as an example, Farm Bill, I would say like, would you pay me $2 for every install I got for you?" And they'd be like, "Sure. This, you know, we monetize so much better than that." And I was just using Facebook ads cuz I was paying 5 cents a click. And there was this moment of opportunity basically where you could do really well um because of this ad platform and and and how cheap it is.

**34:26** · Now, fast forward to today, I don't even know what a CPC is. On average, it's probably $2 or something like that. Yeah, it's $23.

**34:34** · $23, right? So, it's it's, you know, so much more expensive and it's and it's just because people didn't know back then, right? And it's sort of the same thing with this with this sort of stuff. It's like, you know, 99.999% of people don't know that this stack exists.

**34:48** · Yeah.

**34:49** · And there's an opportunity to create offers and arbitrage right now.

**34:54** · The right tooling, the right approach.

**34:55** · You have a terminal with a million context tokens. There's the opportunities are endless.

**35:00** · Yeah. you know, so I appreciate you sharing.

**35:03** · Yeah.

**35:04** · Um and uh I'll include the link that for that skill in the show notes in the description for sure.

**35:11** · I'll include links on where to follow Amir uh on X and and other places.

**35:16** · And uh stay saucy, my friend.

**35:18** · Thank you for having me, man. Good to see you.

**35:20** · Good to see you. All right.