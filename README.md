# Contents

This project includes a file to generate ballroom and latin finals.

## Background

Ballroom and latin finals are composed of 5 dances each, with the WDSF specifying a lenght of 1min 30s - 2mins maximum duration of each song. For self-guided practice, being able to just play one sound file and have the whole final in one place is extremely useful. Manually editing songs, clipping them and adding them together is  a lot of work if one wants to generate multiple finals (to avoid boredom of always listening to the same final).

## Features

- Generate competition-length versions of audio files, including a fade out at the end for a smooth transition
- Generate the audio file for a final of all five dances, including a break between two songs
- You only need to specify the audio files and their associated dance, the rest is automatically accomplished by the code 

# Setup

## Requirements

- Python libraries:
  - Common libraries: os, pandas, dotenv
  - Special libraries: pydub
- Other software:
  - FFMPEG (Some package managers, e.g. Anaconda, can install it for your environment)

## Setup instructions

0. Install any requirements you have not yet installed.
1. Create a .env file for the finals generator to use. You need to set three variables:
   - MUSIC_IN: The path to your dance music. The generator is configured to automatically search all subfolders for the specified audio files, so you can set this path e.g. to your music library
   - SONGS_OUT: The path to the folder where you want to save the competition version of your songs
   - FINALS_OUT: The path to the folder where you want to save the finals audio files
2. Create a list_songs.txt file in which you save the songs and their dances.
3. Run the generate_comp_sons.ipynb notebook

## Song file setup

The file listing the songs, list_songs.txt, needs to be written in a specific way. The two large dance types (Latin & Standard) need to be specified with a "." in front of them. Dances need to be written on a new line with a "+" in front of them; their names are hardcoded. Songs need to be written underneath their dances on a new line with no special symbol. The song name should be the full file name. When searching for an audio file, the generator does not consider the file type, so any audio files will be used. The general structure hence is:

. Standard
+ Slow Waltz
song_1
+ Tango
song_2
+ Viennese Waltz
...
+ Slowfox
+ Quickstep
. Latin
+ Samba
+ Cha
+ Rumba
+ Paso Doble
+ Jive

Currently, there needs to be at least one audio file for any dance, otherwise the generator will fail. You can manually edit the notebook to remove one of the two dance types, or one of the dances (e.g. if you want to create a 3-song final for the D-Class).

# Potential future ideas

(ordered without priority)

- Separate generating competitive songs from generating finals
- Create a more flexible final: When not specifying a dance, skip the dance
