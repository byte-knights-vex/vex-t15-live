# Wall Maze

The robot starts at the bottom of a maze. Around the maze are markers: **A**, **B**, **1**, **2**, **3** and **Finish**.

You won't measure every distance. Instead, the robot drives until its bumper hits a wall, then turns. Your starter has the robot set up and nothing else.

```actions
- camera: top
- load-starter
```

---

# Bump and turn

This loop drives forward until the left bumper is pressed:

```python
while not left_bumper.pressing():
    drivetrain.drive(FORWARD)
    wait(5, MSEC)
drivetrain.stop()
```

Then turn to face a new direction. Headings are in degrees: 0 is up the field, 90 is right, 180 is down, 270 is left.

```python
drivetrain.turn_to_heading(270, DEGREES)
```

Set a slow, steady speed first: `drivetrain.set_drive_velocity(30, PERCENT)`.

---

# Reach A

Use bump-and-turn to drive to marker **A**. Plan the route on the top view first.

```actions
- run
- reset-world
- camera: top
```

```gates
- regionReached: A
- runCompleted
```

---

# Reach B

Now find a route to marker **B**. It's farther in, so you'll need more turns. `drive_for` can help when there's no wall to bump into:

```python
drivetrain.drive_for(REVERSE, 300, MM)
```

```actions
- run
- reset-world
```

```gates
- regionReached: B
- runCompleted
```

---

# Reach 2

Next, marker **2**.

```actions
- run
- reset-world
```

```gates
- regionReached: 2
- runCompleted
```

---

# Reach 3

Then marker **3**, deeper in the maze.

```actions
- run
- reset-world
```

```gates
- regionReached: 3
- runCompleted
```

---

# Finish

Drive all the way to **Finish**.

```actions
- run
- reset-world
- camera: follow
```

```gates
- regionReached: Finish
- runCompleted
```

---

# Challenge: no touching

Bumpers only work by hitting walls. The distance sensor sees a wall before you touch it:

```python
while distance.object_distance(MM) > 50:
    drivetrain.drive(FORWARD)
    wait(5, MSEC)
drivetrain.stop()
```

Reach marker **3** again, this time **without touching any wall**.

```actions
- run
- reset-world
```

```gates
- regionReached: 3
- noWallContact
- runCompleted
```
