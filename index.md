class: center
name: title
count: false

# Rust 2024 and beyond

.p60[![Ferris](./images/ferris.svg)]

.me[.grey[*by* **Nicholas Matsakis**]]
.left[.citation[View slides at `https://nikomatsakis.github.io/rustnation-24/`]]

---

# I wear many hats

???

So, yeah, who am I? I've been involved in Rust a long time, and along the way, I've accumulated a great many hats. Not literal hats, but different roles that I play.

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

# Bursty blogger

![Babysteps](./images/babysteps.png)

.footnote[https://smallcultfollowing.com/babysteps]

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

# Rust in 2024

What I see...

* GREAT OPPORTUNITY
* GREAT RISK

???

So, where are we at? It's 2024, Rust is being used more and more, and clearly there's a *ton* of opportunity for it to grow. But that's because I'm kind of a pessimist, and I always believe that I'm going to wake up tommorrow to find that people don't like Rust, not really.

---

# Rust in 2024

What I see...

* GREAT OPPORTUNITY
* ~~GREAT RISK~~ SOME RISK

???

More realistically, there's *some* risk -- primarily, the risk I see is that we will get complacent. I mean, Rust is great, but it can be so much better!

---

# Our North Star

### Empowering everyone to build reliable, efficient, and maintainable software

???

So what do we want Rust to be? Well, this is our north star -- we want Rust to empower *everyone*. That word does a lot of work, we want Rust to make building software more accessible to more people. We want it to empower them to build reliable, efficient, and -- above all -- maintainable software.

--

*Design for the long term*

???

You heard it in Lars' keynote yesterday. A key part of Rust's value prop is that it helps you to build software that lasts a long time. I mean I want you to be able to write Rust programs that will still be running after you and your children are dead. Ok, that's kind of morbid. Anyway, you get the idea.

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

# What makes Rust *Rust*?

???

Lately I've gotten kind of obsessed with figuring out what makes Rust *Rust*. I've found that being able to put words to the "ineffable qualities" that we are shooting for when we design can help us to achieve them more reliably.

--

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

.small[**NB:** Good example of where I'm speaking for myself here:<br>
    These are not "official" values of Rust, though I think they (or something like them) should be.]

???

This is my latest take on Rust's core goals. There are 5 of them, and they are in order, starting with the most important. Let's go through with them.

So, number one is reliability -- we saw it in Lars's talk. Rust's "secret weapon" and most appealing quality is not really performance, it's the feeling that "if your code compiles, it works". And it makes sense. People could always get performance from C, but they couldn't get reliability.

Number two is *performant and composable abstractions*. This is that sense that, once you've finished the "rough draft" of your code, it's going to perform pretty good, even if you still have to tune it. It's also this idea that you shouldn't have to stop using high-level, idiomatic abstractions to get good performance. Composable meanwhile is the idea that you should be able to take small things and put them together to build more complex, surprising things.

The next one is *low-level control*. Look, Rust is for building systems software, and sometimes you've just got to get down to the bits. If you want to control the memory layout of your struct, or count every memory allocation, we want you to be able to do that. 

--

.abspos.top260.left515[¹]

.footnote[¹ Check out Andres's talk on Easy Mode Rust! (Also thanks Andres for *This Week in Rust*!)]

???

One thing I've noticed is that sometimes, though, people get a bit too obsessed with that. I think you'll find that the more experienced the Rust developer, the fewer lifetimes, references, and advanced features they wind up using. Check out Andres's talk on Easy Mode Rust to learn more about that.

So what about extensible? Look, some langauges try to package up everything you need. Rust is not that language. We try to be minimal, but to deliver the tools that people can use to build libraries and crates that can do everything. This lets us scale better and we get a lot of power from it.

Finally, accessibility. I'll be honest, I wish this could be "easy", but I don't think Rust is always easy -- nor can it be, because building reliable, maintainable systems is not easy. But we do always try to be *supportive*, to help you achieve your goals.

---

# Iterators: performant, composable abstractions

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| .mark[🏎️] | .mark[Performant, composable abstractions] | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

So, let's look at a case study of one beloved part of Rust's design that I think exemplifies these values pretty well. If you've ever written any Rust, you've probably worked with **iterators**.

---

# Let's tell a story

![Barbara](./images/Barbara.png)

.footnote[
    Artistic credit goes to my daughter.
]

???

To better understand the value prop, we're going to tell a story, and it starts with Barbara. She's a Rust programmer. She's also a drawing that my daughter made some years back.

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

One day, Barbara is reading over some code that creates thumbnails for a vector of images in the application.

---
template: thumbnails
.arrow.abspos.left400.top90.rotSW[![Arrow](./images/Arrow.png)]

---
template: thumbnails
.line2[![Arrow](./images/Arrow.png)]

---
template: thumbnails
.line3[![Arrow](./images/Arrow.png)]

.abspos.left500.top165[
```rust
// impl Iterator<Item = &Image>
```
]

--

.arrow.abspos.left600.top145.rotS[![Arrow](./images/Arrow.png)]

--

.arrow.abspos.left730.top145.rotS[![Arrow](./images/Arrow.png)]

---
template: thumbnails
.line4[![Arrow](./images/Arrow.png)]

.abspos.left500.top195[
```rust
// impl Iterator<Item = Image>
```
]

--

.arrow.abspos.left250.top175.rotSW[![Arrow](./images/Arrow.png)]
--

.arrow.abspos.left450.top175.rotSW[![Arrow](./images/Arrow.png)]

--

.arrow.abspos.left730.top175.rotS[![Arrow](./images/Arrow.png)]

---
template: thumbnails
.line5[![Arrow](./images/Arrow.png)]

.abspos.left500.top220[
```rust
// ?
```
]

--

.arrow.abspos.left550.top150.rotNW[![Arrow](./images/Arrow.png)]

--

.abspos.left500.top220[
```rust
// Vec<Image>
```
]

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

???

So this is the code that Barbara actually writes. You can also see how iterators are *composable*. You start with a simple iterator but you can build it up to express more complex ideas.

Now, in truth, you could write code much like this in just about any language. What makes Rust special is a trick that we learned from C++, a trick called *zero-cost abstractions*. The idea is that high-level abstractions like iterator can be written in a way that they are *guaranteed* to compile down to really efficient code -- well, so long as you enabled compiler optimizations. Don't forget to run with `--release`! Very important.

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

???

Anyway, once the compiler is done with your code, it's going to look something like this, which is pretty much what you'd have done if you wrote it by hand. In fact, it's going to have a few optimizations that you maybe would have overlooked.

---

template: with-translated-code

.arrow.abspos.left430.top300.rotSW[![Arrow](./images/Arrow.png)]

???

For example, when we create the new array, we know how big it should be, so we can allocate it to just the right size.

---

template: with-translated-code

.arrow.abspos.left340.top420.rotNW[![Arrow](./images/Arrow.png)]

???

And when you access an element from an array, that normally requires bounds checks, but since iterators don't expose this index, it can't be out of bounds, so we can use unsafe code to skip that....

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

So you get something like this.

--

.abspos.left650.top450.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left300.top550[
.speech-bubble.barbara.right[
Which would *you* rather write?
]]

???

In some other languages *who we shall not name*, you find that using high-level, nice features like this comes with a kind of *abstraction tax*. You can use them, but for the most efficient parts of the code, you have to rewrite it to work in this low-level way. With Rust, when things work right, this is not necessary.

---

# Extensibility: minimal built-in

| | What makes Rust *Rust*? | |
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

| | What makes Rust *Rust*? | |
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

# Let's talk about THE FUTURE

![bill&ted's council from the future](images/bill-ted-future-council.jpg)

???

OK, enough about iterators, let's talk about **Rust's future**.

--

## `std::future::Future`, that is

???

And by that, I of course mean the future of Rust, but I also mean it quite literally -- async Rust's futures trait.

That pun never gets old.

---

# Async Rust

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| .mark[🏎️] | .mark[Performant, composable abstractions] | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

So what is async Rust? It's a set of language features for building high peformance network servers, which has turned out to be a key application area for Rust.

---

# Async Rust can be so very cool¹

It's also a bit different than async/await in other languages.

.footnote[
    ¹ Shoutout to Alex Crichton, Aaron Turon, Taylor Cramer, Boats, Carl Lerche, and others who contributed to this design, sadly none of whom are here today.<br>
]

???

Async Rust's design is, in my opinion, very cool.

Syntactically, it looks very much like async-await in other languages, but under the hood, it works a bit differently, which turns out to make a big difference.

---

# Async in JavaScript starts a task

```js
async function process_row(row) { 
    /* do some really smart stuff */
}

let promise = process_row(row);
```

.abspos.left755.top115.width100[![Javascript](./images/JavaScript-logo.png)]

.abspos.left600.top350[![Alan](./images/Alan.png)]

.abspos.left350.top400[
.speech-bubble.alan.right[
In JavaScript, calling an<br>
async functions<br>
starts a task.
]]

.abspos.left50.top350.bgactive.padding20[
    Task A
]

???

So how do async functions in JavaScript work? Well, in JavaScript, if you've got a task, say Task A...

--

.abspos.left10.top230.width50[![Arrow](./images/Arrow.png)]

???

...and it calls an Async Function...

--

.abspos.left200.top350.bgactive.padding20[
    Task B
]

???

then this winds up starting another task...So now you have two tasks running.

---

# Await in JavaScript waits for the task

```js
async function process_row(row) { 
    /* do some really smart stuff */
}

let promise = process_row(row);
let result = await promise;
```

.abspos.left755.top115.width100[![Javascript](./images/JavaScript-logo.png)]

.abspos.left600.top350[![Alan](./images/Alan.png)]

.abspos.left350.top400[
.speech-bubble.alan.right[
When I use await,<br>
I pause my task until<br>
the other task finishes.
]]

.abspos.left50.top350.bgactive.padding20[
    Task A
]

.abspos.left50.top470.width75.height10.bgsuspended.padding20[
    
]

.abspos.left200.top350.bgactive.padding20[
    Task B
]

.abspos.left10.top260.width50[![Arrow](./images/Arrow.png)]

???

In turn, when Task A *awaits* the future, it basically stalls until Task B completes.

--

.abspos.left200.top475.huge[↵] 

.abspos.left50.top520.bgactive.padding20[
    Task A
]

???

and then it can keep going.

---

# Core idea: future

```rust
async fn process_row(row: Row) -> Result {
    /* do some really smart stuff */
}

let future = process_row(row);
```

.abspos.left0.top350[![Barbara](./images/Barbara.png)]

.abspos.left240.top400[
.speech-bubble.barbara.left.medium[
    In Rust, an `async fn`<br>
    returns a **future**,<br>
    a bit of **suspended code**.
]]

???

So what happens with Rust?

--

.abspos.left550.top400.width70.bgactive.padding10.medium[
    Task A
]

???

In Rust, when you're in a task...

--

.arrow.abspos.left10.top230[![Arrow](./images/Arrow.png)]

???

...and you invoke an async function...

--

.abspos.left650.top400.bgfuture.padding10.medium.rounded_corners[
    `process_row(row)`
]


???

that is just going to create an **data structure**, which we call a future.
It's totally inert. Nothing is happening.
This struture represents a suspended computation.

---

# Core idea: future

```rust
async fn process_row(row: Row) -> Result {
    /* do some really smart stuff */
}

let future = process_row(row);
let result = future.await;
```


.abspos.left0.top350[![Barbara](./images/Barbara.png)]

.abspos.left240.top400[
.speech-bubble.barbara.left.medium[
**Awaiting** a future<br>
makes the current task<br>
execute the future
]]

.abspos.left550.top400.width70.bgactive.padding10.medium[
    Task A
]

.abspos.left650.top400.bgfuture.padding10.medium.rounded_corners[
    `process_row(row)`
]

--

.arrow.abspos.left10.top260[![Arrow](./images/Arrow.png)]

???

Now, when a task **awaits** a future...

--

.abspos.left550.top480.width70.bgactive.padding10.medium[
    .await
]

.abspos.left630.top475.rotSW.huge[⇗] 

???

That task then goes and executes that future, moving the function along.
Once the await is done, the future is again inert.
So async functions are only executing when they are awaited, 
they're like a kind of "lazy operation".

---

name: compose

# You can build bigger futures

```rust
async fn process_row(row: Row) -> Result {
    /* do some really smart stuff */
}

let future1 = process_row(row1);
let future2 = process_row(row2);
let future3 = join!(future1, future2);
```

.abspos.left0.top350[![Barbara](./images/Barbara.png)]

.abspos.left240.top400[
.speech-bubble.barbara.left.medium[
This design lets you<br>
**compose** futures<br>
into bigger ones,<br>
without having to<br>
spawn a task for<br>
each each piece.<br>
]]

???

Why is this cool? It comes back to that idea of composability and zero-cost abstractions.
Futures can be built up into bigger futures -- like here.

---
template: compose

.abspos.left650.top450.bgfuture.padding10.medium.rounded_corners[
    `process_row(row1)`
]

.arrow.abspos.left10.top230[![Arrow](./images/Arrow.png)]

???

when we call `process_row` the first time we get one future

---
template: compose


.abspos.left650.top450.bgfuture.padding10.medium.rounded_corners[
    `process_row(row1)`
]

.abspos.left650.top550.bgfuture.padding10.medium.rounded_corners[
    `process_row(row2)`
]

.arrow.abspos.left10.top260[![Arrow](./images/Arrow.png)]

???

then we get a second one. Remember, at this point, both futures are inert. no code is running, these are just data structures stored on the stak, very cheap.

---
template: compose

.abspos.left630.top370.width210.height270.bgfuture1.padding10.medium.rounded_corners[
    `joined future`
]

.abspos.left650.top450.bgfuture.padding10.medium.rounded_corners[
    `process_row(row1)`
]

.abspos.left650.top550.bgfuture.padding10.medium.rounded_corners[
    `process_row(row2)`
]

.arrow.abspos.left10.top290[![Arrow](./images/Arrow.png)]

???

then we can build them up into a compound future. Still no code is running, but now we have a future that represents the idea of doing both calls concurently -- i.e., at the same time.

---

# You can build bigger futures

```rust
async fn process_row(row: Row) -> Result {
    /* do some really smart stuff */
}

let future1 = process_row(row1);
let future2 = process_row(row2);
let future3 = join!(future1, future2);
future3.await
```

.abspos.left0.top350[![Barbara](./images/Barbara.png)]

.abspos.left240.top400[
.speech-bubble.barbara.left.medium[
Awaiting will<br>
process the<br>
two rows<br>
concurrently.
]]

.abspos.left630.top370.width210.height270.bgfuture1.padding10.medium.rounded_corners[
    `joined future`
]

.abspos.left650.top450.bgfuture.padding10.medium.rounded_corners[
    `process_row(row1)`
]

.abspos.left650.top550.bgfuture.padding10.medium.rounded_corners[
    `process_row(row2)`
]

.arrow.abspos.left10.top320[![Arrow](./images/Arrow.png)]

.abspos.left480.top400.width70.bgactive.padding10.medium[
    Task A
]

.abspos.left480.top480.width70.bgactive.padding10.medium[
    .await
]

.abspos.left570.top465.huge[⇒] 

???

when we await this combined future, our single task winds up running both futures concurrently.

This is cool because spawning tasks, in general, requires allocation. It represents a runtime cost. If we made every async function eagerly spawn a task, like in JavaScript, we'd be allocating memory proportional to the number of futures that we want to run concurrently. But in Rust, we don't have to do that.


---
name: scaling-up-to-streams

# Scaling up to streams

```rust
async fn batch_job(db: &Database) {
    let rows = run_query(db, FIND_WORK_QUERY).await;
    let results = stream::iter(rows)
        .map(|row| process_row(row)))
        .buffered(5);
    while let Some(result) = results.iter().next().await {
        upload_result(result).await;
    }
}
```

???

This in turn lets us scale up to more complex things, like streams. Here is a neat piece of code.

---

template: scaling-up-to-streams

.arrow.abspos.left10.top150[![Arrow](./images/Arrow.png)]

???

It starts by querying a database to fetch a bunch of rows.

---

template: scaling-up-to-streams

.arrow.abspos.left10.top180[![Arrow](./images/Arrow.png)]

???

Then it creates a stream that will iterate over the rows....

---

template: scaling-up-to-streams

.arrow.abspos.left10.top210[![Arrow](./images/Arrow.png)]

???

...processing each one in turn...

---

template: scaling-up-to-streams

.arrow.abspos.left10.top240[![Arrow](./images/Arrow.png)]

???

... and buffering them up so that you can process 5 of those rows concurrently.
The number 5 is presumably chosen to keep concurency but keep peak memory usage down.

---

template: scaling-up-to-streams

.arrow.abspos.left10.top270[![Arrow](./images/Arrow.png)]

???

then we can pull each of those results as they complete and upload the final result.

---

template: scaling-up-to-streams

.abspos.left600.top350.fliplr[![Barbara](./images/Barbara.png)]


.abspos.left350.top400[
.speech-bubble.barbara.right.medium[
Dang! It's *so* cool<br>
to express complex<br>
control-flow so compactly.
]]

???

Pretty neat, right? A great example of how concise Rust can be while still generating the same low-level code you would write by hand.

---

# Async Rust gives low-level control

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | .mark[Low-level control and transparency] | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

Another advance of not spawning tasks for every async functions is that it lets async functions be used in very low-level contexts.

---

# Embassy

> Rust's async/await allows for unprecedently easy and efficient multitasking in embedded systems. [..] **It obsoletes the need for a traditional \[Real-time operating system]** with kernel context switching, and is faster and smaller than one!

from https://embassy.dev/

???

For example, check out the embassy runtime, which lets you write async functions to run on tiny devices that don't even have an operating system! Very cool.

---

# But Async Rust has some gaps

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| .mark[⚙️] | .mark[Reliable] | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

As cool as async Rust is, it also has some gaps, and these gaps worry me. The one I am most worried about has to do with reliability.

---

name: bbbs

# But Async Rust has some gaps

```rust
async fn batch_job(db: &Database) {
    let rows = run_query(db, FIND_WORK_QUERY).await;
    let results = stream::iter(rows)
        .map(|row| process_row(row)))
        .buffered(5);
    while let Some(result) = results.iter().next().await {
        upload_result(result).await;
    }
}
```

.abspos.left600.top350.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left450.top400[
.speech-bubble.barbara.right.medium[
Why do<br>
my connections<br>
keep timing out?
]]

???

You see, that really cool high-level code I showed you?
It actually has a pretty subtle bug.
If you run it, things will mostly work fine -- except when they don't.
Sometimes, your database connections will time out.
This is not good!
This kind of thing is not supposed to happen in Rust!
What is going on?

---

template: bbbs

.line3[![Arrow](./images/Arrow.png)]

.abspos.left50.top430.width180.height80.bgactive.center[
    Task
]

.abspos.left300.top505.bgfuture.padding10.medium.rounded_corners[
    `rows`
]

???

Well, it has to do with Rust's model. You see, when you create the `rows` stream, remember, nothing happens yet.

---

template: bbbs

.line6[![Arrow](./images/Arrow.png)]

.abspos.left50.top430.width180.height80.bgactive.center[
    Task
]

.abspos.left50.top510.width180.height80.bgsuspended.center[
    next().await
]

.abspos.left300.top505.bgfuture.padding10.medium.rounded_corners[
    `rows`
]

.abspos.left220.top490.huge[⇒] 

???

It's only here, when we *await* the next function, that stuff starts to happen. The first time, this will cause those 5 connections to start and the database query to run. The next time, it will go and keep those connections going, making progress, until the next item is done.

---

template: bbbs

.line7[![Arrow](./images/Arrow.png)]

.abspos.left50.top430.width180.height80.bgactive.center[
    Task
]

.abspos.left50.top510.width180.height80.bgsuspended.center[
    next().await
]

.abspos.left50.top590.width180.height80.bgsuspended.center[
    (await)
]

.abspos.left300.top505.bgfuture.padding10.medium.rounded_corners[
    `rows`
]

.abspos.left300.top590.bgfuture.padding10.medium.rounded_corners[
    `upload_result(result)`
]

.abspos.left220.top570.huge[⇒] 

???

At that point, the `rows` stream is just an inert data structure again.
And now the task begins to execute the result uploading.
While that is happening, `rows` is not executing, so any connections that are open to the database won't continue working.
This can cause them to timeout.

---

# If it compiles, it works?

With Async Rust, not as often as we'd like:

* Nested awaits
* Unexpected cancellation
* Misuse of `select!`
* Difficult cleanup because we have no async drop
* Uninitialized or mixed executors

???

You can see why I'm so worried.
These kind of errors are a clear violation of that core value propsition that Rust offers -- that if it compiles, it works.
Over time we've found a number of patterns like this, places where the async model has rough edges.

--

Want to read more?

* [Stories submitted to the wg-async vision doc](https://rust-lang.github.io/wg-async/vision/submitted_stories/)
    * especially [Barbara battles buffered streams](https://rust-lang.github.io/wg-async/vision/submitted_stories/status_quo/barbara_battles_buffered_streams.html)
* Tyler Mandry's "for await" [blog post](https://tmandry.gitlab.io/blog/posts/for-await-buffered-streams/)
* Tomaka's [A look back at asynchronous Rust](https://tomaka.medium.com/a-look-back-at-asynchronous-rust-d54d63934a1c)

???

I won't go into details but here are some great resources to read more, if you're interested.

---

# Async Rust roadmap

| Year | Language |
| ---  | :-- |
| 2019 | Async fns |
| 2019-2022 | *Ecosystem development*¹ |
| 2023 | Async fn in traits² |
| 2024 | Async closures, generators... |

.footnote[
    ¹ Shoutout to Alice Ryhl, go see her keynote this evening! Also the Shuttle folks, who spoke yesterday, Luca Palmieri's Pavex, Zainab Ali's talk-- too many to list, really.<br>
    2 Big shoutout to Michael Goulet, Eric Holk, Tyler Mandry, other members of Async WG.<br>
]

???

Here's a brief history of async Rust. We stabilized async functions in 2019. Since then there's been a lot of great ecosystem development, and that's partly how we learned about some of these footguns. Recently started shipping new language features again.

The good news is that I think, with our new experience as well as this new language work, we can start to address these gaps.

---

# Where I hope we get to¹

* Standard way to write async Rust that...
    * lets you gracefully handle cancellation and streams
    * supports a rich, interopable ecosystem of middleware, logging, etc
    * works everywhere, from embedded to servers²
    * is easy to learn, well documented, and free of footguns

.footnote[¹ Speaking for myself here, not a consensus opinion.<br>² To the extent possible.]

???

So this is where I personally would like to get to.
I'd like to have a standard way to write async Rust that avoided the footguns I showed you.
It should let you easily change between executors, so you can use Tokio, or Embassy, or other options, and you should still be able to grab and deploy middleware etc from crates.io whatever you choose.
No doubt it's going to take some work to develop this, but I think we'll find a path.

---

# Where else can we do better on reliability?

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| .mark[⚙️] | .mark[Reliable] | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

OK, so I showed you one threat to reliability, but what other threats are out there?

---

# cve-rs

How many of you saw [cve-rs](https://github.com/Speykious/cve-rs)?

![cvs-rs](./images/cve-rs.png)

???

How many of you have heard of the cve-rs project?

Yeah-- so this is a project that exploits a long-standing bug in the compiler to offer "safe" Rust APIs that will crash your system and do horrible things.

How many of you are worried about this?

Yeah, me too. This is bad! Rust's not supposed to do that!

And yet, it's not the thing that worries me the most.

---

# Infrastructure¹ and supply chain security²

Thank goodness for the Rust Foundation.³

.footnote[
    ¹ For far too long, Rust infra team was almost entirely Pietro Albini and Mark Simulacrum...<br>
    ² Shoutout to the members of the [crates.io team](https://www.rust-lang.org/governance/teams/crates-io), led by  Justin Geibel and Tobias Bieniek.<br>
    &sup3; Who employ JD Nose on Rust Infra, Tobias Biniek on crates.io, and Walter Pearce on Security. Check out Walter's talk on painter!
]

???

I think i we're talking about dire threats to Rust's reliability guarantees, in some ways, our biggest risk is the same risk we've seen from other projects -- the crates.io ecosystem. Rust leans hard on extensibility, which means we lean hard on crates, which means it's very important that this system operates securely and is free of malware.

Fortunately things are doing very well here. Some years back, it was very hard. The infrastructure team was basially just Pietro -- here in the audience! -- and MArk, unfortunately not here, and the crates.io team was exclusively volunteers.

But with the Rust Foundation, things are different. We have dedicated staff, and we've also got people like Walter Lewin coming up with cool, innovative projects that can help bar raise the bar with respect to security. I definitely recommend you check out Walter's talk on Painter later today, very cool stuff.

---

# Delivering on our core promise, Reliability

* Supply chain, infrastructure security.

???

OK, so we're making progess on supply chain security.

What about the trait solver? Well, what about unsoundness like cve-rs? As I said, this was based on a longstanding bug, and the reason that bug has not yet been fixed is two-fold. First, it seemed unlikely to occur in the wild -- thanks cve-rs for violating that by the way -- but also because it required some serious refactoring and rearchitecting internally to the compiler to fix in the right way. I'm very pleased to say that this work took a big step forward when, after years of work, Bastian Keucher recently opened a PR to stabilize the first use of a new trait solver for Rust.

The other big development is the work towards a Rust specification. Beginning with Ferrocene -- many folks in the audience today from there -- we have started to have a specification that says what Rust should do. Be sure to go see Pietro's talk to learn more about that. Thanks to Ferrocene generously open sourcing that work, we're able to use it as a starting point to build out an official Rust spec. Shout to Mara -- here today! -- and others doing that work.

--
* Unsoundness like cve-rs?
    *  New trait solver¹ unblocks bug fixes
--
* Spec work:
    * Ferrocene [open-sourced](https://ferrous-systems.com/blog/ferrocene-open-source/) their [spec](https://github.com/ferrocene/specification)²
    * building on that to [create an official Rust spec](https://blog.rust-lang.org/inside-rust/2023/11/15/spec-vision.html)³

--

* Developing Rust solvers
    * Stable MIR
    * [Kani](https://model-checking.github.io/kani-verifier-blog/2023/08/03/turbocharging-rust-code-verification.html), [Cruesot](https://github.com/creusot-rs/creusot), [Prusti](https://github.com/viperproject/prusti-dev), [Aeneas](https://github.com/AeneasVerif/aeneas)

???

Getting a spec in turn unlocks the last interesting development, which is being able to support rich theorem provers for Rust. These tools allow us to take code that is theoretically unsafe and prove that it cannot, in fact, cause undefined behavior -- effectivelly, prove mathematically that it is safe, even if it doesn't obey Rust's type system rules. This takes a lot more work than just writing safe Rust, but it's the ultimate guarantee.

To do this, solvers need access to Rust's type system, so we're building out a set of APIs called *Stable MIR* that give access to the compiler's intenals, in turn enabling verifies like the ones you see here. Most of this work is still in a fairly experimental state but it's advancing rapidly and there's a lot of promise.

---

# Where I hope we get to¹

.abspos.top90[![Tokio crates.io page](./images/cio-tokio.png)]

.footnote[¹ Speaking for myself here, not a consensus opinion.]

???

So where can we get to? As of now, we have a lot of widely used crates in the ecosystem that lean heavily on unsafe. Something like Tokio, for example, would not be possible without it. But the reality is that, no matter how hard the Tokio devs work -- and they do work hard -- we've learned from C that they'll never get all the memory safety bugs.

--

.abspos.top580.left450.width200.height50.bgred.center[![unsafe-code](./images/unsafe-code-verified.svg)]

???

I'd like to see them get to the point where widely used libraries like Tokio
are able to prove their unsafe code is correct. I don't think this will ever be practical to do for every library, but for widely used libraries, I very much think it's worth the trouble -- if we can get the tools good enough!

---

# Scaling accessibility

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| .mark[🤸🏾] | .mark[Accessible and supportive] | |

???

So let's talk about the last one, accessibility and supportiveness.

---

# Rust error messages are great¹

How many people here love Rust error messages?

.footnote[¹ Now this IS a consensus opinion. In Esteban Küber, David Wood and the Diagnostics WG we trust!]

???

I think the most well-known example of Rust being supportive is its error meessages.  How many people here love Rust's error messages, raise your hands...

--

![Mean girls](./images/mean-girls.gif)

???

This is how the room looks to me. It's a good thing you raised your hands because otherwise this gif would look pretty dumb. 

Right now, those error messages are great because of the hard work of people like Esteban Kuber and David Wood -- both in the audience today -- improving the compiler.

---

# But remember this?

.abspos.left50.top100.p60[
![Ferris](./images/rustacean-flat-gesture.png)
]

.abspos.left375.top200[
.speech-bubble.left.ferris[
    Cannot assign to `counter`, as it is a<br>
    captured variable in a `Fn` closure
]]


.abspos.left650.top350[![Alan is sad](./images/Alan-Sad.png)]

.abspos.left200.top475[
.speech-bubble.right.alan[
I...have no idea what this means.
]]

???

But we saw earlier that, despite all of that, there are still cases
where the compiler winds up talking in jargon, telling you why the
type system is not happy, but not what the real problem is.

---

# What about [*this*](https://github.com/diesel-rs/diesel/issues/2450)?

```
the trait bound `diesel::query_builder::SelectStatement
<schema::scripts::table, diesel::query_builder::select_clause
::DefaultSelectClause, diesel::query_builder::distinct_claus
e::NoDistinctClause, diesel::query_builder::where_clause::WhereClause<
diesel::expression::operators::Eq<schema::scripts::columns::id,
&str>>>: diesel::query_builder::IntoUpdateTarget` is not satisfied

the trait `diesel::query_builder::IntoUpdateTarget` is not
implemented for `diesel::query_builder::SelectStatement<
schema::scripts::table, diesel::query_builder::select_clause
::DefaultSelectClause, diesel::query_builder::distinct_clause
::NoDistinctClause, diesel::query_builder::where_clause::WhereClause<
diesel::expression::operators::Eq<schema::scripts::columns::id,
&str>>>`

help: the following implementations were found:
<diesel::query_builder::SelectStatement<F,
diesel::query_builder::select_clause::DefaultSelectClause,
diesel::query_builder::distinct_clause::NoDistinctClause, W>
as diesel::query_builder::IntoUpdateTarget>rustc(E0277)
```

???

And if you think that is bad, consider things like this message,
which I copied from a Diesel issue. This stuff happens beacuse Diesel
is using Rust traits to model things like database schemas, and the compiler
doesn't know *anything* about that.

---

# How can we improve Rust's errors?

* `#[diagnostic::on_unimplemented]` -- custom trait error messages
    * Coming May 2nd in Rust 1.78.0!
    * Shout-out to Georg Semmler, Esteban Küber, Michael Goulet, and more!
* Local translations -- what if you don't speak English?
    * Shout-out to David Wood and others!

???

So what we can do about it? We're starting to see progress, such as 
the stabilization of the "on-unimplemented" attribute, which lets crates
customize the errors you see when a trait is not implemented.

We are also seeing efforts like error translations, helping make Rust 
more accessible to people whose first language is not English.

---
 
# Can we go further?

What if crates could *control their development experience*?

Diagnostics?

???

The current stuff is cool, but how far can we push it? 

How much can we let crates customize diagnostics?

--

.large[Lints??]

???

What if they could specify custom lints, so that they can catch common 
errors from using their API?

--

.huge[IDE refactorings???]

???

Or what if they could extend the refactorings you see in the API with 
things specific to the crate? 

That'd be really cool, right?

---
 
# Procedural macros today

.abspos.left50.top150.bgactive.padding20[
    Tokens
]

.abspos.left180.top150.huge[⇒]

.abspos.left250.top125.bgactive.padding20[
    Procedural<br>
    macro
]

.abspos.left425.top150.huge[⇒]

.abspos.left500.top150.bgactive.padding20[
    Tokens
]

???

If we could do all that, Rust would be an even better platform for
translating the details of your domain into code. I think we can do that,
and partly because we've seen how much mileage we get from procedural
macros and custom derives. These are the compiler extensions we have today,
and they basically work by taking in tokens or text and emitting text.
Very simple, but they can do so much.

---
 
# *Supercharged* procedural macros

.abspos.left50.top150.bgactive.padding20[
    Tokens
]

.abspos.left180.top150.huge[⇒]

.abspos.left250.top125.bgactive.padding20[
    Procedural<br>
    macro
]

.abspos.left425.top150.huge[⇒]

.abspos.left500.top150.bgactive.padding20[
    Tokens
]

???

What if they could access more than just tokens and text?

--

.abspos.left50.top300.bgactive.padding20[
    Type info
]

.abspos.left200.top270.huge[⇗]

???

What if they could read type info?

--

.abspos.left50.top450.bgactive.padding20[
    All that other stuff<br>
    the compiler knows
]

.abspos.left220.top350.huge[⇗]

???

And all that other stuff the compiler knows?
That'd be super cool, right?

--

.abspos.left400.top330.bracket.red[}]

.abspos.left500.top300.red.huge[
    Stable MIR! (sort of)
]

???

If this sounds familiar, it's because it's basically the same
information that solvers need to use to prove unsafe code is sound.
So I believe we can leverage and improve those investments to let us
build supercharged macros that will give us a ton of expressive power.

---
 
# Where I hope we get to¹

* Crates can build rich developer experiences
    * Procedural macros, custom derives
    * Lints, static verifiers, theorem provers
    * Improved diagnostics

.footnote[¹ Speaking for myself here, not a consensus opinion.]

???

So this is where I would like us to get to. 
Crates should be able to build rich developer experiences,
going beyond what is possible today to support richer macros,
diagnostics, lints, and the whole range of things.

---
name: values-support

# Rust's values support each other

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔧 | Low-level control and transparency | |
| 🌟 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

???

OK, we're coming on the end of the talk, but I want to close with 
a bit of reflection on the way that we've seen Rust's values support each other.

---
template: values-support

*Extensible* supports *Accessible*

.abspos.left400.top280.huge.red[⤸]

???

For example, we saw that extensibility supports accessibility,
because empowering crate authors with things like procedural macros
or custom diagnostics improves the user experience.

---
template: values-support

.abspos.left180.top150.fontsize650.red[⤸]

*Reliable* supports *Accessible*

???

For that matter, reliability makes Rust accessible, because -- trust me --
there is nothing LESS accessible than debugging a data race or a memory
safety bug.

---
template: values-support

.abspos.left540.top240.fontsize300.bracket2.red[}]

.abspos.left520.top300.fontsize250.red[⤴ ]

...but *Accessible* supports **everything**.

???

But what about Accessibility? What does it support?

Well, I think it supports EVERYTHING ELSE.

And that's because Rust is open source.

Let me explain.

---
 
# The open source positive feedback cycle

.abspos.left325.top200[Design improves]

???

When you've got a solid open source project...

--

.abspos.left600.top180.fontsize300.red[⤵]
.abspos.left600.top300[Users come]

???

...and people notice it and start using it...

--

.abspos.left600.top370.fontsize300.rot90.red[⤵]
.abspos.left350.top400.center[Users make<br>suggestions]

???

...they start having ideas how it could be better...

--

.abspos.left150.top370.fontsize300.rot180.red[⤵]
.abspos.left100.top300.center[Users make<br>improvements]

???

...and then, some subset of them start to implement those ideas...

--

.abspos.left150.top180.fontsize300.rot270.red[⤵]

???

at which point the whole cycle begins again, reinforcing itself.
Neat.

---
 
# Open source burnout is a thing

.center[.p50[![Burnout guide](./images/balance-for-open-source.png)]]

.footnote[[Read more.](https://opensource.guide/maintaining-balance-for-open-source-maintainers/)]

???

Of course, the reality can be a bit more complicated.
Lately there's been a lot of talk about burnout in open source
and I can assure you it is a real thing.
This is true in Rust, just like every other open source project,
and it's something I really want to see us improve.

---
 
# Modes

Users

>

Contributors

???

A big part of the problem is that the story doesn't really end 
with contributors. In the story as I told it, people have ideas, and some 
smaller set of people then go and open PRs to implement those ideas...

--

>

**Maintainers**

???

...but I left out the *even smaller* set who have to review those PRs.
This is the set that winds up carrying the most load -- as well as guilt.
Other people are volunteering their time to write code for your project, 
and you might not even be able to offer them a timely review? 
Doesn't feel great.

---
 
# So you want to be a maintainer?

* Review PRs.

???

So how can you help?
Well, part of it is, don't just contribute code, but stick around,
review PRs. 

You don't have to be "approved" to do it, you can do a "pre-review", 
just help to highlight potential problems and make suggestions.

Eventually you may find your pre-reviews are reliably finding all the issues
in the project.

--
* Label and categorize ("triage") incoming issues!
* Help prepare the agenda for Rust team meetings!¹
* Take notes!
* Build bots like rfcbot!
* "Program management" like running the Rust 2024 edition!²
* Moderation!³

.footnote[
    ¹ Thanks TC, you're the best! 💜<br>
    ² Three cheeers for Mara, Eric Huss, and Bstrie: you're ALSO the best! 💜<br>
    ³ We **desperately** need more moderators. The team is currently just two, Josh Gould -- here today! -- and Oli Scherer.
]

???

But it doesn't stop there. In fact, there's a ton of invisible "glue work"
that goes into making a projection function. Helping to share this load
has such a large impact -- much more impact, ironically, than writing code.

One area I particularly want to call out is moderation. Josh Gould, one of only
two moderators, is here today. Say thank you and ask them about this important,
but often thankless, work.

---

# So many new and great tools

* Open source teams at many companies
* Rust Foundation (cloud desktops for contributors, grants, fellowships, and more)

???

I think we can do a lot more to build a healthy, sustainable community.
Thankfully, we've got a bunch of great new tools.
Over the last few years, for example, the Rust compiler maintainers
have quietly gone from being mostly volunteers to having an awful lot of
people being paid to work on the compiler.

And the Rust Foundation has been experimenting with the project on new 
and interesting ideas, such as having member companies 
offering people fast cloud desktops.

---
 
# Where I hope we get to¹

* Rich, diverse set of both career maintainers and volunteers
* Inclusive community where everyone feels welcome
* Well-documented pathways to be a part of Rust
    * Structured, cohort-based² onboarding!
    * For [more than coders](https://smallcultfollowing.com/babysteps/blog/2019/04/15/more-than-coders/)!


.footnote[
    ¹ Speaking for myself here, though if you disagree, I'd like to know why.<br>
    ² Hat tip to Doc Jones, who really helped me see the importance of this.
]

???

So what should we be shooting for? I'd like to see us having a rich, diverse
set of contributors, some of whom are making a career of it, and others doing
it on the side. I want us to have well documented onboarding paths and an
inclusive community where everybody feels welcome.

---

# One last shout-out

.center.p30[![Ernest](./images/ernest.png)]
.center[    ...and the rest of the Rust Nation team.]

???

I want to close out with one last shout-out.
I've made a point to highlight people who are active in the Rust org,
especially the ones who are here today. I'm sure I missed a lot of you.
But I want to make sure we recognize the great people who assembled
such a great conference, with such great speakers, and such a great audience.
Thanks Ernest and the rest of you!

---

# Thanks

![bill&ted's council from the future](images/bill-ted-future-council.jpg)

.center["Be excellent to each other."]

???

So yes, thanks for bearing with me, even if I'm a few minutes over time,
and please, come up and say hi, I'd love to talk to you!
