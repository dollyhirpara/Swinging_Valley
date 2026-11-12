# Swinging Valley: Game Rules & Design Conclusion

Updated 12 Nov 2026 · every number below is the live value in the prototype's `TUNING` object.

## Summary

Swinging Valley is a one-thumb endless swinger: tap a hook to swing, tap the next before your 4-second grip slips, and survive as long as you can. Its core tension is **hang and you get shot, swing fast and you stay hidden**. The day-1 hook is **Grip Gloves**: they unlock after run 1, arrive at 08:00 the next day, and stretch grip from 4 s to 7 s.

Each enemy has one job: **outrun the bugs, dodge the ninjas, hunt the birds**. Birds are the only enemy you can kill; kills pay coins and missions, never energy. Money follows fair-play rules: no offers on day 0, never mid-run, at most one smart offer per session.

| Item | Link |
| --- | --- |
| Play (Ink & Paper) | [dollyhirpara.github.io/Swinging_Valley](https://dollyhirpara.github.io/Swinging_Valley/) |
| Code | [github.com/dollyhirpara/Swinging_Valley](https://github.com/dollyhirpara/Swinging_Valley) |

## Controls and swing

One thumb, three gestures: tap a hook to grab it, tap the next hook to jump to it, tap empty sky to let go. Phones play in landscape; desktop uses the mouse or Space.

| Rule | Value |
| --- | --- |
| Vines | 4–5 per run, 150–215 apart, reshuffled every run; 3 hooks each (high, mid, low) |
| Tap a hook | Grabs it if it is 40–370 units away; each hook has an 80-unit touch area |
| Tap the next hook | Jumps straight to it; the vine reels you in to 78% of the distance |
| Tap empty sky | Let go and fly; a slow release (under 340) is thrown forward at 420 |
| Grab boost | Every grab tops the swing up to 380, even from a dead hang |
| Swing assist | +220/s² for 1.6 s after a new hook, then damping 0.2/s |
| Gentle falls | Catching a hook softens a drop to 300; free fall caps at 640 |
| Physics | Gravity 1400, top speed 900, fixed 1/120 s step |
| Desktop | Click hooks; Space grabs the hook ahead or lets go; G wears a glove; 1 / 2 use bubbles; M mutes |

**Grip.** You hold one hook for 4 s (7 s with Grip Gloves). A new hook or a cliff landing resets it; re-grabbing the same hook does not. The ring around the hero drains jade → gold → red, and the hook shows the same ring. In the last 1.6 s a countdown, sweat drops, a shaking hand and a red rope warn you. At zero you slip and cannot grab for 0.3 s.

**Speed states.** Under 160 while hanging you are an easy target. Above 460 bugs lose track of you. Above 480 the hero glows mint: birds can be knocked out and ninja leaps miss.

## Energy and danger

Energy is health, not a timer: hanging, swinging and standing cost nothing. The run ends when energy hits 0 and you decline (or cannot afford) a revive.

| Source | Effect |
| --- | --- |
| Start | 100 energy (+10 per Max-energy upgrade) |
| Bug spit | −10, then 0.6 s invulnerable |
| Ninja leap | −12, once per leap |
| Fall to the valley floor | −15, respawn on the nearer cliff, 1 s safe |
| Poison cloud | up to −14 per second while inside, scaling down as the cloud fades |
| Energy bolt | +12; one every 9–13 s, max 2 on screen, zigzag between the cliffs |
| Bird knockout | no energy (coins and missions only) |

**Danger ramp.** Bug aim speed and all enemy damage grow by 2.5% for every second survived. The enemy cap starts at 3 and rises by 1 every 15 s up to 8; at least 2 enemies are always present. Spawns come every 2.2–4.2 s, shrinking to 45% of that by 120 s. Low energy (under 30%) pulses a red screen edge.

## Enemies and kills

Each enemy punishes one habit, and only birds can be killed: outrun the bugs, dodge the ninjas, hunt the birds.

| | Spitter bugs | Ninjas | Grumpy birds |
| --- | --- | --- | --- |
| Punishes | Slowing down | Your low point | Lazy routes |
| Where | Walk the valley floor at 60/s | Cling to the inner cliff walls; none in the first 8 s | Patrol between the cliffs at 55/s, at the height of the cliff tops; max 2 |
| Attack | Lock on faster the slower you are; a red aim line and lock-on ring, then a spit at 680 (−10) | While you hang on a vine, it simulates your swing to find your next low point, flashes red 0.35 s, then leaps to meet you there (−12) | Every 4–7 s glows 0.8 s, then releases a poison column (96 wide) that rises to the sky, holds 2.5 s and fades over 3 s; two birds never puff within 1.8 s |
| Your answer | Swing above 460 and they lose track | Be above 480 when it reaches you and the leap misses ("dodged!") | Fly through it above 480 to knock it out |
| Can be killed | No | No | **Yes** |
| Stays | 15–25 s | 14–22 s; after a leap it lands, runs back, climbs and waits 2–3.5 s | 14–22 s |

Spawn mix: 42% bugs, 30% ninjas, 28% birds (a bird becomes a bug when 2 birds are already out).

**Bird kills.** Each knockout pays **15 coins** (×2 in a Treasure Run), with a freeze-frame, screen shake and the bird floating away as a ghost. A 2nd or 3rd bird within 4 s is a combo: ×2 then ×3 (up to 45 coins), shown as a COMBO badge under the timer. Kills never give energy, so survival stays a skill, not a farm. Bird missions: knock out 2 birds today, 5 in one run, 2 in one combo.

## Pickups, bubbles and missions

Treasure is always placed where a swing can reach it, and anything within 85 units drifts into your hands.

| Pickup | Rule |
| --- | --- |
| Coins | 10 (lasts 9 s, 55% of spawns), 25 (6 s, 33%), 60 (3.5 s, 12%); one every 2.2–3.8 s, max 3; 12% appear on a cliff top as a 10 |
| Rubies | 1.5% of spawns (about 1 every 3–4 runs), last 4 s; run 2 always shows one at 14 s |
| Energy bolts | +12 energy (see Energy and danger) |
| Treasure Run | One run a day with 2× coins, switched on from home; an extra one costs 5 rubies |

**Bubbles** open from run 2, as round buttons at the bottom centre (1 use each per run, +1 per Bubble-limit upgrade). DEF blocks all damage for 3 s. INV makes enemies lose you for 6 s and resets bug aim. On the first 2 days DEF is highlighted once when energy drops under 30%, and INV once when a bug is about to fire.

**Daily missions** open from run 2 and show on home. There are 2 regular missions (+20 coins, 1 star) and 1 daily mission (+50 coins and 2 rubies, 2 stars); a finished regular mission is replaced next run, the daily one changes each day. When one completes mid-run, "Mission accomplished" rises above the right cliff.

| Mission pool | Goal |
| --- | --- |
| Knock out 2 grumpy birds | 2 (across the day) |
| Knock out 5 grumpy birds in one run | 5 |
| Knock out 2 birds in one combo | 2 |
| Grab a 60 coin treasure | 1 |
| Grab 6 hooks in a row without landing | 6 |
| Survive 60 seconds | 60 s |
| Grab 3 energy bolts in one run | 3 |
| Dodge 5 bug spits | 5 |
| Collect 150 coins in one run | 150 |
| Survive 40 s without slipping | 40 s |

## First session and the D1 hook: Grip Gloves

The day-1 hook turns the player's own slips into a promise: Grip Gloves unlock at the end of run 1, arrive at 08:00 the next day, and stretch grip from 4 s to 7 s. Nothing is locked while you wait; you can keep playing.

```
Run 1 ends ──► Gloves unlock ──► 08:00 next day ──► DAY 1 ──────────────► Day 2 onward
your slips      countdown starts   local push and     1 glove auto-on        tap glove: 24 h
shown to you    "Remind me"        in-game message    24 h + 3 free          more: rubies, IAP
```

**Day 0, in order.**

1. **Home:** the live valley with the hero swinging, a locked next valley, and a 4 s vs 7 s grip demo.
2. **Run 1:** pure swinging, no meta. Slips teach the grip; the red aim line teaches "keep moving".
3. **End of run 1:** "Slipping off hooks? Get a better grip." The card shows your slips and falls, a side-by-side demo, the arrival time and a live countdown, the notification you will get, and a "Remind me" button.
4. **Run 2:** daily missions and bubbles open, a guaranteed ruby at 14 s, and the first revive offer (coins).
5. **Run 3+:** Treasure Run, shop, skins and the ad chest. Play as long as you like.

| Grip Gloves rule | How it works |
| --- | --- |
| Unlock | When run 1 ends; the countdown starts at once |
| Arrival | The next 08:00 that is at least 6 h away |
| Reminder | Local push at 08:00 in a real build ("Your Grip Gloves are ready! Hold every hook 3 s longer before you slip. Your first day is free.") plus the same message in game; the browser prototype can only notify while open |
| Day 1 | Home shows "Play with gloves"; the first glove is put on automatically for 24 h (forced first use), plus 3 free gloves in the bag |
| Effect | Grip 4 s → 7 s per hook; staying on one vine keeps building your swing, capped at 620 |
| Wearing more | Tap the glove button (bottom centre) during a run or "Wear a glove" on home: 1 glove = 24 h |
| Getting more | 10 rubies each, glove packs (3 for ₹79, 10 for ₹199), Starter Pack, Glove Club |
| Fair play | Base grip is fair without gloves; gloves never block damage |

**Why it works.** It fixes a pain the player just felt, built from their own numbers. It shows exactly what they get (4 s vs 7 s) and exactly when (a live countdown). Day 1 starts with gloves already on, so the first run back is the best run yet.

## Economy and money

The game makes money from gloves, rubies and cosmetics under seven fair-play rules; every purchase in the prototype is simulated.

**Fair-play rules.**

1. No offers on day 0.
2. Never interrupt a run; offers live on the results screen and in the shop.
3. At most one smart offer per session, with the reason shown.
4. Feel it free first: gloves are free on day 1 before any glove offer.
5. Everything that affects play can be earned, just slower.
6. No lives or energy timers; you can always play.
7. Revives stop at 3 per run, so spending in a run has a ceiling.

| Currency | Earn | Spend |
| --- | --- | --- |
| Coins (soft) | Treasure, bird knockouts (15, combo up to 45), missions, 2× Treasure Run, ad "double this run's coins" | Max energy (30, 60, 100, 150, 210, 280, then +80), bubble limit (150, 300, 500), skins (120–400), new valleys (800, 1500, full game), 1st revive (100) |
| Rubies (hard, rare) | Rare drop (about 1 per 3–4 runs), 2 per daily mission, daily ad chest (2), IAP | Grip Glove (10), 2nd revive (5), 3rd revive (15), extra Treasure Run (5), Fire trail (40) |

**Revive ladder (per run).** 1st: 100 coins → 2nd: 5 rubies → 3rd: 15 rubies → no 4th. A revive gives 60 energy and 2 s of safety; you have 6 s to decide. Glove Club makes the first revive of each day free.

| Store item | Price | Contents |
| --- | --- | --- |
| Starter Pack | ₹49, once | 5 gloves + 30 rubies + Golden Langur skin; offered once from day 1 when free gloves run low |
| Ruby packs | ₹29 / 79 / 199 / 499 / 999 | 10 / 30 / 90 / 250 / 550 rubies (+10% to +40% bonus on the big ones) |
| Glove packs | ₹79 / ₹199 | 3 / 10 gloves |
| Glove Club | ₹149 / month | Gloves always on, 5 rubies a day, 1 free revive a day, +1 Treasure Run a day |
| Cosmetic trails | ₹49 or 40 rubies | Holi, Diwali, Fire; zero power |
| Valley Pass | ₹199 / season | 30 tiers for playing, exclusive skin (full game, from day 7) |
| Rewarded ads | Free | Double a run's coins; daily ruby chest; always optional |

**Smart offer.** The player model picks at most one per session from day 1: gloves low → Starter Pack; could not afford a revive → 30 rubies; 3+ slips with no gloves → 3 gloves.

## Metagame, launch metrics and assumptions

Every layer runs on its own clock, so something is always close to finishing; power stays small (energy and grip only).

| Clock | What finishes |
| --- | --- |
| Every run | Coins and rare rubies, bird hunts and combos, a new best time |
| Every day | 3 missions (the daily one pays rubies), one 2× Treasure Run, the ad ruby chest, glove days |
| Every week | Skins and trails, max energy and bubble upgrades, the Valley Pass opens on day 7 |
| Every month | A new 30-tier Valley Pass season, new valleys (Monsoon Valley, Night Bazaar), Glove Club perks |
| Long term | Diwali and Holi events, friend and city leaderboards, new enemies and vine layouts |

| Soft-launch metric | Target |
| --- | --- |
| D1 retention | ≥ 40% |
| D1 returners who play with gloves | ≥ 70% |
| D7 retention | ≥ 15% |
| Payer conversion by D7 | ≥ 2% |

**Kill or pivot.** Swinging is not fun without the meta → kill. Gloves lift D1 by under 5 points vs a plain shop → change the hook. Slips are the top quit reason → raise base grip. Payers under 1% after the Starter Pack → rework offers, not prices.

**Assumptions.** India-first mobile casual audience, landscape play, prices in INR. Targets are pre-test estimates. Valley Pass, new valleys and leaderboards are designed, not built. The prototype's reviewer button "skip to tomorrow" fakes the overnight wait; "Reset all data" returns to day 0.

**Built with AI.** Code, art and audio were generated with Claude (Claude Code) from these rules; Playwright bots and phone playtests checked every change. In the game, ninjas predict your swing, a coach reads each run and gives one tip, and the same player model picks the one smart offer.
