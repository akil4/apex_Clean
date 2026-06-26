# Version 1
## Data source commitment
Championship data - [robschmitt github API](https://github.com/robschmitt/MotoGP-API)  / [racingmike endpoint](https://github.com/micheleberardi/racingmike_motogp_import) 
Historical / Candidate data - [Wikipedia API](https://api.wikimedia.org/wiki/API_catalog)
## Screen content specs
### Championship standings: 
A dropdown for selecting year
A dropdown for selecting class(MotoGP, Moto2, Moto3)
A dropdown for selecting category(Rider, Team, Constructor)
A table with the following structure

| Position | Rider | Team | Constructor | Points | Difference |
| -------- | ----- | ---- | ----------- | ------ | ---------- |
|          |       |      |             |        |            |
Historical data can be viewed by changing year in the dropdown menu
### Rider profile:
A picture
Rider Name
Quote
Rider Country
Team and Constructor
Short description
## Information Architecture
### Home:
Has schedule with local and remote timings of the next session similar to mototiming.live
A navbar at the bottom/top with schedule, standings, rider
Clicking the standings will go to championship standings
Clicking the rider will go to rider data page
### Championship standings
A clean ui as mentioned previously
### Rider profile
As mentioned previously
## Visual design direction
Try
![[palette.jpg]]
Fallback:
![[populorpalette.png]]
Typography:
Audiowide, Syncopate available in google fonts
Layout:
Flex layout
## Wireframes
Here are the text-based ASCII wireframe sketches for your three-part MotoGP application layout. They focus entirely on structural layout zones, component placement, and anchoring the bottom navigation bar across all screens.

## Screen 1: Home / Schedule Page

> **Layout Strategy:** Inspired by `mototiming.live`, the top area features a prominent countdown/status banner for the upcoming GP, followed by a clean, scannable table split into Local Time and your current Remote/Track Time zones.

Plaintext

```
+-------------------------------------------------------------+
|                                                             |
|   [ ICON ]            NEXT RACE: ASSEN GP                   |
|                       Countdown: 02d : 14h : 35m            |
|                                                             |
+-------------------------------------------------------------+
|                                                             |
|  SESSION SCHEDULE                                           |
|                                                             |
|  +-------------------------------------------------------+  |
|  | Session    | Local Time (IST)   | Track Time (GMT+2)  |  |
|  +------------+--------------------+---------------------+  |
|  | Practice 1 | Fri 14:15          | Fri 10:45           |  |
|  | Practice 2 | Fri 18:30          | Fri 15:00           |  |
|  | Free Prac. | Sat 13:40          | Sat 10:10           |  |
|  | Qualifying | Sat 14:20          | Sat 10:50           |  |
|  | Sprint     | Sat 18:30          | Sat 15:00           |  |
|  | Warm Up    | Sun 13:10          | Sun 09:40           |  |
|  | Main Race  | Sun 17:30          | Sun 14:00           |  |
|  +------------+--------------------+---------------------+  |
|                                                             |
|                                                             |
+-------------------------------------------------------------+
| [ ACTIVE ]             |              |                     |
|  Schedule/Home         |  Standings   |  Rider Data         |
+-------------------------------------------------------------+
```

## Screen 2: Championship Standings Page

> **Layout Strategy:** Form follows function. A clean configuration zone at the top utilizes three simple dropdown fields to filter by Year, Class, and Category, instantly updating the dense results table below.

Plaintext

```
+-------------------------------------------------------------+
|                                                             |
|   CHAMPIONSHIP STANDINGS                                    |
|                                                             |
|   +--------------+   +--------------+   +---------------+   |
|   | Year: 2026 V |   | Class: GP  V |   | Type: Rider V |   |
|   +--------------+   +--------------+   +---------------+   |
|                                                             |
|  +----+------------------+---------------------+----+----+  |
|  | Pos| Rider            | Team                | Pts| Diff|  |
|  +----+------------------+---------------------+----+----+  |
|  | 1  | F. Bagnaia       | Ducati Lenovo Team  | 160| --  |  |
|  | 2  | J. Martin        | Prima Pramac Racing | 145| -15 |  |
|  | 3  | M. Marquez       | Gresini Racing MotoGP| 132| -13 |  |
|  | 4  | E. Bastianini    | Ducati Lenovo Team  | 114| -18 |  |
|  | 5  | M. Vinales       | Aprilia Racing      | 100| -14 |  |
|  +----+------------------+---------------------+----+----+  |
|                                                             |
|                                                             |
+-------------------------------------------------------------+
|                        | [ ACTIVE ]   |                     |
|  Schedule/Home         |  Standings   |  Rider Data         |
+-------------------------------------------------------------+
```

## Screen 3: Rider Data Page

> **Layout Strategy:** A profile layout split into two distinct visual areas. The top half functions as an identity card showing biographical markers (photo, flag, team), while the lower portion handles text layouts like quotes and descriptions.

Plaintext

```
+-------------------------------------------------------------+
|                                                             |
|  +-----------------------+  Rider: Francesco Bagnaia        |
|  |                       |  Country: Italy [Flag]           |
|  |                       |  Team: Ducati Lenovo Team        |
|  |      [ RIDER ]        |  Bike: Desmosedici GP26          |
|  |       PROFILE         |  Number: #1                      |
|  |        IMAGE          |                                  |
|  |                       |  +----------------------------+  |
|  |                       |  | "Go fast, take chances."   |  |
|  +-----------------------+  +----------------------------+  |
|                                                             |
|  BIOGRAPHY / DESCRIPTION                                    |
|  +-------------------------------------------------------+  |
|  | Francesco "Pecco" Bagnaia is an Italian motorcycle    |  |
|  | racer competing in MotoGP for the Ducati Lenovo Team. |  |
|  | Having won consecutive premier class titles, he is    |  |
|  | known for his analytical riding style and precise...  |  |
|  +-------------------------------------------------------+  |
|                                                             |
+-------------------------------------------------------------+
|                        |              | [ ACTIVE ]          |
|  Schedule/Home         |  Standings   |  Rider Data         |
+-------------------------------------------------------------+
```
## Challenges resolved
1. The rider data page shows the list of motogp riders in championship standings order.
2. on mobile we can just have position, rider and points
3. home shows a _summary card_ of the top 3 standings plus next race info — a dashboard, not a full table. Standings gets its own page and nav slot
4. do not drop it. it was mistake.