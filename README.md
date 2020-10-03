# 1. Lizzie-improvements

<!-- TOC -->

- [1. Lizzie-improvements](#1-lizzie-improvements)
    - [1.1. Lizzie - Leela Zero Interface](#11-lizzie---leela-zero-interface)
    - [1.2. Running a release](#12-running-a-release)
        - [1.2.1. Building Leela Zero](#121-building-leela-zero)
        - [1.2.2. Building Lizzie](#122-building-lizzie)
        - [1.2.3. Running Lizzie](#123-running-lizzie)
    - [1.3. Changes in the initial release (v1.0)](#13-changes-in-the-initial-release-v10)
        - [1.3.1. Fix #727 (winrate graph for LCB)](#131-fix-727-winrate-graph-for-lcb)
            - [1.3.1.1. About Lcb](#1311-about-lcb)
        - [1.3.2. Fix #701 (wrong winrate in WinratePane)](#132-fix-701-wrong-winrate-in-winratepane)
        - [1.3.3. Remove redundant score display to fix #683](#133-remove-redundant-score-display-to-fix-683)
        - [1.3.4. Add play sound](#134-add-play-sound)
        - [1.3.5. Show GTP console during initial tuning of KataGo](#135-show-gtp-console-during-initial-tuning-of-katago)
        - [1.3.6. Update obsolete "Leela Zero" in DisplayStrings_ja_JP](#136-update-obsolete-leela-zero-in-displaystrings_ja_jp)
        - [1.3.7. About background image](#137-about-background-image)
        - [1.3.8. About komi 6.5 points](#138-about-komi-65-points)
    - [1.4. Changes in v1.1](#14-changes-in-v11)
        - [1.4.1. Fixed initial placement for handicap games](#141-fixed-initial-placement-for-handicap-games)
        - [1.4.2. Fix obsolete "Leela Zero" for the default player name](#142-fix-obsolete-leela-zero-for-the-default-player-name)
        - [1.4.3. Fixed a bug where the win rate graph would cross the board](#143-fixed-a-bug-where-the-win-rate-graph-would-cross-the-board)
        - [1.4.4. Fix saveBackRouting skipping nodes](#144-fix-savebackrouting-skipping-nodes)
        - [1.4.5. Fix: "Pondering on/off" was not updated by Analyze button](#145-fix-pondering-onoff-was-not-updated-by-analyze-button)
        - [1.4.6. Fix (scoreMean & scoreStdev)](#146-fix-scoremean--scorestdev)
        - [1.4.7. Option to opaquely paint grayscale territory prediction on board](#147-option-to-opaquely-paint-grayscale-territory-prediction-on-board)
    - [1.5. Changes in v1.2](#15-changes-in-v12)
        - [1.5.1. Fixed a bug that lizzie freezes when loading certain FOX GO SGF files](#151-fixed-a-bug-that-lizzie-freezes-when-loading-certain-fox-go-sgf-files)
        - [1.5.2. Show error dialog for typical engine troubles](#152-show-error-dialog-for-typical-engine-troubles)
        - [1.5.3. Fix parsing GAMEINFOMAIN when GONGJE is missing](#153-fix-parsing-gameinfomain-when-gongje-is-missing)
        - [1.5.4. Avoid infinite loop in switchEngine](#154-avoid-infinite-loop-in-switchengine)
        - [1.5.5. Fix #745 (NPE after initial config)](#155-fix-745-npe-after-initial-config)
    - [1.6. Changes in v1.3](#16-changes-in-v13)
        - [1.6.1 Record startup log for #756 even when printCommunication is not set #759](#161-record-startup-log-for-756-even-when-printcommunication-is-not-set-759)
        - [1.6.2 Show dialog for #756 when engine ended unintentionally](#162-show-dialog-for-756-when-engine-ended-unintentionally)
        - [1.6.3 Show "Engine is down." in trouble instead of "Engine is loading..."](#163-show-engine-is-down-in-trouble-instead-of-engine-is-loading)
        - [1.6.4 Show GTP console when engine ended unintentionally](#164-show-gtp-console-when-engine-ended-unintentionally)
        - [1.6.5 Import komi fix for Fox SGF from KaTrain (ref. #755)](#165-import-komi-fix-for-fox-sgf-from-katrain-ref-755)
        - [1.6.6 Fix #752 (deadlock by Fox SGF)](#166-fix-752-deadlock-by-fox-sgf)
    - [Changes in v1.4](#changes-in-v14)
        - [Fix #765 (handicap bug in #758) #766](#fix-765-handicap-bug-in-758-766)
        - [Improve subboard and add option not refresh variation when displayed](#improve-subboard-and-add-option-not-refresh-variation-when-displayed)
        - [A try about new logo](#a-try-about-new-logo)
        - [Fix: "Engine is down." was not shown for panel UI](#fix-engine-is-down-was-not-shown-for-panel-ui)
        - [bump version to 0.7.4 #720](#bump-version-to-074-720)
        - [Correct inconsistent indents #763](#correct-inconsistent-indents-763)
        - [Update contributors #764](#update-contributors-764)

<!-- /TOC -->

日本語での説明は、こちらのリンク先をご覧ください→
https://ameblo.jp/hope366/entry-12629155281.html

## 1.1. Lizzie - Leela Zero Interface
![GIF 2020-07-13 12-46-35](https://user-images.githubusercontent.com/63999713/87269204-6d744200-c507-11ea-80aa-263f24205251.gif)
Lizzie is a graphical interface allowing the user to analyze games in
real time using [Leela Zero](https://github.com/gcp/leela-zero). You
need Java 8 or higher to run this program.

See the [Wiki](https://github.com/featurecat/lizzie/wiki) for learning more.

[![Build Status](https://travis-ci.org/featurecat/lizzie.svg?branch=master)](https://travis-ci.org/featurecat/lizzie?branch=master)


## 1.2. Running a release

Just follow the instructions in the provided readme in the
[release](https://github.com/featurecat/lizzie/releases/tag/0.7.2).

The first run may take a while because Leela Zero needs to set up the
OpenCL tunings. Just hang tight, and wait for it to finish, then you
will see Leela Zero's analysis displayed on the board. Feel free to supply
your own tunings, as this will speed up the process. Do this by copying
any `leelaz_opencl_tuning` file you have into the directory.

### 1.2.1. Building Leela Zero

First, you will need to have a version of Leela Zero that
continually outputs pondering information. You can get this from one
of the Lizzie releases or build it yourself; just compile from the **next**
branch of Leela Zero (see http://github.com/gcp/leela-zero/tree/next for more
details).

    $ git clone --recursive --branch next http://github.com/gcp/leela-zero.git

### 1.2.2. Building Lizzie

The simplest way to build Lizzie is to use [Maven](https://maven.apache.org/).

To build the code and package it:

    $ mvn package

### 1.2.3. Running Lizzie

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

## 1.3. Changes in the initial release (v1.0)

### 1.3.1. Fix #727 (winrate graph for LCB)

 When studying with katago in lizzie, there was a problem in drawing the graph when the winning rate display method was Lcb.If the score difference becomes extremely large, the graph will not be drawn correctly and the vertical movement will be repeated violently.This has been improved in v1.0.
 This screenshot shows a 5 stone handicap game setup. White 2, 4, 6, 8 are passes.

<img src="https://user-images.githubusercontent.com/63999713/87446286-13bd6600-c634-11ea-88e7-39baf95f3f55.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87453050-eb863500-c63c-11ea-9bf9-69409e921ed3.jpg" width="45%">



#### 1.3.1.1. About Lcb

 With LeelaZero, for example, Q3 is searched 10 times and the average win rate is 43.16%.
 LCB at this time is 40.86%.

 Q3 -> 10 (V: 43.16%) (LCB: 40.86%)

 In 10 searches, the winning rate of 43.16% shifts 2.3% (43.16-40.86) up and down,
 In other words, the true win rate is in the range below.

 40.86% <= 43.16% <= 45.46%

 This smaller one is the LCB, and as the number of searches increases, the deviation becomes smaller and the LCB approaches 43.16%.Generally, MCTS starts the one with the largest number of searches in Root, but Leela Zero uses the one with the largest LCB.I'm supposed to choose. This was about +70 Elo stronger.

### 1.3.2. Fix #701 (wrong winrate in WinratePane)

 This screenshot is the second station of the 5th match of Alpha Go and Isedle 9th dan.The screenshot above is a real-time analysis, and the screenshot below is a sgf file saved in panel UI mode and loaded.The screenshot above showing the white win rate of 34.3% is correct and the screenshot below shows the previous number.This bug has been fixed.

<img src="https://user-images.githubusercontent.com/63999713/87452256-f5f3ff00-c63b-11ea-89be-9d7391379bf5.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87452332-115f0a00-c63c-11ea-9663-ca889d3a0095.jpg" width="45%">


### 1.3.3. Remove redundant score display to fix #683

 Although the numerical value showing the disparity information is displayed in the upper center of the winning percentage bar, there was a bug that the numerical value here was always 0 when the pre-analyzed sgf file was read and moved with pondering off.In v1.0 this confusing display has been removed.

### 1.3.4. Add play sound

 Put the jar file and the sound folder in the lizzie folder.When you start lizzie, an item called Settings → Play Sound has been added, so you can switch on/off the start sound here.You can also switch by ""play-sound": true," in config.txt.

### 1.3.5. Show GTP console during initial tuning of KataGo

 Tuning is performed only the first time when the OpenCL version of katago is started with lizzie, so it may take a considerable time depending on the performance of the computer.So some people may give up thinking it is a bug or freeze.With this fix, the GTP console is displayed only at the first startup, and you can see that the tuning work is being performed internally.To verify, delete the KataGoData folder in the lizzie or katago folder and then launch the OpenCL version of katago with lizzie.

### 1.3.6. Update obsolete "Leela Zero" in DisplayStrings_ja_JP

 In the official release version, "Leela Zero is loading" will continue to be displayed in the lower left until the analysis starts, regardless of the engine type.The modified version will display "Loading engine".

<img src="https://user-images.githubusercontent.com/63999713/87438168-2894fc00-c62a-11ea-8f0d-0de55759c7eb.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87439880-42374300-c62c-11ea-8da6-e2e0424b2dd1.jpg" width="45%">



### 1.3.7. About background image

 In v1.0, the starry sky background is applied by default, but the user can apply any image.For the background image, put your favorite image in the yasnaya folder in the thema folder of the Lizzie folder, set the upper menu to yasnaya in the theme tab from the settings of the upper menu, and you can make it your favorite image with the path of the background image below it. I will. (It will be reflected when Lizzie is restarted after the change)
 We also recommend 1920x1080 as the size of the image file used. If the file size is small, it may not be displayed properly.

### 1.3.8. About komi 6.5 points

 In the official release version, komi is set to 7.5 points, but it has been changed to apply 6.5 points at startup.This is convenient when using katago to consider Japanese rules and Korean rules. leelazero has no effect because it does not support variable komi.

## 1.4. Changes in v1.1

### 1.4.1. Fixed initial placement for handicap games

 In KataGo's handicap game, the initial placement was randomly determined, but it has been changed to the official placement.

 <img src="https://user-images.githubusercontent.com/63999713/87868402-1fac7d80-c9d0-11ea-8d12-6b4f9f78aae0.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87868427-584c5700-c9d0-11ea-822f-fc9c6c1790a2.jpg" width="45%">

### 1.4.2. Fix obsolete "Leela Zero" for the default player name

 When playing a new game with KataGo, "Leela Zero" was displayed in the game info dialog box and the player name at the bottom of the board, but it has been changed to "AI".

  <img src="https://user-images.githubusercontent.com/63999713/87859317-49818800-c96f-11ea-9fcd-c48f721e76d1.jpg" width="45%"> <img src="https://user-images.githubusercontent.com/63999713/87859331-6453fc80-c96f-11ea-88b0-53d9aa8d0378.jpg" width="45%">

### 1.4.3. Fixed a bug where the win rate graph would cross the board


 When loading a pre-analyzed sgf file and moving it from the beginning with pondering off, if the automatic width adjustment of the winning percentage graph is enabled, the graph appears to cross the main board greatly.This bug has been fixed in v1.1.

  ![graph](https://user-images.githubusercontent.com/63999713/87859391-cd3b7480-c96f-11ea-92a9-4fcc5df0f0c6.jpg)

### 1.4.4. Fix saveBackRouting skipping nodes

 See the screenshot below. In the above screenshot, switch the engine from Katago to leelazero. It should be in the same phase, but the result will show the point of another previous branch, as in the screenshot below.Thus, if you have several branches, switching engines may show aspects of another previous branch. This bug has been fixed in v1.1.

![GIF 2020-07-13 14-43-42](https://user-images.githubusercontent.com/63999713/87859408-ec3a0680-c96f-11ea-914e-f4a0b105b5fd.gif)

### 1.4.5. Fix: "Pondering on/off" was not updated by Analyze button

 When Pondering on is displayed, click the "Analysis" button on the toolbar to stop the search on the board. However, it does not update to "Pondering off" until you move the mouse cursor over the main board. In the modified version, "Pondering off" is displayed immediately after clicking the "Analysis" button.

 ![GIF 2020-07-19 3-40-03](https://user-images.githubusercontent.com/63999713/87859677-e8a77f00-c971-11ea-8a14-f4854c109022.gif)

### 1.4.6. Fix (scoreMean & scoreStdev)

 There are three items above the winning percentage graph: "mean", "stdev", and "Last move". In real-time analysis, all three work normally, but when moved with the pondering off, "mean" and "stdev" are fixed at the final numerical values ​​and do not work properly.In v1.1, these two non-functioning items were hidden when moving with pondering off.

### 1.4.7. Option to opaquely paint grayscale territory prediction on board

 About the lower menu "Kata Estimate", added the option to display with opaque white to black paint.To switch, go to View → KataGo Settings → Trend Information → Brend with board. The shortcut key is "Shift-Period". The changes will be reflected when you turn on Pondering on.

 <img src="https://user-images.githubusercontent.com/63999713/87859685-fe1ca900-c971-11ea-84e9-413694fde269.jpg" width=45%> <img src="https://user-images.githubusercontent.com/63999713/87859692-112f7900-c972-11ea-9bbc-9a1e682184d9.jpg" width=45%>

## 1.5. Changes in v1.2

### 1.5.1. Fixed a bug that lizzie freezes when loading certain FOX GO SGF files

 Some FOX GO game records contain many explanations and branches. This is often seen in official competitions between professionals.
 If you save this and load it with lizzie, lizzie may freeze. This bug has been fixed in v1.2.

### 1.5.2. Show error dialog for typical engine troubles

 Previously, lizzie did not display any information if lizzie could not be started normally due to some flaw. With this fix, an error message will be displayed in a dialog box if the engine is improperly installed.

### 1.5.3. Fix parsing GAMEINFOMAIN when GONGJE is missing

 This is a fix for GONGJE (komi) when loading a GIB format file, but the details are unknown and are currently under investigation.

### 1.5.4. Avoid infinite loop in switchEngine

 Lizzie can freeze in switchEngine if the engine does not close its pipe after the GTP command "quit" for some reason.I'm afraid this may occur when users write their scripts for cloud engines.
 This bug has been fixed in v1.2.

### 1.5.5. Fix #745 (NPE after initial config)
 
 Details are unknown.See [here](https://github.com/featurecat/lizzie/issues/745).

## 1.6. Changes in v1.3

### 1.6.1 Record startup log for #756 even when printCommunication is not set #759

 The main reasons why lizzie does not start normally are that the engine command input is incorrect, the contents of the KataGo configuration file are incorrect, the weight file is incorrect, and so on.
 In such cases, lizzie will display in the Gtp console why it failed to start.

### 1.6.2 Show dialog for #756 when engine ended unintentionally

 Displays an error message in a dialog box if the engine fails to start.

### 1.6.3 Show "Engine is down." in trouble instead of "Engine is loading..." 

 If the engine fails to start, the status display at the bottom left was previously displayed as "Loading engine ...", but it has been changed to "Engin is down".

### 1.6.4 Show GTP console when engine ended unintentionally

 With some of the above fixes, users can now easily identify the cause when lizzie fails to launch successfully.

 For example, if you start lizzie without placing it in the weight file lizzie folder, it will look like the screenshot below.

 ![error](https://user-images.githubusercontent.com/63999713/94359971-0832f480-00e5-11eb-9e54-c7f0b806e9fe.jpg)

### 1.6.5 Import komi fix for Fox SGF from KaTrain (ref. #755)

 The FOX GO SGF file may contain incorrect komi values. Fixed to be converted to the correct komi value and read when loaded with lizzie

### 1.6.6 Fix #752 (deadlock by Fox SGF)

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





