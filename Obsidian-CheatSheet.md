# Obsidian Cheat Sheet

See [Basic formatting syntax](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax).

### Callouts
Create with a chevron.

```md
> [!info]- Expand to see more
> This is the detail area.
```

### Date and Time

`Ctrl + P date`  
`Ctrl + P time`

The date is: 2024-04-18
The time is: 18:04

Date Format: `YYYY-MM-DD`  
Time Format: `HH:mm` (military clock)

Updated time format: `h:mm a` (AM/PM clock)

### Embed a PDF in a Note

To embed a PDF:
```md
![[Document.pdf]]
```

You can also open a specific page in the PDF, by adding `#page=N` to the link destination, where `N` is the number of the page:
```md
![[Document.pdf#page=3]]
```

You can also specify the height in pixels for the embedded PDF viewer, by adding `#height=[number]` to the link. For example:
```md
![[Document.pdf#height=400]]
```

See [Embed a PDF in a note](https://help.obsidian.md/Linking+notes+and+files/Embed+files#Embed+a+PDF+in+a+note).

### Footnotes

```md
This is a simple footnote[^1].

[^1]: This is the referenced text.
```

### Horizontal Rule
Three asterisks, dashes, or underscores in a row.

```md
---
```

### Animated GIF
Either drag and drop from a web page. Or save to Obsidian vault and embed manually.

```md
![[stimpy-red.gif]]
```

![stimpy-red](https://github.com/gkhays/cheatsheets/assets/773981/5d4d058f-ee24-448b-b21a-e10b4e4d7bf0)

See [Can animatged GIFs be made to play in Obsidian?](https://forum.obsidian.md/t/can-animated-gifs-be-made-to-play-in-obsidian/32767).

### Embed YouTube Video
Use the Markdown embed image syntax, e.g.
```
![](https://www.youtube.com/...)
```

See [Embed YouTube Videos in Notes](https://forum.obsidian.md/t/embed-youtube-videos-in-notes-link-timestamps-to-embedded-video/36779).
