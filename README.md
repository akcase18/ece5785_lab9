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
- 2 trains will not arrive/approach at the exact same time (2)
### Behavioral Invariants
- There will be a barrier down whenever a train is at the crossing (both)
- The alarm will be on from 10 seconds before until 10 seconds after the train is at the crossing (both)
- The barrier will be up whenever a train isn't present (both)
- The alarm will be on whenever a barrier is down (both)

## Validating Example FSM
For interpretation 1:
- This FSM cannot handle 2 trains at the same time. Once one train enters the system, the FSM doesn't check the approach sensors, and could result in a train being at the crossing when the barrier is up.

For interpretation 2:
- What happens if two trains trigger the approach sensors at the same time? This is undefined behavior that is not explained in the FSM.

