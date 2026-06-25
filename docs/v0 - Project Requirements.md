# Version 0:
## Goal
I am building a MotoGP application that shows the current championship standings of classes MotoGP, Moto2, Moto3 and also the previous championship standings. The championship standings of riders, constructors and teams. It shows the points scored by each candidate and difference against the next candidate along with a picture. It would also be better to include these in the future,
1. live timing sessions
2. other motorsports
3. analysis dashboard
4. a discussion section
5. also a prediction algorithm for motogp fantasy team and motogp predictor
6. a session schedule with local and remote times
7. a rider description page
8. calendar
9. a motogp stream
## Why it matters
The purpose of this project was mainly for my portfolio showcase, but if it gains traction i will modify this according to the users requests. This solves the cluttering the official motogp.com application already has. this shows only the results and standings of candidates. It should have a clean ui with consistent and reliable functionality. The main purpose is to remove clutter and simplify the application for better user experience.
## Tasks
### Problem framing
1. The official motogp.com site/webapp is very cluttered with news and unseen glimpses, behind the paddock and stuff like tickets all in one place. This is definitely not good for the average user.
2. I just wish there was a site with good ui and easy to navigate site where i can see where i am and where to look.
3. First, i will build it as a result and standings, in the next iterations i will make it a statistics, fan knowledge and a live timing product. The main goal is to make a standings and result with clean ui.
### Competitive Audit
1. **motogp.com** - Lot of information for technically apt users. Has all historical data. Has a huge database of unseen footages and videos for fans. Ticket booking to experience motogp in the tracks and a videopass that allows users to buy and stream the entire motogp for the year. Has interesting things about riders. It includes motogp fantasy and motogp predictor which is a fun way to interact with the other fans of the sport. A calendar that shows the race dates. Live timing of all the sessions. Visually the webapp is hard to navigate and feels cluttered. There seems to be no animations in this. It has like a lot of repeated segments in the site. The site feels boring and out of date.
2. **mototiming.live** - The main page shows the schedule of the next GP with both local times and remote times. It has a very clean and readable ui. It shows the standings and historical standings of motogp championships. It shows the points scored and the difference in points of the riders in the main page. The superior feature is the fast and immediate update of live timing in every sessions including practice(not sure). It has statistics and comparison charts of riders and bikes in races. It has a fetured merch page. A section to watch motogp free(not sure about the legality).  It contains trends of the riders over the span of the championship standings. Description of riders. A comparison page. It includes all classes of the motogp. It also has a detailed standing chart. The riders and manufacturers and teams are colour coded accordingly. This is something what i want to replicate. Still the developer shows live timing and schedule in the main page, which seems a bit off to me, people who have the time to see live timing would instead stream the entire race(atleast in my mind). So i want to prioritize championship standings in the home page. 
3. **app.mototiming.com** - This has a clean github like color coded UI. It looks like it is specifically made for hardcore fans due to its technical nature. It has separate menu pages for schedule, live sessions, grid positions, results, standings. The schedule gives timing in the remote times. It also has the motogp calendar. It also is visually good but takes longer to load. It contains historical data of the championship standings. This looks visually good but not appealing for common audience.
### Scope constraint
1. I can spend like 4 hours tops everyday.
2. No launch date, i will keep expanding as i see this as a personal project.
3. good with html css and a little it of js. other than that continuous learning.
### Success definition
1. A better UI and experience for a normal user or a new MotoGP fan.
2. I will use this project for learning and portfolio building.
3. A reliable and stable and consistent motogp championship standings.
## Deliverables
1. Project vision statement
2. Competitive audit of competitors
3. Skills and time audit
4. Feature priority list
5. What this is not
### Feature priority list
1. Championship standings
2. Historical standings
3. Schedule with local and remote times
### What this is not
This is not supposed to be an application for technically well versed people. It is not to attract already fans of motogp franchise.
## Questions
1. Historical fans reference
2. No. I don't think they allow to use their data freely though.
3. A good ui but badly placed elements.
4. The clutteredness of the entire site. It has everything at one place.
5. I want to work with real time data but i can start with historical/simulated data.
## Before version 1
### What this is not
 not for fans who want _everything_ — telemetry, paddock gossip, ticket booking. You want fans who just want **standings and results, fast and clean.** That's a different statement
### Data source
1. **Ergast API** - This shows data related to F1 not MotoGP. Will be useful later. depracated in 2024, should move to **jolpica API**. 
2. **mototiming.live** - https://mototiming.live/api/stats/2026/MotoGP this is where it seems mototiming is getting its data from. it is blocked for me. wss://ws.mototiming.live/app/y9xhaf9nqjzcwykoupwc?protocol=7&client=js&version=8.4.0&flash=false don't know what this is about.
3. **Official MotoGP API** - https://github.com/robschmitt/MotoGP-API this seems reliable. but have to check if this will really work
   https://www.reddit.com/r/motogp/comments/14bsw39/official_motogp_api_free/ need to read this reddit thread again
4. **StrungSafe** - https://github.com/StrungSafe/MotoGP-API need to look into this being developed by a single person for his own work
5. **RacingMike** - https://github.com/micheleberardi/racingmike_motogp_import an API developed by michael to take data from public endpoints. not sure if still usable.
   https://api.micheleberardi.com/swagger/
6. **Wikipedia** - wiki data not suitable for live timings also data must be cleaned. Data of riders history and free to use.
7. **Own** - can build my own web scraper and aggregater but have to learn about it first.
### Homepage priority
Championship standings
### Questions
1. mototiming.live, it is very colorful and user friendly
2. github.com, react.dev, theodinproject.com
3. pure visual preference
# Version 0 — Closed

**Confirmed scope for Version 1:**

- Championship standings — riders, teams, constructors — across MotoGP, Moto2, Moto3
- Historical standings navigation
- Rider profile pages

**Confirmed constraints:**

- Solo developer, ~4 hours/day
- No hard launch date but Version 1 has a defined "done" condition
- Data source to be confirmed before architecture begins
- Clean UI for normal fans and newcomers — not a power-user tool

**Confirmed data strategy:**

- Investigate robschmitt and RacingMike endpoints first
- Backend acts as a proxy layer so data source is swappable
- Slightly delayed data is acceptable for standings