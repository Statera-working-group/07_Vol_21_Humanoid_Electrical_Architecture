**Volume 21. Humanoid Electrical Architecture**

# Chapter 01. Humanoid Electrical Architecture Overview

## 01.01. Humanoid System Overview

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 로봇(Humanoid Robot)은 인지(Perception), 컴퓨팅(Computation), 전력 공급(Power Delivery), 통신(Communication), 구동(Actuation), 안전(Safety)이 하나의 통합된 아키텍처(Architecture)로 동작해야 하는 고도로 통합된 전기기계 시스템(Electromechanical System)이다. 안정된 베이스(Base)에 고정된 기존 산업용 로봇과 달리 휴머노이드는 여러 관절형 팔다리를 움직이는 동시에 자신의 자세를 지속적으로 제어해야 한다. 따라서 전기 아키텍처(Electrical Architecture)는 단순히 개별 액추에이터(Actuator)를 지원하는 수준을 넘어 전신 동작(Whole-Body Behavior)을 구성하는 핵심 기반이 된다.

휴머노이드의 신체는 몸통(Torso), 머리(Head), 팔(Arm), 손(Hand), 다리(Leg), 발(Foot)을 중심으로 구성된 지능형 전기 서브시스템(Intelligent Electrical Subsystem)의 분산 네트워크(Distributed Network)로 볼 수 있다. 각 영역에는 액추에이터(Actuator), 모터 드라이브(Motor Drive), 엔코더(Encoder), 힘 또는 토크 센서(Force or Torque Sensor), 로컬 제어기(Local Controller), 통신 인터페이스(Communication Interface)가 조합되어 배치된다. 이러한 분산 모듈(Distributed Module)은 상위 수준의 컴퓨팅 및 네트워크 자원과 협력하여 기계적 기능을 관리 가능한 전기 및 연산 도메인(Computational Domain)으로 분리한다.

시스템 수준(System Level)에서 몸통(Torso)은 주요 전력(Power), 컴퓨팅(Computing), 네트워크(Networking), 안전(Safety) 기능을 통합하기 위한 자연스러운 중심 영역이 된다. 배터리 모듈(Battery Module)은 주 에너지원(Primary Energy Source)을 공급하며, 전력 분배 하드웨어(Power Distribution Hardware)는 관절 드라이브(Joint Drive), 컴퓨터, 센서, 보조 전자장치로 에너지를 전달한다. 고출력 액추에이터와 저전력 디지털 전자장치는 서로 다른 전기적 요구사항, 보호 조건, 과도 특성(Transient Characteristics)을 가지므로 여러 전압 도메인(Voltage Domain)이 함께 사용될 수 있다.

관절 모듈(Joint Module)은 휴머노이드의 움직임을 생성하는 기본적인 구성 요소이다. 하나의 관절에는 전기 모터(Electric Motor), 모터 드라이버(Motor Driver), 위치 엔코더(Position Encoder), 토크 센싱(Torque Sensing), 브레이크 기능(Braking Capability), 온도 모니터링(Temperature Monitoring), 로컬 진단(Local Diagnostics)이 통합될 수 있다. 현대적인 휴머노이드 설계에서는 모터를 독립된 부품으로 취급하기보다 명령 수신, 상태 보고, 이상 감지, 협조 제어(Coordinated Control)에 참여할 수 있는 지능형 모듈(Intelligent Module)로 액추에이터 어셈블리(Actuator Assembly) 전체를 다루는 방향으로 발전하고 있다.

팔(Arm)은 어깨(Shoulder), 상완(Upper Arm), 팔꿈치(Elbow), 손목(Wrist), 엔드 이펙터 인터페이스(End-Effector Interface)에 걸친 협조 전기 제어(Coordinated Electrical Control)를 필요로 한다. 이러한 관절은 충분한 토크(Torque)를 제공하면서도 부드러운 움직임과 정확한 위치 제어를 유지해야 한다. 손(Hand)은 작은 공간 안에 다수의 손가락 액추에이터(Finger Actuator), 촉각 센서(Tactile Sensor), 힘 센서(Force Sensor), 마이크로 모터 드라이브(Micro Motor Drive)를 배치해야 하므로 추가적인 설계 난도가 발생한다. 이에 따라 말단부(End Effector)에 가까워질수록 전기 통합 밀도(Electrical Integration Density)가 크게 증가한다.

다리(Leg)는 체중을 직접 지지하고 동적 균형(Dynamic Balance)을 유지해야 하므로 더욱 강한 실시간 요구사항(Real-Time Requirement)을 가진다. 엉덩이(Hip), 무릎(Knee), 발목(Ankle) 모듈은 매우 작고 예측 가능한 지연시간(Latency)으로 명령과 피드백을 교환해야 한다. 발 센싱(Foot Sensing)은 접촉 상태, 하중 분포, 지면과의 상호작용 정보를 제공한다. 이러한 피드백은 균형 제어(Balance Control), 보행 생성(Gait Generation), 외란 회복(Disturbance Recovery), 서기·걷기·회전과 같은 전신 동작 사이의 안전한 전환에 활용된다.

인지(Perception)는 전기 아키텍처의 범위를 모션 제어(Motion Control) 이상으로 확장한다. 카메라(Camera), 라이다(LiDAR), 관성 센싱(Inertial Sensing), 마이크(Microphone), 촉각 장치(Tactile Device) 등의 센서는 로봇 자체와 주변 환경에 관한 정보를 지속적으로 생성한다. 특히 머리(Head)는 카메라 어레이(Camera Array), 거리 측정 센서(Ranging Sensor), 마이크 어레이(Microphone Array), 스피커(Speaker), 디스플레이(Display), 전용 인지 컴퓨팅(Perception Computing)을 포함할 수 있는 중요한 인지 영역이다. 따라서 센서 배치, 대역폭(Bandwidth), 시간 동기화(Synchronization), 전원 무결성(Power Integrity), 열 관리(Thermal Management)는 시스템 수준의 설계 요소가 된다.

컴퓨팅(Computing)은 일반적으로 시간 특성과 작업 부하(Workload)의 특성에 따라 분리된다. 실시간 제어 프로세서(Real-Time Control Processor)는 액추에이터, 균형, 안전 관련 기능의 결정론적 제어 루프(Deterministic Control Loop)를 담당하고, AI 컴퓨터(AI Computer)와 GPU는 인지, 계획(Planning), 언어(Language), 멀티모달 모델(Multimodal Model), 상위 수준 행동을 처리한다. 이러한 분리는 연산량이 많은 AI 작업이 시간 임계 제어(Time-Critical Control)에 직접적인 영향을 주는 것을 방지한다. 시간 동기화(Time Synchronization)는 센서 관측과 액추에이터 상태를 일관된 시간 기준(Temporal Reference)으로 해석할 수 있도록 서로 다른 컴퓨팅 도메인을 연결한다.

통신 네트워크(Communication Network)는 이러한 분산 구성 요소를 연결하는 신경계(Nervous System)의 역할을 수행한다. CAN FD는 강건한 임베디드 통신(Embedded Communication)을 지원할 수 있으며, 이더캣(EtherCAT)은 긴밀하게 동기화된 액추에이터 및 제어 네트워크에 활용될 수 있다. 기가비트 이더넷(Gigabit Ethernet)은 카메라, 인지 컴퓨터, 중앙 컴퓨팅 자원에 필요한 높은 대역폭을 제공하며, ROS 2/DDS는 하드웨어 전송 계층(Hardware Transport Layer) 상위에서 분산 소프트웨어 통신을 지원할 수 있다. PTP 기반 동기화(PTP-Based Synchronization)는 네트워크 장치 전체에 공통 시간 기준(Common Timing Reference)을 제공할 수 있다.

와이어 하네스 및 커넥터 엔지니어링(Wire Harness and Connector Engineering)은 휴머노이드의 배선이 신체 움직임에 따라 반복적으로 굽힘과 비틀림을 받기 때문에 특히 중요하다. 몸통 하네스(Torso Harness)는 비교적 구조화된 배치가 가능하지만, 팔과 다리의 하네스는 관절 움직임에 따른 지속적인 굴곡을 견뎌야 한다. 배선 경로는 굽힘 반경(Bend Radius), 스트레인 릴리프(Strain Relief), 전자파 적합성(Electromagnetic Compatibility), 마모(Abrasion), 커넥터 유지력(Connector Retention), 정비 접근성(Service Access), 기계적 간섭을 고려해야 하며 액추에이터 부하와 에너지 소비를 증가시키는 불필요한 질량도 최소화해야 한다.

안전(Safety)은 상당한 전기 및 기계 에너지(Mechanical Energy)를 가진 휴머노이드가 사람과 동일한 물리적 공간을 공유하기 때문에 전기, 연산, 기계 계층 전반에서 동작해야 한다. 비상 정지(Emergency Stop), 충돌 감지(Collision Detection), 중복 센싱(Redundant Sensing), 제어된 전력 차단(Controlled Power Isolation), 제동(Braking), 고장 격리(Fault Containment), 고장 시 운전 유지(Fail-Operational) 또는 안전 고장(Fail-Safe) 전략이 일관성 있게 상호작용해야 한다. 따라서 고장이 감지되었을 때 임의의 전자장치를 단순히 정지시키는 것이 아니라 시스템 수준에서 적절한 대응이 수행되어야 한다.

진단(Diagnostics)은 복잡한 분산형 기계 시스템의 상태를 지속적으로 파악할 수 있도록 한다. 관절 온도, 모터 전류, 엔코더 상태, 통신 오류, 배터리 상태, 센서 건전성(Sensor Health), 컴퓨팅 상태, 전력 분배 고장을 모니터링하고 기록할 수 있다. 원격 진단(Remote Diagnostics)과 디지털 트윈(Digital Twin)은 이러한 정보를 물리적 로봇 외부로 확장하며, 예측 유지보수(Predictive Maintenance)는 축적된 운용 데이터를 활용하여 성능 저하가 예상하지 못한 현장 고장으로 발전하기 전에 이를 식별할 수 있도록 한다.

전기 아키텍처는 제조(Manufacturing)와 수명주기(Lifecycle) 요구사항도 지원해야 한다. 생산 시험(Production Testing)과 생산라인 최종 시험(End-of-Line Verification)은 배치 전에 각 모듈이 정상적으로 동작하는지 확인하며, 모듈식 교체(Modular Replacement)는 현장 정비의 복잡성을 줄인다. 표준화된 전기 인터페이스(Standardized Electrical Interface)를 적용하면 관절, 센서, 컴퓨터, 배터리 등의 서브시스템을 전체 로봇의 재설계 없이 교체하거나 업그레이드할 수 있으므로 정비성(Serviceability)은 사후 고려사항이 아니라 아키텍처의 기본 요구사항이 된다.

휴머노이드 지능(Humanoid Intelligence)은 기존의 인지 및 모션 제어 위에 또 하나의 아키텍처 계층을 추가하고 있다. 비전-언어 모델(Vision-Language Model), 비전-언어-행동 모델(Vision-Language-Action Model), 에이전트(Agent), 파운데이션 모델(Foundation Model), 피지컬 AI 런타임(Physical AI Runtime)은 멀티모달 관측(Multimodal Observation)을 목표와 행동으로 변환할 수 있다. 그러나 이러한 AI 구성 요소는 명확하게 정의된 인터페이스를 통해 결정론적 제어(Deterministic Control) 및 안전 계층과 연결되어야 하며, 확률적 추론(Probabilistic Reasoning)이 안정적이고 안전한 물리적 실행을 담당하는 메커니즘을 우회하지 않도록 해야 한다.

실용적인 휴머노이드 시스템은 긴밀하게 결합된 에너지(Energy), 정보(Information), 제어(Control) 흐름의 계층 구조로 이해하는 것이 적절하다. 전력은 배터리와 전력 분배 장치(Power Distribution Unit)에서 컴퓨팅, 센싱, 액추에이션으로 이동하고, 센서 데이터는 실시간 컴퓨팅과 AI 컴퓨팅으로 전달되며, 명령은 다시 분산 관절 모듈로 전달된다. 동시에 진단 및 안전 정보는 이러한 경로를 지속적으로 교차한다. 궁극적으로 휴머노이드의 성능은 움직임, 부하, 고장, 환경 외란(Environmental Disturbance)이 발생하는 상황에서도 이러한 흐름을 얼마나 효과적으로 동기화하고 유지하는가에 달려 있다.

전체적인 설계 과제는 단순히 액추에이터 출력이나 AI 컴퓨팅 성능을 극대화하는 것이 아니다. 성공적인 아키텍처는 에너지 효율(Energy Efficiency), 결정론적 제어, 통신 대역폭, 센서 정확도(Sensor Fidelity), 배선 복잡성, 열적 한계(Thermal Limit), 기능 안전(Functional Safety), 유지보수성(Maintainability), 연산 능력(Computational Capability) 사이의 균형을 확보해야 한다. 이러한 통합을 통해 휴머노이드는 전기 아키텍처를 기반으로 기계적 신체화(Mechanical Embodiment), 인지, 지능, 현실 세계의 행동(Real-World Action)을 연결하는 하나의 통합된 피지컬 AI 플랫폼(Physical AI Platform)으로 구현된다.

## 01.02. Functional Requirements

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 로봇의 기능 요구사항(Functional Requirements)은 안정적인 보행(Locomotion), 정교한 조작(Dexterous Manipulation), 인지(Perception), 지능(Intelligence), 통신(Communication), 안전(Safety), 유지보수성(Maintainability)을 지원하기 위해 전체 전기·전자 시스템(Electrical and Electronic System)이 수행해야 하는 기능을 정의한다. 이러한 요구사항은 기계적 능력(Mechanical Capability)을 전력, 센싱, 컴퓨팅, 네트워킹, 제어와 연결한다. 따라서 개별 관절 모듈(Joint Module)이나 전자 부품을 선정하기 전에 시스템 수준(System Level)에서 요구사항을 정의해야 한다.

주요 동작 요구사항(Motion Requirement)은 몸통(Torso), 팔(Arm), 손(Hand), 다리(Leg), 머리(Head) 및 기타 메커니즘에 분산된 다수의 관절을 협조 제어(Coordinated Control)하는 것이다. 각 관절은 동작 명령(Motion Command)을 수신하고 충분히 정확한 위치, 속도, 토크, 온도 및 상태 정보를 제공해야 한다. 여러 관절에서 누적되는 지연은 자세, 조작 정확도, 보행 안정성, 전신 협조(Whole-Body Coordination)에 직접적인 영향을 줄 수 있으므로 제어 지연시간(Control Latency)과 갱신 주기(Update Timing)는 예측 가능해야 한다.

보행(Locomotion)을 위해 전기 아키텍처(Electrical Architecture)는 엉덩이(Hip), 무릎(Knee), 발목(Ankle), 신체 지지 관절을 지속적으로 제어하면서 동적 균형(Dynamic Balance)을 유지해야 한다. 발 센싱(Foot Sensing)은 지면 접촉과 하중 상태에 관한 신뢰성 높은 정보를 제공해야 하며, 관성 정보(Inertial Information)는 신체 방향과 움직임을 추정하는 데 사용된다. 시스템은 서기, 걷기, 회전, 외란 회복(Disturbance Recovery), 서로 다른 동작 상태 사이의 전환 과정에서도 동기화된 피드백과 액추에이터 제어(Actuator Control)를 유지해야 한다.

조작(Manipulation)은 보행과 다른 특성의 요구사항을 발생시킨다. 어깨와 팔 관절은 비교적 높은 토크와 제어된 움직임이 필요하지만, 손목과 손은 소형 전자장치, 정밀 위치 제어(Fine Position Control), 촉각 센싱(Tactile Sensing), 힘 센싱(Force Sensing), 다수의 소형 액추에이터를 요구한다. 따라서 전기 시스템은 공통 아키텍처 내에서 서로 다른 액추에이터 클래스(Heterogeneous Actuator Classes)를 지원하면서 각 서브시스템이 기계적 기능에 적합한 대역폭, 정밀도, 보호 및 진단 기능을 갖추도록 해야 한다.

전력 시스템(Power System)은 액추에이터, 컴퓨터, 센서, 통신 장치 및 보조 시스템이 동시에 동작하는 데 필요한 충분한 순간 및 연속 에너지를 제공해야 한다. 여러 관절이 동시에 가속, 감속하거나 외력에 저항하면서 휴머노이드의 전기 부하(Electrical Load)는 빠르게 변화할 수 있다. 전력 분배 시스템(Power Distribution System)은 이러한 과도 부하(Transient Load)를 견디면서 민감한 전자장치에 안정적인 전압을 공급하고, 하나의 과부하 또는 고장 분기가 관련 없는 다른 기능까지 불필요하게 중단시키는 것을 방지해야 한다.

서로 다른 부하를 효율적으로 지원하기 위해 다중 전압 도메인(Multiple Voltage Domains)이 필요할 수 있다. 고출력 관절 드라이브(Joint Drive)는 주 액추에이터 버스(Primary Actuator Bus)를 사용할 수 있으며, 컴퓨터, 센서, 통신 전자장치 및 제어 장치는 더 낮은 조정 전압(Regulated Voltage)을 요구할 수 있다. 배터리 모듈(Battery Module), DC-DC 변환(DC-DC Conversion), 전력 분배 장치(Power Distribution Unit), 보호 장치(Protection Device), 모니터링 회로(Monitoring Circuit)는 에너지를 효율적으로 분배하고 고장이 로봇 전체로 전파되기 전에 감지 및 격리할 수 있도록 협력해야 한다.

인지 시스템(Perception System)은 자율 운용(Autonomous Operation)에 필요한 충분한 환경 및 내부 상태 정보를 제공해야 한다. 카메라 어레이(Camera Array), 라이다(LiDAR), 마이크(Microphone), 관성 센서(Inertial Sensor), 힘 센서(Force Sensor), 촉각 센서(Tactile Sensor), 엔코더(Encoder) 등의 장치가 동시에 동작할 수 있다. 따라서 기능 요구사항에는 센서 대역폭(Sensor Bandwidth), 샘플링 주파수(Sampling Frequency), 동기화(Synchronization), 데이터 무결성(Data Integrity), 캘리브레이션 지원(Calibration Support), 가용성(Availability)이 포함되어야 한다. 센서 데이터는 제어되지 않는 지연이나 손실 없이 적절한 처리 시스템으로 전달되어야 한다.

컴퓨팅 요구사항(Computing Requirements)은 결정론적 제어(Deterministic Control)에서 연산 집약적인 인공지능(Artificial Intelligence)에 이르는 넓은 범위를 포함한다. 실시간 프로세서(Real-Time Processor)는 관절 제어, 균형 제어, 안전 감독(Safety Supervision) 및 기타 시간 임계 기능(Time-Critical Function)을 제한된 실행 시간 내에서 수행해야 한다. AI 컴퓨터(AI Computer)와 GPU는 인지, 멀티모달 추론(Multimodal Reasoning), 계획(Planning), 파운데이션 모델(Foundation Model), 체화 지능(Embodied Intelligence)을 지원해야 한다. 아키텍처는 높은 연산 부하를 갖는 AI 작업이 저수준 물리 제어에 필요한 시간 보장(Timing Guarantee)을 저하시키지 않도록 설계되어야 한다.

통신 요구사항(Communication Requirements)은 제어 트래픽(Control Traffic)과 인지 트래픽(Perception Traffic)의 서로 다른 특성을 반영해야 한다. CAN FD와 같은 네트워크는 강건한 임베디드 통신(Embedded Communication)을 지원할 수 있고, 이더캣(EtherCAT)은 긴밀하게 협조되는 장치에 결정론적 통신(Deterministic Communication)을 제공할 수 있으며, 기가비트 이더넷(Gigabit Ethernet)은 고대역폭 센서 및 컴퓨팅 데이터를 전송할 수 있다. ROS 2/DDS 등의 미들웨어(Middleware)는 분산 소프트웨어 기능을 연결하며, 기반 네트워크 아키텍처는 적절한 서비스 품질(Quality of Service)과 고장 격리(Fault Containment)를 유지해야 한다.

시간 동기화(Time Synchronization)는 선택적인 네트워크 기능이 아니라 하나의 기능 요구사항이다. 관절 상태, 관성 측정값, 카메라 프레임, 힘 측정값, 인지 출력, 제어 명령에는 일관된 타임스탬프(Timestamp)가 연결되어야 한다. PTP 또는 이에 상응하는 동기화 메커니즘(Synchronization Mechanism)은 분산 장치 사이에 공유 시간 기준(Shared Time Base)을 설정할 수 있다. 정확한 타이밍은 센서 융합(Sensor Fusion), 이벤트 재구성(Event Reconstruction), 협조 제어, 진단, 물리적 움직임과 기록된 데이터 사이의 의미 있는 상관관계를 가능하게 한다.

인간-로봇 상호작용(Human-Robot Interaction)은 상당한 힘을 생성할 수 있는 휴머노이드가 사람과 가까운 거리에서 동작하기 때문에 높은 수준의 안전 요구사항(Safety Requirements)을 발생시킨다. 시스템은 비상 정지(Emergency Stop), 충돌 감지(Collision Detection), 제어된 토크 감소(Controlled Torque Reduction), 전력 격리(Power Isolation), 중복 센싱(Redundant Sensing), 적절한 안전 고장(Fail-Safe) 또는 고장 시 운전 유지(Fail-Operational) 대응을 지원해야 한다. 잘못된 인지 결과나 상위 수준의 판단이 필수적인 보호 메커니즘을 무력화하지 않도록 안전 기능은 비안전 AI 동작(Non-Safety AI Behavior)으로부터 충분히 독립되어야 한다.

고장 관리(Fault Management)는 아키텍처 전체에 분산되어야 한다. 로컬 관절 제어기(Local Joint Controller)는 과전류, 과열, 엔코더 불일치, 통신 손실, 비정상적인 모터 동작 등을 감지해야 하며, 상위 제어기(Higher-Level Controller)는 이러한 고장이 전신 동작에 미치는 영향을 평가해야 한다. 고장의 심각도에 따라 성능 저하 운전(Degraded Operation), 동작 제한, 제어 정지(Controlled Stop), 관절 제동(Joint Braking), 전력 격리 또는 완전한 비상 정지(Emergency Shutdown)까지 서로 다른 대응이 수행될 수 있다.

전기 아키텍처는 물리적 통합 요구사항(Physical Integration Requirements)도 충족해야 한다. 하네스(Harness)와 커넥터(Connector)는 좁고 움직이는 구조물 내부에 배치되면서 반복적인 굽힘, 비틀림, 진동, 기계적 하중을 견뎌야 한다. 배선은 충분한 전류 용량(Current Capacity), 전압 강하 성능(Voltage-Drop Performance), 신호 무결성(Signal Integrity), 전자파 적합성(Electromagnetic Compatibility), 절연 보호(Insulation Protection)를 유지해야 한다. 동시에 추가적인 질량은 관절 토크와 에너지 소비를 직접 증가시키므로 하네스 질량과 배선 복잡성을 최소화해야 한다.

열적 거동(Thermal Behavior)은 전기적 기능과 밀접하게 연결된다. 모터, 모터 드라이버, DC-DC 컨버터(DC-DC Converter), 배터리, 프로세서, GPU, 통신 장치는 모두 열을 발생시키며, 이러한 장치들은 공기 흐름이 제한된 소형 신체 구조 내부에 배치되는 경우가 많다. 기능 요구사항은 허용 동작 범위(Acceptable Operating Range), 온도 모니터링, 디레이팅 동작(Derating Behavior), 보호 정지 임계값(Protective Shutdown Threshold)을 정의해야 한다. 열 관리(Thermal Management)는 국부적인 과열이 부품 수명을 단축하거나 안전을 저해하지 않으면서 필요한 성능을 유지할 수 있어야 한다.

진단(Diagnostics)은 로봇 상태를 지속적으로 파악할 수 있도록 해야 한다. 상태 모니터링(Health Monitoring)은 배터리, 전원 레일(Power Rail), 관절 드라이브, 센서, 네트워크, 컴퓨터, 안전 장치를 포함해야 한다. 이벤트 로깅(Event Logging)은 주요 고장과 운전 조건을 동기화된 타임스탬프와 함께 기록해야 한다. 원격 진단(Remote Diagnostics), 디지털 트윈 통합(Digital Twin Integration), 예측 유지보수(Predictive Maintenance)는 이러한 기능을 로봇의 전체 수명주기로 확장하여 고정된 유지보수 주기가 아닌 실제 운용 상태를 기반으로 정비 의사결정을 수행할 수 있도록 한다.

소프트웨어와 펌웨어 유지보수(Software and Firmware Maintenance)는 안전하고 제어 가능한 업데이트 메커니즘(Update Mechanism)에 대한 추가적인 요구사항을 발생시킨다. 무선 업데이트(Over-the-Air Update)는 정비 작업을 줄일 수 있지만, 업데이트 과정에서 핵심 제어기가 불일치하거나 사용할 수 없는 상태로 남아서는 안 된다. 따라서 버전 관리(Version Management), 호환성 검사(Compatibility Checking), 롤백 기능(Rollback Capability), 무결성 검증(Integrity Verification), 안전 중요 소프트웨어와 비안전 소프트웨어 도메인의 분리는 유지보수가 가능한 휴머노이드 전기 플랫폼을 구성하는 중요한 요소이다.

제조(Manufacturing) 및 현장 서비스(Field Service) 요구사항은 초기 아키텍처 설계 단계부터 반영되어야 한다. 관절 모듈, 센서 어셈블리(Sensor Assembly), 컴퓨터, 배터리, 하네스, 전력 분배 부품은 생산 시험(Production Testing), 생산라인 최종 검증(End-of-Line Verification), 고장 위치 식별(Fault Localization), 모듈식 교체(Modular Replacement)를 지원해야 한다. 표준화된 인터페이스(Standardized Interface)는 조립 및 수리 복잡성을 감소시키고 개별 서브시스템이 전체 휴머노이드 플랫폼의 완전한 재설계 없이 발전할 수 있도록 한다.

마지막으로 아키텍처는 기존 로봇 제어(Conventional Robotic Control)에서 체화 AI(Embodied AI)로의 전환을 지원해야 한다. 비전-언어 모델(Vision-Language Model), 비전-언어-행동 모델(Vision-Language-Action Model), 에이전트(Agent), 파운데이션 모델(Foundation Model), 피지컬 AI 런타임(Physical AI Runtime)은 동기화된 인지 및 로봇 상태 정보에 접근하면서 안전하게 물리적 움직임으로 변환될 수 있는 목표 또는 행동을 생성해야 한다. 따라서 AI 추론(AI Reasoning), 모션 계획(Motion Planning), 실시간 제어(Real-Time Control), 안전 감독(Safety Supervision) 사이의 명확한 인터페이스가 필수적이다.

이러한 기능 요구사항은 서로 독립적인 사양이 아니라 강하게 상호 의존한다. 액추에이터 성능을 높이면 배터리 용량, 배선, 열 부하, 안전 요구사항이 영향을 받고, 센서를 추가하면 대역폭, 동기화, 컴퓨팅 요구량이 증가한다. AI 성능을 높이면 전력 및 냉각 요구사항이 증가하고, 추가적인 중복성(Redundancy)은 질량과 통합 복잡성을 증가시킨다. 따라서 성공적인 휴머노이드 전기 아키텍처는 동작(Motion), 에너지(Energy), 정보(Information), 지능(Intelligence), 안전(Safety), 신뢰성(Reliability), 수명주기(Lifecycle) 요구사항 전체에 대한 시스템 수준 최적화(System-Level Optimization)를 통해 구현되어야 한다.

## 01.03. Zonal Architecture

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

조널 아키텍처(Zonal Architecture)는 모든 센서, 액추에이터, 주변장치를 중앙 제어기(Central Controller)에 개별적으로 연결하는 대신 로봇의 물리적 영역(Physical Region)을 기준으로 휴머노이드 전기 시스템을 구성한다. 몸통(Torso), 머리(Head), 팔(Arm), 손(Hand), 다리(Leg) 및 기타 신체 영역은 각각 로컬 전력 분배(Local Power Distribution), 통신 인터페이스(Communication Interface), 센싱 전자장치(Sensing Electronics), 제어 자원(Control Resource)을 포함하는 전기 존(Electrical Zone)을 형성할 수 있다. 이러한 방식은 전기적 구성을 휴머노이드의 물리적 구조와 일치시킨다.

기존의 중앙집중형 아키텍처(Centralized Architecture)는 개별 장치에서 중앙 전자 제어 장치(Central Electronic Unit)까지 많은 배선을 연결해야 할 수 있다. 다수의 관절과 센서를 갖는 휴머노이드에서는 이로 인해 상당한 하네스 질량(Harness Mass), 배선 경로 복잡성(Routing Complexity), 커넥터 수(Connector Count), 패키징 난이도(Packaging Difficulty)가 발생한다. 조널 아키텍처는 주변의 전기 인터페이스를 로컬 존 제어기(Zone Controller) 또는 게이트웨이(Gateway)에서 통합한 후 상위 컴퓨팅 시스템과 정보를 교환함으로써 이러한 장거리 점대점 연결(Point-to-Point Connection)을 감소시킨다.

몸통(Torso)은 배터리(Battery), 전력 분배 장치(Power Distribution Unit), 실시간 컴퓨터(Real-Time Computer), AI 컴퓨터(AI Computer), 네트워크 스위치(Network Switch), 안전 제어기(Safety Controller)를 수용할 수 있으므로 자연스럽게 중앙 통합 존(Central Integration Zone)의 역할을 수행한다. 이 중앙 영역에서 전력 및 고속 통신 백본(High-Speed Communication Backbone)이 주변 존으로 확장될 수 있다. 따라서 몸통 존(Torso Zone)은 분산된 신체 전자장치와 시스템 수준의 컴퓨팅, 에너지, 네트워크, 안전 인프라 사이를 연결하는 주요 브리지(Bridge) 역할을 수행한다.

팔(Arm)은 어깨(Shoulder), 상완(Upper Arm), 팔꿈치(Elbow), 손목(Wrist), 엔드 이펙터(End Effector)의 전자장치를 포함하는 독립적인 존으로 구성할 수 있다. 로컬 인터페이스(Local Interface)는 엔코더 데이터(Encoder Data), 토크 측정값(Torque Measurement), 온도, 모터 드라이버 상태(Motor-Driver Status), 진단 정보(Diagnostic Information)를 통합하면서 개별 관절로 제어 명령을 분배할 수 있다. 이러한 구성은 어깨를 통과하는 독립적인 신호 배선의 수를 감소시키고 팔 어셈블리(Arm Assembly)를 더욱 모듈화된 전기 서브시스템으로 구성할 수 있도록 한다.

손(Hand)은 정교한 손이 특히 높은 밀도의 소형 액추에이터와 센서를 포함하기 때문에 특수한 서브존(Sub-Zone)을 형성할 수 있다. 손가락 액추에이터(Finger Actuator), 촉각 어레이(Tactile Array), 힘 센서(Force Sensor), 마이크로 모터 드라이브(Micro Motor Drive), 로컬 제어기(Local Controller)는 작은 공간에서 다수의 저수준 신호(Low-Level Signal)를 생성할 수 있다. 로컬 통합(Local Aggregation)을 적용하면 가능한 많은 신호를 손 내부에서 처리하면서 상위 명령과 처리된 피드백만 보다 단순하고 표준화된 전력 및 통신 인터페이스를 통해 손목을 통과하도록 구성할 수 있다.

다리 존(Leg Zone)은 엉덩이(Hip), 무릎(Knee), 발목(Ankle), 발 센싱 시스템(Foot Sensing System)이 균형과 보행에 직접 참여하기 때문에 특히 결정론적 동작(Deterministic Behavior)이 요구된다. 로컬 다리 제어기(Local Leg Controller) 또는 통신 노드(Communication Node)는 주변 관절 인터페이스를 협조 제어하면서 동기화된 상태 정보를 중앙 실시간 제어기(Central Real-Time Controller)와 교환할 수 있다. 조널 분할(Zonal Partitioning)이 균형 제어 루프(Balance Control Loop)에 예측할 수 없는 지연을 발생시키거나 안전 중요 피드백(Safety-Critical Feedback)의 가용성을 저하시키지 않도록 설계해야 한다.

머리(Head)는 카메라(Camera), 라이다(LiDAR), 마이크 어레이(Microphone Array), 스피커(Speaker), 디스플레이(Display), 그리고 경우에 따라 로컬 인지 컴퓨팅(Local Perception Computing)을 포함하는 인지 중심 존(Perception-Oriented Zone)을 구성한다. 이러한 장치는 높은 대역폭의 데이터를 생성할 수 있으므로 머리 존은 액추에이터 중심 존보다 이더넷 계열 통신(Ethernet-Class Communication)에 더 많이 의존할 수 있다. 로컬 통합을 적용하면 목을 통과하는 케이블 수를 줄이면서 중앙 인지 및 AI 컴퓨팅 자원으로 동기화된 센서 데이터를 전달할 수 있다.

전력 분배(Power Distribution) 역시 동일한 조널 구조를 따를 수 있다. 몸통에서 모든 장치까지 개별적으로 보호된 전력 회로를 배선하는 대신 주 전력 백본(Main Power Backbone)을 통해 각 영역의 분배 노드(Distribution Node)에 전력을 공급하고, 해당 노드에서 주변 부하에 대한 분기 보호(Branch Protection), 스위칭(Switching), 전압 변환(Voltage Conversion), 전류 모니터링(Current Monitoring)을 수행할 수 있다. 고출력 액추에이터 회로와 저전압 전자장치는 적절하게 분리되어야 하지만, 조널 전력 분배(Zonal Power Distribution)를 적용하면 하네스를 단순화하고 고장 위치 식별 능력을 향상시킬 수 있다.

조널 전력 노드(Zonal Power Node)는 전압, 전류, 온도, 보호 상태(Protection Status)를 모니터링하여 비정상적인 상태를 발생 위치와 가까운 곳에서 식별할 수 있어야 한다. 주변 장치에 전기적 고장이 발생하면 전체 로봇의 전원을 불필요하게 차단하지 않고 영향을 받은 분기 또는 존만 격리할 수 있다. 이는 단계적 성능 저하(Graceful Degradation)를 지원하고 진단 해상도(Diagnostic Resolution)를 향상시키면서 하나의 중앙 전력 분배 장치(PDU)에 집중되어야 하는 보호 하드웨어의 양을 줄일 수 있다.

통신 아키텍처(Communication Architecture)는 조널 설계를 가능하게 하는 주요 기반 요소이다. 이더캣(EtherCAT) 또는 이와 유사한 결정론적 네트워크(Deterministic Network)는 모션 제어 장치를 연결하고, CAN FD는 강건한 임베디드 인터페이스를 지원하며, 기가비트 이더넷(Gigabit Ethernet)은 존 사이의 인지 및 컴퓨팅 트래픽을 전달할 수 있다. 필요한 경우 게이트웨이(Gateway)가 서로 다른 네트워크 기술을 연결할 수 있으며, ROS 2/DDS는 컴퓨팅 기능 사이의 상위 수준 분산 통신을 제공할 수 있다. 따라서 물리적 네트워크는 각 존에서 생성되는 트래픽의 특성에 맞게 최적화할 수 있다.

물리적인 영역 분리가 서로 다른 시간 도메인(Timing Domain)을 만들어서는 안 되므로 시간 동기화(Time Synchronization)는 모든 존에 걸쳐 적용되어야 한다. 관절 위치, 관성 측정값(Inertial Measurement), 발의 힘, 카메라 프레임, 촉각 정보, 제어 이벤트에는 전신 협조(Whole-Body Coordination)를 위한 일관된 타임스탬프(Timestamp)가 필요하다. PTP 기반 동기화(PTP-Based Synchronization) 또는 이에 상응하는 메커니즘은 휴머노이드 전체에 공통 시간 기준(Common Time Reference)을 분배하여 정확한 센서 융합(Sensor Fusion), 결정론적 제어 협조, 이벤트 로깅(Event Logging), 시스템 동작 재구성을 가능하게 한다.

조널 아키텍처는 하네스 엔지니어링(Harness Engineering)에도 변화를 가져온다. 다수의 전용 신호를 포함하는 긴 배선 번들(Wiring Bundle)을 전력 트렁크(Power Trunk)와 통신 백본(Communication Backbone), 그리고 짧은 로컬 분기(Local Branch)의 조합으로 대체할 수 있다. 이는 특히 어깨, 엉덩이, 목, 손목, 발목과 같은 가동 인터페이스(Moving Interface)에서 큰 장점을 제공한다. 이러한 관절 영역을 통과하는 도체 수를 줄이면 하네스 직경, 굽힘 저항(Bending Resistance), 기계적 피로(Mechanical Fatigue), 커넥터 복잡성 및 전체 로봇 질량을 감소시킬 수 있다.

모듈성(Modularity)은 또 다른 주요 장점이다. 팔, 다리, 손, 머리 어셈블리는 전력, 네트워크, 동기화, 진단, 안전 인터페이스를 정의하는 표준화된 전기 경계(Standardized Electrical Boundary)를 중심으로 설계할 수 있다. 제조 또는 정비 과정에서는 전체 로봇에 통합하기 전에 완전한 조널 모듈(Zonal Module)을 독립적으로 시험할 수 있다. 손상된 모듈을 교체할 때에도 다수의 개별 전기 연결을 다시 구성하는 대신 제한된 수의 표준 인터페이스만 분리하고 연결할 수 있으므로 정비성이 향상된다.

그러나 안전 기능(Safety Function)은 조널 경계를 넘어 효과적으로 동작해야 한다. 비상 정지 명령(Emergency-Stop Command), 충돌 정보(Collision Information), 관절 고장 상태(Joint Fault State), 중복 센서 신호(Redundant Sensor Signal), 전력 격리 요청(Power-Isolation Request)은 예측 가능한 방식으로 필요한 제어기에 전달되어야 한다. 존 제어기가 안전 동작을 방해하는 단일 고장점(Single Point of Failure)이 되어서는 안 된다. 따라서 시스템 위험도에 따라 중요 신호에는 중복 통신 경로(Redundant Communication Path), 독립 안전 채널(Independent Safety Channel), 로컬 보호 반응(Local Protective Reaction), 직접적인 하드웨어 메커니즘(Direct Hardware Mechanism)이 필요할 수 있다.

진단(Diagnostics)은 조널 아키텍처의 계층적 특성(Hierarchical Nature)을 통해 이점을 얻을 수 있다. 개별 장치는 로컬 상태 정보를 해당 존 제어기로 보고하고, 존 제어기는 상태를 통합하여 의미 있는 고장 정보를 중앙 진단 시스템(Central Diagnostic System)에 전달할 수 있다. 로봇은 문제가 특정 액추에이터, 센서, 로컬 네트워크 구간(Local Network Segment), 전력 분기(Power Branch), 또는 전체 신체 존에서 발생했는지를 식별할 수 있다. 이러한 계층 구조는 원격 진단(Remote Diagnostics), 이벤트 로깅, 디지털 트윈(Digital Twin), 예측 유지보수(Predictive Maintenance)도 지원한다.

프로세싱 능력(Processing Capability)이 더욱 소형화되고 향상됨에 따라 각 존 내부의 로컬 지능(Local Intelligence)도 점진적으로 증가할 수 있다. 존 제어기는 모든 원시 신호(Raw Signal)를 중앙 컴퓨터로 전달하는 대신 신호 조절(Signal Conditioning), 센서 전처리(Sensor Preprocessing), 액추에이터 협조(Actuator Coordination), 상태 모니터링(Health Monitoring), 로컬 안전 감독(Local Safety Supervision)을 수행할 수 있다. 그러나 로컬 자율성(Local Autonomy)이 전신 제어, 중앙 안전 정책(Centralized Safety Policy), 시스템 수준의 모션 목표와 충돌하지 않도록 책임의 분할을 명확하게 정의해야 한다.

조널 설계(Zonal Design)는 미래 휴머노이드 플랫폼을 위한 확장 가능한 경로(Scalable Path)도 제공한다. 서로 다른 크기와 구성을 가진 로봇에서도 공통적인 몸통, 팔, 손, 다리, 인지 존 개념을 재사용하면서 개별 모듈의 수 또는 성능을 변경할 수 있다. 새로운 센서나 액추에이터 역시 전체 전기 시스템을 재구성하지 않고 해당 존 내부에 통합할 수 있으므로 액추에이터, AI 컴퓨터, 센서, 배터리, 통신 기술의 발전에 따라 아키텍처를 지속적으로 확장할 수 있다.

결과적으로 조널 아키텍처는 물리적 조닝(Physical Zoning), 분산 제어(Distributed Control), 중앙 협조(Centralized Coordination)를 결합한다. 에너지와 고대역폭 데이터는 백본 네트워크(Backbone Network)를 통해 이동하고, 로컬 존 노드(Local Zone Node)는 주변의 전기 자원을 관리하며, 실시간 컴퓨팅(Real-Time Computing)은 전신 움직임을 협조 제어하고, AI 컴퓨팅(AI Computing)은 인지와 지능형 행동을 제공한다. 이러한 계층이 효과적으로 통합되면 조널 아키텍처는 배선 복잡성과 질량을 감소시키면서 모듈성, 확장성(Scalability), 정비성(Serviceability), 고장 격리(Fault Isolation), 전체 휴머노이드 시스템 통합(System Integration)을 향상시킬 수 있다.

## 01.04. Distributed Control

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

분산 제어(Distributed Control)는 수십 개의 관절, 센서, 전력 장치, 안전 기능이 물리적으로 분산된 신체 전체에서 동시에 동작해야 하는 휴머노이드 로봇의 핵심 아키텍처 원칙이다. 모든 제어 기능을 하나의 중앙 프로세서(Central Processor)에서 실행하는 대신 연산 기능을 관절 제어기(Joint Controller), 영역 제어기(Regional Controller), 실시간 컴퓨터(Real-Time Computer), 상위 AI 시스템(Higher-Level AI System)으로 분산한다. 각 계층은 요구되는 지연시간(Latency), 대역폭(Bandwidth), 기능적 책임(Functional Responsibility)에 적합한 작업을 수행한다.

가장 낮은 계층에서는 지능형 관절 제어기(Intelligent Joint Controller)가 물리적 액추에이터(Actuator)와 가까운 위치에서 동작한다. 관절 제어기는 모터 드라이버(Motor Driver), 위치 엔코더(Position Encoder), 토크 센서(Torque Sensor), 브레이크(Brake), 온도 센서(Temperature Sensor), 전류 측정 회로(Current Measurement Circuit)와 직접 인터페이스할 수 있다. 빠른 로컬 제어 루프(Local Control Loop)는 모든 측정값과 스위칭 판단을 로봇 전체 네트워크를 통해 전달하지 않고 모터 전류, 토크, 속도 또는 위치를 제어함으로써 통신 의존성을 줄이고 결정론적 동작(Deterministic Behavior)을 향상시킨다.

액추에이터 제어 루프(Actuator Control Loop)는 일반적으로 상위 수준의 모션 계획(Motion Planning)보다 훨씬 빠르게 동작하므로 로컬 제어(Local Control)는 특히 중요하다. 모터 전류 제어(Motor-Current Regulation)와 토크 제어(Torque Control)는 엄격하게 제한된 실행 주기를 요구할 수 있지만, 전신 궤적 생성(Whole-Body Trajectory Generation)은 상대적으로 낮은 주기로 동작할 수 있다. 이러한 기능을 분리하면 인지, 계획 또는 AI 작업의 처리 시간이 변동하더라도 고주파 제어(High-Frequency Control)를 안정적으로 유지할 수 있다. 결과적으로 이러한 계층 구조는 하드 실시간 동작(Hard Real-Time Behavior)을 연산 집약적인 지능 기능으로부터 분리한다.

영역 제어기(Regional Controller)는 팔, 다리, 손, 머리와 같은 공통 물리 서브시스템에 속하는 여러 관절을 협조 제어할 수 있다. 예를 들어 다리 제어기(Leg Controller)는 엉덩이(Hip), 무릎(Knee), 발목(Ankle), 발의 힘(Foot Force), 로컬 관성 정보(Local Inertial Information)를 결합한 후 요약된 상태를 전신 제어기(Whole-Body Controller)와 교환할 수 있다. 마찬가지로 팔 제어기(Arm Controller)는 어깨, 팔꿈치, 손목, 엔드 이펙터 인터페이스(End-Effector Interface)를 협조 제어하여 개별 관절과 중앙 모션 계획 사이의 중간 제어 계층(Intermediate Control Layer)을 형성할 수 있다.

전신 실시간 제어기(Whole-Body Real-Time Controller)는 이러한 분산 영역을 하나의 협조된 휴머노이드 움직임으로 통합한다. 동기화된 관절 및 센서 상태를 수신하고 로봇의 동적 상태(Dynamic Condition)를 추정하며 균형(Balance), 자세(Posture), 보행(Locomotion), 조작(Manipulation)을 위한 기준값(Reference)을 생성한다. 모든 모터의 스위칭 이벤트를 직접 제어하기보다는 일반적으로 토크, 속도, 위치, 임피던스(Impedance), 궤적 기준(Trajectory Reference)을 하위 제어기에 전달하고, 하위 제어기는 결정론적인 로컬 타이밍에 따라 명령을 실행한다.

이러한 계층적 분산(Hierarchical Distribution)은 보행 과정에서 특히 큰 장점을 제공한다. 균형은 발 접촉(Foot Contact), 관절 토크, 신체 방향(Body Orientation), 명령된 움직임 사이의 빠른 상호작용에 의존한다. 로컬 제어기는 액추에이터 안정성을 유지하고, 영역별 다리 제어기는 주변 관절을 협조 제어하며, 전신 제어기는 전체 자세와 동적 균형(Dynamic Balance)을 관리한다. 타이밍 요구사항에 따라 책임을 분산함으로써 모든 연산을 하나의 계산 병목(Computational Bottleneck)을 통해 처리하지 않고도 외란(Disturbance)에 신속하게 대응할 수 있다.

조작(Manipulation)도 유사한 원칙을 따르지만 정밀도와 센서 상호작용(Sensor Interaction)을 더욱 강조한다. 손 제어기(Hand Controller)는 다수의 소형 손가락 액추에이터를 협조 제어하면서 촉각 및 힘 측정값을 로컬에서 처리할 수 있다. 손목과 팔 제어기는 힘, 임피던스, 관절 궤적을 제어하고 중앙 제어기는 원하는 엔드 이펙터 동작(End-Effector Motion)을 결정할 수 있다. 이러한 분리는 중앙 제어 컴퓨터에 모든 저수준 센서 및 모터 트랜잭션(Transaction)을 집중시키지 않고도 다수의 액추에이터를 사용하는 정교한 조작(Dexterous Manipulation)을 확장할 수 있도록 한다.

분산 센싱(Distributed Sensing)은 분산 액추에이션(Distributed Actuation)을 보완한다. 엔코더, 토크 센서, 발 센서, 촉각 어레이(Tactile Array), 관성 측정 장치(IMU), 카메라 등의 장치는 서로 다른 주파수와 대역폭으로 데이터를 생성한다. 로컬 처리 노드(Local Processing Node)는 정보를 전달하기 전에 필터링(Filtering), 검증(Validation), 캘리브레이션 보상(Calibration Compensation), 통합(Aggregation), 특징 추출(Feature Extraction)을 수행할 수 있다. 그러나 안전 중요 또는 제어 중요 측정값은 예측 가능한 지연시간으로 사용할 수 있어야 하므로 전처리(Preprocessing)가 결정론적 제어나 고장 감지에 필요한 정보를 가려서는 안 된다.

통신 네트워크(Communication Network)는 분산 제어 계층을 연결하므로 제어 시스템 자체의 일부가 된다. 이더캣(EtherCAT)은 동기화된 액추에이터 네트워크를 위한 결정론적 통신(Deterministic Communication)을 제공할 수 있으며, CAN FD는 강건한 임베디드 제어 및 진단 트래픽을 지원할 수 있다. 기가비트 이더넷(Gigabit Ethernet)은 고대역폭 인지 및 컴퓨팅 데이터를 전송할 수 있고, ROS 2/DDS는 분산 소프트웨어 기능을 연결할 수 있다. 네트워크 선택은 각 제어 경로의 타이밍, 페이로드(Payload), 신뢰성, 안전 요구사항을 반영해야 한다.

물리적으로 분산된 제어기들이 하나의 협조된 시스템처럼 동작해야 하므로 시간 동기화(Time Synchronization)는 필수적이다. 서로 다른 관절 또는 신체 존(Body Zone)에서 수집된 측정값을 올바르게 결합하려면 공통 시간 기준(Common Temporal Reference)이 필요하다. PTP 또는 이에 상응하는 동기화 메커니즘은 제어기와 컴퓨터 사이의 클록(Clock)을 정렬할 수 있다. 정확한 타임스탬프(Timestamp)는 센서 융합(Sensor Fusion), 상태 추정(State Estimation), 협조 궤적 실행(Coordinated Trajectory Execution), 이벤트 재구성(Event Reconstruction), 명령과 물리적 반응 사이의 인과관계 분석을 지원한다.

제어 아키텍처는 각 기능의 명확한 제어 권한(Control Ownership)도 정의해야 한다. 여러 제어기가 중재(Arbitration) 없이 동일한 액추에이터에 독립적으로 명령을 전달할 수 있다면 서로 충돌하는 명령으로 인해 불안정하거나 위험한 동작이 발생할 수 있다. 따라서 각 제어 모드(Control Mode)는 명확한 권한, 상태 전환(State Transition), 명령 우선순위(Command Priority)를 가져야 한다. 상위 제어기는 동작을 요청할 수 있지만, 하위 제어기는 액추에이터 제한과 로컬 보호 기능을 적용하여 추상화(Abstraction) 과정에서도 필수적인 물리적 제약이 유지되도록 해야 한다.

안전 감독(Safety Supervision)은 필요한 경우 정상적인 분산 제어를 무시하고 개입할 수 있을 정도로 충분한 독립성을 유지해야 한다. 비상 정지 신호(Emergency-Stop Signal), 충돌 이벤트(Collision Event), 과도한 토크, 통신 손실, 엔코더 불일치, 열적 고장(Thermal Fault), 전력 이상은 즉각적인 로컬 대응을 요구할 수 있다. 관절 제어기는 중앙 응답을 기다리기 전에 해당 액추에이터를 비활성화하거나 제한할 수 있으며, 영역 및 시스템 수준의 안전 제어기는 제어 정지(Controlled Stop), 자세 안정화(Posture Stabilization), 제동(Braking), 전력 격리(Power Isolation)와 같은 보다 광범위한 대응을 협조할 수 있다.

고장 격리(Fault Containment)는 분산 제어의 또 다른 중요한 장점이다. 하나의 관절 제어기 고장이 다른 모든 서브시스템의 비제어 동작(Uncontrolled Behavior)으로 자동적으로 이어져서는 안 된다. 로컬 고장 감지(Local Fault Detection)는 비정상 전류, 온도, 센서 불일치, 통신 타임아웃(Communication Timeout)을 식별하고 영향을 받은 액추에이터를 정의된 안전 상태(Safe State)로 전환할 수 있다. 이후 상위 제어기는 로봇이 성능 저하 상태로 계속 동작할지, 자세를 유지할지, 제어된 복구(Controlled Recovery)를 수행할지, 또는 완전한 정지를 수행할지를 결정할 수 있다.

중복성(Redundancy)은 기능의 중요도(Functional Criticality)에 따라 선택적으로 적용할 수 있다. 균형 관련 센서, 중앙 실시간 컴퓨팅, 통신 경로 또는 안전 제어기는 중복 자원(Redundant Resource)을 요구할 수 있지만 중요도가 낮은 주변 기능은 일시적인 손실을 허용할 수 있다. 분산 아키텍처는 로봇의 모든 구성 요소를 이중화하지 않고도 중요 제어 경로를 보호할 수 있으므로 이러한 선택적 중복성을 실용적으로 구현할 수 있다. 핵심 과제는 중복성 관리(Redundancy Management) 자체가 결정론적이며 진단 가능한 상태를 유지하도록 하는 것이다.

분산 제어는 확장성(Scalability)도 향상시킨다. 손가락 수를 증가시키거나 새로운 센서 어레이를 추가하고, 액추에이터 모듈을 변경하거나 새로운 신체 존을 도입하더라도 중앙 컴퓨터가 모든 새로운 전기 인터페이스를 직접 관리할 필요는 없다. 로컬 제어기가 장치별 복잡성(Device-Specific Complexity)을 흡수하고 표준화된 상태와 명령을 상위 계층에 제공할 수 있으므로 서로 다른 휴머노이드 구성이 공통적인 시스템 수준 제어 프레임워크(System-Level Control Framework)를 공유할 수 있다.

진단(Diagnostics) 역시 동일한 계층 구조를 자연스럽게 따른다. 관절 제어기는 액추에이터 수준의 상태를 모니터링하고, 영역 제어기는 서브시스템의 동작을 관찰하며, 중앙 진단 시스템(Central Diagnostics)은 로봇 전체의 고장을 상호 연관하여 분석한다. 이벤트 로그(Event Log)는 여러 분산 노드에서 발생한 고장을 재구성할 수 있도록 동기화된 타임스탬프를 사용해야 한다. 원격 진단(Remote Diagnostics), 디지털 트윈(Digital Twin), 예측 유지보수(Predictive Maintenance)는 장기간 운용 과정에서 모터 전류, 관절 온도, 통신 품질, 센서 상태, 제어기 성능의 변화 추세를 분석할 수 있다.

소프트웨어 아키텍처(Software Architecture)는 결정론적 제어와 상위 수준 지능(Higher-Level Intelligence) 사이의 분리를 유지해야 한다. AI 컴퓨터는 인지, 파운데이션 모델(Foundation Model), 비전-언어 모델(VLM), 비전-언어-행동 모델(VLA), 계획, 에이전트(Agent) 기능을 실행할 수 있지만, 이러한 출력은 일반적으로 목표(Goal), 궤적(Trajectory), 제약조건(Constraint), 검증된 행동 요청(Validated Action Request)의 형태로 물리적 제어 계층에 입력되어야 한다. 실시간 제어기는 이러한 의도를 동기화된 물리적 움직임으로 변환하며, 안전 계층은 명령이 허용 가능한 운용 범위(Allowable Operating Boundary) 내에 있는지를 검증한다.

따라서 가장 효과적인 분산 제어 아키텍처는 로컬 자율성(Local Autonomy)과 전역 협조(Global Coordination)를 결합한다. 관절 제어기는 빠르고 결정론적인 액추에이션을 제공하고, 영역 제어기는 신체 서브시스템을 협조하며, 전신 컴퓨터(Whole-Body Computer)는 균형과 움직임을 관리하고, AI 컴퓨터는 지능형 행동(Intelligent Behavior)을 생성하며, 독립적인 안전 메커니즘(Independent Safety Mechanism)은 전체 계층을 감독한다. 이러한 계층의 결합을 통해 휴머노이드는 타이밍 결정성(Timing Determinism), 고장 격리, 진단성(Diagnosability), 안전한 물리적 상호작용을 유지하면서 반응성이 높은 움직임과 확장 가능한 지능을 구현할 수 있다.

## 01.05. Safety Architecture

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 로봇의 안전 아키텍처(Safety Architecture)는 고장 상황에서도 제어된 동작을 유지하면서 사람, 로봇, 주변 환경을 보호해야 한다. 휴머노이드는 강력한 액추에이터(Actuator), 저장된 전기 에너지(Stored Electrical Energy), 관절형 메커니즘(Articulated Mechanism), 자율 의사결정(Autonomous Decision Making), 인간과의 근접 상호작용(Close Human Interaction)을 결합하므로 안전을 하나의 비상 기능만으로 구현할 수 없다. 안전은 전기, 기계, 컴퓨팅, 통신, 소프트웨어 계층 전체에 걸쳐 분산되어 구현되어야 한다.

안전 아키텍처는 시스템 수준(System Level)의 위험 인식(Hazard Awareness)에서 시작한다. 잠재적인 위험에는 의도하지 않은 관절 움직임, 과도한 토크, 균형 상실, 충돌, 끼임 또는 협착, 배터리 고장, 전기적 단락, 과열, 통신 장애, 센서 오류, 잘못된 제어 명령 등이 포함된다. 각 위험에는 감지 메커니즘(Detection Mechanism)과 정의된 대응(Defined Response)이 연결되어야 하며, 이를 통해 로봇이 예측할 수 없는 물리적 동작을 발생시키는 대신 제어된 상태로 전환되도록 해야 한다.

비상 정지(Emergency Stop)는 가장 기본적인 보호 기능 중 하나이다. 비상 정지 요청(Emergency-Stop Request)은 정상적인 동작 명령을 무시하고 상위 AI 동작(High-Level AI Behavior)과 독립적으로 사전에 정의된 안전 대응(Safe Response)을 시작할 수 있어야 한다. 로봇의 상태에 따라 액추에이터 전력을 즉시 차단하는 것이 항상 가장 안전한 방법은 아니며, 지지력을 잃은 휴머노이드가 쓰러질 수도 있다. 따라서 아키텍처는 비상 개입(Emergency Intervention)과 비제어 전력 차단(Uncontrolled Power Removal)을 구분하고 정지, 제동, 안정화를 협조해야 한다.

안전 정지(Safe Stopping)는 운용 상태에 따라 서로 다른 전략을 필요로 할 수 있다. 정상적으로 서 있는 로봇은 먼저 관절 토크를 감소시키면서 안정적인 자세로 이동할 수 있지만, 심각한 전기적 고장에서는 신속한 전력 격리(Power Isolation)가 필요할 수 있다. 조작(Manipulation) 중에는 제어 정지(Controlled Stop)를 수행하면서 운반 중인 물체가 예기치 않게 떨어지는 것을 방지해야 할 수 있다. 따라서 안전 동작은 모든 이벤트에 동일한 정지 절차를 적용하기보다 로봇 전체의 물리적 상태를 고려해야 한다.

관절 수준 보호(Joint-Level Protection)는 첫 번째 분산 안전 계층(Distributed Safety Layer)을 형성한다. 지능형 관절 제어기(Intelligent Joint Controller)는 모터 전류, 토크, 속도, 위치, 엔코더 일관성(Encoder Consistency), 온도, 통신 상태, 모터 드라이버 고장(Motor-Driver Fault)을 모니터링할 수 있다. 로컬 한계(Local Limit)를 초과하면 제어기는 토크를 제한하거나 동작을 정지하고, 브레이크를 작동하거나 드라이브를 비활성화할 수 있다. 로컬 대응(Local Reaction)은 네트워크 지연시간에 대한 의존성을 감소시키고 모든 비정상적인 액추에이터 상태가 중앙 컴퓨터의 판단을 기다리는 상황을 방지한다.

영역 안전 감독(Regional Safety Supervision)은 서로 연관된 여러 관절로 보호 기능을 확장한다. 팔, 손 또는 다리 제어기는 개별 관절의 동작이 해당 서브시스템의 예상 움직임과 일치하는지를 평가할 수 있다. 다리 제어기(Leg Controller)는 지지 또는 균형을 위협하는 상태를 감지할 수 있으며, 팔 제어기(Arm Controller)는 조작 과정에서 비정상적인 힘을 식별할 수 있다. 영역 감독을 통해 고장이 전신 불안정(Whole-Body Instability)으로 전파되기 전에 물리적인 상황을 고려하여 해석할 수 있다.

전신 안전 제어(Whole-Body Safety Control)는 휴머노이드 전체의 결합된 상태를 평가한다. 관절 상태, 발의 힘(Foot Force), 관성 측정값(Inertial Measurement), 접촉 정보(Contact Information), 액추에이터 가용성(Actuator Availability), 동작 명령을 이용하여 균형과 자세가 복구 가능한지를 판단할 수 있다. 관절이나 센서를 사용할 수 없게 되면 제어기는 운전을 계속할 수 있는지, 움직임을 제한해야 하는지, 또는 안정적인 상태로 제어된 전환(Controlled Transition)을 수행해야 하는지를 결정해야 한다.

충돌 안전(Collision Safety)은 휴머노이드가 사람을 위해 설계된 환경에서 동작하기 때문에 특히 중요하다. 인지 센서(Perception Sensor)는 접촉 전에 장애물과 사람을 식별할 수 있으며, 토크 센서, 모터 전류 추정(Motor-Current Estimation), 촉각 센싱(Tactile Sensing), 힘 센서(Force Sensor)는 예상하지 못한 물리적 상호작용을 감지할 수 있다. 외부 인지가 모든 접촉을 식별하지 못할 수 있고 접촉 센싱만으로는 충분한 예방 거리를 확보할 수 없기 때문에 이러한 메커니즘은 상호 보완적인 보호 계층을 제공한다.

힘 및 토크 제한(Force and Torque Limitation)은 물리적 제어 계층과 가까운 위치에서 적용되어야 한다. 상위 수준의 계획(Planning) 또는 AI 시스템이 움직임을 요청할 수 있지만, 로컬 및 실시간 제어기는 액추에이터 명령이 허용된 위치, 속도, 가속도, 토크, 전력 경계 내에서 유지되도록 해야 한다. 따라서 소프트웨어에서 생성된 움직임은 모터 드라이브에 전달되기 전에 결정론적 제약 적용(Deterministic Constraint Enforcement)을 거쳐야 하며, 잘못된 상위 수준 명령이 제한되지 않은 물리적 힘으로 직접 변환되는 것을 방지해야 한다.

AI와 안전 제어(Safety Control) 사이의 기능적 독립성(Functional Independence)은 필수적이다. 비전-언어 모델(Vision-Language Model), 비전-언어-행동 모델(Vision-Language-Action Model), 파운데이션 모델(Foundation Model), 플래너(Planner), 에이전트(Agent)는 목표와 행동을 생성할 수 있지만, 안전 제한을 임의로 비활성화하거나 보호된 제어 경로(Protected Control Path)를 직접 우회할 수 있는 무제한 권한을 가져서는 안 된다. AI 출력은 요청된 행동(Requested Behavior)으로 취급되어야 하며 물리적 환경에서 실행되기 전에 모션 제어 및 안전 계층에서 검증되어야 한다.

분산 제어기(Distributed Controller)가 지속적인 정보 교환에 의존하므로 통신 안전(Communication Safety)도 필요하다. 메시지 손실, 과도한 지연시간, 데이터 손상, 중복 명령, 동기화 오류, 네트워크 분할(Network Partitioning)은 감지되지 않을 경우 위험한 상태를 발생시킬 수 있다. 따라서 제어 인터페이스는 시퀀스 모니터링(Sequence Monitoring), 타임아웃 감독(Timeout Supervision), 타당성 검사(Plausibility Check), 하트비트 메시지(Heartbeat Message), 오류 검출(Error Detection), 통신 품질이 허용 수준 이하로 떨어졌을 때의 정의된 폴백 동작(Fallback Behavior)과 같은 메커니즘을 사용해야 한다.

로봇의 서로 다른 부분에서 얻은 상태 정보가 일관된 물리적 시점을 나타내야 하므로 시간 동기화(Time Synchronization)는 안전에 직접적으로 기여한다. 관절 위치, 관성 측정 장치(IMU)의 측정값, 발의 힘, 카메라 관측, 안전 이벤트는 타임스탬프(Timestamp)가 크게 다를 경우 잘못 해석될 수 있다. 동기화된 시간 기준(Synchronized Time Base)을 사용하면 제어기가 움직임과 센서 이벤트를 정확하게 연관시킬 수 있으며, 시간 정확도가 허용 한계를 벗어날 경우 동기화 고장(Synchronization Fault) 자체도 감지할 수 있어야 한다.

전기 안전(Electrical Safety)은 배터리에 저장되고 액추에이터로 전달되는 상당한 에너지를 관리해야 한다. 전력 아키텍처(Power Architecture)는 과전류(Overcurrent), 과전압(Overvoltage), 저전압(Undervoltage), 단락(Short Circuit), 절연 문제(Insulation Problem), 비정상 온도 등의 전기적 고장을 감지해야 한다. 보호 장치(Protection Device)와 전력 분배 장치(Power Distribution Unit)는 필요한 경우 영향을 받은 분기를 격리하면서 시스템 수준의 위험으로 전체 정지가 필요한 경우를 제외하고 로컬 고장이 정상적인 영역까지 불필요하게 비활성화하지 않도록 해야 한다.

열 보호(Thermal Protection)는 전기 및 동작 안전과 밀접하게 연결된다. 모터, 모터 드라이브, 배터리, 프로세서, GPU, 전력 변환기(Power Converter)는 지속적인 부하에서 온도가 상승할 수 있다. 온도 모니터링(Temperature Monitoring)은 경고 임계값(Warning Threshold), 성능 디레이팅(Performance Derating), 토크 제한(Torque Limitation), 작업 부하 감소(Workload Reduction), 보호 정지(Protective Shutdown)를 지원해야 한다. 가능한 경우 점진적 개입(Progressive Intervention)이 바람직하며, 이를 통해 열적 한계로 인해 기능을 갑자기 제거해야 하기 전에 로봇이 안전 상태에 도달할 수 있다.

중복성(Redundancy)은 모든 구성 요소를 동일하게 복제하는 방식이 아니라 고장 결과의 심각성에 따라 적용해야 한다. 중요한 균형 센서, 안전 제어기, 통신 경로, 상태 추정 입력(State-Estimation Input)은 중복되거나 서로 다른 원리를 사용하는 정보원(Diverse Information Source)을 필요로 할 수 있다. 아키텍처는 중복 채널 사이의 불일치를 감지하고 어떤 정보가 여전히 신뢰 가능한지를 판단해야 한다. 중복성은 공통 원인 고장(Common-Cause Failure)과 채널 간 불일치를 관리하는 로직까지 함께 고려할 때 효과적으로 동작한다.

고장 격리(Fault Containment)는 국부적인 고장이 휴머노이드 전체로 전파되는 것을 방지한다. 고장 난 센서, 관절 제어기, 네트워크 구간(Network Segment), 전력 분기(Power Branch)는 가능한 경우 격리되어야 하며, 영향을 받지 않은 서브시스템은 계속 제어된 상태를 유지해야 한다. 이를 위해서는 존(Zone)과 제어 도메인(Control Domain) 사이에 명확한 전기 및 소프트웨어 경계가 필요하다. 조널 아키텍처(Zonal Architecture)는 개별 신체 영역이 중앙 안전 감독(Central Safety Supervision)과의 통신을 유지하면서 고장을 감지, 보고, 격리할 수 있도록 지원한다.

충분한 안전 기능이 유지되는 경우 즉각적인 전체 정지보다 단계적 성능 저하(Graceful Degradation)가 더 적절할 수 있다. 중요도가 낮은 센서를 잃은 경우 속도를 낮추어 운전을 계속할 수 있으며, 팔 관절 하나가 고장 난 경우 모든 컴퓨팅 기능을 정지시키지 않고 조작 기능만 중단해야 할 수 있다. 그러나 성능 저하 운전(Degraded Operation)은 사전에 정의된 안전 규칙을 따라야 한다. 일부 기능이 남아 있다는 이유만으로 남은 시스템 구성이 명확하게 제어 가능한 상태를 유지할 수 없는 상황에서 운전을 계속해서는 안 된다.

진단 및 이벤트 로깅(Diagnostics and Event Logging)은 안전 관련 동작을 이해하기 위한 근거를 제공한다. 고장 코드(Fault Code), 관절 상태, 전력 조건, 온도, 네트워크 상태, 안전 명령, 제어기 상태 전환(Controller Transition)은 동기화된 타임스탬프와 함께 기록되어야 한다. 이러한 기록은 고장 재구성(Fault Reconstruction), 검증(Validation), 현장 유지보수(Field Maintenance), 안전 메커니즘 개선을 지원한다. 원격 진단(Remote Diagnostics)과 디지털 트윈(Digital Twin) 시스템은 운용 시간과 다수의 로봇에 걸쳐 반복적으로 발생하는 이상 상태를 추가로 연관 분석할 수 있다.

소프트웨어 및 펌웨어 업데이트(Software and Firmware Update) 과정에서도 안전이 유지되어야 한다. 손상되거나 불완전한 업데이트로 인해 안전 중요 제어기(Safety-Critical Controller)가 정의되지 않은 상태에 남아서는 안 된다. 안전한 업데이트 메커니즘(Secure Update Mechanism)은 무결성 검사(Integrity Checking), 버전 호환성 관리(Version Compatibility Management), 제어된 활성화(Controlled Activation), 롤백 기능(Rollback Capability), 중요 및 비중요 소프트웨어 도메인의 분리를 제공해야 한다. 업데이트가 정상적으로 완료되지 못할 경우에도 안전 기능은 유지되거나 사전에 정의된 보호 상태(Protected State)로 전환되어야 한다.

따라서 전체 안전 아키텍처는 정상적인 휴머노이드 동작을 둘러싸는 독립적이면서도 긴밀하게 통합된 계층 구조를 형성한다. 로컬 관절 보호(Local Joint Protection)는 즉각적인 액추에이터 고장에 대응하고, 영역 감독(Regional Supervision)은 서브시스템 동작을 해석하며, 전신 안전(Whole-Body Safety)은 자세와 안정성을 유지한다. 전기 보호(Electrical Protection)는 저장 에너지를 제어하고, 시스템 수준 메커니즘(System-Level Mechanism)은 비상 대응을 협조한다. AI 및 자율 기능은 이러한 안전 경계를 대체하는 것이 아니라 그 내부에서 동작한다.

잘 설계된 휴머노이드 안전 아키텍처는 궁극적으로 고장과 불확실성(Uncertainty)을 예측 가능한 물리적 대응으로 변환한다. 감지(Detection), 검증(Validation), 고장 격리, 제어 정지, 전력 격리, 중복성, 진단, 복구(Recovery)는 분산된 로봇 전체에서 상호 협력해야 한다. 목표는 이상이 발생할 때마다 단순히 모든 움직임을 정지시키는 것이 아니라, 현실적으로 발생 가능한 모든 고장이 제어 가능성(Controllability), 진단 가능성(Diagnosability), 주변 사람에 대한 보호를 유지하면서 달성 가능한 가장 안전한 상태(Safest Achievable State)로 이어지도록 하는 것이다.
