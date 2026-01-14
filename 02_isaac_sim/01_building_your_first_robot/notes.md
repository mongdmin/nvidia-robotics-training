# Isaac Sim/1 - Study Notes

## 느낀점
이번 챕터를 실습하면서, 내가 원하는 기능의 로봇을 만들려면  
계층(Hierarchy)+물리(Physics)+제어(Control)+센서(Sensors)+ROS 2(Streaming)가
하나로 연결돼야 하고, 하나라도 빠지면 전체가 동작하지 않는다는 걸 확실히 깨달았다.

---

## 내가 확실히 익힌 것들
- Isaac Sim 기본 조작/UI(Stage/Properties/Viewport)와 작업 흐름을 익혔다.
- Visual mesh만으로는 물리 상호작용이 안 되고, 물리 기반 시뮬을 위해  
  `Physics Scene + Rigid Body + Colliders + Ground`가 필요하다는 걸 체감했다.
- 로봇을 만들 때 부모 Xform 아래에서 구조를 잘 잡는 것이 관리/확장에 중요했다.
- OmniGraph(차동 제어 + 키보드 입력)로 로봇을 “제어 가능한 시스템”으로 만들었다.
- RGB 카메라 + 2D LiDAR를 장착하고 센서 시각화로 동작을 확인했다.
- ROS 2 Bridge + ActionGraph로 LiDAR 데이터를 ROS 2로 publish하고 RViz에서 확인했다.
  (ActionGraph가 센서 데이터를 읽고 토픽으로 내보내는 핵심 파이프라인이라 중요했다.)

---

## 꿀팁
- RViz에서 안 보이면 TopicName / FrameID 불일치를 먼저 의심해야 한다.
- PhysX LiDAR는 장애물에 Collider/Physics 속성이 없으면 감지가 안 될 수 있다.
- Joint/Topic/Frame 이름은 작은 오타 하나로도 전체가 안 돌아가서 이름 관리가 중요했다.