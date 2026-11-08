# shortcuts-example

A minimal example of keeping keyboard shortcuts in [`shortcuts.md`](shortcuts.md) and publishing
them to GitHub Pages with [shortcuts](https://github.com/damian-krawczyk/shortcuts). The
repository holds only the shortcuts file and a workflow. The tool is installed when needed.

## Edit locally

Install the tool once:

```sh
npm install -g https://codeload.github.com/damian-krawczyk/shortcuts/tar.gz/main
```

Then, in this folder:

```sh
shortcuts serve shortcuts.md --open           # edit in the browser at http://127.0.0.1:4190/
shortcuts validate shortcuts.md               # check the file
shortcuts build shortcuts.md -o dist/index.html   # the read-only page, works offline
```

Run the install command again to update the tool. If zsh says `command not found: shortcuts`
right after installing, run `rehash` or open a new terminal.

## Publish to GitHub Pages

[`.github/workflows/pages.yml`](.github/workflows/pages.yml) installs the tool, validates
`shortcuts.md`, builds `dist/index.html` and deploys it on every push to `main` that changes
`shortcuts.md`.

One-time setup: in the repository, go to **Settings → Pages → Source** and choose
**GitHub Actions**. To redeploy without a change (for example after the tool was updated), run
the workflow from the **Actions** tab (*Run workflow*).

The published page is read-only. It shows your favorites (★) but can't change them. To change
shortcuts, run `shortcuts serve` locally, then commit and push `shortcuts.md`.
