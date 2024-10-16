# Lab 9: Verification
## Invariants
### Environmental Invariants
- Depart signal will always happen after an approach signal
- The power will never be interrupted
- Trains on each track run in only one direction
- All commands will be followed correct, and in a timely fashion
- All sensors/inputs will work as described
- The train will not reach the crossing before 10 seconds has elapsed since it went through the approach sensor
- There will only be 2 trains at the crossing at one time
### Behavioral Invariants
- There will be a barrier down whenever a train is at the crossing
- The alarm will be on from 10 seconds before until 10 seconds after the train is at the crossing
- The barrier will be up whenever a train isn't present
- The alarm will be on whenever a barrier is down

## Validating Example FSM
This FSM cannot handle 2 trains at the same time. Once one train enters the system, the FSM doesn't check the approach sensors, and could result in a train (the second one) being at the crossing when the barrier is up.

