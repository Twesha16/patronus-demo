# Patronus: product prototype

In a future where everyone has a personal AI agent that knows them better than they know themselves, Patronus helps people catch up with themselves: to explore, notice and remember their own preferences.
This click-through prototype follows one user, Riya, from onboarding through the three modes (Quiet, Ambient, Active) to the main site with Explore, Daily take and her taste profile.
All content is dummy data. Nothing is saved or sent anywhere, and no permissions are actually requested.

## Run it

1. Unzip the folder.
2. Double-click **`index.html`**. It opens in your web browser (Chrome, Safari, Edge or Firefox).

That's it. You need an internet connection for the fonts, but nothing else to install.

Prefer not to download? The same prototype is online at **https://patronus-demo.vercel.app**

<details>
<summary>If double-clicking doesn't work</summary>

Some locked-down browsers block pages opened straight from a file. Run a tiny local server instead. In a terminal, inside the unzipped folder:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000 in your browser. Press Ctrl+C in the terminal to stop it.
</details>

## How to move through it

- **Next:** click the arrow on the right edge of the screen, or press **→** or **Space**.
- **Back:** the round button at the bottom left, or **←**.
- **Mock answers:** click the text bar ("Click to continue") to see the answer, or click **I don't know** to get a nudging question first.
- **Skip ahead:** "Skip tutorial and go to main site" at the bottom right of the tutorial.
- **Modes demos:** on the modes screen, click Ambient or Active, then "See … mode demo". On the main site they're under **Modes** in the sidebar.
- Best viewed on a laptop or desktop screen.

## What's inside

- `index.html`: the whole prototype (HTML, CSS and JavaScript in one file).
- `assets/`: images used by the prototype. Photo credits are in `assets/type/CREDITS.md`.
