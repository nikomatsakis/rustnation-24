class: center
name: title
count: false

# Rust 2024 and beyond

.p60[![Ferris](./images/ferris.svg)]

.me[.grey[*by* **Nicholas Matsakis**]]
.left[.citation[View slides at `https://nikomatsakis.github.io/rustnation-24/`]]

---

# I wear many hats

---

# Rust language designer

???

Longest surviving member of Rust team

---

# Senior Principal Engineer @ Amazon 

???

Amazon is adopting Rust for many purposes

I lead Amazon's efforts to invest in Rust and support the Rust language.

I'll talk more about this.

---

# What hat am I wearing today?

All of them.

None of them.

???

I'm here giving you my personal opinion.
I won't tell you that I wear no hats.
I don't believe a person can truly take off a hat.
I don't believe you would want them to.
I'm influenced by what Amazon needs.
I'm influenced by what people at Mozilla needed.
And I'm influenced most of all by what I see that *Rust* needs.
I'll talk more about this as I go.

What I do want to be clear on, though, is that I'm going to talk about some proposals and design directions. For the most part these represent my desires and not the consensus of the Rust language design team. 

I'll be clear about it.

---

# Rust in 2024

What I see...

* GREAT OPPORTUNITY
* GREAT RISK


---

# Rust in 2024

What I see...

* GREAT OPPORTUNITY
* ~~GREAT RISK~~ SOME RISK

???

- Cut to the chase
    - What do I see for Rust?
        - I see *opportunity*
        - I also see *risk*
        - **Stability without stagnation** has never been more important
        - I'm here to talk about what I see working great, and what I see as big priorities to improve

---

# Our North Star

### Empowering everyone to build reliable, efficient, and maintainable software

--

*Design for the long term*

???

As always, Rust's north star remains empowerment 

---

# Rust's most important value?

### RELIABILITY?

--

### PERFORMANCE?

--

### ACCESSIBILITY?

---

# Rust's most important value?

--

### STABILITY *without* STAGNATION

???

These days I tend to think of *Stability without stagnation* as our ur-value.
Rust can never be perfect. 
We'll never get everything right the first time.
But as long as we persist in growing changing and innovating, we are going to be ok.

---

# Back to the axioms

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔍 | Transparent and tunable low-level details | |
| 🔧 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

.small[**NB:** Good example of where I'm speaking for myself here:<br>
    These are not "official" values of Rust, though I think they (or something like them) should be.]

---

# Iterators are an example of performant, composable abstractions

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| .mark[🏎️] | .mark[Performant, composable abstractions] | |
| 🔍 | Transparent and tunable low-level details | |
| 🔧 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

---

# Let's tell a story

.p30[![Barbara](./images/Barbara.png)]

???

This is Barbara. She's a Rust programmer.

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

.abspos.left30.top350.p30[![Barbara](./images/Barbara.png)]

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

.arrow.abspos.left430.top300.rotSW[![Arrow](./images/Arrow.png)]

---

template: with-translated-code

.arrow.abspos.left340.top420.rotNW[![Arrow](./images/Arrow.png)]

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

--

.abspos.left650.top450.p30.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left300.top550[
.speech-bubble.barbara.right[
Which would *you* rather write?
]]

---

# Extensibility: minimal built-in

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| 🏎️ | Performant, composable abstractions | |
| 🔍 | Transparent and tunable low-level details | |
| .mark[🔧] | .mark[Extensible and productive] | |
| 🤸🏾 | Accessible and supportive | |

---

template: thumbnails

.abspos.left300.top415[
.speech-bubble.left.barbara[
*Oh hey, I could run these in parallel!*
]]

---

![Rayon](./images/Rayon.png)

.footnote[
    (I am a co-maintainer, though really Josh Stone does the lion's share of the work)
]

---
name: thumbnailspar

# One day, Barbara is thinking...

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .par_iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

.abspos.left30.top350.p30[![Barbara](./images/Barbara.png)]

.line3[![Arrow](./images/Arrow.png)]

---
template: thumbnailspar

.abspos.left300.top415[
.speech-bubble.left.barbara[
*Rayon makes this so easy!*
]]

---

# Example: Rayon

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| .mark[⚙️] | .mark[Reliable] | |
| 🏎️ | Performant, composable abstractions | |
| 🔍 | Transparent and tunable low-level details | |
| 🔧 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |

---
name: meetalan
# Let's tell a story

```rust
fn make_thumbnails(images: &[Image]) -> Vec<Image> {
    images
        .par_iter()
        .map(|image| image.make_thumbnail())
        .collect()
}
```

.abspos.left30.top350.p30[![Barbara](./images/Barbara.png)]

.abspos.left500.top350.p30[![Alan](./images/Alan.png)]

???

So some time later, Barbara has an intern Alan.

---
template: meetalan

.abspos.left300.top415[
.speech-bubble.left.barbara[
Your job is to<br>add telemetry
]]

--

.abspos.left420.top550[
.speech-bubble.right.alan[
OK!
]]

???

Alan's job is to add telemetry to this product.
In particular, they want to count how many thumbnails they made.

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

.abspos.left500.top350.p30[![Alan](./images/Alan.png)]

???

So some time later, Barbara has an intern Alan.
Alan's job is to add telemetry to this product.
In particular, they want to count how many thumbnails they made.

---
template: thumbnailsbug

.line2[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
Let's see, I'll need a counter...
]]

---
template: thumbnailsbug

.line6[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
...add 1 for each image...
]]

---
template: thumbnailsbug

.line10[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
...and log it for telemetry. Done!
]]

---
template: thumbnailsbug

.abspos.left250.top350.p30.fliplr[![Barbara](./images/Barbara.png)]

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

--

.abspos.left25.top570[
.speech-bubble.barbara.right[
Looks great! Ship it!
]]

--

.line6[![Arrow](./images/Arrow.png)]

---
.page-center[
![rewind](./images/rewind.gif)
]

---
template: thumbnailsbug

.line10[![Arrow](./images/Arrow.png)]

.abspos.left170.top475[
.speech-bubble.right.alan[
...and log it for telemetry. Done!
]]

---
template: thumbnailsbug
name: thumbnailsbugferris

.line6[![Arrow](./images/Arrow.png)]

.abspos.left235.top350.p60[
![Ferris](./images/rustacean-flat-gesture.png)
]

.abspos.left25.top570[
.speech-bubble.topright.ferris[
Hold up there buddy! What's this?
]]

---
template: thumbnailsbug

.line6[![Arrow](./images/Arrow.png)]

.abspos.left235.top350.p60[
![Ferris](./images/rustacean-flat-gesture.png)
]

.abspos.left150.top570[
.speech-bubble.right.alan[
Gee, thanks Ferris! My hero!
]]

---
.page-center[
![rewind](./images/rewind.gif)
]

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



---
template: thumbnailsbug
name: stupid-compiler

.abspos.left500.top350.p30[![Alan is sad](./images/Alan-Sad.png)]

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

---
template: stupid-compiler

.abspos.left250.top350.p30.fliplr[![Barbara](./images/Barbara.png)]

.abspos.left75.top475[
.speech-bubble.barbara.right[
Ah, yeah, this.<br>
Use `AtomicUsize`.
]]


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

.abspos.left500.top350.p30[![Alan](./images/Alan.png)]

---
template: thumbnailsfixed

.line2[![Arrow](./images/Arrow.png)]

---
template: thumbnailsfixed

.line6[![Arrow](./images/Arrow.png)]

---
template: thumbnailsfixed

.line10[![Arrow](./images/Arrow.png)]

---
template: thumbnailsfixed

.abspos.left320.top470[
.speech-bubble.right.alan[
Welp, now I know!
]]

--

.abspos.left200.top200[
.p100[![GI Joe](./images/knowing-is-half-the-battle.gif)]
]

---

# Just a story...?

--

.center[
.p60[![2 spideys meme with Niko](./images/meme.png)]
]

---



---

# Example: async

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | Reliable | |
| .mark[🏎️] | .mark[Performant, composable abstractions] | |
| 🔍 | Transparent and tunable low-level details | |
| 🔧 | Extensible and productive | |
| 🤸🏾 | Accessible and supportive | |


---

# I want to focus on these

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| .mark[⚙️] | .mark[**Reliable**] | 👈🏽 |
| 🏎️ | ~~Performant~~ | ✅ |
| 🔍 | ~~Transparent and tunable~~ | ✅ |
| 🔧 | Extensible and productive | ⬅️ |
| 🤸🏾 | Accessible |  ⬅️ |

---

# Async Rust can be so very cool

---

# Core idea: future

```rust
async fn process_row(row: Row) -> Result {

}

future.await
```

---

# Embassy example

---

# Streams example

```rust
let rows = db.select_rows()
    .map(async |item| process_item().await)
    .buffered(5);
```

---

# But it also have more than its share of gotchas

```rust
let rows = db.select_rows()
    .map(async |item| process_item().await)
    .buffered(5);
while let Some(row) = rows.next().await {
    process_row(row).await;
}
```

--

See the bug?

--

.line4[![Arrow](./images/Arrow.png)]

---

# But it also have more than its share of gotchas

---

# Reliability in unsafe code


---

# cve-rs

---

# way forward

---

# make safety proof be the mark of a good package

---

# I want to focus on these

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | ~~Reliable~~ | ✅ |
| 🏎️ | ~~Performant~~ | ✅ |
| 🔍 | ~~Transparent and Tunable~~ | ✅ |
| .mark[🔧] | .mark[**Extensible and Productive**] | 👈🏽 |
| 🤸🏾 | Accessible |  ⬅️ |

---

# Proc macros, custom derive are so cool

---

# But also so limited

---

# Custom diagnostics

---

# Custom lints

---

# Custom refactorings??

---

# I want to focus on these

| | What makes Rust *Rust*? | |
| :-- | :-- | :-- |
| ⚙️ | ~~Reliable~~ | ✅ |
| 🏎️ | ~~Performant~~ | ✅ |
| 🔍 | ~~Transparent and Tunable~~ | ✅ |
| 🔧 | ~~Extensible and Productive~~ | ✅ |
| .mark[🤸🏾] | .mark[**Accessible**] | 👈🏽 |

---

# Accessible

Not the language.

Always room to do more.

---

# Accessible
