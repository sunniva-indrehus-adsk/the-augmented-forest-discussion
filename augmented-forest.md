---
marp: true
theme: theme.css
paginate: true
---

<!--
THE AUGMENTED FOREST: a 20-minute recap of Kent Beck's GOTO Copenhagen 2026
keynote (Fri 2 Oct, TAP1 Main Stage). Eleven slides, about 1.5–2 minutes each,
with time left for questions. The slides carry pictures; the speaker notes
("Say:") carry the story.

Same theme as the "Jenter i AI" deck (theme.css). The illustrations are flat
SVGs in figures/augmented-forest/, drawn for this deck in one palette:
forest green, desert sand, and Autodesk blue for the genie.
-->

<style>
:root {
  --forest: #2E7D4F;
  --desert: #C08A2E;
}

/* Big illustration with a label underneath. Used on most slides. */
.scene { display: flex; flex-direction: column; align-items: center; text-align: center; }
.scene img { display: block; width: 100%; height: auto; }
.scene .label {
  font-family: var(--display);
  font-weight: 700;
  font-size: 1.25em;
  margin-top: 0.15em;
}
.scene .tag { color: var(--muted); font-size: 0.8em; margin-top: 0.1em; }
.forest-c { color: var(--forest); }
.desert-c { color: var(--desert); }
.genie-c  { color: var(--accent); }

/* Three icons with a short label each. */
.icons {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2em;
  margin-top: 1.4em;
  text-align: center;
}
.icons img { width: 170px; height: 170px; display: block; margin: 0 auto 0.5em; }
.icons b { display: block; font-family: var(--display); font-size: 1.15em; }
.icons span { color: var(--muted); font-size: 0.8em; }

.big-quote {
  font-family: var(--display);
  font-weight: 700;
  font-size: 1.6em;
  line-height: 1.25;
  letter-spacing: -0.01em;
}
.attrib { color: var(--muted); font-size: 0.7em; margin-top: 0.6em; }
</style>

<!-- _class: title title-photo -->
<!-- _header: 'GOTO Copenhagen 2026 · recap' -->
<!-- _paginate: false -->

<!-- White title slide: title-photo gives black type, the black Autodesk logo
     and a blue eyebrow. --photo: none drops the photo, so only the theme's
     white corner gradients are left, white on white. -->
<style scoped>
section { --photo: none; }
.hero { position: absolute; right: 40px; top: 110px; width: 600px; }
.hero img { display: block; width: 100%; }
.hero .lamp { position: absolute; width: 44%; left: -4%; bottom: -8%; }
h1, h2, h3 { max-width: 560px; }
</style>

<div class="hero">
  <img src="figures/augmented-forest/forest.svg" alt="">
  <img class="lamp" src="figures/augmented-forest/genie.svg" alt="">
</div>

### Kent Beck's keynote, retold

# The Augmented Forest

## Forests, deserts and genies

<!-- Say (0:30): Introduce yourself in one sentence. "The closing keynote at
     GOTO Copenhagen this year was Kent Beck: creator of XP, TDD, co-author of
     the Agile Manifesto. I've been thinking about it since, so here it is in
     twenty minutes." -->

---

# Kent Beck

<style scoped>
.bio { display: grid; grid-template-columns: 340px 1fr; gap: 3em; align-items: center; margin-top: 0.6em; }
.bio .portrait { width: 340px; height: 340px; border-radius: 50%; overflow: hidden; box-shadow: 0 0 0 8px var(--paper), 0 0 0 9px var(--rule); }
.bio .portrait img { width: 100%; height: 100%; object-fit: cover; display: block; }
.bio ul { margin: 0; padding-left: 1.1em; font-size: 1.05em; line-height: 1.6; }
.bio li strong { font-family: var(--display); }
.bio .figcap { text-align: center; margin-top: 1em; }
</style>

<div class="bio">
<div>
  <div class="portrait"><img src="figures/augmented-forest/kent-portrait-hat.jpg" alt="Kent Beck smiling, in a blue fedora and a bow tie"></div>
  <div class="figcap">Photo: Robert Opiyo, via kentbeck.com</div>
</div>
<div>

- Created **Extreme Programming**
- Rediscovered **test-driven development**
- Co-created **JUnit** with Erich Gamma
- Signed the **Agile Manifesto**, 2001
- Wrote *Tidy First?*, and codes with **genies** every day

</div>
</div>

<!-- Say (1:00): Most of the room knows the name, so keep this quick. The
     point to make: this isn't an AI hype person. It's someone who has spent
     forty years on how to change code safely, and who now spends his days
     coding with AI agents and writing about what he finds. -->

---

# GOTO Copenhagen 2026

<style scoped>
/* Two photos side by side at the same height. 418 px is the selfie's own
   4:3 height at this width, so the selfie isn't cropped: there are faces
   right at both edges. The stage photo (about 1.23:1) is taller, so cover
   trims a little off its top and bottom instead: rigging and audience. */
.opening { display: grid; grid-template-columns: 1fr 1fr; gap: 1.4em; margin-top: 0.4em; }
.opening img { display: block; width: 100%; height: 418px; object-fit: cover; border-radius: 4px; }
.opening .figcap { margin-top: 0.35em; }

/* Nick wasn't in the selfie, so his headshot is added in. Placed and sized
   in percent of the selfie so it scales with it: he sits at the far side
   of the table in the middle, between the two men, with two people to his
   left and three to his right. At 11% of the photo's width his face is the
   size of his neighbours', and his head is level with theirs. No ring: a soft
   radial mask fades the edge into the wall behind, so he reads as part of
   the photo rather than a badge on top of it. */
.opening .group { position: relative; }
.opening .group .nick {
  position: absolute;
  left: 37.5%;
  top: 38%;
  width: 11%;
  aspect-ratio: 1;
  height: auto;
  border-radius: 0;
  object-fit: cover;
  object-position: center 40%;
  -webkit-mask-image: radial-gradient(circle at 50% 48%, #000 55%, transparent 71%);
  mask-image: radial-gradient(circle at 50% 48%, #000 55%, transparent 71%);
}
</style>

<div class="opening">
  <div class="group">
    <img src="figures/augmented-forest/goto-selfie.jpg" alt="Selfie with colleagues at GOTO Copenhagen 2026">
    <img class="nick" src="figures/augmented-forest/nick-headshot.png" alt="Nick">
    <div class="figcap">At GOTO Copenhagen 2026</div>
  </div>
  <div>
    <img src="figures/augmented-forest/kent-forest-genie.jpg" alt="Kent Beck on stage in front of his handwritten title slide: The Forest Genie">
    <div class="figcap">On stage, the talk was called <em>The Forest Genie</em></div>
  </div>
</div>

<!-- Say (1:00): Start with the selfie: who you went with, and what the
     conference was like. Then the stage photo.

     Mention the photo: the program said "The Augmented Forest", but his
     handwritten first slide said "The Forest Genie".

     Background: the Forest & Desert metaphor is from Beth Andres-Beck and
     Kent Beck (Øredev 2024). The genie is Kent's word for AI coding agents,
     used since spring 2025. The keynote's question was: AI makes programming
     more fun and harder at the same time. How do we keep up, still get work
     done, and explain it to people who don't code? -->

---

# Two landscapes

<style scoped>
.pair { display: grid; grid-template-columns: 1fr 1fr; gap: 3em; margin-top: 0.4em; }
.pair .scene img { width: 92%; }
.words { font-size: 0.85em; margin-top: 0.5em; color: var(--ink); }
.runs { font-family: var(--display); font-weight: 700; font-size: 1.3em; margin-top: 0.4em; }
</style>

<div class="pair">
  <div class="scene">
    <img src="figures/augmented-forest/desert.svg" alt="Desert">
    <div class="words">Deadlines · bugs · painful on-call · change is the enemy</div>
    <div class="runs desert-c">Runs on fear</div>
  </div>
  <div class="scene">
    <img src="figures/augmented-forest/forest.svg" alt="Forest">
    <div class="words">Small safe steps · tests · rare bugs · change is expected</div>
    <div class="runs forest-c">Runs on trust</div>
  </div>
</div>

<!-- Say (2:00): Desert first, because most of us have been there. "We travel
     by force of will under an oppressive heat." Little margin, no time to look
     back, estimates rule, metrics used to control people.

     The forest is resource-rich and self-renewing: today's work makes
     tomorrow easier. Tests, pairing, refactoring, continuous release. On-call
     is "no big deal" because there are so few bugs.

     Land on the bottom line. Kent's view: the single most important
     difference is trust vs fear. Trust in each other, in yourself, in the
     software and in the future.

     Why the metaphor matters (Beth Andres-Beck): "This architecture you've
     described sounds like a lush forest, but we are living in the desert."
     Advice doesn't carry over. Forest advice ("write tests, pair") misfires in
     the desert, where there's no slack. Desert advice ("more estimates, more
     review layers") makes no sense in the forest. Getting from desert to
     forest takes small, safe steps the whole community takes: "No developer
     can do it alone, and no amount of technology will get us there." -->

---

# Features &amp; futures

<style scoped>
/* Photo left, at the height the slide allows under the title (1800 x 1611,
   so 480 px tall is 536 px wide). Features/futures stacked on the right. */
.ff { display: grid; grid-template-columns: 536px 1fr; gap: 2.4em; align-items: center; margin-top: -0.2em; }
.ff .photo img { display: block; width: 536px; height: 480px; object-fit: cover; border-radius: 4px; }
.ff .photo .figcap { margin-top: 0.35em; }
.ff .pair { display: grid; grid-template-columns: 1fr 1fr; gap: 1.2em; text-align: center; }
.ff .pair img { width: 110px; height: 110px; display: block; margin: 0 auto 0.3em; }
.ff .pair b { display: block; font-family: var(--display); font-size: 1.2em; }
.ff .pair span { color: var(--muted); font-size: 0.8em; }
.speed { margin-top: 1.6em; text-align: center; font-family: var(--display); font-weight: 700; font-size: 1.1em; line-height: 1.5; }
.speed .was { color: var(--muted); }
.speed .now { color: var(--accent); }
</style>

<div class="ff">
  <div class="photo">
    <img src="figures/augmented-forest/kent-features-futures.jpg" alt="Kent Beck on stage at GOTO Copenhagen in front of his hand-drawn Features &amp; Futures chart">
    <div class="figcap">Kent Beck, GOTO Copenhagen 2026</div>
  </div>
  <div>
    <div class="pair">
      <div><img src="figures/augmented-forest/icon-features.svg" alt=""><b>Features</b><span>what it does today</span></div>
      <div><img src="figures/augmented-forest/icon-futures.svg" alt=""><b class="forest-c">Futures</b><span>what it could do tomorrow</span></div>
    </div>
    <div class="speed">
      <span class="was">100 people · 10 years</span><br>↓<br><span class="now">1 person + genie · 1 week</span>
    </div>
  </div>
</div>

<!-- Say (1:45): Kent's older idea, and the lens for the rest of the talk. Software is
     valuable in two ways: the features it has today, and the options it keeps
     open for what it could do next. Every feature spends some of those
     options, so the system gets stiffer over time, unless you put options
     back with tidying, tests and structure.

     Point at the photo, Kent's own chart. Blue curve: every feature spends
     futures, sliding down to the corner where nothing more can be built. Red
     staircase: alternate features with tidying, and both keep growing.

     Features are easy to see and count, so they win. Futures sit below the
     surface, so they get skipped.

     The genie is great at features and no good at managing futures. The line
     at the bottom is Kent's: it used to take a hundred people ten years to
     reach the point where there are no options left. With a genie, one
     person can get there in a week. Leave that hanging: the genie is next. -->

---

# The Genie

<style scoped>
.g { display: grid; grid-template-columns: 1.1fr 1fr; gap: 2em; align-items: center; margin-top: -0.6em; }
</style>

<div class="g">
<img src="figures/augmented-forest/genie.svg" alt="Genie lamp with blue smoke">
<div>
<div class="big-quote">"Sometimes it's useful, and sometimes it's damaging."</div>
<div class="attrib">Kent Beck on AI coding agents</div>
</div>
</div>

<!-- Say (1:30): Why "genie" and not "assistant"? A genie grants wishes. It's
     powerful, eager to please, and unpredictable: you get what you asked for,
     which isn't always what you meant.

     Kent's name for working with it properly is "augmented coding", as
     opposed to vibe coding. In vibe coding you only care whether it works.
     In augmented coding you still care about the code: tested, tidy,
     understood. Same values as before, more leverage. -->

---

# How genies misbehave

<div class="icons">
  <div><img src="figures/augmented-forest/icon-cheat.svg" alt=""><b>It cheats</b><span>deletes the failing test</span></div>
  <div><img src="figures/augmented-forest/icon-overreach.svg" alt=""><b>It overreaches</b><span>grants wishes you didn't make</span></div>
  <div><img src="figures/augmented-forest/icon-tarpit.svg" alt=""><b>It degrades</b><span>the genie tarpit</span></div>
</div>

<!-- Say (1:45): All three are from Kent's own experience.
     Cheats: you asked for green tests, so deleting the failing one counts.
     Overreaches: extra features, extra abstractions, rewrites nobody asked for.
     Degrades: "a degraded facsimile of the mediocre code it trained on".
     Complexity piles up until the genie itself gets stuck in it. That's the
     serious one: the genie makes the code harder to change, and harder-to-
     change code makes the genie worse. It's the features-and-futures curve
     from two slides back, sliding down to zero options at genie speed.

     If Kent showed a live example here, tell it. -->

---

# Taming the genie

<div class="icons">
  <div><img src="figures/augmented-forest/icon-tests.svg" alt=""><b>Tests</b><span>the wish, written down</span></div>
  <div><img src="figures/augmented-forest/icon-steps.svg" alt=""><b>Small steps</b><span>short leash, cheap to undo</span></div>
  <div><img src="figures/augmented-forest/icon-eye.svg" alt=""><b>Watch it</b><span>read the diff</span></div>
</div>

<p style="text-align:center; margin-top:1.3em; font-family:var(--display); font-weight:700; font-size:1.2em">Every one of these is a <span class="forest-c">forest</span> practice.</p>

<!-- Say (1:45): Kent calls TDD a superpower with agents: the test is the
     wish, written so the genie can't misread it. Small steps keep it on a
     short leash. Read the diff, especially changes to tests.
     One more: asking for code "like Kent Beck" improved the style but not the
     architecture. Design took explicit constraints.

     Then pause on the bottom line. This is the turning point of the talk. -->

---

# AI intensifies both

<style scoped>
.amp { display: grid; grid-template-columns: 170px 40px 110px 50px 1fr; align-items: center; gap: 0.5em; margin: 0.2em 0; }
.amp img { display: block; width: 100%; }
.amp .op { font-family: var(--display); font-weight: 700; font-size: 1.6em; color: var(--muted); text-align: center; }
.amp .out { display: flex; align-items: center; gap: 1em; }
.amp .out img { width: 300px; }
.amp .out b { font-family: var(--display); font-size: 1.15em; }
</style>

<div class="amp">
  <img src="figures/augmented-forest/desert.svg" alt="Desert"><div class="op">+</div>
  <img src="figures/augmented-forest/genie.svg" alt="Genie"><div class="op">→</div>
  <div class="out"><img src="figures/augmented-forest/desert.svg" alt="Bigger desert"><b class="desert-c">More code,<br>more sand</b></div>
</div>
<div class="amp">
  <img src="figures/augmented-forest/forest.svg" alt="Forest"><div class="op">+</div>
  <img src="figures/augmented-forest/genie.svg" alt="Genie"><div class="op">→</div>
  <div class="out"><img src="figures/augmented-forest/forest.svg" alt="Bigger forest"><b class="forest-c">Faster learning,<br>more forest</b></div>
</div>

<!-- Say (2:00): This is the thesis from the keynote abstract: AI intensifies
     both experiences. The genie isn't a landscape. It amplifies whatever
     landscape it lands in.

     In the desert: more code, faster, under the same pressure. No tests to
     catch a wish gone wrong, reviewers drowning in diffs, tangled code, the
     tarpit.

     In the forest: tests turn every wish into a checkable contract, small
     steps are cheap to throw away, tidy code is easier for the genie to read
     too, and experiments become almost free.

     The genie is identical in both rows. Only the soil differs. Forest
     practices used to be "nice to have when we find time". With a genie,
     they're the leash.

     For non-programmers: "We bought the genie, why aren't we faster?"
     "Because we put it in the desert." -->

---

# Five principles

<style scoped>
.pr { display: grid; grid-template-columns: 600px 1fr; gap: 2.4em; align-items: center; margin-top: -0.2em; }
.pr .photo img { display: block; width: 600px; height: auto; border-radius: 4px; }
.pr ol { margin: 0; padding-left: 1.3em; font-family: var(--display); font-weight: 700; font-size: 1.3em; line-height: 1.75; }
.pr ol li::marker { color: var(--forest); }
</style>

<div class="pr">
<div class="photo"><img src="figures/augmented-forest/kent-principles.jpg" alt="Kent Beck on stage in front of his handwritten list of principles"></div>
<div>

1. Promote connection
2. Automate toil
3. Preserve struggle
4. Surface choices
5. Encourage learning

</div>
</div>

<!-- Say (1:45): Kent's handwritten list, as he showed it. These are how to
     grow the forest when you have a genie: use it to automate the toil, but
     keep the people connected, keep the choices visible, and keep learning.

     Spend the most time on "preserve struggle". The genie can take away the
     struggle that's how we learn, and a team that stops learning slides
     back towards the desert. (Fill in what Kent said about each one; the
     photo only shows the words.)

     Then turn it back to the room:
       Ask   - where are we forest, and where desert?
       Check - would our tests catch a wish gone wrong?
       Plant - one small, safe step this sprint: a test, a tidying, a
               smaller slice. -->

---

<!-- _class: statement -->

<style scoped>
.end { display: grid; grid-template-columns: 1fr 1fr; gap: 2em; align-items: center; }
.end .art { position: relative; }
.end .art .lamp { position: absolute; width: 46%; right: -4%; bottom: -6%; }
.src { position: absolute; left: var(--margin-x); right: var(--margin-x); bottom: 64px; font-size: 13px; color: var(--muted); line-height: 1.6; }
.src a { color: var(--muted); }
</style>

<div class="end">
<div>
<div class="big-quote">Plant the forest before you summon the genie.</div>
<p style="margin-top:1.2em; color:var(--muted)">Thank you · Questions?</p>
</div>
<div class="art">
<img src="figures/augmented-forest/forest.svg" alt="">
<img class="lamp" src="figures/augmented-forest/genie.svg" alt="">
</div>
</div>

<div class="src">
Kent Beck, <em>The Augmented Forest</em>, GOTO Copenhagen 2026 · <a href="https://gotocph.com/2026/sessions/4170/the-augmented-forest">gotocph.com/2026/sessions/4170</a> · <a href="https://dl.acm.org/doi/10.1145/3837729.3850163">doi.org/10.1145/3837729.3850163</a><br>
Beth Andres-Beck, <em>Forest &amp; Desert</em> · <a href="https://newsletter.kentbeck.com/p/forest-and-desert">newsletter.kentbeck.com/p/forest-and-desert</a> · Kent Beck on genies · <a href="https://newsletter.kentbeck.com/t/genies">newsletter.kentbeck.com/t/genies</a> · Kent Beck, <em>Features Versus Futures</em> · <a href="https://www.youtube.com/watch?v=AZn7JZiNetA">youtube.com/watch?v=AZn7JZiNetA</a>
</div>

<!-- Say (0:30): Pause, say thank you, take questions. The closing line is
     your own summary of the talk, not a Kent Beck quote; don't attribute it
     to him. -->
