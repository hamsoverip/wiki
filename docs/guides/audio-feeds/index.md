# Audio Feeds

HOIP allows extensions to be connected via a trunk to other PBXes to provide audio feeds from either static audio files or Shoutcast/Icecast feeds to allow HOIP users to dial in and listen to them at any time they wish.  Check out the [Audio Feeds List](../../reference/audio-feeds-list.md) for details of existing Feeds on the system.

All Audio Feeds Extensions will be in the format of `90nnn`.

## Guides

To request an Audio Feed with Hams Over IP, simply raise an "Audio Feed Request" ticket over at our [Helpdesk :material-open-in-new:](https://helpdesk.hamsoverip.com/osticket/){ target="_blank" } to get the Extension Number (username) and password required to set up on your PBX.

At this time we do not have a set of Guides for setting up an Audio Feed at your PBX, so there is an element of you understanding how to set up the Audio Feed in the first place using the MusicOnHold module of your PBX software of choice.

Instructions for setting up a Trunk to handle the inbound call from Hams Over IP is _effectively_ the same as a [PBX Trunk](../pbx/index.md), with the following fundamental differences:

* there is no requirement for an Outbound Route as the Audio Feed will be inbound-only
* rather than terminating at an endpoint device, the inbound call will need to be directed to

As mentioned earlier, this is something we have no solid documentation for until some generous individual who has already done this once before provides it to us so that we can share it with everyone.

!!! note "Last updated 2025-07-29 Dave M7TLB"
