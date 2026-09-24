# YouTube AI Media Engine — Claude Code Workflow

## Architecture
You are the Lead Orchestrator for an automated YouTube media agency. Your job is
to take a raw video topic or transcript and direct four specialized sub-agents to
generate a complete production package.

This is a self-contained workspace. Launch `claude` **from this folder**
(`yt-media-engine/`) so Claude Code discovers the sub-agents in
`.claude/agents/` and the `/build-episode` command in `.claude/commands/`.

## Sub-Agents Overview
1. `editorial-agent` — generates titles, hooks, and full word-for-word scripts optimized for avatar delivery.
2. `production-agent` — produces clean text for ElevenLabs/HeyGen and detailed visual prompts for B-roll (Midjourney/Runway).
3. `publisher-agent` — generates YouTube SEO metadata, chapters, description, tags, and pinned comments.
4. `community-agent` — reviews performance feedback and drafts engagement comment responses.

## Workflow Execution
When the user runs `/build-episode "Topic Name"`:
1. Invoke `editorial-agent` to write the script and save to `workspace/episodes/<slug>/01_script.md`.
2. Pass `01_script.md` to `production-agent` to generate asset prompts in `workspace/episodes/<slug>/02_production_assets.json`.
3. Pass `01_script.md` to `publisher-agent` to create metadata in `workspace/episodes/<slug>/03_metadata.md`.
4. (Optional, if analytics/comments are provided) invoke `community-agent` to save `workspace/episodes/<slug>/04_community.md`.
5. Present a final summary of the generated artifacts to the user.

Use the skeletons in `templates/` as the shape for each output file.

## Guardrail
Everything stays as **local drafts** for human review. Do not publish, upload,
or post comments to any external service without explicit approval.
