# Lizzie-improvements

<!-- TOC -->

- [Lizzie-improvements](#lizzie-improvements)
    - [Lizzie - Leela Zero Interface](#lizzie---leela-zero-interface)
    - [Running a release](#running-a-release)
        - [Building Leela Zero](#building-leela-zero)
        - [Building Lizzie](#building-lizzie)
        - [Running Lizzie](#running-lizzie)
    - [Changes in the initial release (v1.0)](#changes-in-the-initial-release-v10)
        - [Fix #727 (winrate graph for LCB)](#fix-727-winrate-graph-for-lcb)
            - [About Lcb](#about-lcb)
        - [Fix #701 (wrong winrate in WinratePane)](#fix-701-wrong-winrate-in-winratepane)
        - [Remove redundant score display to fix #683](#remove-redundant-score-display-to-fix-683)
        - [Add play sound](#add-play-sound)
        - [Show GTP console during initial tuning of KataGo](#show-gtp-console-during-initial-tuning-of-katago)
        - [Update obsolete "Leela Zero" in DisplayStrings_ja_JP](#update-obsolete-leela-zero-in-displaystrings_ja_jp)
        - [About background image](#about-background-image)
        - [About komi 6.5 points](#about-komi-65-points)
    - [Changes in v1.1](#changes-in-v11)
        - [Fixed initial placement for handicap games](#fixed-initial-placement-for-handicap-games)
        - [Fix obsolete "Leela Zero" for the default player name](#fix-obsolete-leela-zero-for-the-default-player-name)
        - [Fixed a bug where the win rate graph would cross the board](#fixed-a-bug-where-the-win-rate-graph-would-cross-the-board)
        - [Fix saveBackRouting skipping nodes](#fix-savebackrouting-skipping-nodes)
        - [Fix: "Pondering on/off" was not updated by Analyze button](#fix-pondering-onoff-was-not-updated-by-analyze-button)
        - [Fix (scoreMean & scoreStdev)](#fix-scoremean--scorestdev)
        - [Option to opaquely paint grayscale territory prediction on board](#option-to-opaquely-paint-grayscale-territory-prediction-on-board)
    - [Changes in v1.2](#changes-in-v12)
        - [Fixed a bug that lizzie freezes when loading certain FOX GO SGF files](#fixed-a-bug-that-lizzie-freezes-when-loading-certain-fox-go-sgf-files)
        - [Show error dialog for typical engine troubles](#show-error-dialog-for-typical-engine-troubles)
        - [Fix parsing GAMEINFOMAIN when GONGJE is missing](#fix-parsing-gameinfomain-when-gongje-is-missing)
        - [Avoid infinite loop in switchEngine](#avoid-infinite-loop-in-switchengine)
        - [Fix #745 (NPE after initial config)](#fix-745-npe-after-initial-config)
    - [Changes in v1.3](#changes-in-v13)
        - [ecord startup log for #756 even when printCommunication is not set #759](#ecord-startup-log-for-756-even-when-printcommunication-is-not-set-759)
        - [Show dialog for #756 when engine ended unintentionally](#show-dialog-for-756-when-engine-ended-unintentionally)
        - [Show "Engine is down." in trouble instead of "Engine is loading..."](#show-engine-is-down-in-trouble-instead-of-engine-is-loading)
        - [Show GTP console when engine ended unintentionally](#show-gtp-console-when-engine-ended-unintentionally)
        - [Import komi fix for Fox SGF from KaTrain (ref. #755)](#import-komi-fix-for-fox-sgf-from-katrain-ref-755)
        - [Fix #752 (deadlock by Fox SGF)](#fix-752-deadlock-by-fox-sgf)
    - [Changes in v1.4](#changes-in-v14)
        - [Fix #765 (handicap bug in #758) #766](#fix-765-handicap-bug-in-758-766)
        - [Improve subboard and add option not refresh variation when displayed](#improve-subboard-and-add-option-not-refresh-variation-when-displayed)
        - [A try about new logo](#a-try-about-new-logo)
        - [Fix: "Engine is down." was not shown for panel UI](#fix-engine-is-down-was-not-shown-for-panel-ui)
        - [bump version to 0.7.4 #720](#bump-version-to-074-720)
        - [Correct inconsistent indents #763](#correct-inconsistent-indents-763)
        - [Update contributors #764](#update-contributors-764)
    - [Changes in v1.4.1](#changes-in-v141)
        - [Fix missing movenum in subboard #770](#fix-missing-movenum-in-subboard-770)
    - [Changes in v1.5](#changes-in-v15)
        - [Disable "Avoid Keep Variations" if it is 0](#disable-avoid-keep-variations-if-it-is-0)
        - [right-click to undo in panel UI](#right-click-to-undo-in-panel-ui)
        - [click to redo in panel UI](#click-to-redo-in-panel-ui)
        - [Fix wrong variation number on subboard](#fix-wrong-variation-number-on-subboard)
    - [Changes in v1.6](#changes-in-v16)
        - [Display existing .sgf file when savingfile](#display-existing-sgf-file-when-savingfile)
        - [Allows reading of uppercase .SGF and .GIB files](#allows-reading-of-uppercase-sgf-and-gib-files)
        - [Display an arbitrary engine name instead of the weight file name](#display-an-arbitrary-engine-name-instead-of-the-weight-file-name)
        - [Toggle large winrate graph by mouse click of center button](#toggle-large-winrate-graph-by-mouse-click-of-center-button)
        - [Restore all checks in View > Panel at startup](#restore-all-checks-in-view--panel-at-startup)
        - [overflow of pondering message in Panel UI](#overflow-of-pondering-message-in-panel-ui)
        - [Fix wrong "Engine is loading..."](#fix-wrong-engine-is-loading)
        - [Fix obsolete "Pondering on" by Analyze > Toggle analyze](#fix-obsolete-pondering-on-by-analyze--toggle-analyze)
        - [variation tree was not updated by click to redo in panel UI](#variation-tree-was-not-updated-by-click-to-redo-in-panel-ui)
        - [Display the analysis result when the file is loaded](#display-the-analysis-result-when-the-file-is-loaded)
    - [Changes in v1.7](#changes-in-v17)
        - [Problems with the variation tree](#problems-with-the-variation-tree)
        - [Issues related to "Settings→Theme→Winning Rate Change Node"](#issues-related-to-settings→theme→winning-rate-change-node)
        - [Winning rate change node for trial](#winning-rate-change-node-for-trial)
        - [There is something wrong with the window that appears in Settings→Theme.](#there-is-something-wrong-with-the-window-that-appears-in-settings→theme)
        - [Overwrite storage issues](#overwrite-storage-issues)
    - [Changes in v1.8](#changes-in-v18)
        - [Leela 0.11.0 on Lizzie 0.7.4](#leela-0110-on-lizzie-074)
        - [Accept only numbers as blunder thresholds](#accept-only-numbers-as-blunder-thresholds)
        - [Make the threshold 0.0 usable for the blunder color of "normal" moves](#make-the-threshold-00-usable-for-the-blunder-color-of-normal-moves)
        - [Fix(slow play/undo/redo)](#fixslow-playundoredo)
        - [Fix #805(The ">>" doesn't work properly)](#fix-805the--doesnt-work-properly)
        - [Fix overflow of variation tree with largeSubBoard in normal UI](#fix-overflow-of-variation-tree-with-largesubboard-in-normal-ui)
        - [Win rate graph related](#win-rate-graph-related)
        - [Fix: Remove wrong-sized ownership marks](#fix-remove-wrong-sized-ownership-marks)
        - [Fix: Up arrow key does not work just after click on a suggested move …](#fix-up-arrow-key-does-not-work-just-after-click-on-a-suggested-move-)
    - [Changes in v1.9](#changes-in-v19)
        - [Fix(playouts "1.5k" is wrongly read as 15000 in SGF)](#fixplayouts-15k-is-wrongly-read-as-15000-in-sgf)
        - [Show background playouts](#show-background-playouts)
        - [Added engine full command as tooltip for easier engine selection](#added-engine-full-command-as-tooltip-for-easier-engine-selection)
        - [Force UTF-8 for saving SGF](#force-utf-8-for-saving-sgf)
    - [Changes in v2.0](#changes-in-v20)
        - [Update DisplayStrings_ko.properties](#update-displaystrings_koproperties)
        - [Fix wrong getCoord which leads analysis hangs when enable katago ownership in rectangle board](#fix-wrong-getcoord-which-leads-analysis-hangs-when-enable-katago-ownership-in-rectangle-board)
        - [only update last-folder if there is something to update](#only-update-last-folder-if-there-is-something-to-update)
    - [Changes in v2.1](#changes-in-v21)
        - [Set region of interest like KaTrain 1.7](#set-region-of-interest-like-katrain-17)
    - [Changes in v2.2](#changes-in-v22)
        - [Strengthening the engine menu](#strengthening-the-engine-menu)
        - [Region of interest](#region-of-interest)
        - [Revive score mode](#revive-score-mode)
        - [Add Help menu](#add-help-menu)
        - [Switch rules from the menu](#switch-rules-from-the-menu)
        - [Fix typo](#fix-typo)
        - [Show message when autoanalysis is denied](#show-message-when-autoanalysis-is-denied)
    - [Changes in v2.3](#changes-in-v23)
        - [append player rank to player name](#append-player-rank-to-player-name)
        - [Apply Japanese rules by default](#apply-japanese-rules-by-default)
        - [Variation windows movenum](#variation-windows-movenum)
        - [Fix D key (toggle "show KataGo score mean")(Limited to Katago)](#fix-d-key-toggle-show-katago-score-meanlimited-to-katago)
        - [Continue analysis off after autoplay](#continue-analysis-off-after-autoplay)
        - [Partial change of key operation explanation](#partial-change-of-key-operation-explanation)
        - [About the opacity slide function of the candidate move](#about-the-opacity-slide-function-of-the-candidate-move)

<!-- /TOC -->

日本語での説明は、こちらのリンク先をご覧ください→
https://ameblo.jp/hope366/entry-12653845300.html

## Lizzie - Leela Zero Interface
![GIF 2020-07-13 12-46-35](https://user-images.githubusercontent.com/63999713/87269204-6d744200-c507-11ea-80aa-263f24205251.gif)
Lizzie is a graphical interface allowing the user to analyze games in
real time using [Leela Zero](https://github.com/gcp/leela-zero). You
need Java 8 or higher to run this program.

See the [Wiki](https://github.com/featurecat/lizzie/wiki) for learning more.

[![Build Status](https://travis-ci.org/featurecat/lizzie.svg?branch=master)](https://travis-ci.org/featurecat/lizzie?branch=master)


## Running a release

Just follow the instructions in the provided readme in the
[release](https://github.com/featurecat/lizzie/releases/tag/0.7.2).

The first run may take a while because Leela Zero needs to set up the
OpenCL tunings. Just hang tight, and wait for it to finish, then you
will see Leela Zero's analysis displayed on the board. Feel free to supply
your own tunings, as this will speed up the process. Do this by copying
any `leelaz_opencl_tuning` file you have into the directory.

### Building Leela Zero

First, you will need to have a version of Leela Zero that
continually outputs pondering information. You can get this from one
of the Lizzie releases or build it yourself; just compile from the **next**
branch of Leela Zero (see http://github.com/gcp/leela-zero/tree/next for more
details).

    $ git clone --recursive --branch next http://github.com/gcp/leela-zero.git

### Building Lizzie

The simplest way to build Lizzie is to use [Maven](https://maven.apache.org/).

To build the code and package it:

    $ mvn package

### Running Lizzie

    $ java -jar "target/lizzie-0.7-shaded.jar"

(or whatever the current version of the shaded `jar` file is in
`target/`).

After you run this command you should see a GUI start. Lizzie will also start a Leela Zero
process that it will communicate with. You can configure the location of Leela Zero from the
`config.txt` file from the folder you started the `java` command. If Lizzie is unable to start
Leela Zero it will display an error and you can fiddle with the `config.txt` file
until you get all the paths correct.

Lizzie will provide multitude of options to load and save SGF files, run an auto analysis and
configure the board. To see all the options just hold down the key **x** (yes, just press and hold
the letter **x**) and you will see all the commands listed in the GUI.

## Changes in the initial release (v1.0)

### Fix #727 (winrate graph for LCB)

 When studying with katago in lizzie, there was a problem in drawing the graph when the winning rate display method was Lcb.If the score difference becomes extremely large, the graph will not be drawn correctly and the vertical movement will be repeated violently.This has been improved in v1.0.
 This screenshot shows a 5 stone handicap game setup. White 2, 4, 6, 8 are passes.

<img src="https://user-images.githubusercontent.com/63999713/87446286-13bd6600-c634-11ea-88e7-39baf95f3f55.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87453050-eb863500-c63c-11ea-9bf9-69409e921ed3.jpg" width="45%">



#### About Lcb

 With LeelaZero, for example, Q3 is searched 10 times and the average win rate is 43.16%.
 LCB at this time is 40.86%.

 Q3 -> 10 (V: 43.16%) (LCB: 40.86%)

 In 10 searches, the winning rate of 43.16% shifts 2.3% (43.16-40.86) up and down,
 In other words, the true win rate is in the range below.

 40.86% <= 43.16% <= 45.46%

 This smaller one is the LCB, and as the number of searches increases, the deviation becomes smaller and the LCB approaches 43.16%.Generally, MCTS starts the one with the largest number of searches in Root, but Leela Zero uses the one with the largest LCB.I'm supposed to choose. This was about +70 Elo stronger.

### Fix #701 (wrong winrate in WinratePane)

 This screenshot is the second station of the 5th match of Alpha Go and Isedle 9th dan.The screenshot left is a real-time analysis, and the screenshot right is a sgf file saved in panel UI mode and loaded.The screenshot left showing the white win rate of 34.3% is correct and the screenshot right shows the previous number.This bug has been fixed.

<img src="https://user-images.githubusercontent.com/63999713/87452256-f5f3ff00-c63b-11ea-89be-9d7391379bf5.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87452332-115f0a00-c63c-11ea-9663-ca889d3a0095.jpg" width="45%">


### Remove redundant score display to fix #683

 Although the numerical value showing the disparity information is displayed in the upper center of the winning percentage bar, there was a bug that the numerical value here was always 0 when the pre-analyzed sgf file was read and moved with pondering off.In v1.0 this confusing display has been removed.

### Add play sound

 Put the jar file and the sound folder in the lizzie folder.When you start lizzie, an item called Settings → Play Sound has been added, so you can switch on/off the start sound here.You can also switch by ""play-sound": true," in config.txt.

### Show GTP console during initial tuning of KataGo

 Tuning is performed only the first time when the OpenCL version of katago is started with lizzie, so it may take a considerable time depending on the performance of the computer.So some people may give up thinking it is a bug or freeze.With this fix, the GTP console is displayed only at the first startup, and you can see that the tuning work is being performed internally.To verify, delete the KataGoData folder in the lizzie or katago folder and then launch the OpenCL version of katago with lizzie.

### Update obsolete "Leela Zero" in DisplayStrings_ja_JP

 In the official release version, "Leela Zero is loading" will continue to be displayed in the lower left until the analysis starts, regardless of the engine type.The modified version will display "Loading engine".

<img src="https://user-images.githubusercontent.com/63999713/87438168-2894fc00-c62a-11ea-8f0d-0de55759c7eb.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87439880-42374300-c62c-11ea-8da6-e2e0424b2dd1.jpg" width="45%">



### About background image

 In v1.0, the starry sky background is applied by default, but the user can apply any image.For the background image, put your favorite image in the yasnaya folder in the thema folder of the Lizzie folder, set the upper menu to yasnaya in the theme tab from the settings of the upper menu, and you can make it your favorite image with the path of the background image below it. I will. (It will be reflected when Lizzie is restarted after the change)
 We also recommend 1920x1080 as the size of the image file used. If the file size is small, it may not be displayed properly.

### About komi 6.5 points

 In the official release version, komi is set to 7.5 points, but it has been changed to apply 6.5 points at startup.This is convenient when using katago to consider Japanese rules and Korean rules. leelazero has no effect because it does not support variable komi.

## Changes in v1.1

### Fixed initial placement for handicap games

 In KataGo's handicap game, the initial placement was randomly determined, but it has been changed to the official placement.

 <img src="https://user-images.githubusercontent.com/63999713/87868402-1fac7d80-c9d0-11ea-8d12-6b4f9f78aae0.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87868427-584c5700-c9d0-11ea-822f-fc9c6c1790a2.jpg" width="45%">

### Fix obsolete "Leela Zero" for the default player name

 When playing a new game with KataGo, "Leela Zero" was displayed in the game info dialog box and the player name at the bottom of the board, but it has been changed to "AI".

  <img src="https://user-images.githubusercontent.com/63999713/87859317-49818800-c96f-11ea-9fcd-c48f721e76d1.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87859331-6453fc80-c96f-11ea-88b0-53d9aa8d0378.jpg" width="45%">

### Fixed a bug where the win rate graph would cross the board


 When loading a pre-analyzed sgf file and moving it from the beginning with pondering off, if the automatic width adjustment of the winning percentage graph is enabled, the graph appears to cross the main board greatly.This bug has been fixed in v1.1.

  ![graph](https://user-images.githubusercontent.com/63999713/87859391-cd3b7480-c96f-11ea-92a9-4fcc5df0f0c6.jpg)

### Fix saveBackRouting skipping nodes

 See the screenshot below. In the above screenshot, switch the engine from Katago to leelazero. It should be in the same phase, but the result will show the point of another previous branch, as in the screenshot below.Thus, if you have several branches, switching engines may show aspects of another previous branch. This bug has been fixed in v1.1.

![GIF 2020-07-13 14-43-42](https://user-images.githubusercontent.com/63999713/87859408-ec3a0680-c96f-11ea-914e-f4a0b105b5fd.gif)

### Fix: "Pondering on/off" was not updated by Analyze button

 When Pondering on is displayed, click the "Analysis" button on the toolbar to stop the search on the board. However, it does not update to "Pondering off" until you move the mouse cursor over the main board. In the modified version, "Pondering off" is displayed immediately after clicking the "Analysis" button.

 ![GIF 2020-07-19 3-40-03](https://user-images.githubusercontent.com/63999713/87859677-e8a77f00-c971-11ea-8a14-f4854c109022.gif)

### Fix (scoreMean & scoreStdev)

 There are three items above the winning percentage graph: "mean", "stdev", and "Last move". In real-time analysis, all three work normally, but when moved with the pondering off, "mean" and "stdev" are fixed at the final numerical values ​​and do not work properly.In v1.1, these two non-functioning items were hidden when moving with pondering off.

### Option to opaquely paint grayscale territory prediction on board

 About the lower menu "Kata Estimate", added the option to display with opaque white to black paint.To switch, go to View → KataGo Settings → Trend Information → Brend with board. The shortcut key is "Shift-Period". The changes will be reflected when you turn on Pondering on.

 <img src="https://user-images.githubusercontent.com/63999713/87859685-fe1ca900-c971-11ea-84e9-413694fde269.jpg" width=45%> <img src="https://user-images.githubusercontent.com/63999713/87859692-112f7900-c972-11ea-9bbc-9a1e682184d9.jpg" width=45%>

## Changes in v1.2

### Fixed a bug that lizzie freezes when loading certain FOX GO SGF files

 Some FOX GO game records contain many explanations and branches. This is often seen in official competitions between professionals.
 If you save this and load it with lizzie, lizzie may freeze. This bug has been fixed in v1.2.

### Show error dialog for typical engine troubles

 Previously, lizzie did not display any information if lizzie could not be started normally due to some flaw. With this fix, an error message will be displayed in a dialog box if the engine is improperly installed.

### Fix parsing GAMEINFOMAIN when GONGJE is missing

 This is a fix for GONGJE (komi) when loading a GIB format file, but the details are unknown and are currently under investigation.

### Avoid infinite loop in switchEngine

 Lizzie can freeze in switchEngine if the engine does not close its pipe after the GTP command "quit" for some reason.I'm afraid this may occur when users write their scripts for cloud engines.
 This bug has been fixed in v1.2.

### Fix #745 (NPE after initial config)
 
 Details are unknown.See [here](https://github.com/featurecat/lizzie/issues/745).

## Changes in v1.3

### ecord startup log for #756 even when printCommunication is not set #759

 The main reasons why lizzie does not start normally are that the engine command input is incorrect, the contents of the KataGo configuration file are incorrect, the weight file is incorrect, and so on.
 In such cases, lizzie will display in the Gtp console why it failed to start.

### Show dialog for #756 when engine ended unintentionally

 Displays an error message in a dialog box if the engine fails to start.

### Show "Engine is down." in trouble instead of "Engine is loading..." 

 If the engine fails to start, the status display at the bottom left was previously displayed as "Loading engine ...", but it has been changed to "Engin is down".

### Show GTP console when engine ended unintentionally

 With some of the above fixes, users can now easily identify the cause when lizzie fails to launch successfully.

 For example, if you start lizzie without placing it in the weight file lizzie folder, it will look like the screenshot below.

 ![error](https://user-images.githubusercontent.com/63999713/94359971-0832f480-00e5-11eb-9e54-c7f0b806e9fe.jpg)

### Import komi fix for Fox SGF from KaTrain (ref. #755)

 The FOX GO SGF file may contain incorrect komi values. Fixed to be converted to the correct komi value and read when loaded with lizzie

### Fix #752 (deadlock by Fox SGF)

 When loading a FOX GO SGF file, lizzie may freeze. A simple fix was made in v1.2, but a more ideal fix was made in v1.3.
 See [here](https://github.com/featurecat/lizzie/pull/757) for more information.

## Changes in v1.4

### Fix #765 (handicap bug in #758) #766

 Lizzie-v0.7.4 had a bug where the winning percentage and score lead were displayed at handicap stone when loading the SGF of the handicap game, but this bug has been fixed in this release.

### Improve subboard and add option not refresh variation when displayed

* mouse hover to stop flicker

  When the analysis is on, the sub-go board changes rapidly and the change charts change, making it difficult to see. It has been modified so that the change diagram is fixed when the mouse pointer is moved over the sub board.
  
* mouse wheel to change variation length
  
  By moving the mouse wheel up and down, you can slowly check the change diagram.

* left/right click to show nth variation

  Click the left and right mouse to display the nth change diagram.

* Addition of "No Refresh Displayed Variation" option

  On the main board, if you hover the mouse cursor over the candidate hand with analysis turned on, the various change charts will change rapidly and it will be difficult to see. You can fix the change chart by enabling this option.

### A try about new logo

 The icons on the taskbar are similar to Sabaki's and hard to distinguish, but the new logo looks like lizzie.

### Fix: "Engine is down." was not shown for panel UI

 This was applied in Lizzie-v0.7.4, but not in Lizzie-improved-v1.3, so I applied it in this release.

### bump version to 0.7.4 #720
### Correct inconsistent indents #763
### Update contributors #764

 These are not functionally explained in particular. If you are interested, please click [here](https://github.com/featurecat/lizzie/pulls?q=is%3Apr+is%3Aclosed)

## Changes in v1.4.1

### Fix missing movenum in subboard #770

 The stone on the sub board has a move number, but there was a bug in Lizzie-v 0.7.4 where this number disappears when you move the mouse cursor to the same position on the main board.
 This bug has been fixed in this release.

## Changes in v1.5

### Disable "Avoid Keep Variations" if it is 0

 Setting Settings> Engine> Avoid Keep Variations to "0" disables this feature and instead enables the "Undo" feature by right-clicking. (When the engine is Leela Zero)
 
### right-click to undo in panel UI

 In panel UI mode, right-clicking anywhere other than the main board did not respond (except for the sub board), but it has been fixed so that the "Undo" effect appears.

### click to redo in panel UI

 Switch to panel UI mode and line up some stones on the board. Next, put back the stones that were lined up. Left-click to place the stone in the same position as it was originally lined up. The stone will not be displayed by itself. Move the mouse cursor to see the stones. It's a very small detail, but it has been fixed so that the stone is displayed the moment you left-click.
 
### Fix wrong variation number on subboard

 Suppose you currently have 10 candidate moves on the main board. By clicking left and right on the sub board, the change diagram from 1 to 10 is displayed. And the number of the change diagram is displayed at the bottom right of the sub board. At this time, there was a bug that the wrong number "11" was displayed. This bug has been fixed in v1.5.

## Changes in v1.6

### Display existing .sgf file when savingfile

 Resolved an issue where existing files were not displayed when saving the file.

 <img src="https://user-images.githubusercontent.com/63999713/97395229-d1404080-1927-11eb-8dea-d4f67e6985fb.png" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/97395424-41e75d00-1928-11eb-9cef-cd5afec00c0b.png" width="45%">  

### Allows reading of uppercase .SGF and .GIB files

 Resolves an issue where uppercase .SGF and .GIB files could not be loaded.

### Display an arbitrary engine name instead of the weight file name

 As shown in the screenshot below, you can freely edit the pull-down menu display when selecting an engine by adding an arbitrary engine name to the beginning of the engine command.
 ![engine1](https://user-images.githubusercontent.com/63999713/97095142-d044b000-1696-11eb-9a92-cf92e1698539.png)
 ![engine2](https://user-images.githubusercontent.com/63999713/97095155-eeaaab80-1696-11eb-8c69-7566f0e5eece.png)
 
### Toggle large winrate graph by mouse click of center button 

 You can now zoom in / out the winning percentage graph by clicking the center of the mouse.

### Restore all checks in View > Panel at startup 

 The settings of various panel displays are stored in lizzie and will be reflected at the next startup.

### overflow of pondering message in Panel UI

 Solved the problem that the status display at the bottom left was slightly shifted downward when in panel UI mode.

### Fix wrong "Engine is loading..."  

 * Fix forever "Engine is loading..." if pondering is off
 
      Fixed an issue where when lizzie was started, if the analysis was stopped before the analysis was started, the status display at the bottom left would remain "Engine is loading" indefinitely.
  
 * Fix unshown "Engine is loading..." until mouse move 

      Solved the problem that "Engine is loading" was not displayed until the mouse was moved when switching the engine.

### Fix obsolete "Pondering on" by Analyze > Toggle analyze

 Solved the problem that the status display at the bottom left was not updated even when switching analysis on / off.

### variation tree was not updated by click to redo in panel UI

 Place some stones on the main board when in panel UI mode. Exclude the next stone and place it in the same place you first placed it. At this time, there was a problem that the change diagram on the upper right was not updated correctly. It has been fixed in v1.6.

### Display the analysis result when the file is loaded

 In the official release version of Lizzie-v 0.7.4, there is a bug that the analysis result is not displayed even if the sgf file containing the analysis result is loaded, but in the Lizzie-improved series, this bug is not present.

## Changes in v1.7

### Problems with the variation tree

 * In Panel UI mode
   * The blunder color of the current node is not visible when analysis is turned on. If analysis is turned off, you can see it.
   * When a node is moved, the blunder color of the current node is not visible. When analysis is on, it becomes visible by turning analysis off, and when analysis is off, it becomes visible by turning analysis on and off.
 * In normal mode
   * When a node is moved, the blunder color of the current node is not visible when analysis is off. It is still visible when analysis is turned on and then turned off again, but it disappears again when you move to another node and come back.
 * There is no black dot in the "□" of the root node (with no stones in the board).

 All of these things have been improved in v1.7.

### Issues related to "Settings→Theme→Winning Rate Change Node"

 * If you enter blunder color, lizzie will not remember it unless you click on another cell.
 * When I try to delete them all, the last line remains. When I click on another cell, it disappears.
 * Threshold values are not reflected in the variation tree unless they are sorted in order of decreasing value, but because the system is not equipped with a sorting function (to sort data according to a certain criterion), it will not work well if the data are entered in pieces.
 * Even if you enter a single threshold or blunder color, it will not be reflected until you restart lizzie.
 * If the threshold is entered by mistake in full-width characters, the analysis on/off will not work, but users are likely to be confused because there is no function to inform them of the error. The fixed version informs the user that an invalid string has been entered by displaying "-777.0" the next time the user checks.
 * You have to restart lizzie to get the new settings for the win rate change nodes.
 
 All of these things have been improved in v1.7.

### Winning rate change node for trial

 To make it easier to recognize the function of the win rate change node, the sample data for a one-time function is pre-set.
 
### There is something wrong with the window that appears in Settings→Theme.

 With the existing lizzie, some parts of it are not displayed correctly in the existing lizzie, so you can move to another tab and come back to it.In v1.7, it is correct from the start.

### Overwrite storage issues

 For example, if a file called "ff.sgf" already exists and you try to save the file by typing "ff", the existing lizzie will be overwritten without a confirmation message, but in v1.7, a confirmation message is shown.

## Changes in v1.8

### Leela 0.11.0 on Lizzie 0.7.4

 Leela 0.11.0 is now available in lizzie.
 Download "Leela 0.11.0 engine only" from https://www.sjeng.org/leela.html and place "Leela0110GTP.exe" or "Leela0110GTP_OpenCL.exe" in the lizzie folder.
 Specify "Leela0110GTP.exe -g" or "Leela0110GTP_OpenCL.exe -g" in the engine command.

### Accept only numbers as blunder thresholds

 When you enter a threshold for a win rate change node, if you enter a string other than an appropriate string, the cell will be surrounded by a red frame and you will not be able to enter blunder color. This allows the user to readily recognize that the wrong string has been entered.

### Make the threshold 0.0 usable for the blunder color of "normal" moves

 For blunder color, it is now possible to specify the normal movement as well.Until now, the best moves and movements close to them were white and inconspicuous, but with the addition of this function, it is now possible to display good movements in cool colors such as light blue.

### Fix(slow play/undo/redo)

 On a CPU-only PC, under the conditions of Panel UI + Toolbar + KataGo (OpenCL), the undo speed may be quite slow (about 0.5 seconds per move).This issue has been resolved.


### Fix #805(The ">>" doesn't work properly)

 ">>" on the lower toolbar is a function to advance 10 moves, but there was a bug that only one move was actually advanced, so I fixed it.

### Fix overflow of variation tree with largeSubBoard in normal UI

 There was a bug that the variation tree protruded to the main board when the winning percentage graph or the sub board was enlarged and displayed when there were many branches in the variation tree. It has been fixed in v1.8.

### Win rate graph related
 
 * Fixed an issue where move numbers were hard to see due to the green winning percentage line.
 * By displaying something like "white +0.5" above the bar graph, the current score lead information is easier to see.
 * Place some stones on the main board with pondering off. Next, turn on pondering and return the stones one by one. At this time, the stdev and score lead information is hidden. Fixed this issue. 

### Fix: Remove wrong-sized ownership marks 

 Display the ownership mark with "katago posture" on the toolbar. Then turn off podering and resize the window. Then the ownership mark is not optimized for the window size. Hide this false display. It will be displayed again as soon as you turn on pondering.

### Fix: Up arrow key does not work just after click on a suggested move …

 Place the stone in the place of the candidate hand displayed on the board. Restoring the stone with the up arrow key or the mouse wheel (up) without moving the mouse pointer. The stone you put on it should disappear, but it doesn't actually disappear. This issue has been fixed in v1.8.

## Changes in v1.9

### Fix(playouts "1.5k" is wrongly read as 15000 in SGF) 

 When adding and saving the analysis data to the SGF in which the analysis data by lizzie is recorded, it sometimes took an unusually long time for the numerical values on each candidate to move.
 In addition, there was a bug that the amount of analysis displayed in the comment column at the bottom right was incorrectly recorded as about 10 times the value on the board. It has been fixed in v1.9.

### Show background playouts

 Previously, when the phase was moved, the display of the total analysis amount on the upper toolbar was the value of the previous phase, but in v1.9 it has been improved to display the total analysis amount stored for each phase. It has been.

### Added engine full command as tooltip for easier engine selection
 
 When you move the mouse cursor to the engine selection pull-down menu, the engine command string pops up for a few seconds.

### Force UTF-8 for saving SGF

 If you load an SGF that uses a non-ASCII code (other than half-width alphanumeric characters, Japanese, etc.) as the player name and then save it, there was a bug that the player name at the bottom of the board would be written strangely.In v1.9 this issue is resolved by forcing UTF-8 when saving the SGF.

## Changes in v2.0

### Update DisplayStrings_ko.properties

 The Korean notation has been improved to make it easier to use. (I can't explain because I don't understand Korean)
 See [here](https://github.com/hope366/Lizzie-improvements/pull/4) for more information.

### Fix wrong getCoord which leads analysis hangs when enable katago ownership in rectangle board

 Analysis hung bug when turning on KataGo's estimated area display on a rectangular board.This bug doesn't seem to occur in Lizzie-improved-v1.9, but it seems to occur in the official version of Lizzie-0.7.4.

### only update last-folder if there is something to update  

 This issue has not been reproduced and cannot be explained in detail. Since a bug in Ubuntu has been reported, it may be a bug limited to Ubuntu.
 
## Changes in v2.1

### Set region of interest like KaTrain 1.7

 * We have also incorporated the new features introduced in KaTrain 1.7 into lizzie. You can specify a rectangular area to limit the analysis within that area.
   * Alt+drag to set region of interest.
   * Alt+click to reset it.

## Changes in v2.2

### Strengthening the engine menu

 Leela 0.11.0 and colab-katago were blank in the engine menu, but now they are displayed by entering a nickname.

### Region of interest

 * In v2.1, all the change diagrams presented were also limited to the specified area, but in v2.2 the entire board is used.
 * In v2.1 it was limited to normal mode, but in v2.2 it can also be used in panel UI mode.
 * In v2.1, if you release Alt before the mouse button, the area specification will fail, but in v2.2 it will be valid.
 * You can now cancel the set analysis area by clicking "Allow" or "Avoid" in the right-click menu. (Only when the engine is Leela Zero and Settings-> Engine-> Avoid Keep Variations is other than 0)

### Revive score mode

 We have revived the score mode, which has been abolished since the score estimation function using zen was applied.
 Click "Game" on the top toolbar and "Score game" is added at the bottom.
 In Score mode, by left-clicking on the dead stone, the numerical value of each other's fixed place considering Komi will be displayed in the Agehama display.

### Add Help menu

 "Help" has been added to the far right of the top toolbar. Help → Keyboard controls is a link to a page explaining lizzie shortcut keys.

### Switch rules from the menu 

 "Rule" has been added to the "Analysis" menu on the toolbar, and you can now freely choose from 11 types of rules.
 This feature is only available if the engine is KataGo.
 In panel UI mode, the selected rule is displayed above the Komi display.

### Fix typo

 In English mode, there was a typo in the contents of the dialog box displayed by selecting "File"-> "Open from online".
 Before modification: Please input a available url.
 After modification: Please input an available url.

### Show message when autoanalysis is denied

 If you run the automatic analysis at the end of the game (without the next move), lizzie will be unresponsive.
 Therefore, "No next move" is displayed in the dialog box.

## Changes in v2.3

### append player rank to player name

 If you load an SGF that has "BR" or "WR" properties, the rank of each player will be displayed at the bottom of the board.

### Apply Japanese rules by default

 Since the rule selection function was applied in v2.2, even if the rule is set to "japanese" in the configuration file, it remains "tromp-taylor" in lizzie. You can change it to "japanese" in lizzie, but to avoid confusion, I changed it so that "japanese" is applied by default when lizzie is started. Also, in the list of rule changes, "japanese" is placed at the top.

### Variation windows movenum

 The move number is displayed in the variation tree.

### Fix D key (toggle "show KataGo score mean")(Limited to Katago)

 By pressing the "D" key, you can now switch the display contents of the candidate move.
 "Normal display"-> "Scorelead + number of searches"-> "Win rate + number of searches"

### Continue analysis off after autoplay

 If you press the R key while hovering the mouse cursor over the candidate hand, the change diagram will be played automatically, but until now, even if you performed with analysis off, the analysis will automatically turn on as soon as the autoplay ends. It was a specification to switch.
 This is inconvenient if you want to observe the change diagram slowly, so if you perform automatic playback with analysis off, change it so that analysis remains off after the end.

### Partial change of key operation explanation

 "Ctrl undo/redo 10 moves"-> "Ctrl-PageUp/Down undo/redo 10 moves"
 "Z toggle suggestions etc."-> "Shift-z toggle suggestions etc."
 "r replay branch"-> "r automatic replay of vairiation diagram"

### About the opacity slide function of the candidate move

 You can adjust the opacity of the candidate move with Ctrl + Shift + PageUp / Down, but the amount of change at one time has been slightly increased.



 





 

 

 
  





