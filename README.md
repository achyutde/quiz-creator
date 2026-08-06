# Quiz Creator

A single-file, static web app that turns a CSV of questions into an interactive quiz you can run in any browser. No server, no build step — everything runs client-side.

## Use it

Open `index.html` in a browser, then either drop in a CSV or click **Try the sample quiz**. To host it online, push this folder to GitHub and enable GitHub Pages (Settings → Pages → Deploy from branch → `main` / root).

## CSV format

A header row is required. Column names are case-insensitive.

| Column | Required | Notes |
| --- | --- | --- |
| `question` | Yes | The question text. Aliases: `q`, `prompt`. |
| `option_a` … `option_f` | Yes (≥2) | Answer choices. Leave later ones blank for fewer options. Aliases: `a`–`f`, `option1`–`option6`. |
| `correct` | Yes | Letter (`A`–`F`) **or** the exact answer text. Aliases: `answer`, `key`. |
| `explanation` | No | Shown after you answer. Aliases: `explain`, `rationale`, `notes`. |
| `topic` | No | Optional label shown above the question. Aliases: `category`, `subject`, `tag`. |
| `section` | No | Optional. When present, questions are grouped into sections with a section filter. Aliases: `part`, `group`, `module`, `unit`. |

Example:

```csv
question,option_a,option_b,option_c,option_d,correct,explanation,topic,section
"What is 2 + 2?","3","4","5","22","B","Simple addition.","Math","Warm-up"
"Capital of Canada?","Toronto","Ottawa","Vancouver","Montreal","B","Ottawa is the capital.","Geography","Warm-up"
```

## Features

- Questions stay in CSV order; answer options are shuffled each run.
- Optional sections: add a `section` column to group questions, with a filter to practice one section or all.
- Immediate feedback with the explanation after every answer.
- Prev / Next plus a jump grid that shows answered (green/red) and bookmarked (★) questions.
- Bookmark any question (★ button or press `b`); a dedicated bookmarks panel plus a "Review bookmarked" mode.
- Progress and bookmarks auto-save in your browser (per quiz, per device).
- **Save / Load progress file**: export your answers + bookmarks to a small `.json` file and import it on another device. To resume elsewhere, load the same CSV first, then click **Load** and pick your saved file.
- Score summary at the end; restart reshuffles.
- Keyboard: ← / → to navigate, `1`–`6` to pick an answer, `b` to bookmark.
