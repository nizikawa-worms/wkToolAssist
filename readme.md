# wkToolAssist v. 0.1.0

Binary-only release.

wkToolAssist is a WormKit module that implements some features present in Tool Assisted WA Builds by Deadcode.

Features:
- Adjust game speed at any time
- Set checkpoints to rollback game state
- Step frame forward/backward
- Show trajectories of moving worms, projectiles and mines
- Show overlay info with worm position, speed and state
- Record .wagame replays in a format compatible with stock WA

Limitations:
- To prevent abuse, the module comes bundled with a special version of WA.exe with disabled network functionality. The module is closed source.
- Version 0.1.0 lacks the ability to edit existing replays. This feature is planned for version 0.2.0
- Recorded replays contain chat message about wkToolAssist being used
- Team flags are replaced with "TA" flag

Installation:

- Extract ToolAssist.dll and TA_*.exe matching your WA version to your Worms Armageddon installation directory.
- Launch TA_*.exe
- Disable wkJellyWorm and wkRealTime if you have them installed
- The module does not work under WINE

Controls:
- Keys 0-9 - set game speed to predefined values:
- 1: 1.0x,
- 2: 0.5x,
- 3: 0.25x
- 4: 0.15x
- 5: 0.1x
- 6: 0.05x
- 7: 0.025x
- 8: 0.0125x
- 9: 0.005x
- 0: stop time

- Keys + - increase/decrease game speed by 0.01x
- Keys [ ]  step a single frame backward/forward
- Key S - save current frame as checkpoint
- Key R - restore game state to the last checkpoint
- Key Z - remove last checkpoint and restore state to the previous one
- Key ~ - revert game to frame 0 and start playing until the last checkpoint

Notes on keyboard inputs:
- Game controls in stock WA are buggy at game speeds 0.25x and below. To fix this problem the module implements it's own keyboard handling logic and uses it at speeds <= 0.25x
- The custom key logic does not respect custom mappings used in wkRemapKeys
- Some keys such as space or enter are set as sticky - pressing them once remembers the state until the next time the key state is read by the game, usually on the next logic frame.
- To "unpress" sticky key, hold shift and press the keyboard key you want to unpress.
- The list of active keys is displayed in the screen corner
