# Version 6: Design System
Here is the completed V6 documentation. I have defined the spacing scale using an 8px base, established a 7-step typographic scale in `rem`, and defined `--color-text-disabled` as `#606366` (Dim Grey), which has a contrast ratio of roughly 2.3:1 against Carbon Grey—intentionally failing AA to visually communicate unavailability without blending into the secondary metadata.

**`docs/v6.md`**

# V6 Design System

## Color Tokens

**Surfaces (Dark Mode Baseline)**

- `--color-bg-base`: `#161616` (Tarmac Black) — The absolute bottom layer. Used for the HTML body and outermost app container.
    
- `--color-bg-surface`: `#2B2B2B` (Carbon Grey) — Elevated level 1. Used for cards, table rows, and the bottom navigation bar.
    
- `--color-bg-floating`: `#404040` (Graphite Grey) — Elevated level 2. Used for floating elements above surfaces, such as dropdown menus, tooltips, and modals.
    

**Text & Icons**

- `--color-text-primary`: `#FFFFFF` (Podium White) — High-emphasis UI. Used for all primary reading text, active tab labels, and primary data points.
    
- `--color-text-secondary`: `#A1A3A6` (Asphalt Grey) — Medium-emphasis UI. Used for timezone labels, inactive nav icons, table borders, and metadata.
    
- `--color-text-disabled`: `#606366` (Dim Grey) — Low-emphasis/Inactive UI. Used exclusively for disabled text or disabled form controls. (Contrast: ~2.3:1 against surface, intentionally failing AA per WCAG 1.4.3).
    

**Accents & Interaction**

- `--color-accent-primary`: `#E21D24` (Race Red) — Critical State / Primary Action. Used for "Live" session badges and primary buttons. _Rule: Never use as foreground text on dark surfaces due to contrast failure. Red must be a background._
    
- `--color-accent-on-red`: `#FFFFFF` — Text/icons placed on top of Race Red backgrounds to ensure AA contrast compliance (~4.9:1).
    
- `--color-accent-secondary`: `#00B8B8` (Grid Teal) — Interactive/Non-critical. Used for active UI controls, links, and secondary interactive icons.
    

**Data Highlights**

- `--color-data-leader`: `#FFE202` (Speed Yellow) — P1 Highlight. Reserved strictly for highlighting the championship leader in standings. Never used for UI chrome.
    
- `--color-data-leader-text`: `#161616` (Tarmac Black) — Text/icons placed on top of Speed Yellow backgrounds to ensure maximum readability.
    

## Typography

**Font Family Assignments**

- `--font-display`: **Audiowide** — The "Data" font. Strictly for countdown timers, race positions (P1, P2), and points numerics.
    
- `--font-structure`: **Syncopate** — The "Wayfinding" font. Strictly for page titles, section headers, and nav labels. Uppercase only. Short strings only.
    
- `--font-body`: **Inter** — The "Workhorse" font. For rider names, team names, dropdown options, bios, and all readable UI text.
    

**Size Scale (Base: 16px)**

- `--text-xs`: `0.75rem` (12px) — Fine print, timezone labels.
    
- `--text-sm`: `0.875rem` (14px) — Metadata, secondary UI labels, inactive nav text.
    
- `--text-base`: `1rem` (16px) — Body text, rider names, table data.
    
- `--text-md`: `1.25rem` (20px) — Subheadings, active nav tabs, dropdown active items.
    
- `--text-lg`: `1.5rem` (24px) — Section headers (e.g., "SESSION SCHEDULE").
    
- `--text-xl`: `2rem` (32px) — Page titles (Syncopate), prominent numerics.
    
- `--text-2xl`: `3rem` (48px) — Hero display numbers, countdown timers (Audiowide).
    

## Spacing

**Scale (8px Base Unit)**

- `--space-xs`: `0.25rem` (4px) — Tight element grouping (e.g., icon to label).
    
- `--space-sm`: `0.5rem` (8px) — Inner padding for small UI components, table cell padding.
    
- `--space-md`: `1rem` (16px) — Default outer padding, gap between stacked cards.
    
- `--space-lg`: `1.5rem` (24px) — Section spacing, padding inside larger profile cards.
    
- `--space-xl`: `2rem` (32px) — Macro layout spacing, margins between major page zones.
    
- `--space-2xl`: `3rem` (48px) — Bottom padding above the sticky navbar.
    
- `--space-3xl`: `4rem` (64px) — Top spacing/Hero padding.
    

## Interaction States

- **Hover (Desktop/Mouse):** Interactive elements (cards, table rows, dropdown items) lighten their background color by a half-step using a subtle white overlay (e.g., `rgba(255, 255, 255, 0.05)`).
    
- **Focus (Accessibility):** Focused elements receive a 2px solid outline in `--color-accent-secondary` (Grid Teal), offset by 2px from the element's bounding box.
    
- **Active (Tap/Press):** The element scales down to `0.98` and the background opacity shifts slightly darker to simulate physical depression.
    
- **Active UI Tab/Selection:** The currently selected tab or dropdown option uses `--color-text-primary` (Podium White) for max contrast.
    
- **Disabled:** The component background remains at its default, but the text shifts to `--color-text-disabled` (`#606366`), and `pointer-events: none` is applied.
    

## Component Inventory

- **Layout & Navigation:** Bottom Navbar, Sticky Page Header, Navbar Item (Active/Inactive).
    
- **Data & Tables:** Standings Table, Table Row (Standard), Table Row (P1 Leader Highlight).
    
- **Cards & Modules:** Session Schedule Card, Contender Summary Card, Rider Profile Card.
    
- **Controls & Inputs:** Dropdown Menu, Dropdown Item, Primary Button.
    
- **Status Indicators:** Live Session Badge, Countdown Timer, Team Color Swatch / Border-Left Decorator.
    

## Team Color Rules

**The Isolation Policy:**

Team colors (e.g., Ducati Red, Yamaha Blue, Trackhouse Aprilia patterns) exist in a strictly isolated `--color-team-*` namespace. They are **never** to be applied to semantic UI elements, typography, buttons, or interactive surfaces. Their usage is restricted exclusively to structural geometric decorators, such as a 4px `border-left` on a standings table row or a static 12x12px square swatch next to a rider's name. This ensures team colors never collide with semantic UI states like "Live" (Race Red) or "Active" (Grid Teal).

## Dark Mode Baseline

**Surface Hierarchy:**

The application does not use pure black (`#000000`). Depth is communicated strictly through lightness steps via the defined surface tokens.

- **Level 0 (Base):** Everything rests on `--color-bg-base` (`#161616`).
    
- **Level 1 (Surface):** Interactive content modules (cards, tables) rest on `--color-bg-surface` (`#2B2B2B`).
    
- **Level 2 (Floating):** Transient interactive layers (dropdowns, tooltips) rest on `--color-bg-floating` (`#404040`) to ensure they distinctly overlay Level 1 elements without relying on heavy box-shadows (which disappear in dark mode).
    

**Commit:** `docs: add V6 design system`

I appreciate the final review and the sign-off on V6. Your feedback on the three flags is completely valid—ignoring line heights and multi-surface contrast checks are exactly the kind of oversights that cause friction in the high-fidelity phase.

To ensure the `docs/v6.md` file is perfectly sealed for this iteration, here are the documented patches for the three flags:

### 1. Typography Line Heights (Flag 1 Patch)

Added to the **Typography** section to ensure vertical rhythm and legibility:

- **Audiowide (Display):** Line-height `1.1`. Prevents large countdowns and numerics from feeling vertically disconnected or cramped.
    
- **Syncopate (Structure):** Line-height `1.2`. Tames the extremely wide letterforms and provides tight vertical rhythm for stacked page titles.
    
- **Inter (Body):** Line-height `1.5`. Ensures maximum readability and comfortable eye tracking for multi-line biographical paragraphs and UI lists.
    

### 2. Disabled Text Contrast Floor (Flag 2 Patch)

Updated the **Color Tokens** definition to explicitly document the lowest-contrast scenario across all surfaces:

- `--color-text-disabled`: `#606366` (Dim Grey) — Low-emphasis/Inactive UI. Used exclusively for disabled text or disabled form controls. _(Contrast: ~2.3:1 against Carbon Grey, ~3.3:1 against Tarmac Black. Intentionally fails AA to visually communicate unavailability without blending into secondary metadata)._
    

### 3. Spacing Token Usage (Flag 3 Patch)

Removed the premature layout predictions from the **Spacing** scale to keep the system strictly abstract:

- `--space-2xl`: `3rem` (48px) — Large layout spacing.
    
- `--space-3xl`: `4rem` (64px) — Extra-large layout spacing.
    

**Commit:** `docs: patch V6 line heights, disabled contrast bounds, and spacing abstraction`

The V6 Design System is fully locked and documented.





















Here are my answers to the three prerequisite questions for the V6 Design System.

### 1. Confirmed Brand Colors, Hex Codes, and Roles

Based on our primary visual direction and the dark mode baseline, here is the committed color palette:

- **Carbon Grey (`#2B2B2B`)**
    
    - _Role:_ Primary Background / Surface.
        
    - _Usage:_ The foundational dark mode background for the entire app, as well as elevated surface backgrounds (like cards or dropdowns).
        
- **Podium White (`#FFFFFF`)**
    
    - _Role:_ Primary Text / High-Emphasis UI.
        
    - _Usage:_ All primary reading text, active tab icons, and primary data points in tables.
        
- **Asphalt Grey (`#A1A3A6`)**
    
    - _Role:_ Secondary Text / Subdued UI.
        
    - _Usage:_ Muted text (like timezone labels), inactive navbar icons, table borders, and disabled states.
        
- **Race Red (`#E21D24`)**
    
    - _Role:_ Primary Action / Critical State / Brand Accent.
        
    - _Usage:_ The "Live" indicator, primary buttons, and team color-coding for Ducati/Aprilia.
        
- **Speed Yellow (`#FFE202`)**
    
    - _Role:_ Highlight / Active State.
        
    - _Usage:_ The active selected state in dropdowns, highlighting the current championship leader (P1), and VR46 team color-coding.
        
- **Circuit Blue (`#004185`)** & **Grid Teal (`#00B8B8` - _from fallback_)**
    
    - _Role:_ Info States / Secondary Accents.
        
    - _Usage:_ Non-critical interactive elements and team color-coding (e.g., Yamaha, Trackhouse, or Aston Martin/Petronas vibes).
        

### 2. What Problem Does Each Color Solve?

Colors here are highly functional, balancing motorsport aesthetics with UI usability:

- **Why Race Red?** Red is the undisputed color of motorsport adrenaline, but functionally, it commands immediate visual hierarchy. In a dark UI, red cuts through the noise. It solves the problem of telling the user _"Look here right now"_—whether that's a "LIVE" session badge or a primary call-to-action.
    
- **Why Speed Yellow?** Yellow provides the highest possible contrast ratio against Carbon Grey. It solves the problem of active state recognition. When a user is scanning a dense standings table, a Speed Yellow accent instantly anchors their eye to the championship leader or the active navigation tab.
    
- **Why Teal / Circuit Blue?** If every accent is Red or Yellow, the app feels like a warning dashboard. Teal and Blue solve the problem of visual fatigue. They serve as "cool" interaction colors—indicating that an element is clickable or selectable (like a dropdown or a secondary filter) without screaming for attention.
    
- **Why Carbon & Asphalt Grey?** They solve the dark mode contrast problem. Pure black (`#000000`) causes eye strain when scrolling text. Carbon Grey softens the background, while Asphalt Grey establishes a clear visual hierarchy for secondary information, ensuring the UI remains scannable.
    

### 3. Typography Across Hierarchy Levels

We are balancing two highly stylized display fonts with a workhorse sans-serif. Here is how they divide the labor:

- **Audiowide (Display / Numerics):**
    
    - _Role:_ The "Data" font.
        
    - _Why:_ It has a distinctly technical, futuristic, digital-dashboard aesthetic. It will strictly handle the **Countdown Timer**, **Race Positions (P1, P2)**, and **Points** in the standings table. It turns raw numbers into a motorsport telemetry experience.
        
- **Syncopate (Macro-Headers / Navigation):**
    
    - _Role:_ The "Structure" font.
        
    - _Why:_ Syncopate is exceptionally wide and commands horizontal space. It will be used for **Page Titles (e.g., CHAMPIONSHIP STANDINGS)**, **Section Headers**, and **Bottom Nav Labels**. Because it is hard to read in long sentences, it is restricted to short, uppercase structural wayfinding.
        
- **Inter (Body / Micro-UI):**
    
    - _Role:_ The "Workhorse" font.
        
    - _Why:_ Audiowide and Syncopate have too much personality; using them for everything would ruin legibility. Inter will handle all **Rider Names**, **Team Names**, **Dropdown options**, and **Biographical paragraphs**. It ensures that when Vale (our casual fan) is trying to actually read information, there is zero cognitive friction.

You are absolutely right to push back. A design system that fails accessibility and surface logic is just a pretty picture that breaks in production. Here are the hard decisions to fix those foundational gaps.

### 1. Circuit Blue vs. Grid Teal

**Decision:** I am dropping Circuit Blue (`#004185`) from the UI semantic system entirely and committing to **Grid Teal (`#00B8B8`)** as the secondary accent.

**Defense:** Circuit Blue is a deep navy. Against a dark background like Carbon Grey, it severely lacks contrast and recedes visually, making it useless for UI controls. Grid Teal pops brilliantly against dark grey. It clearly communicates "interactive but non-critical" (unlike Red's "alert" or Yellow's "active selection"). Circuit Blue will be banished from the UI system and relegated strictly to the Team Colors pool (e.g., for Yamaha or Trackhouse).

### 2. Team Colors vs. UI State Colors

**Decision:** Team colors and Semantic UI colors will live in two strictly isolated design patterns.

**Defense:** To prevent semantic collision, Team Colors will _never_ be applied to typography, icons, buttons, or interactive surfaces. Instead, they will be restricted to **structural geometric accents**. For example, in the standings table, a Ducati rider will simply have a 4px wide `border-left` in Ducati Red on their row, or a small static color swatch next to their name.

By confining team colors to predictable structural boundaries, the user will inherently understand that a Red left-border means "Ducati", but a Red pill badge with white text means "LIVE RACE".

### 3. Contrast Ratios (Against Carbon Grey `#2B2B2B`)

I ran the math. You were spot on about Race Red—it fails catastrophically. Here are the actual ratios:

- **Podium White (`#FFFFFF`) on Carbon Grey:** **14.3:1** (Passes AAA for all text).
    
- **Speed Yellow (`#FFE202`) on Carbon Grey:** **~10.9:1** (Passes AAA for all text).
    
- **Asphalt Grey (`#A1A3A6`) on Carbon Grey:** **~5.6:1** (Passes AA for normal text, AAA for large text).
    
- **Race Red (`#E21D24`) on Carbon Grey:** **2.89:1** (FAILS AA completely. Requires minimum 3:1 for large text and 4.5:1 for normal text).
    

**How we handle the Red failure:** Race Red _cannot_ be used for text on a Carbon Grey background. Period. If we need a red alert badge, the component must be a Race Red _background_ with Podium White text on top of it (White on Race Red is ~4.9:1, which passes AA).

### 4. Surface Hierarchy

To create proper depth, we need a darker base. Carbon Grey (`#2B2B2B`) is actually quite light for a dark mode base layer; if we use it for the background, elevated cards have to be even lighter, which starts washing out the dark mode aesthetic.

**Decision:** We are splitting the dark surfaces into two distinct layers:

- **Base Layer (`#161616` - Tarmac Black):** The absolute bottom layer. Used for the app's main HTML body background.
    
- **Elevated Surface (`#2B2B2B` - Carbon Grey):** Used for components that sit on top of the base layer, such as the Rider Profile cards, the Standings table rows, and Dropdown menus.
    

By pushing the base layer darker to `#161616`, Carbon Grey (`#2B2B2B`) now functions perfectly as our elevated surface, signaling to the user that they are looking at distinct, interactive modules resting on the background.

You are right to hold my feet to the fire on this. A design system is built on math and strict rules, not vibes. Here are the answers to the three remaining pressure points.

### 1. Grid Teal Contrast Ratios

I ran the numbers for Grid Teal (`#00B8B8`). It is highly accessible across both of our defined dark mode surfaces.

- **Grid Teal on Tarmac Black (`#161616`):** **~7.5:1**. (Passes WCAG AAA for both normal and large text).
    
- **Grid Teal on Carbon Grey (`#2B2B2B`):** **~6.0:1**. (Passes WCAG AA for normal text, AAA for large text).
    

_Conclusion:_ Grid Teal is fully cleared to function as an interactive text or icon color on any surface in the app.

### 2. The Third Surface Level

To create a third level for floating elements (like dropdown menus opening over a card, or tooltips), we need to maintain a consistent mathematical step in lightness without washing out the dark mode aesthetic.

- **Base (Level 0):** `#161616` (Tarmac Black)
    
- **Surface (Level 1):** `#2B2B2B` (Carbon Grey)
    
- **Floating (Level 2):** `#404040` (**Graphite Grey**)
    

_Reasoning:_ `rgb(22, 22, 22)` jumps to `rgb(43, 43, 43)`, which is a +21 step in RGB values. Applying roughly the same upward step from Carbon Grey lands us at `rgb(64, 64, 64)`, which is `#404040`. It provides immediate, intuitive visual separation from the surface below it while remaining definitively dark.

### 3. Resolving the Speed Yellow Conflict

You spotted a critical semantic collision. If Speed Yellow is both "Navigation/UI Active" and "Championship Leader P1," the color loses its meaning and creates visual noise. We must separate the structural UI from the data highlights. Here are the three best options to resolve this:

**Option A: Shift UI Active State to Podium White (Recommended)**

- _How it works:_ The active tab in the bottom navbar and the selected option in a dropdown turn Podium White (`#FFFFFF`). Speed Yellow is reserved _strictly_ as a data highlight for the P1 Championship Leader.
    
- _Why it’s strong:_ White is the standard iOS/Android dark mode convention for "active tab." It is perfectly neutral, high-contrast, and leaves the colorful accents (Yellow/Red) exclusively for motorsport data.
    

**Option B: Shift UI Active State to Grid Teal**

- _How it works:_ Since we defined Grid Teal as our "interactive but non-critical" accent, we use it for active tabs and selected dropdowns. Speed Yellow stays with P1.
    
- _Why it’s strong:_ It consolidates all interactive UI states under one color family (Teal), drawing a hard line between "App Controls" (Teal) and "Racing Data" (Yellow/Red).
    

**Option C: Shift P1 Highlight to a Structural Badge**

- _How it works:_ Keep Speed Yellow for the active UI state, but remove it from the P1 row entirely. Instead of a color highlight, P1 gets a distinct structural badge (e.g., a "LEADER" pill or a crown icon in Podium White).
    
- _Why it’s weak:_ It strips the app of a very classic motorsport visual trope (the yellow leaderboard highlight).
    

My strong preference is **Option A**. It relies on established OS-level muscle memory for the UI, keeping the interface invisible so the racing data (Yellow/Red) can be the hero.

