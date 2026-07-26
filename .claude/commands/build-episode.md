---
description: Run the full multi-agent YouTube production pipeline for a topic
argument-hint: "Topic Name"
---
You are the Lead Orchestrator for the YouTube AI Media Engine. Build a complete
production package for this episode topic:

**$ARGUMENTS**

## Setup
1. Derive a kebab-case slug from the topic (e.g. "AI Voice Receptionists" → `ai-voice-receptionists`).
2. Create the output folder `workspace/episodes/<slug>/`.
3. Use the skeletons in `templates/` as the shape for each output file.

## Pipeline (run sequentially, passing outputs forward)
1. Invoke the `editorial-agent` to write the 5 titles, thumbnail concept, and the
   full word-for-word script with `[VISUAL]` cues.
   → Save to `workspace/episodes/<slug>/01_script.md`.
2. Pass `01_script.md` to the `production-agent` to produce clean HeyGen/ElevenLabs
   dialogue (with SSML `<break>` markers) and Midjourney/Runway prompts (`--ar 16:9`).
   → Save to `workspace/episodes/<slug>/02_production_assets.json`.
3. Pass `01_script.md` to the `publisher-agent` to generate the SEO title (<60 chars),
   description with chapters/timestamps, 10-15 tags, and a pinned comment.
   → Save to `workspace/episodes/<slug>/03_metadata.md`.
4. (Optional — only if the user provides analytics or comments) Invoke the
   `community-agent` for comment triage, drafted replies, a performance digest, and
   follow-up episode ideas.
   → Save to `workspace/episodes/<slug>/04_community.md`.

## Finish
- Present a summary table of the generated artifacts and their paths.
- Do NOT publish anything externally (no upload, no comment posting). Everything
  stays as local drafts for human review and approval.
