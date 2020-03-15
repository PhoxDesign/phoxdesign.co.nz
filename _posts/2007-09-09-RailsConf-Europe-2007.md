---
layout: post
title: RailsConf Europe 2007 Transcript
tags: ruby
---

Geoffrey Grosenbach: I’m Geoffrey Grosenbach, it’s Ruby on Rails Podcast episode number 58, October 2007, more interviews from RailsConf Europe in Berlin. Want to let you know my friend Fabio Akita is hosting a reject conf type conference in Sal Paulo, Brazil November 17th go to rubyonrailsworkshops.com for the details.

All right, RailsConf Europe in Berlin, talking with David Chelimsky, one of the authors of RSpec.

David Chelimsky: Hello. Let me clarify that statement you’ve just made. Steve Baker is the author of RSpec originally, I am the lead developer and one of the core maintainers of it now and have been for over a year, but the original authorship. Just want to give credit where credit’s due.

Geoffrey: Great clarification and Aslak Hellesoy also…

David: Aslak and Brian Takita. Dave Astels worked on it a lot early on but he hasn’t in a while and if you go to the RSpec… rspec.rubyforge.org and look for the community page, you’ll see well over forty other contributors which we’re pretty excited about.

Geoffrey: Now, personal plug here: I did a couple of PeepCode tutorials on RSpec which you helped out with a little bit and they’ve gone absolutely nuts, I mean I was really surprised at the level of interest… a lot of people want to learn RSpec. You taught a workshop on Monday and I heard it was just packed: did you find it was a lot of people who had tried it and wanted to find the details, or learning it for the first time?

David: It was kind of about 50/50. We asked at the beginning who had been using RSpec and about half the people raised their hands.

Geoffrey: OK.

David: It might have been a little bit more but it wasn’t the whole crowd. Some people were just there because they had heard about it and wanted to find out what the deal was.

Geoffrey: Now, early on there were quite a few changes, iterations, syntax changes…

David: Uh-huh.

Geoffrey:...but it’s stabilized a lot now and…

David: See that was back when it was beta software.

Geoffrey: Yes. You’re allowed to do that.

David: Well not only are we allowed to do it but everybody is and so, there’s this thing like Edge Rails people know this, right? You take on this risk and you assume the risk, you know? Until something’s formally released. So yeah.

Geoffrey: Now what’s the plan from here on out… now that it’s stabilized are you forking off some other branches for experimental features or is there a roadmap?

David: So yeah. Well I would hesitate to call it a roadmap because that sounds a little more thought out and formalized, but we have an idea and the idea is that we’ll start using the Linux model for the releases, so…

Geoffrey: Even and odd numbers…

David:...the next release will be 1.1 Now all the stuff that’s in what was the original RSpec framework which we’re now calling the example runner, right because we talk about now descriptions and examples of behavior, so that’s the “it” block, that’s just the terminology that we’re using instead of saying, “Well I’ve got five ‘its’ in my describe!” it’s easier to say, “I’ve got five examples in my description.”

Geoffrey: Yep.

David: Kind of rolls better and so that’s all going to remain stable, that’s not going to change. There will be… I’m sure there will be changes in the future but they’ll always be backwards compatible from here on in. The new piece that we’re adding is the story runner, which is formally RBehave and we’ve merged the RBehave into RSpec.

Geoffrey: And that’s only in the last couple of weeks?

David: It’s within the last month and it hasn’t been released yet.

Geoffrey: OK.

David: And so we will release that and that’ll be the 1.1 release with the story runner included, so the thing that we’re not sure about with that is… we want to be able to say, “Hey, the story runner is experimental, use at your own risk, but the other stuff is solid and you should use it,” and I’m not quite sure how to message that with a version number. But we don’t want to break the frameworks apart. The whole point of merging it in is because we want it to be one cohesive BDD framework.

Geoffrey: That makes sense, you know: up until now there are the core elements: user should be valid, all these kind of things, and you can do model tests and controller tests and yet people have said, “Oh, well how am I going to test the entire or specify the entire stack all the way through?” so that story runners are going to fulfill that kind of a need.

David: Exactly, exactly. And so before story runner, before RBehave existed, you know I was always either using something like Selenium or Water to do in-browser testing or Rails integration test or some combination thereof. So we definitely wanted to have a piece that could fulfill that role inside RSpec.

Geoffrey: Now I was going to ask Jay Fields this, maybe I’ll ask him also, but he… for under test unit he has a very specialized system which I have been using a little bit of in some of my legacy tests, where he actually loads up an ActiveRecord connector that will throw an error during unit tests if you even try to touch the database. For RSpec it’s kind of flipped, it’s acceptable to use the database in unit tests but encouraged to mock or stub in controller tests, how did you come about that philosophy?

David: Well, there’s a couple of different schools of thought about how to deal with models and one is that it’s a unit test so you shouldn’t touch the database and that comes from the sort of more classic TDD approach about unit testing. And so… the other thing is, the other view is that you should be mocking out layers and layers and layers of the library that you’re using, and in order to… in order to spec out models that have associations and never touch the database, you have to recreate a lot of stuff in the form of mocks that exists in the Rails framework and not in your application.

So there’s a perspective that says, “You shouldn’t be doing that because that’s someone else’s world. You shouldn’t be messing with that.” The risk associated with that is that their internals can change and now you have to change everything in your application when you take on a new release in your tests.

The thing that Jay is doing is making sure that everything runs really fast. There’s a trade off that you have to take. The trade off is that either; things are a little bit brittle, and everything runs really fast. Or things are a little less brittle, and things run a little bit slower. He’s taking the side of: “I want things to run fast”, because he’s working on big teams with huge amounts of code, a lot of people who have to deal with that code.

Geoffrey: Brittleness may be less of an issue because with a big team, you have to have a real firm plan going into it. You may not be doing massive changes.

David: Well, no.

Geoffrey: Maybe that’s not the issue.

David: This is an interesting thing. People get really freaked out when they have to change their tests when they change their code.

Geoffrey: Yes.

David: And that’s something that’s never bothered me. I think what that comes from is the notion that the definition of refactoring that we work with. When you’re refactoring, you’re changing the structure of the code without changing the behavior. Now we start talking about behavior driven development. It’s all about behavior. I think there’s an unfortunate connection that’s made there that says, “Oh, well if I’m doing BDD, then I never have to change my tests if I change any of my code.”

Geoffrey: Yes.

David: Now you shouldn’t have to change any of the high level tests, like the integration tests, if you’re changing stuff under the hood. But, if you’re changing API’s of objects, then…

Geoffrey: Then it makes sense.

David: Then it makes perfect sense that you’re going to have to change the code that goes along with it. I think it’s great when you can minimize that, but I think having a goal of never having to do it ever is just unpragmatic.

Geoffrey: Well thanks for the thoughts.

David: Yes, thank you.

[new segment]

Geoffrey: Here at RailsConf Berlin; very secret interview with Dave Troy about special projects. Tell us about it: Twitter Vision.

Dave Troy: Yes, well, what we did—Twitter Vision is something that we put together back in about March. Right around the time the Twitter was starting to take off, right around south by southwest, that sort of thing.

It’s a visualization of all the traffic going through Twitter on a Google map. We have both the Google map version as well as a 3-D version. The visualization itself isn’t what’s cool. What’s cool is you can actually see what people are thinking around the world in real time. So we just see if we have Tweets popping up here from Florida, we see something pop up from Italy, France, or South America, etc., the kind of mundane stuff that people tend to twitter about. But you get a real sense for…

Geoffrey: Different languages, Japanese.

Dave: Yes, and what’s going on culturally. And because it’s all real time, usually a minute ago, or less. You can even see breaking news stories spread around the world and that sort of thing. We’ve got some different visualization’s here. We’ve got other features where you can rate which posts you like and stuff like that and create rankings based on all of that. But the cool part is; it’s built in Rails. And it actually uses Twitter’s API. We mirror pretty much their whole database and have these features based on that.

Then I also did another match up based on the same basic underlying engine called Flicker Vision, which let’s you see pictures from around the world. If you look at that, you’ll see pictures from whatever; people vacationing and people taking pictures of weddings. Saturday’s are a big wedding day.

We recently received notification that the Museum of Modern Art is going to be having a big exhibition in New York called “Design in the Elastic Mind”. They’re going to be featuring both Twitter Vision and Flicker Vision for three months starting on February 19th until May 12th. This will be the first time that a rail is out because it’s been put into the Museum of Modern Art.

Geoffrey: That’s amazing.

Dave: And maybe not the last time. You never know how this is going to go.

Geoffrey: Probably wasn’t your goal when you wrote it.

Dave: No. The concept of me having my work in the Museum of Modern Art is strange to me. We’re pumped up, it’s cool.

Geoffrey: Any way you could hook this into the rail’s track and show which patches are being submitted all around the world?

[laughter]

Dave: Yes, actually, we get a lot of requests for things like, “Can you do like a ‘such and such’ vision?” So what we need is a Rails Vision, figure out what the hell’s going on with the Rails community.

[laughter]

Geoffrey: Well awesome. FlickerVision.com and TwitterVision.com or, the Museum of Modern Art in February?

Dave: Yes, exactly. 57th street, stop in and take a look.

Geoffrey: Beautiful.

Dave: all right, thanks Jeff.

[new segment]

Geoffrey: Post RailsConf Berlin. I’m talking here to Nick Sieger. So, on the JRuby team now, you aren’t working for Sun, at least not yet, right? Or did they hire you on too?

Nick Sieger: They hired me on.

Geoffrey: You’re on, OK.

Nick: I’ve been with them since May of this year. Right around the time of RailsConf Portland, actually. I didn’t get hired to work on JRuby, oddly enough, which is not such a bad thing actually. Charlie and Tom, they’re both pretty entrenched engineers on the core code base. I’m along there because I’ve been a contributor in the past, but I see myself as more of an app developer and integrations developer. I view my role in the team, also at Sun, as actually to test JRuby, to stress it out, to makes sure Rails works really well. With it, we’re developing a Rails application at Sun right now, so we’re going to be making use of JRuby in the process.

Geoffrey: Nice. So does that mean submitting a lot of bugs or actually you’ll come upon something and fix it.

Nick: Fixing them too, yes. I do that so that I can make fixes as well. I’m trying to fix things as they come across them when I can.

Geoffrey: Now JRuby 1.0, at one point it was released six months?

Nick: Yes, the beginning of June was 1.0, we had a 1.01 release just a few weeks ago. We’ll probably push some more compatibility releases out and in addition we’re targeting a 1.1 release with a full compiler in run room.

Geoffrey: Now it seems like one of the big things that people are excited about – not only inter-operability with other java libraries – but also deployment and using existing java solutions to deploy a Rails app. What’s the state of that?

Nick: The state of the art there is you can package up Rails apps in a java web application archive, WAR file today, and it works in just about any java app server. At Sun we’re targeting, using that kind of deployment strategy for our app. Basically put it in a WAR-file. We can put a bunch of Rails-apps in a single glassfish application server, and we’re looking forward to the efficiencies of not having to manage big packs of mongrels, especially as you start to run multiple apps at once.

Geoffrey: So what’s up? There’s going to be another 1.1 release coming up in the next few months. What are the plans for that?

Nick: The basic roadmap is a full compiler. Jared started with the compiler for a while now. Charlie has been working on it, and promised to finish it by then.

What that means is your entire Ruby program will be able to be compiled into java byte code. Run directly on the JVM which will have a lot of interesting consequences for performance, for portability, even off the station in some cases. People could use JRuby to compile the Ruby scripts into byte code. Then it would be virtually impossible to go back to the Ruby source. So that’s kind of an interesting application too.

There’s some other things planned, I think, as well. Probably some more compatibility, performance fixes and remember there’s probably a couple other items I can’t remember off the top of my head.

Geoffrey: Well it’s very exciting. Thanks a lot!

Nick: Sure!

Geoffrey: So, RailsConf 2007, Europe in Berlin. So we’re standing here with David Heinemeier Hansson. What do you think of the conference at this time?

David Heinemeier Hansson: I think it went great. I think it’s really interesting how the European conference has a slightly different feel. Of course it’s smaller, but it also has a different feel to it. It’s interesting to see people from a lot of different countries, more so then the US. It’s of course very US-based.

It’s great to hear from people in Italy, people in France, people in Norway, all over the place. I get to talk to people from those countries here versus the US, where I’m mostly hanging out with Americans. So that’s cool.

Geoffrey: Seems like there are a lot of people who came to Portland, and then they also came to here, but of course a lot of just Europeans.

David: Yeah, yeah. There’s definitely people doing both, which I think is actually pretty cool. Unlike a lot of conferences, who are doing like US and EU, our EU conference is actually not just a rehash of what’s going on at the American conference. Which I think is a really big strength. We’re not just recycling material, it’s mostly all new—keynotes, all new presentations and so on. And things move fast enough that six months apart, a lot of new stuff will have come up.

Geoffrey: Now in your keynote, you’re kind of warning people there’s not going to be anything ground breaking. There’s a lot that people have seen, but Rails 2.0 is coming up pretty soon, a little bit of stability for the next few months.

David: Yeah I think so. I think it’s actually good. We’ve fostered a lot of revolutions on people and in a very short period of time in the past. I think it’s good that people get a chance to catch up in some sense.

I think we’ve had a lot of stuff pushed out there that still hasn’t been thoroughly adopted, for example the Rails stuff. I mean it’s been quite a while since we’ve announced it, it’s even further since I developed the first app according to those principles but it’s still not something everybody has picked up. So I think it’s good that 2.0 is going to improve a lot of things. A lot of small things, but it’s also giving people a chance to catch up on the big stuff.

Geoffrey: One last technical thing. I was surprised that you’ve said “Active Resource was never really intended to be used outside of firewalls;” at 37signals you’re using it internally between applications. Initially people were very excited because they thought, “Oh, consume all those remote API’s,” but maybe it’s really there to change the way people design their applications.

David: Well, I think its two fold. It’s in generous for me to say it’s not being used outside because we’re actually exposing something like the Highrise API. Our sample implementations are actually Active Resources, so anybody who want’s to use Highrise will go through Active Resources and that’s a public side.

My own personal use of it is mostly to restructure my applications behind a firewall. So I want Highrise to use the same credit card storage mechanism as Basecamp does. I don’t want to duplicate the code. I don’t want to do plug-ins. I want this to be a separate application. Active Resource really allows you to build a net of applications behind the firewall that you can hook up and share functionality in a really simple and easy to use way.

I think that’s actually where it’s going to have the biggest impact. There’s been web services for a long time, and people are pretty used to using those for consuming external information. Perhaps they’re not as used to re-architecting their internal setups with the webservices. I think Active Resource makes that really easy because if you have Rails all around, you’re already producing XML. Just by making a scaffold application you have something that could be consumed by an Active Resource.

So I’m hoping more people will take that up as their applications grow larger and that they want to separate more concerns and so on and so forth.

Geoffrey: Exciting. We can look for a Rails 2.0 preview release in the next couple of weeks, then?

David: Yeah, definitely. I’m hoping it’s shorter than that. I’m hoping that within the next week or so we’re going to wrap everything up. It’s pretty much there, so you can cheat, and you can download edge as it is. It’s going to be pretty damn close to what the preview is going to look like. When we’re doing the preview, we’re going to do real gems and we’re going do an attack in SVM and so on, and get people ready to jump on 2.0.

Geoffrey: Well thank you. All right!

The Rails Podcast is sponsored by PeepCode Screencasts. There’s a new PDF book on Rails 2.0 by Ryan Daigle.
