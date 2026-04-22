---
name: governance-pm-slide-deck
description: "Create polished, on-brand executive slide decks in Python-pptx for Snowflake Data & AI Governance. Use when: building a customer deck, QBR presentation, roadmap slide, executive briefing, or any data-backed PowerPoint. Triggers: create a deck, build a slide, make a presentation, create slides, build a pptx, customer deck, executive deck, roadmap deck, QBR deck, pitch deck, slide deck."
---

# Governance PM Slide Deck Skill

Generates polished, Snowflake-branded PPTX files using `python-pptx` + `matplotlib`.
Encodes the EXACT design system, color palette, geometry, and structural patterns
derived from the Envision Healthcare CEC deck (April 2026) and internal exec decks.

---

## Two Deck Modes

This skill covers two distinct visual styles. Choose before you start.

| Mode | Use when | Header style | Background |
|------|----------|-------------|------------|
| **Customer deck** | External meeting, CEC, customer EBC | Left blue stripe + light `#F0F7FD` panel | White slide + light panel |
| **Internal exec deck** | QBR, internal metrics, leadership review | Heavy navy top bar + white text | White slide + navy bar |

The customer deck mode is the one your team consistently calls out as looking better
for external audiences. The patterns below cover BOTH, clearly labeled.

---

## What Is Working Well (and Why)

These are the design decisions most frequently praised — and most often missed when
team members try to replicate the deck:

### 1. LEFT Vertical Stripe (Customer Mode) — Not a Top Bar
The very first shape on every slide is a thin `#29B5E8` vertical stripe on the left
edge (0.12" on the title slide, 0.08" on content slides), running full height.
Combined with the `#F0F7FD` (barely-blue white) header panel, this creates a
clean, airy look. PMs trying to replicate the deck use a top bar (wrong) and the
whole visual system falls apart.

### 2. Extended Color Palette — Section Colors as a System
Each section of the deck owns a color. The color appears on the section number badge,
the left accent bar, the section header background, and any callout in that section.
This cross-slide color continuity is why the deck reads as a *designed system* rather
than individual slides:
- `#29B5E8` — Data Quality / Snowflake blue
- `#11567F` — Overview / dark teal-blue
- `#00C8A0` — Observability / bright teal
- `#FF7A00` — RCA / orange
- `#6B48FF` — AI / Cortex Code / purple
- `#0C3D5E` — Deepest navy for "what makes it different" boxes

### 3. Cortex Code Callout on Every Content Slide
Every product slide ends with a purple callout box (`#F3F0FF` background, `#6B48FF`
header strip) containing a ❄ prompt that a user could type RIGHT NOW.
This converts a feature-description slide into an *activation moment*. Without this,
the deck is informational. With it, the deck is a sales tool.

### 4. Opening Questions Before Any Product Content
Slide 3 (before any product is shown) asks 4 industry-specific discovery questions.
Each question has a colored left bar matching the section it maps to. This personalizes
the conversation and makes the product slides land in the customer's own context.
Most PMs skip this or put it at the end. Putting it second — before Horizon — is the
structural move that makes the deck feel like a conversation, not a presentation.

### 5. Industry Scenario Box Before Technical Walkthroughs
On deep-dive slides, a `#FF7A00` orange callout box anchors the content to a specific
real scenario (e.g., "A physician productivity dashboard shows a 40% drop in ED
encounters. Is this a real clinical trend — or a data pipeline failure?").
The technical steps that follow are now solving *their problem*, not demonstrating
*your product*. This is the single biggest driver of "this felt relevant to us."

### 6. Capability Tile Grid (Horizon Overview Slide)
Six equal-width tiles in a horizontal row: colored header strip + near-white body.
Compact, scannable, and no wasted space. PMs tend to use a 3×2 grid or bullets.
The single horizontal row with the `#FAFCFF` body makes the capabilities feel
co-equal and integrated, which reinforces the "one platform" message.

### 7. "Without X" Dark Navy Contrast Box
A `#0C3D5E` box near the bottom of the observability slide states the cost of NOT
having the capability ("Manual triage → 4–8 hours of engineer time → stakeholders
already angry"). This negative contrast makes the positive case feel credible and
earned, not just promotional.

### 8. Maturity Journey as Forward Motion, Not a Status Report
Four stages in a left-to-right progression (Foundation → Protection → Observability
→ AI-Ready), each with a Cortex Code prompt at the bottom. The customer can self-locate
("we're at Stage 2") and immediately see what's next. This turns a feature overview
into a roadmap conversation.

---

## Color Palettes

### Customer Deck Palette (use this for external-facing decks)

```python
from pptx.dml.color import RGBColor

# Primary section colors — each section owns one
SNOW_BLUE   = RGBColor(0x29, 0xB5, 0xE8)  # Data Quality, left stripe, badges
DARK_BLUE   = RGBColor(0x11, 0x56, 0x7F)  # Overview section
TEAL        = RGBColor(0x00, 0xC8, 0xA0)  # Observability, Classification
ORANGE      = RGBColor(0xFF, 0x7A, 0x00)  # RCA, scenario callout boxes
PURPLE      = RGBColor(0x6B, 0x48, 0xFF)  # AI / Cortex Code
DEEP_NAVY   = RGBColor(0x0C, 0x3D, 0x5E)  # "What makes it different" boxes
DARK_GREEN  = RGBColor(0x0A, 0x5C, 0x3A)  # Step 4 / success / "Fix & verify"

# Background tints — section-matched
BG_MAIN     = RGBColor(0xF0, 0xF7, 0xFD)  # Header panel, footer, card bg (light blue-white)
BG_ALT      = RGBColor(0xFA, 0xFC, 0xFF)  # Alternating card bg (near-white)
BG_PURPLE   = RGBColor(0xF3, 0xF0, 0xFF)  # Cortex Code callout bg (light purple)
BG_BLUE     = RGBColor(0xD0, 0xE6, 0xF5)  # DMF feature list bg (mid blue tint)
BG_GREEN    = RGBColor(0xEA, 0xF7, 0xF1)  # Industry examples bg (light green tint)
BG_STAGE    = RGBColor(0xE8, 0xF0, 0xF8)  # Maturity stage sub-header bg
WHITE       = RGBColor(0xFF, 0xFF, 0xFF)
```

### Internal Exec Deck Palette (QBR, metrics, leadership)

```python
NAVY    = RGBColor(0x1A, 0x3F, 0x6F)  # Top bar, title slides
BLUE    = RGBColor(0x29, 0xB5, 0xE8)  # Accent lines, badges
TEAL    = RGBColor(0x00, 0xB4, 0xD8)  # KPI card borders
GREEN   = RGBColor(0x2D, 0xC5, 0x6E)  # Growth, positive metrics
ORANGE  = RGBColor(0xF6, 0x82, 0x1F)  # Accent, warnings
LGREY   = RGBColor(0xF3, 0xF4, 0xF6)  # Card backgrounds, footer
GREY    = RGBColor(0x6B, 0x72, 0x80)  # Secondary text
DKGREY  = RGBColor(0x37, 0x41, 0x51)  # Body text
WHITE   = RGBColor(0xFF, 0xFF, 0xFF)
```

---

## Slide Dimensions

```python
from pptx import Presentation
from pptx.util import Inches

prs = Presentation()
prs.slide_width  = Inches(13.33)
prs.slide_height = Inches(7.5)
BLANK = prs.slide_layouts[6]   # Always use blank layout — no default placeholders
```

---

## Core Helpers

```python
from pptx.enum.text import PP_ALIGN
from pptx.util import Inches, Pt

def add_rect(slide, x, y, w, h, fill=None, line_color=None):
    shape = slide.shapes.add_shape(1, Inches(x), Inches(y), Inches(w), Inches(h))
    shape.line.fill.background()
    if fill:
        shape.fill.solid()
        shape.fill.fore_color.rgb = fill
    else:
        shape.fill.background()
    if line_color:
        shape.line.color.rgb = line_color
        shape.line.width = Pt(1)
    return shape

def add_text(slide, text, x, y, w, h, size=14, bold=False, color=None,
             align=PP_ALIGN.LEFT, italic=False):
    tb = slide.shapes.add_textbox(Inches(x), Inches(y), Inches(w), Inches(h))
    tf = tb.text_frame
    tf.word_wrap = True
    p = tf.paragraphs[0]
    p.alignment = align
    r = p.add_run()
    r.text = text
    r.font.size = Pt(size)
    r.font.bold = bold
    r.font.italic = italic
    r.font.color.rgb = color or RGBColor(0x33, 0x33, 0x33)
    return tb

def add_image(slide, buf, x, y, w, h):
    buf.seek(0)
    slide.shapes.add_picture(buf, Inches(x), Inches(y), Inches(w), Inches(h))

def fig_buf(fig, dpi=150):
    import io
    buf = io.BytesIO()
    fig.savefig(buf, format="png", dpi=dpi, bbox_inches="tight",
                facecolor=fig.get_facecolor())
    buf.seek(0)
    return buf
```

---

## CUSTOMER DECK Templates

### Title Slide (customer mode)

Geometry derived precisely from Envision Healthcare CEC deck:

```python
s = prs.slides.add_slide(BLANK)

# White background
add_rect(s, 0, 0, 13.33, 7.5, fill=WHITE)

# LEFT vertical blue stripe (0.12" wide, full height) — most important element
add_rect(s, 0, 0, 0.12, 7.5, fill=SNOW_BLUE)

# Thin top horizontal blue line
add_rect(s, 0.12, 0, 13.21, 0.08, fill=SNOW_BLUE)

# ❄ icon + "Snowflake" wordmark at top-left
add_text(s, "❄", 0.5, 0.3, 0.9, 0.8, size=28, color=SNOW_BLUE)
add_text(s, "Snowflake", 1.35, 0.43, 3.0, 0.5, size=18, bold=False,
         color=RGBColor(0x33, 0x33, 0x33))

# Main title (large, bold, dark)
add_text(s, "Snowflake Horizon", 1.0, 1.7, 11.2, 1.0,
         size=40, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))

# Subtitle
add_text(s, "Data Governance, Quality & Privacy", 1.0, 2.72, 11.2, 0.65,
         size=22, color=RGBColor(0x44, 0x55, 0x66))

# Short teal accent line (partial width, not full) beneath subtitle
add_rect(s, 2.5, 3.48, 8.3, 0.05, fill=TEAL)

# Event / meta info
add_text(s, "Customer Engineering Center  |  Menlo Park  |  April 2026",
         1.0, 3.65, 11.2, 0.5, size=14, color=RGBColor(0x55, 0x66, 0x77))
add_text(s, "Raja Balakrishnan  —  Sr. Manager, Product Management, Snowflake",
         1.0, 4.15, 11.2, 0.45, size=13, color=RGBColor(0x55, 0x66, 0x77))

# Bottom tagline panel (F0F7FD — light blue-white)
add_rect(s, 0.12, 5.9, 13.21, 1.6, fill=BG_MAIN)
add_text(s, "One platform. Governed by default.",
         1.0, 6.15, 11.2, 0.5, size=18, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))
add_text(s, "Classification  •  Data Quality  •  Privacy  •  Tagging  •  Lineage",
         1.0, 6.65, 11.2, 0.4, size=13, color=RGBColor(0x44, 0x55, 0x66))
```

### Content Slide Header (customer mode) — use on every non-title slide

```python
def customer_slide_header(slide, title, subtitle=None):
    # White full background
    add_rect(slide, 0, 0, 13.33, 7.5, fill=WHITE)
    # LEFT vertical blue stripe (0.08" wide)
    add_rect(slide, 0, 0, 0.08, 7.5, fill=SNOW_BLUE)
    # Light blue-white header panel (0.08" to 13.33", top 1.1")
    add_rect(slide, 0.08, 0, 13.25, 1.1, fill=BG_MAIN)
    # Title text (dark, not reversed)
    add_text(slide, title, 0.35, 0.10, 10.0, 0.62,
             size=26, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))
    if subtitle:
        add_text(slide, subtitle, 0.35, 0.65, 12.0, 0.38,
                 size=13, color=RGBColor(0x44, 0x55, 0x66))

def customer_slide_footer(slide, text="Snowflake Confidential  |  April 2026"):
    # Light blue-white footer band
    add_rect(slide, 0.08, 7.3, 13.25, 0.2, fill=BG_MAIN)
    add_text(slide, text, 0.35, 7.31, 12.5, 0.18,
             size=8, color=RGBColor(0x77, 0x88, 0x99), italic=True)
```

### Agenda Slide (numbered sections with color badges)

Each row: left accent bar (0.08" wide) + content rect + colored number badge (0.5"×0.5") + title + subtitle.
Alternates between `BG_MAIN` (#F0F7FD) and `BG_ALT` (#FAFCFF) backgrounds.

```python
# section_colors maps each section number to its color
section_colors = {
    1: SNOW_BLUE,   # Opening Questions
    2: DARK_BLUE,   # Horizon Overview
    3: TEAL,        # Data Quality
    4: ORANGE,      # Observability/RCA
    5: SNOW_BLUE,   # Classification & Privacy
    6: PURPLE,      # Cortex Code / AI
    7: DEEP_NAVY,   # Maturity / Next Steps
}
agenda_items = [
    (1, "Opening Questions",          "What matters most to your team right now?"),
    (2, "Snowflake Horizon — Overview","One platform for all governance needs"),
    (3, "Data Quality & Observability","Automated monitoring, scoring & anomaly alerting"),
    (4, "Data Observability: RCA",    "Find the root cause fast; know what breaks before it does"),
    (5, "Data Classification & Privacy","Auto-detect sensitive data; enforce privacy policies"),
    (6, "Governed by AI — Cortex Code","Natural language governance: ask instead of code"),
    (7, "Maturity Journey & Next Steps","Where to start and how to grow"),
]
row_h, row_start = 0.78, 1.12
alt_bgs = [BG_MAIN, BG_ALT]  # alternating
for i, (num, title, subtitle) in enumerate(agenda_items):
    col = section_colors[num]
    bg  = alt_bgs[i % 2]
    y = row_start + i * (row_h + 0.02)
    # Left color accent bar
    add_rect(s, 0.35, y, 0.08, row_h, fill=col)
    # Row background
    add_rect(s, 0.43, y, 12.52, row_h, fill=bg)
    # Colored number badge
    add_rect(s, 0.55, y + 0.14, 0.50, 0.50, fill=col)
    add_text(s, str(num), 0.55, y + 0.14, 0.50, 0.50,
             size=16, bold=True, color=WHITE, align=PP_ALIGN.CENTER)
    # Title and subtitle
    add_text(s, title,    1.18, y + 0.10, 5.5, 0.38, size=16, bold=True,
             color=RGBColor(0x1A, 0x2E, 0x44))
    add_text(s, subtitle, 1.18, y + 0.46, 11.5, 0.28, size=11,
             color=RGBColor(0x55, 0x66, 0x77))
```

### Opening Questions Slide (discovery before product)

```python
# Personalize the 4 questions to the customer's industry before building the deck.
questions = [
    (SNOW_BLUE, "Platform Vision",
     "As you think about your data platform over the next few years — what capabilities are most critical to unlock?"),
    (DARK_BLUE, "Data Quality & Trust",
     "How confident is your organization today in the quality of data used in dashboards and analytical models?"),
    (TEAL, "Sensitive Data & Compliance",
     "How are you currently identifying and protecting sensitive data across your schemas?"),
    (PURPLE, "AI & Conversational Analytics",
     "What's the #1 use case you'd want to enable first if governance were fully in place?"),
]
qy, qh = 1.35, 1.25
for i, (col, qtitle, qtext) in enumerate(questions):
    qx = 0.4 if i % 2 == 0 else 6.8
    if i == 2: qy += qh + 0.15   # row 2
    qxi = qx
    add_rect(s, qxi, qy, 0.08, qh, fill=col)
    add_rect(s, qxi + 0.08, qy, 5.9, qh, fill=BG_MAIN)
    add_text(s, qtitle, qxi + 0.18, qy + 0.1, 5.5, 0.35,
             size=13, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))
    add_text(s, qtext, qxi + 0.18, qy + 0.45, 5.5, 0.7,
             size=11, color=RGBColor(0x33, 0x44, 0x55))
```

### Cortex Code Callout Box (end of every content slide)

```python
def cortex_code_callout(slide, section_label, prompt_text, y=6.1, w=12.5):
    """Purple callout that ends every content slide with an actionable prompt."""
    x = 0.4
    # Light purple background
    add_rect(slide, x, y, w, 1.15, fill=BG_PURPLE)
    # Purple header strip
    add_rect(slide, x, y, w, 0.33, fill=PURPLE)
    add_text(slide, f"❄ {section_label}", x + 0.12, y + 0.04, w - 0.3, 0.26,
             size=12, bold=True, color=WHITE)
    # Prompt text
    add_text(slide, prompt_text, x + 0.12, y + 0.38, w - 0.25, 0.7,
             size=11, color=RGBColor(0x22, 0x22, 0x44), italic=True)
```

### Scenario Callout Box (anchor deep-dive slides)

```python
def scenario_box(slide, scenario_text, y=1.35):
    """Orange scenario box — places the customer's problem before the technical solution."""
    add_rect(slide, 0.4, y, 12.5, 0.72, fill=ORANGE)
    add_text(slide, "Scenario:", 0.55, y + 0.06, 1.5, 0.28,
             size=12, bold=True, color=WHITE)
    add_text(slide, scenario_text, 2.1, y + 0.06, 10.6, 0.6,
             size=11, color=WHITE)
```

### "Without X" Contrast Box

```python
def without_box(slide, contrast_text, y=5.55):
    """Dark navy box showing the cost of NOT having the capability."""
    add_rect(slide, 0.4, y, 12.5, 0.6, fill=DEEP_NAVY)
    add_text(slide, contrast_text, 0.55, y + 0.1, 12.1, 0.45,
             size=11, color=WHITE, bold=False)
```

### Capability Tile Grid (Horizon Overview slide)

```python
# 6 equal-width tiles in a single horizontal row
# tile_color = section color, tile_label = capability name, tile_body = 2-3 lines
tiles = [
    (SNOW_BLUE, "Data Quality",     "Automated metric\nfunctions, quality\nscoring, SLA alerts"),
    (TEAL,      "Classification",   "Auto-detect PHI/PII\nacross every column\nin every schema"),
    (ORANGE,    "Privacy",          "Dynamic masking,\ndifferential privacy,\nrow access policies"),
    (DARK_BLUE, "Tagging & Lineage","Tag propagation,\ncolumn-level lineage,\npolicy enforcement"),
    (PURPLE,    "AI Governance",    "Govern AI inputs &\noutputs; protect data\nin Cortex workflows"),
    (DEEP_NAVY, "Cortex Code",      "Natural language\ngovernance: ask\ninstead of SQL"),
]
tile_w = 2.02
tx = 0.4
ty = 2.1
tile_h = 2.5
for col, label, body in tiles:
    add_rect(s, tx, ty, tile_w, 0.42, fill=col)
    add_text(s, label, tx + 0.08, ty + 0.05, tile_w - 0.15, 0.32,
             size=12, bold=True, color=WHITE)
    add_rect(s, tx, ty + 0.42, tile_w, tile_h - 0.42, fill=BG_ALT)
    add_text(s, body, tx + 0.1, ty + 0.52, tile_w - 0.18, tile_h - 0.55,
             size=10.5, color=RGBColor(0x22, 0x33, 0x44))
    tx += tile_w + 0.1
```

### Three-Column Feature Breakdown (classification, privacy slides)

```python
# Each column: colored header strip + near-white body with bullet points
cols = [
    (SNOW_BLUE, "Automatic Classification", [
        "• Scans every column across all tables",
        "• Identifies 50+ semantic categories: NAME, DOB, MRN, NPI, SSN",
        "• Assigns privacy categories automatically",
        "• Runs on schedule or triggered on demand",
    ]),
    (DARK_BLUE, "Custom Classifiers", [
        "• Build regex-based classifiers for org-specific fields",
        "• Facility codes, procedure IDs, internal reference numbers",
        "• Version-controlled and reusable across all schemas",
    ]),
    (TEAL, "Tag-Driven Policy Enforcement", [
        "• Classification automatically applies object tags (CONTAINS_PHI)",
        "• Masking policies bind to tags — not individual columns",
        "• New PHI column classified → masking applied automatically",
    ]),
]
col_w = 4.0
cx = 0.4
for col_color, col_title, bullets in cols:
    add_rect(s, cx, 2.1, col_w, 0.42, fill=col_color)
    add_text(s, col_title, cx + 0.1, 2.14, col_w - 0.18, 0.35,
             size=13, bold=True, color=WHITE)
    add_rect(s, cx, 2.52, col_w, 4.3, fill=BG_ALT)
    by = 2.65
    for b in bullets:
        add_text(s, b, cx + 0.12, by, col_w - 0.22, 0.55, size=11,
                 color=RGBColor(0x22, 0x33, 0x44))
        by += 0.6
    cx += col_w + 0.16
```

### Numbered Steps — Two Parallel Columns (RCA + Impact Analysis)

```python
# Used for side-by-side workflows (e.g., Root Cause vs Impact Analysis)
def numbered_steps_column(slide, header_color, header_label, steps, x, y, col_w=5.8):
    # Column header
    add_rect(slide, x, y, col_w, 0.42, fill=header_color)
    add_text(slide, header_label, x + 0.12, y + 0.06, col_w - 0.2, 0.32,
             size=14, bold=True, color=WHITE)
    step_colors = [SNOW_BLUE, DARK_BLUE, TEAL, DARK_GREEN]
    sy = y + 0.52
    for i, (step_title, step_desc) in enumerate(steps):
        col = step_colors[i % len(step_colors)]
        # Step number badge
        add_rect(slide, x + 0.1, sy, 0.38, 0.38, fill=col)
        add_text(slide, str(i + 1), x + 0.1, sy, 0.38, 0.38,
                 size=14, bold=True, color=WHITE, align=PP_ALIGN.CENTER)
        add_text(slide, step_title, x + 0.6, sy, col_w - 0.7, 0.28,
                 size=12, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))
        add_text(slide, step_desc, x + 0.6, sy + 0.3, col_w - 0.7, 0.38,
                 size=10, color=RGBColor(0x44, 0x55, 0x66))
        sy += 0.82

# Usage
numbered_steps_column(s, SNOW_BLUE, "Root Cause Analysis",
    [("DMF alert fires", "Freshness DMF detects table hasn't refreshed in 18 hours"),
     ("Lineage traces upstream", "Column lineage walks back to the failed source task"),
     ("Root cause identified", "Source task failed silently — no downstream alert existed"),
     ("Fix & verify", "Restart feed, re-run pipeline, confirm DMF returns to baseline")],
    x=0.4, y=2.15)

numbered_steps_column(s, TEAL, "Impact Analysis",
    [("Identify the source", "Before changing schema — ask: what depends on this?"),
     ("Lineage traces downstream", "Maps: table → views → Dynamic Tables → dashboards → AI model"),
     ("Scope the blast radius", "Understand which reports and stakeholders are affected"),
     ("Change with confidence", "Know exactly what to test, notify, and revalidate")],
    x=6.9, y=2.15)
```

### Maturity Journey Slide (4-stage progression)

```python
stages = [
    (SNOW_BLUE, "Stage 1\nFoundation", "Know what you have",
     ["• Activate classification across key schemas",
      "• Apply object tags to sensitive columns",
      "• Enable freshness & null-rate DMFs on critical tables"],
     "\"Classify my top 5 schemas and show me all PHI columns\""),
    (TEAL, "Stage 2\nProtection", "Protect what matters",
     ["• Apply dynamic masking to all classified PHI columns",
      "• Implement row access policies for role-based boundaries",
      "• Expand DMF coverage with custom quality rules"],
     "\"Create masking policies for all PHI columns in CLINICAL\""),
    (ORANGE, "Stage 3\nObservability", "Trust your pipelines",
     ["• Deploy anomaly detection for volume and freshness",
      "• Enable column-level lineage across all pipelines",
      "• Automate RCA workflows with lineage + quality context"],
     "\"What pipeline broke and why is my ED dashboard stale today?\""),
    (PURPLE, "Stage 4\nAI-Ready", "Govern AI, not just data",
     ["• Certify trusted data products for Cortex AI workloads",
      "• Govern AI agent inputs and outputs",
      "• Enable conversational analytics on governed semantic layer"],
     "\"Is my data ready for conversational analytics? What gaps remain?\""),
]
stage_w = 3.0
sx = 0.4
for col, stage_label, stage_sub, bullets, coco_prompt in stages:
    # Stage header
    add_rect(s, sx, 1.35, stage_w, 0.55, fill=col)
    add_text(s, stage_label, sx + 0.1, 1.38, stage_w - 0.18, 0.5,
             size=13, bold=True, color=WHITE)
    # Sub-header bg
    add_rect(s, sx, 1.9, stage_w, 0.38, fill=BG_STAGE)
    add_text(s, stage_sub, sx + 0.1, 1.93, stage_w - 0.18, 0.32,
             size=11, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))
    # Bullets
    add_rect(s, sx, 2.28, stage_w, 2.8, fill=BG_ALT)
    by = 2.38
    for b in bullets:
        add_text(s, b, sx + 0.1, by, stage_w - 0.18, 0.5, size=10,
                 color=RGBColor(0x22, 0x33, 0x44))
        by += 0.55
    # Cortex Code prompt
    add_rect(s, sx, 5.08, stage_w, 0.6, fill=BG_PURPLE)
    add_rect(s, sx, 5.08, stage_w, 0.22, fill=PURPLE)
    add_text(s, "❄", sx + 0.08, 5.1, 0.22, 0.18, size=10, color=WHITE)
    add_text(s, coco_prompt, sx + 0.08, 5.32, stage_w - 0.16, 0.32,
             size=9, color=RGBColor(0x22, 0x22, 0x44), italic=True)
    sx += stage_w + 0.24
```

### Next Steps Slide (with timing badge)

```python
next_steps = [
    (SNOW_BLUE, "1", "Horizon Assessment Workshop",
     "2-hour hands-on session — run DMFs, review auto-classification on your actual schemas. Output: governance gap analysis.",
     "⏱  Suggested within 2 weeks"),
    (TEAL, "2", "Proof of Concept",
     "Build a Cortex Analyst semantic view on your highest-priority use case. Start with governed, classified data.",
     "⏱  Suggested 3-week POC"),
    (ORANGE, "3", "Data Quality Pilot",
     "Activate schema-level DMF monitoring on your top critical tables. Establish baselines and alerting before next BI refresh.",
     "⏱  Quick win — start immediately"),
    (PURPLE, "4", "Governance Maturity Roadmap",
     "Co-create a phased roadmap aligned to your platform vision — mapping Horizon capabilities to your specific use cases.",
     "⏱  Workshop in 4–6 weeks"),
]
ny = 1.35
for col, num, title, body, timing in next_steps:
    # Left accent bar
    add_rect(s, 0.4, ny, 0.08, 1.25, fill=col)
    # Row background
    add_rect(s, 0.48, ny, 12.42, 1.25, fill=BG_MAIN)
    # Number badge
    add_rect(s, 0.58, ny + 0.12, 0.45, 0.45, fill=col)
    add_text(s, num, 0.58, ny + 0.12, 0.45, 0.45,
             size=15, bold=True, color=WHITE, align=PP_ALIGN.CENTER)
    # Title and body
    add_text(s, title, 1.18, ny + 0.08, 9.0, 0.38,
             size=14, bold=True, color=RGBColor(0x1A, 0x2E, 0x44))
    add_text(s, body, 1.18, ny + 0.46, 9.0, 0.55,
             size=11, color=RGBColor(0x33, 0x44, 0x55))
    # Timing badge (right side)
    add_rect(s, 10.3, ny + 0.25, 2.4, 0.38, fill=BG_STAGE)
    add_text(s, timing, 10.4, ny + 0.27, 2.2, 0.32,
             size=10, color=RGBColor(0x1A, 0x2E, 0x44), italic=True)
    ny += 1.38
```

---

## INTERNAL EXEC DECK Templates

### Title Slide (internal / dark mode)

```python
s = prs.slides.add_slide(BLANK)
add_rect(s, 0, 0, 13.33, 7.5, fill=NAVY)         # full navy background
add_rect(s, 0, 3.35, 13.33, 0.08, fill=BLUE)      # blue accent stripe at midpoint
add_text(s, "DECK TITLE", 1.0, 1.4, 11.33, 0.9,
         size=38, bold=True, color=WHITE, align=PP_ALIGN.LEFT)
add_text(s, "Subtitle or theme line", 1.0, 2.3, 11.33, 0.7,
         size=22, color=BLUE, align=PP_ALIGN.LEFT)
add_text(s, "Analysis Period: Q1 FY27", 1.0, 3.7, 11.33, 0.4, size=13, color=LGREY)
add_text(s, "Prepared by: Raja Balakrishnan | Data Governance PM", 1.0, 4.15, 11.33, 0.4,
         size=13, color=LGREY)
add_text(s, "CONFIDENTIAL", 1.0, 6.8, 4.0, 0.4, size=10, color=GREY, italic=True)
add_text(s, "April 2026", 10.5, 6.8, 2.5, 0.4, size=10, color=GREY, align=PP_ALIGN.RIGHT)
```

### Content Slide Header (internal mode)

```python
def internal_slide_header(slide, title, subtitle=None):
    add_rect(slide, 0, 0, 13.33, 1.15, fill=NAVY)
    add_rect(slide, 0, 1.15, 13.33, 0.06, fill=BLUE)
    add_text(slide, title, 0.4, 0.12, 11.5, 0.75,
             size=28, bold=True, color=WHITE, align=PP_ALIGN.LEFT)
    if subtitle:
        add_text(slide, subtitle, 0.4, 0.82, 11.5, 0.35,
                 size=12, color=BLUE, align=PP_ALIGN.LEFT)

def internal_slide_footer(slide, text="Snowflake Internal — Confidential | April 2026"):
    add_rect(slide, 0, 7.22, 13.33, 0.28, fill=LGREY)
    add_text(slide, text, 0.3, 7.24, 12.5, 0.22, size=7.5, color=GREY, italic=True)
```

### KPI Cards (internal mode)

```python
def kpi_card(slide, x, y, w, h, value, label, delta=None, val_color=None):
    add_rect(slide, x, y, w, h, fill=LGREY, line_color=TEAL)
    add_text(slide, value, x+0.08, y+0.08, w-0.16, h*0.52,
             size=30, bold=True, color=val_color or NAVY, align=PP_ALIGN.CENTER)
    add_text(slide, label, x+0.08, y+h*0.52, w-0.16, h*0.28,
             size=10, color=GREY, align=PP_ALIGN.CENTER)
    if delta:
        add_text(slide, delta, x+0.08, y+h*0.76, w-0.16, h*0.22,
                 size=10, bold=True, color=GREEN, align=PP_ALIGN.CENTER)
```

### Two-Run Bullet (internal mode)

```python
bullets = [
    ("Key metric:", "grew +73% — the strongest signal in the cohort."),
    ("Root cause:", "customers completing classification setup after CoCo guidance."),
]
y = 3.38
for bold_part, rest in bullets:
    tb = s.shapes.add_textbox(Inches(0.5), Inches(y), Inches(12.33), Inches(0.38))
    tf = tb.text_frame
    tf.word_wrap = True
    p = tf.paragraphs[0]
    r1 = p.add_run(); r1.text = "▸  " + bold_part + "  "
    r1.font.bold = True; r1.font.size = Pt(12); r1.font.color.rgb = NAVY
    r2 = p.add_run(); r2.text = rest
    r2.font.bold = False; r2.font.size = Pt(12); r2.font.color.rgb = DKGREY
    y += 0.52
```

### Closing Slide (internal mode — mirrors title with 3 KPIs)

```python
s = prs.slides.add_slide(BLANK)
add_rect(s, 0, 0, 13.33, 7.5, fill=NAVY)
add_rect(s, 0, 3.5, 13.33, 0.07, fill=BLUE)
add_text(s, "Headline that captures everything.", 1.0, 1.6, 11.33, 1.0,
         size=30, bold=True, color=WHITE, align=PP_ALIGN.CENTER)
add_text(s, "Supporting line connecting numbers to story.",
         1.5, 2.75, 10.33, 0.75, size=15, color=BLUE, align=PP_ALIGN.CENTER)
summary_kpis = [("+14.9%", "AUM Growth"), ("+73.4%", "DMF Growth"), ("+51.6%", "Data Security")]
skw, skx, sky = 3.5, 0.67, 4.2
for val, lbl in summary_kpis:
    add_rect(s, skx, sky, skw, 1.5, fill=RGBColor(0x0E, 0x2A, 0x4E), line_color=BLUE)
    add_text(s, val, skx+0.1, sky+0.1, skw-0.2, 0.8,
             size=32, bold=True, color=GREEN, align=PP_ALIGN.CENTER)
    add_text(s, lbl, skx+0.1, sky+0.85, skw-0.2, 0.55,
             size=10, color=BLUE, align=PP_ALIGN.CENTER)
    skx += skw + 0.24
```

---

## Matplotlib Chart Conventions

```python
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(6, 3.6), facecolor="white")

# Match chart colors to slide palette
ax.barh(labels, values, color="#29B5E8", alpha=0.88, height=0.45)

# Strip all non-essential spines
ax.spines[["top", "right", "left"]].set_visible(False)
ax.tick_params(left=False, bottom=False)
ax.xaxis.grid(True, linestyle="--", alpha=0.35)
ax.set_axisbelow(True)

# Always annotate the growth rate in bottom-right (boxed)
ax.text(0.98, 0.06, "+73.4% growth", transform=ax.transAxes, ha="right",
        fontsize=10, color="#2DC56E", fontweight="bold",
        bbox=dict(boxstyle="round,pad=0.3", fc="white", ec="#2DC56E", lw=0.8))

plt.tight_layout()
add_image(slide, fig_buf(fig), 0.4, 1.3, 6.4, 4.1)
plt.close(fig)
```

---

## Typography Reference

| Element | Size | Style | Color |
|---|---|---|---|
| Title slide main title | 40pt | Bold | `#1A2E44` (customer) / WHITE (internal) |
| Title slide subtitle | 22pt | Regular | `#445566` (customer) / BLUE (internal) |
| Tagline in bottom panel | 18pt | Bold | `#1A2E44` |
| Content slide title | 26pt | Bold | `#1A2E44` (customer) / WHITE (internal) |
| Content slide subtitle | 13pt | Regular | `#445566` (customer) / BLUE (internal) |
| Section number badge | 16pt | Bold | WHITE |
| Column/tile header | 12-14pt | Bold | WHITE |
| Body text | 10-12pt | Regular | `#334455` |
| Cortex Code prompt | 11pt | Italic | `#222244` |
| Scenario box text | 11pt | Regular | WHITE |
| KPI value (internal) | 30pt | Bold | NAVY or GREEN |
| Footer | 8pt | Italic | `#778899` |

---

## Standard Slide Flow

### Customer Deck (13 slides, CEC / EBC style)

| # | Slide | Key component |
|---|---|---|
| 1 | Title | Left stripe + snowflake icon + bottom tagline panel |
| 2 | Agenda | Numbered sections with alternating color badges |
| 3 | Opening Questions | 4 discovery questions before any product content |
| 4 | Challenge / Pain Points | 4-box grid mapped to customer's industry pain |
| 5 | Horizon Overview | Capability tile grid + "what makes it different" box + Cortex Code callout |
| 6 | Data Quality | DMF list + industry signal examples + "what next" bridge |
| 7 | Observability: RCA & Impact | Scenario box + 2-column numbered steps + "without" contrast |
| 8 | Classification | 3-column feature breakdown + Cortex Code callout |
| 9 | Privacy | 2-column features (masking + row access) + Cortex Code callout |
| 10 | Tagging & Lineage | 2-column feature list + Cortex Code callout |
| 11 | Cortex Code — full slide | 5 use-case tiles, each with a prompt |
| 12 | Maturity Journey | 4-stage progression (Foundation → AI-Ready) with CTAs |
| 13 | Next Steps | 4 numbered actions with timing badges |

### Internal Exec Deck (9 slides, QBR / metrics style)

| # | Slide | Key component |
|---|---|---|
| 1 | Title (dark navy) | Full navy + blue stripe at midpoint |
| 2 | Executive Summary | 4 KPI cards + 4 two-run bullets |
| 3 | Adoption / Baseline | Bar chart + KPI cards |
| 4 | Growth / Trend | 2 charts (time series + benchmark) |
| 5 | Strongest Signals | 2 charts on fastest-growing metrics |
| 6 | Scorecard Table | Full data table + key takeaway box |
| 7 | Hard Questions | 2×2 Q&A objection grid |
| 8 | Next Steps | 4 numbered steps with color accent bars |
| 9 | Closing (dark navy) | Headline + 3 summary KPIs |

---

## Workflow

1. **Clarify mode**: Customer deck (external meeting) or Internal exec deck (QBR/metrics)?
2. **Gather inputs**: Topic, customer name/industry, 3-4 headline metrics or messages,
   any industry-specific scenarios or pain points to personalize.
3. **Choose structure** from standard flow above. Trim or extend as needed.
4. **Personalize** before writing code:
   - Opening Questions → rewrite for the customer's domain
   - Scenario box → use a scenario from the customer's data environment
   - Industry examples → replace with the customer's actual systems/tables
5. **Generate** the Python script using the templates in this skill.
   - Always `BLANK` layout — never use default pptx placeholders
   - Every content slide needs `customer_slide_header()` + `customer_slide_footer()`
   - Every content slide ends with `cortex_code_callout()`
6. **Run** and confirm output path.

---

## Quality Checklist (Customer Deck)

- [ ] Left vertical `#29B5E8` stripe on every slide (0.12" title, 0.08" content)
- [ ] Header panel: `#F0F7FD` with DARK title text (NOT reversed white-on-navy)
- [ ] Footer: `#F0F7FD` band with "Snowflake Confidential" in italic grey
- [ ] Agenda: numbered badges with section-matching colors, alternating row backgrounds
- [ ] Opening Questions slide appears BEFORE any product content (slide 3)
- [ ] Every content slide ends with `cortex_code_callout()` (purple box + ❄ prompt)
- [ ] At least one Scenario Box on any deep-dive slide
- [ ] Capability tile grid uses `#FAFCFF` body, colored header strips
- [ ] Maturity Journey has 4 stages with a Cortex Code prompt at each stage
- [ ] Next Steps includes timing badge on each item
- [ ] "Without X" contrast box on the observability or RCA slide

---

## Real Examples (in `/Users/rbalakrishnan/`)

| File | Description |
|---|---|
| `Downloads/Envision_Healthcare_Horizon_CEC_Apr23_v3.pptx` | **Source of truth** — customer CEC deck, all patterns derived from this |
| `governance_coco_adoption_slides.pptx` (+ `governance_coco_slides.py`) | Internal exec mode, all 9 slides |
| `Governance_Skills_Practitioner_Guide.pptx` (+ `gen_pptx.py`) | 16-slide practitioner deck |
| `Governance_Q2_FY27_Roadmap.pptx` (+ `governance_q2_roadmap_gen.py`) | Roadmap + PLT inventory |
