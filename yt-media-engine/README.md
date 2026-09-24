# yt-media-engine

Self-contained multi-agent YouTube media production engine for Claude Code. It
turns a raw video topic into a complete production package: script → avatar/voice
assets → SEO metadata → community engagement.

## Usage

```bash
cd yt-media-engine
claude
```

Then run the pipeline:

```
/build-episode "How Small Businesses Can Setup AI Voice Receptionists"
```

Claude launches each sub-agent in an isolated context and writes the outputs to
`workspace/episodes/<slug>/`.

## Layout

```
yt-media-engine/
├── CLAUDE.md                       # Orchestrator rules
├── .claude/
│   ├── agents/                     # editorial / production / publisher / community
│   └── commands/build-episode.md   # /build-episode slash command
├── templates/                      # Output skeletons (script, assets, metadata, community)
└── workspace/episodes/             # Generated packages (see ai-receptionist/ example)
```

## Sub-agents

| Agent | Role | Output |
| --- | --- | --- |
| `editorial-agent` | Titles, thumbnail concept, avatar-ready script | `01_script.md` |
| `production-agent` | HeyGen/ElevenLabs dialogue + Midjourney/Runway prompts | `02_production_assets.json` |
| `publisher-agent` | SEO title, chapters, tags, pinned comment | `03_metadata.md` |
| `community-agent` | Comment triage, drafted replies, analytics digest | `04_community.md` |

> **Guardrail:** all output stays as local drafts. Nothing is published, uploaded,
> or posted without explicit approval.

The `workspace/episodes/ai-receptionist/` folder is a worked example of a full
generated package.
