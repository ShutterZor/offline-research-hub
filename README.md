# Research Hub — Academic Research Dashboard

A **single-file, offline-first personal research management dashboard** for tracking working papers, submissions, and publications. No build tools, no server, no dependencies — just open the HTML file in a browser.

[中文版README](./README_ZH.md)

![Type](https://img.shields.io/badge/type-single--file%20HTML-blue) ![Deps](https://img.shields.io/badge/dependencies-none-brightgreen) ![Storage](https://img.shields.io/badge/storage-localStorage-orange)

---

## ✨ Features

### Dashboard

- At-a-glance stats: working / under-review / published counts and average progress
- Overall progress bars computed live from stage completion
- Recent-updates timeline (auto-refreshed whenever anything changes)

### Working Papers (在研论文)

- **Hierarchical stage tree** (up to 3 levels): click the hollow circle to toggle done (cascades to children)
- Fully **customizable stages**: add / rename / delete, with sensible defaults (引言 → 文献综述/理论假设 → 研究设计 → 实证分析 → 结论与启示)
- **Drag-and-drop reordering** — level-1 stages reorder freely; level-2/3 stages move only within their parent
- **Double-click inline editing** for title, authors (chip editor with add / hover-delete / drag-sort), target journal, next action, and folder path
- **Editable priority** dropdown (High / Medium / Average) with color-coded badges
- **Filter** by keyword and priority
- **Flow to Submissions** with one click — inherits title, authors, and folder path

### Submissions (在投论文)

- Editable title, authors, current journal, submission date, manuscript ID, submission count, next action
- **Submission history**: add / delete records; date and journal are double-click editable; status is a dropdown (已投稿 / 初审中 / 外审中 / 小修改 / 大修改 / 已录用 / 已拒稿)
- **Flow to Publications** — inherits title, authors, current journal (→ journal), and folder path

### Publications (已发表论文)

- Card view + **GB/T 7714-2025 reference list** view (Chinese and English in separate columns, 5 sort modes, one-click copy)
- **Citation counts**: double-click to edit manually for any paper; English-journal papers can fetch live counts from **Crossref** by DOI (per-paper button with reminders, plus a batch update)
- Language detection is **journal-name based** (Chinese journal name → Chinese paper)
- **One-click export**: generates a standalone static HTML page with all data hard-coded — same theme, reference lists, and expandable "查看更多" details (abstract / keywords / citations / DOI link). Ready to share or print

### Cards, everywhere

- Add (appends to the end, debounced), delete (with confirmation), and **drag-to-reorder** cards on all three pages
- IDs (R001 / S001 / P001…) **renumber automatically** after any add / delete / reorder
- All edits are keyed to a stable internal ID, so renumbering never breaks saved data

### Themes & Privacy

- 6 themes (Academic Blue, Graphite, Forest, Burgundy, Indigo, Warm Paper), persisted
- Everything is stored in your browser's `localStorage` — the file itself stays clean
- The Crossref contact email is entered **in the page** (stored locally), never hard-coded in the HTML — safe to share the file publicly

## 🚀 Getting Started

1. Download `Research-Hub-V2.1.html`
2. Open it in any modern browser (Chrome / Edge / Firefox)
3. Edit your papers directly on the page — everything is remembered by the browser

### Adding your own data

All sample data lives in the `DATA_EMBEDDED` object at the top of the `<script>` block. Replace it with your own papers (structure is self-documenting), or simply use the on-page **＋ 新增** buttons and edit inline.

### Exporting / sharing

- **Publications page → ⬇ 一键导出** produces a fully static, self-contained HTML snapshot (data hard-coded) you can host anywhere
- Fill in the Crossref email input before sharing, so visitors can refresh citation counts politely

## 🗂 Version History

| Version  | Highlights                                                   |
| -------- | ------------------------------------------------------------ |
| **v2.1** | Editable citation counts (manual for all; Crossref fetch for English-journal papers with reminders); journal-name-based language detection; removed demo "Open Article" button |
| **v2.0** | One-click export of publications to a standalone static webpage (theme-aware, GB/T 7714-2025, expandable details, print-friendly) |
| **v1.9** | Merged volume(issue) editing; Crossref email moved from hard-coded constant to an in-page input (privacy-safe sharing); reference list reads edited values |
| **v1.8** | Author/keyword chip editor (light-green pills, add / hover-delete / drag-sort) on research & submission cards; full editing on publication cards; flow Submissions → Publications; long titles no longer squash status badges |
| **v1.7** | Fixed new-card placement (always appended at end) & double-click multi-add; editable priority dropdown (High/Medium/Average); removed tag row, authors chips; research → submission flow; submission history add/delete |
| **v1.6** | Card add/delete/drag-reorder with automatic renumbering; editable titles & fields; submission history editing with status dropdown |
| **v1.5** | Fixed double-click inline editing (event delegation bug); auto "last updated" timestamps (minute precision) on any change |
| **v1.4** | Stage drag-and-drop sorting; inline editing of target journal / next action / folder path with localStorage persistence |
| **v1.3** | Interactive stage tree (click-to-complete, add/rename/delete, up to 3 levels, localStorage) |
| **v1.2** | Theme engine, Crossref citation lookup, GB/T 7714-2025 reference list |

## 🛠 Tech Notes

- Pure vanilla HTML / CSS / JS in one file — zero dependencies, works offline
- State persisted in `localStorage` under versioned keys (`research-hub-stages-v1`, `research-hub-fields-v1`, `research-hub-cards-v1`, `research-hub-crossref-*`)
- Crossref queries use the polite `mailto=` parameter when an email is provided; results are cached locally
- Language detection: journal name containing CJK characters → Chinese paper; otherwise English (falls back to the `language` field when the journal is empty)

## 📄 License

MIT — feel free to use, modify, and share.
