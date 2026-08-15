# ILAF Plugins

A Claude plugin marketplace holding the ILAF Takaful (إيلاف للتأمين التكافلي) brand workflow.

## Plugins

### `ilaf-brand`

Everything needed to produce ILAF social media content and report on it.

**Skills**

| Skill | What it does |
|-------|--------------|
| `ilaf-social-design` | Branded Arabic/English feed posts, Stories and animated reels. Bundles the brand colors, fonts, white logo, Islamic pattern, Sadu band and panel elements. |
| `ilaf-monthly-social-report` | The bilingual monthly deck for management — ILAF's Instagram and Google Business numbers, plus the Kuwaiti insurer competitor benchmark. Includes the daily story/ads capture log. |

**Commands**

| Command | What it does |
|---------|--------------|
| `/ilaf-brand:post` | Feed post, 1080×1350, both colorways |
| `/ilaf-brand:story` | Story, 1080×1920 |
| `/ilaf-brand:animate` | Turn an approved still into motion |
| `/ilaf-brand:track-today` | Log today's competitor stories, ads and followers |
| `/ilaf-brand:report` | Build the monthly performance deck |

**Connectors** (declared in `.mcp.json`)

Canva · Adobe for creativity · Google Drive · Supermetrics · Higgsfield

You still authenticate each one yourself the first time. The plugin declares which
connectors the workflow needs; it does not carry any credentials.

## Install

Add this repository as a marketplace, then install the plugin:

```
/plugin marketplace add <your-github-username>/ilaf-plugins
/plugin install ilaf-brand@ilaf-plugins
```

To try it before pushing anywhere, point Claude at the local folder instead:

```
/plugin marketplace add ./ilaf-plugins
```

## Layout

```
ilaf-plugins/
├── .claude-plugin/
│   └── marketplace.json
└── ilaf-brand/
    ├── .claude-plugin/
    │   └── plugin.json
    ├── .mcp.json
    ├── commands/
    └── skills/
        ├── ilaf-social-design/
        └── ilaf-monthly-social-report/
```

## Notes

- Brand assets live inside each skill's `assets/` folder, so the plugin is self-contained —
  no waiting for files to be re-shared.
- The large `Ilaf Design 2026` photo library is deliberately **not** bundled. It's big and
  topic-specific; the design skill explains where to pull from it.
- Bump `version` in `ilaf-brand/.claude-plugin/plugin.json` whenever you change a skill,
  so installs elsewhere can tell which revision they have.
