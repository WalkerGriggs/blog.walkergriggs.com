+++
title = "walkergriggs.com source file"
author = ["Walker Griggs"]
description = "What started as a 1 terabyte external harddrive loaded with a few sentimental photos has turned into a 40TB NAS and 26TB worth of offline drives. This post is an attempt to answer 'how I store and track offline files.'"
draft = false
creator = "Emacs 27.1 (Org mode 9.6.6 + ox-hugo)"
+++

## Posts {#posts}


### <span class="org-todo todo TODO">TODO</span> Digital Homesteading <span class="tag"><span class="_essays">@essays</span></span> {#digital_homesteading}

Tech is [changing](https://trends.google.com/trends/explore?cat=5&date=2011-01-01%202021-01-01&q=%2Fm%2F011spz0k,%2Fg%2F11b7lxp79d,%2Fm%2F0wkcjgj). Whether you want to call it horitzontal scaling, scaling out, distributing, or deconstructing; the ways we structure, write, test, and deploy systems is changing.

I argue though, that the ways we learn, however, are not changing but should be. Learning the latest, individual abstraction isn't enough anymore. Side projects are often too narrow and our exposure to "enterprise systems" is limited. We, as engineers, are not adequately tailoring our "studies" to fit the needs of industry... but we could be.

I propose a form of continuous learning called "digital homesteading" which emphasizes composition and encourages self-sufficiency.

<!--list-separator-->

-  Homesteading, generally

    Homesteading is synonymous with the Homestead Act of 1862 which granted US citizens a western tract of 160 acres should they be willing to settle and farm the land. Generally, the US governemnt used homesteading to incentive western expansion, but we'll ignore the political machinations. Fast forward to the 1970, the Back to the Land Movement worked to similar effect, where people took up rural smallholdings in search of increased autonomy and self-sufficiency.

    Homesteading, in this context, is analogous to self-sufficiency. More often than not, homesteaders were physically seperated from society or relied on a small, local community. They grew their own crops, hunted their own game, built their own shelters, and mended their own fences. If their roof leaked, they patched it. If their clothes tore, they patched them just the same. The list goes on, but in every example, they had to rely on their own intuition and experience to solve their daily problems. If they didn't have experience with a particular trade, they were pretty well incentivised to learn.

<!--list-separator-->

-  Continuous learning, generally

    As is common in ever-changing industries, engineers need to constantly onboard new material, practice our craft, and mind our information diet. Most importantly, we need to learn in ways which compliment idustry needs.

    Speaking to my own experience, my typical "learning lifecycle" is fairly sequential and well deliniated. I'll think up a project which suits the some topic. If I'm feeling ambitious, I might even blend two new topics; a language and paradigm, for example. From there, I'll start reading documentation, lay the groundwork, and mould the core behaviors. More often than not though, that project ends up on the private-repo pile after a few iterations or I feel sufficiently versed on the topic. I forget about it, and move on to the next topic.

    I'd be willing to bet this pattern is pretty common. This method isn't "bad" or ineffectual, but there are some areas for improvement.

    First, like cramming for a test, we don't retain a lot of that info. I'm especially guilty of searching through old projects for a pattern or practice I found useful, but couldn't reproduce.

    Perhaps more importatnly, these projects also exist in a vacuum. We understand the bounds of the topic in isolation, but don't always see the interaction between two systems. Think of this like unit testing vs integration testing; one isolates behaviors and mocks the bounderies, the other encapulates behavior and instead focuses on interacton.

    See again: "we need to learn in ways which compliment industry needs".

<!--list-separator-->

-  Homesteading meets continuous learning

    So far we've touched on homesteading and continuous learning in practice. Let's bridge that gap by first reviewing examples of what I consider to be digital homesteading in practice, and then using those examples to derrive a few characteristics of digital homsteading in theory.

    The most approachable example is a homelab (note the shared root: "home"). An average homelab might be a few rasberry pis as "compute nodes", an old laptop repurposed as a NAS, or maybe a desktop as a router. You, as the "homesteader", might run KVM or ESXI (type 1 hypervisors) on a makeshift server. You might run Telegraf, InfluxDB, and Grafana to collect, store, and visualize hardware metrics. You might also setup a home network with Pfsense and stream movies with Plex. Slowly, you're building out an ecosystem of systems and services.

    Another example. Say you're in the market for a new graphics card, but are having trouble following the various stock trackers, raffles, and notifications. You might write a web app that lets you define alerts through a simple domain specific language. Of course, your friends on discord or slack or IRC want to use that app too. Everyone loves a good chatbot and there are lots of off the shelf solutions, but maybe you want to write your own. You'll want to understand the bots failure modes, so you setup Rollbar or Sentry to error tracking. Maybe you'll even want to push soft touch alerts to your home, so you write a Philip Hue integration. The possibilities are endless.

    In both examples,

    -   We're building an ecosystem. We're layering services or systems which interact with and complement eachother.
    -   Our services persistent, but not production.
    -   The individual components span multiple layers.
    -   Each service provides useful but not vital functionality
    -   We're self sufficient along at least one vertical.

    <!--list-separator-->

    -  Ecosystem

        We're not just considering how an individual component behaves, but how multiple systems interact. Enterprise servces are transitioning to horizontal systems of scale, and we need to factor that into our design process.

        Consider your digital homestead. Where is the barn in relation to the fields? The food cellar? Have we considered how the three systems work in concert? With regards to our more tangible example: have we considered how our discord bot pulls information from the web app? Are they tighly coupled? Does the webapp implement any business logic, or just expose the DSL? Do the latest stock alerts need to be persisted, or only cached?

    <!--list-separator-->

    -  Persistent

        Digital homesteads should run around the clock. According to the 2020 Stack Overflow Survey, DevOps and Site Reliability Engineers are value multipliers in enterprise environments.

        > Site reliability engineers and DevOps specialists remain among the highest paid individual contributor roles. 80% of respondents believe that DevOps is at least somewhat important, and 44% work at organizations with at least one dedicated DevOps employee.

        Persistent homesteads go beyond SRE though. When we take responsibility for supporting every stage of software development -- when we're product owners responding to feature requests, senior leadership driving priority, on-call operators triaging downed systems, SRE debuggig service blips, and DevOps implementing resilient runtime environments -- we're service owners.

        Service ownership is overlooked in the majority of continuous learning projects, despite it being such a critical facet of successful enterprise services.

    <!--list-separator-->

    -  Span multiple layers

        It's important to think about where and how things are run. This diversity adds perspective

    <!--list-separator-->

    -  Useful but not vital

        This bullet ties back to the "persistent but not production" mantra. You're only going to resent your digital homestead if you rely on it for "business critical" tasks. These systems will be flawed, they will take time, they will break, and you will need to fix them.

        Hosting an SMTP server for your professional email or writing a React clone for an enterprise service is objectively a bad idea. In the end of the day, we're not looking to reinvent the wheel, but to instead understand why the wheel is fabulous, how the wheel is fallable, and how the wheel can be leveraged to great success.

        If we give our homestead value, we'll stay invested. If we rely on our homestead to feed the neighborhood, we risk a famine.

    <!--list-separator-->

    -  Self-sufficient

        In self-sufficiency, we find the most valuable lessons. If something isn't readily available, we can write it ourselves. If we aren't immediately sure how to write it ourselves, we can learn through trial and error.

        Of course you could follow this rule to an extreme -- I'm not suggesting we write our own compilers (though you certainly could challenge yourself). I'm suggesting that in an industry of higher order abstarctions, we might consider our own Back to the Land Movement.


### <span class="org-todo todo TODO">TODO</span> State Machines All the Way Down <span class="tag"><span class="_essays">@essays</span></span> {#state_machines_all_the_way_down}


### <span class="org-todo todo TODO">TODO</span> A Standard for Password Management <span class="tag"><span class="_devlogs">@devlogs</span></span> {#standard_for_password_management}

<!--list-separator-->

-  tldr;

    Passwords are inherently insecure. We've layered a number of secure practices (some consumer facing, others system facnig) like MFA, security questions, oauth, and OIDC to complimen passwords and have built supporting systems like password managers to enable users to reliably and safely use sufficiently secure passwords, but we haven't written a standard for password management.

    I propose a standard set of endpoints which let users, or password managers by proxy, programatically manage their passwords.

    Use case: Say a user has 100 accounts at 100 different websites. Some, but not all support MFA. The user wants to rotate their passwords semi-regularly. Currently, they have to visit each of the 100 websites, login, navigate through unique account settings,  manually update their password, and update their password manager.

    Instead, a user should be able to press one button in their password manager which will programatically generate a new password and update the account settings through the proposed endpoints. Better yet, the password manager should do this automatically every N days without the user needing to trigger the process.


### <span class="org-todo todo TODO">TODO</span> Five Years with Emacs <span class="tag"><span class="_devlogs">@devlogs</span></span> {#five_years_with_emacs}


### <span class="org-todo done DONE">DONE</span> Coding Diddles <span class="tag"><span class="_essays">@essays</span></span> {#coding_diddles}

> "If you fail in copying from a master you succeed in birthing an original art", Kushal Poddar

Last year, a colleague of mine picked up woodcarving. They told me about their battle with the “originality demon” and how, even when learning a new and productively right-brain skill, they felt every knife stroke needed to be an original one. Each complete whittle needed to an attractive addition to a catalog of novel works.

Then a content creator – a carving guru, as my colleague referred to him – referred to some of their more simple or instructive carvings as “diddles”. These diddles were common, practiced, and rehearsed; there’s absolutely nothing original about these them. He event went as far as to dictate each cut as if they were notes on a staff. Yet, they were a critical part of this creator's trade, and so my colleague took solace in the idea that regardless of profession or experience, we need to iterate on the trite before we can produce even a modicum of original work.

My colleagues' story resonated with me; programming works the same way.

I can't count the number of times I've stumbled on a new idea, excitedly put pen to paper, and resurfaced a few hours later to learn -- after some light 'market research' -- that someone else has solved the problem. At that point I’m faced with the decision to write it off as a fun investigation or to forge ahead knowing that someone beat me to the punch. And of course someone else has! Given the glut of public repositories on Github alone, it’s hard to imagine some problems haven’t been solved.

I wouldn’t call this a particularly productive outlook, but for some innate reason it’s a shared human experience. We want to be adventurers and make great discoveries, and yet the most notable advances are often those in a solved fields.

Take chess, for example. The further a player deviates from the "main line" or accepted variation, the higher their odds of finding a novelty -- a move no one has considered before in that position. 99.9999% of those novelties aren't fabulous moves, but there's a one-in-an-infinitesimally-small chance they've discovered something game changing. Chess is not a solved game; that's why we continue to play. On the surface, it looks like there are a finite number of moves. On the surface, every player has perfect knowledge. And on the surface, there shouldn't be a stone un-turned. For those reasons alone, finding novelties Chess is exhilarating. Repetition, learning the lines, and studying old games are the only way you'll find a novelty worth its salt.

Like chess games or wood carvings, frame your programming projects as diddles. Sorting algorithms, data structures, security groups, EMNIST data, hello worlds – all are diddles. There’s nothing original about heap sort and certainly classifying handwritten letters seems like a solved problem. We should take solace in that. Before we write our magnum opal, we should understand existing systems. How can we presume to be entirely original until we know all existing prior art.

There’s another part to diddles too. In a recent post about Basic English and controlled languages, I touched on that, to learn quickly we need to first learn slowly. By limiting the syllabus to the most common parts, we’re giving ourselves time to build a solid, reliable, and practical foundation. My colleague may have carved 15+ canoes in one weekend, but their last iteration was infinitely better than their first. By freeing themselves from the need to produce original work, they were able to focus on the techniques of carving.

Thinking about my own experience learning Go, I probably wrote just as many CLIs as my colleague has carved canoes. CLIs aren’t sexy and they’re most certainly not novel. But now I can whip out a CLI faster than you read this post. And how many times have I needed to in the wild. Tons!

So write like Didion! Paint like Jackson! Dribble like Jordan!

Practice your diddles, re-implement your darlings, and study how “innovations” make use of your favorite data structures. Before you blow anyone’s mind, first learn what makes their brain tick.


### <span class="org-todo done DONE">DONE</span> Basic English <span class="tag"><span class="_essays">@essays</span></span> {#basic_english}

> It takes only 400 words of Basic to run a battleship; with 850 words you can run the planet.
>
> Ivor Armstrong Richards

I'm terrible at learning foreign languages. In fact, I studied Latin for 8 years -- a dead language for all intents and purposes -- and hardly remember a thing. Recently I tried learning Italian; that fell by the wayside too.

My experience with foreign languages could probably be summed up in one word: overwhelming. Gerunds and gerundives. Participle. Present perfect imperatives. Yet, somehow, there's a sizable population of polyglots out there who learn languages, or at least the basics, in just a few weeks. How? Enter: Basic English.

Basic English is a controlled language, or a whittled down version of a language meant to reduce complexity and improve comprehension. Charles Ogden and Ivon Richards designed Basic English as a tool for those learning English as a second language. Odgen believed that the fastest path to become conversational in any language was to learn only the most used words.

Of the hundreds of thousands of words in the English language, Basic is only 850. Britches, breeches, bell-bottoms, blue jeans -- who cares, so long as you can say "pants".

Of course, this got me thinking about my experience learning to code, or work with computers more generally. Honestly, Basic English is not far off.

In high school, we wrote hundreds of lines on paper well before we typed a single character into a text editor. Before we learned loops, we learned about variables. Before variables: types. The syllabus was condensed to 850 words (or whatever the programming equivalent is), and we kept to it. Our diction was limited, and we drilled those core principles home.

Jump forward however many years, and my experience learning Rust was vastly different. I dove straight into traits and borrowing and async, and I ultimately failed to learn the language. I don't know Rust any better than I know Italian. I didn't limit myself to 850 words.

My initial revision of this essay proposed (or at least attempted to) a model to evaluate programming languages. My reasoning was that math, philosophy, and computer science are fundamentally just syntaxes to express logic, arguments, and reasoning. A well designed language, so I reasoned, <span class="underline">wasn't</span> a language with many bells in whistles. Instead, it applied routine, boring, consistent, trite syntax to great effect.

That train of thought is a logical fallacy though: a faulty parallel construction. Controlled languages don't help <span class="underline">evaluate</span>, they just improve legibility for non-native speakers. Rust isn't a bad language by any stretch, and English isn't either -- they're just difficult to grok for the first-time speaker.

So what can we learn from controlled languages as programmers, architects, or designers?

****1) Learn slowly to learn quickly****

What did my experience with Rust teach me? You're never too experienced, smart, or savvy to start from square one. The core contributors of Rust literally wrote [a book on getting started](https://doc.rust-lang.org/stable/book/) for a reason.

This takeaway is the more obvious of the two, but we willingly walk ourselves into a trap when we jump straight to complex features, patterns, or idioms. We push well past those 850 words, and sabotage our learning process.

****2) Simple code is empathetic code****

I <span class="underline">love</span> writing list comprehensions in Python! My caveman brain releases endorphins when I realize how much I can do in only one line. Paradoxically, though, list comprehension can be... incomprehensible.

We need to write code with the understanding that someone in a galaxy far far away will need to read it.

In my case, maybe that person is a colleague who isn't familiar with Python. Maybe they're a contractor who knows Python, but it's been a while. Or maybe I've switched companies, and am not around to answer their questions. By saving myself a few keystrokes, I've cost someone valuable minutes; I'm not respecting their time.

Of course, list comprehension is a small example, but this principle applies just as well to complex patterns and sprawling systems. Simplicity is empathy.

All in all, controlled languages are an interesting theory and intuitively make so much sense. I likely won't be fluent in Italian any time soon, but I'll certainly remind myself to slow down and keep it stupid simple. I might even revisit Rust and do it right this time.


### <span class="org-todo done DONE">DONE</span> Learning Go Generics with Advent of Code <span class="tag"><span class="_devlogs">@devlogs</span></span> {#learning_go_generics_with_aoc}

_This post is a living draft and may be revised. If you have any comments, questions, or concerns, please reach out._

Yesterday, the Go core team released [go1.18beta1](https://go.dev/blog/go1.18beta1) which formally introduces generics. There isn't a whole lot of info circulating yet aside from git history and [go-nuts](https://groups.google.com/g/golang-nuts) experiments, but the overall reception feels very positive.

Personally, I've been hands on with generics for the better part of a week all thanks to the [Advent of Code](https://adventofcode.com), which has been the perfect venue to take generics for a spin. If you're not familiar with AOC...

> Advent of Code is an advent calendar of small programming puzzles for a variety of skill sets and skill levels that can be solved in any programming language you like. People use them as a speed contest, interview prep, company training, university coursework, practice problems, or to challenge each other.
>
> You don't need a computer science background to participate - just a little programming knowledge and some problem solving skills will get you pretty far. Nor do you need a fancy computer; every problem has a solution that completes in at most 15 seconds on ten-year-old hardware. -- [Eric Wastl](http://was.tl/)

This article will cover the basics of generics (or enough to get you started) and uses my AOC experiments a case study.

<!--list-separator-->

-  Generics, generally

    Go feels immediately more flexible with generics. The language is less prescriptive but still opinionated, and the implementation feels wonderfully idiomatic. But what do I mean by that?

    For starters, generics feel very low-touch from a developers point of view. They've only added three new features:

    -   Type parameters for functions and types
    -   Type sets defined by interfaces
    -   Type inference

    <!--list-separator-->

    -  Type parameters

        Type parameters are one or more name-type parings that look visually similar to our standard parameters; the only difference being type params are surrounded by square brackets, not parentheses. The square brackets, thankfully, are a consistent syntax you'll see used in struct declarations and variable initialization.

        ```go
        [a, b constraint1, c constraint2]
        ```

        Consider the `Max` function you've written dozens of times. We can now replace our strongly typed numeric like `int32` or `float64` with a far more permissible type parameter `T`. `T`, in this instance, is any type which fulfills the `Ordered` constraint (which we'll circle back to constraints shortly).

        ```go
        func Max[T constraints.Ordered](x, y T) T {
            if x > y {
                return x
            }
            return y
        }
        ```

        When we call this function, we have to explicitly pass the type argument as part of the functions instantiation. Instatiation is a two part process where the compiler...

        1.  substitutes the type argument for all instances of the respective type parameter. In our case, the two `T` arguments and one return value are swapped to be `int` specifically.
        2.  checks that the two function arguments implement the constraints. The compiler will fail to instantiate if this step fails. Again, in our case, the compiler checks that 3 and 4 satisfy the `Ordered` constraint.

        <!--listend-->

        ```go
        max := Max[int](3,4)
        ```

        It's also worth pointing our that the function call above both instantiates and runs the function. We could instantiate the function separately, which might be a slight optimisation in some cases.

        ```go
        maxInt := Max[int]

        max := maxInt(3,4)
        ```

        As for data structures, these type parameters work the same way. Types can optionally have a type parameter list, and methods of that type must declare matching type lists in the receiver.

        ```go
        type Grid[T any] struct {
            values        []T
            height, width int
        }

        func (g *Grid[T]) At(x, y int) T {
            return g.Values[(g.height * y) + x]
        }

        var grid Grid[int]
        ```

        Notice the `any` keyword? It's now an alias for `interface{}`!

    <!--list-separator-->

    -  Type sets and constraints

        So what are these "constraints" we've been tossing around?

        Constraints are a new package in the standard library that describe type sets. Type sets are just lists of types which satisfy some target behavior. For example, the `Signed` constraint is the set of all signed integer types, and the `Integer` constraint is the union of `Signed` and `Unsigned`. To check if a type satisfies a constraint, the compiler just checks if that type is an element in the constraint's type set.

        At the time of writing this, there are only six, simple constraints: `Signed`, `Unsigned`, `Integer`, `Float`, `Complex`, and `Ordered`. `Ordered` is the most permissive and includes all floats, integers, and strings; and was the constraint I reached for most often in initial testing.

        ```go
        // Signed is a constraint that permits any signed integer type.
        // If future releases of Go add new predeclared signed integer types,
        // this constraint will be modified to include them.
        type Signed interface {
                ~int | ~int8 | ~int16 | ~int32 | ~int64
        }

        // Integer is a constraint that permits any integer type.
        // If future releases of Go add new predeclared integer types,
        // this constraint will be modified to include them.
        type Integer interface {
                Signed | Unsigned
        }
        ```

        You may have also noticed that these constraints are actually interfaces under the hood. Traditionally, interfaces have defined a 'method set' and every type which implements those methods implements that interface.

        The other perspective, and one which is more relevant to generics, is that interfaces describe a set of _types_ and the method set is only a means by which we filter the set of _all types_ -- the empty interface. It seems only reasonable then that we should be able add a specific type to that list directly.

        Well, as of `1.18beta1`, interfaces _can_ enumerate types directly by way of a type set (`Signed | Unsigned`, for example). Of course, method sets as we have known then are still 100% compatible and preferred in many cases.

        In summary, type constraints are just interfaces and the types which satisfy those constraints are those enumerated by the interface. When you're defining a generic function with a constraint, you're basically defining a big list of all possible argument types.

        For now, this flavor of type set interfaces can only be used as function constraints, but in the future I would like to see variables loosely typed according to a given constraint.

<!--list-separator-->

-  Advent of Code

    Day 9 or "Smoke Basin" is a fun exercise in navigating grids which boils down to "can you find elements in a grid in which all surrounding 'neighbors' are larger than it". Before we dive into the puzzle logic, lets setup our data structures.

    Fortunately, grids are common data structures in the Advent of Code, but unfortunately one that I've rewritten a number of times depending on the element type. My preferred approach is to structure the grid as a list and to define several helper methods to access elements with X,Y coordinates.

    We'll need to directly compare Grid elements but would like this to be reused for, say, ASCII characters in the future, so the `Ordered` constraint makes the most sense.

    ```go
    type Point struct {
            X, Y int
    }

    type Grid[T constraints.Ordered] struct {
            H, W int
            Vals []T
    }
    ```

    As for the helper methods, notice how the function receivers also specify the generic type `T`? That tells the compiler that these methods are applicable to any Grid which meets its constraint. A receiver like `(g *Grid[int])` would only be applicable to integer grids. Otherwise these are standard helper methods to access generic values in the grid, either by point coordinates, index, or relative direction.

    ```go
    // Index returns the integer index value for a grid element given some point.
    func (g *Grid[T]) Index(p *Point) int {
            return (p.Y * g.W) + p.X
    }

    // Point returns the a point object for a grid element given some index.
    func (g *Grid[T]) Point(i int) *Point {
            return &Point{
                    X: i % g.W,
                    Y: i / g.W,
            }
    }

    // At returns the element found at some given point.
    func (g *Grid[T]) At(p *Point) T {
            return g.Vals[g.Index(p)]
    }

    // InBounds returns true if the point is within the grid, and false if not.
    func (g *Grid[T]) InBounds(p *Point) bool {
            return p.X >= 0 && p.X < g.W &&
                    p.Y >= 0 && p.Y < g.H
    }

    // Neighbors returns a list of point objects for each (in-bound) element of the
    // grid, given a list of directions. For example, the direction (1,0) would be
    // the point to the right.
    func (g *Grid[T]) Neighbors(p *Point, directions []*Point) (points []*Point) {
            for _, direction := range directions {
                    tmp := p.Add(direction)
                    if g.InBounds(tmp) {
                            points = append(points, tmp)
                    }
            }
            return
    }
    ```

    Finally, the puzzle logic.

    The puzzle input for day 9 was a grid of integers where each point represented the depth of the sea floor with 0 being the lowest and 9 being the highest. The first part of the puzzle is to find all of the low points (a point where the neighboring values are all greater) and add their values.

    A simple solution is to iterate over the grid, check if each point is a "low point", and add the low point's values to a running total. There are a number of optimizations we could make here, but lets stick with the direct approach first.

    ```go
    // IsLowPoint returns true if the given Point is lower than all its neighbors,
    // and false if not.
    func IsLowPoint[T constraints.Ordered](grid Grid[T], target *Point) bool {
            for _, p := range grid.Neighbors(point, FOUR_AXIS_DIRECTIONS) {
                    if grid.At(p) <= grid.At(target) {
                            return false
                    }
            }
            return true
    }

    // LowPoints returns a list of Points which correspond to all the low points in
    // some given grid.
    func LowPoints[T constraints.Ordered](grid Grid[T]) (points []*Point) {
            for i := range grid.Vals {
                    point := grid.Point(i)
                    if IsLowPoint(grid, point) {
                            points = append(points, point)
                    }
            }
            return
    }

    // PartOne returns the sum of the values of all the low points in some given
    // grid.
    func PartOne(grid Grid[int]) (sum int) {
            for _, point := range LowPoints(grid) {
                    sum += grid.At(point) + 1
            }
            return
    }
    ```

    A few things to note. In `PartOne`, we're actually specifying that our generic grid is a grid of integers. Although the addition operator is technically defined on strings for concatenation, the compiler knows that the return value must be an integer and the `Ordered` type set includes strings and floats. So to guarantee type safely, the compiler will enforce a strongly typed grid. The `LowPoints` and `IsLowPoint` functions only ever perform comparisons on grid values, so those can stay generic.

    Part two is an iteration on the Grid we've just written, so I'll leave that as an exercise for you.

<!--list-separator-->

-  Final thoughts

    Up until `1.18beta1`, I was frequently copying and pasting data structures and helper methods. In the best case, that led to code duplication. In the worst case, that led to unnecessary extraction and  abstraction. Generics feel like a handy way to inject flexibility into your code without resorting to re-use or adapter patterns, for example. That said, I'll have to see sufficiently complex implementations to form any lasting opinions.

    At this point, I worry that -- like any new, shiny tool -- developers will look to cram generics wherever they can. Frankly, I think that generics will make the biggest impact in standard libraries -- not your application backend. The most obvious example is `math`, where currently _every_ function takes a `float64` and requires a significant amount of casting if you're working with integers (`int(math.Abs(float64(value)))`).

    As for AOC, I'm all for using [container/heap](https://pkg.go.dev/container/heap) to implement a priority queue once in a while, but rewriting methods like `Abs`, `Max`, and `Min` is slow and inefficient. Even the standard 2-dimensional grid gets repetitive after a while. As a result, puzzlers have written their own [libraries of helper methods](https://github.com/Bogdanp/awesome-advent-of-code#go) to speed things along; contents range from simple data structures to stdin readers tailored to AOCs input.

    I tried writing a library myself last year, but it felt brittle. Grids wont always contain integers and I should be able to compare strings just as easy as numerics. Interfaces might have been an option, but felt clumsy for my use case.

    Enter: generics. I'm taking another stab with the help of `1.18beta1` -- all contributions are welcome.


### <span class="org-todo done DONE">DONE</span> ZNC, the right way <span class="tag"><span class="_devlogs">@devlogs</span></span> {#znc_the_right_way}

I've setup [ZNC](https://wiki.znc.in/ZNC) one too many times.

Sometimes I forget it's [riding shotgun](https://en.wikipedia.org/wiki/Riding_shotgun) on a spare droplet heading to the trash heap. Other times, my payment method expires and so too does the instance. Other times I'm too lazy to host it in the cloud at all, so I run it locally. In any case, today I wanted to set up ZNC the right way... for the last time.

I also want to document the process for posterity and stop scouring the web for the same articles time after time.

The TODO list for today:

-   Setup a dedicated domain
-   Provision a dedicated droplet, hosted on [DigitalOcean](https://www.digitalocean.com/)
-   Configure separate listeners for IRC and HTTP traffic
-   Generate an SSL cert with [LetsEncrypt](https://letsencrypt.org/)
-   Setup [Nginx](https://nginx.org/en/) to terminate SSL traffic and proxy to ZNC


#### Dedicated domain and droplet {#dedicated-domain-and-droplet}

I'll gloss over the relatively simple steps like [provisioning a droplet](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04), [securing the firewall](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04), [installing ZNC](https://wiki.znc.in/Installation), and [purchasing a domain](https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars).

tldr; I...

1.  Provisioned a droplet.
2.  Purchased a new domain. I opted for a `.chat` TLD because I thought it was appropriate
3.  Directed the registrar to DigitalOcean's nameservers. Consolidating behind a single control panel makes life much easier.
4.  Created an A record with an `irc` subdomain pointing at the IP of my new droplet.

For the remainder of this post, I'll use `irc.example.chat` as my placeholder domain!


#### Configuring ZNC {#configuring-znc}

How you configure ZNC is a matter of personal taste. I opt to load fairly standard modules like [chanserver](https://wiki.znc.in/Chansaver), [fail2ban](https://wiki.znc.in/Fail2ban), [log](https://wiki.znc.in/Log), and [identfile](https://wiki.znc.in/Identfile) but feel free to go crazy! One thing that is important to mention though, are the separate listeners.

I created one listener for SSL IRC traffic over 6697 and one listener for non-SSL HTTP traffic over 8080. The web listener has SSL disabled because 1) it's only a self signed cert 2) it's only hosting to `localhost`.

```xml
<Listener listener0>
    AllowIRC = true
    AllowWeb = false
    IPv4 = true
    IPv6 = false
    Port = 6697
    SSL = true
    URIPrefix = /
</Listener>

<Listener listener1>
    AllowIRC = false
    AllowWeb = true
    Host = localhost
    IPv4 = true
    IPv6 = false
    Port = 8080
    SSL = false
    URIPrefix = /
</Listener>
```


#### Configuring Nginx {#configuring-nginx}

I'll first preface this section by saying: I'm not an Nginx wizard by any means. In fact, most of this configuration comes from the [Nginx blog](https://www.nginx.com/blog/using-free-ssltls-certificates-from-lets-encrypt-with-nginx/) and [Stack Overflow](https://stackoverflow.com/questions/34236949/znc-on-a-subdomain-with-nginx-reverse-proxy).

Before we can generate a certificate, we want to add a basic configuration. I dropped a file in `/etc/nginx/config.d` and create a softlink to `sites-available` and `sites-enabled`.

```bash
touch /etc/nging/config.d/irc.example.chat
ln -s /etc/nginx/config.d/irc.example.chat /etc/nginx/sites-available
ln -s /etc/nginx/config.d/irc.example.chat /etc/nginx/sites-enabled
```

I then edited the parent configuration. Fortunately, it's fairly readable; nginx will proxy all SSL traffic from `irc.example.chat` to our ZNC localhost listener. We can also set a few headers in the process.

```text
server {
    listen      443 ssl http2;
    server_name irc.example.chat;
    access_log  /var/log/nginx/irc.log combined;

    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_set_header      Host             $host;
        proxy_set_header      X-Real-IP        $remote_addr;
        proxy_set_header      X-Forwarded-For  $proxy_add_x_forwarded_for;
        proxy_set_header      X-Client-Verify  SUCCESS;
        proxy_set_header      X-Client-DN      $ssl_client_s_dn;
        proxy_set_header      X-SSL-Subject    $ssl_client_s_dn;
        proxy_set_header      X-SSL-Issuer     $ssl_client_i_dn;
        proxy_read_timeout    1800;
        proxy_connect_timeout 1800;
    }
}
```

The `ssl_certificate` configs will be added by `certbot` in the next step. If they aren't added for whatever reason, they should look something like...

```text
ssl_certificate     /etc/letsencrypt/live/irc.example.chat/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/irc.example.chat/privkey.pem;
```


#### Generating certs with LetsEncrypt {#generating-certs-with-letsencrypt}

Now the fun part, and the reason to setup the domain in the first place. I used the [EFF's](https://www.eff.org/) handy [certbot](https://certbot.eff.org/) with Nginx drivers to provision a cert with LetsEncrypt. Technically the Nginx drivers aren't necessary -- you could provision the certs directly -- but the added config editor is a nice feature.

`certbot` took care of just about everything!

```bash
sudo apt-get install certbot python3-certbot-nginx

certbot --nginx -d irc.example.chat
```

I say "just about" because these certs still expire every 90 days. I'm guaranteed to forget about the cert, so I set a cron job (`sudo crontab -e`) to renew the cert every week.

```text
0 0 * * 0 certbox renew --quiet
```


#### Configuring Weechat {#configuring-weechat}

The last step of any ZNC install is to setup your client. I use [Weechat](https://weechat.org/), so the next steps may be different for you.

Weechat needs to validate ZNC's SSL cert to connect over `6697`, so grab the SSL certificate fingerprint from the droplet first.

```bash
cat ~/.znc/znc.pem \
    | openssl x509 -sha512 -fingerprint -noout \
    | tr -d ':' \
    | tr 'A-Z' 'a-z' \
    | cut -d = -f 2
```

On the weechat client, I added the `ZNC` server with a default network, set the fingerprint, connected, and saved my changes. One detail that I forget constantly: these creds aren't your network creds, they're your ZNC creds.

```text
/server add ZNC irc.example.chat/6697 -ssl -username=username/network -password=password
/set irc.server.ZNC.ssl_fingerprint <fingerprint>
/connect ZNC
/save
```

Most networks require you to authenticate with SASL these days, which I set through Weechat. Another option is to load the SASL module and set your credentials through the web console.

```text
/msg *Status LoadMod sasl
/msg *SASL Set nick pass
/msg *SASL RequireAuth true
```

And that's about it. We've setup the A record for our domain, configured separate HTTP and IRC listeners for ZNC, generated an SSL cert through LetsEncrypt, proxied web traffic to ZNC with Nginx, and connected securely with Weechat. A pretty productive afternoon!

If you'd like to chat, you can find me on [libera.chat](https://libera.chat/)!


### <span class="org-todo done DONE">DONE</span> A Year with Emacs <span class="tag"><span class="_devlogs">@devlogs</span></span> {#a_year_with_emacs}

<span class="underline">It is important to preface that everything in this article is opinion and based off (roughly) a year of heavy Emacs usage. It is also important to know that this article will be updated along side my configuration and tastes. So without further ado...</span>

We all know Emacs is an immensely powerful beast. We also know how easy it is to venture down a rabbit hole of elisp and never surface. I liken it to a carpenter replacing a door. After removing the old door, he notices the hinges are askew. He removes the hinges only to notice rot in the door frame. By the time he replaces the frame, he notices a slight difference in shade between the new frame and old moldings... The learning curve for Emacs is wonderfully circular. That being said, I would like to take a moment and explain my configuration in moderate detail.

Before I get too technical, I should probably explain my fascination and reservation with Emacs. Brief background: I was forced into using Emacs when the only other editor on the lab machines was Gedit (and Vi, but we'll forget about that for now). In all honestly, it was quite a hassle. I began compiling a minimal init.el out of necessity. Linum, flyspell, you name it. It was certainly a gradual transition from cushy Atom, but, after a long while, it became an addiction. It wasn't until I discovered a keyboard designed with Emacs in mind (Atreus) did I see Emacs (and the devoted community) in all of its glory.

As for my reservations...

> The learning curve is far too steep. My time is best spent elsewhere.

WRONG. The weeks of struggling with Meta keys and Emacs pinkie pays off. Trust me. My workflow has increased substantially, and I feel extraordinarily comfortable in my configuration. Granted, emacs is truly a lifestyle. Embrace it.

> It's a bloated editor packed with legacy functionality. The startup time is just too long!

MYTH. You think Emacs is too heavy for you system? Try running Eclipse and Chrome simultaneously and then get back to me. As long as your config file is optimized (cough cough 'use-package'), the startup time won't be longer than a couple of seconds. Granted, on a system with limited resources, Vi may be a better option. Which brings me to my biggest qualm. Vi is an editor. Emacs is an editor AND IDE. When remoting into a server, I'm not about to Xforward a fully functional Emacs when bandwidth and memory are scarce. For that reason, I keep a modest .vimrc on hand for some quick cli editing.

<!--list-separator-->

-  Configuration

    <!--list-separator-->

    -  melpa and use-package

        Melpa is a very common package manager for Emacs. I try not to rely on it, though it certainly comes in handy. The simple (and recommended) solution...

        ```lisp
        ;; Melpa
        (require 'package)
        (setq package-enable-at-startup nil)
        (add-to-list 'package-archives
          '("melpa" . "https://melpa.org/packages/"))
        (add-to-list 'package-archives
          '("melpa-stable" . "http://stable.melpa.org/packages/"))
        ```

        Now it wasn't until a friend picked through my config when I learned about 'use-package'. UP is a wonderful macro written by John Wiegley that declares and isolates packages in your config. Each package can then be initialized, configured, and bound independently. This is a must use...

        ```lisp
        ;; Bootstrap 'use-package'
        (unless (package-installed-p 'use-package)
            (package-refresh-contents)
            (package-install 'use-package))
        (setq use-package-verbose t)
        ```

    <!--list-separator-->

    -  tabs / whitespace

        The next few go hand in hand: tabs and whitespace. I'd like to reiterate, these are simply opinions. Feel free to disagree, but I cannot stand tabs in my code. Tab size varies across environments but a space will ALWAYS be one column. Case closed. That being said, tab functionality is quite nice, so I've turned indent-tabs-mode to nil. Simply...

        ```lisp
        (setq-default indent-tabs-mode nil)
        (setq-default tab-width 2)
        ```

        The next is an acquired taste: whitespace-mode. Ever since I properly configured my whitespace (invisibles) to be tastefully visible, I've grown to appreciate the subtly clean code. Trailing whitespace / unnecessary new lines have since disappeared.

        ```lisp
        ;; Whitespace
        (use-package whitespace
            :bind (("C-c C-w" . whitespace-mode))
            :init
            (dolist (hook '(prog-mode-hook text-mode-hook conf-mode-hook))
                (add-hook hook #'whitespace-mode))
            :config
            (add-hook 'prog-mode-hook 'whitespace-mode)
            (global-whitespace-mode t) ;; Whitespace ON.
            (setq whitespace-global-modes '(not org-mode))
            (setq whitespace-line-column 80) ;; Set indent limit.
            (setq whitespace-display-mappings
            '(
                (space-mark 32 [183] [46])
                (newline-mark 10 [172 10])
                (tab-mark 9 [9655 9] [92 9]))))
        ```

        Here, I've remapped the display for the space, newline, and tab to suit my taste. Whitespace is shown on pretty much every mode except org (where it really is never needed). Other than that, lines over 80 columns are highlighted. Simple and lovely.

    <!--list-separator-->

    -  helm

        Helm is a package that I never knew I needed, until I started using it. It's described as an incremental completion and selection narrowing framework. Essentially, it gives me proper control over buffers, files, and commands similar to Smex (with a Neotree feel). Helm, however, is capably of out of order regex matching which is surprisingly uncommon.

        Here, I've remapped the helm key bindings to reflect standard C-x C-f / tab-complete functionality.

        ```lisp
        ;; Helm
        (use-package helm
            :ensure t
            :bind
            (("M-x" . helm-M-x)
            ("C-x C-f" . helm-find-files))
            :config
            (setq helm-split-window-in-side-p        t  ;; opens helm inside window
                  helm-move-to-line-cycle-in-source  t
                  helm-autoresize-min-height         20
                  helm-autoresize-max-height         40
                  helm-scroll-amount                 8)
            (define-key helm-map (kbd "<tab>") 'helm-execute-persistent-action)
            (define-key helm-map (kbd "C-z") 'helm-select-action)
            (setq helm-mode-fuzzy-match t))
        ```

    <!--list-separator-->

    -  org

        Org-mode might be one of the most expansive and powerful features of emacs. It is perfect for daily organization, notes, etc. Recently, I've adopted the org-clock, which can time tasks and generate useful reports. I may not be a freelancer who charges by the hour, but it certainly keeps me on track and focused.

        ```lisp
        ;; Org
        (use-package org
            :ensure t
            :mode (("\\.org$" . org-mode))
            :bind (("C-c C-x C-i" . org-clock-in)
                   ("C-c C-x C-o" . org-clock-out)
                   ("C-c C-x C-j" . org-clock-goto)
                   ("C-c C-x C-r" . org-clock-report))
            :config
            (progn
                (define-key org-mode-map "\M-q" 'toggle-truncate-lines)
                (setq org-directory "~/org")
                (setq org-clock-persist t)
                (setq org-clock-mode-line-total 'current)))
        ```

        While these snippets are not my configuration in it's entirety, the full file is not a hulking mass. It can be found at in my [dotfiles repo](https://github.com/WalkerGriggs/DotFiles/blob/master/.emacs). Feel free to take and modify what you need. If you have anything to contribute, feel free to shoot me a


### <span class="org-todo done DONE">DONE</span> Ergodox Infinity LCD Firmware <span class="tag"><span class="_devlogs">@devlogs</span></span> {#ergodox_infinity_lcd_firmware}

So you've got yourself an Ergodox Infinity. Congratulations! Everyone probably thinks your a little bit crazy spending that much on a keyboard that strange with LCD displays that small and a layout you're struggling to type on. But it's ok -- anyone who shares this strange obsession probably understands.

This post is really to demonstrate how to change the default layer's LCD logo. [Asciipr0n](http://asciipr0n.net/ergodox-infinity-logo/) has a very clean guide to this, but I find that parts of it are (if not the majority of it is) out of date. Since the firmware has been updated, I thought I'd update the guide.

<!--list-separator-->

-  Prerequisites

    I don't want to go too deep into these. Essentially, here is the shopping list of the things you'll need...

    <!--list-separator-->

    -  Firmware

        The firmware, and really the whole reason for this post, well be using is the [kiibohd/controller](https://github.com/kiibohd/controller). Jacob Alexander (aka Haata) is not only Input Clubs head honcho, but he IS Input Club (well... sorta). He not only wrote kiibohd, but also wrote kll (the keyboard layout language). You'll want to clone his firmware...

    <!--list-separator-->

    -  dfu-util

        This toolchain is what we'll be using to flash our firmware onto the board. I downloaded mine from apt-get but it's also available on Homebrew. It's simple enough to download.

    <!--list-separator-->

    -  gcc-arm-none-eabi

        This one may only apply to me, but I feel like it shouldn't go unsaid. I needed to download the gcc-arm-none-eabi package to properly build the arm firmware with the gcc compiler. Granted, I'm running Debian over here, so you OSX users may not need this step.

    <!--list-separator-->

    -  Python Imaging Library

        This is only necessary if you plan to use kiibohd's bitmap2Struct.py conversion file. Custom logos can only be flashed in the form of byte array, so this script it highly recommended... unless you want to write your byte array by hand. Download 'Image' with pip...

<!--list-separator-->

-  Customize Layout

    So now that we have everything we need to continue, customize your layout. I just use [Input Club's Configurator](https://configurator.input.club/). It's quite simple and doesn't require too much explanation. Just select the button you want to change, and choose its new function. Go as deep into the layering as you wish. My one recommendation: keep a FLASH button on each half in layer seven. This way, you wont have to flip over your board and hit the reset button with paperclip.

    Once you have everything mapped out, download the firmware from the configurator and set aside the ZIP file for later.

    If you have aversion to this configurator, so be it. You can use whatever program --or lack thereof if you hate yourself -- you want, as long as the .kll files compile in the end

<!--list-separator-->

-  Create a Logo

    This part is fun and quite straight forward. Create a logo that fits inside 128x32 screen. Anything large won't get flashed. You can create a the logo in any way, as long as you can get it to .bmp file. Originally, I used [Piskel](http://www.piskelapp.com/) to create mine.

    {{< figure src="/img/ergodox-infinity-lcd-firmware/game_of_life.png" width="50%" >}}

    I created the permutation of a glider from Conway's Game of Life. If you don't know exactly what that is, I highly recommend looking into it.

    Essentially, the bitmap can be whatever so long as it's a black foreground on white background. (Though... I've just begun to tinker with and observe the conversion of color bitmaps to the monochromatic lcd display... So you can always give that a try).

    Now in order to flash this new logo onto your board, it needs to be in the form of a byte array. The easiest way to convert your bitmap into the byte array is to use the firmware's [bitmap2Struct.py](https://github.com/kiibohd/controller/blob/master/Scan/Devices/STLcd/bitmap2Struct.py) -- as I mentioned earlier. This script spits out two visual representations of the bitmap and the byte array. Just shove the output into a file for later.

    ```bash
    python bitmap2Struct.py --filename <filename> > ByteArray.txt
    ```

    Here is what my ByteArray.txt file look like:

    ```nil
    uint8_t array[] = {
    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0xf0, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x0f, 0x00, 0x00, 0x00, 0x00,
    }
    ```

<!--list-separator-->

-  Prepare the Firmware

    Now that we have all of our files ready to go, it's time to prep the firmware. A few things have changed in the structure of the firmware, so it does take a few steps to get setup. Oddly enough, we need to build the default ergodox firmware in order to rebuild ours later.

    ```bash
    cd controller/Keyboards
    ./ergodox.bash
    ```

    Now you may notice in the firmware's root directory, a 'kll' directory has been created. That is where we need to add our custom layouts. So make yourself a layout directory and copy in all our .kll files from the ZIP the configurator created.

    ```bash
    mkdir controller/kll/layouts/<my_layout>
    cp <configurator ZIP>/*.kll controller/kll/layouts/<my_layout>
    ```

    Since we have our logo's byte array all squared away, all we have to do is include it. Head into the Scan directory and copy the infinity_ergodox module.

    ```bash
    cd controller/Scan
    cp -r Infinity_Ergodox Infinity_Ergodox_Custom
    ```

    Now the one and only thing we need to alter in here is the STLcdDefaultImage in scancode_map.kll. Replace the default Input Club's byte array with our custom byte array from earlier.

    Bingo. Now our layouts are almost ready to be flashed. We now need to quickly modify our own build script.

    ```bash
    cd controller/Keyboards && cp ergodox.bash ergodox-custom.bash
    ```

    Edit this new bash file and update the DefaultMap and PartialMaps to include each layer's .kll map created in the configurator. You can also alter the BuildPath, but I'm not building more than one set of firmware at a time, so I leave them as the default ICED-L and ICED-R. Do note: each map (default or partial) requires the lcdFuncMap. Here is mine for example:

    ```bash
    # This is the default layer of the keyboard
    # NOTE: To combine kll files into a single layout, separate them by spaces
    # e.g.  DefaultMap="mylayout mylayoutmod"
    DefaultMap="<my_layout>/MDErgo1-Default-0 lcdFuncMap"

    # This is where you set the additional layers
    # NOTE: Indexing starts at 1
    # NOTE: Each new layer is another array entry
    PartialMaps[1]="<my_layout>/MDErgo1-Default-1 lcdFuncMap"
    PartialMaps[2]="<my_layout>/MDErgo1-Default-2 lcdFuncMap"
    PartialMaps[3]="lcdFuncMap"
    PartialMaps[4]="lcdFuncMap"
    PartialMaps[5]="lcdFuncMap"
    PartialMaps[6]="lcdFuncMap"
    PartialMaps[7]="<my_layout>/MDErgo1-Default-7 lcdFuncMap"
    ```

    Finally, change the ScanModule from Infinity_Ergodox to Infinity_Ergodox_Custom or whatever you called your Scan Module. Now we should be all ready to flash.

<!--list-separator-->

-  Build and Flash

    Now that we have everything set and ready to go, we can actually get this firmware onto your board and have you on your way. First step, rebuild the default firmware from earlier, but run your custom build script this time.

    ```bash
    cd controller/Keyboards
    ./ergodox-custom.bash
    ```

    This should build your new firmware and create two directories: ICED-L.gcc and ICED-R.gcc. Those contain the binary files to flash.

    ```bash
    # Connect only your left board and enter flash mode
    sudo dfu-util --download ICED-L.gcc/kiibohd.dfu.bin

    # Connect only your right board and enter flash mode
    sudo dfu-util --download ICED-R.gcc/kiibohd.dfu.bin
    ```

    At this point, your Ergodox Infinity should be both flash with your layout and your custom logo. Happy hacking!


### <span class="org-todo done DONE">DONE</span> Pipewire in Docker <span class="tag"><span class="_devlogs">@devlogs</span></span> {#pipewire_in_docker}

{{< figure src="/img/pipewire-in-docker/pipewire.gif" width="100%" >}}

[Pipewire](https://pipewire.org/) is a graph-based multimedia processing engine that lets you handle audio + video in real time! I've had way too much fun playing with it recently, but spent longer than I care to admit spinning it up in an Ubuntu container.

Most of the examples I saw floating around were using [systemd](https://www.freedesktop.org/wiki/Software/systemd/) or [Fedora](https://getfedora.org/en/server/), but my requirements were

1.  Ubuntu 22.04
2.  Processes run as background sub-shells without systemd
3.  Built from the latest source
4.  Drop-in replacement for PulseAudio

Side note: I spent some time tinkering with 18.04 LTS, which requires either a [PPA](https://pipewire-debian.github.io/pipewire-debian/) or building [Meson](https://mesonbuild.com/Reproducible-builds.html) and [Alsa utils](https://github.com/alsa-project/alsa-utils) from scratch (Pipewire requires versions not available older Debian systems). I highly recommend the PPA if you head that route...


#### Front matter and dependencies {#front-matter-and-dependencies}

As with most containers, we first define the front matter and install all Pipewire build / runtime dependencies. There are probably a few unnecessary packages floating around here, but the goal of this spike wasn't to optimize the container's size.

```Dockerfile
FROM ubuntu:22.04 AS pw_build

LABEL description="Ubuntu-based stage for building pipewire" \
      maintainer="Walker Griggs <walker@walkergriggs.com>"

RUN apt-get update \
    && apt-get install -y \
    debhelper-compat \
    findutils        \
    git              \
    libasound2-dev   \
    libdbus-1-dev    \
    libglib2.0-dev   \
    libsbc-dev       \
    libsdl2-dev      \
    libudev-dev      \
    libva-dev        \
    libv4l-dev       \
    libx11-dev       \
    ninja-build      \
    pkg-config       \
    python3-docutils \
    python3-pip      \
    meson            \
    pulseaudio       \
    dbus-x11         \
    rtkit            \
    xvfb
```


#### Relevant environment variables {#relevant-environment-variables}

The next step is setting the relevant environment variables for building Pipewire. I like to do this after installing dependencies so I don't have to re-install everything if one variable changes.

In this example, we're pulling Pipewire's latest version (as of time of writing) and defining our build directory. We're building Pipewire in `/root` as `root` -- worst practice, but it's a spike.

```Dockerfile
ARG PW_VERSION=0.3.60
ENV PW_ARCHIVE_URL="https://gitlab.freedesktop.org/pipewire/pipewire/-/archive"
ENV PW_TAR_FILE="pipewire-${PW_VERSION}.tar"
ENV PW_TAR_URL="${PW_ARCHIVE_URL}/${PW_VERSION}/${PW_TAR_FILE}"

ENV BUILD_DIR_BASE="/root"
ENV BUILD_DIR="${BUILD_DIR_BASE}/build-$PW_VERSION"
```


#### Build the thing {#build-the-thing}

Now that we've installed our dependencies, we're ready to build Pipewire itself. Meson is Pipewire's build system of choice. I don't have much experience with Meson, but it was easy enough to work with.

```Dockerfile
RUN curl -LJO $PW_TAR_URL \
    && tar -C $BUILD_DIR_BASE -xvf $PW_TAR_FILE

RUN cd $BUILD_DIR_BASE/pipewire-${PW_VERSION} \
    && meson setup $BUILD_DIR \
    && meson configure $BUILD_DIR -Dprefix=/usr \
    && meson compile -C $BUILD_DIR \
    && meson install -C $BUILD_DIR
```


#### Setup the entrypoint scripts {#setup-the-entrypoint-scripts}

Next up are the dominoes of entrypoint scripts.

```Dockerfile
COPY startup/      /root/startup/
COPY entrypoint.sh /root/entrypoint.sh

WORKDIR /root
CMD ["/bin/bash", "entrypoint.sh"]
```

I like to breakdown the entrypoint scripts and order them with a filename prefix. I forget exactly where I picked up this habit, but it stuck a long time ago.

In this example, I'm running `xvfb` as a lightweight X11 server. From everything I've read, Pipewire is really designed to run on a full `Wayland` system, but I haven't made the jump on any of my machines and likely wont for some time.

```bash
# startup/00_try-sh.sh
for f in startup/*; do
    source "$f" || exit 1
    sleep 2s
done

# startup 01_envs.sh
export DISABLE_RTKIT=y
export XDG_RUNTIME_DIR=/tmp
export PIPEWIRE_RUNTIME_DIR=/tmp
export PULSE_RUNTIME_DIR=/tmp
export DISPLAY=:0.0

# startup/10_dbus.sh
mkdir -p /run/dbus
dbus-daemon --system --fork

# startup/20_xvfb.sh
Xvfb -screen $DISPLAY 1920x1080x24 &

# startup/30_pipewire.sh
mkdir -p /dev/snd
pipewire &
pipewire-media-session &
pipewire-pulse &
```

Pipewire has a few runtime requirements; [dbus](https://www.freedesktop.org/wiki/Software/dbus/) and [rtkit](https://github.com/heftig/rtkit) are top of mind. So long as the Pipewire media session can fork the system dbus session though (or launch a new one), you should be fine. I've personally disabled rtkit.

Another point of note: I've opted for [media-session](https://gitlab.freedesktop.org/pipewire/media-session) which is, unsurprisingly, a reference implementation of Pipewire's media session. In future revisions, I plan to replace it with the more advanced [Wireplumber](https://gitlab.freedesktop.org/pipewire/wireplumber). Media Session was quick and easy for the time being though.


#### Run the thing! {#run-the-thing}

There's not much to it. If we hop into the container and check on the Pulse server's, we can see that our Pipewire server is running and properly emulating Pulse. Great success!

```text
root@8e86f658e342:/# pactl info
Server String: /tmp/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 42
Tile Size: 65472
User Name: root
Host Name: 8e86f658e342
Server Name: PulseAudio (on PipeWire 0.3.59)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
```

I'll likely write more about Pipewire once I get more experiencing working with it as a desktop service and as an API client. [Wim](https://hachyderm.io/@wtay@fosstodon.org) and [team](https://hachyderm.io/@pipewire@fosstodon.org) have written some great [client examples](https://docs.pipewire.org/examples.html) which I've modified for a few different use cases -- the [Simple Plugin API (SPA)](https://docs.pipewire.org/page_spa.html) is surprisingly... simple. More to follow!


### <span class="org-todo done DONE">DONE</span> Zettelkasten, Rhizomes, and You <span class="tag"><span class="_essays">@essays</span></span> {#zettelkasten_rhizomes_and_you}

{{< figure src="/img/zettelkasten_rhizomes_and_you/zettel_1.jpg" caption="<span class=\"figure-number\">Figure 1: </span>Chris Korner, Deutsches Literaturarchiv Marbach" width="435px" >}}

A few years ago, I stumbled upon a collection of odd websites that called themselves "brain dumps." On the surface, they seemed like collections of disjointed thoughts – fragments of ideas that linked to seemingly unrelated topics. Often, they bridged disciplines altogether.

That's when I learned about Zettelkasten.


#### Zettelkasten {#zettelkasten}

Zettelkasten (sometimes referred to as Zettel or Zet) is a system for taking notes that is specifically structured to develop ideas, not just collect them. The method has existed [for hundreds of years](https://archive.org/details/bub_gb_IgMVAAAAQAAJ/page/n156/mode/1up) under various names, but at its core, it consists of "bite-sized" notes written on slips of paper that are linked by a heading or a unique ID. These slips, often index cards, are filed away in a place that can be easily referenced and traversed.

The theory behind it is sound. Verweisungsmöglichkeiten, translated as a "referral opportunity" or "possibility of linking," refers to any moment when you might reference another note or tangential thought. For example, ‘structuralism’ might refer to ‘post-structuralism’ which itself links to ‘Michel Foucault’ and a plethora of post-structuralists.
Small, pointed notes can connect to any number of these thoughts across various topics, and reviewing your notes often results in finding commonalities among seemingly disparate ideas. With enough notes in your slip box, you can even hold a conversation with it.

In fact, Niklas Luhmann, a German sociologist credited with creating the modern Zettelkasten method, referred to his slip box as a "partner of communication." His notes comprised just over 90,000 index cards and helped him write nearly 50 books and 600 essays. Luhmann said:

> It is impossible to think without writing; at least it is impossible in any sophisticated or networked fashion. Somehow we must mark differences and capture distinctions which are either implicitly or explicitly contained in concepts. Only if we have secured in this way the constancy of the schema that produces information can the consistency of the subsequent processes of processing information be guaranteed. And if one has to write anyway, it is useful to take advantage of this activity in order to create in the system of notes a competent partner of communication.

You can browse [Luhmann's archive](https://niklas-luhmann-archiv.de/) online if you're interested.

{{< figure src="/img/zettelkasten_rhizomes_and_you/zettel_2.jpg" caption="<span class=\"figure-number\">Figure 2: </span>The Niklas Luhmann Archive, Historisches Museum Frankfurt" width="435px" >}}


#### The Spatial and Temporal {#the-spatial-and-temporal}

In my experience, Zettelkasten felt counterintuitive at first. We, as humans, live and think spatially. Even how we perceive time is geometric. For example, we've created the concept of a "timeline." When you complete a task, you've put it "behind you." When you start a new phase of life, you're eager to see "what lies ahead." Humans are inherently spatial – we live in a three-dimensional world – so naturally, our notes are too.

For example, as we read text or listen to a lecture, we take notes sequentially – top to bottom. We indent or nest our notes to show that certain thoughts "belong" to a certain topic. Headers encapsulate subheaders, similar to how rooms encapsulate closets (which themselves have drawers and boxes, etc.).

Zettelkasten, however, avoids concepts of past, present, and belonging. Notes aren't concerned with what came before or after them, only how individual thoughts relate to one another. They juxtapose and correlate ideas, rather than spatially positioning them. The value of a note isn't in its individual content, but in the narrative they collectively tell as you discover new paths between and bridges across topics.

Luhmann, too, valued this idea of "internal branching". New ideas shouldn't be appended to a list of prior notes, but instead inserted among connected thoughts. This internal network of links creates a greater combination of thoughts than if we simply connected thoughts to what came before and after.


#### Deleuze, Plato, and Rocking Chairs {#deleuze-plato-and-rocking-chairs}

Last year, a colleague introduced me to a group of post-structuralists, including Derrida, Deleuze, and Baudrillard. Deleuze particularly caught my attention with his interest in topology. Relevant to this essay is his disdain for representational thinking and strict hierarchy.

To properly understand Deleuze, we should probably first understand Plato. Plato believed that everything has an ideal form, and the closer something is to that ideal form, the closer it is to perfection. For example, there is an ideal chair, and so a chair with a slight wobble is closer to perfection than a chair with a broken leg.

Deleuze describes this model as "arborescent"; it is structured like a tree, where the ideal form is the root and the lesser representations extend out over the branches to the canopy.

In our "chair" example, somewhere on that tree are stools, stumps, and hammocks. They are ranked according to their proximity to the ideal chair. Plato might ask, "How perfect of a chair are you?" but Deleuze took issue with this line of reasoning. He proposed that a better question is "How are you different?" or "What characteristics make you unique?" We can then categorize the stump, stool, and hammock not by their representation of an "ideal chair," but by the differences between them. Stools are portable, hammocks are soothing, and stumps firmly ground you in nature.

{{< figure src="/img/zettelkasten_rhizomes_and_you/rhizome.jpg" caption="<span class=\"figure-number\">Figure 3: </span>Terry Winters, Rhizome, 1998, Smithsonian American Art Museum" width="435px" >}}

In contrast, Deleuze calls this "rhizomatic" thinking. Rhizomes are systems of roots that spread horizontally underground and branch in every direction. Ginger and asparagus are rhizomes.
They have no top or bottom, no start, and no end. They are circuitous and cyclical. If you kill one section, the remaining roots will live on. If you cut it in half, they will live separate lives.

Relative to arborescent thought, in a rhizome nothing represents something else and certainly not an ideal form. In rhizomes, all that exist are the connections between nodes. Stools are chairs without a back. Chairs are hammocks without a rotating axis. Hammocks and rocking chairs incorporate motion.

Zettelkasten are also rhizomes. My notes for this essay point me towards Spinoza, then to Pantheism, then to Sikhism, then to Buddhism, then to the concept of time, which itself inspired my earlier point that humans perceive time spatially. They branch, reconnect, wind, and are never hierarchical. They are, if we want to think spatially, horizontal.


#### Repetition and Paratext {#repetition-and-paratext}

There is another connection between Deleuze and Zettelkasten worth exploring, and that is repetition. Deleuze believed that when you repeat something, you are creating a copy of that thing. When you think about a rocking chair, you are creating another representation of that chair – one that differs in many ways from all the rocking chairs you have seen before. Therefore, by rereading or repeating your notes, you are creating a unique multiplicity.

The problem with this is that your notes do not exist in a vacuum. They are, if transcribed linearly, surrounded by prior context. They are spatially dependent on adjacent ideas – how the topic is presented, the previous lecture, the syllabus as a whole, and even the notes on the chalkboard. This framing is paratextual; it informs how you approach the primary text, similar to how the cover of a book or the font on its spine might.

When you repeat or review linear, contextual notes, you are creating a snapshot of a previous argument – paratext and all. You are retracing the same ground and connecting the same dots. This repetition cannot lead to the creation of new ideas.

Deleuze dislikes representational thinking, in part, because we cannot create anything new if everything represents a common root or a perfect form.
yourself the opportunity to reframe those thoughts. You are not just rehashing the same ideas in the same light; you are creating an entirely new amalgamation from existing scraps. You will find more opportunities for external connection – verweisungsmöglichkeiten – and therefore more opportunities to evolve and transform your existing ideas.

Luhmann found it extremely important for communication partners (you and your notes, in this case) to "mutually surprise each other." Partners can only successfully communicate, or produce new information, when they "communicate in the face of different comparative goals."


#### In closing {#in-closing}

So why am I writing this? It was, for all intents and purposes, a proof of concept; a successful conversation with my “communication partner”.

In fact, the majority of time spent writing this piece was spent on flow, grammar, and narrative. I took the bulk of the content from a series of notes written on disparate topics at various times over the last year.

The graph now has enough nodes -- the rhizome enough roots -- that I’m surprised by new connections. I can follow trains of thought longer than a few nodes. I can venture forward, backpedal, and reconsider thoughts I had from months prior. No note has a perfect form. No note is dependent on time or space. No note is dependent on another.

In all honesty, I'm not sure where this train of thought should end, or if it should end at all.

Maybe in the future, I'll write something more concrete on how exactly I take notes. For the time being, I'm still working out the finer details. I'll update this conclusion with "new nodes" as they are written.


#### References {#references}

Deleuze, Gilles. _Difference and Repetition_. New York: Columbia University Press, 1994.

Deleuze, Gilles, and Félix Guattari. _A Thousand Plateaus: Capitalism and Schizophrenia_. Minneapolis: University of Minnesota Press, 1987.

Genette, Gérard. _Paratexts: Thresholds of Interpretation_. Literature, Culture, Theory 20. Cambridge ; New York, NY, USA: Cambridge University Press, 1997.

Luhmann, Niklas. _Communicating with Slip Boxes_. Accessed January 5, 2023. <https://luhmann.surge.sh/communicating-with-slip-boxes>.

_The Rhizome - A Thousand Plateaus, Deleuze and Guattari_. Then &amp; Now, 2018. <https://www.youtube.com/watch?v=RQ2rJWwXilw&ab_channel=Then%26Now>.


### <span class="org-todo done DONE">DONE</span> Timestamp Troubles <span class="tag"><span class="_talks">@talks</span></span> {#timestamp_troubles}



#### Recording {#recording}

<iframe src="https://www.youtube-nocookie.com/embed/m0yNWtCeWh8" allowfullscreen title="YouTube"></iframe>


#### Abstract {#abstract}

Video is hard, and reliable timestamps in increasingly virtual environments are even harder.

We at Mux recently broke ground on a new live video experience, one that takes a website URL as input and outputs a livestream. We call it Web Inputs. As with any abstraction, Web Inputs hides quite a bit of complexity, so it wasn’t long before we ran up against our first “unexpected behavior”: our audio and video streams were out of sync.

This talk walks you through our experience triaging our timestamps troubles. It’s a narrative account that puts equal weight on the debugging process as the final implementation, and aims to leave the audience with a new perspective on the triage process.

I hope you’ll learn from our mistakes, a bit about Libav audio device decoders, and hopefully a new pattern for web-to-video streaming.


#### Transcript {#transcript}

{{< figure src="/img/timestamp_troubles/slide_1.png" width="435px" >}}

Hey everyone, my name is Walker Griggs, and I’m an engineer at Mux.

I’m actually going to do something a little out of order here and introduce the “punchline” for my talk before I even introduce the topic.

{{< figure src="/img/timestamp_troubles/slide_2.png" width="435px" >}}

The punchline is: “reliable timestamps when livestreaming from virtual environments are really, really hard.”

I’m giving the punchline away because this talk isn’t about the conclusion, it’s about the story I’m going to tell you. It’s a story about our mistakes, a little bit about Libav audio device decoders, and a lot a-bit about some good, old-fashion detective work.

One last piece of framing: up until I joined Mux 9 months ago, I worked with databases. That was a simpler time. WHIP still meant whipped cream and DASH was still 100 meters.

I've realized, though, that databases and video have a lot more in common than you might think. They’re both sufficiently complex pillars of the modern internet, they both require a degree of subject matter expertise, and, at first glance, neither are exceptionally transparent.

That’s why this talk will be geared to those of us who are looking to level up our deductive reasoning skills and maybe add new triage tools to our tool box. In the end of the day, all that matters is "getting there".

{{< figure src="/img/timestamp_troubles/slide_3.png" width="435px" >}}

So where is this talk going?

We’ll start by introducing the problem space, of course. Every good story needs an antagonist. We’ll take a quick detour to talk about timestamps, and use that info to color how we triaged the problem. Finally, we’ll arrive back at our problem statement and how we fixed it.

{{< figure src="/img/timestamp_troubles/slide_4.png" width="435px" >}}

So let’s jump into it. On and off for the last 9 months, I’ve been working on a system called Web Inputs. Web Inputs takes a website URL as input, and outputs a livestream. URL in, video out. On the surface that seems pretty simple, but, as most abstractions do, that simplicity hides a great deal of complexity.

{{< figure src="/img/timestamp_troubles/slide_5.png" width="435px" >}}

Web Inputs has to wear quite a few hats.

1.  First and foremost, it runs a headless browser to handle all of the target website’s client-side interaction. For example, broadcasting WebRTC is a common use case, so the headless browser -- Chromium, in our case -- needs to decode all participant streams.
2.  Chromium then pushes audio and video onto separate buffers -- X11 and Pulseaudio, specifically. We opted to use a virtual X11 frame buffer instead of a canvas to avoid the GPU requirement.
3.  Finally, FFmpeg can transcode the buffer content and broadcast over Mux’s standard Livestream API.

{{< figure src="/img/timestamp_troubles/slide_6.png" width="435px" >}}

An adjustment we made early on, and one that's the catalyst for this **entire** talk, is to hide the page load from the livestream. If we start Chrome and immediately buffer audio and video, we're going to catch the webpage loading in the resulting livestreaming. That's not a great customer experience.

{{< figure src="/img/timestamp_troubles/slide_7.png" width="435px" >}}

Instead, we can listen to Chrome’s events. One of which is called “First Meaningful Paint”, and that’s effectively Chrome saying “something interesting is on the screen now, you should probably pay attention. A colleague of mine, [Garrett Graves](https://github.com/GRVYDEV) actually came up with this idea. From a timing perspective, it worked really well, but this change is also when we started seeing some odd behaviors.

{{< figure src="/img/timestamp_troubles/slide_8.png" width="435px" >}}

Behavior number 1: the first 4-7 seconds of audio and video looked like they were shot from a cannon. The audio was scattered all over the place, and frames were jumping left and right.

Behavior number 2: the audio + video would meander in and out of sync over the course of the broadcast.

{{< figure src="/img/timestamp_troubles/slide_9.png" width="435px" >}}

That’s no good. So what did we do? We did, what I’m sure many of you all are guilty of, and stayed up late into the morning fiddling with ffmpeg flags. We read all the blog posts on AV sync. We tried various combinations of filters and flags.

The problem with this approach, as many of you are probably itching to call out, is it lacks evidence. We spent a day on what effectively amounted to trial and error. In fact, a colleague of mine put together a spreadsheet of the flags we had tried, links to the resulting videos, and various, subjective scores.

The most frustrating part: sometimes we’d get close, and I mean really really close. And then one test run would fail, which would put us back on square one.

Another point to call out here: we were testing in different environments. We were comparing behaviors from production against our development stack and the differences were staggering. We allocate Web Inputs some number of cores in production. For context, our entire development stack runs on that same number. It didn’t take long before we noticed how inconsistent dev really was, and that our qualitative assessments weren’t going to get us there.

Empirical evidence is and will always be the fastest way to understanding your problem.

{{< figure src="/img/timestamp_troubles/slide_10.png" width="435px" >}}

Before we look at any logs or metrics, let’s run through a quick primer on timestamps so we’re all on the same page.

{{< figure src="/img/timestamp_troubles/slide_11.png" width="435px" >}}

You’ll often hear PTS and DTS talked about -- the "presentation timestamp" and "decode timestamp". For starters, every frame has both and they dictate the frames' order. The PTS is when a player should _present_ that specific frame to the viewer. The DTS is when the player should _decode_ the frame.

These timestamps are different because frames aren’t always stored or transmitted in the order you view them. Some frames actually refer back to one another. These are called "predictive" or "delta" frames.

{{< figure src="/img/timestamp_troubles/slide_12.png" width="435px" >}}

With that out of the way, let’s talk about our triage process.

One thing we found early in our investigation: FFmpeg was complaining about timestamps assigned by the Pulseaudio device decoder. Naturally, we wanted to go right to the source, so we added some new log lines to the decoder and dumped various metrics to disk.

{{< figure src="/img/timestamp_troubles/slide_13.png" width="435px" >}}

The first thing to call out: "non-monotonic DTS in output stream". These can be the bane of your existence if you’re not careful. It means that your decoded time stamps are not increasing by the same amount frame to frame.

Another bit to call out are the sample sizes. We’re seeing a huge push of these 64kb packets at the start of the stream, which settles down to a steady 4kb after the first few seconds.

The next bit to question: PTS and DTS on audio samples. Audio ‘frames’ don’t form groups of pictures like video frames do. Audio doesn’t have predictive frames, so why are they used, and why are they different?

Ultimately it comes down to Libav’s data models. Frames and packets are general structs and used for both video and audio, so we can think of “PTS” and “DTS” in this context as ‘appropriately typed fields that can store timestamps’. So that explains why we’re using this terminology, but it doesn’t explain why they’re different.

{{< figure src="/img/timestamp_troubles/slide_14.png" width="435px" >}}

For that we have to look at the Pulse decoder which does 3 things when it assigns timestamps to frames.

The first is to fetch the time according to the wall clock; that’s the DTS. It then adjusts the DTS by the sample latency. That latency is just the time difference between when the sample was buffered by Pulse and requested by ffmpeg.

It then runs it through a filter to de-noise the DTS and smooth out the timestamps frame-frame. The wall clock isn’t always perfect, as we’ll see more of in a second, and it can be exceptionally sporadic in these virtual environments.

Keep in mind, this system is running a docker container, running on a VM, which is probably itself part of a hypervisor. We’re likely not using a hardware timing crystal here, so we de-noise that PTS to offset and inconsistencies.

{{< figure src="/img/timestamp_troubles/slide_15.png" width="435px" >}}

We’re heading in the right direction, but at this point I’d say we have “data” — not “evidence”. Long log files aren’t exactly human readable, and certainly harder to reason about. I may not be a Python developer, but the one thing I’ll swear by is its ability to visualize and reason about data sets.

The first thing we wanted to visualize were these timestamps, of course. We expected to see a linear increase in timestamps, maybe an artifact of those non-monotonic logs in the first few seconds.

{{< figure src="/img/timestamp_troubles/slide_16.png" width="435px" >}}

Good news: we do! But, maybe not as clearly as we should.

Unfortunately, this graph doesn’t tell us that much. We can’t draw any conclusions from this data. What would be more helpful would be to graph the **rate** at which these timestamps fluctuate because what we really care about is “how reliable or consistent these timestamps are”. The derivative, or the rate of change, of this data might show us how unstable these timestamps actually are.

{{< figure src="/img/timestamp_troubles/slide_17.png" width="435px" >}}

Lo and behold; the derivative is pretty telling. So what are we looking at? Well a derivative of a linearly increasing function is flat, so that tells us that after some number of seconds, our timestamps are dead close to linearly increasing. That’s what we want!

But the first few seconds — they tell another story. Every time the slope increases, timestamps are increasing in a super-linear way. When the slope decreases, our timestamps are slowing down or even “jumping back in time” in a sub-linear way. So that’s interesting, but maybe more interesting is that this is only occurring for the first few seconds.

Also worth calling out is that our denoising filter is doing it’s job, but it can’t spin gold from straw. The peaks are lower and the troughs are higher, but the filter is only as good as the data it’s fed.

There was another piece to the logs: that back pressure of buffered samples at the beginning of the stream.

{{< figure src="/img/timestamp_troubles/slide_18.png" width="435px" >}}

If we graph the latency as well, we see some rough correlation. Again, high pangs of latency early in the stream which settles down to something more consistent.

{{< figure src="/img/timestamp_troubles/slide_19.png" width="435px" >}}

If we think back to those initial behaviors, I think this visualizes them pretty well. We see an initial scramble of timestamps which likely is causing the player to throw frames at us in a seemingly random or unpredictable order. We can also see that the timestamps aren’t perfectly linear, which would explain why AV sync meanders a little bit over the course of a stream.

Something to call out here though: this is just a correlational and not directly causational relationship. These are only part of the picture. It might be hasty to drop the gavel and blame Pulse. There’s a number of paths unexplored here. For example, these are only the audio samples. There’s a whole other side to the video samples to explore.

{{< figure src="/img/timestamp_troubles/slide_20.png" width="435px" >}}

We needed to step back and consider our goals at this point, though. It’s important to remember that these visualizations are just interpretations -- not hard evidence. We, like many of you, are under deadlines.

We had to make the difficult decision here. Keep digging, or action what we already know. We went with the latter, and wanted to strip the problem back to first principles.

Before we talk about how we fixed it, it's important to talk about what we already knew.

{{< figure src="/img/timestamp_troubles/slide_21.png" width="435px" >}}

-   We already knew that latency was at play, and that Pulse was buffering more than we needed.
-   We knew that our timestamps were based off of wall clocks that we couldn't always trust in this environment (even after denoising).
-   We knew some simple metrics like the starting timestamp, exactly how many samples we’ve decoded, and the target frequency.

{{< figure src="/img/timestamp_troubles/slide_22.png" width="435px" >}}

The first and very naive solution we used to validate our hypothesis was to ignore all samples until we were pulling off nice, round, 4kb packets. This solution gave us fine results in a controlled environment, but we'd never want this hack in production for obvious reasons.

The logical next step here is to flush Pulse's buffers. If you remember where this entire saga began, we were trying to cleanly start headless chrome **without** broadcasting the loading screen. Any data buffered before the start of the transcode can be tossed. We found limited success interacting with the audio server directly.

The last option was the one we ultimately went with, which is counting the number of samples and computing the DTS on the fly.

{{< figure src="/img/timestamp_troubles/slide_23.png" width="435px" >}}

So what does that look like for us? First, we record the wall time when we initialize the device decoder — that’s our ‘starting time’. We then ignore all buffered samples with a DTS before that starting time.

From there, we count each sample we do care about and use that to determine sample perfect timestamps using our target frequency and timebase.

For example, if our target frequency is 48khz, or 48000hz, and we’ve already decoded 96000 samples, that means we’re exactly 2 seconds into the livestream.

{{< figure src="/img/timestamp_troubles/slide_24.png" width="435px" >}}

If we translate this solution into terms Libav will understand, it's actually fairly simple.

{{< figure src="/img/timestamp_troubles/slide_25.png" width="435px" >}}

The results were so much closer. Not perfect, but closer. In fact, over the next few days, we ran a 8 hour test stream and noticed that, over the course of the day, millisecond by millisecond, the video pulled ahead of the audio.

{{< figure src="/img/timestamp_troubles/slide_26.png" width="435px" >}}

So, what gives?

See: what we learned first hand was, when it comes to livestreaming timestamps, you can’t trust any one single method. Counting samples is great in theory, but not responsive by itself. There are a number of reasons why we might drop samples, and this solution doesn’t have any way to recover if we do. Sharks bite undersea cables.

So instead, we can re-sync where appropriate and actually use the wall clock as a system of checks and balances. If the two methods of determining timestamps disagree by more than some threshold, re-sync. You could, for example, reset that initial timestamp and restart the frame counter.

This solution gives you the accuracy of a wall clock but the precision of sample counting.

{{< figure src="/img/timestamp_troubles/slide_27.png" width="435px" >}}

So what are some takeaways here?

1.  For us, this experience was our first time getting our hands dirty with device decoders. We found that, in this instance, going through FFmpeg's documentation flag by flag wasn't going to cut it. There's a big gap in online resources between high level glossary and low level specification. Getting hands on was the only way to fill that gap.
2.  Choose redundancy where it matters. This lesson is something we've learned in infrastructure and database; video is no different. It's not always best to trust a single system when calculating timestamps.
3.  The last take away, and one that we actually started recently, is to invest in glass-to-glass testing. We wasted far too many hours watching test cards and Big Buck Bunny -- my palms still get sweaty when I hear that pan flute.

    One thing we tried was injecting QR codes directly into test cards with audible sync pulses at regular intervals. We can then check the resulting waveform to see if those pulses landed on frames flagged with QR codes. We can then use the frame count and sample rate to calculate how we've deviated.

{{< figure src="/img/timestamp_troubles/slide_28.png" width="435px" >}}

That said, I think the big takeaway here is the one I told you was coming from the very beginning: “reliable timestamps in virtual environments are really, really hard.”


### <span class="org-todo done DONE">DONE</span> The Guy Who Likes Lemons <span class="tag"><span class="_essays">@essays</span></span> {#the_guy_who_likes_lemons}

\#+begin_description
I’ve recently been thinking about my personal brand – whatever that means. Do I want to expose all of myself? None? Probably some facets, but which? I doubt I’ll ever find the right balance, if there is such a thing.
de#+end_description


#### “I want to be remembered as the guy who likes lemons.” {#i-want-to-be-remembered-as-the-guy-who-likes-lemons-dot}

About 10 years ago, I asked a college admissions advisor what she considered the most memorable essay she’d ever read. She responded without pause: “I want to be remembered as the guy who likes lemons.”

She explained. There are always wonderful essays about ambition and adversity, but this one, semi-sensible essay took the cake. The first sentence was “I want to be remembered as the guy who likes lemons.”

She didn’t remember the specifics of the essay. It was probably some analogy about how the author strove to be bright and funky, or sweet and sour. The contents of the essay didn’t even matter; it was all about that unforgettable opening sentence that I’m still talking about 10 years later.

In a world where hiring managers review your resume  [in 6 seconds](https://www.theladders.com/static/images/basicSite/pdfs/TheLadders-EyeTracking-StudyC2.pdf), users context switch [after 400ms](https://lawsofux.com/doherty-threshold/), and the optimal sales email can fit [in a single tweet](https://blog.boomerangapp.com/2016/02/7-tips-for-getting-more-responses-to-your-emails-with-data/), the guy who likes lemons got that advisor’s attention in just 11 words.


#### Wear Orange Shoes {#wear-orange-shoes}

Four years later, I read Dave Kerpen’s book [“The Art of People”](http://www.artofpeoplebook.com/). Out of 53 chapters, one detail has stuck with me: Kerpen always wears orange shoes.

Some people will think that’s silly; most won’t notice. There’s a sliver of people, though, that will never forget those bright orange shoes. If that translates to just one new connection, hire, or investment, the shoes have paid out in dividends.

> I stood in a room filled with entrepreneurs and investors, hoping to get the attention of just one. I was contemplating whether to get a drink from the bar, when all of a sudden I heard, “I have got to talk to the man wearing those f–king shoes!”…
>
> Were my orange shoes the reason I secured an investment? Of course not. But they were the reason I got into a conversation in the first place. In a room full of people trying to get busy people’s attention, that was all it took to stand out in the crowd.

The key, Kerpen asserts, is to garner attention and be authentic. When I gave my first conference talk, the overwhelming majority of messages in the Slack thread weren’t questions; they were comments about my mustache. Some jokes were Mario riffs, and others were a bit more creative.

Jokes aside, my mustache gave me an identity at that conference, intentional or not. As one commenter said: “your mustache brought all the boys to the yard”. Afterwards, a friend told me that I couldn’t shave it; “it’s part of your brand”.

The funny thing is I never intended to grow a mustache. I was debugging a misbehaving system under a time crunch, and didn’t shave for a bit. After the dust settled, I promised coworkers that I’d keep the mustache until our product launched. Now I have a permanent tea strainer.


#### Look good, feel good, sh\*t in the woods! {#look-good-feel-good-sh-t-in-the-woods}

{{< figure src="/img/the_guy_who_likes_lemons/look_good_feel_good.jpg" width="435px" >}}

I went to college in Maine. Freshman orientation was a one-week trek deep into the forest. So deep, in fact, that our van had skid plates for dirt roads and bull bars in case we “bumped” into a moose.

Before we left campus with our groups, one of the student guides stood on a picnic table and started chanting “Look good, feel good, sh\*t in the woods!”, emphasizing every word. Then everyone joined in!

It was goofy and ridiculous, but it loosened everyone up and made us comfortable around each other. We’d be living in close quarters for the week, and quite out of our element, but something about being crass and childish was oddly freeing. It shattered social pretense and set a clear tone; we were there to be honest and ourselves.

We played orientation-type games, repaired a few hiking trails, and then went our separate ways. Over the next four years, though, you could walk into any communal space, chant “look good, feel good!”, and at least one person would holler back “sh\*t in the woods!” while grinning ear to ear.

I recently met a fellow alumna at a holiday party. I told this story and repeated those magic words. [“COOT!”](https://life.colby.edu/what-to-do/first-year-experience/coot/), she said (the name of our orientation week). Those 9 words were all it took to open the flood gate of shared experiences, and we happily compared notes and swapped stories.


#### The Game of Life {#the-game-of-life}

I’ve recently been thinking about my personal brand – whatever that means. Do I want to expose all of myself? None? Probably some facets, but which? I doubt I’ll ever find the right balance, if there is such a thing.

At the end of the day, like all of you, I have varied interests. What I might want to shout from the rooftops one day, I may be uncomfortable sharing the next; and what others might find meaningful, might feel inconsequential to me.

One interview that lives rent-free in my head is [Numerphile’s discussion with John Conway on his Game of Life](https://youtu.be/E8kUJL04ELA). To Conway, the Game of Life felt like an insignificant curiosity. To the rest of the world, the game was immensely impactful.

Conway spent much of his illustrious career studying cellular automaton, but his most notorious work can be written in [less than 40 characters](https://codegolf.stackexchange.com/a/12733).

[Kolmogorov complexity](https://en.wikipedia.org/wiki/Kolmogorov_complexity) is the theory that something is as complex as the shortest program that can reproduce it. By those standards, the Game of Life is less complex than [the name of some Welch towns](https://en.wikivoyage.org/wiki/Llanfairpwllgwyngyll).

> Well, I used to say, and I’m still inclined to say occasionally, that I hate it, I hate the Game of Life. I don’t really, at least I don’t anymore.
>
> The reason why I felt like that was that, whenever my name was mentioned with respect to some mathematics, it was always the Game of Life. And I don’t think the Game of Life is very very interesting. I don’t think it was worth all that, I’ve done lots of other mathematical things. So I found the Game of Life was overshadowing much more important things and I did not like it.

The Game of Life and Conway’s relationship with it, highlights how little it takes to leave a lasting impression and how it often happens when you least expect it. No matter how we try, we can’t control it.

[Franz Wright](https://exceptindreams.livejournal.com/373521.html) wrote that “one of the few pleasures of writing is the thought of one’s book in the hands of a kind hearted intelligent person somewhere.”

I take solace in knowing that, as long as we approach life bright and funky, bold and authentic, or smiling and borderline puerile, someone will remember.

And so, of course, there’s only one way to close. My name is Walker Griggs, and I want to be remembered as the mustached man who looked good, felt good, loved lemons, and shat in the woods – metaphorically, of course.

{{< figure src="/img/the_guy_who_likes_lemons/walker_griggs_the_guy_who_likes_lemons.jpg" height="300px" >}}


### <span class="org-todo done DONE">DONE</span> Data Preservation, Alf's Room, and Spicy P <span class="tag"><span class="_essays">@essays</span></span> {#data_preservation_alfs_room_and_spicy_p}

{{< figure src="/img/data_preservation_alfs_room_and_spicy_p/alfs_room.gif" caption="<span class=\"figure-number\">Figure 4: </span>Alf, \"Welcome to Alf's Room. I am Alf\"" >}}

A colleague of mine recently bought a capture card to record their Nintendo Switch. I asked if they wanted to stream on Twitch or post to Youtube. “No,” they explained, “I just like saving the recordings for my personal archives...something to remember.”

They explained that they once posted often on a Youtube channel and were proud of the content. Even with some regular viewers, though, they decided to delete the channel and contents along with it. Looking back, they deeply regret that decision -- understandable.

I’ve had a similar experience. I had a Youtube channel sometime around 2011, posting silly game montages. I wasn’t any good at the games but enjoyed creating, curating, and narrating. In some ways, the channel made me feel like I was contributing to the broader gaming community.

You can imagine my disappointment when someone commented: “your videos are fantastic; if only you started 3 years ago.” Looking back, that comment is hilariously short sighted. Youtube and esports were in their infancy back then and still are in many ways. But I was young and took feedback from a random internet stranger to heart – something I still struggle with today. I chose to believe that I was too late to the punch. Like my colleague, I deleted the channel.

In hindsight, I think that was a huge mistake. My content was likely the most sincere that I’ll ever produce. I had no expectations. “Youtuber” was barely a career, and I was stoked to get 50 views. I was posting for myself; something relatively few folks can say today -- myself included.

That conversation with my colleague highlights a crucial distinction between personal and public content. There’s something inherently genuine and intimate about content created just for yourself or your closest circle. There’s no ego -- only enthusiasm. That sincerity makes it all the more intriguing to the outsider and what I believe contributed to Youtube’s early success.


#### Spicy P and the Handycam Vision {#spicy-p-and-the-handycam-vision}

Pascal Siakam, an NBA player currently with the Toronto Raptors, showed up to the NBA All-Star game this year with a tape camcorder – three, actually! What may have started as an homage to [Shaq and his VX1000](https://twitter.com/NBAonTNT/status/1627142034522796033) turned into a spectacle all its own.

{{< figure src="/img/data_preservation_alfs_room_and_spicy_p/spicy_p.jpg" caption="<span class=\"figure-number\">Figure 5: </span>Sam Byford, Pascal Siakam and his NBA All-Star Weekend camcorders: an investigation" width="435px" >}}

People were throwing themselves at the camera. In a sea of cellphones and broadcast equipment, everyone wanted to be taped by Spicy P and his Handycam Vision. It was a sincere gesture on Siakam’s part. His smiles were genuine, and everyone’s reactions were priceless. Afterwards, he posted clips to Instagram. The film was grainy and the colors fluctuated so often that it couldn’t be used for anything but personal records. I love that idea.

Lowering the production quality, in a way, signals to others that you intend to create memories -- artifacts of a time worth remembering. Saikam didn’t stabilize his footage or edit out moments where the ref blocked the camera. He panned faster than the camera could capture, and he wasn’t concerned about lighting or framing or jump cuts. The footage is a lens through which he can relive those moments -- we’re just along for the ride, warts and all.

[Sam Byford has a full post](https://www.multicore.blog/p/pascal-siakam-and-his-nba-all-star) <span class="underline">exclusively</span> dedicated to Siakam and cameras. I'll leave the technical breakdown to him, because he's certainly done his research.


#### Alf’s Room {#alf-s-room}

Siakam's story reminds me so much of Adachi Yoshinori's website [Alf's Room,](https://alf-s-room.com/) which gained popularity in small circles after Nick Robinson posted [The mystery of MICHAELSOFT BINBOWS](https://www.youtube.com/watch?v=yDzAAjzbV5g).

Alf’s Room is Yoshinori’s digital “cabinet of curiosities.” The site is broken down into a handful of categories like trains, computers, and music. One stands out: the “exhibition room,” home to “weird, unusual and mysterious things, photos, etc.” It’s a grab bag of oddities like t-shaped vending machines, potted plants at train stations, and holiday lights. Like Siakam, Yoshinori doesn’t worry about the composition of his photos. They exist solely to document his experiences.

{{< figure src="/img/data_preservation_alfs_room_and_spicy_p/alfs_room_ueki_station.jpg" caption="<span class=\"figure-number\">Figure 6: </span>Adachi Yoshinori, Ueki Station" width="435px" >}}

On their own, these oddities and unusual mysteries wouldn’t garner likes or follows; they would never individually “blow up.” Yet, Alf’s Room did indeed go viral. It falls on the intersection of quaint and eccentric, and I have to believe that it gained brief fame because of its quirky personality. The site itself could be part of someone else’s “weird and unusual” digital curio – that’s what makes it so appealing.

His website isn’t some Squarespace-special. It’s been hand crafted and maintained since 1996 with no target audience in mind except himself. It’s a digital diary that just so happens to be publicly accessible.

As an aside, it’s the poster child of [IndieWeb](https://indieweb.org).


#### Betamax and Blinkenlights {#betamax-and-blinkenlights}

Along with any conversation about digital archives comes concerns about mixing preservation and privacy.

For some time now, I’ve wanted to build a rack dedicated to the conversation and restoration of analog tape media. Aside from my love for all things [blinken'](https://en.wikipedia.org/wiki/Blinkenlights), I’m interested in the preservation of at-risk media.

There’s an incredible amount of data actively decaying or otherwise falling victim to the annals of time. VCRs are breaking down, tapes are rotting, and interest in the older formats has completely disappeared with all but a dedicated few. Tapes are not a durable format, at least not the tape made for home consumption.

{{< figure src="/img/data_preservation_alfs_room_and_spicy_p/blinkenlights.jpg" caption="<span class=\"figure-number\">Figure 7: </span>/u/nicholasserra, Video archival rack build: one year update; More gear, bigger rack" width="435px" >}}

Ironically, that fragility makes this data more valuable. Disney will always have a master record of “Beauty and the Beast,” but your family memories can never be recovered.

Barbecues in the park, your child’s first steps, and highschool graduations are moments that capture the fundamental human experience and serve as a historical record regardless of how mundane the memory.

A close friend asked a simple but difficult question when I mentioned digitizing non-commercial tape: “do you think that’s an invasion of privacy?” Should the lifecycle of those tapes be tied to the lifespan of the camera-person? Is there a statute of limitation on privacy where these artifacts transition from personal effects to public archive? Where does ‘good will’ fit?

I don’t think there’s a clear answer to this moral quandary. But I do know that the same sincerity that makes cherished memories private and intimate also makes them intriguing. In some paradoxical way, that also makes them worth sharing.


#### So what? {#so-what}

So what do blinkenlights, Alf’s Room, and Spicy P have to do with each other? For starters, data is plentiful and only getting more abundant. That presents a new challenge in deciding what data is worth keeping. I’ll argue, the most important data are the bits you never share – the bits that can never be replaced.

Forget those well lit, well staged, well edited ‘candids’; I’m talking about those half-drunk selfies with your mother at Christmas dinner.

I’m talking about Adachi Yoshinori’s snapshots tracking the history of potted trees at his local train station or Pascal Siakam’s grainy footage of his friends at the All-Star game.

I’m talking about my Youtube channel from 2011 and those VHS tapes stuffed deep in your grandparents' closet. I may not be the right person to preserve them, but you are.


### How to Overcomplicate Offline Storage <span class="tag"><span class="_devlogs">@devlogs</span></span> {#how_to_overcomplicate_offline_storage}

Seven years ago, I made the decision to keep offline backups of all my personal data. What started as a 1 terabyte external harddrive loaded with a few sentimental photos, zipped folders of school projects, and maybe the odd 360p DVD rip has turned into a 40TB NAS and 26TB worth of offline drives.

{{< figure src="/img/how_to_overcomplicate_offline_storage/lto.jpg" caption="<span class=\"figure-number\">Figure 8: </span>LTO Tapes: the dream no one can reasonably afford" width="435px" >}}

Recently, I tried explaining my system to a friend but my thoughts kept running off in every possible direction. This post attempts to answer 'how I store and track offline files'; [Data Preservation, Alf’s Room, and Spicy P](https://walkergriggs.com/2023/03/25/data_preservation_alfs_room_and_spicy_p/) answers 'why.'


#### What to backup {#what-to-backup}

Before anyone thinks about how they handle offline storage, they should first think about what they’re storing. Personally, I have three rules.

_**Can this data be replaced?**_

If not, I won't hesitate to keep multiple offline copies. Data in this category includes family photos and artifacts of hard work like blog posts, source code, or research notes. These are items that need to be protected at all times.

_**Do I access the file regularly?**_

If I access the file less often than I perform a round of disk maintenance, it’s probably not worth keeping on a spinning disk. That said, pulling out the drives, setting up an external drive dock, and mounting the drives all take time. I avoid it when I can.

_**Am I running out of online storage space?**_

As I’ve expanded my networked storage, my definition of a “large file” has changed, and my tolerance for always-online storage has grown. Mileage may vary.


#### Picking the right drive {#picking-the-right-drive}

Everyone has a different opinion on which drives are best for offline storage. I think the best drives are the ones you have.

Personally, my archive drives are a graveyard of systems-past. They’re all different capacities, manufactured by different companies, and spin at different speeds. As long as they’re above their [S.M.A.R.T. thresholds](http://ntfs.com/disk-monitor-smart-attributes.htm), they’re fine by me.

Capacity is another story; some drives are just too small to bother with. My general rule of thumb is “4 times the size of your data set, divided by your maximum acceptable number of drives”. Personally I never want to maintain more than 10 offline drives at a time. Routine scrubbing and maintenance can be a slow process; let’s not make it slower than it has to be.

For me, currently, that’s `(12TB * 4) / 10` or about 5TB per drive. At the moment, I have a grab bag of 8, 4, and 3TB drives, so that math works out pretty well.

Why 4x the size of the dataset? Well, hard drives – especially old drives – aren’t meant to be long term, offline data solutions. As a result, I try to keep 2 copies of every file spread across multiple drives. I also like to keep 50% capacity available, which is probably overkill but it spreads the files out nicely and reduces the blast radius should a drive completely fail.

<!--list-separator-->

-  Storing your drives

    This bit might sound pedantic, but storing your drives properly is, in many ways, just as important as their S.M.A.R.T. status. I keep my drives in [Orico cases](https://www.orico.cc/us/product/detail/3665.html), labeled with their model number, serial number, capacity, and canonical name.

    The cases claim to be shock and static resistant, but I still keep the drive in an antistatic bag with a small silica packet inside the case just to be safe. Of course, I store those cases somewhere dry with little temperature fluctuation. Harddrives are pretty hearty, but I’d rather be safe than sorry.


#### Workflow, in theory {#workflow-in-theory}

This is where things get opinionated and tailored to your needs. Personally I wanted a system that could:

-   Be fully administered (backup, recovery, and maintenance) in a Linux shell – bonus points if that shell is live booted off the thumb drive with only standard kernel tools
-   Leave the files fully intact and accessible without any special software or de-serialization or de-fragmentation
-   Locate the file among all the offline drives
-   Validate the content of every block with checksums
-   Replicate the files easily and implicitly

I chose `btrfs` and `git-annex`.

I initially narrowed my filesystem choice down to either BTRFS or ZFS, but I have personal experience with the former and dislike the experience of exporting and offlining ZFS pools. BTRFS is now included in the Linux kernel and has all the features I look for in a modern filesystem. Relevant to this use case: block-level deduplication, disk defragmenting, and data scrubbing.

Git Annex surprised me, honestly. I hadn’t given it much thought in the past, but it covered my requirements fully. At the very least, it aligns with my normal software development workflow. From their website:

> git-annex allows managing large files with git, without storing the file contents in git. It can sync, backup, and archive your data, offline and online. Checksums and encryption keep your data safe and secure. Bring the power and distributed nature of git to bear on your large files with git-annex.

Annex supports quite a few remote repository backends like web, bittorrents, XMPP, and S3 to name a few. Unless I decide to move files into AWS S3 or Glacier in the future, I’ll only ever use the bare filesystem. I’d recommend at least reading through their docs – they’re wonderful!


#### Workflow, in practice {#workflow-in-practice}

My workflow, in practice, is pretty simple.

1.  Load a drive up with files until it’s mostly full
2.  Annex those files into a git repository and sync to the origin remote
3.  Defragment the drive
4.  Scrub the filesystem to ensure that all checksums match
5.  Clone the repository on another drive and copy over any files that have less than 2 copies.

Here are some rough steps to reproduce that workflow.

<!--list-separator-->

-  Create an annex repository

    First thing’s first, we need to create an annex repository. I always keep one local repository on my system, so I can run a quick git annex whereis when I need to locate a file. That local repo won't store any large files though.

    ```bash
    $ mkdir -p ~/anenx && cd ~/annex
    $ git init
    $ git annex init
    $ git annex numcopies 2
    ```

<!--list-separator-->

-  Format and prepare a fresh drive

    Once we’ve set up the origin remote we can format our first drive, clone a copy of the annex, and create an “offline repo.”

    A small but critical detail: name and label your drive the same thing. I mean psychically label the drive, initialize the filesystem, title offline annex, and mount to a directory all with the same name – drive0, in this case. You can use the annex description for a bit more metadata; I use the hdd model number, so I always have it tracked.

    ```bash
    $ mkfs.btrfs -L drive0 /dev/sdb

    $ mkdir -p /mnt/drive0
    $ mount /dev/sdb /mnt/drive0 && cd /mnt/drive0

    $ git clone ~/annex && cd ~/annex
    $ git annex group drive0 archive
    $ git annex wanted drive0 standard
    $ git annex describe drive0 "WD80EMZZ-00TBGA"

    $ git annex info drive0
    uuid: 3ddb6b63-33d8-43fa-8553-e594866530af
    description: WD80EMZZ-00TBGA0 [drive0]
    trust: semitrusted
    remote: drive0
    cost: 100.0
    type: git
    repository location: /mnt/drive0/annex/
    last synced: 2023-03-21 04:33:17 UTC
    remote annex keys: 1
    remote annex size: 355.86 megabytes
    ```

<!--list-separator-->

-  Copy the files over

    At this point, we’re ready to start backing up our files! Rsync is the easiest way to copy our files over, but any tool that validates the files’ checksums will work.

    ```bash
    $ cd /mnt/drive0/annex
    $ rsync -h --progress /mnt/somefarawayland/big_buck_bunny.mp4 ./

    $ git annex add ./big_buck_bummy.mp4
    $ git commit -S -m "🅱️ig 🅱️uck 🅱️unny"
    $ git annex sync
    ```

    Syncing the file is a bit like pushing. It makes sure that all other remotes are aware of the commit and file. If we jump back to the origin repo and sync as well, we should see the newly committed file.

    ```bash
    $ cd ~/annex
    $ git annex sync

    $ git annex list
    here
    |drive0
    ||web
    |||bittorrent
    ||||
    _X__ big_buck_bunny.mp4
    ```

    What's more, since we set the desired number of copies to 2, we can list all files missing a copy. We can even check the location of the file and grab some info on the drive – all the info you’d ever need when recovering offline data.

    ```bash
    $ git annex list --lackingcopies 1
    here
    |drive0
    ||web
    |||bittorrent
    ||||
    _X__ big_buck_bunny.mp4

    $ git annex whereis big_buck_bunny.mp4
    whereis big_buck_bunny.mp4 (1 copy)
        0eb61bd8-80d8-4ebe-8ba8-2f93296ac1ad -- wgriggs@DebianBox:/mnt/drive0/annex [drive0]
    ok
    ```

    You might notice as well that if you list the repo, the files have been moved into a `.git/annex` directory and replaced by a symlink. This structure lets you organize your files -- no matter how large -- into directories which span multiple harddrives.

    ```bash
    $ ls -l
    big_buck_bunny.mp4 -> .git/annex/objects/some/long/path.mp4
    ```

    If, for example, I uploaded `tears_of_steel.mp4` in this same repository but on another drive, each drive would have a symlink to both files. But the links would only resolve to the actual files on each respective drive.

    ```bash
    $ git annex list --lackingcopies 1
    here
    |drive0
    ||drive1
    |||web
    ||||bittorrent
    |||||
    _X___ big_buck_bunny.mp4
    __X__ tears_of_steel.mp4

    $ ls -al /mnt/drive0
    big_buck_bunny.mp4 -> .git/annex/objects/some/long/path.mp4
    tears_of_steel.mp4 -> .git/annex/objects/some/other/path.mp4
    ```

    This use of symlinks is one of the hidden gems in git-annex. Every offline drive stores a local copy of the repository, and the content of the repository contains every symlink. Only the drive that contains the file has a valid link, but the drive knows the location of every file.

    Was your laptop with the origin repository remote stolen? Not a problem: grab any offline drive and clone the repo. The caveat here is that you need to keep the repositories on each drive up to date with git annex sync, but that shouldn’t be an issue if you perform routine maintenance.

<!--list-separator-->

-  Duplicate the files

    Now that one of our drives has the file annexed, we need to create a second copy. Setup a second drive same as before: create the filesystem, mount the drive, and clone the repository. This time, instead of using rsync to copy the files to the new drive, we can use annex get to identify files on available drives missing duplicates.

    ```bash
    $ git annex get --auto --numcopies 2
    ```

    After the file has been copied over the second drive and the repos have syncd, you'll see that a copy exists on both drives.

    ```bash
    $ git annex list
    here
    |drive0
    ||drive1
    |||web
    ||||bittorrent
    |||||
    _XX__ big_buck_bunny.mp4
    ```

<!--list-separator-->

-  Maintenance

    Let’s say this drive has the capacity for exactly one copy of `big_buck_bunny.mp4`. Before packing the drive away, I’ll run a quick disk defragmentation and data scrub to validate the file’s integrity. This step is likely overkill, but what about this process isn’t?

    ```bash
    $ btrfs filesystem defrag -vf /mnt/drive0
    $ btrfs scrub /mnt/drive0
    ```

    An important note: I’ll pull this drive out every 4-6 months and run another scrub! Part of offline storage is actually spinning the disk up, mounting it, and making sure all the files are as you expect.