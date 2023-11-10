---
dg-publish: true
---
I took all of my notes in Obsidian, and used Ole's [GitHub - oleeskild/digitalgarden](https://github.com/oleeskild/digitalgarden) and [Cloudflare Pages](https://pages.cloudflare.com/) to publish them on the internet.

There have been a couple of guides out there on this, but few of them actually solved my problems with Cloudflare specifically, so here you go!

Until I actually get around to it, here's a link to the guide I used initially, but ran into problems with: [How I Published My Knowledge Base Online for Free](https://sharaf.cc/40-49-toolbox/40-note-taking/40-01-obsidian/guides/publish-obsidian-vault-for-free/)

The KEY when publishing to Cloudflare is the **Build Configuration**. Specifically, where I differed from Sharaf's guide I changed the "_build output directory_" to from `/src/site` to `/dist`.

![[How this site was made-1.png]]

After that, I went into Obsidian to push some changes, and it was up and running! I had to tweak the settings a little bit to get them all showing correctly, but as you can see, everything is running fine.
