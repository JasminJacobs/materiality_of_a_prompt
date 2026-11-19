# Materiality of a Prompt — Visual legend (updated 19 Nov 2026, v1.0)

Colour shows **certainty** (as in the footer "Reading the data"); an icon on the line shows **access** (who owns it). No dashes.
(Tried and dropped: colour = access, dashes = certainty. v0.9 had double lines and casings for access; replaced by icons, as on the website.)

## Colour = how sure we are (certainty)
| Colour | Certainty |
|---|---|
| White #FFFFFF | Certain: measured (traceroute) or published |
| Blue #3FF9FF | Uncertain: estimated, or likely but not confirmed |
| Red #FF3F88 | No data: nothing is published |

## Icon = who owns it (access)
| Access | Scene | Line | Square in the counter |
|---|---|---|---|
| Public | 1 Public Enter | Plain line, no icon | Plain filled square |
| Shared | 2 Shared Exchange | Line with the shared icon (two overlapping rings) every ~150 px | Filled square with the two-ring icon |
| Private | 3 Private Enclosure | Line with the lock icon every ~150 px | Filled square with the lock icon |

Icons sit on a dark disc so they stay readable on the line; they take the line's colour (certainty).
Radio (device → router / antenna) stays a dotted line.

## Uncertain vs. no data
- Uncertain = there is a basis (our estimate, an external estimate such as Epoch AI, or "likely" in Epoch AI), but not confirmed.
- No data = nothing published to base an estimate on (e.g. which Google data centre answers; Proton's power and chips; repeaters on the sea floor).
- Something moves from no data to uncertain once we estimate it ourselves.
- Data centre cards show only facts that are published and verified; a fact nobody publishes is left out of the card.

## Codes next to values
| Code | Meaning | Colour |
|---|---|---|
| SR | Self-reported by the company | White |
| EXT | External estimate (e.g. Epoch AI, Projet Celsius) | Blue |
| EST | Our own estimate | Blue |
| ? | No data provided | Red |

## Cable counter
- 1 square = 25 km, same scale in all three scenes, adds up from Enter to Enclosure; last square fills gradually.
- Groups per cable type (radio, copper / coax / fibre, sea cable), each ending in its symbol.
- Squares shrink only when the column (down to the tally) is full.
