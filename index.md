class: center
name: title
count: false

# Rust 2024 and beyond

.p60[![Ferris](./images/ferris.svg)]

View slides at `https://nikomatsakis.github.io/rustcameroon-25/`.

.me[.grey[*by* **Nicholas Matsakis**]]
.footnote[Press `P` to read the transcript.]

---

# I wear many hats

???

So, yeah, who am I? I've been involved in Rust a long time, and along the 
way, I've wound up playing a number of different roles.

---

# Rust language designer¹

.footnote[¹ Shoutout to Tyler Mandry, Rust language design team co-lead, and Josh Triplett, fellow lang team member, both here today.]

???

To start, I work on the design of the language itself. I'm co-lead of the Rust language design team, along with Tyler Mandry -- here in the audience!. Together with the rest of the lang team like Josh Triplett (here in the audience!) we decide what features we are going to add to Rust and which we will not.

---

# Senior Principal Engineer @ Amazon 

???

I'm also a Senior Principal Engineer at Amazon. In that capacity I get to work with the teams using Rust at Amazon -- and there are a lot! How many of you build something that uses S3? Yeah, you're using Rust.

The great thing about this role is that I get to go and talk very deeply to those Rust teams, learn what's working, what's not, and then bring that back to the Rust community, where it gets combined with what other users are experiencing, and used to make Rust better for everyone.

---

# Bursty [blogger](https://smallcultfollowing.com/babysteps)

![Babysteps](./images/babysteps.png)

???

I also maintain a blog. I have for a long time, I love it. I say I'm bursty because sometimes I write 3 posts in a day, other times, like recently, it can be months. It just depends on what I've got going on.

---

# What hat am I wearing today?

None of them.

All of them.

???

So what hat am I wearing today? In one sense, none of them. I'm hearing giving you my personal opinion. I'm going to tell you things that I believe but which don't represent team consensus and certainly not Amazon's opinion.

On the other hand, all those roles inform that opinion, and I don't really believe you can fully "take off" a hat like that.

---

# Our North Star

### Empowering everyone to build reliable, efficient, and maintainable software

???

Rust has always had a consistent north star: we want Rust to empower
*everyone* -- that word *everyone* does a lot of work, we want Rust to broaden
the pool of people -- building reliable, efficient, and 
-- above all -- maintainable software.

--

*Design for the long term*

???

A key part of Rust's value prop is that it helps you to build software that lasts a long time. I mean I want you to be able to write Rust programs that will still be running after you and your children are dead. Ok, that's kind of morbid. Anyway, you get the idea.

---

# Rust's most important value?

### RELIABILITY?

???

So what is Rust's most important value? Is it reliability? Performance? Productivity? Actually, I think it's none of these things. They're important, but they're not the *most* important value.

--

### PERFORMANCE?


--

### PRODUCTIVITY?

---

# Rust's most important value?

### STABILITY *without* STAGNATION

???

I would say *that* honor goes to *Stability without stagnation*. Nobody ever gets everything right on the first try, and Rust is no exception. I mean, we try pretty hard, and I think we get pretty close, but there's always room for improvement. So we try hard to continue iterating, learning from our experiences, and making Rust better -- but we try to do that *without* disrupting that Rust software that has to work and keep working over the long term.

---

# Rust 2024 Edition is coming!

"Breaking changes where no code breaks..."

.footnote[
    [There's a song about that...](https://www.youtube.com/watch?v=q0aNduqb2Ro)
]

???

One of the coolest tools we have for that is the Rust edition. The Rust Edition lets us make tweaks and changes that affect how the language works but without breaking existing crates. Usually these changes are small and you barely even notice. A key part of this is that it only affects new code or code that opts in -- old code keeps working and building like it always did, and we always support interoperability between old and new editions. So everything keeps going.

---
name: rust-rusty1

# What makes Rust *Rusty?*

???

Lately I've gotten kind of obsessed with figuring out what makes Rust *Rust*. I've found that being able to put words to the "ineffable qualities" that we are shooting for when we design can help us to achieve them more reliably.

---
name: rust-rusty2

# What makes Rust *Rusty?*

| | What makes Rust *Rusty?* | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

.small[**NB:** Good example of where I'm speaking for myself here:<br>
    These are not "official" values of Rust, though I think they (or something like them) should be.]

---
template: rust-rusty2

???

This is my latest take on Rust's core goals. There are 5 of them, and they are in order, starting with the most important. Let's go through them briefly.

Reliability: "if it compiles, it works" -- or at least, if it doesn't, it's
*your* fault, not *Rust's* fault.

Performant: the "first draft" of your Rust code should perform pretty well. 
And while you may have to optimize, you won't normally have to do so by making 
your code low-level and cryptic.

Low-level control: look, if you want to account for every bit in your struct
or count every memory allocation, we want to let you. Rust is for systems software, and sometimes that's necessary.

---
name: rust-rusty3
template: rust-rusty2

.abspos.top270.left510[¹]

.footnote[¹ Check out Andre Bogus's [talk on Easy Mode Rust](https://www.youtube.com/watch?v=33FG6O3qejM)! (Also, thanks Andre for *This Week in Rust*!)]

---
template: rust-rusty3

???

Side note but I've definitely noticed that sometimes, though, people get a 
bit too obsessed with that. You can tell an experienced Rust developer because
they avoid complex lifetimes etc unless they're really needed.
Andre Bogus gave a great talk on this yesterday, "Easy Mode Rust", so 
check it out.

---
template: rust-rusty3

???
Extensible: some languages try to package up everything you will ever need.
Rust is not that language. We try to give you a good starting point and then
give you the tools to build the rest. This is more scalable.

---
template: rust-rusty3

???

Accessibility: I'll be honest. I wish I could say that being Rusty meant being
*easy*, but we all know that's not true. And partly that's the domain.
Building reliable, maintainable software that lasts a long time is HARD.
But while we can't make it *easy*, we can be supportive, and do our best to 
help, and that's our goal.

---

# Iterators: performant, composable abstractions

| | What makes Rust *Rusty?* | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| .mark[🏎️] | .mark[Performant, composable abstractions] | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

OK, let's see how these work in action. I'm going to illustrate by taking
a close look at *iterators*, which I think are a great example of a performant,
composable abstraction.

---

# Let's tell a story

![Barbara](./images/Barbara.png)

.footnote[
    Artistic credit goes to my daughter.
]

???

To better understand the value prop, we're going to tell a story, and it starts with Barbara. She's a Rust programmer. She's also a drawing that my daughter made some years back and that I kind of love to death.

---
name: thumbnails

# Let's tell a story

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

.abspos.left30.top350[![Barbara](./images/Barbara.png)]

???

Barbara is working on an app and she needs to take a list of images
and create thumbnails for them. So, she sits down and bangs out this code
using iterators. You've probably written code like it before.
It's a great example of composability, how the iterator APIs let you create
combine operations like map, filter, to do non-trivial things.

---

name: make-thumbnails-at-top

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

---
template: make-thumbnails-at-top

???

This is the code Barbara writes. But what is the code that *runs*?
This is where Rust takes advantage of a really cool trick that we learned
from C++, which is called *zero-cost abstractions*. 

---

template: make-thumbnails-at-top
name: with-translated-code

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    let mut i = 0;
    let l = images.len();
    let mut output = Vec::with_capacity(l);
    while i < l {
        output.push(images[i].make_thumbnail());
        i += 1;
    }
    output
}
```

---
template: with-translated-code

???

The idea is that you can write this high-level code but, once the compiler 
is finished optimizing, what you get out is going to be equivalent to 
the low-level code you would've written by hand.
So something like this.  In fact, this code includes a few optimizations 
you might not have thought of.

---

template: with-translated-code

.arrow.abspos.left430.top300.rotSW[![Arrow](./images/Arrow.png)]

???

For example, when we create the new array, we know how big it should be, so we can allocate it to just the right size.

---

template: with-translated-code

.arrow.abspos.left340.top420.rotNW[![Arrow](./images/Arrow.png)]

???

And when you access an element from an array, that normally requires 
bounds checks.

---

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    let mut i = 0;
    let l = images.len();
    let mut output = Vec::with_capacity(l);
    while i < l {
        output.push(unsafe { images.get_unchecked(i).make_thumbnail() });
        i += 1;
    }
    output
}
```

.arrow.abspos.left500.top420.rotNW[![Arrow](./images/Arrow.png)]

???

But since we're using iterators, we know the bounds are in-scope,
so we can just skip them.  So you get something like this.

--

.abspos.left650.top450.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left300.top550[
.speech-bubble.barbara.right[
Which would *you* rather write?
]]

???

And this is Rust's promise: high-level things like iterators and closures
don't come with hidden costs. Those costs can become a kind of abstraction
tax that means that when you really need perforance you have to write
low-level code. In Rust, at least when things are working right, that's not
necessary.

---

# Extensibility: minimal built-in

| | What makes Rust *Rusty?* | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| .mark[🌟] | .mark[Extensible and productive] | |
| 🤸🏾 | Accessible and supportive | |

???

So what about extensibility? One cool thing about iterators is that they are really *just* a library. They don't make use of anything that you, as a crate author, don't also have access to. That means that people can build things like iterators and put them in the public ecosystem.

---

template: thumbnails

.abspos.left300.top415[
.speech-bubble.left.barbara[
*Oh hey, I could run these in parallel!*
]]

???

Here is one example. Imagine Barbara is looking at this code and she realizes, hey, we could create all these thumbnails in parallel, and things would run faster!

---

![Rayon](./images/Rayon.png)

.footnote[
    (I am a co-maintainer, though really Josh Stone does the lion's share of the work)
]

???

To do this, she goes to crates.io, where she finds a crate Rayon. In fairness, I started Rayon, but these days it's maintained by Josh Stone -- love ya Josh! Anyway, she decides to give it a try.

---
name: thumbnailspar

# Parallelizing with Rayon

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .par_iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

.abspos.left30.top350[![Barbara](./images/Barbara.png)]

.line3[![Arrow](./images/Arrow.png)]


---
template: thumbnailspar

.abspos.left300.top415[
.speech-bubble.left.barbara[
*Rayon makes this so easy!*
]]

???

With Rayon, all she has to do is change one line -- `iter` becomes `par_iter` -- and voila, she has parallel execution. Neat!

---

# Example: Rayon

| | What makes Rust *Rusty?* | |
| :-- | :-- | :-- |
| .mark[⚙️] | .mark[Reliable] | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

OK, so iterators are performant, they're extensible, but how do they demonstrate *reliability*?

---
name: meetalan
# Adding telemetry

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .par_iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

.abspos.left30.top350[![Barbara](./images/Barbara.png)]

.abspos.left500.top350[![Alan](./images/Alan.png)]

???

Well, some time later, Barbara has an intern Alan.

---
template: meetalan

.abspos.left300.top415[
.speech-bubble.left.barbara[
Your job is to<br>add telemetry
]]

???

She tells Alan that his job is to add telemetry to their app, measuring how many thumbnails they create.

--

.abspos.left420.top550[
.speech-bubble.right.alan[
OK!
]]

???

"No problem", he says!

---
name: thumbnailsbug

# Let's tell a story

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    let mut counter = 0;
    let vec = images
        .par_iter()
        .map(|image| {
            counter += 1; 
            image.make_thumbnail()
        })
        .collect();
    log(counter);
    vec
}
```

.abspos.left500.top350[![Alan](./images/Alan.png)]

???

So Alan gets to work. He's not terribly experienced.

---
template: thumbnailsbug

.line2[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
Let's see, I'll need a counter...
]]

???

He starts by adding a counter.

---
template: thumbnailsbug

.line6[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
...add 1 for each image...
]]

???

Adding one for each image.

---
template: thumbnailsbug

.line10[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
...and log it for telemetry. Done!
]]

???

and finally logging the result to telemetry. Looks pretty good!

---
template: thumbnailsbug

.abspos.left250.top350.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left280.top440[
.thought.barbara.bubble1[&nbsp;]
]

.abspos.left310.top410[
.thought.barbara.bubble2[&nbsp;]
]

.abspos.left340.top390[
.thought.barbara.bubble3[&nbsp;]
]

.abspos.left25.top475[
.speech-bubble.barbara[
*I'm ready for lunch.*
]]

???

He opens up his PR for Barbara to review.
She's hungry, and she's got a lot on her mind.


--

.abspos.left25.top570[
.speech-bubble.barbara.right[
Looks great! Ship it!
]]

???

She reads it quickly and says "look pretty good! ship it!" So that code goes into production.

--

.line6[![Arrow](./images/Arrow.png)]

???

But wait! There's a bug! You see, when you have a `+= 1` like this, it can't actually be used from multiple threads. To see why, think about how a computer adds a number. It first has to read from memory, then it adds one, then it writes the reuslt back. So if you have two parallel threads, and they are both running at the same time, they can both go and read the same value, say 0, add 1 to to it, yielding 1, and then both write the same result back. Now you made two thumbnails, but your counter just says 1.

This is the worst kind of bug because, in practice, the code is going to run. The only thing is that your telemetry result will just silently be off. Eventually you might notice, but probably not for a long time. --- oh, wait. That's not what happens. I forget! We're using Rust!

---
.page-center[
![rewind](./images/rewind.gif)
]

???

Let's rewind and try that again.

---
template: thumbnailsbug

.line10[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
...and log it for telemetry. Done!
]]

???

So, back when Alan has finished his PR, he goes to see if it builds and run some tests -- and wait, it won't compile!

---
template: thumbnailsbug
name: thumbnailsbugferris

.line6[![Arrow](./images/Arrow.png)]

.abspos.left235.top320.p60[
![Ferris](./images/rustacean-flat-gesture.png)
]

.abspos.left25.top540[
.speech-bubble.topright.ferris[
Hold up there buddy!<br>
This could cause a data race!
]]

???

Rust's type system will not permit you to modify a counter like this from two threads at once. The compiler helpfully points out there's a data race.

---
template: thumbnailsbug

.line6[![Arrow](./images/Arrow.png)]

.abspos.left235.top320.p60[
![Ferris](./images/rustacean-flat-gesture.png)
]

.abspos.left150.top570[
.speech-bubble.right.alan[
Gee, thanks Ferris! My hero!
]]

???

Alan is able to fix it and feels great about himself.

---
.page-center[
![rewind](./images/rewind.gif)
]

???

Well, almost. I'm kind of simplifying it. Let's see what *really* happens.

---

template: thumbnailsbug

.line6[![Arrow](./images/Arrow.png)]

.abspos.left235.top320.p60[
![Ferris](./images/rustacean-flat-gesture.png)
]

.abspos.left25.top540[
.speech-bubble.topright.ferris[
    Cannot assign to `counter`, as it is a<br>
    captured variable in a `Fn` closure
]]

???

In reality, the compiler gives an error like this. (read in robot voice)

---
template: thumbnailsbug
name: stupid-compiler

.abspos.left500.top350[![Alan is sad](./images/Alan-Sad.png)]

---
template: stupid-compiler

.abspos.left350.top475[
.speech-bubble.right.alan[
Stupid compiler.
]]

.abspos.left300.top580[
.speech-bubble.right.alan[
Help me!
]]

???

Honestly, Alan is probably fairly confused. He says "Man, Rust is hard! Barbara, help!"

---
template: stupid-compiler

.abspos.left250.top350.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left75.top475[
.speech-bubble.barbara.right[
Ah, yeah, this.<br>
Use `AtomicUsize`.
]]

???

Now Barbara takes a look. She's seen this before, and knows what that error means, and how to fix it.

---
name: thumbnailsfixed

# Let's tell a story

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    let counter = AtomicUsize::new();
    let vec = images
        .par_iter()
        .map(|image| {
            counter.fetch_add(1, Ordering::SeqCst);
            image.make_thumbnail()
        })
        .collect();
    log(counter.load(Ordering::SeqCst));
    vec
}
```

.abspos.left500.top350[![Alan](./images/Alan.png)]

.line2[![Arrow](./images/Arrow.png)]
.line6[![Arrow](./images/Arrow.png)]
.line10[![Arrow](./images/Arrow.png)]


???

Alan rewrites his code to use `AtomicUsize`, which will ensure the counter is correct, even if multiple threads are executing.

---
template: thumbnailsfixed

.abspos.left320.top470[
.speech-bubble.right.alan[
Welp, now I know!
]]

???

This is cool! Alan learned something! Now he knows about data races, and he'll take that knowledge with him, hopefully helping avoid bugs even when using languages that are not Rust.

Also, if you're a child of the 80s like me, you can't see the words "Now I know"..

--

.abspos.left200.top200[
.p100[![GI Joe](./images/knowing-is-half-the-battle.gif)]
]

???

...without thinking of GI Joe. Because knowing is half the battle!

---

# Hack without fear

> Rust lets you hack without fear.<br>
> <br>
> — Felix Klock, many years back

???

And *this*, I think, is Rust's true value proposition. I think this phrasing, "Hack without fear", is the best articulation I have heard. It came from Felix Klock many years ago. Basically the idea is that Rust lets you build the systems you wanted to build, but you were afraid, because you didn't know if you'd be able to maintain it.

---

# Hack without fear

> We had a lot of ideas to improve performance, but we were hesitant to introduce them into critical systems given the risk of subtle bugs.<br><br>
>
> With Rust, we achieved up to double-digit percentage performance improvements. Rust’s type system provides a structure which we used to safely optimize our code.<br><br>
>
> — Seth Markle, Senior Principal Engineer, S3

???

Remember I said Rust was being used in S3? Here's a great quote from a Senior Principal Engineer in that space. He's talking about how they rewrote a library that was originally in C. What I love about this is that you would think that using Rust would not give you any performance boost over using C, but in fact, precisely because of reliability, they were able to make a bunch of improvements in the design and get big wins. Cool!

---

# Rust 2025 Project Goals

Draft RFC open now:

https://rust-lang.github.io/rust-project-goals/2025h1/index.html

---

# Flagship Goal 1: Async

Continue making Rust easier to use for network systems by

bringing the Async Rust experience closer to parity with sync Rust.

* tell a complete story for the use of async fn in traits, unblocking wide ecosystem adoption;
* improve the ergonomics of Pin, which is frequently used in low-level async code; and
* prepare to support asynchronous (and synchronous) generators in the language.

---

# Next feature: async closures

```rust
fn debug(
    x: impl Fn(&str) -> u32
) -> u32 {
    if env::var("DEBUG").is_ok() {
        eprintln!(x(22));
    }
}

do_something(|| "Hello")
```

---

# Next feature: async closures

```rust
async fn debug(
    x: impl AsyncFn(&str) -> u32
) -> u32 {
    if env::var("DEBUG").is_ok() {
        eprintln!(x(22).await);
    }
}

do_something(|| "Hello")
```


---

# Flagship Goal 2: RFL on stable

Continue helping Rust support low-level projects by stabilizing compiler options and tooling

used by the Rust-for-Linux (RFL) project.

Focus for 2025H1 is tooling.

---

# Flagship Goal 3: Rust All Hands 2025

Convene Rust maintainers to celebrate Rust's tenth birthday at RustWeek 2025 (co-organized with RustNL).

Author a first draft for a Rust vision doc and gather feedback.


---

# Thanks

![bill&ted's council from the future](images/bill-ted-future-council.jpg)

.center["Be excellent to each other."]

???

So yes, thanks for bearing with me, even if I'm a few minutes over time,
and please, come up and say hi, I'd love to talk to you!
