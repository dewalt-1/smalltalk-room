# Computer Room: Smalltalk

Squeak 1.1 (1996, based on Apple's Smalltalk-80) running in the browser through
[SqueakJS](https://squeak.js.org) by Vanessa Freudenberg. Nothing to install: open
the page, wait for about 4 MB to download the first time, and you're in.

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The page. Loads SqueakJS and starts the image. |
| `squeak_bundle.js` | SqueakJS, the Smalltalk virtual machine written in JavaScript (MIT licence, see `LICENSE-SqueakJS.md`). |
| `squeak/Squeak1.1.image` | The Smalltalk system itself: every object, window and method. |
| `squeak/Squeak1.1.changes` | A log of every change made to the image. |
| `squeak/SqueakV1.sources` | The source code of the original system. |

## Hosting

The folder is a plain static website. Anything that serves files works.

**GitHub Pages (free, one link for students)**

1. Create a new public repository, e.g. `smalltalk-room`.
2. Upload the contents of this folder (not the folder itself) to the repository.
3. In the repository: Settings → Pages → Source: "Deploy from a branch", Branch: `main`, folder `/ (root)`.
4. After a minute the page is at `https://<your-username>.github.io/smalltalk-room/`.

**Netlify Drop (no account setup)**: drag this folder onto https://app.netlify.com/drop.

**Any web server** (e.g. university web space): copy the folder up and link to `index.html`.

**Offline in the classroom**: browsers will not run it from a double-clicked file.
Start a small server in this folder instead:

```
python3 -m http.server 8000
```

and open http://localhost:8000. Other computers on the same network can use your
computer's IP address instead of `localhost`.

## How saving works

- The first visit downloads the three files into the student's browser (IndexedDB).
  Every later visit loads from there, so it also works offline.
- "save" in the Smalltalk screen menu writes the changed image back into the browser.
  It survives reloads, but only in that browser on that computer.
- A **fileOut** (e.g. of a changed method) also lands in the browser, not in Downloads.
  The small **files** button in the bottom right corner lists those files and downloads a copy.
  This is how students hand in work: fileOut, then files → download the `.st` file.
- Clearing site data in the browser deletes everything.

## Preparing your own starting image

1. Open the page, set it up the way students should find it (for example
   `Display newDepth: 1`, a Workspace with instructions, your own menu item).
2. Screen menu → save.
3. Click **files** and download `Squeak1.1.image` and `Squeak1.1.changes`.
4. Replace the two files in `squeak/` with them and re-upload.

Students who already visited keep their cached copy. To force everyone onto a new
image, rename both files (e.g. `ComputerRoom2.image` and `ComputerRoom2.changes`,
the names must match) and update the file names in `index.html`.

## Mouse

| You do | Smalltalk calls it | Used for |
|---|---|---|
| Left button | red | selecting, clicking, drawing |
| Right button | yellow | text menu: do it, print it, accept |
| Cmd-click or Option-click | blue | window menu: close, move, frame, collapse |

Menus appear only while the button is held down. Hold, move to the item, release.

## First thing to try

Hold the mouse on the grey background, choose open… → workspace, type:

```
Display newDepth: 1.
Form toothpaste: 30
```

select both lines, press Cmd-D, and draw with the left button. Right-click to stop.
The code is in the Browser under Graphics-Display Objects → Form → class → examples → toothpaste:.

## Licences

SqueakJS: MIT (see `LICENSE-SqueakJS.md`). Squeak 1.1 was released by Apple in 1996
under the Squeak License; in 2006 Apple relicensed Squeak 1.1 under the Apache License 2.0.
