# AI without tears

```{abstract}
Discussions are ongoing on adding AI guidance to the Rubin Developer Guide.
This technote has some framing thoughts and suggestions to inform the debate, based on running a team with a wide variety of views and practices on the matter.
It is not policy, nor is it intended to be - the views are the author's.
```

```{note}
This is an informal discussion document. Semantic shortcuts (like sometimes referring to AI agents as Claude because mostly that's what we use) are aplenty. Suggested dev guide content is at the end, but this is one situation where I'd say don't skip all the verbiage to get to it - the how and why matters as well as the what here.
```

## First, let's stop losing our minds over this

It's been a long time since a topic has set Slack on fire like this (maybe even from before we used Slack).
I think we all recognize that this is an issue where reasonable people can differ, but here is a quick round of hot buttons that it can help to recognize when arguing with your coworkers.

This section also serves as a primer of what I feel should be in or out of scope of what the dev guide has opinions on.

### Not everybody thinks like you

Because this type of tooling is so enmeshed in the workflow of the people who use it, it really highlights differences in how people work.
A person with certain subtypes of ADHD adores getting an AI-generated stub to work on, even if it's lame/rubbish and needs total rewriting, because it jump-starts them over the executive dysfunction they experience when starting difficult tasks.
A person with more OCD tendencies is utterly infuriated by aforementioned lameness/rubbish and doesn't want it polluting their clarity of thought.

Use Claude.
Don't use Claude (exception coming).
Use it at the beginning for whiteboarding.
Use it in the middle for templating.
Use it at the end for troubleshooting.
It doesn't and shouldn't matter.
Only what you git commit matters.

To me, this is the same as remote work: some places have policies on this, but I don't care whether people work here, there, or on the beach - their work speaks for them regardless of where their butt sits.
Focus on the outcome, not the method.

_How people use these tools in the privacy of their own laptop should be out of scope for policy._

### Put the non-work issues aside (or at least try)

There are obvious social impacts of this technology.
These, understandably, often come with loaded emotional context, of the "will entry-level jobs be replaced by the time my kid reaches workforce age" variety.

I am obviously not saying you should ignore these issues (in fact please don't) but their merit in a work context is actually limited.
The fact that I frequently fly transatlantic does not mean I don't care about the carbon dioxide level in the atmosphere; perhaps I don't, or perhaps I believe the correct solution to the problem requires other action besides never seeing my family again.

The main problem with being unable to separate work and social context is that negative emotions bleeding through to work interactions are unhelpful.
We're all feeling the uncertain impact of this technology enough without someone piping up "well when AIs nuke the planet..." while I am reporting on a Claude code analysis as input to the potential adoption of a codebase.
Mate, I can't do anything to stop AIs nuking the planet right now, but I can definitely save a day of high-quality engineering effort by asking Claude to do this task.
Yes, I am aware of the moral weakness of this position, but it's also pragmatic.

_Focus on how the tool is being used in the work context and avoid general doom-mongering_

### Software is Legion

Every real software person knows in their bones that software can be many things.
It can be art and it can be science.
It can be a dumb tool or an elegant edifice.
This isn't a value judgment: if you're building an elegant edifice when a dumb tool was called for, I'd like you on my Zoom to discuss how many story points you spent on this.
On the other hand, you'd better not be shipping me some dumb tool that I have to base my entire deployment strategy on.

Specifically for us, our software is often the way we encode what we know - about our telescope, our data, our science and our users.
It's how we know what we know, and how we tell other people what we know, and how we train youngsters on what to know.
If I opened the door to find that an alien, fairy, or Claude had left behind the LSST Science Pipelines, I would not think it's Christmas.
How we have got to this codebase is as important as what it does to the pixels.

Does that apply to any piece of software we write?
No.
Does it apply to any piece of software I am willing to support?
Almost certainly.

_Keep in mind the goals of peri-software activities around any given codebase_

## Towards the dev guide

When thinking about what to add to the dev guide, here are some issues to consider.

### Talk to the hand that wields the hammer, not at the hammer

Agency and responsibility always lie with the developer.
Avoid differentiating between human and agent when you can simply specify the desired standard in neutral terms.
For example, if (as your Lead) I want readable concise commits that capture the motivation behind a change, I don't care if you wrote them or your Claude wrote them.
Either way, it's your responsibility to make sure I get what I ask for.

This is both because it is literally true (if you think Claude output is the same no matter who's doing the prompting you'd be wrong), and because it avoids the kind of micro-management that nobody wants to see in a dev guide.

_Focus on "AI-agnostic" code - ideally, nobody should be able to tell_

### I want to know what you meant not what Claude meant who in any case means nothing

This is the one hill I personally am willing to die on.

When you write a technote, be it a problem statement, a design proposal or an implementation plan, the value of the technote is not merely in the content - it's in telling me how you are approaching the problem.
How you think.
What you really want to do.
Perhaps it is because my team thrives on technical debate, but I need to know I am having an argument with you, not the dog who did your homework.

We have thankfully avoided being the kind of organization that generates paper for paper's sake, so I would like to think that nobody is even tempted to do this, but in any case, don't.
Note this doesn't mean you can't use the tooling to generate references, or do an editorial markup or whatever, but if the semantic content isn't a product of your thoughts, how am I even going to engage with you?
I read documents to get some kind of insight.
If I wanted a Claude answer I would ask Claude, not ask you for a write-up.

Also, I am going to say, it's painfully obvious when you're reading AI-generated content, so it kind of fails the agnostic criterion above most of the time anyway.

_No AI for document semantic content_

### Don't ask a human to review your Claude use

Somewhat related, let's talk about code review.
Code review is one of those peri-coding functions that has a lot of simultaneous goals.
Sure it's an extra pair of eyes on the codebase, but it is also a mentoring tool, a knowledge dissemination exercise, and an enormous demand on the time of somebody technically senior who has a million other things they could be doing.

If you spend a morning doing other things while Claude lined up a commit for you, it seems grossly unfair to ask me to spend my afternoon reviewing it.
And yes, I have seen where this leads - a committer using Claude to write code then a reviewer uses Claude to then review and... people.
We are here to do things together.

Now, by all means feel free to get Claude to pre-review yourself before assigning a human - in fact, if you have a history of being a time-consuming reviewee, please do so, for the love of God.
By the time you are burning human reviewer time though, you better be standing by what you have PRed.
If Claude has done most of the work on your commit, it is _your_ responsibility to review it to the point where you can own it.

_The AI-agnostic way of putting this is to always be respectful of the reviewer's time_

### Wait, you know who can save reviewer time? Claude

No, I have not lost my mind.
I don't mean reviewers should be using Claude for code review.
Rather, AI tools are actually phenomenal contextual linters.
They should absolutely be used to flag issues to the committer before they reach review.

The pricing here can be a bit horrific to contemplate depending on how this is done, but big fan of AI-CI that catches things (like dev guide violations or departures from team-local practices) that would otherwise burn reviewer time.
Even for people who choose not to use AI tooling in their workflow, this is something that it seems a crime not to take advantage of.
This is the most obvious exception to my "eh, don't use Claude if you don't want to" earlier stance.

_Let's write some team- or repo-specific GitHub Actions that catch issues that commonly come up in review_

(This will require money)

### Provenance disclosure

It makes no sense to be a purist on this issue.
Disclosing all use of AI in the production of a codebase will soon make as little sense as disclosing that you used an editor (if we're not there already).
We should trust our developers to understand when it matters and when it does not.

For example, it is not of any actionable value for me to tell you that I got Claude to do a proofreading run of this technote to find all the dangling sentences I littered it with every time I got distracted by Slack.
This is because (a) you should be grateful there are no dangling sentences and (b) whether Claude or my resident pedant pointed them out to me makes no difference to their eventual fix-up.
A disclosure would be an annoying waste of space.

On the other hand, there are situations where agent use is of communicable value.
An example would be "When I self-reviewed with Claude, it suggested lines 135-188 as a potential speed-up of the previous approach. This did speed up the code and does pass all tests, but I am not entirely sure I grasp all the potential impact. Opinions? Agent session transcript attached".
The same lines of code with a simple "speed-up" commit message are clearly... not okay.

This is highly situational, but my own experience is that the times I am impelled to disclose agent use tend to fall into one of two categories.

One is a case where the agent input and/or output could be of interest to you.
For example, if I was evaluating two third-party packages against each other for possible adoption, and Claude decided one of them was not fit for purpose, an illustration of the evaluation prompts I supplied and the detailed response is of legitimate interest in getting you to agree with the quality of my evaluation.

The second case, let's face it, is an honest "eh, it's good enough probably" situation (though you'd better be right that the recipient is okay with "good enough probably" kind of work).
For example if you ask me for a back-of-the-envelope estimate of how many RSP accounts are duplicates, throwing an AI at the question of whether Bob Blum at Rubin is the same guy as Robert Blum at NOIRLab is a good-enough response to a back-of-the-envelope level request.
Note however that this is not an exception to the "stand by your work no matter who did it" rule.
I am standing by my assessment that this approach meets the (in this case low) bar for the work - and if I tell you that we have 5,000 accounts and 15,000 of them are duplicates you can call me a sloppy lazybones and I don't get to say "but Claude said" as an excuse.
Them's the rules.

_Disclose AI use (including prompts and/or transcripts) when a reasonable recipient of your work would judge them to be relevant_

## Adjacent issues

Some issues that go beyond the narrow development process, since we're on the topic.
More general culture points than dev guide scope.

### Parity of access

As a multi-institutional activity, we have ended up with unequal access to AI tooling.
We really should come up with a floor where every developer has a Pro plan equivalent (or whatever) budgeted so we don't perpetuate the current haves-and-have-nots situation.

Requires dollars and management action.

### Abandon the productivity framing

This is a bit of a personal soapbox, but hey, it's my technote and I'll cry if I want to.

AI tools are licensed by commercial concerns who market them as productivity boosters to justify their cost.

First, this is an unhelpful framing that has stoked a bunch of negative feelings towards what are otherwise useful tools.

Secondly, my observation is that this is not really how we're using these tools.
People are using them for ambitious language ports that would otherwise never be scheduled as a priority, or for a bit of extra bling in a UI, or for a less fscked up web search experience, or to catch embarrassing errors before they reach a reviewer, etc. In other words, I see a lot of value-add type of work, and a bunch of reasons to own this framing.

### Don't set the polar bears on fire for nothing

Has anybody had the experience of being on the 4th round of arguing with their agent about something it would have taken a fraction of the time to do yourself? (sheepily raises her hand).

Beware negative effort (rarer now with better models but still happens).
And you do have more than a hammer, so use resources appropriately.
Maybe a local spell-checker is a reasonable thing to run before burning tokens for Claude to tell me that I still don't know how to spell ~Mineapolis~ ~Mineappolis~ Min- oh never mind.

Or maybe I should ask Claude how to get VSCode to reformat my technotes to one sentence per line and set it up once, rather than asking it to reformat my text every time.
In fact, I'll go do that now.

### Look, you're not the only person with the new toy

Nobody needs you to run Claude for them.
If you find a bug, please resist the urge to accompany your report with an "and Claude says the problem is..." - it's kinda annoying.
If I need AI help to root-cause a bug in my own codebase, I can probably prompt it with a lot more context.

In general, your AI is _your_ intern, sensei, whatever.
Don't assume your colleague is going to use it as you would; let them make their own choices.

This example is really very mild as far as obnoxious behaviour goes, to be clear, but remember this is already a topic in which Feelings With A Capital F are involved.
Just the facts and let it go.

### Compliance

Yup so we all are employed at some kind of institution that has discovered (or invented) a compliance requirement, typically using some kind of security policy standing to do so.
Needless to say, people who don't write a lot of code are not going to make people who write a lot of code happy with that kind of document.

As a member of Rubin DM, whenever you encounter this kind of framing, you are encouraged to remind people that we are a multi-institutional activity, and we do a lot of work on public open source codebases inside communities that couldn't care less who Rubin staff are employed by.

Less grumpily, compliance language is incredibly unhelpful without situational clarification.
I could tell you not to use Claude on critical code, but if I don't define what critical code is, you'd be none the wiser as to what that means.

Short of legal constraints (which of course are beyond argument), we want to have our developer guide be determinant of our practices as much as possible, as it's the one thing we all have in common irrespective of who signs our paychecks.
To that end, it might be tactically sound to go into more detail than would be strictly necessary in some areas, such as having a list of AI tooling that does not require any special permission or consideration to use, and using the RFC process to add new ones.

As to the spirit (rather than the letter) of these compliance initiatives, I believe the AI-agnostic approach is largely sound here too.
You wouldn't let Claude check in unreviewed mirror control code written by the marketing department any more than you would let your neighbour's nephew do so.
This isn't a Claude issue, it's a code safety issue, regardless of the source.
Though, granted, it is a lot more possible for you to get code from the crack marketing department that actually will pass tests now.

## Developer guide example draft

You may use AI tools as it fits your working style and to the extent that you feel it adds value to your work.
Use of those AI tools in no way releases you from your responsibility to take due care on the code you commit, understand its consequences and limitations, communicate its intent clearly, ensure it is robust and maintainable, and aligned within your team's technical culture.

Strive to submit code that a reviewer cannot tell (nor has to care) whether it was produced with AI assistance.
This protects everybody's ability to use or not use this toolong to whatever extent they feel appropriate.

*Do* use AI tooling, in combination with CI where sensible, to self-review your code so as to minimize the code reviewer's burden.
If you do use AI assistance to produce code, you should review it with particular dilligence before you submit it for code review - reviews should be a conversation between you and your reviewer, not your agent and your reviewer.

Disclose details of AI use when particularly relevant to the recipient or consumer of the work.

Do *not* use AI tooling to generate semantic content in situtations where your own thoughts and judgment were solicited (the kind of things we write technotes on).

Seek guidance from your team lead on any additional compliance requirements your employer places on AI use.

