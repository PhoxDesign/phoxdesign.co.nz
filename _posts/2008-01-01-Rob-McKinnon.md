---
layout: post
title: Rob McKinnon: TheyWorkForYou.co.nz
categories: dev
---

Geoffrey Grosenbach: It’s the Ruby on Rails podcast! I’m Geoffrey Grossenbach, episode number 59, October 2007. I was in London for a few days and got to speak with some local Rubyists, including Rob McKinnon, who is working on an interesting site called, “They Work for You.”

[transfer to London interview]

Geoffrey Grossenbach: So, Geoffrey Grossenbach here in London with Rob McKinnon, who has done some interesting things with government websites all around the world.

Rob McKinnon: That’s right. I moved to London about two and a half years ago, and was inspired by some developer activists here, who have been doing a number of websites. One of them was called theyworkforyou.com, which covers the U.K. parliament. It helps you actually find out what your representative is voting on, and how they voted.

I was quite inspired by this, and wanted to do something to cover my home country, New Zealand. They were using a mix of Pill, PHP and Python. The code-base open source, and it looked like a bit more than I could take on at the time. So, I started a Ruby on Rails site. Mine is the same name, theyworkforyou.co.nz. It lets you know what’s going on in the New Zealand parliament. It’s a work in progress. It’s interesting.

Geoffrey: What does it show? You can see who voted, what they voted on, how frequently, even other commentary.

Rob: Yes. I’m trying to put more focus on the issues, rather than the members of the parliament. One thing that I showed you earlier tonight, was a use of the spy clients helper. That was showing questions to each minister and the frequency of the questions over time. So, you could quickly at a glance look at this index and see if a particular minister was having more questions asked of them this month compared to another month.

It gives you that quick overview of what’s going on, that just wasn’t possible before.

Geoffrey: You started this as kind of a personal thing, but it ended up being fairly influential.

Rob: Well, ah,

Geoffrey: You started redesigning their site?

Rob: Yes. They were inadvertently publishing some metadata, as CSS class names. I found out earlier this year, that they were doing a redesign and that CSS class name metadata was going to disappear. I did an on-line campaign saying that it was actually quite useful and that the public had a right to this data.

My spike lines were going to flat-line if they didn’t continue to publish this. I don’t know if it was me, but, when the new site finally launched, they actually have retained this CSS class name semantic metadata; which has been really good. They have even assigned me a technical contact at the New Zealand parliament now, just if I have any further problems, there’s someone for me to keep in touch with.

Geoffrey: That’s awesome. You see people out on the streets, trying to get signatures. You think of politics happening that way, but here, it’s happening on-line. Even from half way across the world!

Rob: Yeah, the next set of features I’m going to launch are social features. So, you are going to be able to have a user account, say what you are tracking and then see what other people are tracking. Also, the official site is now publishing which companies and people are making submissions on bills. So, you are going to be able to track companies and what they are doing related to their parliament activity.

It’s a whole new game. I think Ruby on Rails being such an easy platform to develop; that rich domain specific applications in, has just made a whole new world of possibilities available to just one developer on his weekends.

Geoffrey: Have you received any objections or hostility toward that, or has it been mostly positive?

Rob: Well, the official, technical side of parliament ignored me for about a year, but now they have realized that this isn’t going away and that it is maybe better to have me as a sort of ally, not an ally, but a partner in the data that’s being published, because I’m able to do new things with the data.

I’ve spoken to a number of members of Parliament in New Zealand when I was there earlier this year. Most of them were quit positive about it, because anything that makes what they do look important is obviously good for them. What did you think of it Jeffery? I showed it to you. What did you think?

Geoffrey: I was impressed. It was very simple and very clean and yet you were able to see actual conversations, paragraphs of things that each of the ministers had said. It was just very straight forward. I think that’s the way it should be. Seems like often, it feels like the purpose of politics is to obfuscate things and make it all so confusing and yet putting it there, clean, simple, what people need.

Rob: Yeah, that’s exactly the aim I had with this website; was actually to lower the amount of time it takes someone who might be interested, just to get to the bits they are interested in.

If you are a professional in the health sector, you are probably interested in what they said relative to the health portfolio. You should be able to get there in two clicks. It shouldn’t take you a long amount of time to get to those little bits you are interested in. I am hoping that will actually increase participation, if you can find those parts that you are interested in.

Geoffrey: You are not trying to push a certain agenda. You are just…

Rob: Oh, of course I am!

Geoffrey: You want to go for Prime Minister?

Rob: No! I really wanted to promote free, open source software and the use of free open source software by government and Parliament. I realize now that the best way to do that is to use it, and get them to use it.

If they are using a website or application that’s built on free open source software, the next time there’s an issue related to that that goes across Parliament, they will have a better understanding of what that means because I can say, “Loo, my site is possible because of this, and might even go away if you pass that law, because…” [laughs]. I think it’s the positive message of what’s possible now because of free open source software, that is one of the main activist points or agendas behind what I’m doing.

Geoffrey: That’s awesome. Finally, technically you use some different ideas, especially the Django community; Adrian Holovaty put some sites together both personally; Chicago Crime. For the Washington Post, looking at US Senators and Congress people and what they voted on. You used some of his ideas for other reasons to setup routes in interesting ways.

Rob: I had the privilege of meeting Adrian at a conference. We showed each other our source code. I was very impressed by the Django routes file. It’s not called routes, but it just seemed very clean and to the point, because the rails routes followed his Ruby code.

I was able to re-factor some common usage patterns into a few helper methods, because I was making heavy use of named routes. My action method names were also the same names as the named routes. Now my file, my routes file looks very much like the Django configuration file.

Geoffrey: This was even before the Rest for Routes were introduced recently, you put this all together.

Rob: That’s right. I decided about two years ago, before active resource was available, yeah.

Geoffrey: Cool. Very encouraging and inspiring to see that happening.

Rob: To audiences in other nations, this thing is happening globally. Nations all over the world and the United States, the Sunlight foundation is doing a lot of websites to help US citizens keep in contact and track what’s going through their system.

We actually had an e-democracy summit in Berlin, a couple of months ago, with people from 11 nations, all doing similar websites and all doing them as volunteers or non-profits. This is a global phenomenon. I think we are really positively motivated and hopefully we will create some positive change.

Geoffrey: That’s awesome. Thank you.

Rob: Thanks.

Geoffrey Grosenbach: The Rails Podcast is sponsored by PeepCode Screencasts. There’s a new PDF on Rails 2.0 by Ryan Daigle, and a screencast about the Git source code control system. Thanks also to Samson Audio for microphones and audio recording equipment.
