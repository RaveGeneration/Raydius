# Changelog

## 1.0.0 (2026-11-26)

### New

- Side chain input. Studio One and Logic send audio into an instrument only through its side chain, so the vocoder and the Audio In programs (N15, O01..O16) could not hear your voice there. Raydius now listens to its side chain as well as to its normal audio input. Studio One: choose the track with your voice in the Sidechain menu at the top of the Raydius window. Logic: choose it in the Side Chain menu at the top right of the plug-in window. Then play notes.

### Fixed

- Long names in the menu boxes, such as FLT1 RESONANCE in the PATCH Destination boxes, no longer run past the edge of the box.

### Unchanged

- All factory programs sound as in 0.9.8, and the normal audio input works as before (checked sample for sample).

## 0.9.8 (2026-11-25)

### Fixed

- Projects and presets keep every edit, step data too, with the window closed as well. Until now edits made with the window closed could be lost when a project was saved or bounced, when the buffer size or sample rate changed, or when a preset was loaded. Undo and redo bring back the exact sound.
- A project with a user program opens with its sound on a computer that does not have that program.
- Many controller moves at once (mod wheel, pitch bend, automation) no longer make notes late (up to 2.8 seconds).
- Automation of very many controls, or programs changed very fast, no longer leaves Raydius busy for minutes after it.
- An effect could stay silent until Raydius was loaded again, after many changes at once that put Rotary Speaker or Talking Mod on insert effect 2 (they are for insert effect 1 only: choosing them there goes back to the effect before).
- A key held while Raydius loads sounds when it is ready.

### Unchanged

- All factory programs sound as in 0.9.7 (checked sample for sample).

## 0.9.7 (2026-11-24)

### New

- Follow DAW Tempo. The DAW button under the Tempo knob (PROGRAM page): arpeggiator, step sequencers, mod sequencers, synced LFOs and synced delays run at your DAW's tempo and stay on its beat, through tempo changes, loops and locates. Off by default; the program keeps its own tempo, which comes back when you switch it off.
- Save your own sounds. SAVE on the PROGRAM LIST page: give it a name and click a user place (or NEXT FREE). The sound becomes a user program and a .syx file in the User Programs folder, which you can share or send to a RADIAS. A sound saved at that place before moves to the folder Replaced; nothing is deleted.
- Envelope follower. It stood still until now. It follows the audio input or the internal bus, moves what is patched to EnvF, and its trigger notes play. Factory programs that change by it: D05, E01, G02, I05, J01, J03, M16; with audio coming in also N10, O05, O09 and the Audio In programs with trigger notes.
- The version number in the window (top right), and Tempo reads in BPM (145.0).

### Fixed

- Audio input: in 0.9.6 the sound coming in was scrambled into noise, always at the same level. Now it is the sound you send, at the level you send it, so the vocoder programs and Audio In programs really work.
- Internal bus: the same fault. C03, F03, I01, I03, J03, K16 and N15 (and O06 with audio coming in) were too loud and partly noise; N15 is 18 dB softer now.
- Turning Tempo while a program plays now also reaches its synced LFOs and mod sequencers (programs without the arpeggiator or step sequencers: they kept the old tempo).
- A knob turned while the arpeggiator or a step sequencer plays could make one step come late or split in two.
- All notes off (a DAW stopping) could leave a held key hanging while a step sequencer played on its channel.
- When a DAW starts playing, the first notes are no longer up to 15 ms late.
- A mono track no longer crashes Raydius; it plays left and right mixed together.
- Very small buffers (16 samples at 48 kHz, 32 at 96 kHz) could hang the DAW.
- Rotary Speaker or Talking Mod on insert effect 2 could silence Raydius for good after loading a project.
- An offline bounce no longer starts with a few silent seconds while Raydius loads.
- MIDI controllers (volume, pan, expression, cutoff, resonance) work in programs with the arpeggiator or a step sequencer on. A MIDI program change no longer changes the sound behind the plugin's back.
- A DAW stopping with the sustain pedal down no longer leaves notes sounding.
- A single .syx file could not be loaded when a library had filled the user programs with blank Init Programs. It takes the first of those places now (NEXT FREE does too).

### Unchanged

- All other factory programs sound as in 0.9.6 (checked sample for sample without audio coming in: the same, but for eight that differ far below what can be heard).

## 0.9.6 (2026-11-23)

### New

- Audio input. Raydius has two audio inputs now, like AUDIO IN 1 and 2 on the RADIAS: left is input 1, right is input 2 (the vocoder's mic input). Send audio from your DAW into Raydius to play the vocoder programs and the programs that use Audio In, for example O01 Ens Vocoder and O13 AudioIn INIT. Your DAW's send level does the job of the AUDIO IN knobs: keep the input below clipping.
- Internal bus. A timbre set to Sub Output IntBus now feeds the vocoder and the other timbres, as on the hardware. Until now that sound was lost, so some factory programs were silent or missing a part:
  - C03 Codex Rhythm: was silent, now plays.
  - N15 Source Code: was silent, now plays. It plays very loud; we are checking that against a real RADIAS.
  - O06 Mono Vocoder: now works with audio coming in.
  - F03 Amalgam, I03 Wah Guitars, K16 Bass Chime: their missing part is back.
  - I01 FormantMorph, J03 NoteRezoDrum: small changes.
- Copy Timbre from another program. The TIMBRE row has a FROM choice: pick any factory or user program in the program list, and COPY takes its timbre into the current program.

### Changed

- SEQ STEPS: the notes in the piano roll start right on their grid line, as in a DAW.

### Unchanged

- All other factory programs sound exactly as in 0.9.5 (checked sample for sample).

## 0.9.5 (2026-11-14), first public release

- The RADIAS OS 2.0 and sound engine, native: about half a core to one core per instance while it plays.
- Every program parameter as a plugin parameter (906), step data through selectors.
- Program page with the 256 factory programs and 256 user programs; .syx and .rdl files load by drop or LOAD.
- Copy, Swap and Init Timbre (the TIMBRE row), as on the RADIAS's UTILITY page.
- Projects keep every edit.
