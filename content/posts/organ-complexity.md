---
title: "Kidneys are hard"
created_at: 2016-07-28T13:47:51-07:00
kind: article
---

Conversation on twitter:

> [&lt;Fiora>](https://twitter.com/FioraAeterna/status/758704690586460160) random thought regarding http://arstechnica.com/science/2016/07/the-man-who-got-the-first-double-hand-transplant-wishes-he-hadnt/
>
> [&lt;Fiora>](https://twitter.com/FioraAeterna/status/758704840360898562) originally, people thought human tech would be superior to transplants, etc, because Obviously Tech Is Better, sci-fi, etc
>
> [&lt;Fiora>](https://twitter.com/FioraAeterna/status/758704953242161152) then sci-fi types started to realize that biology was really good at what it does and human replacements were laughable try-hards
>
> [&lt;Fiora>](https://twitter.com/FioraAeterna/status/758705029670776833) but the problem is we have no freaking clue how the biological stuff works, while we do understand our shitty replacements
>
> [&lt;Fiora>](https://twitter.com/FioraAeterna/status/758706138061811714) so.... we may end up going full circle back to cyborgs because we suck at biology?
>
> [&lt;yaodema>](https://twitter.com/yaodema/status/758712622309109760) And because prostheses are getting way better. Transplants are terrible, nerve damage is hard to fix, etc.
>
> [&lt;Fiora>](https://twitter.com/FioraAeterna/status/758713108487507970) exactly. even if human organs are way better than artificial ones, we don't understand them enough to use and fix them

This is sorta true. Biology is hard, especially when you want to validate your understanding by actually making functioning things. Transplants are, as in the linked article, kind of hit or miss, and require immunosuppressants and antibiotics (for surgery), which is a bit like having to pump a factory full of chlorine gas before you can fix anything. But I don't know if artificial replacements are so much of an improvement, at least as concerns understanding.

Large parts of the body are effectively irreplaceable for the forseeable future - most obviously, the immune and nervous systems*, exactly the ones an implant most needs to deal with. Given that the implant designer can't design the entire body, the first reason implants (or, it should be said, transplants) are so difficult to design/perform is that their interactions with the rest of the body, especially these systems, are difficult to control. It's not that hard to make a pump the size of a heart, but it's hard to make one that hooks up to the cardiovascular system without something dying, and, at present, impossible to make one that properly responds to nervous signals.

The difficulty of course changes depending on what is being replaced. We can make legs now that are better than real ones in a few aspects. Artificial hands can reach and grasp and are beginning to provide haptic feedback. Hearts are, as mentioned, regulatorily isolated, and only last a few years. Ears are only good enough to make it easier to read lips.

The problem of interaction is one of both physics and understanding. We lack understanding of what nervous signals mean: this is something we can improve and are improving on. (It's something I'd like to help improve.)

But we also lack the _physical ability_ to make good connections. When you insert a neuroprosthetic into somebody, you maneuever a wire or probe into an area that has neurons in it. The probe then mediates some electrical stimulation - emits or sucks in nearby electrons, which hopefully alters the local potential enough that neurons nearby change their behavior in a way close to what we would like. It's hard to understate how crappy this is. The probe has to be designed to do minimal damage to living tissue - damage that's quite easy to do, since living tissue isn't great with electric shocks - as well as to survive itself in an environment few iridium wires have ever gone before. Even when this is accomplished, its actual ability to stimulate is not great, because it can only manipulate the outside potentials.

Humans have, in fact, designed "artificial cochleas" better than any of the signal processing in cochlear implants; but they lack the ability to effectively communicate with spiral ganglion cells, so nobody's getting one in their skull any time soon.

But that's all still, more or less, a technological problem, something we will maybe solve in the future, ushering in an era of slightly less laughable replacements.

So let's ask: why is it that biology is hard, and computers are easy?

The blithe answer is evolution. There has been no selection pressure for humans to evolve JTAG ports for debugging, and so we lack them. There has been no selection pressure to make open heart surgery easy, so it's newer than computers despite that we've had all the tools to open ribcages for quite a while. There has been no selection pressure to make kidneys hot-swappable, so we have to bother with immunosuppressants and all that crap.

This is true but doesn't really answer anything. There might be _reasons_ that the body is as hard to operate on as it is; actual design considerations that could come up even when an enterprising neuroprosthetist decides to redesign humanity from scratch, piece by piece.

When you, or a robot, jogs, on your so-mechanically-interesting legs, the most obvious thing to happen is that the control system (brain, CPU) sends signals to the actuators (muscles, motors) to move in some jogging pattern. This is a process reasonably well understood by roboticists, and robots can successfully walk. The second most obvious thing to happen is that less famous parts of actuators, with obscure names like "nuclear bag fibers" or "Hall effect sensors", send signals back to and through the control system so that the system as a whole can be adjsted to walk better. Roboticists have, as far as I know, a pretty good understanding of this too, and so Boston Dynamics machines can walk on rubble.

The less obvious thing to happen, in humans and I don't think robots, is the sympathetic response. Your brain sends signals down your vagus nerve that hit most organs. Your heart beats faster: obviously. Your lungs reorient to take in more air: no surprise. Your pupils dilate: uh. Your intestines' autonomic peristalsis is inhibited: guess that makes sense. Smooth muscles around blood vessels contract or relax depending on whether they feed your gastrointestinal system or your extremities: okay. Your kidneys secrete more renin: what?

Unsurprisingly, all this is part of a "design" to regulate energy usage, since there's not much call to continue digesting lunch while you're running from the jabberwock. But practically speaking, it means every part of the body has to somehow be informed about a bunch of seemingly irrelevant crap. Kidneys are not just filters: they react to sympathetic innervation, as well as water and sodium levels, and [all this complex stuff that inexplicably involves the lungs](https://en.wikipedia.org/wiki/Renin%E2%80%93angiotensin_system). Pretty much every organ is like this. Even the gallbladder, probably, even though it's mostly just a bag.

So if you want a replacement organ, either you have to fit all those complex interactions into your implant, or you just focus on one thing and abandon the rest. That is to say, replacement organs are not just laughable try-hards because it's hard to make a small pump/filter/whatever, they're laughable try-hards because they can't do everything the original can do. Artificial hearts (and, again, transplants), as mentioned, don't receive vagus innervation and only sometimes** even change their flow rate in response to blood pressure. Dialysis machines are huge and generally make you sit still. Etc.

You may think that this is not so bad. That you can roll this up as a necessary sacrifice in order that we can have some understanding of what the hell is happening. That we can just have our artificial organs do one thing, and do it well.

Does [that](https://en.wikipedia.org/wiki/Unix_philosophy) even work for computers? If you have used a computer for very long, you probably know that the answer is no. Eventually you want emacs or Firefox or to sprint without your muscles slowly dying of oxygen starvation, and suddenly you don't understand anything. Listen: when I leave Firefox on for a long time, YouTube videos don't play smoothly. Do I know what that happens? No. Do I expect to fix it? Ha ha no. Do I expect anybody to fix it? Still no, because I know that the problem is probably a consequence of complex interactions between the memory allocator, SpiderMonkey, systemd, Linux syscalls, my zshrc, my Steam community profile, electromagnetic emanations from the nearby power substation, and possibly even the CPU at some level. I have as much understanding of the problem as I do of cancer. The symptom is obvious, but for the cause I'm left thinking stupid things like "maybe I should upgrade" or "doesn't red wine help with that?"

I think that humanity has not yet come up with a good way to design this kind of system. There might not even be one, for standards of "good" allowing maintenance like you can do on simpler machinery. Consider how hard it is to get a video game working well on Linux, and then imagine how hard it will be to install a Weyland-Yutani lymph node in a body that has original components, a Betacel pacemaker, and kidneys of two different brands.

This isn't to say that implants are inherently useless, or won't get better, or anything like that. I just think that a complex system like the body, individual parts of it, or even my desktop computer, is going to be more-or-less inherently hard to understand.

*: This is a whole other post

**: Wikipedia says that CARMAT, developed in 2008, is the first to do this, but I admit I don't know much about artificial heart design and this may be wrong.
