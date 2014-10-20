FluidFrames

Move, hide, scale, and resize frames with independent x&y axes.
http://www.wowinterface.com/downloads/info7080-FluidFrames.html

Usage Instructions:

Unsaved Movement
	Drag almost any normal UI Panel (e.g. CharacterFrame, SpellbookFrame, TalentFrame, QuestLogFrame, FriendsFrame, etc.) from any open space on the frame. This movement is intended to be for temporary changes and does not store location in the FluidFrames database. 
	However, this movement registers the frame as user placed.  The position will be remembered by the WoW client and restored on subsequent login/reloadui if not overridden by placement code (e.g. CharacterFrame, Minimap). Most of these draggable frames reset if you hide and re-show them. 
	Some frames will not reset automatically (e.g. GameMenuFrame, BattlefieldFrame). To reset these, highlight the frame, right click to reset and then reloadui/relog.
	The MinimapCluster is an added exception case and can be dragged by the top bar.
	Temporary dragging can be disabled using the checkbox in the Khoas options.

Saved Movement
	Setup a Binding - Assign a key-binding [Main Menu > Key Bindings > FluidFrames > Highlight Mouse Frame] to select, highlight and cycle through frames under the cursor. (The "Highlight All Mouse Frames" binding cycles through all frames under the cursor, including unnamed ones.)
	Highlight a Frame - Put your cursor over the frame you want to move and use the key-binding.  It will select the frame the furthest underneath. Consecutively using the key-binding will highlight frames closer to the front. Hold shift while using the key-binding to cycle backwards through the frames.
	Move - Drag the highlighted frame to relocate it permanently. It will disable movement from other code sources and save across sessions.
	Resize - Hold shift and drag from the sides or corners to resize.
	Re-scale - Hold shift and drag the bottom right re-scale icon to re-scale.
	Reset - Right-click to reset a moved/resized/rescaled frame once highlighted.

Bindings:
	Highlight Mouse Frame - Cycle through highlighting frames under the cursor (hold shift to cycle backwards)
	Highlight All Mouse Frames - Cycle through highlighting all frames under the cursor, including unnamed frames (hold shift to cycle backwards)

Notes:
	Dragging will also drag sibling frames. (Frames that have the same parent and are anchored to the frame you are dragging.)
	To drag some bars you have to drag the 1st button.
	To move the primary action button bar drag ActionButton1.
	To find the ShapeshiftBarFrame put your mouse over the left edge of the 1st button when using the key-binding.
	To drag all the player buffs & debuffs make sure you drag the TemporaryEnchantFrame.
	To move Chat Frames just unlock and use the default tabs.
	To drag the TargetFrame make sure you don't drag the TargetFrameTextureFrame on accident.
	To move the whole minimap drag the MinimapCluster.
	Experiment with which frame to change. if it doesn't work the way you wanted just right-click to reset.
	Some frames have complex sub frames that update their locations independent of parent size.  If resizing doesn't work well try scaling.
	If secure frames are moved by default blizzard code while in combat they cannot be moved back until after combat. Also, you will not be able to drag secure frames in combat.

Feedback & Support
If you have bugs or feature requests please use the buttons on the WoWInterface page.
For other feedback, use the comments. 
If you'd like to donate to show your support, that can be done through paypal with a paypal account or by credit card. Remember donations are much appreciated but non-contractual. Thank you!
https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4165527

FAQ:
Q) How do I use the same settings for all my characters?
A) Edit FluidFrames.toc and change "SavedVariablesPerCharacter" to "SavedVariables"

Q) How do I control a Vehicle/MindControl when the MainMenuBar is hidden.
A) Temporarily unhide the MainMenuBar, highlight it and drag it up off the bottom. Execute the script "/run BonusActionBarFrame:Show()". The BonusActionBarFrame should appear bellow the MainMenuBar. Highlight it and drag it where you'd like. Highlight the MainMenuBar, right click to reset it, then click the 'Hide' button above it and un-highlight it by using the binding again. Note that if you don't do this when hiding the MainMenuBar your primary action bar bindings may break when you leave a Vehicle/MindControl.

Change Log:

2.4h-60000
- .toc update

2.4g-50300
-----------
- .toc update, compatible with WoW 5.3 "Escalation"

2.4g-50200
-----------
- prevent taint to mail frame.
- .toc update, compatible with WoW 5.2.0

2.4f-50001
-----------
- prevent taint from RaidParentFrame.
- Fix ReforgingFrame so it's draggable from the top portion again.

2.4e-50001
-----------
- prevent taint from PetJournalParent

2.4d-40300
-----------
- MoP Beta compatibility (build 15799 tested)

2.4c-40300
-----------
- fix initialization for those players whose addon variables finish loading AFTER the player has entered the world.
for the technically inclined in wow 3.x and later VARIABLES_LOADED is not guaranteed to fire before PLAYER_ENTERING_WORLD on a 'cold login'

2.4b-40300
-----------
- attempt to fix the startup error with TimeManager reported by Kharthus
(still can't reproduce it myself)

2.4a-40300 (based on FluidFrames 2.4)
-----------
- taint prevention
- add TimeManager to options for dragging (default off, go into options to enable)
- fix PVPFrame dragging
- Update frame lists 
(we can no longer disable mouse on modelframes Blizzard 
has mouse scripts running for zoom / rotate etc on them now)
- set a couple more hooks for immobilized frames
- toc update, compatible with Hour of Twilight (4.3)

v2.3
- Added out of combat delays to re-hide and re-position secure frames that were moved in combat.
- Added dependent sibling frame detection to scale/resize/hide frames that had the same parent and whose position is exclusively dependent on the frame being scaled/resized/hidden or one of its other dependent sibling frames.
- Delayed SetParent and Show hooks to undo on the next OnUpdate so as to also catch dependent siblings parented or shown at the same time.
- Delayed SetPoint, SetParent and Show hooks to undo when you leave combat for secure frames.
- Refactored code to a number of files to make updating easier.

v2.2
- Enabled SendMailFrame, TokenFrame, and the PetPaperDollFrameCompanionFrame for dragging their parent frame
- Found a bug that was breaking UIChildWindows dragging, but then decided to just disable it by design, since those frames are all anchored to their parent frame, which are draggable.

v2.1
- Changed distribution to distribute FluidFrames with Portfolio unembedded.
- Fixed bug that caused LoD UI Panels to not be temporarily draggable
- TOC to 30000

v2.0
- Embedded Interface Config Option Panel (Using Portfolio instead of Khaos)
- Added Re-show All option, to show all hidden frames without resetting position.
- Fixed temporary dragging
