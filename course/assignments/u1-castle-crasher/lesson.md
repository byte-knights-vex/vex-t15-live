# Castle Crasher

Your robot starts at the bottom of the field. In the middle stands a castle made of blocks, with four smaller castles in the corners.

Your first job: **drive into the middle castle and knock it down.**

Use the camera buttons to look around the field.

```actions
- camera: top
- camera: follow
```

---

# Meet the starter

Your `main.py` already has a program in it. The top part, between `#region` and `#endregion`, sets up the robot:

- two drive motors, on ports 1 and 10
- an inertial sensor, so the robot knows which way it's facing
- a `drivetrain` that drives both motors together

Leave that part alone. Your code goes under `# Your code here`:

```python
drivetrain.set_drive_velocity(50, PERCENT)
drivetrain.set_turn_velocity(50, PERCENT)
drivetrain.drive_for(FORWARD, 800, MM, 50, PERCENT)
```

If your code ever gets messed up, you can start over:

```actions
- load-starter
```

---

# Run it

Press **Run** and watch the robot. Did it reach the castle?

```actions
- run
- reset-world
```

To go on, crash the middle castle: knock over at least 5 of its 10 pieces, and let the program finish without an error.

```gates
- objectsMoved: {ids: [castle-center-*], minCount: 5}
- runCompleted
```

---

# How drive_for works

```python
drivetrain.drive_for(FORWARD, 800, MM, 50, PERCENT)
```

| Part | Meaning |
|---|---|
| `FORWARD` | which way to drive (`REVERSE` backs up) |
| `800, MM` | how far: 800 millimeters |
| `50, PERCENT` | how fast: half speed |

The program waits until the robot has driven the whole 800 mm, then goes on to the next line.

---

# Make it yours

Try changing the program, then run it again:

- Drive farther, or faster. What happens to the castle?
- Add a turn: `drivetrain.turn_for(RIGHT, 90, DEGREES)`
- Can you reach one of the corner castles?

```actions
- run
- reset-world
- camera: follow
```

---

# Done

You drove a robot with Python. Everything you write is saved and checked in for your teacher.

Next up: the Wall Maze. Press **Back to assignments** to pick it.
