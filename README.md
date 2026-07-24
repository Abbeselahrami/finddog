# finddog

Remote ad configuration for the **Find Dog** iOS game. The app fetches
`config.json` on every launch (≤6s), so ad behaviour changes here take effect
with **no App Store update**.

Raw URL the app reads:
`https://raw.githubusercontent.com/Abbeselahrami/finddog/main/config.json`

## Keys
- `ads.enabled` — master switch (false = zero ads)
- `appOpenEnabled`, `appOpenOnResume`, `bannerEnabled`, `mrecEnabled`, `interstitialEnabled`, `rewardedEnabled` — per-format on/off
- `appOpenId`, `bannerId`, `mrecId`, `interstitialId`, `rewardedId` — ad unit ids (swap test → real here)
- `interstitialOnLevelEnter` — interstitial when entering a level (Home → Game)
- `interstitialOnNextLevel` — interstitial after completing a level
- `interstitialOnBack` — interstitial on the back button (Game → Home)
- `interstitialOnGameOver` — interstitial on Restart after running out of paws
- `minSecondsBetweenInterstitials` — global interstitial cooldown (default 15)

> The AdMob **App ID** (`GADApplicationIdentifier`) lives in the app's Info.plist,
> not here — changing it needs a binary update.

> Validate before committing: `python3 -m json.tool config.json`
> Invalid JSON is ignored by the app (it keeps the cached/bundled config).
