# Lab 9: Verification
## Invariants
### Environmental Invariants
- Depart signal will always happen after an approach signal
- The power will never be interrupted
- Trains on each track run in only one direction
- All commands will be followed correct, and in a timely fashion
- All sensors/inputs will work as described
### Behavioral Invariants
- There will be a barrier down whenever a train is at the crossing
- The alarm will be on from 10 seconds before until 10 seconds after the train is at the crossing
- The barrier will be up whenever a train isn't present
- The alarm will be on whenever a barrier is down

## Validating Example FSM
Overall, this system falls apart if there are multiple trains within the operating area (between the approach sensor and departure sensor). The FSM has no way of sensing a train approaching except for just after "idle", so a second train approaching when the system is at any state other than "idle" will cause a safety hazard. Example:

- If you have a 2nd train approach after the first train has approached (between states "ringing, arms up" and "ringing, arms down"), the arms will raise after the first train departs, but the second train will still be at the crossing. This violates the invariant: "There will be a barrier down whenever a train is at the crossing".