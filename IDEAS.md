# Ashcraft ideas

## done (10/22 evening)
- Push-to-talk voice (V / D-pad down / touch 🎙 HOLD) over PeerJS media call
- Minecraft controls: hold-to-break with crack, 9-slot hotbar + wheel, E inventory, Shift sneak, Ctrl / double-W sprint, F5 camera (first person default), glass + gold blocks
- Level 1: Ash Bus drop + glider, 6 step objectives with per-input hints, 2 loot chests (golden pickaxe 2x), sky island finale, VICTORY ASH confetti + dance, medals, goofy googly-eyed husks, sunset sky, embers, water shimmer, storm next-circle preview, splash respawn
- Late join snapshot (host sends all edits, crystals, timer)
- Build mode with IndexedDB autosave + export/import JSON (format {format:'ashcraft-world',v:1,edits:[...]}; keep stable)

## queue
- Snapshot should also carry opened chests, objective step and husk hp.
- Husk "wave" event at step 3 (spawn 3 husks walking toward the player so the wall matters).
- B button / emote wheel on victory screen; more dances.
- First-person held pickaxe viewmodel (arm not visible in first person).
- Partner talking indicator; mic level meter.
- TURN relay fallback for networks where peer-to-peer fails.
- Build mode co-op (share build world over PeerJS), multiple save slots.
- Verify late-join partner avatar appears for 3rd joiner (test showed snapshot OK but avatar flag false once).
- Real-device test on iPad Safari with a Bluetooth controller.

## done (10/22 evening live pushes)
- iron sword (5c91db5) · day/night + night-only husks (f987de4) · storm removed (b36603e)
- bigger map + glass world wall + dig 6 deep w/ gold ore + soccer patch (1966a23)
- soccer ball + facing goals + score, co-op synced (e9e0fda)
- hidden loot common/rare/legendary + armor (fcb1bf2) · crafting table + recipe book (1f97ef2)

## queue (next)
- show partner's armor/weapon in co-op; ball state in late-join snapshot (now arrives within 1/16s via 'ball' msg)
- pets (dog that follows), more block types (torch-like glow via emissive only), level 1 tutorial step for crafting
- perf: merge/instance block meshes (world now ~4.3k meshes)
- perf instanced blocks (e67a6a8) · partner gear + ball/score in snapshot (6e63e00) · craft step + lamp/wool blocks + scrolling hotbar (8a9c8e4) · pet dog ASHY (latest)

## done (10/27 evening live pushes)
- partner's ASHY dog visible in co-op, synced over PeerJS (efe4f89)
- ASHY tricks: sit (T / 🐶 SIT) + fetch the soccer ball (Y / ⚽ FETCH) (8a5c49a)
- build mode save keeps hotbar slot, sword/armor, camera; old saves still load (8ef7ba7)

## done (10/27 night)
- tablet pass: touch devices render at 1.25x pixel ratio (was up to 2x, ~60% fewer pixels) + 1024 shadow map; blocks already instanced (~50 draw calls, ~49k tris); glass no longer writes depth so glass behind glass shows; leaves opaque OK; late-join snapshot carries opened chests (dba680d)

## queue (after 10/27)
- real 2-tablet co-op test of partner dog + fetch (client fetch goes through host 'kick')
- note: perf gate needs force-click on #play (5s click times out); patched copy at /tmp/gate.py

## done (10/27 late night)
- late-join snapshot carries objective step + wave flag + husk hp; 'hk' msg also carries hp (old hosts/clients still compatible)
- husk wave at step 3: 3 husks spawn ~13 blocks ahead and walk at you so the wall matters (host/solo only, once per round)
- first-person held pickaxe viewmodel (iron, turns gold with golden pickaxe, swings when mining; no arm; hidden in 3rd person)
