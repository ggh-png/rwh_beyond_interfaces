# RWH Beyond Interfaces

이 저장소는 RWH Beyond의 ROS 2 인터페이스 패키지 `rwh_beyond_msgs`를 제공합니다.
협업 프로젝트는 이 패키지를 빌드해 BT의 `/run_demo` 액션을 호출할 수 있습니다.

| 액션 이름 | ROS 2 타입 | 용도 |
|---|---|---|
| `/run_demo` | `rwh_beyond_msgs/action/RunDemo` | BT 집기·배치와 실행 피드백 |
| `/infer_grasps` | `rwh_beyond_msgs/action/InferGrasps` | 파지 후보 추론 |
| `/segment_image` | `rwh_beyond_msgs/action/SegmentImage` | 이미지 분할 |

## 워크스페이스에 추가하기

접근 권한이 있는 GitHub 계정으로 인증한 다음, ROS 2 환경을 설정한
터미널의 워크스페이스 루트에서 실행합니다.

```bash
mkdir -p src
git clone https://github.com/ggh-png/rwh_beyond_interfaces.git src/rwh_beyond_interfaces
rosdep install --from-paths src --ignore-src -y
colcon build --packages-select rwh_beyond_msgs
source install/setup.bash
ros2 interface show rwh_beyond_msgs/action/RunDemo
```

워크스페이스에는 `rwh_beyond_msgs` 소스가 한 곳에만 있어야 합니다.
RWH Beyond와 함께 빌드할 때는 상위 프로젝트의 `moma-mj-lab.repos`에 고정된
리비전을 사용합니다. 외부 클라이언트도 같은 리비전을 사용하세요.

[RunDemo Goal·Result·Feedback 문서](https://ggh-png.github.io/rwh_beyond/bt-operation/)
