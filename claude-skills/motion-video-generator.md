![video](assets/mind-blowing.mp4)
Video Generator (Remotion)
Create professional motion graphics videos programmatically with React and Remotion.

⚠️ Sandbox Environment Constraints (Read First)
This skill runs in a restricted sandbox. Know these hard limits before starting:
Blocked network domains (will fail silently or with 403):

release-assets.githubusercontent.com — blocks cloudflared binary download
remotion.media — blocks Remotion's Chrome Headless Shell auto-download (required for npx remotion still and npx remotion render)
Any Cloudflare tunnel infrastructure

What this means for the workflow:

Cannot render to MP4/PNG inside the sandbox — npx remotion render and npx remotion still both fail because Chrome Headless Shell cannot be downloaded.
Cannot expose the dev server publicly — Cloudflare tunnel binary cannot be downloaded either.
npx create-video@latest is interactive — it prompts for template selection and hangs. Never run it without piping input or use manual scaffolding instead.

Correct approach:

Scaffold manually (no create-video@latest) — create all files by hand.
Start the dev server — npm run dev works fine; server comes up at localhost:3000.
Package the project as a .tar.gz and deliver it via present_files.
User renders locally — they extract the archive, run npm install && npm run dev, then npx remotion render on their own machine where Chrome Headless Shell downloads freely.


Default Workflow (ALWAYS follow this order)

Scrape brand data (if featuring a product) — see Firecrawl section below.
Manually scaffold the project at /home/claude/output/<project-name>/ — do NOT use create-video@latest.
Write all source files — package.json, tsconfig.json, remotion.config.ts, src/index.ts, src/Root.tsx, scene components.
Install dependencies: cd output/<project-name> && npm install
Start dev server in background to verify it compiles:

bash   cd /home/claude/output/<project-name> && npm run dev > /tmp/remotion.log 2>&1 &
   # Wait for "Server ready" line
   sleep 20 && cat /tmp/remotion.log

Confirm "Built in Xms" appears in the log — this proves the code compiled with no TypeScript errors.
Package and deliver:

bash   cd /home/claude/output
   tar -czf <project-name>.tar.gz <project-name>/
   cp <project-name>.tar.gz /mnt/user-data/outputs/

Call present_files with the .tar.gz path.
Tell the user to run locally:

bash   tar -xzf <project-name>.tar.gz
   cd <project-name>
   npm install
   npm run dev          # Preview at localhost:3000
   npx remotion render <CompositionId> out/video.mp4   # Export
Never do these in the sandbox:

npx create-video@latest (hangs on interactive prompt)
npx remotion still (fails — Chrome Headless Shell blocked)
npx remotion render (same reason)
cloudflared tunnel (binary download blocked)
curl ... githubusercontent.com (blocked)
curl ... remotion.media (blocked)


Manual Scaffold Template
Use this exact structure every time:
output/<project-name>/
├── src/
│   ├── index.ts          ← registerRoot entry point
│   ├── Root.tsx          ← <Composition> declarations
│   └── <VideoName>.tsx   ← Main video + all scenes
├── public/               ← Static assets (optional)
├── package.json
├── tsconfig.json
└── remotion.config.ts
package.json (copy exactly — no bun, no create-video scripts)
json{
  "name": "<project-name>",
  "version": "1.0.0",
  "scripts": {
    "dev": "npx remotion studio",
    "build": "npx remotion bundle",
    "render": "npx remotion render"
  },
  "dependencies": {
    "remotion": "^4.0.0",
    "@remotion/bundler": "^4.0.0",
    "@remotion/renderer": "^4.0.0",
    "@remotion/cli": "^4.0.0",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "lucide-react": "^0.383.0"
  },
  "devDependencies": {
    "@types/react": "^18.0.0",
    "@types/react-dom": "^18.0.0",
    "typescript": "^5.0.0"
  },
  "remotion": {
    "entryPoint": "src/index.ts"
  }
}
tsconfig.json
json{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["ES2022", "DOM"],
    "jsx": "react",
    "strict": false,
    "module": "ES2022",
    "moduleResolution": "bundler",
    "esModuleInterop": true
  },
  "include": ["src"]
}
remotion.config.ts
tsimport { Config } from "@remotion/cli/config";
Config.setVideoImageFormat("jpeg");
Config.setOverwriteOutput(true);
src/index.ts
tsimport { registerRoot } from "remotion";
import { RemotionRoot } from "./Root";
registerRoot(RemotionRoot);
src/Root.tsx
tsximport { Composition } from "remotion";
import { MyVideo } from "./MyVideo";

export const RemotionRoot: React.FC = () => (
  <>
    <Composition
      id="MyVideo"
      component={MyVideo}
      durationInFrames={300}
      fps={30}
      width={1920}
      height={1080}
    />
  </>
);

Core Architecture
Scene timing pattern
tsx// All durations in frames at 30fps
// Scene 1: frames 0–150 (5s)
// Scene 2: frames 130–280 (5s, 20-frame overlap = seamless transition)
// Scene 3: frames 260–410 (5s)
// Total: ~410 frames (~13.7s)

export const MyVideo: React.FC = () => (
  <AbsoluteFill>
    <PersistentBackground />          {/* OUTSIDE sequences — always visible */}
    <Sequence from={0} durationInFrames={155}>
      <SceneOne />
    </Sequence>
    <Sequence from={130} durationInFrames={155}>
      <SceneTwo />
    </Sequence>
    <Sequence from={260} durationInFrames={155}>
      <SceneThree />
    </Sequence>
  </AbsoluteFill>
);
useCurrentFrame inside Sequence
Inside a <Sequence from={N}>, useCurrentFrame() returns frames relative to the sequence start (always starts at 0). You do NOT need to subtract N manually.
Core animation hooks
tsximport { useCurrentFrame, useVideoConfig, interpolate, spring } from "remotion";

const frame = useCurrentFrame();
const { fps } = useVideoConfig();

// Fade in over 30 frames
const opacity = interpolate(frame, [0, 30], [0, 1], {
  extrapolateLeft: "clamp",
  extrapolateRight: "clamp",
});

// Spring entrance (scale from 0.8 to 1)
const scale = spring({
  frame,
  fps,
  from: 0.8,
  to: 1,
  config: { stiffness: 300, damping: 20 },
});

// Slide up
const y = interpolate(frame, [0, 25], [40, 0], {
  extrapolateLeft: "clamp",
  extrapolateRight: "clamp",
});

Motion Graphics Principles
AVOID (Slideshow anti-patterns)

Fading to black between scenes
Centered text on solid backgrounds with no animation
Same transition repeated throughout
Linear, robotic motion (use spring physics)
Static holds longer than 2–3s with nothing moving
Emoji — NEVER use emoji, always use Lucide React icons

PURSUE (Motion graphics)

Overlapping transitions (next scene starts before current ends)
Layered compositions — background / midground / foreground
Spring physics for all entrances
Varied scene pacing (2–5s, mixed rhythm)
Continuous visual elements that persist across scene boundaries
Custom transitions: clipPath wipes, scale morphs, perspective flips
Lucide React for all iconography (import { Eye, ... } from "lucide-react")

Transition techniques
NameImplementationWipeclipPath: inset(0 ${100 - progress}% 0 0)Zoom-throughScale a foreground element to scale(20) while next scene fades in behindCircle revealclipPath: circle(${r}% at 50% 50%) interpolated 0→150%Perspective fliptransform: perspective(800px) rotateY(${angle}deg)Slide-pushBoth scenes translate simultaneously in same direction

Visual Style Guidelines
Typography

One display font + one body font maximum
Massive headlines (80–120px), tight letter-spacing
Keep on-screen text SHORT — viewers cannot pause
Use fontFamily: "monospace" or import Google Fonts via @remotion/google-fonts

Color

Use brand colors from Firecrawl scrape as primary palette
Avoid generic purple/indigo gradients unless brand uses them
Dark backgrounds (near-black, #050A10) with intentional accent pops
Single highlight color at high saturation (e.g. #00FFD1, #FF4444)

Layout

Asymmetric layouts — off-center type creates visual tension
Edge-aligned elements rather than everything centered
Generous whitespace as a design element
Depth: one subtle gradient layer, not stacked textures


Fetching Brand Data with Firecrawl
Use when the video features a real product or company.
bashbash scripts/firecrawl.sh "https://example.com"
Returns: brandName, tagline, headline, description, features[], logoUrl, faviconUrl, primaryColors[], ctaText, socialLinks.
Download assets after scraping:
bashmkdir -p public/images/brand
curl -s "${FAVICON_URL}" -o public/images/brand/logo.svg
curl -s "${OG_IMAGE_URL}" -o public/images/brand/og-image.png

Reusable Component Patterns
Animated background with SVG grid
tsxconst GridBackground: React.FC<{ frame: number }> = ({ frame }) => {
  const pulse = interpolate(frame % 90, [0, 45, 90], [0.05, 0.2, 0.05]);
  return (
    <div style={{ position: "absolute", inset: 0, background: "#030A0F" }}>
      <svg style={{ position: "absolute", inset: 0, width: "100%", height: "100%", opacity: 0.25 }}
        viewBox="0 0 1920 1080">
        <defs>
          <pattern id="grid" width="80" height="80" patternUnits="userSpaceOnUse">
            <path d="M 80 0 L 0 0 0 80" fill="none" stroke="#00FFD1" strokeWidth="0.5" />
          </pattern>
        </defs>
        <rect width="100%" height="100%" fill="url(#grid)" />
      </svg>
      <div style={{
        position: "absolute", inset: 0,
        background: "radial-gradient(ellipse at center, transparent 40%, rgba(3,10,15,0.85) 100%)"
      }} />
    </div>
  );
};
Spring-entrance card
tsxconst Card: React.FC<{ delay?: number; children: React.ReactNode }> = ({ delay = 0, children }) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();
  const scale = spring({ frame: frame - delay, fps, config: { stiffness: 350, damping: 25 } });
  const opacity = interpolate(frame - delay, [0, 12], [0, 1], {
    extrapolateLeft: "clamp", extrapolateRight: "clamp"
  });
  return (
    <div style={{ transform: `scale(${scale})`, opacity, background: "rgba(0,10,20,0.85)",
      border: "1px solid #00FFD1", borderRadius: 16, padding: "32px 40px" }}>
      {children}
    </div>
  );
};
Staggered text reveal (character by character)
tsxconst TextReveal: React.FC<{ text: string; charDelay?: number }> = ({ text, charDelay = 2 }) => {
  const frame = useCurrentFrame();
  return (
    <div style={{ display: "flex", flexWrap: "wrap" }}>
      {text.split("").map((char, i) => {
        const f = frame - i * charDelay;
        return (
          <span key={i} style={{
            opacity: interpolate(f, [0, 8], [0, 1], { extrapolateLeft: "clamp", extrapolateRight: "clamp" }),
            transform: `translateY(${interpolate(f, [0, 8], [20, 0], { extrapolateLeft: "clamp", extrapolateRight: "clamp" })}px)`,
            fontSize: 64, fontWeight: 800, color: "#fff",
          }}>
            {char === " " ? "\u00A0" : char}
          </span>
        );
      })}
    </div>
  );
};
Clippath wipe transition
tsxconst WipeTransition: React.FC<{ durationFrames?: number; color?: string }> = ({
  durationFrames = 20, color = "#00FFD1"
}) => {
  const frame = useCurrentFrame();
  const progress = interpolate(frame, [0, durationFrames], [0, 100], {
    extrapolateLeft: "clamp", extrapolateRight: "clamp"
  });
  return (
    <div style={{
      position: "absolute", inset: 0, background: color,
      clipPath: `inset(0 ${100 - progress}% 0 0)`,
      opacity: 0.12, pointerEvents: "none",
    }} />
  );
};

Common Aspect Ratios
FormatDimensionsYouTube / 16:91920×1080TikTok / Reels / Shorts (9:16)1080×1920Instagram Feed (4:5)1080×1350Square1080×1080

Quality Checklist (verify before packaging)

 npm run dev boots without TypeScript errors and shows "Built in Xms"
 Mute test — does the story read visually without sound?
 Squint test — is text hierarchy visible at a glance?
 Slideshow test — is there always something in motion on screen?
 Timing test — spring motion feels organic, not robotic?
 No emoji anywhere — only Lucide React icons
 All interpolate calls have extrapolateLeft/Right: "clamp"
 Persistent elements (background, ambient shapes) are OUTSIDE <Sequence> blocks


Delivery Instructions to User (always include)
After calling present_files, always tell the user:
Extract and run:
  tar -xzf <project>.tar.gz
  cd <project>
  npm install
  npm run dev         ← preview at localhost:3000 in Remotion Studio
  npx remotion render <CompositionId> out/video.mp4   ← export MP4
Rendering requires internet access to download Chrome Headless Shell (~150MB, one-time).
On Windows use: npx remotion render <CompositionId> out\video.mp4

Key Remotion APIs Reference
tsximport {
  AbsoluteFill,      // position:absolute, full frame container
  Sequence,          // time-offset children; frame resets to 0 inside
  useCurrentFrame,   // current frame number (relative inside Sequence)
  useVideoConfig,    // { fps, width, height, durationInFrames }
  interpolate,       // map frame range to value range
  spring,            // physics-based spring animation
  Img,               // preloading-aware image component
  Audio,             // audio component
  staticFile,        // reference files in /public
} from "remotion";

scripts/firecrawl.sh
bash#!/usr/bin/env bash
set -euo pipefail
SCRIPT_DIR="$(cd "$(dirname "$0")" && pwd)"
WORKSPACE_DIR="$(dirname "$(dirname "$SCRIPT_DIR")")"
if [ -f "$WORKSPACE_DIR/.env" ]; then set -a; source "$WORKSPACE_DIR/.env"; set +a; fi
URL="${1:?Usage: firecrawl.sh <url>}"
if [ -z "${FIRECRAWL_API_KEY:-}" ]; then echo "Error: FIRECRAWL_API_KEY not set" >&2; exit 1; fi
curl -s -X POST 'https://api.firecrawl.dev/v1/scrape' \
  -H 'Content-Type: application/json' \
  -H "Authorization: Bearer ${FIRECRAWL_API_KEY}" \
  -d "$(cat <<EOF
{
  "url": "$URL",
  "formats": ["markdown", "extract", "screenshot"],
  "extract": {
    "schema": {
      "type": "object",
      "properties": {
        "brandName": {"type": "string"},
        "tagline": {"type": "string"},
        "headline": {"type": "string"},
        "description": {"type": "string"},
        "features": {"type": "array", "items": {"type": "string"}},
        "logoUrl": {"type": "string"},
        "faviconUrl": {"type": "string"},
        "primaryColors": {"type": "array", "items": {"type": "string"}},
        "ctaText": {"type": "string"},
        "socialLinks": {"type": "object"}
      }
    }
  }
}
EOF
)"
