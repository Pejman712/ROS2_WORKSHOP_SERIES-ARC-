# ROS 2 Workshop Series - ARC

This README explains how to pull and run the ROS 2 Humble TurtleBot3 VNC Docker image, open the desktop GUI, launch Gazebo, and drive the robot using keyboard teleoperation.

---

## 1. Log in to Docker Hub

```bash
docker login
```

---

## 2. Pull the ROS 2 Humble + TurtleBot3 VNC Image

Pull the latest image:

```bash
docker pull pjmrobotics/ros2-turtlebot3-vnc:latest
```

To pull a specific tag, replace `latest` with the tag name:

```bash
docker pull pjmrobotics/ros2-turtlebot3-vnc:tagname
```

---

## 3. Run the ROS 2 TurtleBot3 VNC Container

Start the container:

```bash
docker run --rm -it \
  --name ros2-turtlebot3-vnc \
  --shm-size=2g \
  -p 6080:80 \
  -p 5900:5900 \
  pjmrobotics/ros2-turtlebot3-vnc:latest
```

### Docker Options

| Option | Meaning |
|---|---|
| `--rm` | Removes the container after it exits |
| `-it` | Runs the container interactively with a terminal |
| `--name ros2-turtlebot3-vnc` | Gives the container a readable name |
| `--shm-size=2g` | Increases shared memory, useful for GUI and simulation workloads |
| `-p 6080:80` | Maps browser-based VNC/noVNC to host port `6080` |
| `-p 5900:5900` | Maps standard VNC to host port `5900` |
| `pjmrobotics/ros2-turtlebot3-vnc:latest` | The Docker image to run |

---

## 4. Open the GUI

After the container starts, open the noVNC interface in your browser:

```text
http://localhost:6080
```

If you are using a VNC client, connect to:

```text
localhost:5900
```

---

## 5. Initialize Gazebo

Inside the container terminal, set the TurtleBot3 model:

```bash
export TURTLEBOT3_MODEL=burger
```

Launch the TurtleBot3 Gazebo world:

```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

---

## 6. Drive the Robot

Open a new terminal inside the container, then set the TurtleBot3 model again:

```bash
export TURTLEBOT3_MODEL=burger
```

Run keyboard teleoperation:

```bash
ros2 run turtlebot3_teleop teleop_keyboard
```

Use the keyboard instructions shown in the terminal to drive the robot.

---

## Notes

- Keep the Gazebo launch terminal running while driving the robot.
- The `TURTLEBOT3_MODEL` environment variable must be set in each new terminal session.
- Use `Ctrl + C` to stop Gazebo or teleoperation.
