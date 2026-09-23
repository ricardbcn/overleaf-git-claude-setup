# This folder is a Git copy of an Overleaf project

This folder is a local Git clone of an Overleaf project (remote `https://git.overleaf.com/<id>`). Co-authors edit the same project live in the Overleaf browser editor. Overleaf is the source of truth.

This `CLAUDE.md` is **local only**: `.git/info/exclude` lists it (and `.claude/`), so it is never pushed and co-authors never see it. Never commit it, and never add other helper files (`.gitignore`, notes, scripts, `.claude/` settings) to the project: anything committed appears in Overleaf for everyone.

## If you are Claude Code

Follow the standing rule "Overleaf projects (Git)" in `~/.claude/CLAUDE.md`. Nothing here overrides it.

## If you are Claude Cowork (or any tool that cannot reach git.overleaf.com)

- **Edit files only. Do not run Git commands that change anything**: no `git add`, `commit`, `pull`, `push`, `fetch`, `merge`, `reset`, `checkout`, `stash` or `rebase`. Read-only `git status`, `git diff` and `git log` are fine if they work.
- **Before you start**, tell me: "Pull this project in Claude Code first, so I edit the latest version." If read-only Git works, also give me the first line of `git status -sb`: if it says `behind`, the copy is out of date. (Not `behind` only means up to date as of the last contact with Overleaf, so the pull comes first anyway.)
- **When you finish**, list every file you changed or created and tell me: "Now ask Claude Code to commit these files, then pull and push." Claude Code commits them first and then pulls, so any clash with co-authors' edits shows up as a conflict for me to decide.

## Rules for everyone

- One paragraph per source line; don't re-wrap or reformat paragraphs you were not asked to change (it creates conflicts with co-authors).
- File and folder names must be valid on Windows: no `: ? * < > | "`, no trailing space or dot.
- Never delete or rename files unless asked; never touch the hidden `.git` folder.
- Don't add the compiled document (e.g. `main.pdf`) or build output (`.aux`, `.log`, …), and don't compile inside this folder (compile to a folder outside it). Figure PDFs/PNGs used by `\includegraphics` are content.
