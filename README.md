<!-- TOC -->autoauto- [1. Lizzie - Leela Zero Interface](#1-lizzie---leela-zero-interface)auto    - [1.1. Running a release](#11-running-a-release)auto        - [1.2.1. Building Leela Zero](#121-building-leela-zero)auto        - [1.2.2. Building Lizzie](#122-building-lizzie)auto        - [1.2.3. Running Lizzie](#123-running-lizzie)auto    - [1.3. Changes in the initial release (v1.0)](#13-changes-in-the-initial-release-v10)auto        - [1.3.1. Fix #727 (winrate graph for LCB)](#131-fix-727-winrate-graph-for-lcb)auto        - [1.3.2. About Lcb](#132-about-lcb)auto        - [1.3.3. Fix #701 (wrong winrate in WinratePane)](#133-fix-701-wrong-winrate-in-winratepane)auto        - [1.3.4. Remove redundant score display to fix #683](#134-remove-redundant-score-display-to-fix-683)auto        - [1.3.5. Add play sound](#135-add-play-sound)auto        - [1.3.6. Show GTP console during initial tuning of KataGo](#136-show-gtp-console-during-initial-tuning-of-katago)auto        - [1.3.7. Update obsolete "Leela Zero" in DisplayStrings_ja_JP](#137-update-obsolete-leela-zero-in-displaystrings_ja_jp)auto        - [1.3.8. About background image](#138-about-background-image)auto        - [1.3.9. About komi 6.5 points](#139-about-komi-65-points)autoauto<!-- /TOC -->
# 1. Lizzie - Leela Zero Interface
![screenshot0 7](https://user-images.githubusercontent.com/63999713/86693777-f0982280-c045-11ea-9b59-1e7b5292851a.jpg)

Lizzie is a graphical interface allowing the user to analyze games in
real time using [Leela Zero](https://github.com/gcp/leela-zero). You
need Java 8 or higher to run this program.

See the [Wiki](https://github.com/featurecat/lizzie/wiki) for learning more.

[![Build Status](https://travis-ci.org/featurecat/lizzie.svg?branch=master)](https://travis-ci.org/featurecat/lizzie?branch=master)


## 1.1. Running a release

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

* When studying with katago in lizzie, there was a problem in drawing the graph when the winning rate display method was Lcb.If the score difference becomes extremely large, the graph will not be drawn correctly and the vertical movement will be repeated violently.This has been improved in v1.0.

![lcb](https://user-images.githubusercontent.com/63999713/86690198-acefe980-c042-11ea-93d2-1158e97a53ca.jpg)

### 1.3.2. About Lcb

With LeelaZero, for example, Q3 is searched 10 times and the average win rate is 43.16%.
LCB at this time is 40.86%.

Q3 -> 10 (V: 43.16%) (LCB: 40.86%)

In 10 searches, the winning rate of 43.16% shifts 2.3% (43.16-40.86) up and down,
In other words, the true win rate is in the range below.

40.86% <= 43.16% <= 45.46%

This smaller one is the LCB, and as the number of searches increases, the deviation becomes smaller and the LCB approaches 43.16%.Generally, MCTS starts the one with the largest number of searches in Root, but Leela Zero uses the one with the largest LCB.I'm supposed to choose. This was about +70 Elo stronger.

### 1.3.3. Fix #701 (wrong winrate in WinratePane)

* This screenshot is the second station of the 5th match of Alpha Go and Isedle 9th dan.The screenshot above is a real-time analysis, and the screenshot below is a sgf file saved in panel UI mode and loaded.The screenshot above showing the white win rate of 55% is correct and the screenshot below shows the previous number.This bug has been fixed.

![up](https://user-images.githubusercontent.com/63999713/86817497-14984a00-c0c0-11ea-8c6a-f283c2d97441.jpg)

![down](https://user-images.githubusercontent.com/63999713/86817567-27ab1a00-c0c0-11ea-937b-ed77bf5e8e0f.jpg)

### 1.3.4. Remove redundant score display to fix #683

* Although the numerical value showing the disparity information is displayed in the upper center of the winning percentage bar, there was a bug that the numerical value here was always 0 when the pre-analyzed sgf file was read and moved with pondering off.In v1.0 this confusing display has been removed.

### 1.3.5. Add play sound

* Put the jar file and the sound folder in the lizzie folder.When you start lizzie, an item called Settings → Play Sound has been added, so you can switch on/off the start sound here.You can also switch by ""play-sound": true," in config.txt.

### 1.3.6. Show GTP console during initial tuning of KataGo

*  Tuning is performed only the first time when the OpenCL version of katago is started with lizzie, so it may take a considerable time depending on the performance of the computer.So some people may give up thinking it is a bug or freeze.With this fix, the GTP console is displayed only at the first startup, and you can see that the tuning work is being performed internally.To verify, delete the KataGoData folder in the lizzie or katago folder and then launch the OpenCL version of katago with lizzie.

### 1.3.7. Update obsolete "Leela Zero" in DisplayStrings_ja_JP

* In the official release version, "Leela Zero is loading" will continue to be displayed in the lower left until the analysis starts, regardless of the engine type.The modified version will display "Loading engine".

![load](https://user-images.githubusercontent.com/63999713/86813282-e6643b80-c0ba-11ea-826b-d28c94b7dd8b.jpg)

![engine](https://user-images.githubusercontent.com/63999713/86813353-0693fa80-c0bb-11ea-92ff-4f2a7e480c7e.jpg)

### 1.3.8. About background image

* In v1.0, the starry sky background is applied by default, but the user can apply any image.There is a folder called theme in the lizzie folder.Create a folder with an arbitrary name in this.Suppose you create a folder called "aaa".Place the image file you want to use as the background in this folder and name the file "background.png".For jpg format image files, you can convert them to png format or just change the name and extension.Next, open config.txt and change it to "theme": "default", → "theme": "aaa",. This will change the background.Start lizzie and select "Settings" -> "Themes" -> "aaa" from the pull-down menu of the top theme. You can also change the background image with this method.
* We also recommend 1920x1080 as the size of the image file used. If the size is small, it looks like a split mode and it looks bad.

### 1.3.9. About komi 6.5 points

* In the official release version, komi is set to 7.5 points, but it has been changed to apply 6.5 points at startup.This is convenient when using katago to consider Japanese rules and Korean rules. leelazero has no effect because it does not support variable komi.


