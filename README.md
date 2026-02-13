# AAE5303 Environment Setup Report Assignment1_25005153G
> **Important:** Follow this structure exactly in your submission README.  
> Your goal is to demonstrate **evidence, process, problem-solving, and reflection** — not only screenshots.

---

## 1. System Information

**Laptop model:**  
ASUS TUF Gaming A15

**CPU / RAM:**  
AMD Ryzen 9 8945H w/ Radeon 780M Graphics, 16GB RAM

**Host OS:**  
Windows 11

**Linux/ROS environment type:**  
_[Choose one:]_
- [ ] Dual-boot Ubuntu
- [ ] WSL2 Ubuntu
- [√] Ubuntu in VM (UTM/VirtualBox/VMware/Parallels)
- [ ] Docker container
- [ ] Lab PC
- [ ] Remote Linux server

---

## 2. Python Environment Check

### 2.1 Steps Taken

Describe briefly how you created/activated your Python environment:

**Tool used:**  
venv

**Key commands you ran:**
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

**Any deviations from the default instructions:**  
None

### 2.2 Test Results

Run these commands and paste the actual terminal output (not just screenshots):

```bash
python scripts/test_python_env.py
```

**Output:**
```
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ python scripts/run_smoke_tests.py
========================================
AAE5303 One-command Environment Check
Tip: read README.md for interpretation and fixes.
========================================


========== Step 1: Python + ROS environment checks ==========
Running: /home/mizukireisei/aae5303-env-check/.venv/bin/python -u /home/mizukireisei/aae5303-env-check/scripts/test_python_env.py
========================================
AAE5303 Environment Check (Python + ROS)
Goal: help you verify your environment and understand what each check means.
========================================

Step 1: Environment snapshot
  Why: We capture platform/Python/ROS variables to diagnose common setup mistakes (especially mixed ROS env).
Step 2: Python version
  Why: The course assumes Python 3.10+; older versions often break package wheels.
Step 3: Python imports (required/optional)
  Why: Imports verify packages are installed and compatible with your Python version.
Step 4: NumPy sanity checks
  Why: We run a small linear algebra operation so success means more than just `import numpy`.
Step 5: SciPy sanity checks
  Why: We run a small FFT to confirm SciPy is functional (not just installed).
Step 6: Matplotlib backend check
  Why: We generate a tiny plot image (headless) to confirm plotting works on your system.
Step 7: OpenCV PNG decoding (subprocess)
  Why: PNG decoding uses native code; we isolate it so corruption/codec issues cannot crash the whole report.
Step 8: Open3D basic geometry + I/O (subprocess)
  Why: Open3D is a native extension; ABI mismatches can segfault. Subprocess isolation turns crashes into readable failures.
Step 9: ROS toolchain checks
  Why: The course requires ROS tooling. This check passes if ROS 2 OR ROS 1 is available (either one is acceptable).
  Action: building ROS 2 workspace package `env_check_pkg` (this may take 1-3 minutes on first run)...
  Action: running ROS 2 talker/listener for a few seconds to verify messages flow...
Step 10: Basic CLI availability
  Why: We confirm core commands exist on PATH so students can run the same commands as in the labs.

=== Summary ===
✅ Environment: {
  "platform": "Linux-6.8.0-94-generic-x86_64-with-glibc2.35",
  "python": "3.10.12",
  "executable": "/home/mizukireisei/aae5303-env-check/.venv/bin/python",
  "cwd": "/home/mizukireisei/aae5303-env-check",
  "ros": {
    "ROS_VERSION": "2",
    "ROS_DISTRO": "humble",
    "ROS_ROOT": null,
    "ROS_PACKAGE_PATH": null,
    "AMENT_PREFIX_PATH": "/home/mizukireisei/aae5303-env-check/ros2_ws/install/env_check_pkg:/opt/ros/humble",
    "CMAKE_PREFIX_PATH": "/home/mizukireisei/aae5303-env-check/ros2_ws/install/env_check_pkg"
  }
}
✅ Python version OK: 3.10.12
✅ Module 'numpy' found (v2.2.6).
✅ Module 'scipy' found (v1.15.3).
✅ Module 'matplotlib' found (v3.10.8).
✅ Module 'cv2' found (v4.13.0).
✅ Module 'rclpy' found (vunknown).
✅ numpy matrix multiply OK.
✅ numpy version 2.2.6 detected.
✅ scipy FFT OK.
✅ scipy version 1.15.3 detected.
✅ matplotlib backend OK (Agg), version 3.10.8.
✅ OpenCV OK (v4.13.0), decoded sample image 128x128.
✅ Open3D OK (v0.19.0), NumPy 2.2.6.
✅ Open3D loaded sample PCD with 8 pts and completed round-trip I/O.
✅ ROS 2 CLI OK: /opt/ros/humble/bin/ros2
✅ ROS 1 tools not found (acceptable if ROS 2 is installed).
✅ colcon found: /usr/bin/colcon
✅ ROS 2 workspace build OK (env_check_pkg).
✅ ROS 2 runtime OK: talker and listener exchanged messages.
✅ Binary 'python3' found at /home/mizukireisei/aae5303-env-check/.venv/bin/python3

All checks passed. You are ready for AAE5303 🚀
✅ Python + ROS environment checks: PASS (12.2s)

========== Step 2: Open3D point cloud pipeline ==========
Running: /home/mizukireisei/aae5303-env-check/.venv/bin/python -u /home/mizukireisei/aae5303-env-check/scripts/test_open3d_pointcloud.py
ℹ️ Loading /home/mizukireisei/aae5303-env-check/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /home/mizukireisei/aae5303-env-check/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.
✅ Open3D point cloud pipeline: PASS (1.9s)

ℹ️ Cleaned up 1 generated file(s) in data/.

========================================
OVERALL RESULT: PASS
========================================

```

```bash
python scripts/test_open3d_pointcloud.py
```

**Output:**
```
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ python scripts/test_open3d_pointcloud.py
ℹ️ Loading /home/mizukireisei/aae5303-env-check/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /home/mizukireisei/aae5303-env-check/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.

```

**Screenshot:**  
_[Include one screenshot showing both tests passing]_

<img width="1284" height="1249" alt="image" src="https://github.com/user-attachments/assets/8dde5477-8e3a-4288-93a6-f4f15c3c5d8f" />

---

## 3. ROS 2 Workspace Check

### 3.1 Build the workspace

Paste the build output summary (final lines only):

```bash
source /opt/ros/humble/setup.bash
colcon build
```

**Expected output:**
```
Summary: 1 package finished [x.xx s]
```

**Your actual output:**
```
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check/ros2_ws$ colcon build
Starting >>> env_check_pkg
Finished <<< env_check_pkg [11.1s]                       

Summary: 1 package finished [11.3s]

```

### 3.2 Run talker and listener

Show both source commands:

```bash
source /opt/ros/humble/setup.bash
source install/setup.bash
```

**Then run talker:**
```bash
ros2 run env_check_pkg talker.py
```

**Output (3–4 lines):**
```
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ ros2 run env_check_pkg talker
[INFO] [1770968792.807432626] [env_check_pkg_talker]: AAE5303 talker ready (publishing at 2 Hz).
[INFO] [1770968793.308112587] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #0'
[INFO] [1770968793.807662470] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #1'
[INFO] [1770968794.308167565] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #2'
[INFO] [1770968794.808657473] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #3'
[INFO] [1770968795.308616852] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #4'
[INFO] [1770968795.807898628] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #5'

```

**Run listener:**
```bash
ros2 run env_check_pkg listener.py
```

**Output (3–4 lines):**
```
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ ros2 run env_check_pkg listener
[INFO] [1770968861.246204394] [env_check_pkg_listener]: AAE5303 listener awaiting messages.
[INFO] [1770968861.303873602] [env_check_pkg_listener]: I heard: 'AAE5303 hello #136'
[INFO] [1770968861.804315756] [env_check_pkg_listener]: I heard: 'AAE5303 hello #137'
[INFO] [1770968862.304325866] [env_check_pkg_listener]: I heard: 'AAE5303 hello #138'
[INFO] [1770968862.804650763] [env_check_pkg_listener]: I heard: 'AAE5303 hello #139'

```

**Alternative (using launch file):**
```bash
ros2 launch env_check_pkg env_check.launch.py
```

**Screenshot:**  

<img width="1209" height="1125" alt="image" src="https://github.com/user-attachments/assets/beb932f0-acae-44eb-b3de-f7fed596bb5b" />



---

## 4. Problems Encountered and How I Solved Them

> **Note:** Write 2–3 issues, even if small. This section is crucial — it demonstrates understanding and problem-solving.

### Issue 1: 
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ apt install numpy
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


**Cause / diagnosis:**  
I didn't use sudo to install packages

**Fix:**  
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ sudo apt install numpy
```bash
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ sudo apt install numpy
```

**Reference:**  
Gemini

---

### Issue 2: 
❌ colcon not found on PATH (required for ROS 2 builds).


**Cause / diagnosis:**  
I didn't install colcon package
**Fix:**  
↳ Fix: On Ubuntu/WSL2:
  - sudo apt update
  - sudo apt install python3-colcon-common-extensions


```bash
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ sudo apt install python3-colcon-common-extensions
```

**Reference:**  
Learning Materials

---


## 5. Use of Generative AI (Required)

Choose one of the issues above and document how you used AI to solve it.

> **Goal:** Show critical use of AI, not blind copying.

### 5.1 Exact prompt you asked

**Your prompt:**
```
文件里没有talker.py和listener.py
```

### 5.2 Key helpful part of the AI's answer

**AI's response (relevant part only):**
```
看来你遇到了一个很经典的“误会”：在 ROS 2 的 ros2 run 命令中，即便你的源代码文件叫 talker.py，但在某些配置下，它在系统里的“花名”（可执行文件名）可能并不带 .py 后缀
```

### 5.3 What you changed or ignored and why

Explain briefly:
- Did the AI recommend something unsafe?
- Did you modify its solution?
- Did you double-check with official docs?

**Your explanation:**  
It recommended nothing unsafe. I was using bing to modify at the same time.

### 5.4 Final solution you applied

Show the exact command or file edit that fixed the problem:

```bash
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ find ~/aae5303-env-check/ros2_ws/src -name "talker*"
/home/mizukireisei/aae5303-env-check/ros2_ws/src/env_check_pkg/src/talker.cpp
(.venv) mizukireisei@mizukireisei-virtual-machine:~/aae5303-env-check$ ros2 run env_check_pkg talker

```

**Why this worked:**  
I found that the code was named talker.cpp and I just egnored that".py"

---

## 6. Reflection (3–5 sentences)

Short but thoughtful:

- What did you learn about configuring robotics environments?
- What surprised you?
- What would you do differently next time (backup, partitioning, reading error logs, asking better AI questions)?
- How confident do you feel about debugging ROS/Python issues now?

**Your reflection:**
- Configuring robotics environments requires meticulous attention to both system-level dependencies (like colcon and locales) and Python-specific dependencies within virtual environments.
- Next time, I would proactively read error logs for specific missing libraries rather than assuming the error is with the command itself.

---

## 7. Declaration

✅ **I confirm that I performed this setup myself and all screenshots/logs reflect my own environment.**

**Name:**  
DU Jiayi Rachel

**Student ID:**  
25005153G
**Date:**  
13/2/2026

---

## Submission Checklist

Before submitting, ensure you have:

- [√] Filled in all system information
- [√] Included actual terminal outputs (not just screenshots)
- [√] Provided at least 2 screenshots (Python tests + ROS talker/listener)
- [√] Documented 2–3 real problems with solutions
- [√] Completed the AI usage section with exact prompts
- [√] Written a thoughtful reflection (3–5 sentences)
- [√] Signed the declaration

---

**End of Report**
