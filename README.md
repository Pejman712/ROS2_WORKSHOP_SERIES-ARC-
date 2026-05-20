# ROS 2 Workshop Series - ARC

This README explains how to run the ROS 2 Humble TurtleBot3 VNC Docker image using Docker Compose, open the desktop GUI, launch Gazebo, and drive the robot using keyboard teleoperation.

---

## Quick Start

```bash
docker compose up
```

This command will pull the image (if needed) and start the container with all necessary configurations pre-set.

To stop and remove the container:

```bash
docker compose down
```

---

## Open the GUI

After the container starts, open the noVNC interface in your browser:

```text
http://localhost:6080
```

If you are using a VNC client, connect to:

```text
localhost:5900
```

---

## Launch Gazebo

In the noVNC browser window, open a terminal and launch the TurtleBot3 Gazebo world:

```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

The `TURTLEBOT3_MODEL` environment variable is pre-configured in the Docker Compose setup, so no export is needed.

---

## Drive the Robot

In the noVNC browser window, open a second terminal and run keyboard teleoperation:

```bash
ros2 run turtlebot3_teleop teleop_keyboard
```

Use the keyboard instructions shown in the terminal to drive the robot.

---

## Notes

- Keep the Gazebo launch terminal running while driving the robot.
- Use `Ctrl + C` to stop Gazebo or teleoperation.
- Run `docker compose down` to stop and remove the container when finished.
