# Robotics | ROS 2 & Autonomous Navigation

![ROS 2](https://img.shields.io/badge/ROS_2-Humble-22314E?logo=ros&logoColor=white) ![Python](https://img.shields.io/badge/Python-rclpy-3776AB?logo=python&logoColor=white) ![Ubuntu](https://img.shields.io/badge/OS-Ubuntu-E95420?logo=ubuntu&logoColor=white)

ROS 2 기반 로봇 소프트웨어 개발을 학습하고 실습 코드를 기록하는 저장소입니다. ROS 2의 노드 및 토픽 통신부터 센서 데이터 처리, 시뮬레이션, 이후 SLAM과 Nav2를 활용한 자율주행까지 단계적으로 학습하는 것을 목표로 합니다.


## 개발 환경

- Ubuntu (듀얼 부팅)
- ROS 2 Humble
- Python / `rclpy`
- Visual Studio Code
- `colcon` 빌드 시스템
- Gazebo 및 RViz2: 시뮬레이션·시각화 학습 도구

## 현재 저장소 구성

```text
ros2_ws/
├── src/
│   ├── my_package/
│   │   ├── launch/
│   │   │   └── dual_timer.launch.py
│   │   ├── my_package/
│   │   │   ├── fast_timer.py
│   │   │   └── timer.py
│   │   ├── package.xml
│   │   └── setup.py
│   └── tutorial_topic/
│       ├── tutorial_topic/
│       │   ├── lidar_subscriber.py
│       │   └── move_publisher.py
│       ├── package.xml
│       └── setup.py
└── .gitignore
```

위 구조는 현재 확인된 주요 파일을 중심으로 간략화했습니다. `build/`, `install/`, `log/`는 빌드 시 자동 생성되며 Git 추적에서 제외합니다.

## 실습 코드

| 패키지 | 파일 | 학습 내용 |
| --- | --- | --- |
| `my_package` | `timer.py`, `fast_timer.py` | ROS 2 타이머 기반 노드 실습 |
| `my_package` | `dual_timer.launch.py` | Launch 파일을 통한 노드 실행 구성 |
| `tutorial_topic` | `lidar_subscriber.py` | `sensor_msgs/msg/LaserScan` 구독 및 LiDAR 거리 데이터 처리 |
| `tutorial_topic` | `move_publisher.py` | Publisher 노드 실습 |

> 파일명 및 이전 실습 내용을 바탕으로 정리했습니다. 각 노드의 정확한 토픽명과 실행 명령은 실제 코드의 설정을 기준으로 확인해야 합니다.

## 빌드 및 실행

ROS 2 Humble이 설치된 Ubuntu 환경을 기준으로 합니다.

```bash
cd ~/ros2_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install
source install/setup.bash
```

패키지와 실행 가능한 노드를 확인합니다.

```bash
ros2 pkg executables my_package
ros2 pkg executables tutorial_topic
```

실습 예시(실행 파일이 등록되어 있는 경우):

```bash
ros2 run tutorial_topic lidar_subscriber
```

LiDAR 구독 노드 실습에서 사용한 토픽은 `/scan_raw`이며, 해당 토픽을 발행하는 센서 또는 시뮬레이터가 실행 중이어야 데이터를 수신할 수 있습니다.

```bash
ros2 topic list
ros2 topic info /scan_raw
```

## 학습 로드맵

아래는 첨부된 강의 소개서의 구성에 따른 학습 주제입니다. 완료 여부는 추후 실습 결과에 맞춰 갱신합니다.

| 단계 | 주제 | 주요 학습 내용 | 상태 |
| --- | --- | --- | --- |
| 1 | 개발 환경 | Ubuntu, VS Code, ROS 2 Humble, Workspace | 실습 진행 |
| 2 | ROS 2 기초 | Package, Node, Launch, Topic, Publisher/Subscriber | 실습 진행 |
| 3 | ROS 2 통신·디버깅 | Service, Action, Executor, Callback Group, RViz2, RQt, rosbag2 | 학습 예정 / 확인 필요 |
| 4 | SLAM | Odometry, Cartographer, Mapping, AMCL, RGB-D Visual SLAM | 학습 예정 |
| 5 | Nav2 | Path Planning, Planner, Controller, Smoother, Costmap, 장애물 회피 | 학습 예정 |
| 6 | Nav2 응용 | Behavior Tree, 다중 로봇, Simple Commander API, Keepout/Speed Filter | 학습 예정 |

## 향후 목표

- ROS 2 Topic, Service, Action 통신 예제 확장
- Gazebo 환경에서 센서 데이터 수집 및 로봇 동작 실습
- SLAM 기반 지도 생성과 위치 추정
- Nav2 기반 경로 계획 및 장애물 회피
- 학습 결과, 실행 화면, 문제 해결 과정을 README에 지속적으로 기록


이 저장소는 ROS 2 및 자율주행 로봇 개발 학습 내용을 정리하는 개인 실습 기록입니다.