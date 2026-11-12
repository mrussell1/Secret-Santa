# 🎄 Secret Santa Draw

A single-page, no-account, no-email Secret Santa name drawer. It runs entirely in the browser: pick names, apply "can't draw each other" rules, and get one private link per person. Each person opens their link and taps a button to see who they're buying for.

## How it works

1. The organizer opens the page and types a **round label** (for example `2026`).
2. Tapping **Draw names** shuffles everyone in the browser until nobody has themselves or a blocked partner.
3. The page shows one link per person. The result is scrambled into the part of the link after the `#`.
4. The organizer sends each person **only their own link**, privately.
5. Each person opens their link, taps **Reveal my match**, and sees their name and the round label.

Nothing is stored anywhere. The draw lives in the organizer's open browser tab, and the part of a link after the `#` is never sent to the web server.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (page, styles, and code in one file) |
| `README.md` | This file |

## Hosting on GitHub Pages

1. Create a new **public** repository (free Pages hosting needs a public repo).
2. Upload `index.html` (the file must be named exactly this) and this README.
3. Go to **Settings → Pages**, choose **Deploy from a branch**, select the `main` branch and the root folder, and save.
4. After a minute or two the site is live at `https://<username>.github.io/<repo-name>/`.

Anyone with the link can use it. No Claude, GitHub, or other account is needed to open it.

## Running a draw

1. Open your site's address (not a person's link).
2. Check the **Round label** and tap **Draw names**.
3. Confirm the **Shared page link** box shows your real site address. Edit it if not.
4. Copy each person's link and send it to that person only.
5. **Send all links before closing or refreshing the tab.** The draw only exists while the page is open.

### Drawing again

Tapping **Draw again** (or refreshing and drawing) creates a brand-new draw. Old links still open and still show the old match, because nothing tracks which draw is "current." That's why the round label exists: change it for each new draw (for example `2027`, or `2026 - Redo`) so an old link is easy to spot. Tell everyone to delete their old links.

## Editing the app

Everything you're likely to change is marked with `EDIT:` comments in `index.html`.

| To change | Look for |
| --- | --- |
| Colors, fonts, candy-cane strip | `EDIT: COLORS` in the `<style>` block |
| Add or remove people | `PEOPLE` at the top of the script |
| Couple or "can't draw" rules | `RULES` right below it |
| Default round label | `DEFAULT_ROUND` |
| Any page wording | The `TEXT` block |
| Number of snowflakes (or removing snow) | `Falling snow` at the bottom of the script |

Notes when editing:

- Names must be spelled identically (including capital letters) in `PEOPLE` and `RULES`.
- If you remove a person, remove any rule that mentions them.
- Each rule is a pair that cannot draw each other in either direction. Nobody can ever draw themselves.
- If your rules make a draw impossible, the page shows an error message instead of freezing.
- Changing `KEY` makes every previously sent link stop working.

After editing, commit the change to GitHub. The site usually updates within a minute or two.

## Privacy and security notes

- **This is obfuscation, not encryption.** Anyone who has a link, or who reads the page's source code, can decode a link. It's meant to stop casual peeking in a family game, not a determined person.
- **The organizer could decode links** if they chose to, so a truly blind draw would need password protection. The organizer also learns their own match.
- **Send each link privately.** Pasting links into a group chat reveals everyone's match to the whole group.
- **Links stay readable** in message history, browser history, and screenshots. Delete messages once everyone has seen their match.
- **No data is collected.** The page loads no outside scripts, fonts, or trackers, and uses no cookies. GitHub may log normal web traffic (such as IP addresses) like any host.
- **Names and rules are visible** to anyone who views the code in a public repo. They are first names only, but consider a vague repo name and deleting the repo after the holidays.
- **Links don't expire.** To take everything down, delete the repo or turn off Pages in **Settings → Pages**.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| Reveal page says "This link doesn't look right" | The link was cut off when copied or pasted. Send it again in full. |
| "Couldn't find a valid draw" message | The rules block every possible draw. Check `PEOPLE` and `RULES`. |
| A person sees the wrong round label | They opened an old link. Send them their newest one. |
| Site shows a 404 after setup | The file isn't named `index.html`, or Pages isn't enabled on the `main` branch. |
| Page changes aren't showing | Wait a couple of minutes, then hard-refresh the browser. |

## License

Free to use and modify for personal use.
