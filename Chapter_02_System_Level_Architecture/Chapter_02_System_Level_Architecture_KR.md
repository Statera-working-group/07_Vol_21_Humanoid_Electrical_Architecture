**Volume 21. Humanoid Electrical Architecture**

# Chapter 02. System Level Architecture

## 02.01. Body Block Diagram

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 신체 블록 다이어그램(Humanoid Body Block Diagram)은 로봇을 서로 독립적인 기계식 팔다리의 집합이 아니라, 상호 협조하는 전기 및 컴퓨팅 시스템(Electrical and Computational System)으로 표현한다. 시스템 수준(System Level)에서 몸통(Torso)은 일반적으로 아키텍처의 중심을 형성하며, 머리(Head), 양팔(Arms), 양손(Hands), 양다리(Legs), 전력 서브시스템(Power Subsystem), 안전 기능(Safety Functions), 컴퓨팅 자원(Computing Resources)을 연결한다. 이러한 구성은 전력, 제어, 통신 및 진단 경계를 정의하기 위한 명확한 기반을 제공한다.

몸통(Torso)은 배터리 인터페이스(Battery Interface), 전력 분배 장치(Power Distribution Unit), 중앙 컴퓨팅 하드웨어(Central Computing Hardware), 통신 스위치(Communication Switches), 안전 제어기(Safety Controller), 주요 와이어 하니스 접속부(Harness Junctions)를 수용할 수 있기 때문에 핵심 통합 영역(Primary Integration Zone)이 된다. 이러한 기능을 신체 중심 가까이에 배치하면 불필요한 케이블 길이를 줄이고 상체와 하체 말단부를 향한 비교적 균형 잡힌 배선을 구성하면서 모듈식 조립(Modular Assembly)과 정비 접근성(Service Access)을 지원할 수 있다.

최상위 수준에서 신체는 중앙 영역(Central Domain), 상체 전기 영역(Upper-Body Electrical Domain), 하체 전기 영역(Lower-Body Electrical Domain)으로 구분할 수 있다. 중앙 영역에는 시스템 관리(System Management)와 공통 인프라(Shared Infrastructure)가 포함되고, 상체 영역은 머리, 어깨, 팔, 손목 및 손을 연결한다. 하체 영역은 엉덩관절(Hip), 무릎(Knee), 발목(Ankle), 발(Foot)을 연결하며, 각 영역은 명령, 피드백, 전력, 동기화 및 상태 정보를 상호 교환한다.

머리 블록(Head Block)은 인지(Perception) 및 인간-로봇 상호작용(Human-Robot Interaction) 장치를 집중적으로 구성한다. 카메라(Camera), 라이다(LiDAR), 마이크 어레이(Microphone Array), 스피커(Speaker), 디스플레이(Display) 및 관련 인지 전자장치는 고대역폭 통신 링크(High-Bandwidth Communication Link)를 통해 중앙 컴퓨팅 시스템(Central Compute System)에 연결된다. 인지 데이터는 관절 제어 트래픽보다 훨씬 클 수 있으므로 머리 인터페이스는 고속 센서 스트림과 결정론적 제어(Deterministic Control), 진단 및 동기화 채널을 구분해야 한다.

각 팔(Arm)은 어깨(Shoulder), 상완(Upper Arm), 팔꿈치(Elbow), 손목(Wrist), 말단 작동기(End Effector) 블록으로 구성된 계층적 체인(Hierarchical Chain)으로 표현할 수 있다. 전력과 통신은 이 체인을 따라 분배되며, 로컬 관절 전자장치(Local Joint Electronics)는 모터를 구동하고 엔코더(Encoder)와 토크 센서(Torque Sensor)를 읽으며 상태 정보를 보고한다. 팔 아키텍처는 개별 관절 또는 전체 팔다리 조립체를 중앙 시스템의 재설계 없이 격리, 교체, 교정 및 진단할 수 있도록 모듈식 인터페이스(Modular Interface)를 유지해야 한다.

손(Hand)은 제한된 공간 안에서 다수의 소형 액추에이터(Actuator)와 센서를 동작시켜야 하므로 특히 높은 전기적 집적도를 갖는 말단부이다. 손가락 액추에이터(Finger Actuator), 마이크로 모터 드라이브(Micro-Motor Drive), 촉각 센서(Tactile Sensor), 힘 센서(Force Sensor), 로컬 제어 전자장치(Local Control Electronics)를 하나의 손 서브시스템(Hand Subsystem)으로 구성하여 손목을 통해 연결할 수 있다. 로컬 집계(Local Aggregation)는 팔을 통과해야 하는 개별 신호의 수를 줄이고 플렉스 하니스 인터페이스(Flex-Harness Interface)를 단순화한다.

각 다리(Leg)도 엉덩관절(Hip), 무릎(Knee), 발목(Ankle), 발(Foot) 블록을 중심으로 구성되지만, 전기 아키텍처는 높은 액추에이터 전력(Actuator Power), 균형 유지에 중요한 피드백(Balance-Critical Feedback), 신뢰성 높은 실시간 통신(Real-Time Communication)을 중점적으로 고려해야 한다. 관절 위치, 속도, 토크, 관성 정보 및 발 접촉 측정값은 보행 안정성(Locomotion Stability)에 직접적으로 기여한다. 따라서 다리 제어 경로의 단절은 즉각적인 시스템 수준의 안전 문제로 이어질 수 있다.

발 블록(Foot Block)은 휴머노이드와 지면 사이의 물리적 인터페이스(Physical Interface)를 제공하므로 관절 엔코더만으로는 신뢰성 있게 획득하기 어려운 정보를 제공한다. 힘(Force), 압력(Pressure), 접촉(Contact) 및 관련 센싱을 이용하여 하중 분포와 지지 상태를 파악할 수 있다. 이러한 측정값은 균형 및 보행 제어기(Balance and Locomotion Controller)로 전달되며, 관성 정보와 관절 상태 정보와 결합되어 로봇의 동적 상태(Dynamic State)를 추정하는 데 사용된다.

전력 분배(Power Distribution)는 전체 신체 블록 다이어그램에 걸쳐 병렬적인 구조를 형성한다. 배터리 시스템(Battery System)의 에너지는 보호 및 분배 단계를 거쳐 관절 드라이브(Joint Drive), 컴퓨터, 센서, 통신 장비 및 보조 부하(Auxiliary Load)에 공급된다. 아키텍처에는 서로 다른 전압 영역(Voltage Domain)과 DC-DC 변환 단계(DC-DC Conversion Stage)를 구성할 수 있으며, 이를 통해 고출력 액추에이터와 민감한 저전압 전자장치가 부적절한 전기적 특성을 공유하지 않고 함께 동작할 수 있다.

시스템 수준 신체 다이어그램(System-Level Body Diagram)에서는 전력 흐름(Power Flow)과 정보 흐름(Information Flow)이 물리적으로 인접한 하니스를 통과하더라도 개념적으로 명확히 분리해야 한다. 전력 경로는 전류, 전압 강하(Voltage Drop), 보호, 열 부하(Thermal Loading), 고장 격리(Fault Isolation)를 기준으로 설계되는 반면, 통신 경로는 대역폭, 지연시간(Latency), 결정성(Determinism), 전자파 적합성(Electromagnetic Compatibility), 토폴로지(Topology)를 중심으로 설계된다. 이러한 구분은 물리적인 하니스 배치가 기능 아키텍처를 불명확하게 만드는 것을 방지한다.

통신 링크(Communication Link)는 분산된 신체 모듈을 하나의 협조된 시스템으로 연결한다. 이더캣(EtherCAT)과 같은 결정론적 네트워크(Deterministic Network)는 정밀하게 동기화된 모션 제어를 지원할 수 있으며, CAN FD는 분산 제어와 진단 기능을 담당할 수 있고, 기가비트 이더넷(Gigabit Ethernet)은 고대역폭 인지 및 컴퓨팅 데이터를 전송할 수 있다. ROS 2와 DDS는 상위 소프트웨어 계층에서 동작하여 컴퓨팅 자원 간 애플리케이션 수준의 정보 교환을 가능하게 한다.

컴퓨팅 블록(Computing Block)은 타이밍 특성과 워크로드(Workload)의 특성에 따라 구분하는 것이 적합하다. 실시간 제어기(Real-Time Controller)는 결정론적인 서보(Servo), 균형 및 안전 관련 기능을 수행하고, AI 컴퓨터(AI Computer)와 GPU는 인지, 계획, 언어, 비전 및 체화 지능(Embodied Intelligence) 워크로드를 처리한다. 이러한 역할 분리는 가변적인 AI 실행 지연이 시간 결정적인 액추에이터 루프를 직접 제어하지 않도록 하면서도, 지능형 행동이 정의된 인터페이스를 통해 모션에 영향을 줄 수 있도록 한다.

시간 동기화(Time Synchronization)는 신체 아키텍처 전체를 연결하는 또 하나의 시스템 수준 기능이다. 카메라, 관성 센서(Inertial Sensor), 관절 제어기, 힘 센서 및 컴퓨팅 노드는 서로 다른 물리적 위치와 주기로 측정 데이터를 생성한다. 정밀 시간 프로토콜(PTP, Precision Time Protocol) 및 관련 동기화 메커니즘을 이용하여 공통 시간 기준(Common Time Reference)을 제공하면 센서 융합(Sensor Fusion), 상태 추정(State Estimation), 진단 및 이벤트 재구성(Event Reconstruction)을 위해 이러한 측정값을 정확하게 시간적으로 연계할 수 있다.

안전 아키텍처(Safety Architecture)는 하나의 주변 블록으로 존재하는 것이 아니라 정상 제어 계층(Normal Control Hierarchy) 전체에 중첩된다. 비상 정지 입력(Emergency-Stop Input), 충돌 감지(Collision Detection), 중복 센서(Redundant Sensor), 액추에이터 정지 메커니즘(Actuator Shutdown Mechanism), 안전 제어기 및 전력 차단 경로(Power Isolation Path)는 휴머노이드를 적절한 안전 상태(Safe State)로 전환할 수 있어야 한다. 따라서 안전 통신과 정지 권한(Shutdown Authority)은 중앙 컴퓨팅과 분산 관절 전자장치 모두에 대해 명확한 관계를 가져야 한다.

진단(Diagnostics)은 신체 전체에 걸쳐 구성되는 두 번째 감독 계층(Supervisory Layer)이다. 관절 모듈, 배터리, 전력 변환기(Power Converter), 센서, 네트워크 인터페이스 및 컴퓨터는 지속적으로 상태 정보(Health Information)를 생성하며, 이를 중앙 모니터링 기능(Central Monitoring Function)에서 통합할 수 있다. 이벤트 로깅(Event Logging), 원격 진단(Remote Diagnostics), 디지털 트윈(Digital Twin), 예지 정비(Predictive Maintenance) 데이터는 공통 시스템 모델을 활용함으로써 신체에서 관찰되는 고장 증상으로부터 실제 원인이 되는 전기 또는 소프트웨어 구성요소까지 추적할 수 있다.

하니스 아키텍처(Harness Architecture)는 논리적인 신체 블록을 실제 물리적 연결로 변환한다. 몸통 하니스(Torso Harness)는 중앙 분배 구조로 기능하고, 팔, 다리 및 머리 하니스는 움직이는 각 서브시스템으로 확장된다. 반복적인 굽힘, 비틀림, 관절 회전, 진동 및 정비 주기로 인해 휴머노이드에서는 유연한 배선(Flexible Routing)이 특히 중요하다. 따라서 커넥터 배치(Connector Placement)는 전기적 성능뿐 아니라 동작 범위, 기계적 보호, 조립 순서 및 정비성(Serviceability)을 함께 고려해야 한다.

모듈식 신체 블록 아키텍처(Modular Body Block Architecture)는 실질적인 교체 경계(Replacement Boundary)를 정의하는 역할도 한다. 어깨, 팔꿈치, 손목, 손, 엉덩관절, 무릎, 발목, 머리, 컴퓨팅 모듈 또는 전력 모듈은 전력, 네트워크, 동기화, 안전 및 진단 인터페이스가 표준화될 경우 교체 가능한 서브시스템(Replaceable Subsystem)으로 취급할 수 있다. 이러한 접근 방식은 시스템 아키텍처를 생산 시험(Production Test), 최종 라인 시험(End-of-Line Validation), 현장 서비스(Field Service), 예비 부품 관리(Spare-Parts Management), 수명주기 엔지니어링(Lifecycle Engineering)과 직접 연결한다.

따라서 최종적인 신체 아키텍처(Body Architecture)는 하나의 휴머노이드 구조 위에 여러 개의 네트워크가 중첩된 형태로 이해하는 것이 적절하다. 기계적 해부 구조(Mechanical Anatomy)는 물리적 영역을 정의하고, 전력 아키텍처(Power Architecture)는 에너지를 공급하며, 통신 아키텍처(Communication Architecture)는 정보를 전달하고, 컴퓨팅 아키텍처(Computing Architecture)는 지능과 제어 기능을 제공한다. 여기에 시간 동기화가 시간적 일관성(Temporal Consistency)을 형성하고 안전 및 진단 기능이 모든 계층을 감독함으로써, 분산된 신체 모듈들이 하나의 통합되고 협조된 전기기계 시스템(Electromechanical System)으로 동작하게 된다.

## 02.02. Control Hierarchy

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 제어 계층(Humanoid Control Hierarchy)은 상위 수준의 목표(High-Level Goal)에서 결정론적 액추에이터 명령(Deterministic Actuator Command)에 이르기까지 로봇의 행동을 체계적으로 구성하면서 타이밍(Timing), 안전(Safety), 책임 경계(Responsibility Boundary)를 명확하게 유지한다. 상위 계층은 로봇이 무엇을 수행해야 하는지를 결정하고, 중간 계층은 이러한 의도를 협조된 전신 동작(Whole-Body Motion)으로 변환하며, 하위 계층은 정밀한 관절 제어(Joint Control)를 실행한다. 이러한 계층 구조는 복잡한 AI 추론(AI Reasoning)이 시간 결정적인 모터 제어 루프(Motor Control Loop)에 직접 간섭하는 것을 방지한다.

가장 높은 제어 수준에서 작업 및 행동 관리(Task and Behavior Management)는 특정 위치까지 걷기, 물체 조작, 사람과의 상호작용 유지, 예상하지 못한 상황에서의 복구와 같은 목표를 해석한다. 이 수준의 명령은 개별 모터 값이 아니라 원하는 결과(Desired Outcome)를 표현한다. 따라서 행동 계층(Behavior Layer)은 의미론적 정보(Semantic Information), 환경 맥락(Environmental Context), 임무 상태(Mission State), 인지 및 안전 기능에서 제공되는 제약 조건(Constraint)을 기반으로 동작한다.

체화 AI(Embodied AI) 기능은 비전-언어 모델(Vision-Language Model), 비전-언어-행동 모델(Vision-Language-Action Model), 에이전트(Agent), 파운데이션 모델(Foundation Model)을 통해 이러한 상위 제어 계층에 기여할 수 있다. 이러한 구성요소는 장면, 명령, 물체, 인간의 의도를 해석하고 작업 수준 행동(Task-Level Action) 또는 행동 정책(Behavioral Policy)을 생성할 수 있다. 확률적 AI 의사결정(Probabilistic AI Decision)이 결정론적 모션 실행 및 안전 필수 제어(Safety-Critical Control)와 분리되도록 출력은 통제된 인터페이스(Controlled Interface)를 통과해야 한다.

작업 관리 계층 아래에서 모션 계획 계층(Motion Planning Layer)은 행동 목표를 물리적으로 실현 가능한 궤적(Physically Achievable Trajectory)으로 변환한다. 이 계층은 원하는 신체 자세, 보행 방향, 조작 목표, 장애물과의 관계, 도달 가능성(Reachability), 동작 제약을 고려한다. 모터를 직접 제어하는 대신 신체 위치와 방향, 말단 작동기(End Effector) 동작, 관절 구성 또는 보행 궤적에 대한 기준값(Reference)을 생성하여 하위 제어 계층이 이를 실행하도록 한다.

전신 제어(Whole-Body Control)는 휴머노이드의 많은 자유도(Degrees of Freedom)를 하나의 동역학적으로 결합된 시스템(Dynamically Coupled System)으로 조정한다. 팔의 움직임은 균형에 영향을 줄 수 있고, 몸통의 방향은 도달 가능성에 영향을 주며, 다리의 움직임은 신체 전체의 지지 상태를 변화시킨다. 따라서 제어기는 관절 한계, 접촉 제약(Contact Constraint), 안정성 요구사항, 액추에이터 성능 및 동시에 수행되는 작업의 우선순위를 고려하면서 몸통, 팔, 다리에 동작 목표를 분배한다.

보행 제어(Locomotion Control)는 이족 보행(Bipedal Motion)이 궤적 생성과 균형 안정화(Balance Stabilization)의 지속적인 협조를 요구하기 때문에 중요한 중간 위치를 차지한다. 원하는 보행 속도 또는 목적지는 발 배치(Foot Placement), 지지 전환(Support Transition), 질량 중심(Center of Mass) 거동 및 관절 기준값으로 변환된다. 발, 관절, 관성 센서(Inertial Sensor)의 피드백을 이용하여 실제 로봇이 계획된 움직임에서 벗어날 때 이러한 기준값을 조정할 수 있다.

균형 제어(Balance Control)는 일반적인 행동 계획보다 더욱 엄격한 타이밍 요구사항을 가진다. 관성 센서, 관절 엔코더(Joint Encoder), 토크 센서(Torque Sensor), 발의 힘 또는 접촉 센서(Contact Sensor)에서 획득한 측정값을 결합하여 신체 방향, 지지 상태 및 동적 움직임을 추정한다. 이후 보정 명령(Corrective Command)을 엉덩관절(Hip), 무릎(Knee), 발목(Ankle), 몸통(Torso), 필요에 따라 팔 제어기에 분배하여 서기, 걷기, 조작 또는 외부 교란 상황에서 안정성을 유지한다.

조작 제어(Manipulation Control)는 제어 계층의 또 다른 중간 분기를 형성한다. 물체를 잡는 것과 같은 작업은 물체 수준 목표(Object-Level Goal)에서 말단 작동기 궤적(End-Effector Trajectory), 팔 구성, 손목 자세, 최종적인 관절 명령으로 단계적으로 변환된다. 정교한 손 제어(Dexterous Hand Control)는 파지 동작을 손가락 위치, 접촉력(Contact Force), 로컬 액추에이터 명령으로 더욱 세분화할 수 있으며, 촉각 및 힘 피드백은 실제 물리적 상호작용에 관한 정보를 제공한다.

팔다리 수준(Limb Level)에서는 팔 및 다리 제어기가 하나의 공통 기계 서브시스템에 속하는 여러 관절을 협조 제어한다. 팔 제어기는 어깨, 팔꿈치, 손목의 움직임을 동기화할 수 있으며, 다리 제어기는 엉덩관절, 무릎, 발목의 동작을 조정한다. 이러한 구성은 전신 제어기에 전달되는 복잡성을 줄이고 서브시스템 진단, 교정(Calibration), 교체 및 독립적인 기능 시험을 위한 자연스러운 인터페이스를 제공한다.

관절 제어(Joint Control)는 물리적 움직임에 가장 가까운 분산 실시간 계층(Distributed Real-Time Layer)을 나타낸다. 각 관절 모듈(Joint Module)은 모터 드라이버(Motor Driver), 엔코더 인터페이스(Encoder Interface), 토크 센싱(Torque Sensing), 브레이크 제어(Brake Control), 로컬 진단(Local Diagnostics) 및 관련 제어 전자장치를 포함할 수 있다. 상위 계층에서 전달되는 위치, 속도 또는 토크 기준값은 모터 명령으로 변환되고 측정된 관절 상태는 피드백으로 반환되어 결정론적 실행 요구사항을 갖는 폐루프 제어(Closed Control Loop)를 형성한다.

가장 내부에 위치하는 모터 제어 루프(Motor-Control Loop)는 가장 짧은 제어 주기(Control Period)로 동작하며 가변적인 상위 수준 컴퓨팅 지연과 독립적으로 유지되어야 한다. 전류 또는 토크 제어(Current or Torque Regulation)는 일반적으로 모터 드라이브 가까이에서 실행되고, 위치 및 속도 루프는 로컬 또는 정밀하게 동기화된 실시간 제어기에서 구현할 수 있다. 이러한 근접 제어는 통신 지연을 줄이고 액추에이터가 외란, 부하 변화 및 명령 전환에 빠르게 대응할 수 있도록 한다.

따라서 제어 계층(Control Hierarchy)은 동시에 타이밍 계층(Timing Hierarchy)이기도 하다. AI 추론 및 작업 계획은 상대적으로 낮거나 가변적인 갱신 주기로 동작할 수 있지만, 모션 계획과 전신 제어는 더 빠른 주기적 실행을 요구하며, 서보 제어(Servo Control)는 매우 결정론적인 고속 동작을 필요로 한다. 이러한 서로 다른 시간적 요구사항을 중심으로 아키텍처를 설계하면 지연된 인지 또는 AI 프로세스가 모터 제어 루프를 불안정하게 만드는 것을 방지할 수 있다.

통신 아키텍처(Communication Architecture)는 네트워크 특성을 제어 요구사항에 맞춤으로써 이러한 제어 경계를 지원한다. 이더캣(EtherCAT)은 동기화된 액추에이터 및 모션 제어 기능을 위한 결정론적 통신을 제공할 수 있으며, CAN FD는 분산 제어 및 진단을 지원할 수 있다. 기가비트 이더넷(Gigabit Ethernet)은 대용량 인지 및 컴퓨팅 데이터를 전송하고, ROS 2와 DDS는 상위 수준 소프트웨어 구성요소와 분산 컴퓨팅 자원(Distributed Computing Resource)을 연결할 수 있다.

계층적 제어는 여러 분산 장치에서 생성되는 측정값에 의존하므로 시간 동기화(Time Synchronization)가 필수적이다. 관절 엔코더, 토크 센서, 카메라, 관성 센서, 발 센서 및 제어기는 데이터를 일관된 시간 기준(Consistent Temporal Reference)과 연계해야 한다. PTP 기반 동기화(PTP-Based Synchronization)는 센싱과 컴퓨팅 사이의 시간적 상관관계를 지원하여 분산 프로세서 전반에서 상태 추정(State Estimation), 센서 융합(Sensor Fusion), 이벤트 분석 및 협조 제어(Coordinated Control)의 정확도를 향상시킬 수 있다.

피드백(Feedback)은 계층을 따라 상향으로 흐르는 반면, 명령은 일반적으로 하향으로 전달된다. 관절 상태는 팔다리 상태(Limb State)로 통합되고, 팔다리 및 센서 정보는 전신 상태 추정(Whole-Body State Estimation)에 기여하며, 해석된 신체 및 환경 상태는 계획과 AI 추론을 지원한다. 이러한 양방향 구조(Bidirectional Structure)는 각 제어 수준이 자신의 추상화 수준과 타이밍 요구사항에 적합한 정보를 제공받는 지속적인 인지-행동 루프(Perception-Action Loop)를 형성한다.

안전 제어(Safety Control)는 일반적인 작업 실행에 종속되지 않고 제어 계층 전체에 대한 권한을 가져야 한다. 충돌 감지(Collision Detection), 비상 정지(Emergency Stop), 중복 센싱(Redundant Sensing), 안전 제어기(Safety Controller)는 위험한 상황이 발생하면 명령된 움직임을 제한하거나 무효화할 수 있다. 고장의 심각도에 따라 속도 또는 토크 제한부터 특정 관절 정지, 액추에이터 비활성화, 정의된 안전 메커니즘을 통한 전력 차단(Power Isolation)까지 다양한 대응이 가능하다.

제어 성능 저하(Control Degradation) 역시 휴머노이드에서 중요하다. 모든 고장이 반드시 동일한 대응을 요구하는 것은 아니기 때문이다. 중요도가 낮은 인지 기능의 손실은 제한된 운전을 허용할 수 있지만, 균형 유지에 필수적인 센싱이나 관절 통신의 손실은 즉각적인 안정화 또는 시스템 정지를 요구할 수 있다. 잘 정의된 제어 계층은 적절한 수준에 고장 대응(Fault Reaction)을 할당하여 시스템 수준의 안전성을 훼손하지 않는 범위에서 가능한 한 로컬 고장을 격리한다.

진단(Diagnostics)은 모든 제어 수준에서 제어 기능과 병렬로 동작한다. 로컬 관절 전자장치는 액추에이터 온도, 전류, 엔코더 상태, 통신 상태 및 기타 건전성 정보(Health Information)를 보고하며, 중앙 모니터링(Central Monitoring)은 이러한 관측값을 전체 시스템 거동과 연계한다. 이벤트 로깅(Event Logging)과 원격 진단(Remote Diagnostics)은 명령, 측정값, 경고 및 고장의 발생 순서를 보존하여 고장 재구성과 예지 정비(Predictive Maintenance)에 필요한 정보를 제공할 수 있다.

제어 계층은 컴퓨팅 자원 사이에서도 모듈성(Modularity)을 유지해야 한다. 실시간 제어 하드웨어(Real-Time Control Hardware)는 결정론적인 모션 및 안전 관련 실행을 담당하고, AI 컴퓨터와 GPU는 인지, 계획, 언어 및 체화 지능을 처리할 수 있다. 이러한 컴퓨팅 영역 사이에 정의된 인터페이스를 구성하면 어느 한쪽이 발전하더라도 전체 제어 시스템을 다시 설계할 필요가 없으며, 컴퓨팅 중복성(Compute Redundancy)을 통해 선택된 핵심 기능을 보호할 수도 있다.

궁극적으로 휴머노이드 제어 계층은 의도(Intention)에서 물리적인 힘(Physical Force)까지 이어지는 연속적인 제어 사슬(Control Chain)을 형성한다. 작업 지능(Task Intelligence)은 원하는 행동을 결정하고, 계획 계층은 행동을 실행 가능한 움직임으로 변환하며, 전신 및 팔다리 제어기는 기계 구조를 협조 제어한다. 관절 제어기는 정밀한 액추에이터 기준값을 생성하고 모터 드라이브는 실제 토크를 발생시킨다. 센서 피드백은 반대 방향으로 전달되어 각 계층이 원하는 행동과 변화하는 실제 물리 상태를 지속적으로 비교할 수 있도록 한다.

이러한 계층적 구성(Hierarchical Organization)은 휴머노이드를 독립적으로 제어되는 관절들의 집합에서 하나의 협조된 체화 시스템(Coordinated Embodied System)으로 전환한다. AI 수준의 지능, 모션 계획, 실시간 제어, 분산 액추에이션(Distributed Actuation), 동기화된 센싱(Synchronized Sensing), 안전 감독(Safety Supervision), 진단을 하나의 컴퓨터에 집중하지 않고 체계적으로 결합한다. 그 결과 관절 수와 컴퓨팅 복잡성이 증가하더라도 결정론적 제어와 모듈식 엔지니어링 경계(Modular Engineering Boundary)를 유지하면서 확장할 수 있는 아키텍처가 형성된다.

## 02.03. AI Compute Hierarchy

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 AI 컴퓨팅 계층(Humanoid AI Compute Hierarchy)은 지연시간(Latency), 결정성(Determinism), 대역폭(Bandwidth), 안전 중요도(Safety Criticality), 모델 복잡도(Model Complexity)에 따라 컴퓨팅 책임을 분리한다. 모든 기능을 하나의 프로세서에서 실행하는 대신 관절 전자장치(Joint Electronics), 실시간 제어기(Real-Time Controller), 인지 컴퓨터(Perception Computer), AI 가속기(AI Accelerator), 상위 수준 컴퓨팅 자원에 워크로드를 분산한다. 이러한 분리는 지능형 행동과 안정적이고 예측 가능한 물리 제어가 공존할 수 있도록 한다.

가장 낮은 컴퓨팅 수준에서 관절 모듈(Joint Module)의 내부 또는 가까이에 위치한 임베디드 프로세서(Embedded Processor)는 액추에이터와 근접하여 유지되어야 하는 기능을 실행한다. 이러한 프로세서는 엔코더(Encoder)와 토크 측정값을 획득하고, 모터 드라이버(Motor Driver) 상태를 감시하며, 로컬 제어 루프(Local Control Loop)를 실행하고 기본적인 진단을 수행할 수 있다. 컴퓨팅 워크로드는 비교적 제한적이지만 대규모 AI 처리 능력보다 예측 가능한 타이밍과 신뢰성 높은 통신이 더욱 중요하다.

관절 수준 위에서는 분산 실시간 제어기(Distributed Real-Time Controller)가 팔, 다리, 손 또는 기타 신체 영역에 속하는 액추에이터 그룹을 협조 제어한다. 상위 계층으로부터 모션 기준값(Motion Reference)을 수신하고 이를 동기화된 관절 명령으로 변환하면서 여러 로컬 장치의 피드백을 수집한다. 이 계층은 물리적 액추에이션(Physical Actuation)과 컴퓨팅 집약적인 인지, 계획 및 AI 기능 사이에 결정론적 경계(Deterministic Boundary)를 제공한다.

중앙 실시간 컴퓨팅 계층(Central Real-Time Computing Layer)은 전신 동작(Whole-Body Motion), 균형(Balance), 보행(Locomotion), 조작(Manipulation), 안전 관련 상태 관리(Safety-Related State Management)를 조정할 수 있다. 관절 상태, 관성 측정값, 힘 정보 및 기타 시간 민감 신호(Time-Sensitive Signal)를 결합하여 휴머노이드의 물리적 상태를 추정한다. 불안정 상태는 빠르게 발생할 수 있으므로 이러한 워크로드에는 제한된 실행 시간(Bounded Execution Time)이 요구되며, 가변 지연시간을 갖는 AI 추론에 의존해서는 안 된다.

인지 컴퓨팅 계층(Perception Computing Layer)은 주로 머리와 신체에 배치된 카메라(Camera), 라이다(LiDAR), 마이크(Microphone) 및 기타 환경 센서에서 생성되는 고대역폭 센서 스트림(High-Bandwidth Sensor Stream)을 처리한다. 영상 처리, 포인트 클라우드 처리(Point-Cloud Processing), 오디오 처리, 객체 감지(Object Detection), 추적(Tracking), 깊이 추정(Depth Estimation), 센서 융합(Sensor Fusion)을 이 계층에서 수행할 수 있다. 인지 워크로드는 일반적인 임베디드 제어보다 훨씬 높은 처리량을 요구하는 경우가 많으므로 전용 가속기(Dedicated Acceleration)를 사용할 수 있다.

GPU 기반 AI 컴퓨팅(GPU-Based AI Computing)은 계층 내에서 더욱 높은 성능을 담당한다. GPU는 시각 인지(Visual Perception), 멀티모달 이해(Multimodal Understanding), 의미론적 매핑(Semantic Mapping), 자세 추정(Pose Estimation), 학습 기반 조작(Learned Manipulation) 및 기타 데이터 집약적 워크로드를 위한 심층 신경망(Deep Neural Network)을 실행할 수 있다. 결정론적 서보 제어기와 달리 이 계층은 병렬 수치 연산과 모델 추론(Model Inference)에 최적화되어 있어 실시간 제어를 위해 확보된 자원을 소비하지 않으면서 대규모 학습 모델을 실행할 수 있다.

AI 컴퓨터(AI Computer)는 체화 지능(Embodied Intelligence)에 사용되는 비전-언어 모델(VLM, Vision-Language Model), 비전-언어-행동 모델(VLA, Vision-Language-Action Model), 에이전트(Agent), 파운데이션 모델(Foundation Model) 구성요소를 실행할 수 있다. 이러한 모델은 인간의 명령을 해석하고, 시각적 관측을 의미론적 개념과 연결하며, 작업을 추론하고 행동을 제안할 수 있다. 그 출력은 목표, 계획 또는 정책(Policy)을 나타내며 일반적으로 액추에이터의 전류나 토크를 직접 명령하지 않고 검증된 모션 및 제어 계층으로 전달되어야 한다.

이러한 분리는 의미론적 지능(Semantic Intelligence)과 물리적 실행(Physical Execution) 사이에 중요한 경계를 형성한다. AI 컴퓨팅은 어떤 물체를 조작해야 하는지, 로봇이 어디로 이동해야 하는지 또는 다음에 어떤 작업을 수행해야 하는지와 같은 문제를 판단한다. 실시간 컴퓨팅은 이러한 의도를 균형, 관절 한계(Joint Limit), 접촉 조건(Contact Condition), 액추에이터 성능 및 안전 제약(Safety Constraint)을 준수하면서 어떻게 실행할 것인지를 결정한다.

중간 계획 컴퓨터(Intermediate Planning Computer)는 AI가 생성한 목표를 구조화된 로봇 행동(Structured Robot Action)으로 변환하여 두 영역을 연결한다. 모션 계획기(Motion Planner)는 충돌이 없는 궤적(Collision-Free Trajectory), 조작 순서, 파지 자세(Grasp Pose), 발 배치(Foot Placement), 전신 구성을 계산할 수 있다. 생성된 기준값은 의미론적 AI 출력보다 물리적 제약을 더 많이 반영하지만 결정론적 서보 계층보다는 상위에 위치하여 추론에서 움직임으로 이어지는 통제된 전환을 형성한다.

이 계층 구조는 데이터 표현(Data Representation)의 차이도 반영한다. 관절 제어기는 주로 전류, 토크, 위치, 속도와 같은 간결한 수치 신호를 처리한다. 전신 제어기는 상태, 자세, 힘, 접촉 및 궤적을 처리한다. 인지 및 AI 컴퓨터는 이미지, 포인트 클라우드(Point Cloud), 오디오, 특징 임베딩(Feature Embedding), 언어 토큰(Language Token), 의미론적 지도(Semantic Map), 학습된 표현(Learned Representation)을 처리하므로 AI 계층으로 올라갈수록 대역폭과 메모리 요구사항이 크게 증가한다.

따라서 통신 네트워크(Communication Network)는 각 컴퓨팅 계층(Compute Tier)의 특성에 맞게 구성해야 한다. 이더캣(EtherCAT)은 실시간 제어기와 액추에이터 모듈 사이의 결정론적 데이터 교환을 지원할 수 있고, CAN FD는 분산 제어 및 진단 통신을 제공할 수 있다. 기가비트 이더넷(Gigabit Ethernet)은 대용량 센서 및 컴퓨팅 트래픽을 전달할 수 있으며, ROS 2와 DDS는 이기종 프로세서(Heterogeneous Processor) 전반의 소프트웨어 구성요소를 연결하면서 컴퓨팅 영역 사이에 정의된 인터페이스를 유지할 수 있다.

시간 동기화(Time Synchronization)는 서로 독립적인 컴퓨팅 계층을 일관된 하나의 물리 시스템으로 연결한다. 센서 프레임, IMU 측정값, 관절 상태, 토크 값 및 제어 이벤트는 정확하게 융합되기 전에 일관된 타임스탬프(Consistent Timestamp)와 연계되어야 한다. PTP 기반 동기화(PTP-Based Synchronization)는 네트워크로 연결된 프로세서에 공통 시간 기준(Common Time Reference)을 분배하여 정확한 상태 추정(State Estimation), 인지 융합(Perception Fusion), 이벤트 재구성(Event Reconstruction), 협조 실행(Coordinated Execution)을 지원할 수 있다.

컴퓨팅 계층의 상위로 이동할수록 메모리 아키텍처(Memory Architecture)의 중요성도 증가한다. 임베디드 제어기는 상대적으로 작은 결정론적 작업 메모리(Deterministic Working Memory)를 요구하지만, 인지 파이프라인(Perception Pipeline)은 연속적인 센서 스트림을 위한 버퍼(Buffer)를 필요로 한다. GPU 및 파운데이션 모델 워크로드는 모델 파라미터(Model Parameter), 중간 활성값(Intermediate Activation), 컨텍스트(Context), 지도(Map), 멀티모달 데이터를 위해 훨씬 큰 메모리 용량을 요구하므로 메모리 대역폭과 데이터 이동이 주요 아키텍처 설계 요소가 된다.

컴퓨팅 계층은 불필요한 대용량 데이터 이동을 최소화해야 한다. 원시 카메라 또는 라이다 스트림은 인지 컴퓨터 가까이에서 처리하고, 필요한 경우 압축된 특징(Compact Feature), 객체, 지도 또는 상태 추정값을 다른 계층으로 전달할 수 있다. 마찬가지로 고주파 모터 피드백(High-Frequency Motor Feedback)은 상위 계층에서 필요하지 않은 경우 결정론적 제어 영역 내부에 유지하여 네트워크 혼잡(Network Congestion)을 줄이고 중앙 프로세서가 데이터 병목(Data Bottleneck)이 되는 것을 방지해야 한다.

안전 기능(Safety Function)은 AI 워크로드가 실패하거나 정지하거나 잘못된 결과를 생성하더라도 계속 유효하게 동작할 수 있는 컴퓨팅 경로를 필요로 한다. 따라서 비상 정지(Emergency Stop) 처리, 중요한 충돌 대응(Collision Response), 액추에이터 정지(Actuator Shutdown), 일부 안정화 기능(Stabilization Function)은 신뢰할 수 있는 실시간 컴퓨팅 영역 또는 전용 안전 컴퓨팅 영역(Dedicated Safety Computing Domain)에 유지되어야 한다. AI 계층은 유용한 상황 정보를 제공할 수 있지만 즉각적인 안전 필수 대응의 유일한 결정 권한이 되어서는 안 된다.

컴퓨팅 중복성(Compute Redundancy)은 손실될 경우 제어된 운전(Controlled Operation)을 유지할 수 없게 되는 기능을 보호할 수 있다. 중복 제어기(Redundant Controller), 상태 모니터링(Health Monitoring), 워치독 메커니즘(Watchdog Mechanism), 장애 전환 로직(Failover Logic), 독립 통신 경로를 시스템 중요도에 따라 적용할 수 있다. 모든 AI 가속기를 반드시 이중화할 필요는 없으며, 특정 프로세서 또는 통신 고장이 발생하더라도 어떤 제어, 인지, 상태 추정 또는 안전 기능이 유지되어야 하는지를 식별하는 것이 중요하다.

진단(Diagnostics)은 모든 컴퓨팅 수준에 걸쳐 동작하며 프로세서 부하, 메모리 사용량, 온도, 통신 상태, 타이밍 위반(Timing Violation), 가속기 사용률(Accelerator Utilization), 소프트웨어 고장, 센서 처리 상태에 대한 가시성을 제공한다. 중앙 상태 모니터링(Central Health Monitoring)은 이러한 관측값을 로봇의 동작과 연계할 수 있고, 이벤트 로깅(Event Logging)은 고장과 제어 대응의 발생 순서를 보존한다. 이러한 정보는 원격 진단(Remote Diagnostics), 디지털 트윈(Digital Twin), 예지 정비(Predictive Maintenance)를 지원한다.

고성능 AI 프로세서와 GPU는 상당한 전력을 소비할 수 있으므로 열 설계(Thermal Design)와 전기 설계(Electrical Design)는 컴퓨팅 계층과 밀접하게 연관된다. 실시간 임베디드 제어기는 일반적으로 비교적 적은 전력을 요구하지만 인지 및 AI 가속기는 훨씬 큰 전력과 냉각 용량을 요구할 수 있다. 따라서 휴머노이드 전체에 워크로드를 할당할 때 전력 분배(Power Distribution), DC-DC 변환(DC-DC Conversion), 열 모니터링(Thermal Monitoring), 컴퓨팅 스케줄링(Compute Scheduling)을 함께 고려해야 한다.

엣지-클라우드 통합(Edge-Cloud Integration)은 컴퓨팅 계층을 실제 로봇의 외부까지 확장한다. 온보드 컴퓨팅(Onboard Computing)은 즉각적인 인지, 제어, 안전 및 자율 운전에 필요한 기능을 유지해야 하며, 원격 서버 또는 클라우드 자원은 플릿 분석(Fleet Analytics), 모델 관리(Model Management), 대규모 학습, 데이터 처리, 디지털 트윈 서비스 및 일부 비실시간 추론을 지원할 수 있다. 네트워크 연결이 손실되더라도 로봇의 필수적인 안전 유지 능력이 사라져서는 안 된다.

소프트웨어 아키텍처(Software Architecture)는 하드웨어에서 설정한 것과 동일한 경계를 유지해야 한다. 실시간 제어 작업, 인지 파이프라인, AI 추론 서비스(AI Inference Service), 계획 모듈, 진단 및 클라우드 인터페이스는 숨겨진 의존 관계(Hidden Dependency)가 아니라 명시적인 API와 메시지 정의(Message Definition)를 통해 통신해야 한다. 이러한 모듈식 접근 방식은 안정적인 시스템 인터페이스를 유지하면서 GPU 플랫폼, AI 모델, 실시간 제어기 또는 통신 기술을 서로 독립적으로 발전시킬 수 있도록 한다.

휴머노이드의 지능이 발전함에 따라 AI 컴퓨팅 계층은 단순히 규모가 커지는 것보다 더욱 이기종화(Heterogeneous)될 가능성이 높다. CPU, GPU, 신경망 가속기(Neural Accelerator), 마이크로컨트롤러(Microcontroller), 안전 프로세서(Safety Processor), 전용 센서 처리 장치는 각각의 특성에 적합한 워크로드를 실행할 수 있다. 엔지니어링의 목표는 모든 수준에서 최대 컴퓨팅 성능을 확보하는 것이 아니라 각 워크로드를 타이밍, 전력, 메모리, 대역폭, 신뢰성 및 안전 요구사항을 만족할 수 있는 적절한 위치에 배치하는 것이다.

궁극적으로 휴머노이드 AI 컴퓨팅 계층은 물리적 상호작용(Physical Interaction)에서 의미론적 지능(Semantic Intelligence)으로 이어지는 단계적 구조를 형성한다. 임베디드 프로세서는 액추에이터를 제어하고, 실시간 컴퓨터는 신체를 협조 제어하며, 인지 컴퓨터는 센서 스트림을 환경 표현(Environmental Representation)으로 변환한다. AI 가속기는 이러한 표현을 해석하고 체화 AI 시스템은 목표와 행동을 생성한다. 통신, 동기화, 안전, 진단, 중복성 및 엣지-클라우드 통합이 이러한 계층을 연결함으로써 하나의 확장 가능한 컴퓨팅 아키텍처(Scalable Computing Architecture)를 형성한다.

## 02.04. Data Flow Architecture

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 데이터 흐름 아키텍처(Humanoid Data Flow Architecture)는 분산된 센서와 액추에이터에서 생성되는 정보가 실시간 제어(Real-Time Control), 인지(Perception), AI 컴퓨팅(AI Computing), 진단(Diagnostics), 외부 시스템(External System)을 거쳐 어떻게 이동하는지를 정의한다. 이 아키텍처는 대용량 인지 데이터가 결정론적 모션 제어(Deterministic Motion Control)를 방해하지 않으면서 서로 매우 다른 특성을 가진 트래픽을 지원해야 한다. 따라서 데이터 경로는 대역폭(Bandwidth), 지연시간(Latency), 타이밍(Timing), 신뢰성(Reliability), 안전 요구사항(Safety Requirement)에 따라 구성된다.

시스템의 물리적 말단(Physical Edge)에서는 관절 엔코더(Joint Encoder), 토크 센서(Torque Sensor), 발 센서(Foot Sensor), 촉각 센서(Tactile Sensor), 관성 측정 장치(IMU), 카메라(Camera), 라이다(LiDAR), 마이크(Microphone), 배터리 모니터(Battery Monitor), 열 센서(Thermal Sensor)가 지속적으로 원시 측정 데이터(Raw Measurement)를 생성한다. 이러한 데이터 소스는 데이터 생성 속도와 형식에서 큰 차이를 가진다. 관절 피드백은 주로 간결한 수치 값으로 구성되는 반면, 카메라와 라이다는 훨씬 높은 대역폭과 처리 능력을 요구하는 대용량 데이터 스트림을 생성한다.

액추에이터 데이터(Actuator Data)는 긴밀하게 결합된 양방향 흐름(Bidirectional Flow)을 형성한다. 상위 제어 계층은 위치, 속도, 토크 또는 전류 기준값(Current Reference)을 관절 모듈로 전송하고, 모터 드라이버(Motor Driver)와 로컬 제어기(Local Controller)는 측정된 위치, 속도, 토크, 전류, 온도, 고장 상태 및 동작 상태를 반환한다. 이러한 신호는 물리적 안정성과 움직임에 직접적인 영향을 주므로 해당 통신 경로에는 예측 가능한 지연시간과 결정론적인 갱신 동작(Deterministic Update Behavior)이 요구된다.

로컬 관절 전자장치(Local Joint Electronics)는 데이터 축소(Data Reduction)와 검증(Validation)의 첫 번째 단계를 수행한다. 원시 엔코더 측정값, 모터 전류, 토크 신호 및 장치 상태를 전송하기 전에 필터링하고, 검사하고, 타임스탬프(Timestamp)를 부여하며, 표준화된 관절 상태 정보(Standardized Joint-State Information)로 변환할 수 있다. 고주파 처리를 액추에이터 가까이에 유지하면 불필요한 네트워크 트래픽을 줄이고 로컬 제어 루프가 가변 지연시간을 갖는 중앙 컴퓨팅에 의존하지 않고 지속적으로 동작할 수 있다.

분산 팔다리 제어기(Distributed Limb Controller)는 팔, 다리 또는 손 내부의 여러 관절에서 발생하는 데이터를 통합한다. 개별 관절 상태는 구성(Configuration), 움직임, 하중 및 건전성(Health)을 나타내는 팔다리 수준 정보(Limb-Level Information)로 변환할 수 있다. 명령은 반대 방향으로 전달되며 팔다리 기준값(Limb Reference)이 동기화된 관절 명령으로 분해된다. 이러한 데이터 통합은 다수의 분산 액추에이터와 중앙 전신 제어(Central Whole-Body Control) 사이에 확장 가능한 인터페이스를 형성한다.

중앙 실시간 제어 영역(Central Real-Time Control Domain)은 동기화된 관절, IMU, 힘 및 접촉 정보를 수신하여 휴머노이드의 물리적 상태를 지속적으로 갱신하여 추정한다. 전신 제어(Whole-Body Control), 균형(Balance), 보행(Locomotion), 조작(Manipulation) 기능은 이 상태 정보를 이용하여 새로운 모션 기준값(Motion Reference)을 생성한다. 지연되거나 일관되지 않은 상태 정보는 안정성과 제어 성능을 직접 저하시킬 수 있으므로 이러한 데이터 루프(Data Loop)는 결정론적 특성을 유지해야 한다.

인지 데이터(Perception Data)는 카메라, 라이다, 마이크 및 관련 센서가 훨씬 큰 데이터셋을 생성하기 때문에 서로 다른 경로를 따른다. 원시 데이터 스트림은 일반적으로 전용 인지 컴퓨팅 자원(Dedicated Perception Computing Resource)으로 전달되며, 여기에서 영상 처리, 포인트 클라우드 처리(Point-Cloud Processing), 오디오 분석, 객체 감지(Object Detection), 추적(Tracking), 깊이 추정(Depth Estimation), 센서 융합(Sensor Fusion)이 수행된다. 이후 모든 원시 센서 데이터를 반복적으로 배포하는 대신 처리된 표현(Processed Representation)을 전달할 수 있다.

인지 계층(Perception Layer)은 센서 중심 데이터(Sensor-Centric Data)를 환경 중심 정보(Environment-Centric Information)로 변환한다. 픽셀(Pixel), 깊이 값, 포인트 클라우드(Point Cloud), 오디오 샘플(Audio Sample)은 객체, 자세(Pose), 장애물, 사람, 의미론적 레이블(Semantic Label), 공간 지도(Spatial Map) 및 기타 구조화된 표현(Structured Representation)으로 변환된다. 이러한 변환은 상위 추론 계층이 해석해야 하는 정보량을 줄이고 AI 및 계획 기능에 더욱 유용한 추상화 수준의 데이터를 제공한다.

AI 컴퓨팅(AI Computing)은 인지 출력과 함께 로봇 상태, 작업 맥락(Task Context), 인간의 명령 및 저장된 지식을 입력으로 사용한다. 비전-언어 모델(VLM, Vision-Language Model), 비전-언어-행동 모델(VLA, Vision-Language-Action Model), 에이전트(Agent), 파운데이션 모델(Foundation Model)은 이러한 입력을 이용하여 의미론적 관계(Semantic Relationship)를 추론하고 목표, 계획 또는 정책(Policy)을 제안할 수 있다. 이러한 출력은 모터 드라이브 명령으로 직접 변환되지 않고 정의된 인터페이스를 통해 계획 및 제어 계층으로 하향 전달된다.

하향 명령 경로(Downward Command Path)를 따라 데이터의 추상화 수준은 점진적으로 변화한다. 인간의 명령은 먼저 작업 목표(Task Objective)가 되고, 이후 행동 계획(Behavioral Plan), 모션 궤적(Motion Trajectory), 전신 기준값(Whole-Body Reference), 팔다리 명령(Limb Command), 관절 기준값(Joint Reference), 최종적으로 모터 제어 값(Motor-Control Value)으로 변환될 수 있다. 각 단계에서 물리적 제약 조건이 추가되고 모호성이 제거되어 상위 수준의 의미론적 의도가 분산 액추에이터에서 안전하게 실행 가능한 결정론적 명령으로 변환된다.

상향 피드백 경로(Upward Feedback Path)는 이와 상호 보완적인 변환을 수행한다. 전기적 측정값과 관절 상태는 팔다리 상태, 신체 상태(Body State), 접촉 추정(Contact Estimate), 건전성 정보로 변환된다. 인지 스트림은 환경 표현(Environmental Representation)으로 변환되고, 진단 관측값은 시스템 건전성 상태(System-Health State)로 변환된다. 따라서 상위 계층은 로봇 전체에서 생성되는 모든 저수준 전기 신호를 직접 처리하지 않고 의사결정에 적합하게 요약된 정보를 수신한다.

서로 다른 통신 기술(Communication Technology)을 사용하여 이러한 다양한 데이터 흐름을 지원할 수 있다. 이더캣(EtherCAT)은 결정론적 액추에이터 및 동기화 트래픽을 전달할 수 있고, CAN FD는 분산 제어 및 진단 메시지를 지원할 수 있다. 기가비트 이더넷(Gigabit Ethernet)은 고대역폭 인지 및 컴퓨팅 데이터를 전송할 수 있으며, ROS 2와 DDS는 이기종 컴퓨팅 자원(Heterogeneous Computing Resource)에 분산된 상위 수준 소프트웨어 구성요소 사이에서 구조화된 메시지를 교환할 수 있다.

시간 정보(Time Information)는 아키텍처 전체에서 데이터와 함께 전달되어야 한다. 카메라, IMU, 관절 엔코더, 토크 센서, 발 센서의 측정값은 획득 시점이 일관되게 파악되어야만 정확하게 융합할 수 있다. PTP 기반 시간 동기화(PTP-Based Time Synchronization)는 공통 시간 기준(Common Temporal Reference)을 분배할 수 있으며, 물리적으로 분리된 프로세서와 네트워크에서 생성된 센서 프레임, 제어 이벤트 및 계산된 상태를 시간적으로 정확하게 연계할 수 있도록 한다.

데이터 생성자(Producer)와 소비자(Consumer)가 서로 다른 속도로 동작할 때는 데이터 버퍼링(Data Buffering)이 필요하다. 고속 카메라는 AI 모델이 처리하는 속도보다 빠르게 프레임을 생성할 수 있으며, 하나의 계획 갱신(Planning Update)이 이루어지는 동안 관절 제어기는 여러 제어 주기를 실행할 수 있다. 버퍼(Buffer), 큐(Queue), 속도 변환(Rate Conversion), 제어된 샘플링(Controlled Sampling)을 이용하면 모든 서브시스템을 동일한 주파수로 동작시키지 않고도 서로 연계할 수 있지만, 지연시간이 중요한 영역에서는 과도한 버퍼링을 방지해야 한다.

데이터 우선순위화(Data Prioritization)는 중요도가 낮은 트래픽이 물리적 제어 성능을 저하시키는 것을 방지한다. 서보 명령(Servo Command), 균형 관련 피드백, 동기화 정보 및 안전 메시지는 지도 업로드(Map Upload), 진단 이력, 모델 파일 또는 일반 텔레메트리(General Telemetry)보다 높은 수준의 타이밍 보장을 요구한다. 따라서 네트워크 분할(Network Segmentation), 트래픽 클래스(Traffic Class), 스케줄링(Scheduling), 대역폭 할당(Bandwidth Allocation)을 통해 대규모 인지 및 AI 워크로드를 처리하면서도 결정론적 경로를 유지할 수 있다.

안전 데이터(Safety Data)는 일반적인 명령 계층 전반에 걸쳐 독립적인 감독 흐름(Supervisory Flow)을 형성한다. 비상 정지(Emergency Stop) 상태, 충돌 정보, 중복 센서 결과, 액추에이터 고장, 안전 제어기(Safety Controller)의 결정은 제한된 지연시간 내에 적절한 제어 및 전력 기능에 전달되어야 한다. 안전 명령은 일반적인 모션 데이터를 무효화하거나 토크 또는 속도를 제한하고, 특정 액추에이터를 비활성화하거나 시스템이 위험 상태에 진입할 경우 전력 차단(Power Isolation)을 수행할 수 있다.

진단 데이터(Diagnostic Data)는 로컬과 중앙 시스템 사이에서 모두 이동한다. 관절 모듈, 모터 드라이버, 센서, 네트워크 인터페이스, 배터리, 컴퓨터 및 전력 전자장치(Power Electronics)는 온도, 전류, 전압, 통신 오류, 타이밍 위반(Timing Violation), 소프트웨어 이벤트 및 고장 코드(Fault Code)를 생성한다. 중앙 건전성 모니터링(Central Health Monitoring)은 이러한 관측값을 로봇 동작과 연계할 수 있으며, 이벤트 로깅(Event Logging)은 문제 해결과 고장 재구성(Failure Reconstruction)을 위해 과거 정보를 보존한다.

동일한 진단 데이터 흐름은 원격 진단(Remote Diagnostics), 디지털 트윈(Digital Twin), 예지 정비(Predictive Maintenance)를 지원할 수 있다. 모든 원시 신호를 지속적으로 전송하는 대신 로봇은 건전성 지표(Health Indicator), 이벤트, 통계 및 선택된 시계열 데이터(Time-Series Data)를 통합하여 전달할 수 있다. 이러한 방식은 성능 저하 추세를 파악하고 실제 동작을 디지털 모델과 비교하며 기능적 고장이 발생하기 전에 정비를 계획하는 데 필요한 정보를 유지하면서 외부 통신 대역폭을 줄인다.

여러 프로세서가 서로 관련된 정보를 필요로 할 수 있으므로 데이터 소유권(Data Ownership)과 인터페이스 정의(Interface Definition)가 중요하다. 이상적으로 각각의 중요한 상태 정보는 하나의 권한 있는 소스(Authoritative Source)에서 생성하고 다른 모듈은 정의된 메시지 또는 API를 통해 이를 사용해야 한다. 명확한 데이터 소유권은 서로 충돌하는 상태 추정과 숨겨진 의존 관계(Hidden Dependency)를 방지하며, 표준화된 인터페이스는 전체 시스템을 다시 설계하지 않고도 관절 모듈, 인지 컴퓨터, AI 가속기 또는 제어 프로세서를 교체할 수 있도록 한다.

엣지-클라우드 통신(Edge-Cloud Communication)은 선택된 데이터 흐름을 휴머노이드 외부로 확장한다. 온보드 시스템(Onboard System)은 플릿 텔레메트리(Fleet Telemetry), 진단 요약, 선택된 센서 기록, 지도 및 운용 통계를 원격 인프라로 전송할 수 있다. 클라우드 또는 서버 자원은 모델 업데이트(Model Update), 임무 정보, 구성 데이터(Configuration Data), 비실시간 분석 결과를 반환할 수 있다. 이러한 외부 연결을 사용할 수 없는 상황에서도 즉각적인 모션, 균형 및 안전 제어는 계속 동작해야 한다.

사이버보안(Cybersecurity)과 무결성 메커니즘(Integrity Mechanism)은 데이터가 컴퓨팅 및 네트워크 경계를 통과할 때 이를 보호해야 한다. 제어 명령, 소프트웨어 업데이트, 구성 파라미터(Configuration Parameter), 진단 접근 및 원격 인터페이스는 일반적인 센서 트래픽과 구분하고 시스템에 미칠 수 있는 영향에 따라 처리해야 한다. 인증(Authentication), 권한 부여(Authorization), 무결성 검사(Integrity Checking), 통제된 인터페이스를 통해 손상되거나 승인되지 않은 정보가 물리적 제어 영역으로 전파되는 것을 방지할 수 있다.

아키텍처는 정보의 가치와 보존 기간에 따라 저장장치(Storage)도 관리해야 한다. 고속 원시 센서 스트림은 일시적으로만 보존할 수 있지만 안전 이벤트, 진단 로그, 교정 파라미터(Calibration Parameter), 소프트웨어 버전 및 중요한 운용 기록은 장기간 보존해야 할 수 있다. 선택적 기록(Selective Recording)은 저장공간 요구량을 줄이면서 중요한 이벤트를 이후 엔지니어링 분석, 검증, 정비 또는 수명주기 관리(Lifecycle Management)를 위해 재구성할 수 있도록 한다.

궁극적으로 휴머노이드 데이터 흐름(Humanoid Data Flow)은 하나의 네트워크 스트림이 아니라 상향, 하향, 수평 및 외부 방향으로 구성된 협조된 정보 경로의 집합이다. 센서 피드백(Sensor Feedback)은 상향으로 이동하고 명령(Command)은 하향으로 전달되며, 동급 제어기(Peer Controller)는 동기화된 상태를 수평 방향으로 교환하고 선택된 운용 데이터는 엣지 또는 클라우드 자원으로 전달된다. 통신, 타이밍, 안전, 진단, 버퍼링, 우선순위화 및 인터페이스 관리를 통해 결정성을 잃지 않으면서 이러한 데이터 흐름이 동시에 공존할 수 있다.

잘 구성된 데이터 흐름 아키텍처(Data Flow Architecture)는 물리적 센싱(Physical Sensing), 분산 액추에이션(Distributed Actuation), 실시간 제어, 인지, AI 추론(AI Reasoning), 진단 및 원격 컴퓨팅(Remote Computing)을 하나의 연속적인 정보 시스템(Information System)으로 연결한다. 각 데이터 클래스(Data Class)를 적절한 처리, 통신, 동기화 및 신뢰성 메커니즘에 대응시킴으로써 휴머노이드는 원시 물리 측정값을 지능적인 의사결정으로 변환하고, 이러한 결정을 다시 안전하고 협조된 물리적 행동으로 변환할 수 있다.

## 02.05. Reference Architecture

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 참조 아키텍처(Humanoid Reference Architecture)는 신체 구조, 전력 분배(Power Distribution), 컴퓨팅 계층(Computing Hierarchy), 통신 네트워크(Communication Network), 센싱(Sensing), 액추에이션(Actuation), 안전(Safety), 소프트웨어(Software)를 하나의 일관된 엔지니어링 프레임워크(Engineering Framework)로 연결하는 재사용 가능한 시스템 청사진(System Blueprint)을 제공한다. 하나의 고정된 구현 방식을 정의하는 것이 아니라 기능적 경계(Functional Boundary)와 표준화된 인터페이스(Standardized Interface)를 설정하여 서로 다른 크기, 관절 수, 성능 목표 및 응용 요구사항을 가진 휴머노이드에 적용할 수 있도록 한다.

물리적 수준(Physical Level)에서 휴머노이드는 몸통(Torso), 머리(Head), 양팔(Arms), 양손(Hands), 양다리(Legs), 발(Feet)을 중심으로 구성된다. 몸통은 중앙 컴퓨팅(Central Computing), 전력 분배, 통신 인프라(Communication Infrastructure), 안전 기능을 위한 핵심 통합 영역(Primary Integration Zone)의 역할을 한다. 각 팔다리는 분산 관절 모듈(Distributed Joint Module), 센서, 로컬 전자장치(Local Electronics), 하니스 연결(Harness Connection)을 포함하는 모듈식 서브시스템(Modular Subsystem)으로 구성되어 명확한 기계적 및 전기적 통합 경계를 형성한다.

참조 전력 아키텍처(Reference Power Architecture)는 배터리 시스템(Battery System)에서 시작하여 보호(Protection), 스위칭(Switching), 전력 분배 장치(PDU, Power Distribution Unit), DC-DC 변환(DC-DC Conversion) 단계를 통해 에너지를 분배한다. 고출력 액추에이터 영역(High-Power Actuator Domain)은 민감한 저전압 전자장치(Low-Voltage Electronics)와 분리하면서 제어된 접지(Grounding) 및 보호 전략을 유지한다. 구현에 따라 48 V, 72 V 또는 다른 전압 수준을 사용할 수 있지만 계층적이고 보호되며 관측 가능하고 정비 가능한 전력 공급이라는 아키텍처 원칙은 동일하게 유지된다.

관절 모듈(Joint Module)은 참조 아키텍처의 기본적인 전기기계 구성 블록(Electromechanical Building Block)을 형성한다. 각 모듈에는 모터(Motor), 모터 드라이버(Motor Driver), 엔코더 인터페이스(Encoder Interface), 토크 센싱(Torque Sensing), 브레이크 기능(Brake Function), 로컬 제어기(Local Controller), 통신 인터페이스, 진단 기능을 통합할 수 있다. 이러한 인터페이스를 표준화하면 기계적 크기와 액추에이터 정격이 서로 다르더라도 어깨, 팔꿈치, 손목, 엉덩관절, 무릎, 발목 및 기타 관절에 공통적인 아키텍처 원칙을 적용할 수 있다.

팔 아키텍처(Arm Architecture)는 어깨(Shoulder), 상완(Upper Arm), 팔꿈치(Elbow), 손목(Wrist), 말단 작동기 인터페이스(End-Effector Interface)를 하나의 협조된 전기적 체인으로 구성한다. 다리 아키텍처(Leg Architecture)도 엉덩관절(Hip), 무릎(Knee), 발목(Ankle), 발 센싱(Foot Sensing), 균형 제어 인터페이스(Balance-Control Interface)를 연결한다. 손은 손가락 액추에이터(Finger Actuator), 촉각 센서(Tactile Sensor), 힘 센싱(Force Sensing), 마이크로 모터 드라이브(Micro-Motor Drive)의 고밀도 네트워크를 구성하며, 머리는 카메라(Camera), 라이다(LiDAR), 마이크(Microphone), 스피커(Speaker), 디스플레이(Display), 인지 관련 전자장치를 집중적으로 배치한다.

컴퓨팅 아키텍처(Computing Architecture)는 결정론적 물리 제어(Deterministic Physical Control)를 컴퓨팅 집약적인 인지 및 AI 워크로드와 분리한다. 임베디드 관절 프로세서(Embedded Joint Processor)는 로컬 액추에이터 기능을 실행하고, 분산 제어기(Distributed Controller)는 팔다리를 협조 제어하며, 중앙 실시간 컴퓨터(Central Real-Time Computer)는 전신 제어(Whole-Body Control), 균형(Balance), 보행(Locomotion), 조작(Manipulation), 상태 추정(State Estimation)을 수행한다. AI 컴퓨터와 GPU는 이러한 결정론적 영역 상위에서 인지, 계획, 멀티모달 추론(Multimodal Reasoning), 체화 지능(Embodied Intelligence) 워크로드를 실행한다.

이러한 컴퓨팅 분리는 지능(Intelligence)에서 물리적 행동(Physical Action)으로 이어지는 통제된 경로를 형성한다. AI 시스템은 목표를 결정하고 환경을 해석하며 행동을 제안할 수 있고, 모션 계획기(Motion Planner)는 이러한 의도를 실행 가능한 궤적(Feasible Trajectory)으로 변환한다. 이후 전신 및 팔다리 제어기는 동역학적, 운동학적, 접촉 및 안정성 제약을 적용하고, 관절 제어기는 최종적으로 생성된 기준값을 모터 명령으로 변환한다. 센서 피드백(Sensor Feedback)은 반대 방향으로 전달되어 제어 계층을 폐루프로 구성한다.

참조 아키텍처는 상위 컴퓨팅 계층에 비전-언어 모델(VLM, Vision-Language Model), 비전-언어-행동 모델(VLA, Vision-Language-Action Model), 에이전트(Agent), 멀티 에이전트 협조(Multi-Agent Coordination), 파운데이션 모델(Foundation Model), 피지컬 AI 런타임(Physical AI Runtime)을 포함할 수 있다. 이러한 기능은 결정론적 제어를 대체하지 않으면서 의미론적 이해(Semantic Understanding)와 적응형 행동(Adaptive Behavior)을 제공한다. 명시적인 인터페이스를 통해 학습 기반 또는 확률적 출력이 물리적 액추에이터에 영향을 주기 전에 검증되고 제약되도록 한다.

인지 아키텍처(Perception Architecture)는 기존 제어와 체화 AI 모두에 필요한 환경 정보를 제공한다. 카메라, 라이다, 마이크, IMU, 관절 엔코더(Joint Encoder), 토크 센서(Torque Sensor), 촉각 센서, 발 센서(Foot Sensor)는 상호 보완적인 관측 정보를 생성한다. 전용 인지 컴퓨팅(Dedicated Perception Computing)은 대용량 원시 데이터 스트림을 객체, 자세(Pose), 접촉(Contact), 지도(Map), 환경 표현(Environmental Representation), 상태 추정값으로 변환하여 계획 및 AI 계층이 효율적으로 사용할 수 있도록 한다.

통신 아키텍처(Communication Architecture)는 분산된 자원을 타이밍 및 대역폭 요구사항에 따라 연결한다. 이더캣(EtherCAT)은 결정론적인 액추에이터 및 모션 제어 통신을 지원할 수 있고, CAN FD는 분산 제어와 진단에 사용할 수 있으며, 기가비트 이더넷(Gigabit Ethernet)은 인지 및 컴퓨팅 데이터를 전송할 수 있다. ROS 2와 DDS는 상위 수준의 소프트웨어 통신을 제공하여 모듈식 서비스(Modular Service)가 이기종 프로세서(Heterogeneous Processor) 사이에서 구조화된 정보를 교환할 수 있도록 한다.

공통 시간 기준(Common Time Base)은 센싱, 컴퓨팅, 제어를 시간적으로 일관된 하나의 시스템으로 연결한다. PTP 기반 시간 동기화(PTP-Based Time Synchronization)는 카메라, 관성 센서(Inertial Sensor), 관절 제어기, 힘 센서, 인지 컴퓨터, 실시간 프로세서에 일관된 타임스탬프(Consistent Timestamp)를 분배할 수 있다. 정확한 시간적 상관관계(Temporal Correlation)는 센서 융합(Sensor Fusion), 상태 추정, 협조 동작(Coordinated Motion), 진단 재구성(Diagnostic Reconstruction), 여러 서브시스템을 통해 전파되는 이벤트 분석의 정확도를 향상시킨다.

데이터 흐름 아키텍처(Data Flow Architecture)도 동일한 기능적 경계를 따른다. 원시 측정값은 센서에서 로컬 처리 및 인지 영역으로 이동하고, 상태 정보는 계획 및 AI 계층을 향해 상향 전달되며, 목표는 점진적으로 궤적, 팔다리 명령, 관절 기준값, 모터 제어 값으로 변환된다. 대용량 센서 스트림은 가능한 경우 해당 데이터를 소비하는 컴퓨팅 자원 가까이에서 처리하여 중앙 네트워크를 통한 불필요한 데이터 이동을 방지한다.

안전 아키텍처(Safety Architecture)는 독립된 하나의 서브시스템으로 동작하는 것이 아니라 모든 기능 영역에 중첩된다. 비상 정지(Emergency Stop), 충돌 감지(Collision Detection), 중복 센싱(Redundant Sensing), 안전 제어기(Safety Controller), 액추에이터 정지(Actuator Shutdown), 전력 차단(Power Isolation)은 일반적인 제어 명령보다 우선하는 권한을 유지해야 한다. 안전 필수 대응(Safety-Critical Response)은 상위 AI 실행과 독립적으로 유지되어 정지, 과부하, 통신 단절 또는 잘못된 AI 프로세스가 필수적인 보호 동작을 제거하지 못하도록 해야 한다.

고장 허용 운전(Fail-Operational) 및 성능 저하 운전(Degraded Operation) 개념은 서브시스템의 중요도에 따라 적용할 수 있다. 중요하지 않은 인터페이스의 손실은 제한된 기능으로 운전을 계속할 수 있지만, 균형, 중요 통신, 액추에이터 제어 또는 안전 센싱에 영향을 주는 고장은 안정화(Stabilization) 또는 제어된 정지(Controlled Shutdown)를 발생시킬 수 있다. 중복 센서, 컴퓨팅 자원, 통신 경로 및 모니터링 메커니즘을 통해 손실 시 허용할 수 없는 시스템 위험을 발생시키는 기능을 보호할 수 있다.

진단(Diagnostics)은 아키텍처 전반에 지속적인 관측 가능성(Observability)을 제공한다. 관절 모듈, 센서, 모터 드라이버, 배터리, 전력 변환기(Power Converter), 네트워크, 실시간 컴퓨터 및 AI 프로세서는 건전성 및 운용 정보(Health and Operating Information)를 모니터링 기능에 보고한다. 이벤트 로깅(Event Logging), 원격 진단(Remote Diagnostics), 디지털 트윈(Digital Twin), 예지 정비(Predictive Maintenance)는 이러한 데이터를 이용하여 고장을 재구성하고 성능 저하를 식별하며 현장 관측 결과를 특정 하드웨어 또는 소프트웨어 구성요소와 연결할 수 있다.

하니스 및 커넥터 엔지니어링(Harness and Connector Engineering)은 논리적 아키텍처를 실제 신체의 물리적 연결로 변환한다. 중앙 몸통 하니스(Central Torso Harness)는 전력과 통신을 머리 및 팔다리 방향으로 분배하고, 유연한 팔 및 다리 하니스(Flexible Arm and Leg Harness)는 반복적인 관절 움직임을 수용한다. 가능한 경우 커넥터 경계(Connector Boundary)는 모듈 교체 경계(Modular Replacement Boundary)와 일치하도록 설계하여 신체를 광범위하게 분해하지 않고 팔다리, 관절, 센서, 컴퓨터 또는 전력 모듈을 분리할 수 있도록 해야 한다.

따라서 정비성(Serviceability)은 개발 완료 후 추가되는 기능이 아니라 참조 아키텍처에 처음부터 포함된다. 표준화된 전기적, 기계적, 통신, 진단 및 소프트웨어 인터페이스를 통해 모듈을 독립적으로 시험하고 체계적으로 교체할 수 있다. 생산 시험(Production Testing), 최종 라인 시험(End-of-Line Testing), 현장 서비스(Field Service), 모듈식 교체(Modular Replacement), 예비 부품 전략(Spare-Parts Strategy), 수명주기 관리(Lifecycle Management)는 초기 시스템 설계에서 정의한 동일한 서브시스템 경계를 활용할 수 있다.

소프트웨어 아키텍처(Software Architecture)는 전기 시스템의 모듈성을 동일하게 반영한다. 실시간 제어, 인지, AI 추론(AI Inference), 모션 계획(Motion Planning), 진단, OTA 업데이트(OTA Update), 건전성 모니터링(Health Monitoring), 외부 통신(External Communication)을 명확하게 정의된 기능 서비스로 분리한다. 안정적인 API, 메시지 정의(Message Definition), 버전 관리(Version Management), 통제된 의존 관계(Controlled Dependency)를 통해 개별 소프트웨어 또는 하드웨어 구성요소가 전체 휴머노이드 플랫폼을 다시 설계하지 않고 발전할 수 있도록 한다.

엣지-클라우드 통합(Edge-Cloud Integration)은 참조 아키텍처의 일부 기능을 로봇 외부로 확장한다. 휴머노이드는 즉각적인 동작에 필요한 온보드 인지(Onboard Perception), 제어, 안전 및 자율 기능을 유지하고, 외부 컴퓨팅은 모델 학습(Model Training), 플릿 분석(Fleet Analytics), 소프트웨어 배포(Software Distribution), 원격 진단, 디지털 트윈 및 장기 데이터 처리를 지원할 수 있다. 필수적인 물리 제어는 네트워크 연결 가능 여부와 독립적으로 유지되어야 한다.

제조 관점(Manufacturing Consideration)은 아키텍처 표준화의 필요성을 더욱 강화한다. 재사용 가능한 관절 모듈, 일관된 커넥터 제품군(Connector Family), 표준화된 하니스 인터페이스, 공통 통신 프로토콜(Common Communication Protocol), 정의된 진단 서비스는 신체 전체에서 불필요한 변형을 줄인다. 동일한 원칙을 이용하면 전체 시스템 구조를 유지하면서 액추에이터 용량, 센서 구성, 컴퓨팅 성능 또는 팔다리 형상을 변경하여 여러 휴머노이드 모델을 지원할 수 있다.

참조 아키텍처는 체계적인 검증(Verification)을 위한 기반도 제공한다. 전력 영역(Power Domain)은 독립적으로 시험할 수 있고, 통신 인터페이스는 타이밍과 대역폭에 대해 검증할 수 있으며, 관절 모듈은 기능 및 신뢰성 시험(Reliability Testing)을 수행할 수 있다. 안전 메커니즘은 고장 주입(Fault Injection) 및 통제된 고장 시나리오(Controlled Failure Scenario)를 통해 검증할 수 있으며, 이후 통합 시험(Integrated Testing)을 통해 서브시스템 간 상호작용이 시스템 수준 요구사항을 만족하는지 확인할 수 있다.

궁극적으로 휴머노이드 참조 아키텍처는 하나의 단순한 블록 다이어그램이 아니라 계층화된 통합 프레임워크(Layered Integration Framework)이다. 신체 영역(Body Zone)은 물리적 모듈성을 정의하고, 전력 아키텍처는 보호된 에너지를 공급하며, 통신 및 동기화는 분산 장치를 연결한다. 컴퓨팅 계층은 센싱을 지능으로 변환하고 제어 계층은 지능을 움직임으로 변환한다. 안전, 진단, 정비성 및 수명주기 관리는 전체 시스템을 감독하고 지속적으로 유지한다.

고출력 액추에이션(High-Power Actuation), 결정론적 제어, 인지, AI 추론(AI Reasoning), 안전 및 외부 컴퓨팅 사이에 명확한 경계를 유지함으로써 참조 아키텍처는 미래 휴머노이드를 위한 확장 가능한 기반(Scalable Foundation)을 제공한다. 새로운 센서, 프로세서, AI 모델, 관절 기술, 통신 프로토콜 및 소프트웨어 서비스를 정의된 인터페이스 내부에 도입할 수 있으므로 플랫폼은 일관된 전기 및 시스템 수준 엔지니어링 원칙을 유지하면서 지속적으로 발전할 수 있다.
