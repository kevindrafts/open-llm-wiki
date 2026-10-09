Design systems for AI-built products turn taste into reusable context: design.md files, reference screenshots, HTML examples, component libraries, skills, typography, color, spacing, motion, and interaction rules that agents can apply across landing pages, apps, slides, videos, and marketing assets without drifting into generic AI design.

# Design Systems for AI-Built Products

## Design.md as Portable Taste

The design.md idea mirrors `AGENTS.md` and `SKILL.md`: write the design system down so an agent can reuse it. A good design file captures typography, colors, spacing, layout rules, animation, interaction patterns, visual references, and constraints.

The practical benefit is consistency. AI can one-shot an attractive first screen, but it often drifts when asked to create secondary pages, slides, promo videos, ads, or new sections. A design.md file helps preserve the same visual DNA across mediums.

## Reference, Systemize, Iterate, Remix

The workflow from the design source is:

1. Start with references from strong products or designers.
2. Generate or collect an initial design direction.
3. Inspect what works: typography, spacing, colors, motion, imagery, and layout.
4. Systemize it into design.md and reusable skills.
5. Iterate through many small refinements.
6. Remix the system into other mediums such as slides, promo videos, social images, and app screens.

This fits [[distribution-led-ai-startups]] because better design can raise landing-page conversion, trust, and shareability.

## Skills and Component Libraries

Design skills act like ingredients: skeuomorphic treatments, 3D elements, lasers, motion patterns, illustration styles, or typography systems. Component libraries such as Tail Arc and tools such as Paper can help agents produce more polished layouts by giving them concrete blocks and references instead of abstract "make it better" prompts.

Useful prompting pattern: ask for subtle refinements, consistent layouts, cohesive themes, and specific component-level changes. Broad prompts like "improve the design" often create noisy, inconsistent output.

## Visual Critique Vocabulary

The Expo design-principles source adds a useful missing layer between vague taste and fully specified design systems: a shared critique vocabulary. Contrast, hierarchy, alignment, proximity, repetition, balance, white space, and unity give a builder a concrete way to review AI-generated screens and request revisions that are more precise than "make it nicer."

This matters because design drift is often a steering problem rather than a generation problem. Agents can assemble competent layouts, but without visual language the human reviewer struggles to diagnose why an interface feels cluttered, generic, or off-brand. In practice, these principles work like an intermediate checklist between raw screenshots and a formal `design.md` system.

The article also reinforces a pragmatic workflow: let AI generate a first pass, review a screenshot against the principles, then iterate with targeted feedback. That fits the broader pattern here of turning taste into reusable operational context rather than expecting one-shot perfection.

## Establish a direction through prototypes

The Railcode case adds a step before documenting a design system. Explore several interpretations of a specific brand idea, preserve variants with their prompts, and compare them side by side. Majuri kept these prototypes in single HTML files and used interactive controls to tune colors and placement. After choosing the hero's direction, he reused it to guide other assets and sections.

The connection to `design.md` is a wiki synthesis. Exploration produces the references and decisions that a reusable design file can preserve. See [[design-principles-for-ai-app-development]] for the case details.

## Preserve the brief and the critique baseline

Chimala's discover, define, and deliver workflow adds useful material for reusable design context: the selected creative brief, the human preferences behind it, approved screenshots, reference images, and explicit examples of unwanted decoration. A stable critique prompt and comparison images make later reviews more consistent. The source recommends fresh screenshot-only critique rather than feeding the reviewer the implementer's prior rationale.

The connection to a design system is a wiki synthesis. Record the choices that survive exploration, including imagery, motion behavior, and what to leave out. Keep rejected prompts as experiments for later model evaluations, separate from the approved direction. Generated video transitions also need their source frames and continuity decisions preserved if future work is to match them. See [[design-principles-for-ai-app-development]] for the workflow and its limits.

## Taste as Moat

The sources argue that baseline AI design is improving but becoming generic. Taste becomes a differentiator because users can feel care, quality, and specificity. For builders, the actionable version is to build a second brain for design inspiration, study products in the niche, and preserve references as reusable context.

## Source Summaries

`processed/Google's Design.md is a design team in a file.md`: Meng To explains design.md as a portable design system for agents. The workflow uses references, design memory, skills, HTML examples, iteration, remixing across media, and taste as the core differentiator for AI-built products.

`processed/My Claude Code workflow no one knows about.md`: Adds a practical landing-page design workflow using reference screenshots, style guides, Paper, Tail Arc components, subtle animations, and agent-driven refinements before pushing to code and A/B testing.

`processed/How to apply professional design principles in AI app development.md`: Adds an eight-principle critique framework for steering AI-generated interfaces: contrast, hierarchy, alignment, proximity, repetition, balance, white space, and unity. The key lesson is that screenshot-based critique plus explicit visual vocabulary produces better revisions than generic "improve the design" prompts.

`processed/How our vibe coded website looks like a designer made it.md`: Adds saved prototype variants, prompt history, interactive style controls, and a chosen hero as a reference for later components.

`processed/How to turn your AI into a world-class designer.md`: Adds creative briefs shaped by human preferences, reference-based critique, generated media, saved failed prompts, and restraint as inputs to reusable design context.

## Related

- [[agent-skills-and-agent-native-tools]]
- [[distribution-led-ai-startups]]
- [[ai-native-startup-strategy]]
- [[ai-marketing-automation-workflows]]
- [[design-principles-for-ai-app-development]]
