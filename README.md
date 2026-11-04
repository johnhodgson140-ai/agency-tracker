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
- ~150-food reference table, your own foods, and saved meals you log in one tap
- Plain-language logging: type or dictate "log my tuna rice meal for lunch"
- Weight trend, energy balance, weekday pattern and consistency charts
- CSV export of every day, weigh-in, trend, burn and target

## Two versions

**This repo** is the standalone copy. It saves to `localStorage`, so the data lives
in whichever browser you opened it in and does not travel between devices. Serve
`index.html` from anywhere — GitHub Pages, or just open the file.

**The hosted copy** on claude.ai adds a cloud store that syncs across your devices,
plus the Claude-powered parts: free-text and dictated logging, photographing a
nutrition label to create a food, and photographing a plate to estimate a meal.
Those features hide themselves here, where there is no Claude to ask.

## Using it

Open Setup first — height, age, activity, goal weight and the rate you want. Then
weigh in daily (same time, before eating) and log what you eat. The engine needs
roughly ten days of both before it stops leaning on the formula.

Day-to-day scale noise is expected and ignored; only the trend line feeds the
estimate.
