# .github

This repository contains the default community health files for TinkerStorm, as well as it's information channels for Discord.

## Attributions

- `channel.svg` and `forum.svg` belongs to Discord Inc.
- `tada.svg` belongs to Twitter Inc. from `twemoji`.
- `webhook.svg` did not appear to have a definitive owner (but is used by Discord Inc.).

Only the color of the icons has changed to match the embeds they are associated with, the resulting product is hosted here for the embeds to use as a smaller CDN (as opposed to using Discord Message Attachments *which can be removed from a message or the message itself can be deleted at any time without warning* or a file host like Imgur, therefore ensuring they can be updated by the community and maintaining the premise for which this was built).

### Steps to generate images for author icons

Either use a command to generate them or a website.
> A website would require the svg display sizes to be modified.

```powershell
# PowerShell one-liner to generate the author icons with svg2png from npm
$size = 256
Get-ChildItem ./assets/*.svg | ForEach-Object { 
  svg2png $_.FullName -w $size -h $size
    -o "$($_.DirectoryName)/$($_.BaseName).png"
}
```

---

In order to account for the icon being a circle, the svg needs to be modified to have an additional square border.
- A border of 288px is enough to account for the `50%` radius of the css border.
  > `$ * 2 = 512, $ * 1.5 = 384, $ * 1.125 = 288`

You may use any tool you like, so long as the image subject remains centered and the image is square.

## Instructions to run

```sh
npm install
# add webhook to env or 'config.json'
# add your files within the repository and specify them directly or use globs
npm run sequence
```

---

If you need any help setting up the environment, [drop by the Discord server](https://discord.gg/Bb3JQQG).