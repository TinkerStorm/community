# community

This repository contains the default community health files for TinkerStorm, as well as it's information channels for Discord.

## `./router/**` - Colors

> The cost of the path to identify it on a component ID (button) or value (select option) when fully deployed at `main` *on this repository* is 92 and 100 respectively. _92 because it currently takes 8 characters to declare the component trigger for `btn-msg:`._

Color coherence isn't as _immediately_ important considering it will be contained within a single response menu, but alterations might follow if each section is assigned a specific color group - and then having each distinct page follow in their respective groups.

> Each page is represented by it's relative path to it's parent, a path cost (if it is part of the menu navigation) and the embed color it has been given. Only two messages will be shown to all users as standard, the rest will be up to them to engage with.
>
> *Color names are matched against ShareX's list of known colors, and are often close matches rather than exact. `Contributor Blue` represents the only color based on the context of the community.*

## Attributions

- `channel.svg` and `forum.svg` belongs to Discord Inc.
- `tada.svg` belongs to Twitter Inc. from `twemoji`.
- `webhook.svg` did not appear to have a definitive owner (but is used by Discord Inc.).

Only the color of the icons has changed to match the embeds they are associated with, the resulting product is hosted here for the embeds to use as a smaller CDN (as opposed to using Discord Message Attachments *which can be removed from a message or the message itself can be deleted at any time without warning* or a file host like Imgur). Therefore ensuring they can be updated by the community and maintaining the premise for which this was built.

### Steps to generate images for author icons

Either use a command to generate them or a website.
> A website would require the svg display sizes to be modified.

```powershell
# A small PowerShell script to generate the author icons with svg2png from npm
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
# add WEBHOOK_URL to env or webhook to 'config.json'
# add your files within the repository and specify them directly or use globs
npm run sequence
```

> A webhook target **must** originate from a bot user to allow the use of components. For this specific configuration, [Turbo Eureka](https://github.com/TinkerStorm/turbo-eureka) is used to send the messages for the menu - or a self-hosted version of it.

***Any webhooks used must not be committed to the repository. Any commits / PRs found with valid and active webhooks will be closed by default and the user will be advised to remove the webhook from their server.** This is to prevent abuse of the webhook and to ensure the webhook is not used for malicious purposes.*

---

If you need any help setting up the environment, [drop by the Discord server](https://discord.gg/Bb3JQQG).