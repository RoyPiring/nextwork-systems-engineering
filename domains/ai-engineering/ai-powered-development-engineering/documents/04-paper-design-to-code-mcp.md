<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Design to Code: Paper + Claude Code via MCP

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-design-engineering)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_v4h8n2s6)

---

## Introducing Today's Project!

This project converts a code-native design into a production-ready React and Tailwind application using Claude Code over MCP.

The goal is to remove the separation between design and development by working on a canvas that maps directly to HTML and CSS. Instead of exporting assets or translating layouts, the system operates on a shared representation where design decisions are already code. This removes rework and enables faster iteration across layout, styling, and implementation.

### Key tools and concepts

The system uses Paper as a code-native design tool, Claude Code for generation, MCP for communication, and React with Tailwind for implementation.

The core idea is eliminating abstraction layers. Layout is defined using real DOM properties, flexbox governs structure, and AI writes directly into that system. This ensures that what is designed is immediately usable and production-aligned.

### Challenges and wins

This project took approximately 90 minutes. The main challenge was stabilizing MCP communication between Paper and Claude Code.

Once resolved, the system enabled direct manipulation of the canvas through prompts. That confirmed the model can operate as both designer and developer in a single loop without context switching.

---

## Designing a Dashboard on a Code-Native Canvas

The design is created directly in Paper using a canvas backed by HTML and CSS.

Every element maps to a real DOM structure. Containers behave as divs, spacing reflects margin and padding, and layout properties are applied exactly as a browser would render them. This removes any translation step between design and code.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_j6w2n8r4)

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_w5j9t3f7)

### Why I needed Paper Desktop, not the browser version

The desktop version provides direct integration with Claude Code.

This allows real-time updates and eliminates the gap between the design tool and execution layer. Without this, the workflow would revert back to manual translation.

### Why Paper instead of Figma

Paper operates as a code-native system while Figma is an abstraction layer.

In Paper, layout properties directly map to CSS, ensuring that what is built visually behaves exactly the same in code. This removes inconsistencies and reduces implementation overhead.

---

## Connecting Claude Code to Paper via MCP

MCP enables direct interaction between Claude Code and the design canvas.

The plugin is installed and activated within Claude Code, allowing prompts to create and modify elements. This establishes a persistent connection where both systems operate on the same structure.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_p2f8d4z6)

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_g3r7v1k5)

### What the marketplace and install commands each did

The marketplace command registers a plugin source so Claude Code can discover Paper plugins.

The install command retrieves and installs the Paper Desktop plugin into the environment. Reloading plugins activates the connection in the current session, enabling MCP communication.

### How MCP bridges design and code

The canvas functions as the DOM.

When Claude writes HTML and CSS, it is applied directly to the design surface. There is no export step because the design is already code. This creates a single system where design and development operate together.

---

## Building the AI Skills Explorer Layout

The layout is constructed using flexbox-based structures.

A main artboard defines the container, followed by a header and multiple content sections. Skill cards and trending sections are arranged using flex layouts to ensure alignment and spacing are consistent.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_v4h8n2s6)

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_d8k2n6q4)

### Why flex layouts work better than absolute positioning for AI agents

Flexbox defines relationships instead of coordinates.

This allows spacing and alignment to adjust dynamically without recalculating positions. Absolute positioning requires fixed values and breaks when content changes.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_k7m3q9v5)

### Why duplicating one card beats building three from scratch

The design emphasizes reuse through duplication.

Creating a single card and duplicating it ensures consistency across elements. This reduces variability and aligns with component-based frontend design principles used in React.

### Structuring the layout with flexbox

The layout forms a structured dashboard.

The header, skill cards, and trending sections are all composed using flex containers. Each element is already represented as HTML with inline CSS, meaning the design is fully executable without conversion.

---

## Populating the Design with Real AI Trend Data

The layout is filled with real content to validate behavior.

Skill cards include roles, demand levels, and salary ranges, while trending sections include tools and descriptions. This ensures the design can handle real-world variability.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_y3n7t1f5)

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_u8c2f6j4)

### How Claude Code updated the canvas without any export step

Claude writes directly into the Paper document model.

MCP acts as the bridge, allowing HTML and CSS to be applied in real time. The canvas updates immediately because it is already backed by DOM structures.

### From placeholder to production content

Placeholder content hides layout issues.

Real data exposes spacing problems, overflow, and inconsistencies. The design must be adjusted after content is applied to ensure it holds under real conditions.

---

## Generating a React and Tailwind Site from the Design

The design is converted into a working frontend.

Claude Code reads computed styles and generates React components with Tailwind classes. The result is a production-ready application that mirrors the design.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_d4g8j2q6)

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_m9t3w7z1)

### Why Paper explicitly recommends React and Tailwind for code generation

React maps directly to the component structure of the canvas.

Tailwind maps directly to CSS values. This creates a near one-to-one translation from design to implementation, minimizing loss of fidelity.

### Comparing the Paper design to the live site

The generated site closely matches the design.

CSS properties are translated into Tailwind utilities, and where no standard utility exists, arbitrary values preserve exact styling.

---

## Handing Claude Code a Red Pen (Secret Mission)

The design is reviewed through critique.

Claude is prompted to evaluate layout decisions and suggest improvements, focusing on refinement rather than expansion.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/ai-design-engineering_v9h3c7p1)

### Where I agreed and disagreed with the AI critique

Refinement requires judgment.

Typography and emphasis changes improved clarity, while certain suggestions conflicted with the design system and were rejected. This reinforces that AI output must be evaluated, not accepted blindly.

---

## What I Learned

This project shows that design and development can operate as a single system when the design layer is code-native.

It proves that AI can generate production-ready frontends directly from structured layouts. The next step is improving performance and optimizing the frontend for real-world usage.

---

---
