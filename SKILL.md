---
name: generate-video-storyboards
description: Turn Chinese scripts, episode outlines, dialogue scenes, or prose plots into production-ready AI video storyboard prompts with character-specific microexpression acting. Use when Codex is asked to 生成分镜、拆分剧本、制作视频提示词、设计微表情或人物情绪演绎、把剧情拆成4—15秒独立生成段、控制SHOT与对白时长、锁定角色场景资产，或减少AI视频生成成本。
---

# Generate Video Storyboards

Convert the user's script into self-contained AI-video generation segments while preserving story meaning, spatial continuity, dialogue clarity, and the requested production-document format.

## Required workflow

1. Read the complete script and all attached reference prompts before drafting.
2. Identify scenes, characters, assets, props, UI, dialogue, actions, causality, and continuity constraints.
3. Divide the story into independent generation segments.
4. Divide every segment internally into multiple SHOTs.
5. Calculate dialogue time before assigning shot timecodes.
6. Write each segment as a separate, self-contained prompt whose timeline starts at 0.
7. Repeat all required constraint sections at both the beginning and end of every segment.
8. Validate durations, dialogue windows, shot continuity, safe zones, and required headings.
9. Save each segment as a separate UTF-8 `.txt` file and provide a `.zip` containing all segments when files are requested or useful.

Read [references/storyboard-format.md](references/storyboard-format.md) before producing the final storyboard. Follow its exact hierarchy and validation checklist.

For any character dialogue, reaction, concealed feeling, emotional reversal, crying, smiling, confrontation, or silent acting, also read [references/microexpression-performance.md](references/microexpression-performance.md) and apply it to the SHOT timing and `【表演要求】` section.

## Microexpression workflow

Before assigning visible acting, determine for each important character: surface emotion, true inner emotion, trigger, resistance strategy, emotional leak, peak or decision, and ending residue.

- Build a playable arc: baseline → trigger → resistance/defense → leak → peak/decision → residue. Use only the stages that fit the available time.
- Translate emotions into observable micro-actions involving gaze focus, eyelids, brows, breath, jaw, throat, lips, shoulders, and fingers. Do not rely on abstract adjectives alone.
- Give each beat one dominant change. Avoid animating the whole face at once.
- Define the gaze target and preserve it across cuts.
- Strong emotion does not automatically mean wide eyes, shouting, constant trembling, or immediate tears. Earn tears, voice breaks, collapse, and overt smiles through progression.
- Respect physical constraints: instruments, eating, drinking, injury, masks, distance, or a turned-away pose restrict which facial actions are visible or possible.
- End the acting passage on a holdable residue such as refocused gaze, lowered eyes, released jaw, restored breathing, turn-away, or stillness.
- Use fixed shots for continuous microexpression changes. Add reaction cuts only when the listener's change is narratively important and unreadable in the existing shot.

## Cost-efficient shot policy

- When the user prioritizes AI generation cost, normally use 3—4 effective SHOTs per 8—15 second segment. Use fewer only for genuinely low-density action that benefits from an uninterrupted performance.
- Every SHOT must carry dialogue, plot action, necessary spatial information, or a readable emotional turn.
- Do not allocate separate shots to environment, props, drinking, or repeated reactions unless they change the plot or emotional state.
- Prefer a fixed-camera long performance over multiple decorative inserts.
- Keep ordinary reaction shots around 0.8—2 seconds and complex microexpression transitions around 2—3 seconds. Merge a reaction into the dialogue or action shot when it does not justify its own cut.
- Any SHOT longer than 3 seconds must contain at least two explicit, timecoded, observable changes. Silence or an abstract emotion alone cannot occupy a long shot.

## Segment timing

- Keep every independent generation segment strictly within 4–15 seconds.
- Prefer 8–15 seconds unless a complete low-density beat naturally ends earlier.
- Reserve the final 1 second of every segment as a safety zone.
- Put no new dialogue, subtitle, character, prop, interface, action start, reveal, or plot information in the safety zone.
- If an action or sentence cannot finish naturally by 15 seconds, end at a complete semantic or action boundary and continue it in the next independent segment.
- Never accelerate speech merely to fit a segment.
- The final SHOT of one independent segment and the first SHOT of the next must not use the same shot size. Also vary lens or composition function so separately generated clips do not require pixel-matching poses.
- Bridge independent segments through sound, eyeline, action result, and prop state rather than asking the model to reproduce the previous final frame exactly.

## Dialogue timing

- Use 4.5–5 Chinese characters per second for calm or ordinary dialogue.
- Use 3.5–4 Chinese characters per second for heavy, sickbed, entrustment, crying, or grief dialogue.
- Allow faster speech only for explicitly agitated arguments or emergencies while retaining intelligibility.
- Reserve 0.3–0.6 seconds every time the speaker changes.
- Count spoken characters and allocate the dialogue window before scheduling reactions or actions.
- Preserve meaning when shortening long dialogue. Do not alter plot facts, intent, relationships, promises, rules, or emotional direction.
- Keep O.S. dialogue off-screen; do not generate the speaker unless the script explicitly cuts to them.
- Finish all dialogue before the final 1-second safety zone.

## Segment and SHOT hierarchy

Treat an independent generation segment and a SHOT as different levels:

```text
Episode
└─ Independent generation segment (4–15 seconds; timeline starts at 0)
   ├─ SHOT 01
   ├─ SHOT 02
   └─ SHOT 03...
```

- Use multiple SHOTs inside every segment; do not turn a 10–15 second segment into one continuous take unless the user explicitly requests a one-take shot.
- Normally use 3–6 SHOTs in an 8–15 second segment. Use fewer only when the action genuinely requires an uninterrupted take.
- Restart SHOT numbering at `SHOT 01` in every independent segment.
- Make SHOT time ranges contiguous with no gaps or overlaps, starting at 0 and ending exactly at the segment duration.
- State each cut, camera position, framing, lens, subject placement, timed action, expression, VFX, and dialogue.
- Preserve identity, wardrobe, prop state, UI state, eyeline, axis, lighting, and geography across cuts.
- Do not append bracketed labels such as `[无台词]` or `[角色：“台词”]` after a SHOT. Put each spoken line exactly once in its timecoded action interval; state non-dialogue sound in prose.

## Camera direction

- Use fixed shots for dialogue, UI reading, precise lip sync, micro-expressions, and complex hand or prop actions.
- Use slow push-ins for discovery, realization, pressure, or suspense.
- Use slow pull-backs for environmental revelation, isolation, or scene closure.
- Use small lateral moves to clarify spatial relationships.
- Use gentle pans for motivated eyeline or subject transitions.
- Use stable tracking only when a character or flying subject actually moves.
- Specify camera start, direction, followed subject, and final composition whenever the camera moves.
- Do not distribute movement evenly. Use movement only when it serves narrative information.
- Forbid unmotivated orbits, whip pans, repeated zooms, handheld shake, direction reversals, and simultaneous complex camera moves.

## Constraint placement

Include these exact sections at the beginning of every independent segment and repeat them after the SHOT script:

1. `【视频规格】`
2. `【时长与对白强制规则】`
3. `【场景、人物与资产锁定】`
4. `【统一空间与界面规则】`
5. `【剧情顺序强制声明】`
6. `【对白顺序强制声明】`
7. `【表演要求】`
8. `【光影与声音】`
9. `【特效限制】`
10. `【通用负向限制】`

Customize asset, plot, dialogue, performance, sound, VFX, and negative constraints for the current segment. Do not mention future characters or props in a way that may cause them to appear early. Do not paste a full-episode plot order into every segment.

## Output behavior

- Use the user's reference style, genre, resolution, frame rate, and asset tags when provided.
- If the user supplies no visual style, infer a coherent style from the script and label the assumption.
- Treat generated Chinese UI text as a post-production overlay unless the user explicitly requires in-model text generation; reserve stable text-safe areas and provide an exact overlay list.
- Produce deliverables rather than only describing the plan.
- Explain material runtime changes concisely. Preserve complete story meaning over mechanically forcing the suggested total duration.
- Do not ask questions when a safe assumption can be made. Ask only when missing assets or a decision would materially change the story.

## Validation

Before delivery, verify every segment:

- duration is 4–15 seconds;
- timeline begins at 0;
- SHOT numbering begins at 01 and is continuous;
- SHOT ranges have no gaps or overlaps;
- final SHOT ends exactly at segment duration;
- exactly the final 1 second is marked as safety zone;
- no dialogue enters the safety zone;
- dialogue timing meets the required speaking rate;
- speaker changes include reaction time;
- normally 3—4 effective SHOTs are present when cost control is requested, with no decorative empty shot;
- every SHOT longer than 3 seconds has at least two explicit, timecoded, observable changes;
- ordinary reaction shots are usually 0.8—2 seconds and complex microexpression transitions 2—3 seconds;
- every adjacent segment boundary changes shot size and also varies lens or composition function;
- SHOT scripts contain no bracketed duplicate dialogue or no-dialogue labels;
- all 10 required sections occur once before and once after the SHOT script;
- plot order, asset state, spatial axis, eyelines, lighting, and props remain continuous;
- each important acting beat has a trigger, observable micro-action, correct gaze target, and holdable residue;
- no microexpression conflicts with the character's physical action, shot size, or visibility;
- the last segment does not reveal a result the script intends to withhold.
