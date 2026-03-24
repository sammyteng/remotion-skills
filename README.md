# remotion-skills

> An AI coding skill for programmatic video creation with [Remotion](https://www.remotion.dev).

Transform natural language prompts into React-based video animations -- rendered to MP4.

```
"Make a 30-second product demo video" -> React + Remotion code -> MP4
```

## What It Does

This skill gives your AI assistant deep knowledge of Remotion's API, patterns, and best practices so it can:

- Generate complete Remotion projects from a description
- Compose multi-scene videos with proper timing and transitions
- Create data visualization animations (charts, counters, progress bars)
- Add professional text animations (typewriter, fade, slide)
- Apply cinematic effects (spring physics, easing curves, parallax)

## Install

### Antigravity (Gemini CLI)
```bash
mkdir -p ~/.gemini/antigravity/skills/remotion-skills
curl -o ~/.gemini/antigravity/skills/remotion-skills/SKILL.md \
  https://raw.githubusercontent.com/sammyteng/remotion-skills/main/SKILL.md
  ```

  ### Claude Code
  ```bash
  mkdir -p ~/.claude/skills/remotion-skills
  curl -o ~/.claude/skills/remotion-skills/SKILL.md \
    https://raw.githubusercontent.com/sammyteng/remotion-skills/main/SKILL.md
    ```

    ### Manual
    Copy `SKILL.md` to your AI tool's skills directory.

    ## Usage

    Just describe your video in natural language:

    ```
    Make a 15-second SaaS product demo with dark theme.
    Scene 1: Brand logo entrance animation
    Scene 2: Three key feature cards appearing one by one
    Scene 3: CTA button with "Start Free Trial"
    ```

    The AI will generate complete Remotion code ready to preview and render.

    ## Requirements

    - Node.js 18+
    - A Remotion-compatible project (npx create-video@latest)

    ## License

    MIT
    
