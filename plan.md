**Sabannah\'s Flower Shop**

*Game Design & Specification Document*

**Overview**

Sabannah\'s Flower Shop is a single-character, day-cycle game about a
young woman running a small flower shop. The surface framing is a
wholesome business sim --- take orders, collect flowers, build bouquets,
keep customers happy. The hidden thesis is learning to take care of
yourself.

The game\'s opening lie is: complete your orders. The player discovers
that overworking depletes the character. That discovery is the game.

*The game is secretly about attunement --- learning to read subtle
internal cues mirrors the real skill of self-awareness. The ending is a
reward for learning to listen, not a reward for efficiency.*

**Structure**

-   5 days total (levels)

-   Each day is exactly 60 seconds

-   A customer is already waiting at the start of every day

-   Before each day, a Day Brief screen shows the order goal and
    starting mood

-   Failing the order minimum or reaching acid reflux mood ends the game

**Screen Flow**

Intro → Day Brief → Game → End of Day → Day Brief (next day) → \...

Game Over (failed orders or wilted) \| Win (all 5 days complete)

**Level Progression**

All levels run 60 seconds. Customer patience is shown in seconds queue
wait time.

  -------------------------------------------------------------------------------------------
  **Day**   **Label**   **Min      **3-Flower   **Patience**   **Spawn   **Self-Care Loot**
                        Orders**   %**                         Gap**     
  --------- ----------- ---------- ------------ -------------- --------- --------------------
  1         Opening Day 8          0%           16s            3--4.5s   Scarce (egg 8s /
                                                                         water 4s)

  2         Gettin the  6          30%          16s            2.5--4s   Normal
            Hang of It

  3         Tough Day   6          50%          16s            2--3.5s   Normal

  4         Peak Season 7          65%          16s            1.8--3s   Normal (friend sick)

  5         Full Bloom  7          75%          18s            2--3.5s   Generous (egg 2s /
                                                                         water 0.6s)
  -------------------------------------------------------------------------------------------

**Day-by-Day Difficulty Breakdown**

  ---------------------------------------------------------------------------------------------------------------------------------------------------------
  **Day**   **Label**       **Quota**   **Order Mix**              **Spawn Gap**   **Self-Care Loot**   **Key Difficulty**
  --------- --------------- ----------- -------------------------- --------------- -------------------- ---------------------------------------------------------
  1         Opening Day     8 orders    All 2-flower               3--4.5s         Scarce               Highest quota in the game. Simple orders but relentless
                                                                                                        grind burns energy fast. Loot is scarce so players who
                                                                                                        skip self-care arrive at Day 2 already depleted.

  2         Gettin the      6 orders    30% 3-flower               2.5--4s         Normal               First 3-flower orders introduce complexity. Self-care
            Your Feet                                                                                    habits matter here — Day 3 punishes those who don't.

  3         Tough Day    6 orders    50% 3-flower,              2--3.5s         Normal               Two simultaneous true crime items (0.8--2s gap each).
                                        ~25% 4-flower                                                   Complexity and spawn rate both jump. Hardest day for
                                                                                                        self-control.

  4         Peak Season     7 orders    65% 3-flower,              1.8--3s         Normal               Friend is sick — pressing SPACE costs −1 energy. Friend
                                        ~25% 4-flower                                                   moves at 45% speed with a red glow. Avoid them.

  5         Full Bloom      7 orders    75% 3-flower,              2--3.5s         Generous             High quota and complex orders, but loot is abundant
                                        ~25% 4-flower                                                   (egg every 2s, water every 0.6s). A reward for players
                                                                                                        who learned to self-care. Arrives depleted = very hard.
  ---------------------------------------------------------------------------------------------------------------------------------------------------------

**Day Brief Messages**

Day 1: \"First day on the job! Time to prove yourself! Complete 8 orders.\"

Day 2: \"Damn, that shit was kinda stressful. Just complete 6 orders this round.\"

Day 3: \"Working is exhausting. You might be more drawn to True Crime, but RESIST!\"

Day 4: \"The shop is picking up & customers want bigger bouquets? BTW, your friend is sick today, so make sure to avoid them.\"

Day 5: \"Final Day, but you've been finding better balance. Pace yourself, stay
fuelled, and finish strong.\"

**Energy System**

The player has 10 energy points displayed as 10 circles in the HUD. Pink
circles = healthy. Red circles = below 5 (low energy). Empty rings =
depleted. Every work action costs energy. Self-care restores it.

  -----------------------------------------------------------------------
  **Action**                **Energy   **Notes**
                            Change**   
  ------------------------- ---------- ----------------------------------
  Accept order at counter   −0.5       Cost on pressing SPACE at counter

  Collect one flower        −0.33      Per flower picked up

  Deliver bouquet (last     −0.33      Automatic on completion
  flower)                              

  2-flower order reward     +0.25      Net per order: −0.92

  3-flower order reward     +0.35      Net per order: −1.15

  4-flower order reward     +0.50      Net per order: −1.33

  Wrong flower penalty      −0.1       Pressing SPACE on wrong color

  Order timer expiry        −0.5       Customer leaves unfulfilled

  Eat egg 🥚                +2.0       2-second eating pause

  Drink water 💧            +1.0       Instant, no pause

  Chat with friend 🫶       +0.5       First 4 times per day

  Over-chat with friend     −0.5       5th+ chat in same day

  Nap 🛏️                    +3.0       5 seconds locked

  Walk into true crime 🕵🏻‍♀️🔍 −3.0       Auto-drains on contact, no SPACE
                                       needed
  -----------------------------------------------------------------------

Core principle: Work is always a net energy drain. Self-care is the only
path to sustained energy. There is no way to stay energized through
orders alone.

**Speed System**

Avatar speed scales linearly with current energy:

energy_fraction = 0.35 + (current_energy / 10) × 0.65

speed = BASE_SPEED × mood_modifier × boost × energy_fraction

-   Full energy (10) → maximum speed

-   Zero energy → 35% of maximum speed

-   Additional 0.65× penalty when mood is meh or below AND energy \< 5

The player feels self-care immediately --- eating or napping makes them
visibly faster.

**Mood System**

Mood is a slow-moving wellbeing score (0--100) that only changes at end
of day. It does not fluctuate mid-round. Starting wellbeing: 70 (fine).

  ---------------------------------------------------------------------------
  **State**   **Name**       **Emoji**   **Speed Mod**  **Wellbeing Range**
  ----------- -------------- ----------- -------------- ---------------------
  5           WEEEE          🌸          1.0×           80--100

  4           fine           😊          0.9×           60--79

  3           meh            😐          0.75×          40--59

  2           wilting        😔          0.55×          20--39

  1           acid reflux    🥀          0.35×          5--19
  ---------------------------------------------------------------------------

**End-of-Day Mood Calculation**

Self-care ratio = self-care actions ÷ order-accept actions

shouldDrop = ended below 5 energy OR self-care ratio \< 30%

-   Failed order minimum → wellbeing −24 (two levels down)

-   shouldDrop → wellbeing −20 (one level down)

-   Healthy and balanced → wellbeing +20 (one level up)

**Energy Carry-Over**

Energy always persists exactly to the next day — no reset, no partial
recovery bonus:

next_start_energy = end_energy

Ending any day depleted means starting the next day depleted.

**Order Flow**

  -----------------------------------------------------------------------
  **Step**         **Detail**
  ---------------- ------------------------------------------------------
  1\. Customer     Arrives off-screen right, walks to queue
  spawns           

  2\. Order hidden Displayed as \"? ?\" until accepted

  3\. Accept at    SPACE near counter → −0.5 energy, 10s timer starts
  counter          

  4\. Flowers      Customer\'s required flowers shown on their card
  revealed         

  5\. Collect      Loot spawns on floor. SPACE near flower → −0.33 energy
  flowers          each

  6\. Wrong flower −0.1 energy, flower not collected

  7\. Deliver      Last flower auto-delivers → −0.33 energy + reward

  8\. Customer     Walks left, speech bubble shows their feedback
  exits            

  Timer expiry     −0.5 energy, customer leaves, counts as lost order
  -----------------------------------------------------------------------

Order timer: 10 seconds on all days. Bouquet sizes: 2, 3, or 4 flowers.

Flower spawn rate: every 600–1000ms (0.6–1 second). Only flowers needed
for the current active order are spawned, and only while an order is
accepted. Each flower lives 3.2–4 seconds before disappearing.

-   4-flower orders appear on Days 3--5 at \~25% of the 3-flower pool

-   Day 1: all 2-flower orders (no complexity, intentional grind trap)

**Customers**

Up to 4 customers can be in the shop simultaneously. Each customer is
assigned a random name, personality, color, and activity (e.g. \"needs
flowers for a date\").

**Customer Personalities**

  ------------------------------------------------------------------------------------
  **Name**   **Color**   **Patience**   **Happy Feedback         **Sad Feedback
                                        (samples)**              (samples)**
  ---------- ----------- -------------- ------------------------------------------------ ------------------------------------------------
  Elise      Pink        Never leaves
                         (patience=9999,
                         never impatient)"these are the most beautiful flowers i've        "plz take care of yourself sav" /
                                        seen" / "you're doing great sav" /               "this is probably cause you didn't eat" /
                                        "GO GO GO GO" / "🥹🥹🥹🥹" /                     "rest up"
                                        "you're doing a great job" / "SO PRETTY"

  Nathan     Blue        Most impatient "Thank you for doing everything exactly as I      "Stupid big boobed bitch!" /
                                        expected in the exact way I wanted" /            "Oh so are you like crashing out rn or" /
                                        "It's giving… you're just better than            "No that's fine never mind"
                                        everyone???" /
                                        "I see the mental health is working with us today"

  Ellen      Purple      Regular        "sav is so guai" /                               "aw man no flowers 4 me" /
                                        "beautiful bouquet im gonna bite it" /           "they die anyways" /
                                        "A+ job wow" / "KILLING IT" /                    "wahhhhh :(" /
                                        "Flower so good I wanna give Sav a big hug"      "*spits on sav*" /
                                                                                         "*activates menace*"


  Erica      Green       Regular        "WOWWWWW" / "so cool" /                          "blehhhhh" /
                                        "my date is gonna love these"                    "aw man no flowers" /
                                                                                         "sad i can't give these to my date"

  Michael    Yellow      Regular        "im gonna use these to ask out a cute girl"      "maybe next time..."
  -----------------------------------------------------------------------------------------------------------------------

Feedback phrases cycle sequentially (not randomly) through each personality's list, looping back after the last phrase. Feedback appears as a speech bubble on the customer as they walk off screen. Happy = pink border. Sad = red border. Feedback is also logged in the end-of-day Yelp Reviews panel.

**Customer Activities**

Each customer is randomly assigned one of: a date, his/her mom (pronoun
matched to character gender), a birthday present, romance, my friend,
himself/herself (pronoun matched to character gender), an important work
thing.

**Spawn Pool (Weighted)**

Nathan and Ellen appear more frequently. Elise is rare. Pool: elise,
nathan, ellen, ellen, erica, erica, michael, michael, nathan.

**Self-Care Items**

  ---------------------------------------------------------------------------------------
  **Item**   **Emoji**   **Effect**   **Timing**   **Notes**
  ---------- ----------- ------------ ------------ --------------------------------------
  Egg        🥚          +2 energy    2s eating    Scarce on Day 1 (8s gap). Normal: 5s
                                      pause        gap. Generous Day 5: 2s gap

  Water      💧          +1 energy    Instant      Scarce on Day 1 (4s gap). Normal: 1.5s
                                                   gap. Day 5: 0.6s gap

  Friend     🫶          +0.25 energy No pause     Max 4 positive chats. 5th+ drains
                                                   −0.5. NOT on Day 4 (friend sick)

  Nap        🛏️          +3 energy    5s locked    Bed in bottom-left corner. Progress
                                                   bar during nap

  True Crime 🕵🏻‍♀️          −3 energy    Auto on      Appears every 1.5--4s, lingers 4s. No
  (trap)                              contact      SPACE needed --- just walking into it
                                                   costs energy

  Journal    📓          +5 energy    SPACE to     Only appears if player enters day in
  (rescue)                            collect      wilting mood (state 2), Days 3+ only.
                                                   Spawns once in lower-right of floor at
                                                   a random time within the first 30s.
                                                   Lingers 7s then disappears.
  ---------------------------------------------------------------------------------------

Self-care items glow teal/green and have a 56px container. True crime
glows red. Flower loot only glows pink when the player is nearby. Items
spawn across a grid to avoid clumping.

**Friend Chat System**

-   Chats 1--4: +0.25 energy, positive message, speed boost

-   Chat 5+: −0.25 energy, amber speech bubble, redirects player to
    other self-care

-   4-dot counter above friend NPC shows remaining positive chats

-   Day 4: Friend appears but is sick. Touching them automatically costs
    −1 energy (2s cooldown between drains). Friend has a red glow and
    moves at 75% normal speed (25% slower). On contact or SPACE: "I'm
    sick! Please avoid me." No chat counter shown.

-   Friend photo head cycles by day: Day 1 Ellen, Day 2 Michael, Day 3
    Nathan, Day 4 Erica, Day 5 Elise

**Friend Messages**

Normal chat (chats 1--4, energy above low threshold):

-   "LOVE U SABANNAH 💛"
-   "Damn you killin it"
-   "Did you eat today or rest?"
-   "Such a great lil worker"
-   "Drink some water. 💧"
-   "Maybe take a little nap? It might help 😴"

Low energy chat (player below 5 energy):

-   "Hey... you look tired. Go take a nap! 😴"
-   "You should really rest. The bed is right there! 🛏️"
-   "Please nap — you're running low on energy 💤"
-   "I'm serious, go sleep. You need it! 😴"
-   "Your energy is low, go eat something!"

Over-limit chat (chat 5+, −0.5 energy, amber bubble):

-   "I can't talk to you all day... take care of yourself! 🌿"
-   "You need more than just me — eat something! 🍓"
-   "Go drink some water, seriously. 💧"
-   "I love you but please take a nap! 🛏️"
-   "You're leaning on me too much. Rest! 😅"

**Lose Conditions**

1\. Failed Order Minimum

-   Day 1: No retry. Game over immediately.

-   Days 2--5: One retry per day. Retry starts at carry-over energy, not
    full.

-   Second failure on the same day = game over.

2\. Acid Reflux

-   Wellbeing drops to 10 or below.

-   No retry. Game ends immediately.

**Win Condition**

Complete all 5 days without triggering a lose condition. Win screen
message:

*\"Sabannah\'s thriving. Five days of running your shop --- and you took
care of yourself through all of it.\"*

**End-of-Day Screen**

Two-column layout:

Left column --- Yelp Reviews: Scrolling movie-credits panel showing all
customer feedback from the day. Happy reviews in green, sad reviews in
red. Counts positive and negative reviews separately.

Right column --- Stats:

-   Combined card (mood bar + warnings + next-day preview): horizontal
    mood temperature bar with reversed gradient (acid reflux left →
    WEEEE right); warning if low energy or low self-care ratio; mood
    improvement banner if mood went up; next-day preview (mood chip +
    energy level + arrow + avatar sprite)

-   Three side-by-side stat boxes: completed orders (X/Y),
    incomplete/lost orders, and self-care counts (chats, eggs, water,
    naps)

**HUD Layout**

  -----------------------------------------------------------------------
  **Position**     **Content**
  ---------------- ------------------------------------------------------
  Top-left         Mood pill: character sprite, Day X/5, level label,
                   mood emoji + name + wellbeing %

  Top-center       10 energy circles (pink = healthy, red = low, grey
                   ring = empty) + wellbeing % bar

  Top-right        Customers in shop (purple) · Orders done/required ·
                   Timer · ⚙️ Settings

  Bottom-left      Nap button with +3⚡ label and progress bar while
                   sleeping

  Below avatar     Energy warnings: \"⚡ Low energy!\", \"😵 Exhausted\",
                   \"😐 Slowing down\" --- below avatar to avoid
                   overlapping bouquet

  Counter          \"\[Name\] needs flowers for \[activity\]\" + purple
                   SPACE-to-accept badge
  -----------------------------------------------------------------------

**Settings Menu (⚙️)**

-   Pause / Resume --- also toggled by ESC. Dims and blurs game world.

-   Restart game --- resets to Day 1 intro.

**Technical Stack**

-   Framework: React (JSX, hooks --- useState, useEffect, useRef,
    useCallback)

-   Rendering: CSS absolute positioning + inline SVG for characters and
    NPCs

-   Game loop: setInterval at 16ms (\~60fps). Added error handling
    (try/catch) in game loop to prevent crashes from infinite loops or
    memory leaks.

-   Input: keydown/keyup (arrow keys, spacebar, ESC)

-   Canvas: 900 × 620px fixed

-   No external dependencies beyond React

**Future Iteration --- Dehydration & Hunger Alerts**

Not yet built. Planned for after players have internalized the core
loop.

Water and egg loot move from floor to HUD status icons. Time-based
alerts replace them:

-   Dehydration: every 20s alert appears. Drink within 10s or −3 energy.

-   Hunger: every 50s alert appears. Eat within 10s or −5 energy.

Rationale: Physiological pressure deepens the game\'s thesis but is too
complex for new players. Introduced later once the work/self-care
balance is internalized.

**Custom Character Art**

All 5 named customers use full photo replacements (`CUST_PHOTOS` map).
Stick body removed for all of them. Photos: `photos/nathan.jpeg`,
`photos/ellen.png`, `photos/elise.png`, `photos/erica.png`,
`photos/michael.png`. Queue: 30×48px `<img>`. Walking: 34×56 SVG
`<image>`. Unnamed/fallback customers still use stick figures.

-   Nathan, Ellen, Elise, Erica, Michael: entire RPG replaced with photo
    in both queue and walking states.

Sav avatar heads are replaced with photos per mood state. Photo heads
are large/bobblehead-sized (r=16, 32×32 SVG units vs body width 36).
Flower petals only shown in state 5 (WEEEE). Stick body always retained.

  -----------------------------------------------------------------------
  **State**   **Name**       **Head**
  ----------- -------------- ---------------------------------------------
  5           WEEEE          `photos/sav_wee.jpeg` + flower petals

  4           fine           `photos/sav_fine.png`

  3           meh            `photos/sav_meh.png`

  2           wilting        `photos/sav_wilting.png`

  1           acid reflux    `photos/sav_wilting.png`
  -----------------------------------------------------------------------

-   Impatient customers: all RPGs shake horizontally
    (`cust-shake` keyframe, 0.45s loop) when their patience state is
    \"impatient\".

*Last updated: v14 · Sabannah's Flower Shop*
