---
layout: layouts/post.njk
title: >
      221 JSJ Visual Studio Code with Wade Anderson Live From Microsoft Build 2016
date: 2016-07-20 07:00:17
episode_number: 221
duration: 36:56
audio_url: https://media.devchat.tv/js-jabber/JSJ221BUILDWadeAnderson.mp3
podcast: js-jabber
tags: 
  - js_jabber
  - podcast
---

This episode was recorded live from The [Microsoft Build Conference](https://build.microsoft.com/) 2016. In this episode we chatted with Wade Anderson of Microsoft about [Visual Studio Code](https://code.visualstudio.com/). You can follow him on [Twitter](https://twitter.com/waderyan_), or check out what he’s done over on [GitHub](https://github.com/waderyan).&nbsp;Picks
- [Parks and Recreation](http://www.imdb.com/title/tt1266020/) (Wade)
- [VidAngel](https://www.vidangel.com/browse) (Wade)
&nbsp;A special thanks again goes out to [Richard Campbell](https://twitter.com/richcampbell) and [Carl Franklin](https://twitter.com/carlfranklin) from [.NETRocks](https://www.dotnetrocks.com/) for putting this podcast series together! You rock!

### Transcript

**_[This episode is sponsored by Front End Masters. They have a terrific lineup of live courses you can attend either online or in person. They also have a terrific backlog of courses you can watch including JavaScript the Good Parts, Build Web Applications with Node.js, AngularJS In-Depth, and Advanced JavaScript. You can go check them out at FrontEndMasters.com.]_**

**_[This episode is sponsored by Hired.com. Every week on Hired, they run an auction where over a thousand tech companies in San Francisco, New York, and L.A. bid on JavaScript developers, providing them with salary and equity upfront. The average JavaScript developer gets an average of 5 to 15 introductory offers and an average salary offer of $130,000 a year. Users can either accept an offer and go right into interviewing with the company or deny them without any continuing obligations. It’s totally free for users. And when you’re hired, they also give you a $1,000 bonus as a thank you for using them. But if you use the JavaScript Jabber link, you’ll get a $2,000 bonus instead. Finally, if you’re not looking for a job and know someone who is, you can refer them to Hired and get a $1,337 bonus if they accept a job. Go sign up at Hired.com/JavaScriptJabber.]_**

**_[Let's face it. Bookkeeping is hard and it's not really what you're good at anyway. Bench.co is the online bookkeeping service that pairs you with a team of dedicated bookkeepers who use simple, elegant software to do your bookkeeping for you. Check it out at Bench.co/JavaScriptJabber for 20% off today. They focus on what matters most and that's why they're there. Once again that's Bench.co/JavaScriptJabber.]_**

**_[This episode is sponsored by Rangle.io. Rangle have been working with Angular 2 for a long time, and they are now putting together an 8-hour, 2-day course designed to help Angular developers, learn how to write apps in Angular 2. If you're looking to level-up your JavaScript and Angular 2 skills, go to Rangle.io/Training and click on the link for Angular 2 Training. If you're looking for other training in React or JavaScript, they also have that available at Rangle.io/Training.]_**

**CHUCK:&nbsp;** We're still here at Build Conference for JavaScript Jabber. AJ is still here.

**AJ:&nbsp;** AJ still here.

**CHUCK:&nbsp;** And we are talking to - I already forgot your name.

**WADE:&nbsp;** Wade.

**CHUCK:&nbsp;** We're talking to Wade about VS Code. Do you want to introduce yourself real quick, Wade?

**WADE:&nbsp;** Yeah, Wade Anderson. I worked as a PM on the Visual Studio Code team. I'm relatively new to the team. I started in December. I did the Visual Studio Code tips and tricks session here at Build yesterday.

**CHUCK:&nbsp;** That's interesting. We also made the Utah Connection which is a JavaScript Jabber thing since most of our hosts live in Utah. But yeah, anyway, so we had Erich Gamma and Chris Diaz on the show about, what? Eight weeks ago, when this comes out, something like that. They talk to us quite a bit about Visual Studio Code. They talk to us about Electron, and how it's used to build it. I'm kind of curious since you did the tips and tricks session. You know, maybe we can just start there. What kinds of things can you do with Visual Studio Code that people aren't really thinking about?

**WADE:&nbsp;** Visual Studio Code is a lightweight editor so we're in the same spaces like Sublime and Atom so --

**CHUCK:&nbsp;** Almost as good as Emacs.

**WADE:&nbsp;** Oh, almost as good as Emacs. We have a --

**CHUCK:&nbsp;** AJ is shaking his head. Some people use Vim. I don't know why, but they do. No, I'm just kidding.

**WADE:&nbsp;** So what we can do with Visual Studio Code that we believe is doing well against alternatives is you can have JavaScript IntelliSense which is really powerful, so we use the Salsa language service which the TypeScript folks here developed. You can get really good help while you're developing. IntelliSense is your control space, and you get a tip on what are the different methods for this object, and you can see what the document is really quickly, right there in the editor.

So this is a powerful feature that you and I use often but not as often in text editors that are lightweight. We think a cross between this lightweight editors with these powerful IDE features makes Visual Studio Code a really good editor for JavaScript developers.

**AJ:&nbsp;** And where does it run?

**WADE:&nbsp;** Where does the- like the Java operating systems?

**AJ:&nbsp;** Yes.

**WADE:&nbsp;** All of them. Yeah, it runs on Mac, Linux and Windows.

**AJ:&nbsp;** Are you even Microsoft anymore?

**WADE:&nbsp;** I'm not sure.

[Laughter]

**WADE:&nbsp;** Almost everyone on the Visual Studio Code team uses a Mac, exclusively for their development. We have a couple of Linux guys, and one or two people might have also use Windows. But we really try to dog feed the product, and feel what it's like to work on Mac, and Linux.

**AJ:&nbsp;** When the anniversary come, update comes out, are people going to start using Windows, too?

**WADE:&nbsp;** I think, our team will stick to Mac and Linux for the dog feeding reasons.

[Laughter]

**AJ:&nbsp;** So it's really a product that's meant for developer outreach, it sounds like. I mean, like that's really the purpose is to reach a broader community?

**WADE:&nbsp;** Yeah, I think so. The vision with it is we want to- I mean, here at Build Conference, we do a great job catering to the Windows developer. We have a lot of loyal fans here. But historically Microsoft hasn't done a great job getting on these platforms. So the aim with Visual Studio Code is let's get out, let's learn from them, let's provide a good tool, let's work with the community, let's see what those needs are, and that can lead to other product offerings that Microsoft can bring to the Mac and Linux communities.

**AJ:&nbsp;** Yeah, that makes sense. It's been really interesting over the last few years. I mean, we've had Scott Hanselman on the various podcasts. You know, I've talked to several other people at different conferences about either they're working for Microsoft or they work in Microsoft technologies. It really has gone from people feeling like you either have to suffer through the Microsoft way or do it the right way to Microsoft really contributing to the wider programmer community, and providing some really great solutions.

It's funny because I talk to people and I'm like, "Yeah, they're not the evil empire, anymore," they kind of acting like they get it now. Especially with open sourcing as much as they have and things like that. They open source the .NET runtime. They have open source Shocker. We just talked [inaudible] a few minutes ago. I mean, there's just so much stuff out there. You know, they bought Xamarin, and they've just announced in the keynote that they've opened it up to different versions of Visual Studio. Basically, it's free if you get the community version of Visual Studio. You get all those Xamarin's stuff.

You know, just all of the stuff where it's like, "Look, we want you to get important stuff done, and here, we're going to give you some great tools to do it," and Visual Studio Code, especially in some of the circles that I move in with Angular and TypeScript has gotten some really, not just wider option but excited adoption because it provides so many nice things with the, you know, as you said the code completion in the Intellisense and some of the other things that are built into it.

Then, when we talk to Chris and Erich, they also talked about being able to add in your own syntax highlighting in Intellisense, and things like that, and extending Visual Studio Code beyond just a code editor that's convenient for the handful of languages that are kind of built into it.

**WADE:&nbsp;** Yeah. With Visual Studio Code, the core offering, you may or may not be aware of this, but we actually recently took C# out of the core. When you download the product, it no longer comes the C# support. You have to actually install that as an extension --

**AJ:&nbsp;** And you kept your jobs? That's awesome.

**WADE:&nbsp;** Yeah, we actually thought it was kind of a radical move because here we are with Microsoft developer tool and we took C#. So our first class citizen with the initial download is JavaScript, and so you download it, we have a great vertical experience with JavaScript. But the idea is that any of these other verticals with Go or C# or Ruby or Python, you install an extension, and you bring that into the editor.

We think that it works great because it keeps the product really lightweight, and you only bring in the tools you need. We've been happy with the- extensions is three, four, five months old now, and has a really good support from the community, and some internal Microsoft teams have been jumping on too.

**AJ:&nbsp;** So one other thing. We're here with actually two podcast. We're here with JavaScript Jabber. We're also here with iPhreaks, which is an iOS development podcast. I'm curious since it runs on Mac and has some of these capabilities. Are there going to be extensions for Objective-C and for Swift, and maybe even some tie-ins so that you can tell it to build and run and it'll do what Xcode does, and compile, and then pull up a, what do you call it, an emulator?

**WADE:&nbsp;** Yeah. This would be really neat. There are mobile platforms we're pursuing so things like React Native, and Ionic Cordova, we have internal teams at Microsoft that have built extensions for that. The React Native extension launched a few weeks ago, and has had some good success so far.

Specifically, in the Apple languages with Swift and Objective-C, we haven't been driving that internally as a Visual Studio Code team, and I haven't seen anything in the community yet for that. But it would be an interesting thing for us to look into. It would be a little bit outside of our... so we really want to hit this JavaScript well which is where the React Native, Ionic is fitting in well with what we're doing. But, in the future, this could be an offering we look into.

**AJ:&nbsp;** Yeah, looks like you also have a partnership with Telerik, or Microsoft does. So I'm also curious if you're going to do anything with NativeScript.

**WADE:&nbsp;** Yeah, actually NativeScript launched an extension just recently. I saw they were doing a mini-theatre here. I don't know too much about it, actually, but I've been hearing some good positive vibes about it. So, I'm curious to see how well it does in the next coming weeks and if people are installing and having good experiences with it.

**AJ:&nbsp;** So I'm going to go back to your session a little bit, what's kind of the least known tip or trick that you shared that will give people the biggest bang for their buck if they're using Visual Studio Code?

**WADE:&nbsp;** I don't know the least known, but what I got across to my tuck is that the fundamental tip that I think, can bring you up to speed with Visual Studio Code, and you're coming from Sublime or Atom, this is going to be familiar. But just opening the command palette, and you have access to all of the commands, and then you can learn the key bindings really well that way, because all the key bindings are right there on the right.

So if anyone's new to Visual Studio Code, and we're surprised when we look at the telemetry how rarely people are discovering the command palette. Just hit F1 then you have access to all of them. As I was getting ready for the tips and tricks session, I could learn the key bindings really quickly because I could see all the commands. So the F1 key stroke which will open the command palette, and then secondly I'm moving to just wherever you are at, type 'CTRL + Space' will do a trigger suggest, which essentially invokes Intellisense. I was surprised in preparing the tips and tricks session how often I was getting help from the editor like JSON files. So if you knew package.json. You’ll get Intellisense in that file.

We’re not created making that visible right now. So you do have to just do CTRL + Space, which I guess is fine if you build one in your space all the time. But those would be the two. The F1 deploy the command palette, and then, the second one is to trigger a suggest with CTRL + Space.

**AJ:&nbsp;** Right. One other thing that I'm curious about, I don't know if we asked Chris or Erich this but, why do Visual Studio Code- I mean, you know Microsoft has Visual Studio. They have various versions of it. Visual Studio Code is kind of a completely different thing, and they're giving it away for free. You know, it's not a selling product. In fact, if anything, it might actually cannibalize some sales of Visual Studio which costs a lot, and it's for Open Source communities where Microsoft has not a lot of reach, and I can kind of see that. But from kind of a business or strategic standpoint, I don't completely understand why they're going this way.

**WADE:&nbsp;** Yeah, I'm not an expert on the strategy, but from what I understand, we talked about this a little bit, a few questions earlier. It can be a loss leader for us and that it helps us engage with communities and a group of customers that we haven't engaged with very well. As we think as product developers, and we try to come up with ideas for products, since it's just so important to get that out of the office and meet the customer where they're at. That's what we learn in startup world - lean startup and things.

So with the Visual Studio Code team, that's what we're doing with the Mac and Linux developers, we're getting out a quote-unquote getting-out-of-the-office. We're engaging with them. We're working with them. I think, the higher ups, the vision for Visual Studio Code for them is well, this could lead to some innovation, some new products that we could develop that might not be obvious until we get out there and engage with customers. Those could end up being very profitable for Microsoft. Imagine, we could come up with something that would help Mac and Linux developers get on [inaudible] at a much higher rate. That would be very profitable for Microsoft. I think would make it so we could say Visual Studio Code accomplished its mission from a business perspective.

**AJ:&nbsp;** That makes sense.

**WADE:&nbsp;** As a team member on the team, I like the vision of that because it seems like a win. I mean, we're engaging with the customer, and not a way to try to trick them into paying. We're just trying to understand their needs so we can really bring solutions that help them.

**AJ:&nbsp;** One other thing that I'm kind of curious about is you see things like Xamarin. Some of these other things that have been announced. A lot of the stuff that showed off with Cortana yesterday. Are you planning on integrating any of those things?

**WADE:&nbsp;** With our extensibility story, that's kind of the avenue we would integrate those things. We're excited to see where that goes, and we have internal Microsoft, even yesterday after my talk, one of the PM's on the Xamarin team came up and introduced herself and we scheduled the time that we could meet up.

Yeah. I would think that we could start to see some integrations with those. But probably always. I could say this fairly confidently, I would say always as in the extensibility story. So we have this vision for our product that it's going to remain lightweight and it's going to be customizable. So if something like Cortana makes sense for a developer, then an extension can be created and if people want it, they can bring it into the tool. But I think that what my vision for the product is and what our team's vision is that we wouldn't ever start shipping Visual Studio Code that's bloated and slow. That would go away from what our vision is for.

**AJ:&nbsp;** I went to the booth over there yesterday, and they were showing me some of the debugging, and it seems like no debugging is baked in. Do you want to talk a little bit about that?

**WADE:&nbsp;** Yes, that kind of goes with as when you demo the product, we have a great JavaScript experience in the end. That includes the Intellisense. That's includes the debugging. Any other editing snippets, and things are all built in right out of the box so that we can pull in these other tools. Like there's a Ruby debugger, a Python debugger, that you can pull into the tool.

To address your question, I'm talking about the Node debugger, we do want to make that an awesome experience. We want Visual Studio Code to be the tool for Node developers that they go to on any platform. That's our vision for it while remaining lightweight.

**AJ:&nbsp;** What's the experience like with the Node debugger as opposed to Emacs?

[Laughter]

**AJ:&nbsp;** I guess, you don't really have a debugger plug it in Emacs.

**WADE:&nbsp;** Not really. No.

**AJ:&nbsp;** Okay.

**WADE:&nbsp;** Visual Studio Code has a loosely coupled relationship with other bashed tools, essentially, or other tools that you can run through the terminal. With the Node debugger, we essentially throw an interface on to the debugging protocol so you can easily set breakpoints from within the editor and then stop those breakpoints and step through.

It adds a UI layer that developers are comfortable with, and that's intuitive. I would say, like I use the Node debugger too often because I write bugs in my code. But I think that we've done a good job hitting just exactly what we need out of a debugger. I mean, we don't have some of the advanced debugging features that go in back in time and things. We can't quite do that yet in the debugger. So it kind of hit this like 80-20 rule pretty well, I think. It gives you what you need for the debugger.

But I think over time, we'll see this expand. Even some of the guys we've talked to some internal partners that are interested in seeing if there's some diagnostics we can do, things to dive in to the memory usage, from the debugger screen. So we're looking into those, and those will probably be available as extensions you would add-on to the core debugger.

**AJ:&nbsp;** I liked what they were showing me over there was pretty simple, like you click on something, you can see the variables that it contained. It wasn't very cluttered. It was actually more attractive to me because it didn't seem like it was doing too much like you're saying.

**WADE:&nbsp;** Yeah, since we've looked at the Node development community, we did a lot of customer studies, and work with customers, and we found debugging was a large pain. Almost everyone was just doing a simple 'console.log' and just log the other variables. I know, that was the approach I had taken for years.

I mean, to say that, one nice thing about that is it's a good cross language debugger. You can do that in every language so that's why people get comfortable with it. But anyone that uses the debugger in Visual Studio Code could say, it's definitely a step-up from there, and it's really, really useful, and easy to configure. Whenever I used debuggers, even when I use them with IDEs occasionally, it takes really some painful steps to get set up. But I found the Node debugger Visual Studio Code just really easy to get going.

**AJ:&nbsp;** What other features are there in Visual Studio Code that either out or coming out soon that people should know about?

**WADE:&nbsp;** There's the git integration. We have good support for git, and a lot of our users that are relatively new to coding really like that because git sometimes can be a hard tool to master, initially. Our new developers like how the git integration is very intuitive, you make a change in your file that the git icon will show a badge how many files have been changed, you go over there you can quickly see the changes, and then you can stage it, do a commit and push all right there in the editor.

For someone like me or other developers that have more experience with git, I was nervous about that when I first looking at it because I like to see what's going on under the hood. While you also, you can open up an output window and see what git commands were running, which I like. It actually helps me learn a little bit more about how git is working. So that's kind of the philosophy you'll take with Visual Studio Code. We want to add these features, but still play really nice with the terminal.

So the git integration, we talked about Intellisense and debugging, then extensions. Those are probably our four big, I would say, value props or features with Visual Studio Code. Then extensions kind of opens up a whole world of different things that we could do.

What we've been really focused on lately, and where I think you'll see our product go in the next three to six months is where want to make the performance better. We want a faster editor. We want something that performs really well, and has very little bugs. So we've been really focused on that, and in just making a better overall user-experience.

So I talked about even the command pallet is and always very used, or some of these features that we like a lot, but we don't see how usage for the users, our hypotheses are that our users are not discovering them. So even extensions, which is all over our website, and seems like such feature people should be aware of, don't see as much usage as you would expect. Over the next few months, I think, you'll see some of those features more discoverable in the product. So we may, on the far left, our activity bar, we may make maybe, a settings icon or something so people are aware of how to get to settings and the key bindings and to really make Visual Studio Code their editor. That's what we want to trying to do for people.

**AJ:&nbsp;** I'm playing around with it right now.

**WADE:&nbsp;** Oh, good!

**CHUCK:&nbsp;** I think, we talk about installation on the other episode, but I think, for the most part, it's pretty straightforward for Mac and Windows. You know, you have an executable and installs it, or you have on Mac, it's either a '.app' that you download, or a '.damage'. I call it damage file - DMG file - that you pull down and then, it tells you to copy it over or douse some insulation.

But on Linux, it's a different story. You know, I've used Ubuntu, and Red Hat, and SUSE Linux with GUIs which I'm assuming you kind of have to have for VS Code, so with those, I mean, they all have different installer formats, right? You've got RPMs. You've got one of the Debian ones, I forget.

**WADE:&nbsp;** Deb.

**CHUCK:&nbsp;**.deb, yeah. Then, the SUSE packages are something else. How do you manage that? Do you just pull it in from your package manager or do you actually have to download it and run it?

**WADE:&nbsp;** Yeah, just a month and a half or so ago, we hired a new engineer in Redmond that system Linux Pro, so he's been tackling this very specific thing for us. Right now, for the Insiders release, so we have the stable release, which is the obvious download when you get to the site. But if you go navigate to the download page, there's now two tabs. There's the stable release, and the Insiders.

On the Insiders now, you can actually download the .deb, or the .rpm. You can download for your specific Linux distro. That is only for the Insiders release just because it didn't make it out to our most recent stable iteration. But going forward, that's how it'll be. So we'll have Daniel, the engineer. He's done a lot of work to get us on the apt-get, and some of these other package managers to make it easy to get on to Linux to make the install experience better.

So Insiders right now, if people want to do that that can make it a better experience. Then, I think, probably by the next stable release, we'll have that available.

**AJ:&nbsp;** Very cool.

**WADE:&nbsp;** Talking about Insiders, though, we are going to a weekly release schedule for Insiders. You can get the latest bits, and we want to encourage people to get in. We'd like that early feedback. It's really helpful for us early on, and I think that people that are on Insiders channel are also really like to have the new features, and try them out early on.

**AJ:&nbsp;** Yeah, it sounds like what Chrome does with Chrome Canary where it's pretty stable, might have a few bugs, try out the new features. It has got nice stuff in it.

**WADE:&nbsp;** Yeah, Insiders still goes through it, through a test cycle for us. We don't ship it broken, at least, too often. We've made one that was little broken, but Insiders, like internally that's the release we're always using, and giving early feedback to the engineering team.

**AJ:&nbsp;** Yeah, but the nice thing is if you have some new or new-ish feature that hasn't come out in the stable version, yet. You know, a lot of times you get that nice tool that can short circuit some work for you.

**WADE:&nbsp;** Yeah, definitely.

**AJ:&nbsp;** So, is there some kind of extension store or something that you have to go at search GitHub?

**WADE:&nbsp;** Yeah, Marketplace.VisualStudio.com/VSCode is the extensions marketplace. It's the web app. They've done a lot of work there. Actually, personally, that's been my project is working with the Marketplace team, and making the experience better, so we've got a good search experience now, and you can see the most popular extensions recently added. Then, you can browse by languages, debuggers, linters, snippets, and themes. I think, over the next few months, we'll see more and more improvement there, as well.

**CHUCK:&nbsp;** So, what would you say are the main advantages over Sublime or Atom?

**WADE:&nbsp;** Sublime and Atom are excellent tools, and we're happy to be in the same space as them. Like myself, I use Sublime for years. I was really happy with a lot of things from it. I think, what users can find with Visual Studio Code, whether they're evaluating all three and deciding which one they want to use, or they're switching from one of the tools. Maybe there's a pain point with Sublime or with Atom.

Visual Studio Code consider the range of text editors and IDEs, and IDEs being one extreme text as being the other. We built Visual Studio Code to be far on the tech center to side, but still pull some of the best features from the IDE. So what you're going to get with Visual Studio Code is you're going to get this Intellisense experience. This contextware editing that's really powerful. You're not going to find that in Sublime, and I don't believe that Atom has support for that.

Although, it might be in the works for them. But where a leader in that space. I mean, we share the team members that work on those tools for Visual Studios are also working on for Visual Studio Code. So we believe we're going to be the leaders and continuing to have great contextware, hints for the developer that can make you a lot more productive.

Then, the debugging experience, we think is superior to the alternatives. If you want this lightweight text editor but you are missing some of these things from the IDE, Visual Studio Code can be a great tool for you. Then, some specifics, like we're very- we're an open source product, which is the same for Atom but different from Sublime, and we're very open about the roadmap and things that we're doing, which is the same for Atom but different from Sublime.

So Sublime users might find that refreshing to feel like the development team is communicating, and responsive to things so we have a small but a growing team, and there's definitely commitment behind Visual Studio Code. I think that users could find, when they're evaluating the three tools, they could find a good long term. We're going to be here for a long time with Visual Studio Code, and we want to make it a winner. So they could get onboard with a tool that will continue to improve, and it's moving at a fast pace, and has a big development ecosystem behind them, with the Visual Studios. I mean, we work in the same building. I saw the Visual Studio guys, and we really can use a lot of that mind share to build a better tool.

**CHUCK:&nbsp;** So inside of Microsoft, why is Visual Studio Code important, because everybody in Microsoft got a free license to Visual Studio?

**WADE:&nbsp;** Right, different developers have different personalities, right? Like me personally, I really like the lightweight text editor much better than the large IDE --

**AJ:&nbsp;** So, we all get to be people?

**WADE:&nbsp;** What?

**AJ:&nbsp;** We all get to be people, like programmers?

**WADE:&nbsp;** Yeah, we all got to be people. Within Microsoft, we do have a strong amount of developers in Microsoft that like Visual Studio Code. It's either they like the lightweightness or they like to develop on Mac and Linux. So Visual Studio Code is the great alternative.

Of course, we don't want to drive people away from Visual Studios. I mean, I've had so many conversations here at Build with Visual Studio users, "Why should I use Visual Studio Code?"

I said, "If you like Visual Studios, like Visual Studio is awesome. Stick with it and it's going to be a great tool," but Visual Studio Code just hits this niche and this for me personally, it's my code editor of choice because I like the lightweight of it. I like that it's not performance heavy on my machine. It's not taking up a lot of space, and it's very customizable. I can make it my editor. I really like that with Visual Studio Code.

**AJ:&nbsp;** You forgot to mention that it's built in JavaScript which is different from Sublime, but same as Atom.

**WADE:&nbsp;** Yeah, I could have said that. Yeah.

**AJ:&nbsp;** I've become a very JavaScript guy. I still can program in other languages. I still enjoy other languages, but JavaScript is where it's at. I mean, it's the biggest deal. You know, I could go in there and play around with Python, and actually to be honest, I'm probably not going to go around there and play with the JavaScript and Visual Studio Code that much. But I like that feeling of knowing that what I'm developing in is what it's developed in. So that if there is some problem, like I'm really familiar with how Node works, I could get in there and probably to fix a bug, if I needed to.

**WADE:&nbsp;** Yeah, it's cool. It's definitely a cool thing that your tool you are using is this same technology that you are using it for. One thing approach with our team is for the last couple of years that the product has been developed, we've been dog feeding it, so all the engineers have been working on the product. It's been their product that they've been using every single day --

**AJ:&nbsp;** To build the product?

**WADE:&nbsp;** To build the product, which is kind of cool. We're using it, writing tons of JavaScript, which makes it sort of like we feel good about this experience, and we love and that helps us with making products decisions because we are the products users in a lot of cases.

**CHUCK:&nbsp;** So, one thing that I've thought about, and got brought up at the UtahJS Conference last year is the idea of like not being so supportive to so many different genres of code, but like really focusing on one. I mean, I kind of feel like I'd be best if there was a JavaScript editor written in JavaScript, a Ruby editor written in Ruby, a Python editor written in Python, and I think it is Jaimens who works at PayPal. I think it was him that's got a presentation and he showed, it was kind of like a git diff, but it had a hook, where it went through... what's that? Inscripting? No, the other thing, that does the parsing, and all of that of JavaScript.

He was showing like this demo of doing diffs rather than using the normal diff tool that isn't JavaScript sensitive. He was doing diff so that it would actually know if a function have moved because it understood this is a JavaScript function, and knew have a variable name change. Basically, it could track refactoring and diff like that. Do you think that you'll continue to be really JavaScript-centric, and maybe dive into something like that? Or are you going to try to be agnostic and just have a focus on JavaScript?

**WADE:&nbsp;** I think, the vision for the product is it's going to be an awesome JavaScript tool. I think that we will continue to be JavaScript-centric. Now, we do that and not bring in some of these other languages? No, I think that some of the focus right now is where are these other under-served development groups on Mac and Linux. Are the Python- like we've had awesome community developer made this Python extension, it's just skyrocketed in popularity, as well as Go. The Go extension is also very popular.

I think as Visual Studio Code, we're going to be centered on JavaScript, but we want to continue to build it as a platform that these other languages can come into. That's the product vision. So maybe not as JavaScript-centric as what you're describing, but it's still the core of the product because we use JavaScript every day. We'll solve the JavaScript that we want to bring in these other languages to make a good experience for them, as well.

**AJ:&nbsp;** So just kind of a wrap up, if people want to go download Visual Studio Code and install it and try it out, where do they go, and where do they go for sort of tutorials for more information as well?

**WADE:&nbsp;** Yeah, it's extremely easy compared to the Visual Studios' install experience. It is fast as lightning to install Visual Studio Code. You go to Code.VisualStudio.com. You can also Google it, or Bing it. Visual Studio Code will be the top hit there.

In the download button, it's right there on the front of the page. You can click that download button. Depending on its operating system so whatever operating system on, it'll download the right packets for you. Then, you just open that zip file or whatever operating system you're on, and it'll be a quick install process. You can get up and going pretty quickly, and then, on our website which was again Code.VisualStudio.com, the slash docs, you can go to get help and to get to your wow experience with the product pretty quickly.

**CHUCK:&nbsp;** Awesome. Now there's one more concept to the show that we do, and since AJ and I are doing several interviews per day, we're not going to do it, but we have the concept of Picks if you listen to like the Twit.tv Shows, they do Picks. Effectively what it is, it is just whatever you're into at the moment. It could be a TV show. It could be a board game. It could be a particular coding tool. Just anything, you know, or JavaScript library, whatever you're into. Do you have one or two things you can share with us?

**WADE:&nbsp;** Yeah, there's- so outside of developer tools, are you saying anything --?

**CHUCK:&nbsp;** Anything. Developer tools or not developer tools, anything.

**WADE:&nbsp;** Yeah, I was telling [inaudible]. My wife and I have an eight month old so he's been going to bed earlier lately so we have been really into watching, catching up on some shows. We've been really into Parks and Rec, lately and VidAngel as well, which the Utah Connections VidAngel is a Utah company. So those have been of our Picks, I guess. That's been a lot of fun.

**CHUCK:&nbsp;** Good deal. Yeah, kids going to bed earlier. It's nice to get that one-on-one time.

**WADE:&nbsp;** Needs some leisure, relaxation badly.

**CHUCK:&nbsp;** All right, well, thank you, Wade, for coming and talking to us. Hopefully, some folks will go out and check out Visual Studio Code.

**WADE:&nbsp;** Yeah, thanks for having me.

**CHUCK:&nbsp;** I know a lot of happy users of Visual Studio Code so I highly recommend to people to go and check it out. One of the thing I want to do real quick is thank Richard Campbell and Carl Franklin for pulling this podcast thing together at Build, and Microsoft for helping us get out here and be involved.

**WADE:&nbsp;** Thank you. Thank you, Chuck and AJ.

**AJ:&nbsp;** Thanks for telling us about Visual Studio Code. Awesome!

**_[Bandwidth for this segment is provided by CacheFly, the world’s fastest CDN. Deliver your content fast with CacheFly. Visit CacheFly.com to learn more.]_**

**_[Do you wish you could be part of the discussion on JavaScript Jabber? Do you have a burning question for one of our guests? Now you can join the action at our membership forum. You can sign up at JavaScriptJabber.com/Jabber and there you can join discussions with the regular panelists and our guests.]_**


