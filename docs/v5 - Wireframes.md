# Version 5: Wireframes
Here are the structural layouts and plain text wireframes for the three screens based on your Information Architecture decisions.

### Screen 1 — Schedule/Home

**Spatial & Structural Answers:**

- **What's at the very top?** A prominent status banner showing the next race location (e.g., "NEXT RACE: ASSEN GP") alongside a countdown timer to the next session.
    
- **How are the session timings laid out?** On desktop, it is a clean table displaying the Session, Local Time (User's timezone), and Track/Remote Time. On mobile, to prevent horizontal scrolling, these will become vertically stacked flex-cards for each session.
    
- **Where does the contenders section begin?** Directly below the session schedule block.
    
- **How is the contenders block structured?** It is a color-coded vertical list or grid of summary cards highlighting only the riders who are mathematically in contention for the championship (within a 37-point difference).
    
- **What happens when there's no race weekend? (off-week state)** The countdown timer extends to the next race weekend. The schedule block displays the _provisional_ timings for that upcoming weekend. The contenders block shifts from "immediate mathematical contention for the next race" to simply displaying the current top 3 overall championship leaders.
    

**Desktop/Tablet Wireframe:**

Plaintext

```
+-------------------------------------------------------------+
| [ LOGO ]                                                    |
|                   NEXT RACE: ASSEN GP                       |
|               Countdown: 01d : 11h : 34m                    |
+-------------------------------------------------------------+
| SESSION SCHEDULE                                            |
| +---------------------------------------------------------+ |
| | SESSION     | LOCAL TIME (IST)   | TRACK TIME (GMT+2)   | |
| +-------------+--------------------+----------------------+ |
| | Practice 1  | Fri 14:15          | Fri 10:45            | |
| | Sprint      | Sat 18:30          | Sat 15:00            | |
| | Main Race   | Sun 17:30          | Sun 14:00            | |
| +---------------------------------------------------------+ |
+-------------------------------------------------------------+
| TITLE CONTENDERS (Within 37 Pts)                            |
| +-----------------+  +-----------------+  +---------------+ |
| | 1. PB63   147pt |  | 2. MM93   110pt |  | 3. JM89 105pt | |
| +-----------------+  +-----------------+  +---------------+ |
+=============================================================+
|        [ HOME ]         [ STANDINGS ]         [ RIDERS ]    |
+-------------------------------------------------------------+
```

### Screen 2 — Standings

**Spatial & Structural Answers:**

- **Where do the three dropdowns live?** At the very top of the screen, just below the page title. On desktop, they sit inline horizontally. On mobile, they are stacked vertically or placed in a horizontal scrollable chip row to save vertical space.
    
- **How does the table behave on mobile vs desktop?**
    
    - **Desktop:** The table expands to show Position, Rider name, Team name, Constructor, Points, and Difference.
        
    - **Mobile:** The table strips away non-essential data to fit the viewport width, displaying only Position, Rider name, and Points.
        
- **Is there any visual treatment for the leader vs other riders?** Yes, rows will be color-coded based on the rider's team or manufacturer using the colors outlined in palette.jpg or the fallback populorpalette.png. The championship leader can be emphasized with a slightly bolder typography treatment (using the selected fonts) or a distinct visual badge.
    

**Mobile Wireframe:**

Plaintext

```
+------------------------------------+
| CHAMPIONSHIP STANDINGS             |
|                                    |
| [ Year: 2026 v ]                   |
| [ Class: GP v  ]                   |
| [ Type: Rider v]                   |
+------------------------------------+
| POS | RIDER               | PTS    |
|-----+---------------------+--------|
|  1  | F. Bagnaia          | 160    |
|  2  | J. Martin           | 145    |
|  3  | M. Marquez          | 132    |
|  4  | E. Bastianini       | 114    |
+====================================+
|  [ HOME ]  [ STANDINGS ] [ RIDERS ]|
+------------------------------------+
```

### Screen 3 — Riders

**Spatial & Structural Answers:**

- **What does a single rider card look like?** The card is split into two visual zones. The top acts as an identity badge containing the rider's picture, name, country flag, team, and constructor. The bottom area holds their quote and a short biographical description.
    
- **How much information is visible per card before scrolling?** The design utilizes a continuous scrollable page where the riders appear in current championship standing order. One full rider profile card should dominate the viewport, acting almost like a vertical swipe feed.
    
- **Is there a header or any navigation within this screen?** There is no complex sub-navigation (to maintain a clean UI for normal fans and newcomers). There is only a simple, sticky header ("Rider Profiles") at the top so users know where they are, while the bottom global navbar remains anchored.
    

**Desktop/Mobile Hybrid Wireframe:**

Plaintext

```
+-------------------------------------------------------------+
| RIDER PROFILES                                              |
+-------------------------------------------------------------+
| +---------------------------------------------------------+ |
| |                                                         | |
| |  [ PROFILE ]      1. Francesco Bagnaia                  | |
| |  [ IMAGE   ]      Country: Italy [Flag]                 | |
| |                   Team: Ducati Lenovo Team              | |
| |                   Bike: Desmosedici GP26                | |
| |                                                         | |
| |  "Go fast, take chances."                               | |
| |  -----------------------------------------------------  | |
| |  Francesco "Pecco" Bagnaia is an Italian motorcycle...  | |
| +---------------------------------------------------------+ |
|                                                             |
|                         [ ^ ]                               |
|                  (Scroll to next rider)                     |
+=============================================================+
|        [ HOME ]         [ STANDINGS ]         [ RIDERS ]    |
+-------------------------------------------------------------+
```
I appreciate the thorough review. You are completely right about the off-week state contradiction and the hidden complexities of the countdown and layout scaling. It is much better to catch these logic gaps now than during implementation.

Here are the requested updates to finalize the V5 wireframes and layout definitions.

### 1. Off-Week State & Provisional Data

- **Contenders Block:** During an off-week, the contenders block will display _all_ riders mathematically within 37 points of the championship leader. This honors the established racing logic rather than defaulting to an arbitrary top 3.
    
- **Risk Flag (Provisional Timings):** If provisional timings for the upcoming race are not yet available from the selected backend API, the schedule block will display a fallback empty state (e.g., "Schedule TBA") rather than breaking the UI.
    

### 2. Countdown Timer Logic

- **Target:** The timer always counts down to the _immediate next session_ that has not yet started. If Practice 1 ends, it automatically targets Practice 2. Once the Sunday Main Race finishes, it shifts to target Practice 1 of the following GP.
    
- **Timezone Handling:** The countdown calculates the difference between the session's UTC timestamp (provided by the backend) and the user's local system time (via standard browser APIs) to ensure accuracy across all global regions.
    

### 3. Contenders Block Layout (Desktop)

- **Behavior Rule:** To accommodate early-season states where 6+ riders might be within 37 points, the desktop contenders block utilizes a **wrapping grid**.
    
- **Constraints:** It will display a maximum of 4 cards per row before wrapping to a new line, ensuring the layout scales cleanly without breaking the viewport width or forcing horizontal scroll.
    

### 4. Riders Screen Scroll Indicator

- **Correction:** The `[ ^ ]` indicator was visually counter-intuitive. It is updated to a simple `[ v ]` pointing downward. The explicit "Scroll to next rider" text label is removed to eliminate cognitive friction. The natural visual cutoff of the next rider's card at the bottom of the viewport will serve as the primary scroll affordance.
    

### 5. Cross-Linking & Interaction States

- **Cross-Linking Decision:** Cross-linking from the Standings table directly to a specific Rider profile card is **out of scope for V1**. Users must navigate strictly via the bottom navbar tabs to maintain architectural simplicity.
    
- **Standings Filter State:** When a user changes a dropdown (e.g., Class or Category), the dropdown retains an active visual highlight, and the table data reloads in place without a full page refresh.
    

### 6. Riders Screen Landing Position

- **Landing Rule:** Whenever the user navigates to the Riders screen via the bottom navbar, the view will **always land at P1** (the current championship leader). The application will not store or remember previous scroll depth.