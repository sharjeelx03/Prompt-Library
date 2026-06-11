# Product Photography Template

**A professional, end-to-end prompt framework for AI-generated product photography — built for commercial output.**

<br/>

[![Version](https://img.shields.io/badge/version-4.0.0-6c63ff?style=flat-square)](.)

<br/>

<div align="center">

<img src="assets/pr1.png" alt="Product Photography Template" width="100%" />

<br/>

[**Overview**](#overview) · [**Supported Platforms**](#supported-platforms) · [**Template**](#template) · [**Field Guide**](#field-guide) · [**Master Prompt**](#final-master-prompt) · [**Quality Standards**](#quality-standards)

</div>

---

## Overview

This template gives you a complete, structured brief for generating commercial-grade product photography using AI image generators. It covers everything from product identity and creative direction to lighting setup, camera settings, material rendering, and a final master prompt — the same way a professional studio brief would.

Designed for e-commerce listings, campaign assets, launch visuals, social ads, and print — at agency quality.

---

## Supported Platforms

| Platform | Strength |
|---|---|
| **GPT Image** | Consistent product accuracy |
| **Midjourney** | Luxury and editorial aesthetics |
| **FLUX** | Photorealistic rendering |
| **SDXL** | Fine-tuned commercial workflows |
| **Ideogram** | Typography and label integration |
| **Leonardo AI** | Rapid concept iteration |
| **Adobe Firefly** | Brand-safe, commercially licensed output |

---

## Photography Styles

`Hero Product Shot` · `Luxury Advertising` · `Commercial Advertising` · `E-Commerce` · `Editorial` · `Lifestyle` · `Flat Lay` · `Studio` · `Macro` · `Campaign` · `Product Launch` · `Billboard Advertisement`

---

## Reference Image Rules

When using reference images, this template enforces strict product fidelity:

**Always Preserve**
- Product shape, proportions, and dimensions
- Materials, textures, and surface finishes
- Colors, branding, logos, and labels
- Construction details and product geometry

**Reference Priority Order**
1. Product accuracy — from primary reference
2. Materials and textures — from primary reference
3. Composition — from secondary reference
4. Lighting — from secondary reference
5. Creative direction — from prompt

**Never Modify**
- Product silhouette or proportions
- Brand identity or logo placement
- Product geometry or colors (unless explicitly specified)

---

## Template

### Product Information

```text
PRODUCT_NAME:
PRODUCT_CATEGORY:
BRAND_NAME:
PRODUCT_SERIES:
PRODUCT_DESCRIPTION:
TARGET_AUDIENCE:

PRICE_POSITIONING:
[ ] Budget  [ ] Mid-range  [ ] Premium  [ ] Luxury  [ ] Ultra Luxury

KEY_SELLING_POINTS:
-
-
-

UNIQUE_FEATURES:
-
-
-

PRODUCT_MATERIALS:
-
-

PRODUCT_FINISH:
-
-

PRIMARY_COLORS:
SECONDARY_COLORS:
ACCENT_COLORS:
```

### Creative Direction

```text
PHOTOGRAPHY_STYLE:
COMMERCIAL_PURPOSE:
VISUAL_THEME:
BRAND_PERSONALITY:
MOOD:
ATMOSPHERE:
EMOTIONAL_RESPONSE:
```

### Environment & Scene

```text
BACKGROUND_TYPE:
BACKGROUND_DESCRIPTION:
BACKGROUND_COLORS:
SURFACE_TYPE:
SURFACE_DESCRIPTION:
ENVIRONMENT_STYLE:
SCENE_DESCRIPTION:

SUPPORTING_ELEMENTS:
-
-

PROPS:
-
-

ENVIRONMENTAL_EFFECTS:
[ ] Fog  [ ] Mist  [ ] Steam  [ ] Water Splash  [ ] Dust Particles
[ ] Floating Elements  [ ] Smoke  [ ] Rain  [ ] Snow  [ ] None
```

### Product Placement

```text
PRODUCT_ORIENTATION:
[ ] Front View  [ ] Three Quarter View  [ ] Side View
[ ] Top View  [ ] Floating  [ ] Tilted  [ ] Exploded View

FRAME_POSITION:
[ ] Center  [ ] Left Third  [ ] Right Third  [ ] Upper Third  [ ] Lower Third

ARRANGEMENT_STYLE:
[ ] Solo Product  [ ] Collection  [ ] Family  [ ] Bundle  [ ] Ecosystem

DISPLAY_STYLE:
[ ] Symmetrical  [ ] Minimal  [ ] Dynamic  [ ] Editorial  [ ] Luxury  [ ] Technical

PRODUCT_ELEVATION:
[ ] Surface  [ ] Acrylic Stand  [ ] Marble Plinth  [ ] Floating  [ ] Suspended

NEGATIVE_SPACE_USAGE:
HERO_PRIORITY:
```

### Lighting

```text
PRIMARY_LIGHT_SOURCE:
[ ] Softbox  [ ] Octabox  [ ] Strip Light  [ ] Beauty Dish
[ ] Window Light  [ ] Fresnel  [ ] Natural Daylight  [ ] Custom

PRIMARY_LIGHT_POSITION:
SECONDARY_LIGHT_SOURCE:
RIM_LIGHTING:
ACCENT_LIGHTING:

LIGHTING_STYLE:
[ ] High Key  [ ] Low Key  [ ] Medium Contrast  [ ] Soft Diffused
[ ] Cinematic  [ ] Dramatic  [ ] Luxury  [ ] Editorial

LIGHTING_CONTRAST:

SHADOW_STYLE:
[ ] Soft Shadow  [ ] Hard Shadow  [ ] Contact Shadow
[ ] Floating Shadow  [ ] Long Shadow

COLOR_TEMPERATURE:
REFLECTION_CONTROL:
SPECIAL_LIGHTING_NOTES:
```

### Camera Settings

```text
CAMERA_BODY:
LENS_TYPE:
FOCAL_LENGTH:

CAMERA_ANGLE:
[ ] Eye Level  [ ] High Angle  [ ] Low Angle  [ ] Overhead  [ ] Three Quarter

CAMERA_DISTANCE:
DEPTH_OF_FIELD:
FOCUS_POINT:
PERSPECTIVE_STYLE:

ASPECT_RATIO:
[ ] 1:1  [ ] 4:5  [ ] 3:2  [ ] 16:9  [ ] 9:16

ORIENTATION:
[ ] Portrait  [ ] Landscape  [ ] Square
```

### Composition

```text
COMPOSITION_STRATEGY:
[ ] Rule of Thirds  [ ] Golden Ratio  [ ] Symmetrical
[ ] Diagonal  [ ] Layered  [ ] Minimalist  [ ] Editorial

VISUAL_FLOW:
FOCAL_HIERARCHY:
BALANCE_STYLE:
COPY_SPACE:
LOGO_SPACE:
CTA_SPACE:
```

### Material Rendering

```text
GLASS_RENDERING:
METAL_RENDERING:
PLASTIC_RENDERING:
FABRIC_RENDERING:
LEATHER_RENDERING:
WOOD_RENDERING:
CERAMIC_RENDERING:
LIQUID_RENDERING:
SPECIAL_MATERIAL_INSTRUCTIONS:
```

### Color & Branding

```text
PRIMARY_COLOR_PALETTE:
SECONDARY_COLOR_PALETTE:
ACCENT_COLORS:
COLOR_HARMONY:
COLOR_PSYCHOLOGY:
BRAND_COLOR_RULES:

POST_PROCESSING_STYLE:
[ ] Natural  [ ] Luxury  [ ] Cinematic  [ ] Editorial
[ ] Commercial  [ ] Vibrant  [ ] Desaturated

COLOR_GRADING:
```

### Platform Parameters

```text
MIDJOURNEY_PARAMETERS:
FLUX_PARAMETERS:
GPT_IMAGE_PARAMETERS:
SDXL_PARAMETERS:
LEONARDO_PARAMETERS:
IDEOGRAM_PARAMETERS:
```

### Video Extension *(Optional)*

```text
VIDEO_TYPE:
VIDEO_DURATION:

CAMERA_MOVEMENT:
[ ] Orbit  [ ] Push In  [ ] Pull Out  [ ] Dolly
[ ] Crane  [ ] Tracking  [ ] Product Spin

PRODUCT_MOVEMENT:
SPECIAL_EFFECTS:

TARGET_PLATFORM:
[ ] TikTok  [ ] Instagram Reels  [ ] YouTube Shorts
[ ] Website Hero  [ ] Advertisement
```

---

## Negative Prompt

Apply this to every generation to eliminate common AI artifacts:

```text
no low quality, no blurry details, no out of focus objects, no pixelation,
no distortion, no warped geometry, no incorrect proportions, no incorrect materials,
no poor reflections, no bad lighting, no unrealistic shadows, no color shifting,
no oversaturation, no undersaturation, no duplicate objects, no floating artifacts,
no AI artifacts, no rendering errors, no watermark, no text overlay,
no missing product parts, no cluttered composition, no amateur photography
```

---

## Final Master Prompt

Once all sections are filled, assemble your final prompt using this structure:

```text
Commercial product photography featuring [PRODUCT_NAME], using [PRIMARY_REFERENCE_IMAGE]
as the primary product reference and [SECONDARY_REFERENCE_IMAGE] as the secondary style reference.

Preserve the exact product shape, proportions, materials, colors, textures, branding,
logo placement, and visual identity from the reference images.

Hero subject: [PRODUCT_DESCRIPTION].
Photography style: [PHOTOGRAPHY_STYLE].
Commercial purpose: [COMMERCIAL_PURPOSE].
Visual theme: [VISUAL_THEME].
Brand personality: [BRAND_PERSONALITY].
Mood: [MOOD].
Atmosphere: [ATMOSPHERE].
Environment: [SCENE_DESCRIPTION].
Surface: [SURFACE_TYPE].
Lighting: [PRIMARY_LIGHT_SOURCE], [LIGHTING_STYLE], [COLOR_TEMPERATURE].
Camera: [LENS_TYPE], [FOCAL_LENGTH], [CAMERA_ANGLE].
Composition: [COMPOSITION_STRATEGY].

Materials rendered with physically accurate behavior, realistic reflections, realistic shadows,
realistic refractions, premium textures, studio-grade lighting, commercial retouching quality,
luxury advertising aesthetics, photorealistic rendering, ultra-detailed surfaces,
premium branding, masterpiece quality, advertising agency quality,
award-winning commercial photography, sharp focus, HDR, 8K.
```

---

## Quality Standards

| Tier | Description |
|---|---|
| **Commercial** | Standard e-commerce and catalog output |
| **Premium Commercial** | High-end retail and brand advertising |
| **Luxury Commercial** | Fashion and premium lifestyle campaigns |
| **Agency Grade** | Full creative agency execution |
| **Global Campaign Grade** | Broadcast, print, and OOH advertising |

**Built-in quality signals applied to every output:**
advertising agency quality · professional studio photography · premium commercial execution · accurate reflections · realistic materials and shadows · brand consistency · commercial retouching quality · ultra-detailed surfaces · sharp focus · HDR · 8K

---

## Contribution Checklist

Before submitting a new product shoot:

- [ ] Product reference images are included in `assets/`
- [ ] All required fields are completed
- [ ] Final master prompt is assembled and tested
- [ ] Output image is included and stored in `assets/`
- [ ] Negative prompt applied and verified
- [ ] Filename follows `##-product-name.md` convention
- [ ] Markdown renders correctly on GitHub

---

## License

**MIT** — Free to use, modify, and distribute with attribution.

---

<div align="center">

<img src="assets/pr2.png" alt="Product Photography Example" width="80%" />

<br/><br/>

*Built for creators who need commercial-grade output, not just pretty pictures.*

</div>