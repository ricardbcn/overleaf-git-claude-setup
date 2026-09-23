# Overleaf + Git, set up by Claude

Edit your Overleaf papers on your own computer (Windows or Mac) while your co-authors keep working in the Overleaf browser editor. Claude Code sets it up for you and then syncs your projects with Overleaf whenever it works on them.

*Version 0.1. Open Beta.*

## What you get

- **Your Overleaf projects as normal folders** on your computer (a `Projects` folder in your home folder, e.g. `Projects/My_Paper`), editable with any editor, LaTeX tool or AI assistant.
- **Automatic syncing when Claude Code edits:** it fetches co-authors' changes first and sends its edits to Overleaf right after, so you never run Git commands. If you edit in another editor (TeXstudio, VS Code, …), ask Claude Code to "pull" before you start and to "commit and push my changes" when you finish. Nothing syncs while Claude Code isn't working on the project.
- **No silent overwrites:** when a co-author changed the same paragraph, Claude stops, shows you *original / yours / theirs* word by word, and asks which to keep.
- **Nothing changes for co-authors:** they keep using the browser. No files are added to their projects.
- **Safe defaults:** your Overleaf token stays in your computer's password store (never in files or chats); no force-pushes, no branches; LaTeX build files are ignored; other AI tools (e.g. Claude Cowork) are told to edit only and leave syncing to Claude Code.

## How to use it

1. You need **Claude Code** (<https://claude.com/claude-code>; it needs a paid Claude plan, Pro or higher, or an Anthropic API account) and **Overleaf Git access**: according to Overleaf, Git works on a project if you or the project's owner has a plan with Git integration (paid or institutional). You don't need Git itself or any Git experience: Claude checks whether Git is installed and, with your OK, installs it.
2. Download [`SETUP_FOR_CLAUDE.md`](SETUP_FOR_CLAUDE.md): open it and click the download icon ↓ at the top right of the file ("Download raw file"). The file alone is enough.
3. Open Claude Code in your home folder (in the desktop app, select the folder named after your user, e.g. `C:\Users\<you>` or `/Users/<you>`) and say:
   > Follow `SETUP_FOR_CLAUDE.md` (in my Downloads folder) to set up Overleaf Git for me.

   If you saved the file somewhere else, name that folder instead. On a Mac, click **Allow** if macOS asks whether Claude (or Terminal, or whichever app you run Claude Code in) may access your Downloads folder, and **Install** (not "Get Xcode") if a window offers to install the "command line developer tools": that is how a Mac gets Git.
4. Follow along (about 15 minutes, plus download time if Git must be installed first). You'll do a few things yourself: approve installs and settings, create a Git token in Overleaf, run one clone command to sign in once, and (if you used them) unlink Overleaf's old Dropbox/GitHub sync.

For a second computer, repeat on that computer. To update an earlier setup, delete the old copy of the file, download the newest one and give it to Claude with the same sentence.

## After setup

- **Claude edits:** open Claude Code in a project folder (e.g. `Projects/My_Paper`) and ask for what you want. Claude fetches your co-authors' latest changes first and sends its edits to Overleaf right after.
- **You edit yourself** (TeXstudio, VS Code, …): ask Claude Code to "pull" before you start and to "commit and push my changes" when you finish.
- **Same paragraph changed by someone else:** Claude shows both versions and asks which to keep.
- **Another Overleaf project:** say "clone this Overleaf project:" and paste its link.
- **About once a year** your Overleaf token expires: Claude tells you and gives you one command to sign in again.

## How it works

```
               Overleaf project (source of truth)
              /            |              \
      co-authors      your Windows PC      your Mac
      (browser)       local Git copy       local Git copy
```

| When two people edit at the same time… | Result |
|---|---|
| different files or different paragraphs | combined automatically |
| the same paragraph (or the line right next to it) | Claude stops and asks you |
| someone is typing live in the browser | your changes wait until they pause, then go through (if they keep typing, Claude keeps your edit and sends it a bit later) |

## What's in this repository

| File | Purpose |
|---|---|
| [`SETUP_FOR_CLAUDE.md`](SETUP_FOR_CLAUDE.md) | Step-by-step instructions for Claude, including all texts it needs |
| [`templates/standing-rule-CLAUDE.md`](templates/standing-rule-CLAUDE.md) | The rule added to `~/.claude/CLAUDE.md` that makes syncing automatic |
| [`templates/project-CLAUDE.md`](templates/project-CLAUDE.md) | Local-only helper file placed in each project (never pushed) |
| [`templates/gitignore_global`](templates/gitignore_global) | LaTeX build files to ignore on your computer |
| [`LICENSE`](LICENSE) | CC BY 4.0 |

## Good to know

- **File names:** avoid `: ? * < > | "` and names like `CON`, `AUX` or `NUL` in Overleaf file and folder names. Windows can't handle them, and one such name blocks Windows users from the whole project.
- **Access:** if a project refuses Git access when it is first cloned (`error 403`), it stays browser-only for you; ask its owner.
- **Token:** Overleaf Git tokens expire after about a year. When Git asks you to sign in again, create a new token and sign in once. If a computer is lost, revoke the token in Overleaf.
- **Overleaf's Dropbox/GitHub sync:** unlink it once Git works (Account Settings → Project synchronisation). Dropbox unlinking affects all projects at once, so the setup clones the projects you still use first.
- **Existing Git users:** the setup shows your current Git settings and keeps them unless you want them changed.
- **Overleaf limits:** one branch, no Git LFS, very large files may be refused, and Git requests are throttled at high rates. Normal work is far below the limits; if Overleaf does throttle (e.g. many push retries while someone types), Claude waits a few minutes and tells you which edits haven't reached Overleaf yet. They stay on your computer and go out with the next push.

## Open beta

This is an early public version. Problems, questions and suggestions are welcome as [GitHub issues](https://github.com/ricardbcn/overleaf-git-claude-setup/issues).

An independent guide, not affiliated with Overleaf or Anthropic, provided as is. Overleaf's menus and limits may change; Overleaf's help pages on Git integration are the authority.

## License

[CC BY 4.0](LICENSE): you may share and adapt this guide for any purpose, as long as you give credit (e.g. "based on *Overleaf + Git, set up by Claude* by ricardbcn, <https://github.com/ricardbcn/overleaf-git-claude-setup>") and say what you changed.
