---
name: governance-pm-slide-deck
description: "Create polished, on-brand executive slide decks in Python-pptx for Snowflake Data & AI Governance. Use when: building a customer deck, QBR presentation, roadmap slide, executive briefing, or any data-backed PowerPoint. Triggers: create a deck, build a slide, make a presentation, create slides, build a pptx, customer deck, executive deck, roadmap deck, QBR deck, pitch deck, slide deck."
---

# Governance PM Slide Deck Skill

Generates polished, Snowflake-branded PPTX files using `python-pptx` + `matplotlib`.
Encodes the exact design system, color palette, and structural patterns that make
Raja's decks look noticeably better than generic ones.

---

## What Is Working Well (and Why)

These are the five things that most visibly separate these decks from default PowerPoint:

### 1. Snowflake Color System — Applied Everywhere
Not just in the header. Every element uses the brand palette consistently.
The teal border on KPI cards, the green for positive growth, the orange for
warnings — these create a coherent visual hierarchy that reads as "designed."

### 2. Two-Run Bullet Pattern
```
▸  Bold colored keyword  regular DKGREY body text
```
Instead of a uniform bullet list, each point has a **blue/navy bold keyword**
followed by the explanation in dark grey. The eye reads the keywords first,
then the detail. This is faster to scan and more executive-friendly.

### 3. KPI Cards with Growth Delta
Large number (30pt bold) + label + green delta in a teal-bordered card.
Executives see the number at a glance and the direction (growth/trend) immediately
below. No need to read a chart to get the headline.

### 4. "Addressing the Hard Questions" Slide
A 2×2 grid of Q&A boxes — each with the anticipated objection in bold navy
and the data-backed answer below. This is the most commented-on slide.
It shows confidence and preparation, and pre-empts interruptions.

### 5. Title/Closing Bookend
Title slide: full navy + blue accent stripe at midpoint.
Closing slide: same full navy layout, but now shows 3 summary KPIs.
This creates a visual "loop" — the audience ends where they began but now
the numbers tell the full story.

---

## Color Palette (Copy Exactly)

```python
from pptx.dml.color import RGBColor

NAVY   = RGBColor(0x1A, 0x3F, 0x6F)   # Snowflake deep navy — headers, titles
BLUE   = RGBColor(0x29, 0xB5, 0xE8)   # Snowflake signature blue — accents, subtitles
TEAL   = RGBColor(0x00, 0xB4, 0xD8)   # KPI card borders
GREEN  = RGBColor(0x2D, 0xC5, 0x6E)   # Positive growth, success
ORANGE = RGBColor(0xF6, 0x82, 0x1F)   # Warnings, accent highlights
WHITE  = RGBColor(0xFF, 0xFF, 0xFF)
LGREY  = RGBColor(0xF3, 0xF4, 0xF6)   # Card backgrounds, footer band
GREY   = RGBColor(0x6B, 0x72, 0x80)   # Secondary text, captions
DKGREY = RGBColor(0x37, 0x41, 0x51)   # Body text

# For matplotlib charts (same palette, hex strings)
MPL_NAVY   = "#1A3F6F"
MPL_BLUE   = "#29B5E8"
MPL_TEAL   = "#00B4D8"
MPL_GREEN  = "#2DC56E"
MPL_ORANGE = "#F6821F"
MPL_GREY   = "#6B7280"
MPL_LGREY  = "#F3F4F6"
```

---

## Slide Dimensions

```python
from pptx import Presentation
from pptx.util import Inches

prs = Presentation()
prs.slide_width  = Inches(13.33)   # widescreen 16:9
prs.slide_height = Inches(7.5)
BLANK = prs.slide_layouts[6]       # completely blank — always use this
```

---

## Core Helper Functions (paste into every generator script)

```python
from pptx.enum.text import PP_ALIGN
from pptx.util import Inches, Pt

def add_rect(slide, x, y, w, h, fill=None, line=None):
    shape = slide.shapes.add_shape(1, Inches(x), Inches(y), Inches(w), Inches(h))
    shape.line.fill.background()
    if fill:
        shape.fill.solid()
        shape.fill.fore_color.rgb = fill
    else:
        shape.fill.background()
    if line:
        shape.line.color.rgb = line
        shape.line.width = Pt(1)
    else:
        shape.line.fill.background()
    return shape

def add_text(slide, text, x, y, w, h, size=18, bold=False, color=None,
             align=PP_ALIGN.LEFT, wrap=True, italic=False):
    txBox = slide.shapes.add_textbox(Inches(x), Inches(y), Inches(w), Inches(h))
    tf = txBox.text_frame
    tf.word_wrap = wrap
    p = tf.paragraphs[0]
    p.alignment = align
    run = p.add_run()
    run.text = text
    run.font.size = Pt(size)
    run.font.bold = bold
    run.font.italic = italic
    run.font.color.rgb = color or DKGREY
    return txBox

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

## Slide Templates

### Title Slide (dark navy bookend)
```python
s = prs.slides.add_slide(BLANK)
add_rect(s, 0, 0, 13.33, 7.5, fill=NAVY)          # full navy background
add_rect(s, 0, 3.35, 13.33, 0.08, fill=BLUE)       # blue accent stripe at midpoint

add_text(s, "DECK TITLE", 1.0, 1.4, 11.33, 0.9,
         size=38, bold=True, color=WHITE, align=PP_ALIGN.LEFT)
add_text(s, "Subtitle or theme line", 1.0, 2.3, 11.33, 0.7,
         size=22, color=BLUE, align=PP_ALIGN.LEFT)

# Meta lines (author, date, analysis period)
add_text(s, "Analysis Period: Q1 FY27", 1.0, 3.7, 11.33, 0.4, size=13, color=LGREY)
add_text(s, "Prepared by: Raja Balakrishnan | Data Governance PM", 1.0, 4.15, 11.33, 0.4, size=13, color=LGREY)

add_text(s, "CONFIDENTIAL", 1.0, 6.8, 4.0, 0.4, size=10, color=GREY, italic=True)
add_text(s, "April 2026", 10.5, 6.8, 2.5, 0.4, size=10, color=GREY, align=PP_ALIGN.RIGHT)
```

### Content Slide Header (use on every non-title slide)
```python
def slide_header(slide, title, subtitle=None):
    add_rect(slide, 0, 0, 13.33, 1.15, fill=NAVY)        # navy top bar
    add_rect(slide, 0, 1.15, 13.33, 0.06, fill=BLUE)     # thin blue accent line
    add_text(slide, title, 0.4, 0.12, 11.5, 0.75,
             size=28, bold=True, color=WHITE, align=PP_ALIGN.LEFT)
    if subtitle:
        add_text(slide, subtitle, 0.4, 0.82, 11.5, 0.35,
                 size=12, color=BLUE, align=PP_ALIGN.LEFT)

def slide_footer(slide, text="Snowflake Internal — Confidential | April 2026"):
    add_rect(slide, 0, 7.22, 13.33, 0.28, fill=LGREY)
    add_text(slide, text, 0.3, 7.24, 12.5, 0.22,
             size=7.5, color=GREY, align=PP_ALIGN.LEFT)
```

### KPI Card
```python
def kpi_card(slide, x, y, w, h, value, label, delta=None, val_color=None):
    add_rect(slide, x, y, w, h, fill=LGREY, line=TEAL)
    add_text(slide, value, x+0.08, y+0.08, w-0.16, h*0.52,
             size=30, bold=True, color=val_color or NAVY, align=PP_ALIGN.CENTER)
    add_text(slide, label, x+0.08, y+h*0.52, w-0.16, h*0.28,
             size=10, color=GREY, align=PP_ALIGN.CENTER)
    if delta:
        add_text(slide, delta, x+0.08, y+h*0.76, w-0.16, h*0.22,
                 size=10, bold=True, color=GREEN, align=PP_ALIGN.CENTER)

# Usage: 4 KPI cards in a row
card_w, card_h = 2.8, 1.65
for i, (val, lbl, delta, vcol) in enumerate(kpi_data):
    kpi_card(s, 0.5 + i*(card_w + 0.26), 1.5, card_w, card_h, val, lbl, delta, vcol)
```

### Two-Run Bullet (bold keyword + body text)
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

### Numbered Steps with Color Accent Bar
```python
steps = [
    (MPL_BLUE,   "01", "Step Title", "Body text explaining the step."),
    (MPL_GREEN,  "02", "Step Title", "Body text."),
    (MPL_ORANGE, "03", "Step Title", "Body text."),
    (MPL_TEAL,   "04", "Step Title", "Body text."),
]
sy, bh, gap = 1.45, 1.15, 0.22
for col, num, title, body in steps:
    accent = s.shapes.add_shape(1, Inches(0.4), Inches(sy), Inches(0.18), Inches(bh))
    accent.fill.solid(); accent.fill.fore_color.rgb = RGBColor.from_string(col[1:])
    accent.line.fill.background()
    bg = s.shapes.add_shape(1, Inches(0.58), Inches(sy), Inches(12.35), Inches(bh))
    bg.fill.solid(); bg.fill.fore_color.rgb = LGREY; bg.line.fill.background()
    add_text(s, num, 0.68, sy+0.08, 0.55, bh-0.1, size=22, bold=True,
             color=RGBColor.from_string(col[1:]))
    add_text(s, title, 1.3, sy+0.08, 3.0, 0.42, size=13, bold=True, color=NAVY)
    add_text(s, body, 1.3, sy+0.5, 11.4, 0.58, size=10.5, color=DKGREY)
    sy += bh + gap
```

### Addressing the Hard Questions (2×2 Q&A)
```python
qa = [
    ("Isn't this organic growth?",
     "Global AUM grew +17.4%. Our cohort grew +14.9% — higher starting base explains the gap. "
     "Where CoCo guidance is direct, cohort outperforms: DMFs +73.4% vs +65.6% global."),
    ("Correlation ≠ causation",
     "Agreed. First-use cohort study (AUM delta T+30/T+60) is in progress. "
     "This analysis is the leading indicator; the cohort study is the definitive proof."),
    ("The sample is self-selected",
     "The cohort includes all skill users in the period, including first-time single-session users. "
     "It is the full adopter population, not a cherry-picked sample."),
    ("Why are credits tiny?",
     "By design. Skills are guides, not compute workloads. "
     "Value is in the governed objects enabled, not the tokens the guide consumed."),
]
positions = [(0.4, 1.35), (7.05, 1.35), (0.4, 3.85), (7.05, 3.85)]
box_w, box_h = 5.7, 1.3
for (q_text, a_text), (bx, by) in zip(qa, positions):
    add_rect(s, bx, by, box_w, box_h, fill=LGREY, line=BLUE)
    add_text(s, f"❓  {q_text}", bx+0.12, by+0.08, box_w-0.2, 0.32,
             size=11, bold=True, color=NAVY)
    add_text(s, a_text, bx+0.12, by+0.42, box_w-0.2, box_h-0.5,
             size=9.5, color=DKGREY)
```

### Key Takeaway Box (right-column insight)
```python
add_rect(s, 8.6, 1.45, 4.35, 3.8, fill=RGBColor(0xEA, 0xF6, 0xFD), line=BLUE)
add_text(s, "Key Takeaway", 8.75, 1.55, 4.0, 0.45, size=13, bold=True, color=NAVY)
insights = ["Point 1", "Point 2", "Point 3"]
iy = 2.1
for ins in insights:
    add_text(s, f"▸  {ins}", 8.75, iy, 4.05, 0.5, size=10, color=DKGREY)
    iy += 0.58
```

### Closing Slide (mirror of title — full navy with 3 summary KPIs)
```python
s = prs.slides.add_slide(BLANK)
add_rect(s, 0, 0, 13.33, 7.5, fill=NAVY)
add_rect(s, 0, 3.5, 13.33, 0.07, fill=BLUE)

add_text(s, "One-sentence headline that captures everything.", 1.0, 1.6, 11.33, 1.0,
         size=30, bold=True, color=WHITE, align=PP_ALIGN.CENTER)
add_text(s, "Supporting line that connects the numbers to the story.",
         1.5, 2.75, 10.33, 0.75, size=15, color=BLUE, align=PP_ALIGN.CENTER)

summary_kpis = [("+14.9%", "AUM Growth"), ("+73.4%", "DMF Growth"), ("+51.6%", "Data Security")]
skw, skx, sky = 3.5, 0.67, 4.2
for val, lbl in summary_kpis:
    add_rect(s, skx, sky, skw, 1.5, fill=RGBColor(0x0E, 0x2A, 0x4E), line=BLUE)
    add_text(s, val, skx+0.1, sky+0.1, skw-0.2, 0.8,
             size=32, bold=True, color=GREEN, align=PP_ALIGN.CENTER)
    add_text(s, lbl, skx+0.1, sky+0.85, skw-0.2, 0.55,
             size=10, color=BLUE, align=PP_ALIGN.CENTER)
    skx += skw + 0.24
```

### Matplotlib Chart Conventions
```python
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt

# Always match chart colors to PPTX palette
fig, ax = plt.subplots(figsize=(6, 3.6), facecolor="white")

# Bar chart style
bars = ax.barh(labels, values, color=MPL_BLUE, alpha=0.88, height=0.45)
for bar, v in zip(bars, values):
    ax.text(v + 25, bar.get_y() + bar.get_height()/2,
            f"{v:,}", va="center", fontsize=11, fontweight="bold", color=MPL_NAVY)

# Always strip top/right/left spines
ax.spines[["top", "right", "left"]].set_visible(False)
ax.tick_params(left=False, bottom=False)
ax.xaxis.grid(True, linestyle="--", alpha=0.35)
ax.set_axisbelow(True)

# Annotate growth rate in bottom-right corner
ax.text(0.98, 0.06, "+73.4% growth", transform=ax.transAxes, ha="right",
        fontsize=10, color=MPL_GREEN, fontweight="bold",
        bbox=dict(boxstyle="round,pad=0.3", fc="white", ec=MPL_GREEN, lw=0.8))

plt.tight_layout()
buf = fig_buf(fig)
add_image(slide, buf, 0.35, 1.3, 6.4, 4.1)
plt.close(fig)
```

---

## Standard Slide Flow (customer deck)

| # | Slide type | Purpose |
|---|---|---|
| 1 | Title (dark navy) | Set tone; audience, date, author |
| 2 | Executive Summary | 4 KPI cards + 4 two-run bullets |
| 3 | Adoption / Baseline | Bar chart + overlap KPI cards |
| 4 | Growth / Trend | 2 charts (time series + benchmark comparison) |
| 5 | Strongest Signals | 2 charts on the fastest-growing metrics |
| 6 | Scorecard Table | Full data table + right-column key takeaway box |
| 7 | Hard Questions | 2×2 Q&A objection-handling grid |
| 8 | Next Steps | 4 numbered steps with color accent bars |
| 9 | Closing (dark navy) | Headline + 3 summary KPIs — mirrors title |

---

## Typography Rules

| Element | Size | Style | Color |
|---|---|---|---|
| Title (dark slide) | 38pt | Bold | WHITE |
| Subtitle (dark slide) | 22pt | Regular | BLUE |
| Slide header title | 28pt | Bold | WHITE |
| Slide header subtitle | 12pt | Regular | BLUE |
| KPI value | 30pt | Bold | NAVY or GREEN |
| KPI label | 10pt | Regular | GREY |
| KPI delta | 10pt | Bold | GREEN |
| Section number | 22pt | Bold | accent color |
| Body text | 12pt | Regular | DKGREY |
| Bold keyword (bullets) | 12pt | Bold | NAVY |
| Caption/footnote | 8-9pt | Italic | GREY |
| Footer | 7.5pt | Regular | GREY |
| Closing headline | 30pt | Bold | WHITE |
| Closing KPI value | 32pt | Bold | GREEN |

---

## Workflow

When asked to build a slide deck:

1. **Clarify** (ask only if not obvious):
   - What is the audience? (exec / CSM / customer / internal)
   - What are the 3-4 headline metrics or messages?
   - How many slides? (default: 8-9 for exec, 12-16 for practitioner)
   - Output path (default: `/Users/rbalakrishnan/rbalakrishnan/<DeckName>.pptx`)

2. **Structure** the slide flow using the standard order above.
   Adjust: remove Scorecard for shorter decks; add Skills Reference slides for practitioner decks.

3. **Generate** a Python script using the helpers and templates in this skill.
   - Always use `BLANK` layout (no default placeholders)
   - Always include `slide_header()` + `slide_footer()` on every non-title slide
   - Always embed charts via `fig_buf()` + `add_image()` — never native pptx charts
   - Always output to the user's preferred folder

4. **Run** the script and confirm the output path.

5. **Report** what each slide shows and which design choices were made.

---

## Quality Checklist

Before handing off any deck, verify:
- [ ] Title slide: full navy background + blue accent stripe at midpoint
- [ ] Every content slide: `slide_header()` called (navy bar + blue underline)
- [ ] Every content slide: `slide_footer()` called (grey band + confidential text)
- [ ] KPI cards: value is bold, delta is green, border is teal
- [ ] Bullets: two-run pattern (bold navy keyword + DKGREY body), not flat strings
- [ ] Charts: matplotlib, brand colors, spines stripped, growth annotated in corner
- [ ] Numbered steps: colored left accent bar (0.18") + LGREY background
- [ ] Objections slide present if this is a data/ROI deck
- [ ] Closing slide: mirrors title (full navy) + 3 summary KPIs in GREEN

---

## Real Examples (in `/Users/rbalakrishnan/`)

| File | Script | What it demonstrates |
|---|---|---|
| `governance_coco_adoption_slides.pptx` | `governance_coco_slides.py` | Full 9-slide exec deck with all components |
| `Governance_Skills_Practitioner_Guide.pptx` | `gen_pptx.py` | 16-slide practitioner deck with code blocks |
| `Governance_Q2_FY27_Roadmap.pptx` | `governance_q2_roadmap_gen.py` | Roadmap + research findings + PLT inventory |
| `Data_AI_Governance_QBR_FY27.pptx` | (QBR generator) | QBR format with OKR progress |
