# Production Factory v1

## Mission
Turn an approved story package into reproducible production jobs without turning episodes into interchangeable templates.

## Factory stages
1. PREPARE
2. ASSET_BUILD
3. VOICE
4. STORYBOARD
5. ANIMATE_EDIT
6. CAPTION
7. THUMBNAIL
8. QA
9. PACKAGE
10. PUBLISH_READY

## Production job invariants
Every job must reference:
- episode_id
- story_package
- source/evidence record
- asset manifest
- rights provenance
- script version
- character/visual registry
- accessibility plan
- QA result

No final export is valid if an asset has unresolved rights status.

## Asset policy
Preferred order:
1. project-created original assets
2. public-domain assets with provenance
3. compatible licensed assets with permission evidence

Do not use copyrighted screenshots, clips, music, or character likenesses unless the rights record explicitly permits the intended use.

## Accessibility baseline
- synchronized captions
- readable on-screen text
- sufficient pacing
- important visual information represented in audio/captions where needed
- no essential meaning conveyed only by color
- final disclaimer remains legible

## QA layers
Content QA: claims match the verified claim ledger.
Story QA: clear beginning, progression, and resolution.
Originality QA: materially different substance from recent episodes.
Rights QA: every final asset has traceable rights status.
Accessibility QA: captions, text, pacing, and visual communication pass.
Technical QA: duration, audio, video, captions, metadata, and export integrity pass.

## Release gate
PUBLISH_READY requires final_video, captions, rights_provenance, qa_pass, metadata, thumbnail, no critical incident, and authorized publishing credentials.

If external publishing is unavailable, stop at PUBLISH_READY; never fabricate a publication URL.

## Monetization safety
Automation may assist research, orchestration, editing, QA, and asset generation. The finished episode must still show a distinct creative/educational purpose. Current YouTube guidance distinguishes materially varied series from repetitive or mass-produced content. citeturn0search0turn0search6
