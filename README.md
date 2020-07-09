# Lizzie-improvements
<!-- TOC -->

- [Lizzie-improvements](#lizzie-improvements)
    - [Lizzie - Leela Zero Interface](#lizzie---leela-zero-interface)
    - [Running a release](#running-a-release)
        - [Building Leela Zero](#building-leela-zero)
        - [Building Lizzie](#building-lizzie)
        - [Running Lizzie](#running-lizzie)
    - [Changes in the initial release (v1.0)](#changes-in-the-initial-release-v10)
        - [Fix #701 (wrong winrate in WinratePane)](#fix-701-wrong-winrate-in-winratepane)
        - [Remove redundant score display to fix #683](#remove-redundant-score-display-to-fix-683)
        - [Add play sound](#add-play-sound)
        - [Show GTP console during initial tuning of KataGo](#show-gtp-console-during-initial-tuning-of-katago)
        - [Update obsolete "Leela Zero" in DisplayStrings_ja_JP](#update-obsolete-leela-zero-in-displaystrings_ja_jp)
        - [About background image](#about-background-image)
        - [About komi 6.5 points](#about-komi-65-points)

<!-- /TOC -->
The explanation in Japanese is at the following link.
https://ameblo.jp/hope366

## Lizzie - Leela Zero Interface
![screenshot0 7](https://user-images.githubusercontent.com/63999713/86693777-f0982280-c045-11ea-9b59-1e7b5292851a.jpg)
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

* ### Fix #727 (winrate graph for LCB)

  * When studying with katago in lizzie, there was a problem in drawing the graph when the winning rate display method was Lcb.If the score difference becomes extremely large, the graph will not be drawn correctly and the vertical movement will be repeated violently.This has been improved in v1.0.

![lcb](https://user-images.githubusercontent.com/63999713/86690198-acefe980-c042-11ea-93d2-1158e97a53ca.jpg)

  * #### About Lcb

With LeelaZero, for example, Q3 is searched 10 times and the average win rate is 43.16%.
LCB at this time is 40.86%.

Q3 -> 10 (V: 43.16%) (LCB: 40.86%)

In 10 searches, the winning rate of 43.16% shifts 2.3% (43.16-40.86) up and down,
In other words, the true win rate is in the range below.

40.86% <= 43.16% <= 45.46%

This smaller one is the LCB, and as the number of searches increases, the deviation becomes smaller and the LCB approaches 43.16%.Generally, MCTS starts the one with the largest number of searches in Root, but Leela Zero uses the one with the largest LCB.I'm supposed to choose. This was about +70 Elo stronger.

### Fix #701 (wrong winrate in WinratePane)

* This screenshot is the second station of the 5th match of Alpha Go and Isedle 9th dan.The screenshot above is a real-time analysis, and the screenshot below is a sgf file saved in panel UI mode and loaded.The screenshot above showing the white win rate of 55% is correct and the screenshot below shows the previous number.This bug has been fixed.

![up](https://user-images.githubusercontent.com/63999713/86817497-14984a00-c0c0-11ea-8c6a-f283c2d97441.jpg)

![down](https://user-images.githubusercontent.com/63999713/86817567-27ab1a00-c0c0-11ea-937b-ed77bf5e8e0f.jpg)

### Remove redundant score display to fix #683

* Although the numerical value showing the disparity information is displayed in the upper center of the winning percentage bar, there was a bug that the numerical value here was always 0 when the pre-analyzed sgf file was read and moved with pondering off.In v1.0 this confusing display has been removed.

### Add play sound

* Put the jar file and the sound folder in the lizzie folder.When you start lizzie, an item called Settings → Play Sound has been added, so you can switch on/off the start sound here.You can also switch by ""play-sound": true," in config.txt.

### Show GTP console during initial tuning of KataGo

*  Tuning is performed only the first time when the OpenCL version of katago is started with lizzie, so it may take a considerable time depending on the performance of the computer.So some people may give up thinking it is a bug or freeze.With this fix, the GTP console is displayed only at the first startup, and you can see that the tuning work is being performed internally.To verify, delete the KataGoData folder in the lizzie or katago folder and then launch the OpenCL version of katago with lizzie.

### Update obsolete "Leela Zero" in DisplayStrings_ja_JP

* In the official release version, "Leela Zero is loading" will continue to be displayed in the lower left until the analysis starts, regardless of the engine type.The modified version will display "Loading engine".

![load](https://user-images.githubusercontent.com/63999713/86813282-e6643b80-c0ba-11ea-826b-d28c94b7dd8b.jpg)

![engine](https://user-images.githubusercontent.com/63999713/86813353-0693fa80-c0bb-11ea-92ff-4f2a7e480c7e.jpg)

### About background image

* In v1.0, the starry sky background is applied by default, but the user can apply any image.For the background image, put your favorite image in the yasnaya folder in the thema folder of the Lizzie folder, set the upper menu to yasnaya in the theme tab from the settings of the upper menu, and you can make it your favorite image with the path of the background image below it. I will. (It will be reflected when Lizzie is restarted after the change)
* We also recommend 1920x1080 as the size of the image file used. If the file size is small, it may not be displayed properly.

### About komi 6.5 points

* In the official release version, komi is set to 7.5 points, but it has been changed to apply 6.5 points at startup.This is convenient when using katago to consider Japanese rules and Korean rules. leelazero has no effect because it does not support variable komi.


