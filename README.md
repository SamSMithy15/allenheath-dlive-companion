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

Download the latest `.tgz` package from the [Releases](../../releases) page.

In Companion:

1. Open the Companion web interface.
2. Go to **Modules → Import module package**.
3. Select the downloaded `.tgz` file.
4. Go to **Connections**.
5. Search for `dLive`.
6. Select **Allen & Heath dLive (two-way)**.
7. Select the installed module version.
8. Add the connection.

> Keep the `.tgz` file as-is. Do not extract it before importing it into Companion.

## dLive Setup

### 1. Find the MixRack IP address

On the dLive:

**MixRack Setup → Config → Network**

The factory default IP address is commonly:

`192.168.1.70`

Your Companion computer must be on the same network.

### 2. Enable MIDI over the network

On the dLive:

**Utility → Control → MixRack Security**

Set:

`Security Level → No Security`

A MixRack restart may be required.

Then go to:

**Utility → Control → MIDI**

Make sure:

- **Send:** On
- **Receive:** On

Write down the first MIDI channel configured on the desk.

> MIDI Send must be enabled for Companion to receive desk changes.

## Companion Connection Settings

| Setting | Value |
|---|---|
| MixRack IP | Your MixRack IP |
| Connect to | MixRack |
| TCP Port | `0` |
| MIDI Base Channel | Same as dLive |

Leave the TCP port at `0`.

The module automatically uses the appropriate MixRack MIDI-over-TCP connection.

> Do not enter the Surface port.

## Feedback Variables

Replace `dlive` with the label of your Companion connection.

### Input 1 fader level

```text
$(dlive:input_1_level)
