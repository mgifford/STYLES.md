# STYLE.md: Human & AI Design Standards

A framework for creating consistent, accessible, and sustainable design standards that are equally readable by humans and AI Agents.

## Why STYLE.md?
In an era of AI-augmented development, a style guide can no longer just be a PDF or a Figma board. It must be a **machine-readable logic gate**. This project provides a standardized format for defining "how we work" so that:
- **Humans** have a clear, plain-language reference.
- **AI Agents** (via [[AGENTS.md]]) have a set of constraints to follow when generating code or content.

## The Three Pillars
This project is part of a larger ecosystem of standards:
1.  [[ACCESSIBILITY.md]]: The foundational requirement. Style is a subset of accessibility.
2.  [[SUSTAINABILITY.md]]: The environmental constraint. Good style is lightweight and efficient.
3.  [[AGENTS.md]]: The operational layer. How AI interacts with these standards.

## Project Structure
This repository contains a variety of "flavors" to demonstrate how the same structural logic can be applied to different organizational needs:

- **/templates**: Scaffolds to help you start your own STYLE.md.
- **/examples/formal-gov**: Designed for public trust and high-compliance environments.
- **/examples/tech-minimal**: Focused on speed, precision, and documentation.
- **/examples/low-bandwidth**: A sustainability-first approach for low-energy environments.

## How to Use This
1.  **Fork** this repository.
2.  **Select a flavor** from the `/examples` folder that matches your project's intent.
3.  **Rename** it to `STYLE.md` and place it in your project's root directory.
4.  **Reference** it in your LLM prompts or `AGENTS.md` file to ensure AI-generated output stays "on-brand."
