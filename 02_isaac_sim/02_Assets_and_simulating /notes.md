# Isaac Sim/2 - Study Notes

## 느낀점
이번 챕터에서는 이미 존재하는 로봇 에셋을 가져와서(URDF → USD)
시뮬 환경에 올리고, 제어를 붙이고(차동 제어 + 키보드), 센서를 달아(카메라/LiDAR)
환경과 상호작용까지 확인하는 흐름을 경험했다.
설정 하나가 틀리면 로봇이 안 움직이거나 센서가 아무 것도 못 보는 상황이 생긴다는 걸 확실히 체감했다.

---

## 내가 확실히 익힌 것들
- URDF가 로봇의 설계도(XML)라는 것과, Isaac Sim에서는 이를 USD(OpenUSD)로 변환해 써야 한다는 흐름을 이해했다.
- URDF Importer에서 모바일 로봇(Carter)은 Fix Base Link를 끄고, 바퀴 조인트는 Velocity 제어로 설정해야 자연스럽게 움직인다.
- Carter의 관절 구조를 Stage에서 직접 확인하면서,
  - 구동 바퀴는 Y축 회전
  - 뒤 캐스터는 수동회전
  구조를 명확히 이해했다.
- OmniGraph의 Differential Controller를 적용해 W/A/S/D로 조종했고,
  Wheel Radius / Wheel Distance 파라미터가 정확해야 움직임이 잘 나온다는 걸 배웠다.
- 키보드 입력 기본 속도 명령이 너무 커서 시뮬이 불안정해질 수 있고,
  maxLinearSpeed / maxAngularSpeed 제한을 걸어야 부드럽고 현실적인 제어가 된다는 걸 확인했다.
- 센서는 URDF에 없을 수 있어서, Isaac Sim에서 직접 추가해야 하며  
  로봇의 `chassis_link` 아래로 붙여야 로봇과 함께 움직인다.
- Lidar가 감지하기 위해 장애물 메쉬는
  Rigid Body + Colliders를 붙여야 한다.
- 마지막으로 Nova Carter처럼 “사전 구성된 로봇 에셋”은  
  센서/물리/재질이 다 준비돼 있어서, 이후 SDG 같은 고급 작업에 바로 들어가기 좋다는 걸 이해했다.

---

## 꿀팁
- URDF Import 단계에서 바퀴 조인트 Target Type을 Velocity로 안 바꾸면 모바일 로봇 제어가 어색해진다.
- 장애물이 “보이는데” LiDAR가 안 찍히면 거의 항상 Collider/Physics 미설정 문제다.
- 키보드로 조종할 때 로봇이 튀거나 제어가 깨지면 maxLinearSpeed / maxAngularSpeed부터 낮춰서 안정화시키는 게 빠르다.