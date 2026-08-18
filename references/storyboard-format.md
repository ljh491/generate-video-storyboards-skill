# Storyboard output format

Use this reference whenever generating the final independent segment files.

## Table of contents

1. File structure
2. Opening constraint block
3. SHOT script structure
4. Ending constraint block
5. Timing example
6. Final checks

## File structure

Write one UTF-8 text file per independent generation segment:

```text
第X集第XX段｜本段具体事件标题（完整视频提示词）
本段时长：N秒｜时间线：0—N秒

【视频规格】
...

【时长与对白强制规则】
...

【场景、人物与资产锁定】
...

【统一空间与界面规则】
...

【剧情顺序强制声明】
...

【对白顺序强制声明】
...

【表演要求】
...

【光影与声音】
...

【特效限制】
...

【通用负向限制】
...

【镜头动作脚本】

SHOT 01｜0—X秒｜焦段＋主体＋景别｜机位或运镜
...

SHOT 02｜X—Y秒｜焦段＋主体＋景别｜机位或运镜
...

SHOT 03｜Y—N秒｜焦段＋主体＋景别｜机位或运镜
...

【段尾强制要求重申】

【视频规格】
...

（依次完整重复其余九个限制部分）
```

Give every segment a specific event title. Do not reuse the episode title as every segment title.

## Opening constraint block

### 视频规格

State style, rendering, aspect ratio, resolution, frame rate, exact segment duration, timeline reset, multi-SHOT requirement, and camera policy.

### 时长与对白强制规则

State the applicable speaking rate, speaker-change pause, exact final safety zone, and prohibition on adding information during it.

### 场景、人物与资产锁定

List only assets relevant to the current segment. Separate face and wardrobe references when supplied. Lock identities, quantities, proportions, costume, props, and state. Explicitly forbid future assets from appearing early.

### 统一空间与界面规则

Lock geography, screen direction, foreground/midground/background, eyelines, UI origin, UI facing, and text compositing policy.

### 剧情顺序强制声明

Write the current segment's causal chain with arrows. Include no future segment events.

### 对白顺序强制声明

List exact speaker order, exact lines, reaction intervals, O.S. status, lip-sync ownership, and final no-dialogue zone.

### 表演要求

Describe playable micro-actions: eyelids, pupils, brows, breathing, gaze, mouth, hand tension, posture, and response intensity. State prohibited exaggerations.

### 光影与声音

State motivated key light, fill, local practical light, exposure continuity, environment sound, action sound, interface sound, and dialogue voice character.

### 特效限制

Allow only effects required by the current actions. Specify physical origin, direction, density, duration, occlusion, and prohibited fantasy substitutions.

### 通用负向限制

Cover location drift, identity drift, wardrobe swaps, asset duplication, anatomy errors, prop physics, UI errors, camera errors, modern intrusions, text, watermarks, logos, and undesired style.

## SHOT script structure

Use the following presentation for every SHOT:

```text
SHOT 01｜0—3.5秒｜24mm海岛核心区大全景｜缓慢前推

硬切／承接上一镜头。

摄影机位于……，从……朝……拍摄。若运镜，说明起点、方向、速度、跟随对象和结束构图。

画面构成：

- 前景：……
- 中景：……
- 背景：……

0—2秒：

具体动作、视线、表情、物理反馈和声音。

2—3.5秒：

动作完成并形成下一个切点。

声音：环境声、动作声以及当前时间段内唯一一次准确对白。
```

Do not append bracketed labels such as `[无台词]`, `[角色：“台词”]`, or a duplicate dialogue list after a SHOT. Put dialogue exactly once in its timecoded action interval. For a silent SHOT, describe only the relevant environment and action sounds in prose.

For a fixed camera, describe its position and view direction. For a moving camera, describe its final framing. Do not write only “镜头移动”.

Use hard cuts by default. Use motivated match cuts, eyeline cuts, reaction cuts, or action cuts when beneficial. Do not introduce decorative transitions without narrative purpose.

## Ending constraint block

After the final SHOT, add `【段尾强制要求重申】` and repeat all 10 required constraint sections in full. Do not replace them with “同上”, a summary, or a reference to the opening block.

The ending block must remain segment-specific. Its purpose is to reinforce the current generation request, not to introduce later events.

## Timing example

For a 12-second independent segment:

```text
SHOT 01｜0—3秒
SHOT 02｜3—6.5秒
SHOT 03｜6.5—9.5秒
SHOT 04｜9.5—12秒

11—12秒｜安全区：保持当前构图、姿势和环境声，不新增任何信息。
```

The safety zone may occupy the final part of the last SHOT. It is not a separate new SHOT unless a deliberate hold shot is visually necessary.

For every pair of adjacent independent segments, the previous final SHOT and next first SHOT must use different shot sizes. Also vary lens or composition function. Preserve continuity through sound, eyeline, action result, and prop state rather than pixel-matching the previous frame.

Any SHOT longer than 3 seconds must include at least two explicit, timecoded, observable changes. Keep ordinary reactions around 0.8—2 seconds and complex microexpression transitions around 2—3 seconds; merge reactions that do not justify a separate cut.

Dialogue example at 5 characters per second:

```text
20-character calm line: allocate about 4 seconds.
Then reserve 0.3–0.6 seconds before another speaker begins.
```

Do not count punctuation as spoken syllables. Do count numbers according to how they will be spoken aloud.

## Final checks

- Open and ending constraint blocks each contain all 10 exact headings.
- The segment contains multiple SHOTs and is not accidentally a one-take.
- The internal timeline is continuous and starts at 0.
- Every camera move has a narrative reason and an end composition.
- Every speaker has enough time and owns the correct lip sync.
- O.S. speakers do not appear unless required.
- The final 1 second contains no new information.
- Adjacent segment boundaries use different shot sizes and do not depend on identical poses.
- Long SHOTs contain multiple observable timed changes rather than abstract emotional holds.
- SHOT scripts contain no bracketed duplicate dialogue or no-dialogue labels.
- All exact Chinese UI strings are collected for post-production.
- Each file stands alone without requiring another segment prompt.
