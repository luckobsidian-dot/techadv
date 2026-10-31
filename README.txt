Tech Adventure v0.17

Open project.godot in Godot 4.3.

v0.17 - Worlds:
- Cheaper unlocks in Zokia factory: Motherboard 5,000 coins (was 25,000), Screen 35,000 (was 100,000).
- New globe button in the top bar (between the gems and the gear) opens the Worlds window.
- World 1 is now called "Zokia factory" (this is the shop you already had; old saves carry over into it).
- World 2 is "Zamzung": same 30 coin start, but 5 items per phone (Case Maker, Chipset, Screen, Battery, Camera), much bigger money (a case starts at 8 coins, a camera at 1,600) and much bigger costs. It has its own lavender look and its own bench layout.
- To enter Zamzung you must pass the "techadvv" gate in Zokia factory (also holding 100,000 coins, WORLD_ENTRY_COINS; every requirement shows as have/goal, e.g. 0/1): Case Maker, Motherboard and Screen all at level 23 (WORLD_ENTRY_LEVEL in main.gd) and all 6 upgrades owned. The Worlds window shows a checklist, and the globe button gets a red dot when you can enter. Once you have entered, you can travel between the worlds for free.
- Each world keeps its own shop (coins, benches, upgrades, offline earnings use the world you left from). Gems, quests, stats, the extra worker and settings are shared.
- Zamzung coins count 1/10 toward the daily "Earn coins" quests, so the bigger numbers can't be used to farm gems.
- All world numbers (names, profits, costs, craft times, upgrade prices) are in the WORLDS table near the top of main.gd, so they are easy to tune.
- Reset progress wipes both worlds.

v0.16 - Extra worker + daily quests:
- STORE (green + button, now a gem shop): hire a second worker for 20 gems (WORKER2_GEM_COST in main.gd). The two workers share each order - the parts are split between them (the second one is purple with a yellow shirt). The + button shows a red dot when you can afford it. Offline rewards account for the second worker.
- DAILY QUESTS: the Quests window now has two tabs, Daily and Milestones. Every day (phone's local midnight) you get 3 new quests picked from: serve customers, double orders, earn coins, make parts, claim offline coins. Goals scale to your shop (about 20 minutes of work). Finish all 3 for +2 bonus gems (DAILY_BONUS_GEMS). The day only moves forward, so setting the clock back brings nothing back; unclaimed dailies are lost at midnight.
- Everything is saved; Reset progress wipes it.

v0.15 - Ads removed, gems + quests:
- No more ads and no ad plugin/account needed (admob_bridge and the ad setup guide are gone).
- New gems (blue diamond counter next to your coins). You earn them from the new Quests button (lower-right): 13 quests like "Serve 5 customers", "Earn 5,000 coins", "Unlock the Motherboard". Tap the green button on a finished quest to collect its gems. The button pulses with a red dot when you have one to collect.
- "Claim x2" on the Welcome back popup now costs 3 gems (OFFLINE_X2_GEMS in main.gd). Plain Claim is always free.
- Quests/gems are saved and wiped by Reset progress.
- The notification reminder is still optional: see SETUP_NOTIFICATIONS.txt (skip it if you like).

v0.14 - Customers can ask for 2:
- About 30% of customers (DOUBLE_ORDER_CHANCE in main.gd) order 2 of everything. They show an "x2" bubble over their head and a red x2 badge on the counter price bubble.
- The worker has to make the whole order twice (case, board, screen, then again) before the sale completes, and you're paid for both sets.
- Offline rewards take double orders into account.

v0.13 - Real ads wired in:
- scripts/admob_bridge.gd now ships active. On a phone, as soon as the AdMob plugin (res://addons/admob) is installed, Claim x2 plays real Google rewarded ads (test ads until you set USE_TEST_ADS to false and paste your Ad Unit IDs). Desktop and no-plugin builds keep the fake 3s test ad. Setup steps: SETUP_ADS_NOTIFICATIONS.txt.

v0.12 - Claim x2 ad + "shop is full" reminder:
- The Welcome back popup now has "Claim x2" (watch an ad, get double) and a plain Claim button. Right now the ad is a fake 3-second TEST AD so you can try it (ADS_TEST_MODE in main.gd). Skipping/closing an ad early gives no bonus.
- When you leave, a notification is scheduled for when the 2h offline cap is reached ("Your shop is full!"). Coming back cancels it. New "Notifications" switch in Settings.
- Real ads and notifications are optional plugins: see SETUP_ADS_NOTIFICATIONS.txt. Rename scripts/notify_bridge.gd.txt (remove the .txt) after installing the notification plugin. Without them the game still runs fine.

v0.11 - Offline rewards:
- Close the game (or lock your phone) and your shop keeps earning, up to a max of 2 hours. Come back to a "Welcome back!" popup and tap Claim.
- The reward is worked out from your current upgrades the moment you return and is saved, so you can't lose it by closing the game before claiming.
- Anti clock-cheat: the game remembers the furthest-ahead time it has ever seen. Setting the clock back earns nothing (you get a warning toast), and setting it forward gives at most 2h and then stops earning until real time catches up. Claiming, closing and reopening can't pay twice.
- Needs the shop open (Case Maker + Worker). Trips under 1 minute earn nothing.
- Tweak in main.gd: OFFLINE_MAX_SECONDS, OFFLINE_MIN_SECONDS, OFFLINE_RATE (1.0 = same as playing, 0.5 = half).

v0.10 - Legless guys + animations:
- Customers and the worker are legless now: round head floating over a rounded body with little eyes, gentle bobbing (the worker bobs faster while working).
- Popups pop in with a bounce and shrink away when closed; the backdrop fades.
- Coin counter pops when you earn coins.
- Red dots pulse; the Upgrades button gently pulses when you can afford something.
- Settings switches slide smoothly. Toast messages slide up and fade. Tap ripples show where you touched.
- Store icon bounces.

v0.9 - UI overhaul + rename:
- Project renamed to techadv (folder, zip, project name, save file techadv_save.cfg - separate from older versions' saves).
- New look: rounded panels with blue headers and shadows, 3D-style buttons, round close buttons, rounded HUD pills, real toggle switches, small icons on every upgrade row.
- Title moved below the HUD so nothing overlaps.
- The green "+" next to your coins is now the Store. It opens an empty "Coming soon" screen for now.
- Settings: Sound, Vibration, Floating +coins, Compact numbers (1.5k / 1.2M) toggles, total earned, Reset progress. Settings are saved and survive a progress reset.
- Small sound effects (coin, buy, error) are generated in code, so there are no audio files to import.

Earlier features:
- 30 starting coins. Unbox Case Maker (25c) and Worker (free) to open the shop.
- Tap any station for its popup: Case Maker 25 levels, Motherboard (25k unlock), Screen (100k unlock). Every order needs every unlocked part.
- Upgrades button (lower-left): More customers, Faster cases, Energy, Faster motherboards, Money, Faster screens.
- Red dots show when something is affordable.
