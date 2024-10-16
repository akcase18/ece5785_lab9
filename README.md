# Lab 9: Verification
## Invariants
### Environmental Invariants
- Depart signal will always occur after an approach signal
- The power will never be interrupted
- The alarm will only sound after a train has been detected
- Trains on each track run in only one direction
- All commands will be followed correct, and in a timely fashion
- All sensors/inputs will work as described
- The train will not reach the crossing before 10 seconds has elapsed since it went through the approach sensor
- There will only be 2 trains at the crossing at one time
- There cannot be 2 trains on the same track at the same time
### Behavioral Invariants
- There will be a barrier from 10 seconds after the approach sensor is triggered, until the depart sensor is triggered
- The alarm will be on whenever a train is present (from approach until departure)
- The barrier will be up whenever a train isn't present
- The alarm will be on whenever a barrier is down                                                         

## Validating Example FSM
This FSM cannot handle 2 trains at the same time. Once one train enters the system, the FSM doesn't check the approach sensors, and could result in a train (the second one) being at the crossing when the barrier is up.

## Proving the FSM

| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | time_elapsed | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|--------------|---------------|
| 0      | 0         | 0        | 0                  | 0                  | 6              | 5              | 16           | 16           | 18           | -             |
| 1      | 0         | 0        | 0                  | 1                  | -              | -              | -            | -            | -            | 25            |
| 2      | 0         | 0        | 1                  | 0                  | -              | -              | -            | -            | -            | 25            |
| 3      | 0         | 0        | 1                  | 1                  | -              | -              | -            | -            | -            | 25            |
| 4      | 0         | 1        | 0                  | 0                  | 6              | 5              | 16           | 16           | 0            | -             |
| 5      | 0         | 1        | 0                  | 1                  | 7              | 28             | 16           | 24           | 13           | -             |
| 6      | 0         | 1        | 1                  | 0                  | 28             | 7              | 24           | 16           | 14           | -             |
| 7      | 0         | 1        | 1                  | 1                  | 28             | 28             | 24           | 24           | 15           | -             |
| 8      | 1         | 0        | 0                  | 0                  | -              | -              | -            | -            | -            | 26, 27        |
| 9      | 1         | 0        | 0                  | 1                  | -              | -              | -            | -            | -            | 25, 27        |
| 10     | 1         | 0        | 1                  | 0                  | -              | -              | -            | -            | -            | 25, 27        |
| 11     | 1         | 0        | 1                  | 1                  | -              | -              | -            | -            | -            | 25, 27        |
| 12     | 1         | 1        | 0                  | 0                  | -              | -              | -            | -            | -            | 18, 26        |
| 13     | 1         | 1        | 0                  | 1                  | 15             | 28             | 16           | 4            | 21           | -             |
| 14     | 1         | 1        | 1                  | 0                  | 28             | 15             | 4            | 16           | 21           | -             |
| 15     | 1         | 1        | 1                  | 1                  | 28             | 28             | 13           | 14           | 21           | -             |

| number | invariant                                                                                                            |
|--------|----------------------------------------------------------------------------------------------------------------------|
| 16     | Depart signal will always occur after an approach signal                                                             |
| 17     | The power will never be interrupted                                                                                  |
| 18     | The alarm will only sound after a train has been detected                                                            |
| 19     | Trains on each track run in only one direction                                                                       |
| 20     | All commands will be followed correct, and in a timely fashion                                                       |
| 21     | All sensors/inputs will work as described                                                                            |
| 22     | The train will not reach the crossing before 10 seconds has elapsed since it went through the approach sensor        |
| 23     | There will only be 2 trains at the crossing at one time                                                              |
| 24     | There will be a barrier from 10 seconds after the approach sensor is triggered, until the depart sensor is triggered |
| 25     | The alarm will be on whenever a train is present (from approach until departure)                                     |
| 26     | The barrier will be up whenever a train isn't present                                                                |
| 27     | The alarm will be on whenever a barrier is down                                                                      |
| 28     | There cannot be 2 trains on the same track at the same time                                                          |