---
name: remotion-skills
description: "AI-powered programmatic video creation with Remotion. Generates React-based video animations from natural language prompts. Use for: product demos, data visualization videos, animated infographics, marketing videos, tutorial recordings, and dynamic content. Workflow: natural language -> React/Remotion code -> render to MP4. Supports: scene composition, transitions, text animations, SVG animations, audio sync, and data-driven video generation."
---

# Remotion AI Video Creation

Create programmatic videos using the Remotion framework. Every frame is a React component render -- describe your video in plain language and get working code.

```
Natural language -> React components -> Remotion render -> MP4 video
```

## When to Use

**Must Use**
- Creating product demo or promotional videos
- - Building data visualization animations
  - - Generating marketing content programmatically
    - - Making tutorial or explainer videos
     
      - **Skip**
      - - Simple static image exports (use image generation tools instead)
        - - Videos requiring live footage or real camera recordings
         
          - ---

          ## Core Concepts

          **Three Remotion primitives:**
          - <Composition> -- defines width, height, fps, total frames
          - - <Sequence> -- controls when content appears (from frame, duration frames)
            - - useCurrentFrame() -- gets current frame number to drive animations mathematically
             
              - ---

              ## Environment Setup

              ```bash
              # Create new Remotion project
              npx create-video@latest

              # Install Remotion in existing project
              npm install @remotion/core @remotion/player @remotion/renderer

              # Preview in browser
              npx remotion studio

              # Render to MP4
              npx remotion render src/index.ts MyComposition out/video.mp4
              ```

              ---

              ## Code Templates

              ### Basic Composition Setup

              ```tsx
              import { Composition } from 'remotion';
              import { MyVideo } from './MyVideo';

              export const RemotionRoot: React.FC = () => {
                return (
                  <>
                    <Composition
                      id="MyVideo"
                      component={MyVideo}
                      durationInFrames={150}
                      fps={30}
                      width={1920}
                      height={1080}
                      defaultProps={{ title: 'My Video' }}
                    />
                  </>
                );
              };
              ```

              ### Animated Component

              ```tsx
              import { useCurrentFrame, interpolate, spring, useVideoConfig } from 'remotion';

              export const AnimatedTitle: React.FC<{ title: string }> = ({ title }) => {
                const frame = useCurrentFrame();
                const { fps } = useVideoConfig();

                const scale = spring({ fps, frame, config: { damping: 200 } });
                const opacity = interpolate(frame, [0, 20], [0, 1], { extrapolateRight: 'clamp' });

                return (
                  <div style={{ transform: `scale(${scale})`, opacity }}>
                    <h1>{title}</h1>
                  </div>
                );
              };
              ```

              ### Timeline Control with Series

              ```tsx
              import { Series } from 'remotion';

              export const MyVideo = () => (
                <Series>
                  <Series.Sequence durationInFrames={60}><Intro /></Series.Sequence>
                  <Series.Sequence durationInFrames={120}><MainContent /></Series.Sequence>
                  <Series.Sequence durationInFrames={90}><Outro /></Series.Sequence>
                </Series>
              );
              ```

              ---

              ## Animation Quick Reference

              | Function | Use Case | Example |
              |----------|----------|---------|
              | interpolate(frame, [0,30], [0,1]) | Linear mapping | opacity, position |
              | spring({ fps, frame }) | Physics-based spring | scale, bounce-in |
              | Math.sin(frame / fps) | Looping animation | oscillate, wave |

              ---

              ## Common Effects

              ### Typewriter Text
              ```tsx
              const charsToShow = Math.floor(interpolate(frame, [0, 60], [0, text.length], { extrapolateRight: 'clamp' }));
              return <span>{text.slice(0, charsToShow)}</span>;
              ```

              ### Animated Number Counter
              ```tsx
              const value = interpolate(frame, [0, 90], [0, 1000000], { extrapolateRight: 'clamp' });
              return <span>{Math.floor(value).toLocaleString()}</span>;
              ```

              ### Progress Bar
              ```tsx
              const progress = interpolate(frame, [30, 120], [0, 100], { extrapolateRight: 'clamp' });
              return <div style={{ width: `${progress}%`, height: 8, background: '#007AFF' }} />;
              ```

              ### Staggered Card Entrance
              ```tsx
              {items.map((item, i) => (
                <Sequence key={i} from={i * 15}><Card data={item} /></Sequence>
              ))}
              ```

              ---

              ## AI Workflow

              1. **Confirm Specs** -- Size, duration (seconds x fps = frames), FPS
              2. 2. **Plan Scenes** -- List each scene with time range and animation style
                 3. 3. **Generate Code** -- One component per scene, compose with <Series>
                 4. **Preview & Render** -- npx remotion studio -> npx remotion render
                
                 5. ---
                
                 6. ## Video Size Reference
                
                 7. | Format | Width | Height | Use Case |
                 8. |--------|-------|--------|----------|
                 9. | Landscape HD | 1920 | 1080 | YouTube, website |
                 10. | Vertical | 1080 | 1920 | TikTok, Reels, Shorts |
                 11. | Square | 1080 | 1080 | Instagram feed |
                
                 12. ---
                
                 13. ## Useful Links
                
                 14. - Official docs: https://www.remotion.dev/docs
                     - - Starter templates: https://github.com/remotion-dev/template-helloworld
                       - 
