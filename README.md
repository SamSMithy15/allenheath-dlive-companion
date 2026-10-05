# Allen & Heath dLive Two-Way for Bitfocus Companion

A custom Bitfocus Companion module for Allen & Heath dLive consoles.

This module provides two-way communication between Bitfocus Companion and the dLive, allowing Companion buttons to show live fader levels, mute states, channel names, and other feedback from the desk.

## Features

- Two-way dLive communication
- Live fader level feedback
- Live mute feedback
- Input channel names
- DCA level feedback
- Set exact fader levels
- Nudge faders up or down
- Mute / unmute / toggle
- Scene recall
- Request current values from the desk
- Ready-to-use button presets

## Requirements

- Bitfocus Companion 5.0.4 or newer
- Allen & Heath dLive MixRack
- Companion computer and MixRack on the same network

## Installation

Download the latest .tgz package from the Releases page.

In Bitfocus Companion:

1. Open the Companion web interface.
2. Go to Modules → Import module package.
3. Select the downloaded .tgz file.
4. Go to Connections.
5. Search for dLive.
6. Select Allen & Heath dLive (two-way).
7. Select the installed module version.
8. Click Add.

Keep the .tgz file as-is. Do not extract it before importing it into Companion.

### Companion 5.0.4 or newer

This module requires Companion 5.0.4 or newer. Companion 4 is not supported.

If importing from a different computer, Companion may require Restricted modules to be enabled.

## dLive Setup

### 1. Find the MixRack IP address

On the dLive:

MixRack Setup → Config → Network

The factory default IP address is:

192.168.1.70

Your Companion computer must have its own IP address on the same network.

Example:

MixRack: 192.168.1.70
Companion computer: 192.168.1.50

### 2. Enable MIDI over the network

On the dLive:

Utility → Control → MixRack Security

Set:

Security Level → No Security

The MixRack may require a restart after changing this setting.

Then go to:

Utility → Control → MIDI

Write down the first MIDI channel configured on the desk.

Make sure both are enabled:

- Send: On
- Receive: On

MIDI Send must be enabled for Companion to receive fader and mute changes made on the desk.

## Companion Connection Settings

Configure the dLive Two-Way connection in Companion using:

Setting | Value
MixRack IP | Your MixRack IP address
Connect to | MixRack
TCP Port | 0
MIDI Base Channel | Same as the dLive

Leave the TCP port set to 0.

The module will use the appropriate MixRack MIDI-over-TCP connection.

Do not enter 51328. That is the Surface port. The MixRack uses port 51325.

## Checking the Connection

Once configured, the Companion connection should turn green and show OK.

Open the module's Presets tab to find ready-made buttons.

For example:

CH 1
-12.5 dB

Move the first fader on the dLive.

The value shown on the Companion button should update to match the desk.

## Feedback Variables

You can use the module's variables directly in Companion button text.

Replace dlive with the label of your dLive Two-Way connection.

Input 1 fader level:

$(dlive:input_1_level)

Input 1 mute:

$(dlive:input_1_mute)

Input 1 name:

$(dlive:input_1_name)

DCA 3 level:

$(dlive:dca_3_level)

These variables update when the corresponding value changes.

## Actions

The module supports actions for:

- Set an exact fader level
- Increase a fader by a specified amount
- Decrease a fader by a specified amount
- Mute
- Unmute
- Toggle mute
- Recall scenes
- Request all current values from the desk

## Fader Levels

The dLive operates in 0.5 dB steps.

For example:

-12.5 dB

is an exact valid dLive level.

Because the desk operates in 0.5 dB steps, a nudge of +1.25 dB will be rounded to the nearest available step.

For predictable results, use whole or half-dB increments.

Below approximately -53 dB, the fader reaches:

-inf

## Scene Feedback

The current scene becomes available after a scene has been recalled.

The dLive does not provide a way for the module to simply ask the desk which scene is currently active.

## Troubleshooting

### Fader feedback is not updating

First check that MIDI Send is enabled on the dLive.

Then try the Companion action:

Request all current values from the desk again

You can also turn the Companion connection off and back on.

Changes made from Companion should update correctly.

### The module will not connect

Check the following:

- The MixRack IP address is correct.
- The Companion computer and MixRack are on the same network.
- The network cable is connected to the MixRack network port.
- MixRack Security Level is not blocking TCP MIDI.
- MIDI Send is enabled.
- MIDI Receive is enabled.
- The Companion computer's firewall allows TCP port 51325.

## Testing

Version 0.1.2 has been tested against two separate practice MixRacks.

- 35 module tests passed
- 68 cross-checks passed

## Known Limitations

- dLive fader levels are limited to 0.5 dB steps.
- Values below approximately -53 dB are represented as -inf.
- The current scene cannot simply be queried from the desk.

## Version

Current version:

0.1.2

Download the latest version from the Releases page.

## License

This project is licensed under the MIT License.
