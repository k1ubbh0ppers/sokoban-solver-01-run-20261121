# Sokoban solver entry

A deterministic Node 22 TypeScript program. It splits the board at the player's hallway row, finds each room component, and solves rooms one at a time in push space. Room search keys combine sorted box locations with the lowest square in the player's reachable region. An exact minimum Manhattan box-to-goal matching guides A*; each push stores a reconstructed shortest walk to its pushing square. The full-level path walks between room doors without moving other rooms' boxes.

## Measurements

The kit scorer reports push-optimal answers on all five practice instances (1,000,000/1,000,000). The house `plain-astar` baseline scores 200,000/1,000,000 on this same set.

| Instance | This solver | P* | Plain A* baseline |
| --- | ---: | ---: | --- |
| i001 | 13 | 13 | 13 (optimal) |
| i002 | 16 | 16 | unsolved within baseline budget |
| i003 | 29 | 29 | unsolved within baseline budget |
| i004 | 47 | 47 | unsolved within baseline budget |
| i005 | 60 | 60 | unsolved within baseline budget |

The solver took about 1.4 seconds for the practice set locally. A second run produced byte-identical solution files. I also generated a separate set with the kit generator; all five instances, including its four-room/sixteen-box instance, scored at their push-optimal counts (about 1.4 seconds total).
