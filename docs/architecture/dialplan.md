# Dialplan

Fundamentally, Hams Over IP is a telephone exchange, and as such there is a defined dialplan. While the specifics are more complicated, the underlying principles are summarized below.

## Regions First

- Routing of 1xxx, 1xxxx, 1xxxxx, and 9xxxx goes to the US1 server
- Routing of 2xxxx, 2xxxxx goes to the EU server
- Routing of 3xxxx, 3xxxxx goes to the Asia/Pacific server

All of these servers are interconnected, but this first number will indicate where the target extension is initially routed.

## Length Indicates Role

- Two or three digits represent links to other VOIP networks; see the "Linked VOIP Networks" category in the side navigation for more details on these
- Four digit are used for admin extensions
- Five digit numbers are used for conference, RF link, and audio extensions
- Six digit numbers are used for end-user and trunk extensions

## Callsign Routing

Non-numerical extensions are matched against callsign routing, which is mapped to the corresponding extension. Note that this only applies to end-user and trunk extensions.

## RadioID Routing

[RadioIDs](https://radioid.net) are 7-digit unique identifiers for amateur callsigns issued by a platform-agnostic body. These identifiers are frequently used for digital voice modes as radio ids (thus the name). When provided by the registering user, these values are mapped to the corresponding user's extension. Note that this is provided as an opt-in process and manually maintained, so these should be viewed as a convenience or vanity compared to the tranditionally assigned extensions.
