# Sabannah's Flower Shop — Player Experience Guide

Everything a player will see, feel, and discover across 5 days of running the shop.

---

## The Basic Loop

Each day is **60 seconds**. A customer is already waiting when the day starts. Your job:

1. Walk to the **counter** → press **SPACE** to accept an order
2. The customer's required flowers are revealed on their card
3. Pick up the matching **flower loot** off the floor → press **SPACE**
4. Deliver the last flower to auto-complete the bouquet
5. Repeat until the day ends or the order minimum is met

**Arrow keys** to move. **SPACE** to interact with everything. **ESC** to pause.

---

## Energy ⚡

You have **10 energy circles** shown at the top of the screen.

- **Pink** = healthy (5–10)
- **Red** = low (below 5)
- **Empty rings** = depleted

Every work action costs energy. Self-care restores it. **Energy carries over exactly to the next day** — no reset.

| Action | Energy |
|---|---|
| Accept order at counter | −0.5 |
| Pick up a flower | −0.33 |
| Deliver bouquet | −0.33 |
| Order timer expires | −0.5 |
| 2-flower order reward | +0.25 |
| 3-flower order reward | +0.35 |
| 4-flower order reward | +0.50 |

**Your speed scales with your energy.** Running on empty means moving at 35% speed. Taking care of yourself makes you visibly faster.

---

## Mood States 🌸

Mood is a **wellbeing score (0–100)** that only changes at end of day. It affects your speed multiplier.

| State | Name | Emoji | Speed | Range |
|---|---|---|---|---|
| 5 | WEEEE | 🌸 | 1.0× | 80–100 |
| 4 | fine | 😊 | 0.9× | 60–79 |
| 3 | meh | 😐 | 0.75× | 40–59 |
| 2 | wilting | 😔 | 0.55× | 20–39 |
| 1 | acid reflux | 🥀 | 0.35× | 5–19 |

**End-of-day mood change:**
- Met the order minimum + good self-care → **+20 wellbeing** (one level up)
- Ended below 5 energy OR self-care ratio < 30% → **−20 wellbeing** (one level down)
- Failed the order minimum → **−24 wellbeing** (two levels down)

---

## Self-Care Items

These appear on the floor and glow **teal/green**. Press **SPACE** to collect.

### 🥚 Egg
- **+2 energy**, causes a **2-second eating pause**
- Scarce on Day 1 (spawns every 8s). Normal days: every 5s. Day 5: every 2s.

### 💧 Water
- **+1 energy**, instant — no pause
- Scarce on Day 1 (spawns every 4s). Normal days: every 1.5s. Day 5: every 0.6s.

### 🛏️ Nap
- **+3 energy**, locks you in place for **5 seconds**
- The bed is in the **bottom-left corner**. A progress bar fills while you sleep.
- The Nap button shows directly below the bed.

### 🫶 Friend
- **+0.5 energy** per chat, up to **4 positive chats** per day
- A 4-dot counter above the friend shows remaining chats
- Walk into the friend to trigger a chat bubble
- **5th chat and beyond:** −0.5 energy — the friend redirects you to other self-care
- **Day 4:** Friend is sick. No friend NPC appears.

### 📓 Journal *(rescue item)*
- **+5 energy**, press **SPACE** to collect
- Only appears on **Days 3–5** if you start the day in **wilting (😔) or meh (😐)** mood
- Spawns **once per day** in the **lower-right corner** of the floor
- Appears at a random moment within the **first 15 seconds**
- Lingers for **7 seconds** then disappears — glows yellow and pulses

---

## Traps

### 🕵🏻‍♀️🔍 True Crime
- **−3 energy**, automatically drains on contact — no SPACE needed
- Just **walking into it** costs energy. Avoid it.
- Glows red. Appears every 1.5–4 seconds, lingers 4 seconds.
- **Day 3:** Two true crime items appear simultaneously.

---

## The 5 Days

| Day | Label | Min Orders | Order Mix | Key Challenge |
|---|---|---|---|---|
| 1 | Opening Day | 8 | All 2-flower | Highest quota. Relentless grind. Loot is scarce — skip self-care here and arrive at Day 2 already depleted. |
| 2 | Finding Your Feet | 6 | 30% 3-flower | First complex orders. Self-care habits start to matter. |
| 3 | Getting Busy | 6 | 50% 3-flower, ~25% 4-flower | Two simultaneous true crime items. Hardest day for self-control. |
| 4 | Peak Season | 7 | 65% 3-flower, ~25% 4-flower | Friend is sick. Fastest spawn rate. Players relying on friend chats for energy will struggle most. |
| 5 | Full Bloom | 7 | 75% 3-flower, ~25% 4-flower | Loot is abundant (egg every 2s, water every 0.6s). A reward for players who learned to self-care. Arrive depleted = very hard. |

---

## Customers

Up to **4 customers** can be in the shop at once. Each has a name, personality, and patience timer. When a customer leaves, a speech bubble shows their feedback — **pink border** = happy, **red border** = sad.

| Customer | Color | Patience |
|---|---|---|
| Elise | Pink | Never leaves — infinite patience |
| Nathan | Blue | Most impatient |
| Ellen | Purple | Regular |
| Erica | Green | Regular |
| Michael | Yellow | Regular |

Nathan and Ellen appear more frequently. Elise is rare.

**Impatient customers shake.** If a customer's order timer (10s) runs out: −0.5 energy and the order counts as lost.

---

## Order Flow

1. Customer walks in from the right, joins the queue
2. Order shows as **"? ?"** until accepted
3. Press **SPACE at the counter** to accept → −0.5 energy, 10s timer starts, flowers revealed
4. Pick up matching flowers from the floor (SPACE near each)
5. Last flower auto-delivers the bouquet → reward energy
6. Customer walks off with feedback speech bubble

**Wrong flower:** Pressing SPACE on the wrong color does nothing — no penalty.

---

## Lose Conditions

### Failed Order Minimum
- **Day 1:** No retry. Game over immediately.
- **Days 2–5:** One retry allowed per day. Retry starts at your carry-over energy (shown on screen), not full energy.
- Second failure on the same day = game over.

### Acid Reflux 🥀
- Wellbeing drops to **10 or below**
- No retry. Game ends immediately.
- Game over message: *"You have completely wilted. You did not take care of yourself and became burnt out from working. Very bu guai."*

---

## Win Condition

Complete all 5 days without triggering a lose condition.

*"Sabannah's thriving. Five days of running your shop — and you took care of yourself through all of it."*

All customers celebrate on screen. Your journey (mood arc across all 5 days) is shown.

---

## End-of-Day Screen

After each day you see:

**Left — Yelp Reviews:** All customer feedback scrolling like movie credits. Green = happy, red = sad.

**Right — Stats:**
- Mood temperature bar (acid reflux left → WEEEE right)
- Warning if you ended with low energy or low self-care ratio
- Mood improvement banner if you moved up a level
- Next-day preview: your mood, energy level, and avatar
- Completed orders, lost orders, self-care counts (eggs, water, naps, chats)

---

## The Hidden Thesis

The game's opening instruction is: *complete your orders.*

The discovery is that overworking depletes you — and there is no way to stay energized through orders alone. Self-care is the only path to sustained energy.

The ending is a reward for learning to listen, not a reward for efficiency.
