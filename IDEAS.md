# Ashcraft ideas

## queue (active — only remaining work)
- Real 2-tablet co-op test (Chris): partner dog + fetch from joining tablet, talking indicator/mic meter, partner sees your dances, pickaxe not covering touch buttons, tablet fps + glass look.
- TURN relay fallback — HELD: PeerJS 1.5.4 default config already uses Google STUN + PeerJS public TURN (eu-0/us-0.turn.peerjs.com:3478). A real fix needs our own TURN (TLS on 443, e.g. Cloudflare Calls TURN / metered.ca) with credentials; adding custom iceServers without a credentialed server would replace the defaults and could break existing rooms. Needs Chris to OK a TURN account.
- Real 2-tablet test of HOST BUILD (build together) + slot picker fits on tablet title screen.
- Real-device test on iPad Safari with a Bluetooth controller (B button opens emote wheel after victory; B still sneaks while held).
- Level 1 tutorial step for crafting polish; more block types (emissive only, never runtime lights).
- note: perf gate needs force-click on #play (5s click times out); patched copy at /tmp/gate.py

## done (10/22 evening)
- Push-to-talk voice (V / D-pad down / touch 🎙 HOLD) over PeerJS media call
- Minecraft controls: hold-to-break with crack, 9-slot hotbar + wheel, E inventory, Shift sneak, Ctrl / double-W sprint, F5 camera (first person default), glass + gold blocks
- Level 1: Ash Bus drop + glider, 6 step objectives with per-input hints, 2 loot chests (golden pickaxe 2x), sky island finale, VICTORY ASH confetti + dance, medals, goofy googly-eyed husks, sunset sky, embers, water shimmer, storm next-circle preview, splash respawn
- Late join snapshot (host sends all edits, crystals, timer)
- Build mode with IndexedDB autosave + export/import JSON (format {format:'ashcraft-world',v:1,edits:[...]}; keep stable)

## done (10/22 evening live pushes)
- iron sword (5c91db5) · day/night + night-only husks (f987de4) · storm removed (b36603e)
- bigger map + glass world wall + dig 6 deep w/ gold ore + soccer patch (1966a23)
- soccer ball + facing goals + score, co-op synced (e9e0fda)
- hidden loot common/rare/legendary + armor (fcb1bf2) · crafting table + recipe book (1f97ef2)

## done (10/27 evening live pushes)
- partner's ASHY dog visible in co-op, synced over PeerJS (efe4f89)
- ASHY tricks: sit (T / 🐶 SIT) + fetch the soccer ball (Y / ⚽ FETCH) (8a5c49a)
- build mode save keeps hotbar slot, sword/armor, camera; old saves still load (8ef7ba7)

## done (10/27 night)
- tablet pass: touch devices render at 1.25x pixel ratio (was up to 2x, ~60% fewer pixels) + 1024 shadow map; blocks already instanced (~50 draw calls, ~49k tris); glass no longer writes depth so glass behind glass shows; leaves opaque OK; late-join snapshot carries opened chests (dba680d)

## done (10/27 late night)
- late-join snapshot carries objective step + wave flag + husk hp; 'hk' msg also carries hp (old hosts/clients still compatible)
- husk wave at step 3: 3 husks spawn ~13 blocks ahead and walk at you so the wall matters (host/solo only, once per round)
- first-person held pickaxe viewmodel (iron, turns gold with golden pickaxe, swings when mining; no arm; hidden in 3rd person)

## done (10/27 late night, round 2)
- Emote wheel: B key / 💃 DANCE touch / controller B after victory; 8 kid-friendly goofy dances (classic, chicken, robot, spin, jumping jacks, noodle, floss, wiggle); partner sees your dance (optional 'dn' field in 'p', old clients ignore)
- Partner talking indicator ("🔊 ENZO TALKING") + mic level meters for you and partner (optional 'tk' field; WebAudio analyser only, no new lights)

## done (10/27 ~9:45pm)
- Build together: HOST BUILD on title hosts your current slot's build world; partner taps JOIN and gets it (snap carries optional bd:1). Edits sync both ways; host autosaves both kids' blocks; guest never overwrites its own saves. Save format unchanged {format:'ashcraft-world',v:1}.
- 3 build save slots (SLOT 1/2/3 on title, remembered; IndexedDB keys build1..3; old saves = slot 1). Export/import use the chosen slot.
- 3rd-joiner fix: the old connection's late 'close' event was wiping the new partner (NET=null, avatar removed). Close/error/data now only count for the current connection; stale avatar/dog cleared when a new partner joins.
