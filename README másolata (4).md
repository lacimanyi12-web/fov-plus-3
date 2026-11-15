# FovPlus (Quest, Beat Saber 1.40.8_7379)

Adjustable FOV for **non-headset cameras** (casting / capture / replay-style cameras),
with an in-game settings tab. It does NOT change the FOV you see inside the headset.

## Set up the project
1. Generate a project from the official Quest mod template (BSMG wiki: "Quest Mod Development Intro").
2. Copy `src/` and `include/` from this folder into it (replace the template's main.cpp, keep its
   CMakeLists.txt / scripts; make sure CMake globs `src/*.cpp`).
3. Replace the template's `mod.template.json` fields with the ones in this folder's file
   (qpm fills in the dependency list on `qmod` build).
4. Add dependencies:
       qpm dependency add beatsaber-hook
       qpm dependency add bs-cordl -v "4008.*"
       qpm dependency add custom-types
       qpm dependency add bsml
       qpm dependency add paper2_scotland2
       qpm restore

## Build / package / install
       qpm s qmod          # builds and produces FovPlus.qmod (see the template's scripts)
Then in ModsBeforeFriday: Upload File -> FovPlus.qmod -> Sync to Beat Saber.
For dev iteration with USB debugging: `qpm s copy` (and `qpm s logcat` / `qpm s restart`).
Script names come from the template; run `qpm s` to list what your copy has.

## Use
Main menu -> mod tab "FovPlus". Press "Log cameras to logcat" while your cast/capture camera is
active, find its name in the log, and put a substring of it in
`/sdcard/ModData/com.beatgames.beatsaber/Configs/FovPlus.cfg` as `nameFilter=...`.
