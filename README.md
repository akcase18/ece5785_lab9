# Lab 9: Verification
There are 2 interpretations:
1) The tracks are running parallel, and the crossing is a street crossing
2) The tracks cross at a point, and there can only be 1 train at the crossing at a time
## Invariants
### Environmental Invariants
- Depart signal will always happen after an approach signal (both)
- The power will never be interrupted (both)
- Trains on each track run in only one direction (1)
- All commands will be followed correct, and in a timely fashion (both)
- All sensors/inputs will work as described (both)
- The train will not reach the crossing before 10 seconds has elapsed since it went through the approach sensor (both)
- The train will not stop in the crossing (2)
- Only 1 train will enter the critical area (between the approach and depart sensors) at a time (2)
- The train won't enter the critical area if the barrier is down (2)
- The other train will stop if an alarm is on (2)
### Behavioral Invariants
- There will be a barrier down whenever a train is at the crossing (both)
- The alarm will be on from 10 seconds before until 10 seconds after the train is at the crossing (both)
- The barrier will be up whenever a train isn't present (both)
- The alarm will be on whenever a barrier is down (both)

## Validating Example FSM
If two trains trigger the approach sensors at the same time, what happens? There is no provision for this in the example FSM, and it could result in either both trains being stopped or neither train stopping.