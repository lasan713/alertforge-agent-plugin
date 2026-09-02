---
name: create-stream-branding
description: Create coordinated streaming brand assets with AlertForge, including Style Sheets, animated overlay packs, AI stream alerts, and transparent videos. Use when a user wants Twitch, YouTube, Kick, OBS, Streamlabs, or StreamElements graphics and motion assets.
---

# Create stream branding with AlertForge

Use the AlertForge MCP tools for product facts and for authenticated creation workflows. Treat tool output as the source of truth for available asset types, prices, credit costs, status, and download URLs.

## Safety and billing

- Connect through AlertForge OAuth when an account tool requests authorization. Never ask the user to paste an OAuth token into chat.
- Before any credit-spending tool, show the current price or plan quote and obtain the user's explicit confirmation. Do not infer confirmation from a general request to explore options.
- Do not invent scene kinds, alert types, prices, project IDs, render IDs, or completion states.
- Treat reference images and generated assets as user-owned content. Do not reuse them outside the requested project.
- Signed result URLs expire. Re-check status to obtain a fresh URL when necessary.

## New overlay pack

1. Call `list_scene_kinds` and `list_particles` when their options are relevant.
2. Ask the three questions required by `plan_design_sheet`, using the wording in that tool's description. Pass the user's answers without inventing a theme.
3. Call `plan_design_sheet`, present its exact credit quote, and get confirmation before `create_design_sheet`.
4. Poll `get_pack_status` until the Style Sheet is ready. Show or link the returned Style Sheet image and get the user's explicit visual approval before `approve_design_sheet`.
5. Call `plan_overlay_pack` for the approved project. Present its exact summary and credit quote, and get confirmation before `create_overlay_pack`.
6. Poll `get_pack_status` at a reasonable interval until complete. Return the direct result links and editor URL. Use `export_pack_zip` only when the user asks for the flat export.

## AI stream alerts

1. Call `list_alert_types` before planning so types and current prices are known.
2. If the user needs a new character, show the current character-generation cost and get confirmation before `generate_alert_character`; poll `get_alert_character_status` until terminal.
3. Call `plan_alert_pack` with only the alert types the user requested. Present the exact quote and get confirmation before `create_alert_pack`.
4. Poll `get_alert_pack_status` at a reasonable interval until every selected alert succeeds or fails. Report individual failures and returned WebM/OBS links accurately.

## Transparent video

1. Call `plan_transparent_video` with the user's creative direction and selected tier.
2. Present the exact quote and any download warning, then get confirmation before `create_transparent_video`.
3. Poll `get_render_status` at a reasonable interval until terminal and return the finished asset links.

When a tool reports a recoverable error, explain the resolution it provides and preserve the current project or plan instead of starting over unnecessarily.
