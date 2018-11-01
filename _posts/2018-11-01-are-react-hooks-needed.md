---
title: "Are React Hooks needed?"
image: "https://rydel.io/assets/summer_house_1.jpg"
tags: react react-hooks design
layout: post
---

Let's find out why React Hooks have been proposed. What kind of problems they are
going to solve? Are they a solution for root problems or maybe just symptoms?
<!--more-->
Having this in mind I will tell you a story...

## Jack and his fancy summer house
![summer house]({{ "assets/summer_house_1.jpg" | absolute_url }})
Let's meet Jack. Jack have a nice white summer house in his garden. Jack really
like to spent time there. Parties for family and friends are organized there.
Everybody like it. Even special lighting has been mounted to make it look more
fancy - part of the lighting works all night, because why not?

But there is a problem - more and more spiders started to like it too. There is
more and more spider webs. It doesn't look good, furthermore Jack has a lot
of work to keep it clean whenever he want to organize a party.

One day Jack said:

- _This is enough! I have to somehow deal with those spiders!_.

He starts to think about the problem. What might be the cause? Why those
spiders like the summer house so much?! Unfortunately he cannot find the answer,
thus he came up with a great idea -
someone will be hired to clean it twice a week!

Weeks goes by. The summer house is mostly clean. Jack is very happy:

- _Problem solved! This was a really good decision to hire somebody._

Two months passed. Although the summer house is kept clean, he have noticed
another bigger issue:

- _The cleaning guy costs me a lot! What's worse, when I want to
 make a party in other day than the cleaning day I have to pay him extra.
 This is not a good solution._

That is why contract with the cleaning guy has been terminated.
Although Jack is happy right now, because his monthly expenditures decreased,
the problem with spiders is still not resolved.

One day he noticed that someone in the neighborhood built similar summer house,
whats more this one has no spider webs at all! It is nice and clean!
Jack goes to the neighbour and ask:

- [J] _Hi neighbour! I would like to ask about your summer house._

- [N] _Yeah, sure! What about it?_

- [J] _I have similar one like you and I have really big issue with spider
 webs, but as I see you do not. What did you do?_

- _[N] Ah! I have had same problem! I have just bought a special chemical remedy.
 I can give you some to try._

- [J] _Oh! I am really thankful!_

Jack go straight to home to try the remedy. He have been using it for a some
time and it works! No more spiders, no more webs. The summer house is nice and
clean, whats more, the specific is really cheap! All problems solved!

Some weeks have passed. While preparing another party for his friends, Jack
noticed an unpleasant smell. It turned out, that it is the remedy. It makes
spiders go away, because of the smell. To keep them away, it must be used
often, but then the smell is really bad, thus having a party in such a place is
a bad idea, therefore he has to cancel the party.

Jack has been thinking for a couple of days, trying to find the root couse.
During one evening a simple thought came to Jack's mind:

- _What if... What if the problem are the lighting? What if it will be turned
  off at night?_

He deiced to try it. The lighting is now turned off at night.

Next few days have passed. The result? No spiders, no webs, no problem!
And everybody lived happily ever after.

The end

### Conclusion
You might think, why this worked? Well... Spiders where there, because of a simple
reason - food! When light was turned on during night, moths came along to the
light. Where lots of moths are, spiders must appear.

Ok, ok, but why I told you the story? How this is related to React Hooks?

Well...

[RCA] - I encourage you to learn little about this concept.
This can be really helpful.

## Let's go back to React Hooks
At first we should ask one simple question:

**Why they were proposed?**

What does the [Motivation](https://reactjs.org/docs/hooks-intro.html#motivation)
says? Three issues has been raised. The first one says:

<cite>
[**It’s hard to reuse stateful logic between components**](https://reactjs.org/docs/hooks-intro.html#its-hard-to-reuse-stateful-logic-between-components)
</cite>

Surely it is hard task. No one denies it. At the very beginning there is really
good content:

<cite>
React does not offer a way to “attach” reusable behavior to a component
(for example, connecting it to a store). If you have worked with React for a
while, you may be familiar with patterns like render props and higher-order
components that try to solve this. But these patterns require you to
restructure your components when you use them, which can be cumbersome and
make code harder to follow.
</cite>

The next second issue is titled:

<cite>
[**Complex components become hard to understand**](https://reactjs.org/docs/hooks-intro.html#complex-components-become-hard-to-understand)
</cite>

And the following:

<cite>
[**Classes confuse both people and machines**](https://reactjs.org/docs/hooks-intro.html#classes-confuse-both-people-and-machines)
</cite>

What I see here is that key points of the motivation is to somehow fix problems
which are not language related, but.... knowledge related. What knowledge? Let
see...

### It’s hard to reuse stateful logic between components
Surely it is a hard topic. Render props and HOCs are quite good solutions,
but I fully agree with the issue which has been presented during
React Conf 2018 by Dan Abramov - using many of them in single place causes the
wrapper hell. I really like the simplified usage of context provider -
`useContext`. It is really pure and simple.

Ok, ok, but where is the problem of knowledege here? I think that you are very familiar with such a statement:

> Composition over inheritance!

This is very good aproach. It keeps many problems of inheritance away, such as
the _Gorilla-banana problem_, which simply says:

> What you want is just a banana, but what you get is banana holded by a
> gorilla and the entire jungle.


But as all in development, there must be a big **BUT**. Surely it is.
The issue here is that composition can be used as same badly as iheritence.
For example - we want to use multiple functionalities which are not related to
each other, in a single component. To do that, we use multiple wrappers, and
then we get the wrapper hell. Morover we are thigtly coupled with several
external things. How to fix that. There are many approches. One of them might
be to declare some kind of a [facade], which groups required functionalities
into one. Another solutions might be the `useContext`.

Just keep in mid that there is no silver bullet for given problem. One must
decide which solution fits the best for a problem with given context.


### Complex component become hard to understand
This touches one of the major topics in development, which is **design** and
**patterns**. Good design decisions and patterns can easily secure from such a
problem. The issue is very simple, but not easy:

> If a component is too complex and hard to understand, then clearly there is a
> design problem (lack of design?), but not JavaScript or tool related.

Even when you transform the complex component to a function using hooks, then
you will still have **a lots of** hooks. If the design will not be changed, then
hooks will not help.

So you may ask - _How to fix it well?_. As I said earlier - the issue is
**simple**, but not **easy**. I am going to publish a series of blog posts
dedicated to good design in React applications, thus stay focused!


## Classes confuse both people and machines
Hmm... Classes confuse, right? What can be told about that to somehow resolve
this issue. Remember [RCA]?

First of all we have to answer simple question:

**When something is confusing?**

There might be many reasons, such as:
- non-deterministic behaviours
- inconsistent API(s)
- etc.

But in my opinion, the most important reason is **lack of knowledge**
about given subject - in this case the `this` keyword and classes/prototypes.
I claim that this is the reason why many people avoid this topic.
When you know how it works, why it works like that, then it is not confusing.
Then you can use it to empower your application by using all goods which came
with OOP.


## Summary
This post's purpose is not to convince you to not use React Hooks. Oh, hell no!
These new features are really handy. They perfectly resolves some set of
problems. Keep in mind that no tool is just bad. Almost nothing is
monochromatic. The same is with React Hooks - **they are not bad**, but they
**can be used badly**.

I would like to expand what has been said by Dan Abramow:

> Do not rewrite your React applications to use hooks right a way. Think about
> the design. Think well through where given thing should have been. Good design
> resolves many major issues. Learn JavaScript! Learn its quirks, gotchas. Learn
> the "bad" things. Learn how things work. If you do, then I assure you, there
> will be no things to be confused by.

### Post Scriptum:
I am well aware that view I presented here might be as confusing as the JS
classes. If you are confident about that some (or all) considerations, ideas,
analysis, etc. are wrong, feel free to reach out me and explain where the
defects are. I will be more than happy to be lead out of mistakes.



[RCA]: https://en.wikipedia.org/wiki/Root_cause_analysis
[facade]: https://en.wikipedia.org/wiki/Facade_pattern

