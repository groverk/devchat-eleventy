---
layout: layouts/post.njk
title: >
      155 iPS Cordova with Ryan J. Salva
date: 2016-06-02 07:00:26
episode_number: 155
duration: 45:26
audio_url: https://media.devchat.tv/iphreaks/iPS155RyanJSilva.mp3?rss=true
podcast: iphreaks
tags: 
  - iphreaks
  - podcast
---

01:04 - Ryan J. Salva Introduction
- [Twitter](https://twitter.com/ryanjsalva)
- [GitHub](https://github.com/ryanjsalva)
- [Blog](http://ryanjsalva.com/)
02:08 - [Cordova](https://cordova.apache.org/)
- [WebView](https://developer.android.com/reference/android/webkit/WebView.html)
05:19 - Hybrid; Native Applications11:58 - Code Reuse and Sharing16:01 - Performance25:32 - Update29:36 - Performance (Cont’d)37:11 - The Development Process&nbsp;Picks
- [Microsoft Bot Framework](https://dev.botframework.com/) (Ryan)
- [Ryan's Blog](http://ryanjsalva.com/) (Ryan)


### Transcript

**_[This episode is sponsored by Hired.com. Every week on Hired, they run an auction where over a thousand tech companies in San Francisco, New York and L.A. bid on iOS developers, providing them with salary and equity upfront. The average iOS developer gets an average of 5-15 introductory offers and an average salary offer of $130,000/year. Users can either accept an offer and go right into interviewing with a company or deny them without any continuing obligations. It’s totally free for users, and when you're hired they also give you a $1,000 signing bonus as a thank you for using them. But if you use the iPhreaks link, you’ll get a $2,000 bonus instead. Finally, if you're not looking for a job but know someone who is, you can refer them on Hired and get a $1,337 bonus as thanks after the job. Go sign up at Hired.com/iphreaks]_**

**JAIM:** Hey everybody and welcome to episode 115 of the iPhreaks Show. Today in our panel, we have no one. It’s just me. It’s just Jaim. I’ve taken over. Do not attempt to adjust your radio. There is nothing wrong. But we do have a guest today and it is Ryan J. Salva.

Ryan, can you tell us a little bit about yourself?

**RYAN:** Yeah man, totally. First, thanks for having me on. I really appreciate the opportunity to chat with you and all weird developers on the podcast. Super cool.

As you said, my name is Ryan J. Salva. I am a product manager over on the visual studio team at Microsoft. Specifically, my team works on JavaScript mobile develop and so anything having to do with Apache Cordova, React Native and even occasionally NativeScript or any other crazy framework that you guys think of to deliver for mobile apps to using JavaScript.

I’m a JavaScript developer myself for about 15-16 years now. I’ve been with Microsoft for only five of those. Before that, I was an entrepreneur, had a couple of startups, a little bit of success there; spent a lot of time in web development. So I love geeking out about anything having to do with web technologies.

**JAIM:** Great. Sounds like we have a lot of cool stuff we can go over. [Inaudible] Today, we’ll talk about Cordova and tell us a little bit about that project.

**RYAN:** Yeah, totally. So I love – people have probably heard about Cordova. It’s been around as a technology framework for about six years now. It was originally developed by the [inaudible] corporation at Vancouver, Canada under the name PhoneGap. So a lot of people, when they hear PhoneGap or Cordova, they think, “What’s the difference between the two?” The fact of the matter is that PhoneGap and Cordova are essentially synonymous.

What it is is a technology – is it’s a way of taking a web application, a JavaScript-based application, packaging all of those web assets up and putting them inside of a Native wrapper so that when you deliver the native APK to the Android device, what you’re actually seeing is a full-screen WebView so all of your UI is rendered via HTML, CSS and JavaScript. But then, there is a bridge in between the web part – the WebView piece of it and Native code running on the other side so that you still get access to things like camera or accelerometer or address book, really that good kind of stuff.

We still have access to all your device capabilities. You still have the ability to sport offline scenarios because all of the web tech – the HTML, CSS and JavaScript – is ultimately packaged with the application.

It’s really just a way for JavaScript developers to participate in the mobile app economy without having to abandon the languages that they love.

**JAIM:** Okay. So you talked about Android, the APK, in the iOS world. You’re actually creating an app and that’s rendered in a UI WebView?

**RYAN:** Yeah. It’s the same across all of them. You essentially got a closed ring WebView which is rendered using, as you might expect, HTML, CSS and JavaScript. In both cases, bearing a still-Native code that can run those Native code as bundled using these things called plugins. Plugin is essentially just a componentized bit of Native code that gives you access to a [inaudible] like camera or accelerometer or address book. Then your HTML application that’s sitting on that WebView uses a common JavaScript API to access the Native code so that in the end, you’re able to use the same common, shared code base cross both iOS and Windows and use a single navigator.camera.gitpicture method. But when it’s deployed to Android or iOS or Windows, it invokes the appropriate Native code for that platform so the camera plugin will be written in Java and the – or on Android and on iOS, it will be written in Objective-C. In Windows, it will be written in C#.

Ultimately, this is really just enabling developers to leverage the languages that they love or if they love JavaScript, stay with their development tools but still participate in the mobile app economy.

**JAIM:** Okay. So in a continuum of how we develop software that runs on mobile apps, we have your Native applications that run iOS, Android, or we have web applications which runs on a web server and just run in your browser. This sounds like it sits in the middle. You’re actually downloading an app but internally, it’s running a UI WebView and everything is happening in HTML so you’re not dealing with the Native controls but you do have access to some hard [inaudible]. You try it off a camera and different things like that. Does that sound right?

**RYAN:** Exactly. Correct. Yeah, that’s precisely correct. In fact, that’s why these types of applications end up being called hybrid applications. They’re a hybrid between Native and web. Significantly, there are ways to actually invoke Native UI controls. For example, developers can leverage things like the Ace plugin which allows you to invoke, let’s say, a tab control or a slide-in navigation menu, something like that. So there are ways that you can actually kind of pull from the best of both worlds – UI constructed using HTML, CSS and JavaScript and UI constructed via the Native layer. That’s kind of advanced techniques if you would [inaudible] more so than man-[inaudible] scenarios.

**JAIM:** Okay. So you do have some access to Native controls, buttons, table view if you need to have that type of functionality?

**RYAN:** Exactly.

**JAIM:** Cool.

**RYAN:** Yeah, absolutely. I think what it really allows you to do is it allows you then to leverage – let’s say you’ve got – let’s say it’s a product list. Let’s say you’ve got a commerce type of app or retail app and you’ve got a product list that’s a bunch of men’s shirts, let’s say. There’s no reason that that long list of just – what it’s usually is just JPEG images along with a little bit of text, that can’t be HTML, CSS and JavaScript across all of your deployment targets, both going to mobile applications and going to web applications. But then, when you’ve got some kind of marquee experience, some sort of ubiquitous navigation or some kind of [inaudible] page kind of home view, entry view that you want to be super slick and have really fluid animations. You want to really feel like the Native platform, that’s when you invoke that bit of Native UI.

So you could maximize then your code sharing and eliminate replication of code across deployment targets but still have really slick custom UI that provides a unique experience based upon the device and the platform which you are using.

**JAIM:** Okay. So you can get some Native features if you want to drill into that.

**RYAN:** Absolutely.

**JAIM:** So if you can just go Native, why are we even looking at hybrid solutions? Why is that a cool thing?

**RYAN:** Really for me, personally, in my own projects, there’s two really big benefits and those cascade out into a bunch of smaller pieces. So really, benefit number one is that I can eliminate redundancy in my code and I don’t have to rewrite the code multiple times for different deployment targets. Being able to consolidate into a single code base allows me to get to market faster. It also allows me to minimize my development cost and it minimizes my maintenance cost overtime. All of that, those are huge. Beyond that, like I said earlier, I’m a JavaScript developer of many years and I’m pretty gosh darn comfortable in JavaScript. So being able to lay down my code both on the backend using Node and on the frontend using JavaScript on the client side of things, it allows me to leverage the skills that I’m most familiar with, most effective with. And that’s me as an individual, as a developer.

But I also talk to a lot of companies that find themselves in a position where their entire team, because the web has been around for 30 years now and a lot of the applications and organizations that have been built have been browser-based. When they need to move to mobile app development, all of their skills are rooted in web technologies. So as they try to make that transition from browser-based applications, web applications to mobile applications, it really help ease that transition between the two worlds. And if you add on top to that the fact that frankly, in a lot of job markets, the number of developers who really have deep skills and native technologies, it’s quite fewer than the number of skilled web developers out there. And the Native app developers who are available are often coming at a much higher price than the web application developers. So it’s much easier and it’s just like a – there’s a larger number of web developers to draw from for organizations to be effective quickly.

**JAIM:** Okay. Sounds like there are – you’re saying it’s true; there are a ton of JavaScript developers. JavaScript has become ubiquitous especially with the last five years or so even though it’s been pretty popular before that.

I think after the nuclear holocaust comes, we’re going to have cockroaches in JavaScript.

**RYAN:** Cockroaches in JavaScript is [inaudible] and I love it; I like it.

**JAIM:** That’s what’s left.

**RYAN:** Yup. And I [inaudible] it to a little bit in there but the whole [inaudible] stack thing, being able to use JavaScript both on your server side and on your client side, that also helps an awful lot when it comes time to put together your team, then you don’t need strongly different skill set for your client side developer and your service developer. The same that I can do double time can do double duty. That’s not just a matter of efficiency of your workforce, but – I don’t know about you but in order for me to build a good application, it really helps for me to know what’s happening both on the server side – on the service side and on the client side. I’ve got a better view of what the total app architecture looks like then and that allows me as a developer to write more efficient code, and so that’s the big plus in my point of view.

**JAIM:** Yeah definitely. If you can use the same language on the server side and on the client side, that’s a huge win. That’s something we’re hoping for with Swift [inaudible] for Objective-C but it’s a benefit. But how much of a benefit is it really? Because web development – developing API server stuff, it’s a certain mindset, certain set of pattern in client development is very different. How much code are you seeing in practice?

**RYAN:** There’s a couple of different angles to look at this. There is a difference here – I totally agree – between building a website and a mobile client. Those are – I wouldn’t say they’re worlds apart but they are very different things.

I tat there – you do see a lot more commonalities between building a web app and a mobile client. A lot of web applications have moved closer to a single page architecture, then the amount of code sharing and code reuse that you can see between your web distribution channel and your mobile app distribution channel can climb up there to the 70% to 80% range.

I think more so than anything else, particularly for developers who are coming from a browser based – web-based application, it’s being able to share their business logic less so than it is the UI layer.

Let’s say – let’s take this canonical example of moving – oh God, I hate using this example, but we’ll use an expense app in the line of business scenario – that expense app, it probably have been there for 15 years and the whole thing needs to be rebuilt from scratch anyways. But so long as you’ve got some decent service based APIs, the transfer of skills from that browser-based deployment target to the web one, it’s a lot easier for those developers to just say, “Alright, pick it up. I can now make some better decisions about my architecture on the mobile client. I may be starting from scratch or close to scratch, but at least when I’m picking up and starting to write again and build that app, I can do so without also having to show them the burden of learning a new language or a new technology at the same time.” I can at least stay in a JavaScript coding model and that allows me again to get the application built quickly to use the exact same code base to all three of the major platforms out there – the iOS, the Androids and the Windows of the world.

That speed to market and reduced maintenance cost overtime really pays of dividends even if the amount of code sharing that I’m doing between my brand new shiny mobile client and my expense app is 10 or 15 years old. Even if there’s not a whole lot of code sharing there, I’m able to get there quickly, I’m able to get there in a way that eliminates redundancy of code between the despair of platforms. So I’m done having to rewrite it two or three times.

**JAIM:** Okay. That makes sense. If you’re coming from a JavaScript background where you’re doing web development, web development as you said is getting heavy client-side patterns which can mimic what we’re doing on mobile clients.

If you’re coming from a JavaScript background and going to write a native app, an iOS app, you have to learn two things. You have to learn UI kit which takes a while. It’s a mind [inaudible] if you’re coming from different [inaudible] and you’re also [inaudible] a language with Swift or Objective-C. [Crosstalk]

**RYAN:** I’ll add to that. You’ve also then got to learn a new IDE as well. You got to switch to Xcode. Not that Xcode isn’t great. I love it but for someone who’s coming to it for the first time, having to switch around their muscle memory and learn a new development environment, there’s a cost to that as well.

**JAIM:** Okay. This allows a lot more developers to get a mobile app up and running.

**RYAN:** Yup.

**JAIM:** One of the drawbacks I’ve seen with the PhoneGap and I think most of our audience are native iOS developers so when they hear PhoneGap, they probably throw up a little bit in their mouth. [Laughs] I got to represent their viewpoint for.

**RYAN:** Nah, totally!

**JAIM:** We started seeing PhoneGap apps three, four years ago and we’ve really seen some really bad apps.

**RYAN:** Oh yeah, dude.

**JAIM:** Performance have been just awful. Table view is [inaudible] barely scroll. So there’s a performance hit with rendering the stuff inn JavaScript versus using the native controls.

**RYAN:** Yeah, totally. And you know what, your audience will be totally right there. To go from a really well-written Objective-C or Swift app and then say, “You know what, I can compare that apples to apples to a PhoneGap/Cordova app, it totally [inaudible].” The chances of seeing performance differences or even subtle UI differences are strong. You’re going to notice a difference there. I think that it’s the trade-off that you make between having to rewrite the app multiple times and seeing a slightly different performance characteristic or slightly different user experience characteristics. A lot of that depends upon the type of the app that you’re writing.

I think about this particularly in light of – if you’re trying to make your entire living – if your business is making all of its revenue .99 cents at a time through app store purchases or in-app purchases, then it probably is going to pay off for you to build that app in native code. Completely agree. Go for it. Do it. But if your business is really making their money selling widgets elsewhere and the app that you’re building is either an employee-facing app, a business-facing app, and if you’re really just trying to mitigate the cost of that development, get something new out there that is effective or that is cost-effective while at the same time being functional. Something like Cordova/PhoneGap is an excellent choice.

I would also add to that. Let’s say I do this all the time. Let’s say that you’ve got an idea for an app. You’re not entirely sure it’s got any traction; you’re just trying to get an MVP out there to see if this is an app worth building. If you wanted to throw together a solid MVP, a good prototype, do it in one or two days. Cordova/PhoneGap and again, another great choice here. That way, you can at least get something into the store, get it there quickly. Get some user feedback. Then if it looks like that app has got legs and you’re ready to build up something that’s a little bit more lux, then go for it. Throw away the old code that you wrote the Cordova app in and rebuild it again using native languages. That’s a totally reasonable strategy as well.

I think a lot of Cordova’s sweet spot, again, is being able to leverage the rich amount of resources that are available to the web community. Being able to leverage that to cut and paste, build something quickly, get it out and not have to worry so much about the long term maintenance split across multiple platforms. The primary value proposition here, the reason for doing it is that you want to share code amongst multiple platforms at a low cost and want to do it quickly. That’s when Cordova really, really shines but then when you’re ready to become a Top 10 app in the store, hell yeah, convert over to native at that point because at that – hopefully, you’ve proven your business model by that point and you’re ready to invest in a more premium experience.

**JAIM:** That’s a good point. One thing I [inaudible] with a lot of my clients is that don’t spend money until you know this is a product that people want to use.

**RYAN:** Totally.

**JAIM:** That completely makes sense to me. So if you can crank something out quickly and just verify what you’re doing, that’s totally valid. It may need to be a native solution at the end game but to choose different approaches, you can go do something quick with Cordova or go native. I feel there’s a continuum.

**RYAN:** Yes.

**JAIM:** If you’re Facebook, you want people using your app everyday; you want them swiping through things and doing all sorts of crazy things. That has to be native. It would never go to Cordova.

On the other spectrum, if you have a [inaudible] audience that needs to use what you’re building, they want to, they need the info, they’ll use whatever you have. If it has bugs, if it has crashes, they don’t care.

**RYAN:** Yeah. Hopefully you’re not deploying bugs and crashes. I don’t want to paint an unfair picture of Cordova that it is a buggy framework. It is not enough itself; it’s actually very stable but [crosstalk].

**JAIM:** I didn’t mean Cordova. I’ve been saying like if people want to use your app, need that info, they’ll put up with whatever they have to.

**RYAN:** Yeah.

**JAIM:** A few years ago, there’s one college hockey app on the app store and it was PhoneGap or something like that and it was awful. It’s probably [inaudible] mobile PhoneGap. Performance is [crosstalk] but it was the only app that had an info so I used it.

**RYAN:** Totally.

**JAIM:** My [inaudible] scores. [Chuckles] They went native a year or two later but if people want to use it, they’ll use it.

**RYAN:** Yeah, and by that point, they have proven it out that people like you would use the app. They would see the ads or whatever kind of monetization strategy they were using and they are ready to graduate up out of it.

It really just depends like do you want to invest all the time upfront especially if you’re trying to target multiple, different app stores. Do you want to invest all the time upfront to write it twice or three times? If you don’t, hey, this is a really great option to test out an idea, to see if it’s got legs. To be fair, there actually are some unique advantages to the JavaScript ecosystem here. The big one – this one gets played up an awful lot by the React Native community but it applies equally well to Cordova apps as well.

One of the shackles that we have as native app developers is that anytime we want to submit an update to the store, we have to just do that [inaudible] resubmit it to the store. I don’t know about you, but my experience has been – especially with the Apple Store – that can often take days but we were actually getting the app, update the [inaudible]. That time, especially if you’ve got a crashing bug or something like that can be Black Death to your reigns. So one of the unique advantages that JavaScript apps like React Native and Cordova and NativeScript have is that you can update your app dynamically without resubmitting to the store.

There’s a clause in the Apple developer agreement that basically says – I forgot what exactly the legal [inaudible] is but it essentially says you could update web assets without resubmitting to the store because, of course, apps like Yelp and Facebook and pretty much everything else out there, needs to be able to get data and images and things like that dynamically. So what that does is that opens up something of a little [inaudible] for Cordova, React Native developers whose entire application is written using JavaScript. It enables them to essentially replace the entire contents of their WWW folder that is packaged locally with the app.

So if you’ve got a bug fix or an update or an incremental feature/enhancement you want to deliver, so long as you’re not changing the fundamental purpose of the application, you can use a service like CodePush or PhoneGap Hydration or Ionic Deploy or anyone of these other essentially update services, to replace the entire contents of your WWW directory and fix that bug, deliver that new feature. Do whatever you need to do and do it as the same release [inaudible] that we expect out of the web.

If you want to deploy updates two, three, four times a day, go at it buddy. It’s all yours to do. That’s the place where I think – we talked a little bit about code-sharing earlier and how that [inaudible] at the same time and after it reduces code redundancy, those are all great and important things. But the ability to update and to deploy the applications, that’s something that uniquely and only JavaScript-powered apps can do and I think that’s a pretty awesome thing.

**JAIM:** Yeah, that’s one of the Achilles heel at least in the Apple ecosystem where [inaudible] you’re dependent on the App Store to give you the thumbs up for anything that you want to change which takes time.

**RYAN:** Exactly.

**JAIM:** Days or weeks. Lesser problem with Android because you can just throw it out there if you need to.

**RYAN:** Yup.

**JAIM:** So how does update work? If the user’s actually using your app and they go in through it and you update the JavaScript [crosstalk], does that happen at app launch? How does that work?

**RYAN:** Yeah, it’s really totally up to the developer. The basic workflow looks like this – I’ve submitted my app to the store for the first time. It’s got to be in the store for people who download it the first time. And when I submit it to the store, I include the native code to process the update. I’m going to use CodePush as my example because it’s my personal favorite. Then, when you’re ready to submit an update, what you’ll essentially do is you will zip up the web assets that you want to deploy and you’ll upload them to the CodePush service.

On the client’s side, it is the developer’s decision what events they want to paying the server for. Usually you’ll use an app life cycle event like on resume or on device ready. You could also make it on a button push or you could even have something running in the background that checks every minute if you want it to. So whatever app life cycle event you use, what will happen is then your mobile client will ping the CodePush service and when it pings the CodePush service, it’ll essentially – part of that asynchronous call, it will include what its current version of [inaudible].

So let’s say it pings the CodePush service and says, “I currently have app version 1.1”, CodePush will say, “Oh hey, I got a 1.2 available.” At that point, it will return a response back to your mobile client and your mobile client can then decide what it wants to do.

There’s lots of options that you could use. For example, you can make the app update mandatory or you can make it optional. You can make the update only deploy to a percentage of your users. If you want to do AB testing for different types of features, or even if you want to incrementally roll out updates so that you’re doing a little bit of test in production and just deploying up to 5% of your user base before you go out to everyone to make sure that you [crosstalk] – exactly! But then at that point, the user experience – people actually using your apps, the most common thing is that you’ll get a little – a dialogue that says, “Version 1.2 is available; would you like to install?” You say okay and at that point, you’ve got two options. You can either force a restart of the app once it’s complete and it’s done or you can let them wait until the next time that they naturally restart their app to replace the contents of the WWW folder.

It does require a restart, the app. But then there’s all sorts of safety checks that you can also put in there to make sure that the actual contents of that zip folder were completely downloaded in a non-corrupt fashion and were correctly installed in the WWW folder.

So one of the things that I love about CodePush service is that it also allows me to essentially rewind the clock. If either the contents were not successfully downloaded or even I delivered an update that I decided I didn’t like because there was a crashing bug in it or something like that, I can rewind the clock and from any user’s experience, all that they see is a little dialogue that says – you can change the language but if this update didn’t work, we’re rolling you back to version 1.1. So that gives me a lot of confidence that what is installed in any users’ machines or on their mobile devices is something that’s actually working. They’re not stuck in some kind of weird in-between state that doesn’t allow them to use the app. That’s particularly when you’re doing dynamic updates and if you move to [inaudible] or you’re making these updates frequently, having that confidence is super important, that the service is taking care of it for you to make sure that they can always get back to a last known good state.

**JAIM:** Okay, that sounds good. Why don’t you talk a little bit more about performance? Because I’ve mentioned that most of developers, when they think of PhoneGap, they think of these – the awful apps we’ve talked about previously. Since then over the past year or two, I’ve been noticing apps that aren’t native but it don’t really make my eyes bleed. [Laughs] They’re useable. If you click on a button, it’s not quite the same or scrolling animations, decelerations – it’s just not the same but it’s a useable app. Can you talk about ways things have changed over the past three years or so?

**RYAN:** Yeah, totally. So first, if I painted the picture earlier that PhoneGap delivered or Cordova universally delivers a subpart experience then thank you for giving me the opportunity to correct that. You’re absolutely right. Within the last two years in particular is what I’ve known, maybe as much as three. Developers just gotten smarter; it’s part of it and the hardware has also gotten faster. That’s really kind of the two channels.

On the hardware getting faster side of things, with iOS9 – I think it’s iOS 9 – Apple allows you to actually implement some of the acceleration that you expect at a normal browser in the embedded WebView. And so in iOS in particular, from a hardware perspective or at least from a browser perspective, that has gotten way better particularly in the last year. From a developer – developers getting smarter perspective, this is where I think the largest leaps and balance have come especially as we got a spade of JavaScript framework that weren’t just adapting from a browser-based framework to a web client or to a mobile client. But there are actually JavaScript frameworks intended specifically for mobile app development. Probably the two or three most popular of these are Ansi UI, Kendo UI and Ionic. The one that I end up probably using the most of is Ionic. Those guys have done a really fantastic job focusing on building high performance apps that adapt to the native UI of their destination platform.

Building performant UI controls, it takes time. It takes a lot of time spent analyzing frames per second. Can you optimize this for-loop a little and how can you get the right inertia or gravity out of your list scrolling? Most app developers don’t want to spend time doing that; they want to spend time doing the fun, creative stuff. So as we’ve gotten frameworks like Ionic where their entire focus is just on building out native-like controls using HTML, CSS and JavaScript, that’s – put application developers in a place where they can just leverage and build on the shoulders of those JavaScript frameworks as UI control frameworks.

When they want an infinite scroll list view or they want a tab control, they just have to invoke a tab control. These are the UI components that come already available in your native SDKs. And for the longest time, web applications, they have div tags and span tags. They essentially have rectangles. There was no tab control, no navigation control so what frameworks like Ionic and [inaudible] have done is they’ve essentially created the web equivalent of these native SDK controls so that when an application developer wants them, they can just put in that web component and be done and they don’t end up – this is what – when you see all of those really – pardon my language – shitty apps our there with terrible performance, what’s often happening is that’s a web app developer whose done copy and paste code. They brought in Angular and they brought in JQuery and they brought in React and they brought in Backbone and they’ve just layered these things on top of each other. They have no business being in the same application developer – in the same application together.

So as we’ve started to build out a sane architecture for what a good mobile app looks like using JavaScript, we’ve gotten better performance out of these applications and we’ve been able to build them more quickly as good recipes and good border plate has arrived.

So if you go to the showcase page for Cordova – cordova.apache.org – or the showcase page for Ionic, ionicframework.com, and you look at some of the apps that are built there, I’m willing to bet, a lot of you might even have some of those apps installed on your phone. And in some cases, may not have even realized that they were hybrid applications because they – they’ve actually gotten to a place where unless you’re really looking for it, the differences can be very minute.

**JAIM:** It’s definitely true; I was talking with an entrepreneur a week or two ago and another developer – a native developer. They’re showing the exact [inaudible] like – I asked them, “Oh, is it native? Is it hybrid?” and the entrepreneur didn’t really know. [Chuckles] Is he [inaudible]? And the other person that I was sitting with was like, “I think this is native.” I’m like, “Okay.” And I looked at it and it wasn’t after I took a closer look like, “Nope, no. these things aren’t right.” I wasn’t sure what they’re using but definitely, you can trick a lot of things.

The performance things are subtle and I don’t know, I discount how important those little small things are especially if people are using your app day in and day out for a lot of things if that’s your core business but for a lot of things, you just want to do one thing and get on with your life.

**RYAN:** Yeah. I recently downloaded a – it’s a noise maker app. It does – when I go to sleep, it has waves or has white noise in the background. Lo and behold, I used it for a couple of weeks, it’s a simple UI; I thought it was a native app and then I found out that no, it’s actually a Cordova app. I had no idea but as a developer, if you make the best use of your technology and you have good design sensibilities out of you, I think in the end, what end users care about is have you displayed craftsmanship in your application? It’s just as easy to create a bad native application as it is to create a bad Cordova application. But if you’re a responsible developer, if you care about your craft; if you spend time on your UI, you can create something that users are going to love but it takes mindfulness. I know that Cordova/PhoneGap has gotten a bad reputation in the past because they were a lot of developers who weren’t really being mindful, who weren’t really displaying craftsmanship because they were just trying to get something functional out there quickly and that – that makes us all look bad.

**JAIM:** Yeah, definitely. So I want to talk a little bit – briefly because we’re a little bit short on time – about the development process. So if you’re trying to build for iOS, are you still bringing up Xcode? What’s the development environment like?

**RYAN:** Yeah, totally. So your primary tools are going to be a text editor, command line interface and your device or emulator deployment target. For me, my primary editor is Visual Studio Code in part because I work on it as a program manager for Visual Studio. I build it but also because it’s a wicked awesome development environment. It’s got nice intellisense and code [inaudible] and it’s super-fast. It’s got integrated debugging. Then at the command line, that’s where you’re really going to leverage the Cordova build tool itself. Then your device, whatever the deployment target is.

Point of fact, while many developers may go into Xcode or may go into Android Studio at some point in their development process, 99.8% of the time, you’re never even opening up the native development tools or at least you don’t need to open up the native development tools.

When you will eventually go into Xcode for example is when you’re doing your signing and your provisioning. But other than that, ultimately Cordova is interfacing with Xcode and farming out the build process to Xcode for iOS or the Android SDK for Android, or to the Windows SDK for Windows. But Cordova has a build tool that takes care of that for you. So all of your active coding time really happens in your text editor of choice. Most JavaScript developers – I’m sure you’re well aware of it – you end up preferring some kind of lightweight thing like Atom or Sublime or VS Code or VIM. Then your debugging tools, a lot of folks choose to use Chrome for their primary debugger. All the code that you’re writing is – it’s usually HTML, CSS and JavaScript that you’re using or one of their variance TypeScripts or SaaS.

**JAIM:** So if you’re debugging in Chrome, do you end up having any differences when you actually go to device? Is that something you have to manage?

**RYAN:** No. You attach to the WebView in the device so you may run it in the device; you deploy to your Android device and then you bring up Chrome and you can attach the Chrome debugger to the WebView that’s running on you tethered Android device.

**JAIM:** Okay. Got it.

**RYAN:** Does that make sense?

**JAIM:** Yeah.

**RYAN:** Yeah, and then in the case of – like I said, my primary editor was VS Code so in that case, there’s actually a debugger that’s built into the editor so the same principle applies. I’m attaching to whatever my deployment device is.

So sometimes – I can deploy to the emulator, I can deploy to the device but a lot of developers will spend a significant percentage of their workflow deploying to a browser. In that case, your question is totally apt. Will there be UI differences or just differences between the browser and the Android device? And there – yes, absolutely. There will be differences, but that’s why when you’re doing your initial development in the browser, that’s where the macro level layout construction want to make sure that the business logic is working correctly. Your last 20 yards pretty much always happen in the device itself.

**JAIM:** Okay, great. So we’re running out of time. Is there anything else you want to talk about or [inaudible] about Cordova?

**RYAN:** No, I think that we’ve covered a lot of pieces of it. I would say that for developers who are particularly coming from native and are already super comfortable working with Swift or Objective-C or Java, the time for you to pick up Cordova is really going to be – maybe when you’re trying to take that new idea and test it with users. Or if you’re trying to take your app and see if maybe it will also have the same momentum in another app store. Let’s say that you have already deployed to Apple – the Apple Store – and you want to see if it’s going to have legs in Google Android Play Store, hey, you know what, Cordova’s a great way for you to test it out and get it out there quickly. Then from there, graduate up to the next level.

For organizations that really aren’t trying to make their business .99 cents at a time but they’re just trying to deliver a lot of business application, Cordova’s another great option for getting an app there quickly to as many devices as possible with as little upfront and long term maintenance cost as possible.

**JAIM:** Alright great. It’s a great overview of Cordova and I hadn’t been really keeping up on it; only listening to the gripes of iOS – native iOS developers [chuckles].

Good to hear the other side and that people have [inaudible] with it. Some apps, they’re useable and you can get by with it.

We’re going to get to the picks tonight.

**RYAN:** I’ll give you two if you don’t mind. I’ve got one thing that I’ve been playing with a lot recently which is the Microsoft Bot Framework as a side project to [inaudible building chat bots recently. This last – was last month. Microsoft released a new framework just with artificial intelligence. It plugs in to the same system that Cortana uses. It has [crosstalk].

**JAIM:** Windows Siri.

**RYAN:** Yeah, Windows Siri exactly. It has allowed me to build a really killer bot with AI and natural language recognition in a relatively short period of time. Anyone who wants to check it out, I would say just Google or Bing or whatever your favorite search engine is [inaudible] your Microsoft chat bot other than the swearing, racist Twitter chat bot, it should be one of the first ones to come up in your search results.

Then beyond that, I got to give a self-plug here. I just, last week, started to pick up blogging again. I hadn’t been doing it for a super long time. If folks want to learn a little bit about Cordova, go check out my blog, ryanjsalva.com. There’s a couple of tutorials down there and it might be a fun exercise folks.

**JAIM:** Okay, great. Yeah, I definitely was impressed with the bots. Our listeners are aware we were all out at Build a month ago, but yeah, we have to see the [inaudible] functionality. It’s really cool and really cool to see other ways to get information to people without the heavy weightiness of downloading an app and things like that. I’m looking forward to seeing what develops from that. Hoping Apple delivers something [inaudible].

There’s WW but I’m going to get to my picks and I don’t have much of a pick but speaking of bots and automatic stuff, I’ve been chuckling at the people trying to chat with me on Skype with the names. I don’t think they’re real but in case that diamondstarsnoopy and glitzliciousfancypants are real people, I’m sorry for blocking you but I’m chuckling at the names that are coming at me on my Skype.

Whatever bot is coming up with those names, I’m laughing.

**RYAN:** Awesomesauce. I love it.

**JAIM:** So Ryan, thanks so much for coming on this show. We tried recording at Build and they actually kicked us out of the room because of the whole conference being shut down. That’s just how it works some days so [inaudible] will be able to come back and I think we learned a lot about Cortana today. So thanks for coming on the show.

**RYAN:** Awesome buddy. Hey, thank you so much. See you again.

**JAIM:** Alright.

**_[Bandwidth for this segment is provided by CacheFly, the world’s fastest CDN. Deliver your content fast with CacheFly. Visit cachefly.com to learn more]_**


