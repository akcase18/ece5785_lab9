# Lab 9: Verification
## Invariants
### Environmental Invariants
- Depart signal will always happen after an approach signal
- The power will never be interrupted
- Trains on each track run in only one direction
- All commands will be followed correct, and in a timely fashion
### Behavioral Invariants
- There will be a barrier down whenever a train is at the crossing
- The alarm will be on from 10 seconds before until 10 seconds after the train is at the crossing
- The barrier will be up whenever a train isn't present
- The alarm will be on whenever a barrier is down