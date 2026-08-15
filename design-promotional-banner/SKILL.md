---
name: design-promotional-banner
description: Design promotional banners for a product
---

# design-promotional-banner

Design promotional banners for what the user is working on. Gather understanding of the project through conversation history. If that context is insufficient, read the project files to understand what it does, as well as analyze the design system, which you can find in CSS files or other relevant places if it is for example a React or a Vue project.
You should gather an understanding of what the user is looking for. Whether they want a single 16:9 banner, a collection of various aspect-ratio banners or a different combination. 
Before designing also understand the purpose of these banners, whether it is social promotion, a guide, an infographics or banners to be used for twitter cards / opengraph metadata.
Ask (if the user didn't provide) the directory in which the banners should be placed. When creating them, your working files can be placed in a temporary directory (refer to your coding harness) unless specified otherwise by the user.
## When to use

This skill should be used upon invocation of it.

## Instructions

1. Understand the project and gather necessary context given previous instructions
2. Check for available tools: imagemagick (magick), browser automation tool (playwright, puppeteer, etc) if one isn't available you can utilize an available web browser.
3. Design the banners as HTML files, CSS can be inlined and should follow the project's guidelines (style) closely. Each banner (and as such, size) should be a separate HTML file.
4. Render the banners utilizing available tools (like a browser automation tool, a skill that allows for rendering HTML pages to image files or simply a web browser)
5. Output them to the directory specified by the user
6. Summarize and shortly describe each deliverable in a markdown table that you output to the conversation log.

## Additional Information
The banners should not feature very tiny elements, sometimes they will be placed in thumbnail environments which will make them impossible to see. Every element should be big enough to be seen clearly.
Avoid overly generic design elements like pills (badges) that can strongly indicate a low-effort AI-made job. The banners should feel fresh, unqiue and take into account modern design guidelines (though the priority is always the user's request and the project design system/colours).
If the user does not specify any text he would like put on the banners, they should at least specify the intent of the deliverable in which scenario the content should be written by you. When writing any content, refer to anti-slop rules.
Utilize banner design rules to achieve an aesthetically pleasing result.

## Banner design rules

A single static promotional banner built in HTML and CSS, screenshotted to PNG. Type,
shapes, and color are the only materials.

### The one-second test
- If the meaning is not readable in one second, cut elements until it is.
- One message: one offer, one benefit, one CTA. Two ideas means two banners.
- Lead with the value, then the brand. Detail belongs wherever the banner points to.

### Composition
- Three levels maximum: hook, one support line, CTA. Everything else is decoration.
- Carry hierarchy with size, weight, and color. Not boxes, borders, or shadows.
- One focal point. If hook, number, and CTA all fight for the eye, demote two.
- Keep content inside a padding of at least 5% of the short edge.
- Pick one alignment and hold it. Mixed left and center reads as unfinished.
- Lay out so the reading path runs hook, support, CTA without the viewer hunting.
- Wide canvas wants a horizontal read, tall wants a vertical stack, square takes either.
- Whitespace is structural. Crowding lowers recall of the one thing you wanted recalled.

### Implementation
- One root element, explicit width and height, `overflow: hidden`, `box-sizing:
  border-box`, zero body margin. Nothing can push past the frame.
- Flex or grid throughout. Absolute positioning only for deliberate overlays.
- Scale type and spacing with the canvas (`cqw`, `vw`, `clamp()`) so a ratio change
  does not break the template.
- No hover states, no scrollbars, no `position: fixed`. The render is a snapshot.
- Screenshot at 2x scale factor and downsample. 1x renders soft type.

### Typography
- Two typefaces maximum, three only if the third carries numbers and labels.
- Load fonts explicitly and wait for them before the screenshot. A fallback-font render
  is a broken banner that fails silently.
- Headline and support line need at least 1.5x size separation, or there is no
  hierarchy, just two competing lines.
- Headline under 6 words, support under 12, at roughly 8 to 12% of canvas height.
- Line length under 40 characters, controlled with `max-width`, not manual breaks.
- `letter-spacing: -0.02em` on large display type, `line-height` 1.05 to 1.15 for
  headlines and 1.4 for body.
- No all-caps past 4 words, no letterspaced body copy, no centered paragraphs, no type
  touching the frame edge.

### Color and contrast
- 4.5:1 for normal text, 3:1 for large or bold display text and any meaningful shape.
  Aim for 7:1 on the headline.
- Background, foreground, one accent. The accent belongs to the CTA and nothing else;
  once it appears twice it stops signalling the action. A multi-color background is one
  element, not three.
- Over a gradient or pattern, check against the lightest and darkest point behind the
  text. Fix by moving the text to a calm region, not by shrinking it.
- Never carry meaning in color alone.
- Grayscale test with `filter: grayscale(1)`. If elements merge, the hierarchy was
  doing nothing.

### Backgrounds
- The background can be the most interesting thing in the banner. It just has to lose
  the fight for attention on purpose.
- Reserve a calm zone for the type and build it into the background rather than
  patching it later. Behind the headline, keep luminance in a narrow band.
- What holds up: tight-hue linear gradients, large soft radial glows, mesh from blurred
  blobs, low-opacity grids or dot fields, angled color blocks, duotone, subtle noise
  over any of these.
- Narrow hue range reads as designed. A full spectrum sweep reads as a template.
- Base color, one gradient or pattern, optional texture. Three layers is plenty.
- Genuinely busy behind text means a real container with its own contrast budget, not a
  text shadow.
- Keep blur and glow radii large relative to the canvas. Small blurs export looking like
  compression artifacts.
- Long subtle gradients band in PNG. Add 3 to 6% noise or spread more luminance.
- The background stays behind everything. No element crossing the headline, no glow
  bleeding into the CTA.

### Decoration
- A shape separates zones, anchors a corner, or points at the CTA. Otherwise it is noise.
- Inline SVG, geometric, consistent stroke weight. Mixing filled and outlined icons
  looks accidental.
- One corner radius, reused. Mismatched radii is the clearest tell of a rushed layout.
- No shadow rescuing contrast, no borders inside borders, no glow around type.

### CTA
- One CTA. Verb first, specific outcome.
- Solid fill, clear edges, roughly 0.8em by 1.6em padding, high contrast behind it.
- Place it where the reading path ends.
- Whatever it promises has to be what the viewer finds on the other side.

### Consistency across a set
- Lock the kit first: color tokens, type pairing, radius, spacing scale, logo placement.
- Drive variants from CSS custom properties so a palette change is not a redesign.
- Recognition accumulates through the visual pattern, not the logo.
- Logo small and consistently placed. Larger than the message means it is an ego piece.

### Pre-ship QA
- View at full size and at 25%. Both must work.
- Grayscale check.
- Confirm the intended font loaded.
- Check the longest copy variant for overflow and clipped descenders.
- Cover the decoration and read the text alone. It should still make the point.
- Check for banding after export, not before.
- Copy passes the anti-slop scan.

### Common failure modes
Everything at the same visual weight. Three CTAs. A headline naming the product
category instead of the benefit. Background competing with the headline instead of
framing it. Centered everything. Shadow patching a contrast problem. Four corner radii.
Logo larger than the message. Every brand color at once. Fallback font shipped because
the render did not wait.

## Anti-slop rules for banner copy

A banner carries a headline, maybe a support line, a CTA, sometimes a badge. Fewer than
twenty words total. Every one of them has to do work. Never paraphrase a pattern to fix
it: decide what the line asserts, then assert that.

### Banned headline patterns
- Negative parallelism in all its disguises: "not just X, it's Y", "more than just a
  X", "the real X is Y", "X? Y." If nobody believes X, delete that half. If the
  contrast is real, state the winning side concretely. Usually the line asserts nothing
  and should be cut.
- The empty verb set: elevate, unlock, transform, revolutionize, supercharge, empower,
  reimagine, streamline. "Unlock your team's potential" says nothing. Name what the
  thing does.
- The arrival announcement: "The future of X is here", "Introducing the new era of X",
  "X, reimagined". Announcing significance is not the same as having it.
- Aspiration filler: "Take your X to the next level", "Your journey starts here",
  "Where X meets Y", "Simply better", "Effortlessly powerful".
- Adjective stacks: "seamless, intuitive, powerful". Two adjectives is one too many at
  headline size. Cut to the one that is falsifiable.
- Alliteration and rhyme reached for as a substitute for a claim. "Smarter. Simpler.
  Sooner." is three words that mean nothing three times.
- Staccato periods used for gravity: "Fast. Secure. Yours." Write the sentence.
- Vague quantifiers: "thousands of teams", "trusted by industry leaders". Use the real
  number or drop the claim. If the number needs supplying, leave `[ADD: how many?]`.
  Never invent one.

### CTA rules
- Verb first, specific outcome. "Get the free template", "See the pricing", "Start the
  trial". Not "Learn more", "Discover", "Get started", "Explore".
- The CTA names what happens on click. If the button says "Get the guide" the next
  screen delivers a guide.
- No urgency the offer does not have. "Limited time" on a permanent offer is a lie the
  viewer will check.

### Register
- Exclamation marks: zero. Emoji in the headline: zero, unless the brand voice is
  genuinely built on them.
- No question headlines that the viewer can answer "no" to and leave.
- No second-person flattery ("You deserve better tools").
- Sentence case for headlines unless the type system calls for caps. Title Case On A
  Marketing Headline Reads As Corporate Filler.
- Match the register to the offer. A developer tool banner that talks like a lifestyle
  brand gets ignored by both audiences.

### Overcorrection is also slop
- No forced slang, no manufactured edginess, no lowercase-everything as a personality.
- Cutting puffery is the whole job. Do not replace it with attitude.
- Preserve the actual offer, price, and terms exactly. Flag anything that looks wrong
  instead of silently rewriting it.

### Process
You cannot see your own slop, because the priors that generate it make it invisible on
re-read. Scan against the list mechanically. Rewrite by meaning, then scan the rewrite,
since rewrites smuggle the same move back in wearing different words. Repeat until a
pass returns zero hits. If a headline survives three passes, throw it out and start
from the bare claim: what does this product do for this person?

### Final test
Read the headline alone, with no logo, no background, no CTA. If it could sit on a
competitor's banner unchanged, it is not a headline yet.