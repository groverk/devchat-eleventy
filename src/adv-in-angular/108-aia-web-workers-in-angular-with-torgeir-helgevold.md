---
layout: layouts/post.njk
title: >
      108 AiA Web Workers in Angular with Torgeir Helgevold
date: 2016-09-01 06:00:54
episode_number: 108
duration: 37:42
audio_url: https://media.devchat.tv/adventures-in-angular/AiA108_Web_Workers_in_Angular_with_Torgeir_Helgevold.mp3
podcast: adv-in-angular
tags: 
  - adv_in_angular
  - podcast
---

1:50 - Introducing Torgeir Helgevold

- [Blog](http://www.syntaxsuccess.com/)
- [Github](https://github.com/thelgevold?tab=repositories)
- [Twitter](https://twitter.com/helgevold)
3:05 - Defining and using Web Worker8:55 - Web Worker and value communication between threads15:05 - Booting an app in Web Worker vs a browser20:15 - Web Worker and mobile browsers23:55 - Reality and perception of running apps on mobile devices29:00 - Multi-threading and Web Workers **Picks:** [Angular NgModule Doc](https://angular.io/docs/ts/latest/guide/ngmodule.html) (John)[Tinker Crate](http://tinker.kiwicrate.com/) (John)[Angular 2 Router by Victor Savkin](https://leanpub.com/router) (Lukas)[“Out of the Tar Pit” by Ben Moseley and Peter Marks](http://shaffner.us/cs/papers/tarpit.pdf) (Lukas)[_Hardcore Henry_](http://www.imdb.com/title/tt3072482/) (Joe)[Vid Angel](https://www.vidangel.com/) (Joe)[Angular 2 Class](http://ftlauderdale.ng-learn.com) with John Papa and Dan Wahlin. Use code “AIA” for $200 off registration (Joe)[Angular 2 Gitter chat](https://gitter.im/angular/angular) (Tor)

### Transcript

Joe: Hello everybody, welcome to Episode 108, The Adventures in Angular Podcast. Today on our panel, we have Ward Bell.

Ward: Hello.

Joe: We’ve also got Stephen Fluin.

Stephen: Hey there.

Joe: John Papa.

John: Hello everyone.

Joe: Lucas Ruebbelke.

Lucas: Hello everyone.

Joe: I’m your host, Joe Eames.

As a special guest we have on our Podcast, I’m just going to butcher your name. I’m not even going to try. Tell us what your name is first.

Tor: My name is Torgier but most people call me Tor. It’s easier that way and easier to remember.

Ward: Yeah. We still want to hear it, Tor. Give it to us.

Tor: Yes, Torgier.

Joe: Your last name?

Tor: Helgevold.

Joe: Helgevold. That’s the up set.

Tor: That’s the mountain, right.

Ward: Is that Somalia?

Tor: It’s Norwegian.

Ward: Norwegian, oh, I was close.

Tor: Yup. You were close.

Joe:The topic today is Web Workers. Before we get into that, it’ll be good to get a little background on you.

Tor: Okay, yeah. My name is Tor. I currently work for ADP in New York City. The project that I'm working on is taking a large Angular 1.5 Application and migrated over to 2.0. That’s how I got started with Angular 2.0, I was preparing for that.

In addition to that, I do some work on the Angular IO side. I’m an author on the NG Docs Team. In addition to that, I do my own blog, I put some samples and some blog posts about Angular 2.0. It’s a light summary.

Joe: Awesome. We want to talk about web workers but we definitely need, it’s one of those topics that a lot of listeners, maybe they’ve heard of them, maybe they haven’t. I think we should definitely get a good introduction on what web workers are and why we’re even talking about them on an Angular show.

Tor: I started by doing a quick POC using Angular. One of the things that I like about Angular is that they have extracted framework from the one time environment. You can take the same code and run it in multiple environments. One of those environment is web workers. I do the POC on my blog were I hosted an app in a web worker frame just to see how it would work. I was very happy to see that you can pretty much write the code the way you normally would if you’re targeting a browser.

I don’t know if I have a good use case right now in my project for web worker. It’s nice to know because at least what it does is it adds, like JavaScript is single threaded. You can’t really have something, like run a heavy computation on that thread because your UI will be not responsive during that time. It’s an opportunity to bring multi-threading if you will to JavaScript where you can upload that computation to another thread in the browser that doesn’t hang the UI thread. You still want the user to be able to interact with your app.

Joe: Tor, could you give us just a kind of set ground rules for web workers. You can describe what they do. Can you describe some scenarios that you commonly use them for that if they weren’t there, what would happened?

Tor: Yes. If you want to run some computation that will take several seconds. What I do is I calculate in factorial in the background. That’s not going to take that long to run but if you have something a little bit longer running, let’s say you want to run some computation and get a result back, it would take maybe several seconds to get the result back. You could upload that, send that computation out to the web worker and have it tell you when it’s done. You could have your UI still be responsive.

Lucas: Let me ask you through a scenario out here. I frequently have a need to find a prime number over a hundred digits. Happens to me all time in typical programmer. I said every time you interview, you just have to solve that problem.

Joe: Yes, usually like a nice typical platforms that needs something like that. Is that an example of sometime when you might want a web worker?

Tor: Yeah. I think that’s a good example. There’s a YouTube video about that scenarios. I think that’s the most used example to showcase when you want web worker. Always something with prime error that prime numbers and long running computations. Yeah, I think that’s one example.

Ward: You said that the web worker when you have a single long running computation. If I have a lot of small computations that together added up into a long running computation. Maybe I have to calculate a couple thousand things and they’ll all separate. Is that a time when I would use a web worker?

Tor: The best use cause if you have something that would take a long time. If it doesn’t take a long time, you might as well—if it’s just a short running process, I'm not really sure that’s actually use case web workers shine.

Stephen: This is Stephen, all time in here. One of the classic examples of the web worker when they first came out from the Chrome team was in doing mapping things. They were actually rendering routes on a map, at the same time it’s still allowing you to move around and interact with the map. By doing all the routing and navigation, computation on that web worker, you could be doing incremental renders at the same time as not blocking the user interface at all.

John: I guess what I’m struggling with and I’ve read some of these as well. I use them in a few cases. I’m struggling with this, it sounds great to say, “Hey, I’ve got some long running process that I need to do something. I don’t want to block the UI i-thread. When does this really come to help me?” If I’ve got some data application and I’m entering an order entry. I’ve got to answer tons of orders. I’m on the phone with customer. I’m entering in, let’s say they’re buying a soda. I’m entering different rows and lots of data. Every time I enter data, it’s doing some calculation to recalculate shipping cost and inventory numbers, and things like that. I want to keep moving along. Is that a place where web worker would help me or is that still too simplistic?

Tor: It might help if you were doing something that was where your user experience was very for spreadsheet like. Single value changes as you place set off a cascade of calculations that were updating other place, other cells in the grid. That conceptually could happen with…

John: Like an inventory type app for example?

Tor: Exactly. I think that’s probably a place where there’s benefit.

John: Stephen had a couple other suggestions. I think one of the things that I’ve seen that can kill you a little bit is if you do some heavy duty JSON parsing.

Tor: Yup.

Ward: In the client, right?

John: On the client, right. Yes. You got a whole bunch of stuff bag and you didn’t want to talk about the UI thread while you’re turning that in the JavaScript object. You could form that out to JSON parsing.

Joe: Would this help things like breeze board? Like freezing the client, let’s say I got bags for massive object raft. I wanted to parse the heck out of it like something like a breeze, a data, a tool. Would using web worker helps that be more responsive?

Lucas: I could say that it’s something that we’re going to look into see what can be done there. There’s a fair amount of calculation involved in trying to find for a large cash to find out of what parts are really updated by a most recent download of information and stuff like that.

I think that there’s an opportunity to do it. Is Tor will know that tell us that one of the challenges is not just getting the work going over there but communicating values back and forth across the boundary between that other thread, the UI thread.

Tor, maybe you can tell us what’s involved. What has to cross that boundary? And what shape is that stuff? The crosses stuff.

Tor: Yes. The way I do in my POC is that Angular offers these message brokers where you initiate a channel between the main UI thread and the web worker thread. They can pass messages then to each other, back and forth. That’s how my simple app works. I basically pass in a number from the UI thread to the web workers saying “Okay, give me in factorial.” When it’s done calculating that, it’s back out to the result. They have an infrastructure and place for that to send messages back and forth.

Stephen: What I find even more impressive is the whole how the web worker code update things to UI. Web workers have access to the DOM directly but when you write the Angular code in the web worker, it basically is as if you’re writing a regular component. You write your views, you change tracking, whatever UIL you put on there. You do it as if you’re doing it the normal way. I find that’s a bit pretty interesting and pretty impressive.

Lucas: I think it’s important to, or really lays the ground work for. We often talked about technologies and how awesome these features are but taking a step back on why we all feel like web workers are such a great thing Angular Two, what those cases are? We listen a few of them now.

The interesting part is if you look at other technologies, let’s say iOS or mobile development or even Silver Light which I did six, seven years ago. Those kind of things or technologies all had a similar type of concept where you had to get off that UI thread to do something and then get back on it, otherwise you kill that user experience. In the web, it was always difficult to do that. Are web workers making it that easier with Angular Two? If so, how?

Tor: Like I said, I’m also kind of trying to find real scenarios where it actually will benefit me a lot. It does seem to usually come back to that, that whole try to off load and keep your thread responsive. I think that’s kind of generally in UI development, you usually come back to that. Let’s say in a multi-threaded environment where you have a WPF affl in a .net. You generally would do certain—the infrastructure is a little bit easier to work with and a little bit more stream line. It is the same concept. If you have to do something that will take a while to complete and if you want to prevent the main UI from being blocked. It comes back to that use case, in all cases.

Joe: It is the service message broker factory. Is that the prime candidate to use to implement this with Angular Two?

Tor: From what I can tell, that’s at least the samples I saw in the source code. There’s not a lot of documentation on this. I have to go digging in the Angular source.

Stephen: A word. Web workers in Angular are really designed to extract most of the work for you. If we think about this general idea about web workers, another thread you can run processes on. Historically, people would run in a very complex things through it. Doing huge calculations, mapping, kind of rippled calculations. One of the ideas with Angular Two is that we built it in the platform so you actually run the entirely of Angular on the web worker, off of the UI thread. What we do is we built it in so that you propagate only the DOM updates back to the main thread.

You make a few changes to your bootstrapping. You bootstrap just to render a part of Angular in the UI thread. You bootstrap a web worker is where you actually run your app module on the components. All their code runs automatically to the web worker which dramatically increases performance and it ensures that anything like changes detection, JavaScript garbage collection. None of that actually hits your UI thread.

Ward: If I understand you right, Stephen, if I were to look at Angular applications, I might find that only some small percentage what that thing is doing, what the app is doing is actually doing a rendering work. Sending commands that update the DOM.

Stephen: Correct.

Ward: But if I run the whole thing in my UI thread, then I’d be spending all of that time on the UI thread for about 10% worth of rendering work. Taking 10% out of the air.

Stephen: Correct. That’s the default mode that basically all web applications have been built in for the history of the web. It’s not well documented yet but we’re trying to make that easier.

Joe: Now, if I had something where I was feeling that it was slow, and it wasn’t the DOM rendering that was slow, but it was all the things that Angular was doing, that my app was doing in order to prepare to get down to that just small relatively, comparatively small DOM updating. There might be some advantage to shifting the application over to web worker.

Stephen: Yeah, exactly.

Joe: Tor, in your example, did you try just picking up an application and booting it in the web worker instead of booting it in the regular browser UI thread?

Tor: Yes, it took a very simple app. That’s the one I’m writing about in my blog post. This one is very simple. On the side, I added a few more features. Some buttons, some regular data binding. The environment feels very much like it would if I was doing it the normal way.

That’s one of the things I really like about Angular. They’ve added attractions to where you can pretty much run this on any kind of host as long as you can interpret and map it back to the native long time environment. You have played with server side running, some native strip.

Now web workers, I feel like this is just another test that that foundation is solid. You can pretty much run it on anything. It is relatively seamless too. There’s some ceremony around setting up these message brokers and all that. Maybe that’s a little heavy handed right now. At the same time, I feel like it’s pretty solid. It’s very nice to see how they’re able to abstract themselves from the native one time environment. Still keep the API very similar for the most part.

Joe: Like you, I was a little more surprised how much I was able to write my app, is the one sample I looked at, exactly as if it were going to be running in the browser. As long as I didn’t do certain things like talk to the DOM directly, get the element and start to update the element, I was good. I think that’s made possible by, I think what you’re describing is the rendering extraction, right?

Tor: Yes, it’s pretty cool. Like you guys, I don’t necessarily see an application for this right away in my business application, but it is still an interesting thing, at least interesting to explore and maybe we’ll find some use cases well this will actually make a huge difference. Right now, I don’t have one. I think I could perhaps find one.

I think maybe a question for Stephen. I was reading a little bit web workers in Angular Two, yesterday. How they use internally and someone was, I’m putting out a question if it would make any sense to try to run the digest cycle in a web worker?

Stephen: Yeah, generally I think that’s actually what ends up happening. All change detection runs in the web worker. I can send you an example, we can share this. It’s a little bit out of date. Ward and I have had time to document some of this stuff cause we got so many other cool exciting things going on.

You literally have your app component defined and running. It’s both any code that you write as well your change detection cycle fully in the web worker. All that gets propagated back are the DOM updates.

Joe: I think that’s very interesting. The one thing that may seem complicated, I can’t picture the whole solution. Right now, you format the digest cycle to something else. Your UI thread is then responsive still but then you trigger another digest cycle. You run the risk of getting back into the Angular one way where you have kind of these nested digest cycles where you really don’t have that same predictability.

Stephen: Because the rendering should not be destructive or should not modify the state at all. The state is all represented virtually within Angular. You’ve got a class, you’ve got a component that has state. It’s updated and that lives in the web worker threaded. Then Angular handles the message back that says “Hey, because the state of this change, I knew that I needed to add another div to this NG4.” Then all it says is “Hey, go add another div to NG4.”

Ward: Right. It’s not a digest cycle on the Angular one sense. It’s a change detection cycle. It’s all in a directional flow. This presumably is one of the advantages of that directional flow because the representation is not necessarily sitting there in the DOM itself but rather an attraction of the DOM, is that fair to say.

That what we’re really executing in background and coming up with a net difference that has to be communicated across from the worker thread to the UI thread and put on screen. All of this pre-supposes that you’re actually suffering from slow change detection. Even if that, a reasonable question to whether if you have slow change detection, offloading it to the thread is the best way to optimize it.

Stephen: One of the use cases to look out those is mobile. Mobile users are so much less powerful that any sort of change, any sort of code you’re running risks interrupting that smooth UX.

Imagining a user scrolling. Maybe you’re virtual loading things. You want that scrolling to be a UX action that propagates back to your Angular application in its separate thread that triggers change detection that says, “Hey, should I render?&nbsp; Do I need to get new data from the server, what do I need to do?” Then process that data all outside of UI threads. The user’s still scrolling. The idea is we add those DOM all and sort change those DOM or make those DOM changes in UI thread where they have to be.

I would say people don’t think we’re run into CPU constraints and bottlenecks, but we absolutely do. You can see it every day in the mobile use case.

Lucas: I think that’s really interesting thing because so many of us who are on this Podcast are used to targeting a desktop browser where we have all the power in the world. We see Angular Two doing so much to crank up performance. For us, the desktop browser users, we feel like we got performance to burn. We can just shock it away. We don’t need this kind of assistance, it’s running plenty fast for us. It appears that Google and Angular Two have their eyes on not just the desktop browser but something else, some other environment. Is that fair to say?

Stephen: Absolutely. I think that’s actually reflected by a recent announcement from the Chrome Dev Team where now by default, the Chrome Dev Tools are actually going to enable CPU throttling. Anytime you open the Chrome Dev Tools, the future version of Chrome, you’re actually going to see what it feels like to be on a mobile device more accurately. I think drawing attention to this is going to help a lot of developers around the world. It reflects the reality of these devices much better.

Joe: Yeah. It’s hard for us who live only on the browser and so many developers taking their job. You think our job is done when we made it run on the browser. Without really thinking terribly hard about where it’s actually going to run.

John, in your world, wherever that world happens to be, what’s the likelihood that something that you’re working on might run on a mobile device?

John: About 100%. Pretty much, I am not exactly sure. Most everything we do is mobile ready, if not mobile first. In some cases, mobile only. Those maybe web applications for Native or Hybrid. Everything that we’re building these days that’s new is being targeted for a phone definitely and some cases a desktop, laptop, or tablet.

This is an important piece that we’ve been dealing for Native apps. Now that we’re running on phones, one of the things we have to figure out is if only a lot of data cause we’re still trying to break our users from the habit of I need 7,000 items of data on a phone. Until we can actually break them of those habits, some cases we need better ways to render. Those will definitely be helpful.

Joe: Did you profile those use cases at all? To understand both the CPU and bandwidth limitations that the really users experience.

John: Yeah we have a lot of stats from apps that are actually in the wild and ones that were inside R&D at this point. Once in a while, we get a lot of data back from how people are using and what are actually doing is what they think they tell us they’re doing.

Ward: Is someone who’s led your company in developing Angular apps. You have to convince people that it will actually work on these devices. It sounds like that Chrome throttling thing would help to reveal where there might be some bottlenecks. The web worker thing if you actually run into a bottleneck might actually be something you can explore. Does it sound like it might?

Lucas: Yeah, it actually is. There’s reality in those perception. I think we have to live in both worlds. The perception right now of a lot of C level executives, lot of large corporations, I believe this to be true on a lot of companies, is that historically in the last five to six years, running apps on mobile devices is a problematic web apps. Because of things like an iPhone, how they used to throttle on browses which they no longer do in certain ways if you do is through what you’re doing with new web views.

Things how much data bandwidth you get. Limitations on the different applications to the CPU as Stephen eluded to. Even just some of the frameworks that are not Native, maybe not being as performed into a lot of different ways. Some of these things, all of these things were through. Some of these things are no longer as true as they use to be.

When you combine that with the idea that we can use things like web workers to offload things on these browsers and these new frameworks are coming out like the Ionics and what not, Native Script, etc. I think it’s really good time, especially to Angular Two, to start diving into these web desktop apps. Learning this and then applying those same things to mobile apps. I have never been more excited about mobile apps with web than I am right now.

Ward: Yeah. To flash forward, I think the end vision, at least what I’m hoping to see personally, is that every application is being run on a web worker. Because there’s always performance benefits that you see when you take work off the UI thread. Every time a mobile device ever stuttered because something was rendering or resizing.

Google has an entire project related to how do we make the web faster called Amp. That revolves around reducing a set of functionality. You have to in very specific ways increase performance. Using something like Angular with web workers, we want you just built kind of not think about it. In desktop development, in mobile development, if it had more multiple threads separating the rendering from the logic of its forever. But because we have this legacy of JavaScript, this single threaded JavaScript that we have to kind of pull ourselves to, we haven’t had that benefit. If we can automate that or make that simple by just changing how you bootstrap an application, that’s the goal.

Lucas: Some of these examples are super dead simple. Think about just a simple list of 20 items on a phone running in a web app. Loading that on a phone natively, that’s like no big deal. Or even on a desktop of web. But once you go to a phone with a web app, sometimes there’s a slight lag. It might even only be 50 mil seconds but the user notices it. By moving things like this to using web workers or what not, if we can eliminate some of those, I think there’s going to be a lot more buy ins for mobile apps with JavaScript.

Tor: Yeah. It’s not a fantasy. You still have to understand and manage how you use CPU cycles. Because CPU cycles have to come from somewhere. With these multicore devices that we keep seeing, this does help.

Ward: That’s extraordinary plain. I want to back up. Hearing you say, I hear you say extraordinary things stuff from time to time. To hear you say, ideally it would be so easy, we think we could get to the point where it would be as simple as just opting in to throwing my application over to a web worker. That’s really the vision. We’re somewhat close to that future.

Tor: I would say we are on the path to that vision, yes.

Ward: Wow. Cause then you could find out, you could just try it and see if made a different on that device. As John was pointing out, you still have to optimize another way because you can’t send the world day to them. Nothing could change that.You have to introduce better algorithms and so forth. But if it’s really that easy, truly looking at the bootstrap code, it looks that easy. When you look at the new.

Stephen: I’m sitting here with my jaw dropping and hitting the table.

Lucas:You sound like trump.

Ward: That’s jaw dropping but.

Tor: One interesting thing too that my background is originally from .net world. There, you have multi-turning. Another thing that brings in with it is you have to make sure that things are thread safe. Are there any issues on web workers around that are there any got use to, cause I didn’t explore that part of it. Does that factor in at all?

Ward: As I was getting to right now, you have the same problems that you have as you do in a single thread. If you run into an infinite loop the result that’ll kill your Angular app. It’s just happening on a different thread. If I were into an infinite loop instead of blocking my UI so I can’t scroll or I can’t touch the screen at all, just my JavaScript and my code is going to stop running.

Joe: I think this is a different question. This is a question what you face in other environments like C Sharp or .net is you face concurrency issues because you’re going to have two threads touching the same data. That can’t happen here.

Stephen: Yeah, cause it’s all running in a single thread still. Just not the UI thread.

Joe: Within the web worker. Moreover, the web worker and the UI thread are never actually writing to the same data. There’s no concurrent data issue.

Tor: All of the data lives in the web worker and then just propagates by DOM updates.

Stephen: Across the channel. You don’t have to worry about locks, some things like that.

Tor: I think also I remember seeing that, I think you don’t actually share data, you clone the data. If you send the same data to two different web workers, they’ll be cloned.

Stephen: Correct.

Tor: I think it’s completely a very different environment.

Joe: Alright. Anything else we should talk about guys, before we wrap up the show Anybody have any useful anecdotes about web workers?

Ward: I was a follower of web worker last week.

Lucas: We’re wing man, web worker wing man.

Joe: Let’s move on to picks. John do you want to go first.

John: Sure. I’ve got two, one technical, one not. For technical, I wanted to point to there’s this dock that our friend Ward Bell has primarily authored on the Angular Docs about NG Modules. I’ve read it about four times. It’s really, really good. It’s very long, but it’s very detailed on the new features of the NG models that came out with RC5. It’s an extremely important feature in Angular 2.0 as we’ve discussed.

What I love about it most is that it takes a problem that was this is a primary use case. It’s definitely a big use case. It takes a problem that was massively difficult with Angular One, lazy loading of modules. It helps, it’s one of the things that helps make lazy loading of modules dead simple in Angular Two along with the router and some other things.

Ward does a fantastic job explaining it in the NG Modules documentation. He deserves kudos for that.

For my non-technical pick, there’s a website that I stumbled across called tinkercrate.com. They’ve got this little packages where you subscribe to it, get a box in the mail, they’ve got for ages 0 all the way up through 16 plus where they send you something that’s like, it’s kind of a science, or a technology, or a math, or engineering. They send you these things in the box where you and your kids can build things together.

One of them that is coming in the mail this week that we’ve been getting excited to play about where it is you get to build a trebuchet with my son. That looks super exciting. It’s like $16 a month and you get to build some really cool stuff. It’s called tinkercrate.

Joe: Awesome. Stephen, how about you?

Stephen: I don’t have a pick.

Joe: What?

Stephen: I’ve been boring. I’m going on a honeymoon this weekend.

Lucas: Yours?

Stephen: My honeymoon.

Joe: He’s crashing one.

John: We did that, a pretty honeymoon?

Stephen: No, this is the honeymoon. Then we’ve got a post honeymoon to schedule.

Joe: Who else’s honeymoon would he be going on?

Lucas: I just wanted to be sure.

Tor: Honeymoon crash or totally sound like.

Lucas: I’m waiting for my invitation in the mail to join them on their honeymoon.

Joe: Stephen, can you tell us where you’re going?

Ward: That was my pick. My pick was I’m going on Stephen’s honeymoon. I’m done. I’m done, I have no picks no.

Joe: Stephen, can you tell us where you’re going on your honeymoon?

Stephen: I’m flying into Paris and flying out of Barcelona.

Joe: Have fun. Congratulations.

Stephen: Thank you.

Joe: Ward, how about you?

Ward: I told you, that was my pick. I was flying to Paris and going to fly out of Barcelona. Now, I’m deeply disappointed. That was my pick.

Joe: Alright. Lucas, how about you?

Lucas: I have two picks. My first pick is a little gem that I found on Lean Pub called the Angular Two Router by our friend Victor Savkin. It’s really quite brilliant. I’m a huge fan of Victor.

My second pick is I was just ranting and raving in Slack about how stoked I was that he actually wrote this book. They started talking about functional programming and some of the axioms around coming rational data flow. He linked me to a paper called Out of the Tar Pit by Ben Mosely and Peter Marks. It was written about ten years ago. Really, really, well written, talking just about some of the complexities that come with the software. Auditory in a programing versus functional programming. How they attempt to solve those. In general how to reduce complexity.

It’s all academic. I had to read it about three times. Eventually, I just printed the entire thing out. It’s about 55 pages. Stayed up until 2 in the morning with a highlighter going through it. Really, really good paper. I’ll put the link in the show notes. I highly recommend just for the sake of writing better software and reducing complexity. Take some time in going through that article.

Joe: I saw a movie recently, this last, few days ago. Hardcore Henry. I watched on VidAngel which I love watching movies on VidAngel, getting the edited out any content, I’m not interested in sync.&nbsp; The movie was actually quite fun. It was filmed from a first person’s stand point. It’s an action film. There was just a lot of very unique stunts and tricks filmed in the first person, kinds of stuff you would not expect to see done. Especially from a person, kind of made me sit and wonder. Wow, how did they do that? How did they do that? How do they make this special effects work? Very fun to watch. I highly recommend watching, if you’re way into over the top action.

I also want to mention again, John Papa and Dan Wahlin doing the training class down in Florida. October 6th and 7th. I’m going to be over there helping them out which I’m super excited about. If you use the code AiA, you can get a couple hundred bucks off your ticket over at www.ng-learn.com. I’m really excited for that. They’re awesome trainers and I think it’s really really fun time over at Florida hanging out near the beach. Maybe sometimes on the beach learning about Angular Two.

Ward: Oh yeah. Tor, how about you?

Tor: Okay, I’m going pick together that chat channel playing go with two. I think that’s an amazing resource for learning Angular. Also to help others. You can both get help and offer help there. I think it’s a great community that hangs out in that channel. Kudos to all those people who dedicate a lot of time there.

Joe: Awesome. Alright Tor, thanks so much for being on the show. We really enjoyed having you on.

Tor: Thanks for having me.

Joe: Thanks for all our listeners, we’ll be back next week.


