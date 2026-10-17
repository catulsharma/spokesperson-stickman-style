# Spokesperson & Stickman Style

Create a video where a photorealistic AI spokesperson speaks in front of, or beside, animated story-matched 2D stickman scenes, with one voice throughout.

This playbook combines two existing ones: the [Historical Documentary Video Workflow](https://github.com/ai-playbooks/historical-documentary-video-workflow) (realistic presenter, character sheet, timeline discipline) and the [VideoExpress Stickman Story Agent](https://github.com/ai-playbooks/videoexpress-stickman-story-agent) (2D stickman master, continuity table, concurrent submission, Auto Align).

## Requirements

- A browser-capable agent that can follow the instructions in `SYSTEM_PROMPT.md`.
- Access to VideoExpress (app.videoexpress.ai) with generation access and its built-in CloneVoice integration.
- Sign in when prompted. The workflow uses the agent's visible built-in browser unless you authorize another browser.

This folder contains instructions for browser automation. It is not a standalone executable or a direct API workflow.

## How to use

Load `SYSTEM_PROMPT.md` as the instructions for your browser automation agent, or ask the agent to read and follow that file.

Start the workflow. It asks four questions together:

| Question | Default |
| --- | --- |
| Idea/Script | Supply a topic, a story, or your own script |
| Presenter and voice | Daniel Reed, a fictional male presenter, with the CloneVoice System Voice Beau Whitaker |
| Ratio | Landscape 16:9; Vertical 9:16 is also supported |
| Duration | 60 seconds total, up to 5 minutes |

Reply with your choices. For example:

> Idea/Script: Explain how a seed becomes a tree, told as a little stickman's garden adventure. Presenter and voice: keep the default. Ratio: Landscape. Duration: 90 seconds.

Let the agent finish. It saves the project and clicks Export Video, then stops. It does not download the video.

## What it creates

- **Spokesperson (photorealistic):** a character sheet fixes the presenter's identity. The presenter opens and closes the video full-frame and appears over the story scenes, keyed on a green background or as a corner inset, depending on what the editor supports.
- **Stickman story scenes (2D):** a stickman master character, environment references and a continuity table keep one protagonist and one set of locations across scenes. Each scene starts where the last one ended and shows a new action.
- **One voice:** every line is created once with the same CloneVoice voice, and the presenter's clips use that audio. Stickman clips are silent, so only one voice plays.
- **Assembly:** stickman clips on the base track, presenter clips on the track above, aligned segment by segment, with Auto Align and a save.

## Audio and video timing

The presenter's clip defines each segment's length. Stickman clips are generated at the same length (rounded up) and trimmed with Cut if they run longer, deleting only the excess video. Speech is never regenerated, cut, stretched or retimed. Final length follows the actual audio and can differ slightly from the requested duration.

## Working preferences

- 2D stickman style for the story scenes and photorealistic style for the presenter; the two are never mixed within a layer.
- No routine playback QA and no unrequested Share, publish or download actions.
- Fast production: each clip is generated once, with retries only for confirmed failures.
- Reuse completed assets when resuming a production.
- Edit instructions in place; no backup prompts or extra reports.
- Generated visuals and voice consistency can vary. Review the saved result before publishing. The presenter-over-scene layering (keyed or inset) is an untested path, so check the layered timeline before exporting.

## Files

- `SYSTEM_PROMPT.md` — instructions the automation agent follows.
- `README.md` — this short usage guide.
