# RF Links (also known as Allstar Links)

HOIP allows extensions to be tied to an Allstar connection to allow others to dial in and use the Allstar Link.

Note that this does not enable Autopatch from the Allstar connection. This is a one way connection from HOIP to your Allstar system, basically a reverse autopatch if you will.

All Allstar Link Extensions will be in the format of `15nnn`, `25nnn` or `35nnn`.  Check out the [RF Links List](../../reference/rf-links-list.md) for details of other Links on the system.

## Guides

* [Configure an RF Link](./configure-rf-links.md) - _this will help you configure your own Allstar node to be an RF Link_

## Troubleshooting

Telemetry data from RF Links - in the form of text messages (SMS) - may be sent to the calling device which - in some cases - may cause it to drop the call.  The following Guides give detail on how - as an Allstar Node owner - you can prevent this from happening.

* [Remove SMS from ASL v1 or v2](./remove-sms-asl-1-2.md)
* [Remove SMS from ASL v3](./remove-sms-asl-3.md)
* [Remove SMS from HamVOIP](./remove-sms-hamvoip.md)

!!! note "Last updated 2025-07-22 Dave M7TLB"
