# Energy Ledger

A personal calorie and macro ledger. One HTML file, no build step, no dependencies
beyond a web font.

Unlike most trackers it does not take your calorie target on faith. It learns your
real daily burn from your own data: it smooths your weigh-ins into a trend line
(EWMA, alpha 0.1), fits the slope of that trend over a rolling window, and solves
energy balance —

    burn = average intake - (trend weight change x 7700 kcal per kg) / days

— then blends that measured figure with the Mifflin-St Jeor estimate in proportion
to how much data it has. Your target follows the result, so metabolic adaptation
during a diet is picked up automatically instead of being argued about.

## What's in it

- Adaptive burn estimate with a stated confidence, and the arithmetic shown in words
- Daily calorie and macro targets, fibre at the 14 g / 1000 kcal guideline
- Thirteen micronutrients tracked against DRI targets and ceilings, with an honest
  coverage figure so partially-logged days do not read as deficiencies
- Weekly check-ins: weight, waist, hips, chest, arm, thigh, neck, body fat and a note
- ~150-food reference table carrying full nutrient profiles, your own foods, and saved
  meals you log in one tap
- Plain-language logging: type or dictate "log my tuna rice meal for lunch"
- Weight trend, energy balance, weekday pattern, body and consistency panels
- CSV export of every day, weigh-in, measurement, nutrient and target

## Two versions

**This repo** is the standalone copy. It saves to `localStorage`, so the data lives
in whichever browser you opened it in and does not travel between devices. Serve
`index.html` from anywhere — GitHub Pages, or just open the file.

**The hosted copy** on claude.ai adds a cloud store that syncs across your devices,
plus the Claude-powered parts: free-text and dictated logging, photographing a
nutrition label to create a food, and photographing a plate to estimate a meal.
Those features hide themselves here, where there is no Claude to ask.

## Using it

Open Setup first — height, age, activity, starting weight, goal weight and the rate
you want. Then log what you eat, and weigh in.

Weighing daily is better, but weekly works: gaps between weigh-ins are filled by
straight-line interpolation before smoothing, so a weekly cadence recovers the same
trend slope. The engine needs two weigh-ins at least ten days apart inside its window
before it will measure anything; below that it says so and stays on the formula.

Day-to-day scale noise is expected and ignored; only the trend line feeds the
estimate.
