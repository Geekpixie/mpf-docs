---
title: Sounds, Music & Audio
---

!!! warning "MPF-MC is being deprecated"

    This instruction page is for the legacy MPF-MC for MPF versions 0.57 and prior. For users of MPF 0.80 and later, please refer to the [Godot Media Controller (GMC) Documentation](../../gmc/index.md)

# Sounds, Music & Audio


!!! note

    Everything in this "Displays & Graphics" section is about the
    default MPF Media Controller

Since the release of MPF 0.30, audio and sound support has been provided
by a custom audio library built on SDL2, SDL_Mixer, and GStreamer
libraries. This custom library allows the MPF development team to create
audio features optimized for pinball machines. The first release
provides basic sound loading and playback capabilities along with some
great new features like [ducking](ducking.md) and [sound pools](variations.md). (Sound support is part of the MPF media controller and only
available if you're using MPF-MC for your media controller).

The basic concept with audio in MPF is that you collect all your audio
files (16-bit .wav, .ogg, and .flac files are currently supported) and
put them in the `/sounds` folder in your machine folder (you can
organize them into sub-folders if you would like). Then in your config
file you create entries for each sound which map a friendly name to the
actual file on disk. You can also set a bunch of defaults for each
sound, such as volume, start time, etc. Then when you want to play a
sound in a game, you can refer to it by the friendly name from your
configuration file. You can also add entries into your configuration
file to set up sounds so they play based on certain MPF events. (For
example, play the sound "laser" every time the event from a pop bumper
being hit is posted.) You can also add sounds to your show files so they
play in-sync with lighting and display effects.

You can think of the audio system in MPF as a sound mixing board that
you control via configuration settings and events. It is divided into
[tracks](tracks.md) (similar to
channels on a mixer), each of which has its own properties such as name,
volume and the number of sounds that may be played simultaneously. New
in MPF 0.50 are specialized track types optimized for specific audio
tasks (such as music playback and creation). You can create up to 8
tracks in your sound system, although typically most machines will
typically use 3 standard tracks ("voice", "sfx", and "music").
Sounds are played on specific tracks and then the tracks are mixed
together to form the final mix. The sounds themselves are objects that
include many properties that control how they will be played such as
what track they play on, volume, looping, priority, how long to wait in
the playback queue before being discarded,
[ducking](ducking.md), etc.

Sounds can be grouped together into a logical grouping called a sound
pool. Sounds pools allow you to reference a group of sound variations as
if it were a single sound. A sound pool name may be used anywhere a
sound asset name may appear. Pools can be used for random differences in
a sound (such as slight variations of a slingshot sound) or for an
ordered sequence of sounds that will repeat. Another common use for
sound pools is to play a random callout from a defined list when
triggered.

You configure your sound system (including tracks) in the
[sound_system:](../../config/sound_system.md)
section of your machine configuration file. You add settings for
individual sound files in the
[sounds:](../../config/sounds.md) section. You
can configure sounds to automatically play on standard tracks when
selected MPF events are posted in the
[sound_player:](../../config_players/sound_player.md) section. Sound pools are specified in the
[sound_pools:](../../config/sound_pools.md)
section. Sound loop tracks use
[sound_loop_sets](../../config/sound_loop_sets.md) and the
[sound_loop_player](../../config_players/sound_loop_player.md) to play and loop sounds. Playlist tracks use
[playlists](../../config/playlists.md) and the
[playlist_player](../../config_players/playlist_player.md) for playing music. Tracks can be controlled when selected
MPF events are posted in the
[track_player:](../../config_players/track_player.md) section.

* [Technical Overview](technical.md)
* [Ducking](ducking.md)
* [Tracks](tracks.md)
* [How to set up sound](basic_setup.md)
* [Tips & tricks](tips_tricks.md)
* [Playing a sound with variations](variations.md)
