---
layout: layouts/post.njk
title: >
      271 RR Problems New Developers Don’t Realize They Have and Hidden Tradeoffs to Coding Decisions Developers Have to Make with Justin Weiss
date: 2016-08-03 07:00:19
episode_number: 271
duration: 46:55
audio_url: http://media.devchat.tv/ruby-rogues/RR271NewDevProblems.mp3
podcast: ruby-rogues
tags: 
  - ruby_rogues
  - podcast
  - new_programmers
---

## [Rails Remote Conf](https://allremoteconfs.com/rails-2016)
&nbsp;01:14 - Justin Weiss Introduction
- [Twitter](https://twitter.com/justinweiss)
- [GitHub](https://github.com/justinweiss)
- [Blog](http://www.justinweiss.com/)
- [Avvo](https://www.avvo.com/) &nbsp;
- [Practicing Rails: Learn Rails Without Being Overwhelmed by Justin Weiss](https://www.justinweiss.com/practicing-rails/)
02:15 - “Learning Rails Without Getting Overwhelmed”?
- [Agile Web Development with Rails by Dave Thomas and David Heinemeier Hansson, with Leon Breedt, Mike Clark, James Duncan Davidson, Justin Gehtland, and Andreas Schwarz](https://pragprog.com/book/rails2/agile-web-development-with-rails)
02:34 - Problems New Developers Don’t Realize They Have04:35 - Learning New Things08:05 - What is a success?09:02 - What can senior devs do? What shouldn’t they do?
- [Apprenticeship Patterns: Guidance for the Aspiring Software Craftsman David H. Hoover and Adewale Oshineye](http://chimera.labs.oreilly.com/books/1234000001813/index.html)
- [Pragmatic Thinking and Learning by Andy Hunt](https://www.amazon.com/Pragmatic-Thinking-Learning-Refactor-Programmers/dp/1934356050)
- [Brandon Hays: The Conjoined Triangles of Senior-Level Development](http://frontside.io/blog/2016/07/07/the-conjoined-triangles-of-senior-level-development.html)
15:43 - Are there still “Architects”?20:45 - The Existential Crisis of Software Development
- [Integrated Tests Are A Scam](http://blog.thecodewhisperer.com/permalink/integrated-tests-are-a-scam)
- [Emo Philips: The best God joke ever - and it's mine!](https://www.theguardian.com/stage/2005/sep/29/comedy.religion)
22:26 - The Responsibility of the Students26:08 - How can new developers obtain objective evidence of their blind spots?
- [Bias Blind Spot](https://en.wikipedia.org/wiki/Bias_blind_spot)
- [The Fifth Discipline: The Art & Practice of The Learning Organization by Peter M. Senge](https://www.amazon.com/Fifth-Discipline-Practice-Learning-Organization/dp/0385517254/ref=sr_1_1?s=books&ie=UTF8&qid=1469747932&sr=1-1&keywords=The+Fifth+Discipline%3A+The+Art+%26+Practice+of+The+Learning+Organization+by+Peter+M.+Senge)
- [Asch Experiment](http://www.simplypsychology.org/asch-conformity.html)
33:49 - Early Career Developers Working Together37:03 - Learning Practices&nbsp;Picks
- [emoj](https://github.com/sindresorhus/emoj) (Coraline)
- [Teaching Robots to Feel: Emoji & Deep Learning](http://getdango.com/emoji-and-deep-learning.html) (Coraline)
- [The Lies of Locke Lamora](https://en.wikipedia.org/wiki/The_Lies_of_Locke_Lamora) (Sam)
- [Gorilla Tape](http://www.gorillatough.com/gorilla-tape) (Sam)
- [Portillo's](http://www.portillos.com/) (Chuck)
- [iPad Pro](http://www.apple.com/ipad-pro/) (Chuck)
- [Apple Smart Keyboard](http://www.apple.com/smart-keyboard/) (Chuck)
- [Apple Pencil](http://www.apple.com/apple-pencil/) (Chuck)
- [GoodNotes](https://itunes.apple.com/us/app/goodnotes-4-notes-pdf/id778658393?mt=8) (Chuck)
- [Podcast Movement](http://podcastmovement.com/) (Chuck)
- [The Principles of Product Development Flow: Second Generation Lean Product Development by Donald G. Reinertsen](https://www.amazon.com/Principles-Product-Development-Flow-Generation/dp/1935401009) (Justin)
- [How to Write in Plain English](http://www.plainenglish.co.uk/files/howto.pdf) (Justin)
- [Avvo](https://www.avvo.com/) (Justin)


### Transcript

 **JESSICA:&nbsp;** Anybody else catch a new Pokémon this morning?

**_[This episode is sponsored by Hired.com. Every week on hired they run an auction where over a thousand tech companies in San Francisco, New York, and L.A. bid on Ruby developers providing them with salary and equity upfront. The average Ruby developer gets an average of 5 to 15 introductory offers and an average salary offer of $130,000 a year. Users can either accept an offer and go right into interviewing with a company or deny them without any continuing obligations. It's totally free for users. And when you're hired, they give you a $1,000 signing bonus as a thank you for using them. But if you use the Ruby Rogues link, you'll get a $2,000 instead. Finally, if you're not looking for a job but know someone who is, you can refer them to Hired and get a $1,337 bonus if they accept the job. Go sign up at Hired.com/RubyRogues.]_**

**CHUCK:&nbsp;** Hey everybody and welcome to episode 271 of the Ruby Rogues Podcast. This week on our panel we have Jessica Kerr.

**JESSICA:&nbsp;** Good morning!

**CHUCK:** Coraline Ada Ehmke

**CORALINE:&nbsp;** Hi everybody.

**CHUCK:&nbsp;** Sam Livingston-Gray.

**SAM:&nbsp;** Bringing back the wacky intro quote one rogue at a time. [Whispers] Help me out here, rogues.

**CHUCK:&nbsp;** I'm Charles Max Wood from DevChat.tv. Go check out RailsRemoteConf.com. We have a special guest this week and that is Justin Weiss.

**JUSTIN:&nbsp;** Hello from Seattle.

**CHUCK:&nbsp;** Do you want to give us a brief introduction?

**JUSTIN:&nbsp;** Yeah, sure. I'm Justin Weiss. I'm the Director of Software Development at Avvo where we help people find legal help that they need, of course, like everyone else we're hiring. I occasionally write at JustinWeiss.com and I wrote a book practicing Rails which is about learning Rails without getting overwhelmed.

**CHUCK:&nbsp;** Nice. Now, to talk…

**CORALINE:&nbsp;** What's the point of learning Rails without getting overwhelmed? I don't understand.

[Laughter]

**JUSTIN:&nbsp;** Yeah, I don't know if you've seen. There was a picture that was going around a while back of all of the things that you need to know in order to be a Rails developer. And it just looks like this multi-tentacled octopus that's trying to attack you.

**SAM:&nbsp;** That's really been Rails all along I feel.

[Chuckles]

**JESSICA:&nbsp;** Well, back at the beginning of Rails we all had to already know this stuff and more. And Rails actually reduced the things we had to think about.

**SAM:&nbsp;** Oh, that's very true. Back when I learned it we could learn everything from the one Pragmatic programming book. At least, that's how I learned it.

**JUSTIN:&nbsp;** Yeah, and it's still usually the one that I recommend for at least getting a decent overview of everything. But there's definitely a lot to dig into.

**CHUCK:** Now, that's the Agile Web Development…?

**JUSTIN:&nbsp;** Yeah.

**CHUCK:&nbsp;** With Rails, I think is what it's called or something like that.

**JESSICA:&nbsp;** Oh, Pragmatic is the publisher.

**CHUCK:&nbsp;** Yes. So, the topic is actually problems that new developers don't realize they have. There's a little more to it than that, but I'm curious to know how… because I think what we're talking about here with Rails ties into problems that new developers don't realize they have. So, I'm curious. What do new developers run into that we just kind of don't think about as experienced people?

**JUSTIN:&nbsp;** Well, I think that the immediate solution you go into when somebody comes into learning something new and get stuck is like, “Oh, they need more resources. They need the right resource that fits them.” And what I've found just by talking to a bunch of people that have written in to me after running into one of my articles or that kind of thing is that it's a lot less about finding the right resource or just by cramming knowledge into your head but that more of the problems come with managing your emotional state, managing your time, managing your priorities. There's a little bit of this desire to do everything right from day one to try to just grab as much knowledge as you possibly can. And that just has not been successful for a lot of people that I've talked to.

**CHUCK:&nbsp;** You make new programmers sound human.

**JUSTIN:&nbsp;** Yeah, I know [chuckles]. It's kind of funny. I don't know what the last thing each of you learned, or the last big thing each of you learned is. But it probably went pretty similarly where it's not so much about finding all the resources. It's about, how do I just keep hammering at this and how do I keep the desire to keep hammering at this until I finally get it?

**JESSICA:&nbsp;** Starting a new job is that, like that. Picking up a new codebase and figuring out how all the infrastructure works and how anybody ever gets anything done.

**CORALINE:&nbsp;** I'm three months into GitHub and I'm still figuring that out.

**JESSICA:&nbsp;** Yeah, three months is just getting started.

**CORALINE:&nbsp;** Yeah.

**CHUCK:&nbsp;** Well, if you're lucky they have a really small system and it only takes that long to figure it out. But when you get into large, complicated systems even if you're focusing on one piece you're still dealing with how it interacts with everything else.

**SAM:&nbsp;** Or even how you interact with everyone else.

**CHUCK:&nbsp;** Yes.

**CORALINE:&nbsp;** So Justin, how much of this do you think is the fault of… not the fault but I think about people coming out of bootcamps and at bootcamp they're all working on greenfield apps and they're learning the latest JavaScript framework and they're working on edge Rails and suddenly they get their first job and they're looking at a Rails 3.2 application using only jQuery. And they're like, “What am I even doing here?”

**JUSTIN:&nbsp;** Yeah. That's one of the reasons that you see at a lot successful companies is mentorship and training being such a big thing. Everybody at least that I've met in my career has wanted to learn, has wanted to grow and get better. And sometimes those resources just are not there.

**SAM:&nbsp;** Well, so my undergrad adviser once made a really interesting comment that sometimes calendar time is the thing that really matters. I feel like there's… when you're learning stuff there are a couple of processes that go on in your brain. There's chunking which is where you learn to identify patterns of things and then put a label on that pattern so you can keep it as one thing in your head. And then there's just plain, the process of neural pruning where after you've learned a new skill your brain sort of makes space and makes that skill more efficient. And both of those things I think just take calendar time. So, I wonder if maybe you want to… well at least for myself one of the fallacies that I had to get over was that the idea that I could be good at everything right away, or anything even. [Chuckles]

**JUSTIN:&nbsp;** Yeah, exactly. I used to say, when it came to some of the things that I… it seemed like I was naturally good at, that it wasn't that I was naturally good at it. It was just that I had seen it before. And if I was in say high school math and I'd already independently read something like a year or two ago that was related to that, it was a lot easier for me to pick it up. It wasn't that I was naturally attuned to it. It's just that I had seen it before.

**CHUCK:&nbsp;** So, you're naturally good at the stuff that you've been prepped for over the years.

[Laughter]

**JUSTIN:&nbsp;** Exactly. You're naturally good at the stuff you've been practicing your whole life.

**CHUCK:&nbsp;** I mean, I did say it a little bit tongue in cheek. But it really is true. It's the things that I look at and I go, “Yeah, I've seen that before,” or, “I can relate to that,” that really, those are the things that seem natural. Sometimes there's something that's really new that for whatever reason the way that I think just lines up neatly with it. But yeah, for the most part when I'm learning something new, it really depends on how much experience I have with something that looks a lot like it.

**CORALINE:&nbsp;** Which begs the question that there is anything new in Computer Science.

**JESSICA:&nbsp;** [Chuckles]

**SAM:&nbsp;** No. Lisp and Smalltalk did it all already.

**CHUCK:&nbsp;** [Laughs]

**CORALINE:&nbsp;** Pretty much.

[Chuckles]

**JUSTIN:&nbsp;** The more I read the more that I start to realize that most of these things are not all that new.

**JESSICA:&nbsp;** Yeah, I want to say that we need to add more resources. But you just mentioned that it's really not about resources. It's not about giving people the right book or writing a tutorial as much as it is giving them the psychological resources to cope?

**JUSTIN:&nbsp;** Yeah. I mean, one of the biggest things that I've found successful for the people that have emailed in and I've talked to that way is that the biggest problem is giving up. That's really the only way to fail. And so, how do you prevent giving up? Well, you have that desire to keep going. You have that confidence that you're starting to get it. You're starting to see some successes. And so, if you can find a way to just repeatedly see those successes as you grow through your learning career, you're going to have that motivation to keep going.

**CHUCK:&nbsp;** So, I want to ask then, what is a success? Is it an “Atta boy,” or a pat on the back or whatever you want to call that? Or is it, “Oh look, I made it work,” or is it passing tests? Can it be any and all of those?

**JUSTIN:&nbsp;** I think it's any and all of those. But at least for most people I know it's that seeing what you've been building actually working in the real world. It's like, “I did that. That's really cool.”

**SAM:&nbsp;** Yeah, I was talking to somebody who's fairly early on in their career just last week. And I asked them if they had a particular specialty that they were interested in, front or backend, so I could figure out where to steer them. And they said something interesting which was that at that point they were still just amazed that they could type things in and make the computer do anything. And so, it was a little bit premature to be picking a specialization. But that was interesting. It reminded me of a perspective that I've long forgotten.

**JUSTIN:&nbsp;** Yeah. I think if a teacher can just keep sparking that “That's so cool” reaction, it's going to be successful.

**SAM:&nbsp;** So, are there things that as a more senior developer I can do to maybe guide people towards those wins or hints or perspectives I can impart? Or is it basically just, “Here, go into the cave. Have your epiphany and you might come out the other side”?

**JUSTIN:&nbsp;** I think sharing stories can be really useful. Like yeah, I actually ran into this same kind of thing last month or a couple of years ago or when I was just starting out. And this is how it affected me. This is what I learned from it. And this is how I moved on. Part of this is also just having people realize that, “No, it's not just you that's running into this problem. You're one in a long, long, long, long line of programmers that have run head-first into that brick wall.”

**JESSICA:&nbsp;** Opposite question. What are some things that senior developers do that really discourage and hurt earlier beginner programmers?

**JUSTIN:&nbsp;** I think a lot of it is when the senior developer is convinced that they are explaining it correctly. And the problem is that the junior developer can't get it. And I'm one that I'll almost always put the… the responsibility is on the person who's explaining it and not the responsibility of the person who is receiving it to understand. And sometimes that means explaining it in several different ways or several different metaphors or with different kinds of language or using different examples or just really trying to figure out how you can match your communication style with the person that is receiving the information from you or that you're communicating with in order to make sure that they come away with it having learned something.

**CORALINE:&nbsp;** And never ever, ever saying, “Oh, that's really easy.”

**JUSTIN:&nbsp;** [Chuckles] Yeah.

**CHUCK:&nbsp;** [Laughs] Yeah. How do you solve this problem? Oh simple, you just… right?

**CORALINE:&nbsp;** Yeah, exactly.

**JUSTIN:&nbsp;** Yeah.

**SAM:&nbsp;** I don't know. If invoices and line items were good enough for our neck-bearded forefathers, gosh darn it they're good enough for me.

[Laughter]

**JESSICA:&nbsp;** Yeah. There are a slew of words to avoid. Just simple, easy, obvious, straightforward.

**CORALINE:** Trivial.

**JESSICA:&nbsp;** Oh, oh yeah. Good one.

**JUSTIN:&nbsp;** Yeah. Anything that's just going to shut down the conversation and indicate that like, “I'm not going to spend time on you because you should understand that,” it's just going to be crushing.

**SAM:&nbsp;** Left as an exercise for the reader.

**JESSICA:** But we don't use those words straightforward, easy, just. I mean we're not trying to crush anyone. That's [chuckles]… we don't remember what it was to not know that. And having spent years learning and accumulating knowledge on something like SQL I have no recollection of not understanding that. But exactly like you said, Justin, it is the teacher's responsibility to assume the context of the learner. And hey, as senior developers we get paid pretty well and this is one of the reasons we do. So, we should suck it up and get better at explaining and not ask people to already understand things just because we do.

**CORALINE:** There's a book that Dave Hoover wrote called 'Apprenticeship Patterns' and he co-authored it and I do not remember his co-author's name. And I apologize for that. But he talks about a boxcar, something called boxcar theory where the best person to teach an early career developer is someone who is three or six months ahead of them. And so on up the chain. Because they still have that memory of what it was like when they were first learning, “Oh, what is Active Record all about?” or you know, “What do I do in a controller?” And they have that empathy still based on their recent experience and their recent memory and that they become the better teacher than the senior person who has, whose experience is so far in the past that we can't really recall what it's like to be a beginner anymore.

**CHUCK:&nbsp;** I think the same idea is put forward in 'Pragmatic Thinking and Learning' by Andy Hunt. And he basically says that somebody who is basically the next level up the chain in the Dreyfus model is the person that can explain it better. Because their understanding is closer to what the person who's trying to learn it has. And I think it's the same idea, just framed a different way.

**JESSICA:&nbsp;** There's an important implication of that which is if you've been learning programming for three or six months then you are the best person to teach that person who just walked in the door. So, everyone is the best teacher for somebody.

**CORALINE:&nbsp;** And that really emphasizes the fact that to be a good developer you have to be a teacher. And it doesn't matter what level you are. Teaching is an essential skill for all developers.

**SAM:&nbsp;** Wait, are you implying that as a senior developer my job is not just to crank out code faster than anybody else can?

**JESSICA:&nbsp;** Hey, even coding is teaching the computer how to do something.

**SAM:&nbsp;** Or more importantly teaching the people who come after you to maintain it. How to maintain it [chuckles] and why you did it that way.

**JESSICA:&nbsp;** [Laughs] Yeah.

**JUSTIN:&nbsp;** We actually just had a conversation about this at work where we were trying to figure out, what are some of these responsibilities that you have that you may not be thinking about as you grow through your development career? And one of the things that we were talking about as interesting was that even as you're growing as an individual developer you're growing much, much more as a teacher and as a communicator. And that there was a question that we still don't have a great answer to, but is there a role for somebody who is a fantastic developer but is not trying to improve their communication, like their teaching skills, those kinds of things.

**JESSICA:&nbsp;** Is that a rock star ninja?

**JUSTIN:&nbsp;** Yeah. [Chuckles]

**SAM:&nbsp;** Architect.

**CHUCK:&nbsp;** [Laughs]

**JUSTIN:&nbsp;** Or the, yeah, the architect that sits in their office all day drawing up diagrams and that kind of thing.

**SAM:&nbsp;** Yeah. Yesterday, at least yesterday as of when we recorded this, Brandon Hays posted an interesting thing on his blog called the conjoined triangles of senior level development. And it's all worth reading the whole thing. But he talks about different components of the responsibility of a senior as being, he has this Venn diagram of connectedness, leadership, and technical capability. But even that doesn't capture everything he was saying so just go read the blog post. I'll put it in the show notes. But yeah, I thought it was a really interesting take on not just being technically competent. Going back to that Venn diagram though, he has the intersection between technical capability and leadership as architect. But left out of that part is all of the stuff under connectedness which is like mentorship, honesty, empathetic development, [laughs] all that other stuff, which is why I sort of [inaudible] said architect. But, yeah.

**CORALINE:&nbsp;** Are there still architects?

**JUSTIN:&nbsp;** I think it depends on what you mean by an architect. It's probably maybe not somebody that just sits in their office and draws diagrams all day but somebody who talks to all the various teams that are working on all the different things and can kind of create a mental map of everything that's going on. And to be able to communicate out areas where there might be redundancies or areas where there's stuff that's working really, really well that should be brought to another part of the team. Or somebody who just has a more bird's eye view of the system.

**CORALINE:** That's true. Sam just pointed out in the chat that the question “Are there still architects?” indicates membership in the startup age culture. I did work at one big company in the last seven years and they were definitely not startup-y. They were very corporate-y. And every team had an architect. So, I guess there are still people with that job title. And that used to be a legitimate aim. That used to be a legitimate career path for developers. Like…

**SAM:&nbsp;** Ouch!

**CORALINE:** I'm a senior developer architect. And we seem to be moving away from that.

**JESSICA:&nbsp;** Or we personally are moving away from enterprise jobs and into Silicon Valley jobs.

**CORALINE:&nbsp;** Yeah. I would argue that architecture is being democratized for better or for worse. We are all becoming architects.

**JESSICA:&nbsp;** And operations and security.

**JUSTIN:&nbsp;** [Inaudible]

**CORALINE:&nbsp;** [Inaudible] generalized.

**JESSICA:&nbsp;** Which just makes things incredibly more harder for new developers.

[Laughter]

**SAM:&nbsp;** Totally.

**JUSTIN:&nbsp;** What I've seen is at the companies is more of this pushing decisions to the people best suited to make them which are typically front line developers, that kind of thing. And so, in that sense you might not have an architect who can dictate a direction. There's a little bit more of this communicating why it's the right way to go, soliciting input from the people that are actually working on the, actually building the tools and software and that kind of thing. And then leading the change more than it is pushing the change.

**CORALINE:&nbsp;** How well does that work? And I am famously critical of Agile methodologies because I think that thinking in two-week increments is stupid. And not planning beyond the next two weeks is stupid. So, how well does that work under those circumstances when they're like, “This is the best possible solution that I can create in two weeks”?

**JUSTIN:&nbsp;** I think that it's where some of the role of an architect or somebody that can take a step back and say these are, these little, these steps in different directions, now what does this look like? How does this all fit together? And is it worth even trying to make these things fit together? What's the value that we're trying to get out of an overall system design? And finding the places where you can put the most value into that. And then trying to get everybody else on board with that.

**CORALINE:&nbsp;** But whose responsibility is that now?

**JUSTIN:&nbsp;** And so, that's where I do kind of see the role of an architect in even some of the more modern companies that are starting up.

**JESSICA:** I see the role of architect as someone who has overlap between teams, perspective overlap, and can communicate what they learned from that to the team. And communicate what they learned from their team outward. And it becomes, yes you have a vision. Yes, you're leading people in making the technical stuff better. But more than that you're in charge of having a broader perspective, a perspective outside the two weeks.

**CHUCK:&nbsp;** I think this confusion though over what an architect is and what all the roles are and why do we focus on two-week sprints and all of this discussion that we're having that we've kind of veered off into, imagine how much harder it is for somebody that's brand new to come in. And it's like, “Okay, well then whose job is it to really kind of have that overarching vision?” And if it's not clear, and if it's kind of everyone, then that's that much more that that junior dev kind of has to figure out. “Well, then since I'm not as experienced do I get to talk about trade-offs? Since I'm not as experienced is that part of my job, too? And do I have to learn about that? Holy cow.”

**SAM:&nbsp;** And since I'm not as experienced, does that mean I'm not allowed to pair with a senior person and “waste their time”? [Chuckles]

**CHUCK:&nbsp;** [Laughs]

**SAM:&nbsp;** Which is a common anti-pattern.

**CORALINE:&nbsp;** I think a lot of it comes down to context, too. We hand an early career developer this, “Oh, you're going to build this widget and you have two weeks to build it and we don't have time to explain to you why it's important or what it's going to be used for. You just need to crank out this code and make it work.”

**CHUCK:&nbsp;** I can't imagine why they would fail if you do that.

**CORALINE:** One wonders.

**SAM:&nbsp;** I'm curious about this existential crisis.

**JESSICA:&nbsp;** Okay, yeah, yeah. So, I'm wondering. Justin, do you have an opinion on the existential crisis of software development as in where we have to let go of having control over the computer and actually ever getting our software right?

**JUSTIN:&nbsp;** Absolutely. If you look at what a lot of newer developers are talking about or frustrated with, there's a lot of this, “Okay, well I started learning how to do unit testing or TDD and then I saw a RailsConf talk where we were talking about how TDD is dead. And then I started trying to figure out, okay, well what about integration testing? Well, then I started reading a blog post about how we shouldn't integration test because they're flaky and…”

**SAM:&nbsp;** They're a scam.

**JUSTIN:** “Take time.” And yeah, exactly. And so, at that point you're just completely lost. And it's like, “Should I even bother learning anything because I'm not going to be doing it right anyway?” And I think the development community is famous for just conflicting arguments that it's really difficult for even experienced developers to really justify one side or the other fully. It's more of a, “Okay, yeah. Kind of both.”

**CHUCK:&nbsp;** I think you should integrate your units end-to-end in your tests.

**JESSICA:&nbsp;** [Laughs]

**SAM:&nbsp;** So, I…

[Chuckles]

**SAM:&nbsp;** At the risk of talking that list of things that a new developer needs to know and making it even longer, I feel like maybe we should add a basic course on rhetoric to teach people how to be persuasive and how to understand how to make arguments well and acknowledging those arguments where they are uncertain of things. Because that's something that developers are famously not good at. [Laughs] Yeah.

**CORALINE:&nbsp;** I don't think you presented your case well, Sam, and I disagree with you.

**JESSICA:** [Laughs]

**SAM:&nbsp;** Well, that's because you're wrong.

[Laughter]

**JUSTIN:&nbsp;** There's something. I think it's called the psychology of small differences or something like that where the smaller the difference between two positions in an argument, the stronger the argument or the more vehement the argument. And so, you tend to see the biggest arguments around things that in the end don't really matter all that much.

**SAM:&nbsp;** There's an Emo Philips joke about that, too.

**CHUCK:&nbsp;** We've been talking a lot about senior developers and architects and people higher up in the chain and what their responsibility is here. But I wonder sometimes if we don't talk enough about the responsibility of the students as well. So, the newer people, what can they do? Or what should they be doing in order to take advantage of this or to help the senior people or architects or whoever it is that they've got to learn from and pick this stuff up from to help them. And how can they apply themselves to learning so that they can learn the things that they need to in order to contribute?

**JUSTIN:&nbsp;** Ask lots and lots and lots of questions. As I've grown more senior in my career and as a developer, the more I realize that part of my responsibility is to ask the obvious questions and to ask the questions to which the answers may seem obvious or where everybody is kind of scared to ask them because they're afraid of not looking smart.

**JESSICA:&nbsp;** Yeah. You can always, you can always phrase it as checking assumptions. It's great to check assumptions. And you can think of an obvious question that way.

**SAM:&nbsp;** Ooh, I like that. I'm stealing that.

[Laughter]

**CHUCK:&nbsp;** Stolen. Gone.

**CORALINE:&nbsp;** Another thing I do with some of the young women that I mentor is I make them read the API and practice the API because something that you said earlier, Justin, about like, “Oh, I've seen this problem before,” sometimes even if you don't remember the syntax just knowing that, “Oh, there's a method on Enumerable that does exactly this thing that I need to do right now,” can be really valuable in getting unstuck.

**JESSICA:&nbsp;** Oh yes. Like if you're learning to cook, go taste all the spices. So you know what your options are.

**CORALINE:&nbsp;** Yeah, it's very much like that.

**SAM:&nbsp;** That's an interesting analogy. Yeah, I think back when James was on the show he at least one time, he mentioned that as being his sort of secret weapon is when everybody else stopped reading after the first part of the Pickaxe he started reading in the API documentation. And he's able to pull a lot of tricks out of his sleeve because of that.

**JUSTIN:&nbsp;** Another thing I think is investing the time upfront in figuring out how to recover when things go wrong. Because that's going to give you, once you start to really understand some of that, that gives you the confidence to try new things and to push the boundaries of your knowledge. And one of the things that I like to spend lots of time on with new developers is teaching them how to explore the system, how to debug, how to read stack traces, how to figure out what an error message actually means without just trusting Google every time.

**CORALINE:&nbsp;** Yes.

**JESSICA:&nbsp;** Ooh.

**JUSTIN:&nbsp;** And an investment in that means that you can kind of let them go off and play for a little bit longer and they're not going to worry that they're going to break things irrecoverably. They're… they have a little bit of a chance to recover before they can come to you and say like, “Hey, I'm stuck. Can you help?”

**JESSICA:&nbsp;** Yeah, stack traces look scary. But oh my god, stack traces are the best thing ever.

**CHUCK:&nbsp;** [Laughs]

**JESSICA:&nbsp;** I remember going from C to Java and the stack trace was like, “Aah, I can see what called what and what and what and what and what.” And sometimes I just look at the stack trace even after I figured out the problem just because oh, you can see the invisible structure of the program sometimes in those. Oh, they're gorgeous.

**SAM:&nbsp;** Totally.

**CHUCK:&nbsp;** Yeah. But sometimes back traces do cause seg faults for our new people in their brains.

**JESSICA:&nbsp;** Yeah. They're scary.

**CHUCK:&nbsp;** Yeah.

**JESSICA:** At first. I mean, until you've already become accustomed to C error messages which are just as terrible except no information.

**CORALINE:&nbsp;** Somebody wrote a gem a while back that would actually read the last line of a stack trace out loud using 'say'.

[Laughter]

**CHUCK:&nbsp;** Awesome. Alright, I have to ask this question. David was tweeting at me this morning when he said he couldn't make it on the call. And we've been talking about asking questions and finding solutions. But sometimes we get hung up on asking the right questions because we don't realize we have a blind spot there. And so, we just kind of pass over it when we should ask a question. And his question is how can new developers obtain objective evidence of their blind spots? For example, if you don't know how badly you can't estimate, how to rigorously approach estimation.

**JUSTIN:&nbsp;** That's a good question. I've seen it be successful just checking your assumptions with people. So like, “Hey, this is what I came up with. How does it sound? Am I missing anything?” Some of it I think is also just getting in tune with yourself when you start to feel like maybe this doesn't feel right, or even in my limited experience I think that there might be something going on here that I'm not quite sure about. And sometimes, and I've experienced this myself, like when I don't know if something is going right and I can't even explain why it doesn't feel right, just going to somebody else and saying, “Hey, this doesn't feel right. I'm not exactly sure why. Can you help me out?” and they'll be able to just get it right away.

**CHUCK:&nbsp;** Yeah. But isn't a blind spot somewhere where it does feel right even though it may not be?

**JUSTIN:&nbsp;** Sometimes. But I mean, that's kind of where I think combining that with also just making a habit of checking your work with somebody that is, it doesn't even have to be somebody more experienced than you because we all have blind spots in completely different places.

**CHUCK:&nbsp;** Okay, I'm going to throw out the rest of his question then, and then we can move on. But he also said, also do we have a confirmation bias that our spots are not blind? Will we resist evidence to the contrary and how do we notice or overcome them? In other words, I think what he's asking is, “So, we assume we don't have a blind spot in an area and that gives us a confirmation bias that nobody calls us out for it. So, we must not have a blind spot there,” where in reality we probably do. I guess I kind of already asked that. But do we resist evidence to the contrary? In other words, when people tell us we're wrong do we tend to put up our back and say, “No, I must be right”? How do you get past that?

**JUSTIN:&nbsp;** Yeah, I think that's super common. I can't count the number of meetings or conversations or things that I've been into where me and others around the table are totally convinced that we're right and yet each coming to completely opposite conclusions because we're each missing something that we don't even know we're missing. And that's a hard one. I think that it takes practice in being open to saying, “This is what I think. This is the evidence that I think is leading me to that conclusion. What am I missing?”

**CHUCK:&nbsp;** We're talking about these blind spots in code but it can also be in the way that we interact with people, too.

**JUSTIN:&nbsp;** I see code as also interaction. A lot of the same ideas and things that go into better communication also go into writing better code, because code communicates. There's a book 'The Fifth Discipline' where there was, one of the sections of that that really resonated with me was this idea of balancing inquiry and advocacy. And so, mentally making a switch between, “I'm in discovery mode. I'm trying to learn more about what the truth of the situation really is with the rest of the people in this room,” and then turning that… and then once you feel like there's a good baseline turning that off and then turning your advocacy on and actually trying to come to a decision. And so, I think that that can be kind of helpful for figuring out those blind spots and that kind of thing.

**CORALINE:&nbsp;** There was this interesting study done by a sociologist named Solomon Asch. And I used this in one of my talks. I don't know how well it would come across in text. He would arrange a group, a line of seven or eight participants, and only one or two of them were actual participants in the experiment. The others were confederates. And he would hold up a care with a line on it and he would ask them to study the card. And then he'd hold up another card with three lines on it labeled A, B, and C. And he built it as a spatial intelligence test and would ask participants which of the three lines, A, B, or C is the same length as the line on the first card. He found that if the confederates who would be asked the question first lied about which line was actually the right size, that depending on the group size, up to 40% of the actual experimental subjects would agree with the wrong answer.

So, I can see that happening very, very often with a new developer who has an idea about what something, about what the right thing is but is going to go along with the so-called experts, the more senior people for fear of appearing stupid or appearing wrong. I think conformity is a huge problem. And we should be encouraging junior developers who have new perspectives on things to share those perspectives because they can challenge the way of thinking that we as more senior people have fallen into.

**JUSTIN:&nbsp;** I think that's great context to set with a new developer as they join, is like it is partially your responsibility to check our assumptions because we've been doing this for a while. We're kind of already locked into some of our ideas. And part of the value you bring to the table is your insight, your questioning.

**SAM:&nbsp;** Yeah. I think though you have to be careful with that and how you frame it. I think telling a new person to the team, “It is your responsibility to check our assumptions,” won't go very well unless you also demonstrate that behavior yourself.

**JUSTIN:&nbsp;** Yeah.

**SAM:&nbsp;** Of like honestly questioning your own decisions, demonstrating when you interact with other developers that you can take questions and feedback well. [Chuckles]

**JUSTIN:&nbsp;** Yup.

**CHUCK:&nbsp;** Yes. Yeah, I think the anecdotal story to that is the person who is learning to make a roast from their mom and the mom cuts the ends off the roast and then puts it in the oven. And so, then the mom gets asked why do you cuts the ends off the roast. She says, “I don't know. I'll ask my mother.” And so, they go ask the grandmother, “Why do you cut the ends off the roast?” And she says, “I don't know. Let me go ask my mother.” And so, they go ask the great grandmother and the great grandmother says, “Well, I only had a pot so big. And so, I cut off the ends so it would fit.” And having somebody new ask those questions and then making it safe to get an answer which is what I think Sam was leading toward and also showing that you're willing to ask that question which the mother and the grandmother in this case do, then you find out, “Oh, well we've been wasting the ends of roasts for two generations.” And you make the process better.

**JUSTIN:&nbsp;** I think you touched on safety a little bit. And I think that a lot of what we're talking about kind of all rolls back to that, to making it safe to experiment, to make it safe to learn, to make it safe to ask questions.

**CHUCK:&nbsp;** Yeah.

**CORALINE:&nbsp;** Creating safe spaces to fail, too.

**SAM:&nbsp;** Mmhmm.

**CHUCK:&nbsp;** Absolutely. And I think helping people explore. You know, why did this fail? Or helping people explore, how did you come to the conclusion that you wanted to try this solution? And doing it in a way that it's a learning experience where you're all learning together instead of, “Well, why did you do it that way? That wasn't… we all knew it wouldn't work that way.” I think that's a very healthy way of approaching some of these things. And it's those failures and those trade-offs that we learn when we're new to this that will carry through the rest of our careers.

**CORALINE:&nbsp;** So, we've been talking a lot about the role of more senior developers in helping early career developers along. But what about cohorts of early career developers working together? How does that dynamic kind of work?

**JUSTIN:&nbsp;** So, you worry a little bit about that blind leading the blind kind of scenario. And so, you want to make sure that there is a good path for both of them to grow in a way that takes them towards that path of becoming more experienced developers. But I think that that does help a lot with the idea of safety in that if the person next to you is making mistakes that you can help work through and you're making mistakes that they can help you work through, then it helps you both grow together.

So, one of the more interesting things that I have learned through the stuff that challenges me and helping other people through the challenges that they run into is that there's a big difference between the difficulty of something and the scope of something. I found that the difficult small scope things are just energizing. They're fun, even if you're bashing your head against the wall. You know, you have that confidence that like, “Yeah, with enough time I can finally learn that.” When it comes to difficult big scope or even easy and big scope, that's when you start getting that crushing feeing, that overwhelming feeling, that, “Where do I even start?” feeling.

And so, like I mentioned that big octopus-like diagram way back in the beginning and one of the bits of advice that works well for that is just like, “Okay, well pick one branch and start learning it.” Probably something that's blocking you from getting more work done because that will make you even more motivated to keep working on it. But really, each of those branches that you start getting well in or getting good at will eventually end up reinforcing other branches and reinforcing other branches until eventually you have some sense of everything that you need in order to successfully build an app. And so, I guess part of that is also prioritization which is just asking yourself, “What's the next thing?” Not thinking about everything, but you know, what's the next thing?

**SAM:&nbsp;** Mm, yeah. So actually, on that note, one of the questions that I've learned to ask is not “What's the next thing?” but “What's the highest risk thing that I can do next?” [Chuckles] Otherwise I find I have a tendency to go off into the weeds and like polish one little corner of the application. And then leave this giant looming question until it blows the deadline.

**CORALINE:&nbsp;** Always do the hard stuff first.

**SAM:&nbsp;** Yeah.

**CHUCK:&nbsp;** If you're doing that though, how do you keep from getting discouraged that all of the stuff working on at least for the first while is hard?

**JUSTIN:&nbsp;** I think it's still that focus of if this is too hard and too big, then can I make it hard and smaller? Can I make that hard and smaller? Until eventually yeah, it's going to be a lot of hard things but they're going to be things that you're pretty confident that with enough time you can do and that it will teach you something while you're doing it.

**SAM:&nbsp;** So, it sounds like maybe part of that is figuring out how to tell yourself, “Yes, this is hard. But no, it's not what I'm doing right now”?

[Chuckles]

**JUSTIN:&nbsp;** Yeah. I'm a big fan of the, “I'm not going to do this list.”

[Laughter]

**SAM:&nbsp;** I like it.

**CHUCK:&nbsp;** Boy in business, that's a big deal. Alright, well anything else before we go hit picks?

**SAM:&nbsp;** You know, I was thinking back to how I've learned things over my career. And this maybe something that doesn't apply to everybody and their different learning styles but one of the things that I've found over and over again is that as I'm trying to make sense of a new concept or a new field I can learn some facts about them and I can try to memorize and regurgitate those facts. But it doesn't ever really click until I find a theory or an explanation or a perspective behind it that gives that, all of the facts, a structured to hang onto. And so, even if I misremember or forget a certain fact, I know approximately where in that space it is and I can go looking for it again. Is there a way that we can remind ourselves to do that or that as senior people we can help new early career people with?

**JUSTIN:&nbsp;** I'm a big fan of examples in general because I feel like seeing enough examples you can start to mentally create a space that you can extract some of those models out of. Also, just like learning other things in general and encouraging learning about anything and everything gives you a wider variety of mental models that you can start to say, “This kind of parallels this thing that I've already thought of,” or, “This kind of matches this thing that I learned a while back.”

**CORALINE:&nbsp;** One of the things I do too with the people I mentor is I ask them to write down in a journal every Google search that they do and the result that helped them the most with that Google search. So, they have the additional memorization activity of actually physically writing it down and they also have a reference of, “Oh, I've done that before and I have that right here.”

**SAM:&nbsp;** You mean, on paper?

**CORALINE:&nbsp;** On paper.

**SAM:&nbsp;** [Gasps]

**CHUCK:&nbsp;** Tree pulp. Wow. I actually really like that idea.

**SAM:&nbsp;** Yeah.

**CHUCK:&nbsp;** Not just for junior people either.

**JUSTIN:&nbsp;** Yeah, there was a talk on onboarding that I saw at a RailsConf a couple of years back that recommended that, of as you start a new job, start a journal. And as you're hiring new people, talk to them about starting a journal where they write down all of their thoughts, all their findings, some of the notes from some of the conversations that they have, and just so they can both see that continual progress that they're making as they get used to working in a new environment. And also so that, “Hey, that one command line that everybody has memorized to deploy, it's right there.”

**CORALINE:&nbsp;** Yeah.

**SAM:&nbsp;** Nice.

**CHUCK:&nbsp;** Alright. Well, things seem to have wound down a little bit. So, let's go ahead and do some picks. Coraline, do you have some picks for us?

**CORALINE:&nbsp;** I have a couple of picks and they are both emoji related. I should go on the record and say that when 'emoji' first came out I hated them and thought they were stupid. And now, I kind of rely on them for nuanced conversation.

So, my first pick is an application called emoj, it's E-M-O-J. It is a Node app created by someone who calls themselves Sindre Sorhus which cannot possibly be their real name. It lets you find emoji from text on the command line. So, you merely type emoj and then a string like I love unicorns and it will spit out emoji related to the text I love unicorns. It is a GitHub project that's really lightweight. And it's really interesting. I did a little digging and it uses something called the Dango API. And in looking up the Dango API I found this article called 'Teaching Robots to Feel: Emoji & Deep Learning'.

So, Dango is a project that they fed hundreds of millions of real world cases of emoji and use machine learning to distill it down to a tool that was small and fast enough to predict emoji for you in real-time. And the best example of this that I found was if you type… and the article has an interactive dialog box on it so you can actually try it out. If you type Beyoncé into the little dialog box it gives you a crown and a bee because she is queen bee, which I thought was like amazing. And it's not just one to one meanings of oh, this emoji means heart. It's like combinations of emoji and it's actually learning cultural meanings of combinations of emoji whether or not they're recognized as individual symbols. So, what a really, really cool application of machine learning. And a nice documentation of pop culture and how we're using emoji in pop culture. So, I thought that was absolutely fascinating. So, those are my two picks.

**CHUCK:&nbsp;** Alright. Sam, what are your picks?

**SAM:&nbsp;** Well, let's see. I'm going to start by plus one-ing Coraline's pick from last week. She recommended 'The Lies of Locke Lamora'. And it sounded fun so I read it over the weekend and it was a fun little caper. I quite enjoyed that.

The other thing I'm going to pick, I have a bunch of books listed here but I'm going to pick something slightly more practical in some sense, and that's Gorilla Tape. Sort of a product plug but Gorilla Tape is essentially duct tape but way more so. It's considerably thicker and the adhesive that they use is much stronger. So, I found that in applications where duct tape has worn off after six months or a year that Gorilla Tape will just keep two things stuck together that I wanted stuck together and it will do it for a very long time. And it's fun to work with. So, them's my picks.

**CORALINE:&nbsp;** We should actually point out that Sam's hat is currently secured to his head using Gorilla Tape.

**CHUCK:&nbsp;** [Laughs]

**SAM:&nbsp;** Yes. I was planning to shave later today but this will be so much more efficient. [Chuckles]

**CHUCK:&nbsp;** I thought that was a stripe on the hat and sideburns. But alright. I've got a couple of picks I'm going to throw out here.

While I was in Chicago this week we went to a place called, I'm not sure if it's Portillo's or Portillo's.

**CORALINE:&nbsp;** Portillo's.

**JUSTIN:&nbsp;** Portillo's, yes.

**CHUCK:&nbsp;** So good. So good. I had me their Portillo's beef hot dog and a chocolate cake shake. [Chuckles] It's was so good. I got to hang out with some cool folks like Ray Hightower and Corey Haines and Ryan Francis. So anyway, thanks to the folks that came out for that. It was a ton of fun.

I also while I was out there I wound up getting an iPad Pro with the keyboard and the Apple pencil. And I have to say that it was really nice to just have the one small thing to carry around with me during the conference. I was at Podcast Movement. I could just take notes with the pencil which was also really nice. And so, I'm going to pick all of those things. And then I got an app, I think it's called GoodNotes. I'll put a link to it in the show notes. But basically what it does is it actually evaluates your handwriting in the notes and you can actually do a full text search on your handwritten notes which is really awesome. And anyway, so that was just terrific at the conference.

And then of course I'm going to pick Podcast Movement as well. Really enjoyed it. Learned a ton of stuff and I'm looking forward to next year, which will actually be in Anaheim, California. So yeah, so those are my picks. Justin, what are your picks?

**JUSTIN:&nbsp;** My first one is a book called 'The Principles of Product Development Flow'. It takes all these ideas about creating software and product from things like Agile and Lean. And it actually uses math and queuing theory and explains why a lot of those ideas work. The writing can be a little bit dense especially starting out but you get used to it pretty quickly. And I found it absolutely mind-blowing to read and totally changed a lot of how I think about that stuff.

The next is a guide called 'How to Write in Plain English'. We talked a little bit about communication and this is a short guide that helps you learn to write more clearly and in a more interesting way. On the downside it makes you way more sensitive to all the business speak that you see all over [chuckles] the place.

**SAM:&nbsp;** That's a downside?

**JUSTIN:&nbsp;** [Chuckles] I mean, yeah. It definitely makes you cringe when you see a lot of that stuff.

**CORALINE:&nbsp;** What's the ask on that?

**JUSTIN:&nbsp;** Yeah [chuckles] god, no. [Laughs]

**CHUCK:&nbsp;** [Laughs]

**SAM:&nbsp;** Thank you and that is the correct response.

**JUSTIN:&nbsp;** Just yeah. And yeah, you should use the guide, not utilize it.

The last one I have is kind of a plug pick for where I work, Avvo. In an industry where it's super common to switch jobs every two years I've been there for nine. And we have lots of devs and product people that have been around for three, four, and five years. It's a great place to be with great people so people tend to stick around. Like I said, we're hiring. And so, just ping me if you're interested in talking more.

**CHUCK:&nbsp;** Awesome. If people want to follow up with you, see what you're doing, bother you on Twitter, what are the best ways to do that?

**JUSTIN:&nbsp;** Yeah, the best way is definitely Twitter. I'm @JustinWeiss. That's W-E-I-S-S. And if you're ever in the Seattle area just ping me. I'm always happy to meet up for coffee, chat about programming, and other various things.

**CHUCK:&nbsp;** Very cool. Well, we'll go ahead and wrap this up. Thanks for coming and we'll catch you all next week.

**_[Bandwidth for this segment is provided by CacheFly, the world's fastest CDN. Deliver your content fast with CacheFly. Visit C-A-C-H-E-F-L-Y dot com to learn more.]_**

**_[Would you like to join a conversation with the Rogues and their guests? Want to support the show? We have a forum that allows you to join the conversation and support the show at the same time. You can sign up at RubyRogues.com/Parley.]_**


