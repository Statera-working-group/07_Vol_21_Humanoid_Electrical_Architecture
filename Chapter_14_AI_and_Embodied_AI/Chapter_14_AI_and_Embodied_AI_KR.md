**Volume 21. Humanoid Electrical Architecture**

# Chapter 14. AI and Embodied AI

## 14.01. VLM Architecture

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

비전-언어 모델(Vision-Language Model, VLM) 아키텍처는 휴머노이드 로봇에서 시각 인식(Visual Perception)과 언어 기반 추론(Language-based Reasoning)을 연결하는 의미론적 인터페이스(Semantic Interface)를 제공한다. 객체 라벨(Object Label)이나 기하학적 검출(Geometric Detection)에서 처리가 끝나는 기존 비전 파이프라인(Vision Pipeline)과 달리, VLM은 카메라 관측(Camera Observation)을 개념, 관계, 명령 및 문맥적 지식(Contextual Knowledge)과 연결할 수 있는 표현으로 변환한다. 이를 통해 로봇은 무엇이 보이는지를 인식하는 것뿐만 아니라 관측된 장면이 현재 작업에서 무엇을 의미하는지도 해석할 수 있다.

휴머노이드 아키텍처(Humanoid Architecture)에서 VLM은 일반적으로 실시간 센싱 및 제어 계층(Real-time Sensing and Control Layer)의 상위에서 동작한다. 카메라, 깊이 센서(Depth Sensor), 라이다(LiDAR), 마이크 및 고유수용성 센서(Proprioceptive Sensor)는 물리 세계의 관측 데이터를 지속적으로 생성하며, 인식 컴퓨터(Perception Computer)는 동기화, 캘리브레이션(Calibration), 필터링 및 기본 특징 추출(Feature Extraction)을 수행한다. 선택된 시각 정보는 AI 컴퓨터(AI Computer) 또는 GPU 서브시스템(GPU Subsystem)으로 전달되며, 여기에서 VLM은 결정론적 관절 제어 루프(Deterministic Joint-control Loop)를 방해하지 않고 상위 수준의 의미론적 해석을 수행한다.

시각 프런트엔드(Visual Front End)는 일반적으로 트랜스포머(Transformer) 또는 이와 유사한 심층 신경망(Deep Neural Architecture)을 기반으로 하는 이미지 또는 비디오 인코더(Image or Video Encoder)를 포함한다. RGB 프레임, 잘라낸 관심 영역(Cropped Region), 깊이 정보가 강화된 이미지(Depth-enhanced Image), 시간적으로 샘플링된 비디오 시퀀스(Video Sequence)는 압축된 시각 토큰(Visual Token)으로 변환된다. 이러한 토큰은 객체, 사람, 도구, 표면, 공간적 관계 및 활동에 관한 의미 정보를 유지하면서 언어 중심 추론 구성요소가 처리해야 하는 원시 센서 데이터(Raw Sensor Data)의 양을 감소시킨다.

투영 또는 멀티모달 정렬 계층(Projection or Multimodal Alignment Layer)은 시각 인코더(Visual Encoder)를 언어 모델(Language Model)에 연결한다. 이 계층의 목적은 시각 특징(Visual Feature)을 텍스트 토큰(Text Token)과 함께 해석할 수 있는 임베딩 공간(Embedding Space)에 매핑하는 것이다. 따라서 언어 모델은 작업자 명령, 카메라 관측, 작업 이력(Task History), 로봇 상태 및 검색된 지식(Retrieved Knowledge)의 조합을 기반으로 추론할 수 있다. 이러한 정렬 계층은 인식과 언어가 서로 다른 데이터 분포(Data Distribution)에서 생성되지만 하나의 공통 추론 과정에 참여해야 하기 때문에 매우 중요하다.

휴머노이드 로봇에서는 물리적 상호작용(Physical Interaction)이 시간에 따라 변화하므로 단일 이미지만으로 충분하지 않은 경우가 많다. 따라서 VLM 아키텍처는 프레임 시퀀스(Frame Sequence), 이벤트 기반 관측(Event-triggered Observation) 또는 압축 비디오 표현(Compressed Video Representation)을 통한 시간적 시각 문맥(Temporal Visual Context)을 지원해야 한다. 시간적 문맥을 활용하면 시스템은 정적인 구성과 진행 중인 행동을 구분하고, 객체의 이동 여부를 판단하며, 사람이 접근하고 있는지를 인식하고, 이전 로봇 행동 이후 환경이 어떻게 변화했는지를 이해할 수 있다.

언어 인터페이스(Language Interface)는 시각 파이프라인에 작업 수준의 의미론적 문맥(Task-level Semantic Context)을 제공한다. 예를 들어 "작업대 옆에 있는 빨간색 용기를 찾아라" 또는 "작업자가 해당 구역을 벗어났는지 확인하라"와 같은 명령은 어떤 시각 특징이 중요한지를 제한한다. VLM은 장면의 모든 요소를 동일한 우선순위로 처리하는 대신 언어적 문맥(Linguistic Context)을 활용하여 작업과 관련된 객체, 속성, 관계 및 이벤트의 의미론적 해석에 집중할 수 있다. 이를 통해 로봇의 목표에 의해 조건화되는 인식 과정(Goal-conditioned Perception)을 구현할 수 있다.

VLM 출력(Output)은 직접적인 액추에이터 명령(Actuator Command)과 명확하게 분리되어야 한다. 모델은 객체 참조(Object Reference), 의미론적 장면 설명(Semantic Scene Description), 공간적 가설(Spatial Hypothesis), 작업 조건, 신뢰도 정보(Confidence Information) 또는 후보 목표(Candidate Goal)를 생성할 수 있지만, 이러한 출력은 물리적 실행 전에 하위의 계획 및 검증 계층(Planning and Validation Layer)을 거쳐야 한다. 이러한 분리는 확률적 멀티모달 추론(Probabilistic Multimodal Reasoning)이 결정론적 모션 제어(Deterministic Motion Control), 충돌 회피(Collision Avoidance), 관절 한계(Joint Limit), 힘 제한(Force Constraint) 또는 기능 안전(Functional Safety) 메커니즘을 우회하는 것을 방지한다.

그라운딩(Grounding)은 언어적 개념이 궁극적으로 물리적 객체와 연결되어야 하기 때문에 휴머노이드 응용에서 특히 중요하다. "왼쪽 테이블 위의 렌치"와 같은 표현은 조작(Manipulation)이 시작되기 전에 관측 가능한 영역, 추적 객체(Tracked Object), 깊이 추정값(Depth Estimate) 또는 월드 모델 엔티티(World-model Entity)와 연결되어야 한다. 따라서 아키텍처에서는 VLM 토큰과 세그멘테이션 마스크(Segmentation Mask), 바운딩 영역(Bounding Region), 객체 트랙(Object Track), 3차원 좌표(3D Coordinate), 장면 그래프 식별자(Scene-graph Identifier)와 같은 인식 출력 사이의 명시적인 연결을 제공하는 것이 유리하다.

VLM은 인식과 로봇의 월드 표현(World Representation)을 연결하는 의미론적 브리지(Semantic Bridge) 역할도 수행할 수 있다. 저수준 인식(Low-level Perception)은 깊이, 자세(Pose), 움직임 및 점유 상태(Occupancy)와 같은 측정 가능한 특성을 결정하는 반면, VLM은 소유 관계, 어포던스(Affordance), 작업 관련성(Task Relevance), 예상 기능과 같은 의미론적 관계를 제공한다. 이러한 표현을 결합하면 로봇은 기하학적 엔티티(Geometric Entity)가 상위 수준 추론 모듈에서 질의할 수 있는 언어 기반 개념(Language-addressable Concept)과 연결된 더욱 풍부한 월드 모델(World Model)을 유지할 수 있다.

메모리(Memory)는 VLM의 기능을 즉각적인 인식 범위 이상으로 확장한다. 단기 멀티모달 메모리(Short-term Multimodal Memory)는 최근 관측, 명령, 대화 및 완료된 행동을 유지할 수 있으며, 장기 저장소(Long-term Store)는 지도, 객체 설명, 절차 및 작업 지식을 포함할 수 있다. 검색 메커니즘(Retrieval Mechanism)은 현재 상황과 관련된 문맥만 제공함으로써 불필요한 모델 입력을 줄이는 동시에, 휴머노이드가 현재의 관측을 이전 작업 과정에서 획득한 정보 또는 외부 지식 시스템(External Knowledge System)을 통해 제공된 정보와 연결할 수 있도록 한다.

휴머노이드 로봇은 제한된 컴퓨팅 자원과 전력 예산(Compute and Power Budget)에서 동작하므로 VLM 실행에는 신중한 자원 분할(Resource Partitioning)이 필요하다. 고해상도 카메라는 대규모 멀티모달 모델(Large Multimodal Model)이 지속적으로 처리할 수 있는 양보다 훨씬 많은 데이터를 생성할 수 있으므로, 프레임 선택(Frame Selection), 관심 영역 추출(Region-of-interest Extraction), 이미지 크기 조정(Image Resizing), 토큰 감소(Token Reduction), 이벤트 기반 추론(Event-driven Inference)이 실용적인 아키텍처 메커니즘이 된다. 경량 인식(Lightweight Perception)은 지속적으로 실행하고, 비용이 높은 VLM 추론은 의미론적 해석 또는 언어 그라운딩(Language Grounding)이 필요한 경우에 활성화할 수 있다.

컴퓨팅 아키텍처(Computing Architecture)는 VLM 워크로드(Workload)를 하드 실시간 제어(Hard Real-time Control)로부터 격리해야 한다. GPU 자원은 시각 인코딩(Visual Encoding), 멀티모달 어텐션(Multimodal Attention), 언어 추론(Language Inference), 임베딩 연산(Embedding Operation)을 수행할 수 있으며, 전용 CPU, MCU 또는 실시간 프로세서(Real-time Processor)는 모터 제어 및 안전 기능을 유지한다. 따라서 스케줄링(Scheduling), 메모리 대역폭(Memory Bandwidth), 열적 한계(Thermal Limit), 추론 지연(Inference Latency), 모델 크기를 함께 고려하여 의미론적 AI 워크로드가 균형 제어(Balance Control), 액추에이터 통신 또는 기타 시간 결정적 로봇 기능을 불안정하게 만들지 않도록 해야 한다.

통신 인터페이스(Communication Interface)는 VLM을 인식, 월드 모델링(World Modeling), 작업 계획(Task Planning), 감독 소프트웨어(Supervisory Software)와 연결한다. 고대역폭 센서 스트림(High-bandwidth Sensor Stream)은 일반적으로 이더넷 계열 네트워크(Ethernet-class Network) 또는 로컬 고속 인터페이스를 통해 전달되며, 의미론적 결과는 로보틱스 미들웨어(Robotics Middleware)를 통해 구조화된 메시지(Structured Message) 형태로 교환할 수 있다. 멀티모달 추론이 물리적 상황을 재구성할 때 시각 관측, 로봇 자세, 관절 상태 및 작업 이벤트가 호환 가능한 타임스탬프(Timestamp)를 참조해야 하므로 시간 동기화(Time Synchronization) 역시 중요하다.

신뢰성(Reliability)을 확보하려면 불확실성(Uncertainty)을 명시적으로 처리해야 한다. VLM은 특히 관측 대상이 가려지거나, 모호하거나, 조명이 부족하거나, 학습 데이터 분포(Training Distribution)를 벗어난 경우 물리적으로 정확하지 않지만 그럴듯한 설명을 생성할 수 있다. 따라서 로봇 소프트웨어는 중요한 의미론적 출력에 신뢰도, 출처 정보(Provenance), 타임스탬프 및 그라운딩 근거(Grounding Evidence)를 연결해야 한다. 중요한 판단은 물리적 행동에 영향을 미치기 전에 결정론적 인식, 중복 센서(Redundant Sensor), 기하학적 제약(Geometric Constraint) 또는 추가 관측을 통해 교차 검증할 수 있다.

보안(Security)과 개인정보 보호(Privacy) 역시 중요한 아키텍처 고려사항이다. 휴머노이드 VLM은 사람, 문서, 디스플레이, 작업 공간 또는 사적인 환경이 포함된 이미지를 처리할 수 있다. 로컬 추론(Local Inference)은 민감한 시각 데이터의 불필요한 외부 전송을 줄일 수 있으며, 엣지-클라우드 통합(Edge-cloud Integration)은 모델 업데이트(Model Update), 비실시간 분석(Non-real-time Analysis) 또는 계산 비용이 높은 추론을 위해 선택적으로 사용할 수 있다. 인증(Authentication), 암호화 통신(Encrypted Communication), 접근 제어(Access Control), 로깅(Logging), 통제된 데이터 보존(Controlled Retention)은 멀티모달 정보가 로봇 외부로 전달되는 경우 함께 적용되어야 한다.

VLM은 궁극적으로 더 높은 수준의 체화 지능(Embodied Intelligence)을 위한 인식 및 언어 기반 토대를 형성한다. VLM의 역할은 동기화된 물리적 관측을 그라운딩된 의미론적 표현(Grounded Semantic Representation)으로 변환하여 비전-언어-행동 모델(Vision-Language-Action Model, VLA), 에이전트(Agent), 플래너(Planner), 파운데이션 모델(Foundation Model), 피지컬 AI 런타임(Physical AI Runtime)이 활용할 수 있도록 하는 것이다. 이러한 계층 구조에서 VLM은 로봇이 무엇을 보고 있으며 그 관측이 무엇을 의미하는지를 해석하고, 이후의 아키텍처 계층은 어떤 목표를 추구할 것인지, 어떤 행동이 적절한지, 그리고 그 행동을 어떻게 안전하게 실행할 것인지를 결정한다.

## 14.02. VLA Architecture

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

비전-언어-행동(Vision-Language-Action, VLA) 아키텍처는 시각적 관측, 언어 명령, 로봇 상태 및 행동 표현을 하나의 통합된 체화 AI(Embodied AI) 프레임워크 내에서 연결함으로써 멀티모달 인식(Multimodal Perception)과 추론을 물리적 행동으로 확장한다. 휴머노이드 로봇에서 VLA는 로봇이 관측한 내용을 해석하고, 의도된 작업을 이해하며, 현재 상황을 추론하고, 실행 가능한 로봇 행동으로 변환될 수 있는 행동을 제안하는 상위 수준 정책 인터페이스(High-level Policy Interface) 역할을 한다.

VLA는 일반적으로 결정론적 모션 제어(Deterministic Motion Control) 및 기능 안전(Functional Safety) 계층의 상위에서 동작한다. 카메라와 기타 인식 센서는 환경 관측 정보를 제공하고, 관절 인코더(Joint Encoder), 토크 센서(Torque Sensor), 힘 센서(Force Sensor), 관성 측정 장치(IMU), 촉각 센서(Tactile Sensor), 액추에이터 피드백(Actuator Feedback)은 로봇 내부의 물리적 상태를 나타낸다. 언어 명령은 작업 의도(Task Intent)를 제공한다. VLA는 이러한 이질적인 입력을 결합하여 안정적인 물리적 실행을 담당하는 실시간 제어기를 직접 대체하지 않으면서 적절한 행동 목표를 결정한다.

시각 정보는 RGB, 깊이(Depth) 또는 시간적으로 샘플링된 관측을 압축된 시각 토큰(Visual Token)으로 변환하는 이미지 또는 비디오 인코더(Image or Video Encoder)를 통해 입력된다. 이러한 표현은 작업과 관련된 객체, 사람, 도구, 작업 공간 및 환경 조건을 나타낸다. 실제 휴머노이드 시스템에서 인식 전처리(Perception Preprocessing)는 데이터가 VLA에 도달하기 전에 동기화, 캘리브레이션(Calibration), 세그멘테이션(Segmentation), 추적(Tracking), 관심 영역 선택(Region-of-interest Selection) 또는 특징 추출(Feature Extraction)을 수행하여 체화 추론(Embodied Reasoning)에 필요한 정보를 유지하면서 계산 부하를 줄일 수 있다.

언어 명령은 작업 목표, 제약 조건, 객체 참조 및 문맥적 관계를 표현하는 형태로 인코딩된다. "용기를 집어 선반 위에 놓아라"와 같은 명령은 대상 객체, 조작 목표(Manipulation Objective), 목적 위치 및 예상 완료 조건과 관련된 개념으로 분해되어야 한다. 따라서 언어는 단순한 명령 문자열(Command String)이 아니라 VLA 파이프라인 전체에서 인식, 추론, 계획 및 행동 생성을 조건화하는 의미론적 명세(Semantic Specification)로 기능한다.

로봇 상태 정보(Robot-state Information)는 VLA 아키텍처를 주로 의미론적 이해에 초점을 맞춘 비전-언어 시스템(Vision-Language System)과 구별하는 요소이다. 모델은 관절 위치, 속도, 말단장치 자세(End-effector Pose), 그리퍼 상태(Gripper State), 접촉 조건(Contact Condition), 균형 정보, 배터리 상태 및 기타 관련 상태 변수를 입력받을 수 있다. 이러한 신호는 제안된 행동이 물리적으로 실행 가능한지를 판단하는 문맥을 제공한다. 동일한 시각적 장면에서도 휴머노이드의 자세, 도달 가능성(Reachability), 현재 파지 상태 또는 상호작용 이력에 따라 서로 다른 행동이 필요할 수 있다.

멀티모달 융합(Multimodal Fusion)은 시각 토큰, 언어 토큰(Language Token), 로봇 상태 임베딩(Robot-state Embedding), 선택적인 메모리를 하나의 공유 표현(Shared Representation)으로 결합한다. 트랜스포머 기반 어텐션 메커니즘(Transformer-based Attention Mechanism)은 언어 표현을 시각적으로 관측된 엔티티와 연결하면서 동시에 로봇의 물리적 구성을 고려할 수 있다. 그 결과 생성되는 표현은 환경에 무엇이 존재하는지뿐만 아니라 어떤 엔티티가 작업과 관련되는지, 로봇과 어떤 관계에 있는지, 이후의 행동으로 물리 세계에서 어떤 변화가 예상되는지를 나타낸다.

행동 표현(Action Representation)은 멀티모달 추론이 어떻게 체화 행동(Embodied Behavior)으로 전환되는지를 정의한다. 시스템 아키텍처에 따라 VLA 출력은 이산 스킬(Discrete Skill), 기호적 행동(Symbolic Action), 말단장치 목표, 궤적(Trajectory), 자세, 웨이포인트(Waypoint), 그리퍼 명령 또는 연속 행동 벡터(Continuous Action Vector)를 나타낼 수 있다. 휴머노이드 아키텍처에서는 VLA가 작업 수준 또는 스킬 수준의 행동을 선택하고, 전용 모션 플래너(Motion Planner)와 제어기가 이를 동역학적으로 실행 가능한 관절 궤적 및 액추에이터 명령으로 변환하는 계층적 표현(Hierarchical Representation)이 효과적이다.

계층적 제어(Hierarchical Control)는 휴머노이드 동작이 매우 다양한 시간 척도(Time Scale)를 포함하기 때문에 특히 중요하다. 의미론적 추론과 작업 선택은 상대적으로 느리게 동작할 수 있지만, 균형 제어, 접촉 안정화(Contact Stabilization), 관절 토크 제어 및 충돌 대응은 훨씬 빠른 결정론적 루프(Deterministic Loop)를 필요로 한다. 따라서 VLA는 멀티모달 모델의 추론 주기로 모든 액추에이터를 직접 제어하기보다 하위 제어 계층에 목표 또는 제한된 행동 참조(Bounded Action Reference)를 생성해야 한다. 이러한 분리는 시스템의 응답성과 물리적 안정성을 유지한다.

행동 청킹(Action Chunking)은 작업에 일련의 조정된 움직임이 필요한 경우 효율성을 향상시킬 수 있다. VLA는 하나의 순간적인 명령만 예측하는 대신 짧은 시간 범위의 행동 토큰(Action Token) 또는 구조화된 스킬 시퀀스(Structured Skill Sequence)를 생성할 수 있다. 이후 실행 시스템은 진행 상태를 모니터링하고 환경이 변화하면 시퀀스를 중단하거나 수정하거나 다시 생성할 수 있다. 이러한 방식은 높은 계산 비용이 요구되는 추론의 반복 횟수를 줄이면서 조작 및 인간-로봇 상호작용(Human-Robot Interaction)에 필요한 피드백 기반 행동(Feedback-driven Behavior)을 유지한다.

폐루프 실행(Closed-loop Execution)은 예측된 행동이 이후의 추론에 사용되는 관측 자체를 변화시키기 때문에 체화 AI에서 필수적이다. 행동이 시작된 이후 카메라, 촉각 센서, 힘 센서 및 고유수용성 피드백(Proprioceptive Feedback)을 통해 예상했던 물리적 결과가 실제로 발생했는지를 판단한다. 새로운 관측은 다시 인식 및 VLA 파이프라인으로 전달되어 인식-추론-행동 순환(Perception-Reasoning-Action Cycle)을 형성한다. 이 피드백 루프는 객체가 이동하거나, 파지에 실패하거나, 접촉 상태가 예상과 다르거나, 사람이 작업 공간을 변경했을 때 행동을 수정할 수 있도록 한다.

메모리(Memory)는 이러한 순환 과정에 시간적 연속성(Temporal Continuity)을 제공한다. 단기 메모리(Short-term Memory)는 최근 관측, 행동, 실패, 대화 및 중간 작업 상태를 유지하여 VLA가 이미 완료된 작업을 판단할 수 있도록 한다. 장기 메모리(Long-term Memory)는 객체 지식, 작업 공간 정보, 학습된 스킬, 운영 절차 및 이전 경험을 포함할 수 있다. 검색(Retrieval)은 현재 작업과 관련된 문맥만 제공하여 모델 입력의 계산 부담을 관리 가능한 수준으로 유지하면서 장시간에 걸친 행동을 지원해야 한다.

스킬 라이브러리(Skill Library)는 파운데이션 모델 추론(Foundation-model Reasoning)과 검증된 로봇 기능 사이에 효과적인 경계를 제공한다. VLA는 이동(Navigate), 도달(Reach), 파지(Grasp), 배치(Place), 검사(Inspect), 전달(Hand Over), 열기(Open), 복구(Recover)와 같은 파라미터화된 기능(Parameterized Capability)을 선택할 수 있으며, 각 기능은 검증된 계획 및 제어 소프트웨어를 통해 구현된다. 이러한 구조는 생성형 모델이 모든 저수준 제어 세부사항을 직접 생성하지 않고도 멀티모달 지능을 통해 유연한 행동을 구성할 수 있게 하며, 재사용 가능한 물리적 행동을 체계적으로 시험할 수 있도록 한다.

안전 감독(Safety Supervision)은 확률적 행동 생성(Probabilistic Action Generation)과 독립적으로 유지되어야 한다. 실행 전에 VLA 출력은 작업 공간 한계, 충돌 제약, 관절 한계, 힘 및 토크 제한, 균형 조건, 사람과의 거리 및 허용된 동작 모드에 대해 검증되어야 한다. 비상 정지(Emergency Stop) 회로와 안전 등급 기능(Safety-rated Function)은 모델 출력과 관계없이 최종 제어 권한을 유지해야 한다. 신뢰도가 부족하거나 그라운딩(Grounding)이 모호하거나 예상하지 못한 환경 조건이 존재하는 행동은 거부하거나 제한하거나 추가 관측 또는 사람의 확인을 요구할 수 있다.

VLA는 의미론적으로 합리적이지만 물리적으로 부적절한 행동을 생성할 수 있기 때문에 불확실성 관리(Uncertainty Management)가 필요하다. 따라서 인식, 그라운딩, 작업 해석 및 행동 선택 전반에서 신뢰도를 평가해야 한다. 기하학적 인식(Geometric Perception), 힘 센싱(Force Sensing), 월드 모델 제약(World-model Constraint), 실행 피드백과의 교차 검증(Cross-checking)은 추가적인 판단 근거를 제공한다. 불확실성이 정의된 임계값을 초과하면 신뢰할 수 없는 행동 시퀀스를 계속 수행하는 대신 추가 관측을 요청하거나 보수적인 복구 행동을 선택하거나 실행을 중지할 수 있다.

컴퓨팅 아키텍처(Computing Architecture)는 AI 추론 자원을 시간 결정적 제어 자원(Timing-critical Control Resource)과 분리해야 한다. GPU 또는 AI 가속기(AI Accelerator)는 시각 인코딩, 멀티모달 트랜스포머(Multimodal Transformer), 정책 추론(Policy Inference), 파운데이션 모델을 실행할 수 있으며, CPU, MCU 또는 실시간 프로세서는 모션 계획 인터페이스, 통신, 안전 모니터링 및 액추에이터 제어를 수행한다. 자원 스케줄링은 추론 지연(Inference Latency), GPU 메모리, 대역폭, 열적 조건 및 전력 소비를 고려하여 대규모 VLA 워크로드가 필수적인 휴머노이드 제어 기능을 저하시키지 않도록 해야 한다.

통신 및 동기화(Communication and Synchronization)는 VLA를 휴머노이드 플랫폼의 더 넓은 전기 및 컴퓨팅 아키텍처와 연결한다. 고대역폭 인식 데이터는 기가비트 이더넷(Gigabit Ethernet)을 사용할 수 있으며, 결정론적 액추에이터 및 관절 통신에는 필요에 따라 이더캣(EtherCAT)이나 CAN FD와 같은 실시간 네트워크를 사용할 수 있다. ROS 2와 DDS는 의미론적 상태 및 작업 메시지를 분산할 수 있으며, 동기화된 타임스탬프(Timestamp)를 통해 시각 관측, 로봇 자세, 힘 측정값 및 생성된 행동이 시간적으로 일관된 상태를 유지하도록 한다.

엣지-클라우드 통합(Edge-cloud Integration)은 모델 학습, 플릿 학습(Fleet Learning), 평가, 데이터 관리 및 대규모 업데이트를 지원할 수 있지만, 물리적 행동 실행이 신뢰할 수 없는 외부 연결에 의존해서는 안 된다. 핵심 인식, 행동 검증, 안전 감독 및 필수 제어 기능은 로컬에서 지속적으로 사용할 수 있어야 한다. 클라우드 자원은 수집된 경험을 처리하고, 모델을 개선하고, 검증된 파라미터를 배포하거나, 비실시간 추론을 제공할 수 있으며, 휴머노이드는 엣지(Edge)에서 자율적이고 안전한 동작을 유지한다.

VLA는 궁극적으로 휴머노이드 AI 계층 구조에서 이해(Understanding)를 체화 실행(Embodied Execution)으로 전환하는 역할을 수행한다. 앞선 VLM 아키텍처(VLM Architecture)가 로봇이 무엇을 관측하고 있으며 그 관측이 무엇을 의미하는지를 규명한다면, VLA는 로봇이 다음에 무엇을 해야 하는가라는 질문을 추가한다. VLA의 출력은 이후 에이전트 아키텍처(Agent Architecture), 스킬 시스템(Skill System), 플래너(Planner), 안전 감독기(Safety Supervisor), 피지컬 AI 런타임(Physical AI Runtime)으로 전달되며, 이를 통해 멀티모달 파운데이션 모델 지능에서 물리 세계의 측정 가능한 행동까지 이어지는 통제된 경로를 형성한다.

## 14.03. Agent Architecture

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

에이전트 아키텍처(Agent Architecture)는 멀티모달 이해(Multimodal Understanding)와 행동 능력을 지속적이고 목표 지향적인 휴머노이드 행동으로 변환하는 의사결정 계층(Decision-making Layer)을 제공한다. VLM이 시각 및 언어 정보를 해석하고 VLA가 인식과 후보 물리 행동을 연결하는 반면, 에이전트(Agent)는 시간의 흐름에 따라 목표를 관리한다. 에이전트는 다음에 무엇을 수행해야 하는지 결정하고, 진행 상태를 평가하며, 적절한 도구 또는 로봇 스킬(Robot Skill)을 호출하고, 환경이나 작업 상태가 변화하면 실행 전략을 조정한다.

휴머노이드 시스템에서 에이전트는 일반적으로 인식(Perception), VLM, VLA, 모션 계획(Motion Planning), 실시간 제어(Real-time Control) 계층의 상위에서 동작한다. 에이전트가 관절 토크, 균형 또는 액추에이터 타이밍을 직접 제어해서는 안 된다. 대신 작업 및 임무 수준(Task and Mission Level)에서 추론하고, 하위 계층에서 검증되는 구조화된 목표(Structured Goal)와 스킬 요청(Skill Request)을 생성한다. 이러한 계층 구조는 상대적으로 느리고 확률적인 AI 추론을 결정론적 물리 제어와 분리하면서 고급 모델이 복잡한 로봇 행동을 조정할 수 있도록 한다.

에이전트는 외부 환경과 로봇 내부 상태를 모두 나타내는 멀티모달 문맥(Multimodal Context)을 입력받는다. 입력에는 VLM 장면 설명, 그라운딩된 객체(Grounded Object), VLA 행동 후보, 월드 모델 엔티티(World-model Entity), 대화, 작업 명령, 로봇 상태 정보, 배터리 상태, 위치 추정(Localization), 실행 피드백 등이 포함될 수 있다. 이러한 입력은 로봇이 현재 무엇을 알고 있는지, 어떤 목표를 수행하고 있는지, 어떤 행동이 이미 실행되었는지, 어떤 제약 조건이 여전히 활성화되어 있는지를 요약하는 에이전트 상태(Agent State)로 변환된다.

목표 해석(Goal Interpretation)은 사람의 명령 또는 자율 임무 요청을 에이전트가 관리할 수 있는 명시적인 목표로 변환한다. "방을 검사하고 손상된 부품을 정비 스테이션으로 가져가라"와 같은 명령은 하나의 행동이 아니라 여러 개의 상호 의존적인 활동을 포함한다. 에이전트는 완료 조건(Completion Condition), 관련 객체, 환경적 제약 및 중간 목표(Intermediate Objective)를 식별하여 명령을 구조화되지 않은 언어 시퀀스로 처리하는 대신 실행 상태를 지속적으로 모니터링할 수 있도록 한다.

작업 분해(Task Decomposition)는 복잡한 목표를 관리 가능한 하위 작업(Subtask)으로 나눈다. 에이전트는 임무를 목표 영역으로 이동, 부품 식별, 상태 확인, 안전한 접근, 파지(Grasp), 운반 및 전달 확인과 같은 단계로 변환할 수 있다. 작업 분해를 통해 서로 다른 로봇 기능을 공통 추론 프레임워크(Reasoning Framework)에서 조정할 수 있으며, 시스템이 실행을 계속할지, 재시도할지, 재계획(Replan)할지 또는 종료할지를 판단할 수 있는 명확한 체크포인트(Checkpoint)를 제공한다.

계획(Planning)은 하위 작업 사이의 순서와 의존 관계를 결정한다. 실용적인 휴머노이드 에이전트는 변경할 수 없는 고정된 시퀀스를 생성하는 대신 새로운 관측이 들어올 때 수정할 수 있는 동적 계획(Dynamic Plan)을 유지한다. 사전 조건(Precondition)은 행동을 언제 시작할 수 있는지를 정의하고, 예상 결과(Expected Outcome)는 실행 이후 형성되어야 할 상태를 나타낸다. 예상 결과와 실제 관측 결과를 비교함으로써 에이전트는 전체 임무를 처음부터 다시 시작하지 않고도 편차를 감지하고 계획을 갱신할 수 있다.

에이전트에는 도구 및 체화 스킬(Embodied Skill) 라이브러리와 연결되는 인터페이스가 필요하다. 사용 가능한 기능에는 인식 질의(Perception Query), 내비게이션(Navigation), 도달(Reach), 파지, 배치(Place), 검사(Inspect), 말하기(Speak), 듣기(Listen), 조작(Manipulate), 열기(Open), 복구(Recover), 데이터베이스 접근 또는 외부 시스템과의 통신 등이 포함될 수 있다. 각 도구는 정의된 입력, 출력, 제약 조건 및 상태 정보를 제공해야 한다. 에이전트는 임의의 저수준 액추에이터 명령을 생성하는 대신 이러한 기능을 선택하고 파라미터화하여 추론과 실행 사이에 통제된 경계를 형성한다.

VLM과 VLA 모델은 에이전트 내부에서 전문화된 추론 구성요소(Specialized Reasoning Component)로 동작할 수 있다. 에이전트는 의미론적 해석, 시각 질의응답(Visual Question Answering) 또는 객체 그라운딩(Object Grounding)이 필요할 때 VLM을 호출하고, 멀티모달 상황을 적절한 체화 행동으로 변환해야 할 때 VLA를 사용할 수 있다. 이러한 모듈식 관계(Modular Relationship)는 하나의 파운데이션 모델(Foundation Model)이 모든 책임을 담당하는 것을 방지하고, 인식, 추론, 행동 생성, 계획 및 안전 기능이 독립적으로 발전할 수 있도록 한다.

메모리(Memory)는 에이전트가 장시간 작업에서 연속성을 유지하도록 한다. 작업 메모리(Working Memory)는 현재 목표, 최근 관측, 활성 계획(Active Plan), 도구 실행 결과 및 실행 상태를 포함한다. 에피소드 메모리(Episodic Memory)는 이전 상호작용과 완료된 임무를 유지할 수 있으며, 의미 메모리(Semantic Memory)는 객체, 환경, 절차 및 기능에 대한 재사용 가능한 지식을 저장한다. 검색 메커니즘(Retrieval Mechanism)은 관련 정보만 선택하여 과거의 문맥이 불필요한 데이터로 추론 모델을 과부하시키지 않으면서 의사결정에 활용되도록 해야 한다.

월드 모델(World Model)은 신뢰할 수 있는 에이전트 추론에 필요한 구조화된 환경 상태(Structured Environmental State)를 제공한다. 월드 모델은 객체, 위치, 사람, 공간 관계, 로봇 자세, 작업 상태, 접근 가능성(Accessibility), 알려진 위험 요소를 표현할 수 있다. 에이전트는 관측과 행동이 발생함에 따라 이러한 표현을 갱신한다. 행동 이후 예상되는 월드 상태(Expected World State)와 새롭게 관측된 조건을 비교함으로써 시스템은 행동 성공 여부와 계획 과정에서 사용된 가정이 여전히 유효한지를 판단할 수 있다.

실행 관리자(Execution Manager)는 에이전트의 결정을 하위 로봇 계층에 전달할 수 있는 통제된 요청으로 변환한다. 선택된 스킬을 디스패치(Dispatch)하고 상태를 모니터링하며 완료 결과를 수집하고 타임아웃(Timeout), 취소, 재시도 및 복구 조건을 관리한다. 따라서 장시간 수행되는 물리 행동은 단순한 함수 호출(Function Call)이 아니라 관측 가능한 실행 프로세스(Observable Execution Process)로 표현되어야 한다. 이를 통해 에이전트는 로봇이 현재 무엇을 수행하고 있는지 지속적으로 인식하고 서로 충돌하는 스킬이 동시에 활성화되는 것을 방지할 수 있다.

폐루프 추론(Closed-loop Reasoning)은 반복적인 관측-추론-행동-평가(Observe-Reason-Act-Evaluate) 순환 구조를 형성한다. 각각의 의미 있는 행동이나 환경 이벤트 이후 에이전트는 새로운 관측을 활성 목표와 예상 결과에 비교하여 평가한다. 실행이 정상적으로 진행되면 다음 계획 단계를 선택한다. 파지에 실패하거나 경로가 차단되거나 객체가 사라지거나 사람이 작업에 개입하면, 에이전트는 원래의 시퀀스를 그대로 계속하는 대신 추가 정보를 수집하고 계획을 수정할 수 있다.

복구 행동(Recovery Behavior)은 실제 환경에 불확실성이 존재하기 때문에 물리적 에이전트의 핵심 구성요소이다. 아키텍처는 복구 가능한 실행 실패와 즉시 종료가 필요한 조건을 구분해야 한다. 파지 실패는 추가 관측과 수정된 파지 전략을 유발할 수 있으며, 위치 추정 실패는 정지 및 재위치 추정(Relocalization)을 요구할 수 있다. 반면 안전에 중요한 고장(Safety-critical Fault)이 발생하면 제한되지 않은 생성형 추론이 대응 방법을 결정하도록 하는 대신 사전에 정의된 안전 상태(Safe State)로 제어를 전환해야 한다.

안전 감독(Safety Supervision)은 에이전트의 추론 과정과 독립적으로 최종 권한을 유지해야 한다. 에이전트가 생성한 목표와 도구 요청은 물리적 실행 전에 정책(Policy), 작업 공간, 충돌, 힘, 관절, 사람 근접성(Human Proximity), 동작 모드 검사를 거쳐야 한다. 비상 정지(Emergency Stop) 기능과 안전 등급 제어기(Safety-rated Controller)는 최종 제어 권한을 유지한다. 에이전트는 안전 정보를 기반으로 추론할 수 있지만 하드웨어 보호 기능, 인증된 안전 기능 또는 로봇 아키텍처에 정의된 결정론적 한계를 무시할 수 없다.

자원 인식(Resource Awareness)을 통해 에이전트는 실제 로봇의 제약 조건을 계획에 반영할 수 있다. 배터리 상태, 열적 한계(Thermal Limit), 컴퓨팅 자원 가용성, 네트워크 연결, 페이로드 상태(Payload Condition), 액추에이터 상태 및 남은 임무 시간은 어떤 계획이 실행 가능한지에 영향을 줄 수 있다. 예를 들어 배터리 용량이 감소하고 있는 휴머노이드는 새로운 장시간 작업을 시작하는 대신 중요한 작업을 완료한 후 충전 위치로 복귀해야 할 수 있다. 따라서 자원 상태는 목표 및 계획 평가의 일부가 된다.

인간 상호작용(Human Interaction)은 언어, 제스처(Gesture), 시각적 그라운딩(Visual Grounding), 대화를 통해 에이전트 루프(Agent Loop)에 통합된다. 명령이 모호한 경우 에이전트는 안전하지 않은 해석을 선택하는 대신 추가 설명을 요청할 수 있다. 또한 작업 진행 상태를 보고하고, 실패 원인을 설명하고, 지원을 요청하거나, 영향이 큰 행동을 실행하기 전에 확인을 받을 수 있다. 이를 통해 언어는 일회성 명령 인터페이스가 아니라 사람과 자율 휴머노이드 시스템 사이의 양방향 감독 채널(Bidirectional Supervisory Channel)로 확장된다.

컴퓨팅 구현(Computing Implementation)은 에이전트 및 파운데이션 모델 워크로드를 실시간 로봇 제어와 분리해야 한다. GPU 또는 AI 가속기(AI Accelerator)는 VLM, VLA, 언어 추론 및 멀티모달 추론을 수행할 수 있으며, CPU는 오케스트레이션(Orchestration), 미들웨어(Middleware), 월드 모델 서비스 및 작업 상태를 관리한다. 전용 실시간 프로세서 또는 MCU는 액추에이터와 안전 기능을 지속적으로 제어한다. ROS 2, DDS, 이더넷(Ethernet), 이더캣(EtherCAT), CAN FD를 통한 통신은 적절한 시간적 경계를 유지하면서 이러한 계층을 연결할 수 있다.

에이전트 아키텍처는 궁극적으로 휴머노이드의 체화 AI 시스템을 통합하고 조정하는 오케스트레이션 계층(Orchestration Layer)으로 동작한다. VLM은 의미론적 이해(Semantic Understanding)를 제공하고, VLA는 체화 행동을 제안하거나 생성하며, 에이전트는 목표, 메모리, 도구, 월드 상태, 실행 피드백 및 계획을 중심으로 이러한 기능을 연결한다. 그 결과 형성되는 계층 구조는 피지컬 AI 런타임(Physical AI Runtime)이 장시간 자율 행동을 지속할 수 있도록 하면서 확률적 AI 의사결정을 검증된 모션 제어, 진단(Diagnostics), 통신 및 기능 안전 메커니즘과 분리된 상태로 유지한다.

## 14.04. Multi Agent Coordination

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

멀티 에이전트 조정(Multi-Agent Coordination)은 단일 자율 의사결정자로 구성된 휴머노이드 에이전트 아키텍처를 여러 로봇, AI 에이전트, 인프라 서비스 및 인간 감독자가 공동 목표를 위해 협력하는 분산 시스템(Distributed System)으로 확장한다. 각 에이전트는 로컬 인식(Local Perception), 추론, 메모리 및 실행 능력을 유지하면서 필요한 정보를 다른 에이전트와 선택적으로 교환한다. 목적은 단순한 통신이 아니라 작업 범위, 자원 활용률, 복원력(Resilience), 운영 효율성을 향상시키는 조정된 의사결정(Coordinated Decision Making)을 구현하는 것이다.

휴머노이드 시스템에서 에이전트(Agent)는 개별 로봇, 전문 AI 서비스(Specialized AI Service), 플릿 조정기(Fleet Coordinator), 인식 서비스 또는 작업 관리 구성요소를 나타낼 수 있다. 에이전트마다 서로 다른 물리적 능력, 센서, 컴퓨팅 자원, 도구 및 운영 제약 조건을 가질 수 있다. 따라서 멀티 에이전트 아키텍처는 현재 환경에서 물리적·계산적으로 작업을 수행할 수 있는 에이전트에게 적절한 작업을 할당할 수 있도록 각 에이전트의 능력과 상태를 명시적으로 표현해야 한다.

조정(Coordination)은 임무 목표(Mission Objective)에 대한 공유된 이해에서 시작된다. 복잡한 요청은 독립적으로 실행할 수 있거나 명확한 의존 관계를 갖는 하위 작업(Subtask)으로 분해할 수 있다. 하나의 휴머노이드는 작업 공간을 검사하는 동안 다른 휴머노이드는 도구를 가져올 수 있으며, 모바일 로봇(Mobile Robot)은 서로 다른 위치 사이에서 자재를 운반할 수 있다. 조정 계층은 이러한 활동 사이의 관계, 병렬로 수행할 수 있는 작업, 그리고 종속 행동을 시작하기 전에 어떤 결과가 먼저 확보되어야 하는지를 결정한다.

작업 할당(Task Allocation)은 능력, 위치, 작업 부하, 에너지, 우선순위 및 예상 실행 비용에 따라 하위 작업을 사용 가능한 에이전트에 매핑한다. 예측 가능한 환경에서는 정적 할당(Static Assignment)으로 충분할 수 있지만, 동적 할당(Dynamic Allocation)을 사용하면 조건이 변경될 때 작업을 다른 에이전트로 이전할 수 있다. 배터리 부족, 액추에이터 성능 저하, 접근 경로 차단 또는 과도한 작업 부하가 발생한 에이전트는 작업을 해제하거나 이전하여 전체 시스템을 다시 시작하지 않고도 다른 적격 에이전트가 임무를 계속 수행하도록 할 수 있다.

중앙집중식 조정(Centralized Coordination)은 감독 에이전트(Supervisory Agent) 또는 플릿 관리자(Fleet Manager)가 전역 작업 상태(Global Task State)를 유지하고 작업을 분배하는 방식이다. 이 아키텍처는 전역 최적화, 정책 적용 및 모니터링을 단순화하지만 통신과 중앙 조정기의 가용성에 의존한다. 분산 조정(Distributed Coordination)은 개별 에이전트가 협상하고 로컬 의사결정을 수행하도록 하여 확장성과 복원력을 향상시킨다. 실제 휴머노이드 시스템에서는 중앙집중식 임무 관리와 분산된 로컬 실행 및 복구를 결합할 수 있다.

통신(Communication)은 협력에 필요한 정보 교환을 제공한다. 에이전트는 구조화된 메시지(Structured Message)를 통해 위치, 작업 상태, 능력, 자원 상태, 객체 관측, 월드 모델 업데이트(World-model Update), 행동 의도(Intent), 실행 결과를 발행할 수 있다. ROS 2와 DDS는 로봇 수준의 분산 통신을 지원할 수 있으며, 이더넷(Ethernet), 무선 네트워크 또는 플릿 인터페이스(Fleet Interface)는 물리적으로 떨어진 시스템을 연결할 수 있다. 메시지 스키마(Message Schema)는 수신 에이전트가 정보를 올바르게 해석할 수 있도록 타임스탬프, 출처 식별자, 유효성, 우선순위 및 신뢰도를 정의해야 한다.

공유 월드 모델(Shared World Model)은 여러 에이전트가 동일한 운영 환경에 대해 추론할 수 있도록 한다. 카메라, 라이다(LiDAR), 위치 추정(Localization), 조작 및 인간 상호작용에서 얻은 로컬 관측은 객체, 사람, 로봇 위치, 위험 요소, 접근 가능성 및 작업 상태의 표현을 갱신할 수 있다. 시스템은 전역적으로 유용한 정보와 순수한 로컬 상태를 구분해야 한다. 연속적인 원시 센서 스트림(Raw Sensor Stream) 대신 의미론적 표현(Semantic Representation) 또는 압축된 표현을 공유하면 네트워크 및 컴퓨팅 요구사항을 크게 줄일 수 있다.

여러 에이전트가 월드 모델의 중복 영역을 갱신하는 경우 일관성 관리(Consistency Management)가 중요해진다. 두 로봇이 서로 다른 시점에서 동일한 객체를 관측하거나 시간 차이, 위치 추정 오차 또는 환경 변화로 인해 서로 다른 위치를 보고할 수 있다. 따라서 업데이트에는 타임스탬프, 신뢰도, 출처 정보 및 충돌 해결 규칙(Conflict-resolution Rule)이 필요하다. 최근의 신뢰할 수 있는 관측은 융합할 수 있으며, 서로 모순되는 정보는 불확실한 공유 상태가 전체 플릿으로 전파되지 않도록 재관측(Re-observation)을 유발할 수 있다.

의도 공유(Intent Sharing)는 물리적 행동이 실제로 발생하기 전에 다른 로봇의 행동을 예측할 수 있도록 한다. 에이전트는 복도에 진입하거나, 공유 객체를 조작하거나, 작업 스테이션을 예약하거나, 충전 스테이션을 사용할 예정임을 미리 알릴 수 있다. 다른 에이전트는 이러한 의도를 자신의 계획에 반영할 수 있다. 이를 통해 상세한 저수준 궤적(Low-level Trajectory)을 지속적으로 교환하지 않고도 경로 충돌, 중복 작업, 자원 경합(Resource Contention) 및 예상하지 못한 상호작용을 줄일 수 있다.

자원 조정(Resource Coordination)은 모든 에이전트가 동시에 사용할 수 없는 자산을 관리한다. 충전 스테이션, 도구, 엘리베이터, 작업 셀(Workcell), 네트워크 대역폭, GPU 서비스 및 제한된 운영 구역은 예약 또는 스케줄링이 필요할 수 있다. 조정 서비스는 이러한 공유 자원의 소유권, 대기열, 우선순위, 타임아웃(Timeout), 해제 상태를 관리할 수 있다. 명시적인 자원 관리는 개별적으로는 유효한 여러 에이전트의 계획이 물리적 실행 과정에서 서로 충돌하는 것을 방지한다.

여러 에이전트가 동일한 작업을 수행할 수 있는 경우 협상 메커니즘(Negotiation Mechanism)이 유용하다. 에이전트는 자신의 능력과 예상 비용을 알릴 수 있으며, 조정기 또는 분산 프로토콜(Distributed Protocol)은 임무 우선순위에 따라 작업을 할당한다. 비용은 거리, 실행 시간, 에너지 소비, 위험, 작업 부하 또는 도구 가용성을 나타낼 수 있다. 목표는 항상 하나의 지표를 최소화하는 것이 아니며, 안전, 긴급성, 자원 균형 및 전체 임무 완료가 로컬 효율성보다 우선될 수 있다.

조정은 하나의 로봇만으로 수행할 수 없는 협력 물리 작업(Cooperative Physical Task)도 지원해야 한다. 두 대의 휴머노이드가 대형 물체를 함께 운반하거나, 부품을 잡고 조립하거나, 서로 다른 시점에서 협력 검사를 수행할 수 있다. 이러한 작업에서는 시간, 상대 자세(Relative Pose), 접촉력(Contact Force), 모션 제약(Motion Constraint)이 서로 결합되기 때문에 작업 수준의 합의만으로 충분하지 않다. 상위 에이전트는 협력 목표를 정의하고, 동기화된 모션 및 힘 제어기(Synchronized Motion and Force Controller)가 안전한 실행에 필요한 결정론적 실시간 조정을 담당한다.

여러 로봇의 관측과 행동을 결합할 때 시간 동기화(Time Synchronization)는 매우 중요하다. PTP 또는 기타 동기화 메커니즘을 통해 센서 측정값, 위치 추정, 이벤트 로그(Event Log), 조정 메시지에 공통 시간 기준(Common Temporal Reference)을 제공할 수 있다. 일관된 타임스탬프가 없으면 공유 월드 모델에서 서로 다른 시점의 상태가 하나의 상태처럼 결합될 수 있다. 이는 이동하는 사람, 모바일 로봇, 협력 조작 및 멀티 에이전트 행동의 사후 분석에서 특히 중요하다.

개별 에이전트를 사용할 수 없게 되었을 때에도 고장 처리(Failure Handling)를 통해 임무의 연속성을 유지해야 한다. 하트비트(Heartbeat), 상태 모니터링(Health Monitoring), 작업 리스(Task Lease), 실행 타임아웃을 사용하여 고장 또는 연결이 끊어진 에이전트를 식별할 수 있다. 해당 에이전트의 활성 작업은 중지하거나 다른 에이전트에 재할당하거나 복구할 수 있다. 로컬 로봇은 통신이 끊겼을 때 플릿 명령을 무기한 기다리는 대신 안전한 자율 행동을 유지해야 하며, 안전 필수 기능은 멀티 에이전트 조정 네트워크와 독립적으로 계속 동작해야 한다.

안전 감독(Safety Supervision)은 로컬 및 공유 운영 조건 모두를 포괄해야 한다. 각 휴머노이드는 독립적인 충돌 회피(Collision Avoidance), 힘 제한, 비상 정지(Emergency Stop) 처리 및 안전 등급 제어(Safety-rated Control)를 유지하며, 조정 계층은 공유 구역, 통행 우선순위 및 협력 작업과 같은 상위 수준의 충돌을 관리한다. 플릿 수준 명령은 로컬 안전 보호 기능을 절대로 무시해서는 안 된다. 조정 정보가 즉각적인 센서 관측과 충돌하는 경우 로봇의 검증된 로컬 안전 메커니즘이 최종 권한을 유지한다.

조정에 참여하는 통신 엔티티가 증가함에 따라 보안(Security)의 중요성도 커진다. 에이전트는 작업 할당, 월드 모델 업데이트 또는 제어 관련 요청을 수락하기 전에 상대 에이전트와 서비스의 신원을 인증(Authentication)해야 한다. 권한 부여(Authorization)는 특정 도구, 구역, 데이터 또는 로봇 기능에 어떤 에이전트가 접근할 수 있는지를 결정한다. 암호화 통신(Encrypted Communication), 무결성 검사(Integrity Check), 로깅(Logging), 소프트웨어 신원(Software Identity), 통제된 자격 증명 관리(Credential Management)는 손상되거나 잘못된 메시지가 물리적 로봇 행동에 영향을 미칠 가능성을 줄인다.

확장성(Scalability)을 확보하려면 에이전트 수가 증가할수록 불필요한 통신과 중앙집중식 계산을 제한해야 한다. 계층적 조정(Hierarchical Coordination)은 위치, 작업 또는 능력에 따라 로봇을 그룹화하고, 로컬 조정기가 빈번한 상호작용을 처리하며 상위 서비스가 임무 전체의 목표를 관리하도록 할 수 있다. 이벤트 기반 업데이트(Event-driven Update), 의미론적 데이터 교환, 토픽 필터링(Topic Filtering), 분산 월드 모델(Distributed World Model)은 대역폭 사용을 줄인다. 새로운 휴머노이드 또는 전문 에이전트를 추가할 때 전체 제어 시스템을 재설계하지 않아도 되는 구조가 필요하다.

인간 감독자(Human Supervisor)도 멀티 에이전트 아키텍처의 일부로 유지된다. 운영자는 우선순위를 할당하고, 예외적인 행동을 승인하고, 플릿 상태를 확인하고, 임무를 수정하거나 자동 협상으로 모호성을 해결할 수 없는 경우 개입할 수 있다. 에이전트는 원시 텔레메트리(Raw Telemetry) 대신 의미론적 요약(Semantic Summary)을 사용하여 진행 상황을 보고함으로써 사람이 여러 로봇을 효율적으로 감독하도록 지원할 수 있다. 운영자가 어떤 에이전트가 결정을 내렸고 특정 행동이 왜 발생했는지 이해할 수 있도록 명확한 작업 소유권과 추적 가능한 의사결정 로그(Decision Log)가 중요하다.

멀티 에이전트 조정은 궁극적으로 개별 휴머노이드 지능의 상위에 분산 체화 AI 계층(Distributed Embodied AI Layer)을 형성한다. VLM은 의미론적 인식(Semantic Perception)을 제공하고, VLA는 인식을 물리 행동과 연결하며, 에이전트 아키텍처는 하나의 로봇에 대해 지속적인 목표와 실행을 관리한다. 멀티 에이전트 조정은 작업 할당, 공유 월드 상태, 통신, 자원 관리, 협상, 동기화 및 복구를 통해 이러한 자율 엔티티를 연결하여 여러 피지컬 AI(Physical AI) 시스템이 일관되고 확장 가능한 로봇 작업 집단(Robotic Workforce)으로 동작할 수 있도록 한다.

## 14.05. Foundation Model Integration

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

파운데이션 모델 통합(Foundation Model Integration)은 대규모 사전학습 AI 모델(Large Pretrained AI Model)을 휴머노이드 로봇의 인식, 추론, 행동, 메모리 및 제어 시스템과 연결하는 아키텍처 계층을 제공한다. 하나의 거대한 단일 모델을 모든 로봇 기능에 직접 내장하는 대신, 이 아키텍처는 파운데이션 모델을 공유 지능 서비스(Shared Intelligence Service)로 취급한다. 따라서 VLM, VLA 모델, 언어 모델(Language Model), 월드 모델(World Model), 전문 멀티모달 모델(Specialized Multimodal Model)은 결정론적 제어 및 안전 기능과 분리된 상태에서 각각의 능력을 제공할 수 있다.

휴머노이드 플랫폼은 카메라, 라이다(LiDAR), 마이크, 촉각 센서(Tactile Sensor), 힘 센서(Force Sensor), 관절 인코더(Joint Encoder), 관성 측정 장치(IMU), 진단(Diagnostics), 인간 상호작용(Human Interaction)으로부터 이질적인 정보를 생성한다. 파운데이션 모델이 추론을 수행하려면 이러한 정보를 적절한 멀티모달 표현(Multimodal Representation)으로 변환해야 한다. 인식 파이프라인(Perception Pipeline)은 동기화, 캘리브레이션(Calibration), 필터링, 추적, 세그멘테이션(Segmentation), 특징 추출(Feature Extraction)을 수행하며, 인터페이스 계층은 선택된 관측과 로봇 상태를 토큰(Token), 임베딩(Embedding), 구조화된 프롬프트(Structured Prompt) 또는 모델별 입력 표현으로 변환한다.

통합 아키텍처는 하나의 모델이 모든 작업을 수행한다고 가정하는 대신 여러 파운데이션 모델을 지원해야 한다. VLM은 의미론적 장면 이해(Semantic Scene Understanding)와 시각적 그라운딩(Visual Grounding)을 전문적으로 수행하고, VLA는 체화 행동 제안(Embodied Action Proposal)을 생성하며, 언어 모델은 작업 추론, 대화 또는 계획을 수행할 수 있다. 월드 모델은 환경 상태의 변화를 예측할 수 있으며, 전문 모델은 음성, 조작, 내비게이션(Navigation) 또는 이상 상태 해석(Anomaly Interpretation)을 담당한다. 오케스트레이션 계층(Orchestration Layer)은 각각의 요청을 어떤 모델이 처리할 것인지 선택한다.

모델 오케스트레이션(Model Orchestration)은 이러한 파운데이션 모델 사이의 라우팅(Routing), 호출, 문맥 구성(Context Construction), 결과 집계(Result Aggregation)를 관리한다. 요청은 작업 유형, 필요한 모달리티(Modality), 지연 시간, 신뢰도 및 사용 가능한 컴퓨팅 자원에 따라 분류된다. 단순한 인식 작업은 경량 로컬 모델(Lightweight Local Model)에서 처리할 수 있으며, 복잡한 의미론적 추론은 더 큰 멀티모달 모델을 호출할 수 있다. 이를 통해 불필요하게 고비용 추론 자원을 사용하는 것을 방지하면서 필요할 때 고급 추론 능력을 활용하고 휴머노이드의 응답성을 유지할 수 있다.

문맥 관리(Context Management)는 각 추론 주기에서 파운데이션 모델에 어떤 정보를 제공할 것인지를 결정한다. 원시 센서 스트림(Raw Sensor Stream)은 일반적으로 데이터량이 너무 크고 상위 수준 추론에 필요한 것보다 많은 정보를 포함한다. 따라서 통합 계층은 관련 이미지, 객체 설명, 로봇 상태, 작업 이력, 대화, 월드 모델 엔티티(World-model Entity), 검색된 지식(Retrieved Knowledge)을 선택한다. 효과적인 문맥 구성은 추론 효율성을 향상시키는 동시에 관련 없는 멀티모달 데이터로 인해 중요한 작업 정보가 가려질 가능성을 줄인다.

그라운딩(Grounding)은 추상적인 모델 출력을 로봇의 운영 환경에 존재하는 물리적 엔티티와 연결한다. 파운데이션 모델이 "작업대 옆의 용기"를 언급하더라도 통합 계층은 해당 표현을 추적된 객체(Tracked Object), 세그멘테이션 영역(Segmentation Region), 3차원 위치 또는 월드 모델 식별자(World-model Identifier)와 연결해야 한다. 의미론적 토큰(Semantic Token)과 측정 가능한 물리 상태 사이의 이러한 연결은 모델이 생성한 추론이 내비게이션, 조작, 검사 또는 인간-로봇 상호작용에 영향을 미치기 전에 반드시 필요하다.

파운데이션 모델의 출력이 로봇 소프트웨어에서 사용되는 경우 구조화된 인터페이스(Structured Interface)를 우선적으로 사용해야 한다. 제한되지 않은 자연어 응답을 실행 가능한 명령으로 직접 받아들이는 대신, 아키텍처는 작업 식별자, 객체 참조, 행동 유형, 파라미터, 신뢰도, 제약 조건 및 예상 결과를 포함하는 스키마(Schema)를 요구할 수 있다. 검증 소프트웨어(Validation Software)는 생성된 구조를 에이전트(Agent), 플래너(Planner), 스킬 관리자(Skill Manager) 또는 VLA 구성요소로 전달하기 전에 검증함으로써 생성형 추론과 물리적 실행 사이의 모호성을 줄인다.

메모리 및 검색(Memory and Retrieval)은 모델 파라미터 내부에 영구적으로 포함할 수 없는 정보를 파운데이션 모델에 추가한다. 작업 메모리(Working Memory)는 현재 작업, 최근 관측, 실행 결과 및 대화를 유지하며, 장기 메모리(Long-term Memory)는 지도, 객체 지식, 운영 절차, 이전 경험 및 로봇별 정보를 저장할 수 있다. 검색 증강 메커니즘(Retrieval-augmented Mechanism)은 각 요청에 관련된 지식을 선택하여 범용 모델이 지속적인 재학습 없이 현재의 운영 문맥을 기반으로 추론할 수 있도록 한다.

도구 통합(Tool Integration)을 통해 파운데이션 모델은 학습된 파라미터 외부에 존재하는 기능에 접근할 수 있다. 에이전트는 인식 질의(Perception Query), 데이터베이스, 지도, 진단 서비스, 내비게이션, 조작 스킬, 외부 API 또는 플릿 시스템(Fleet System)에 대한 통제된 인터페이스를 제공할 수 있다. 모델은 정의된 스키마를 통해 이러한 도구를 요청할 수 있지만, 실행 관리자(Execution Manager)가 해당 요청의 유효성과 허용 여부를 판단한다. 이를 통해 생성형 지능(Generative Intelligence)과 소프트웨어 또는 물리적 기능 사이에 통제된 관계를 형성할 수 있다.

모델 적응(Model Adaptation)은 범용 파운데이션 모델을 휴머노이드 특화 응용에 더욱 유용하도록 만든다. 프롬프트 엔지니어링(Prompt Engineering), 어댑터(Adapter), 저순위 적응(Low-rank Adaptation), 미세조정(Fine-tuning), 모방 학습(Imitation Learning), 선호도 최적화(Preference Optimization), 작업별 헤드(Task-specific Head)를 통해 모델을 로봇 용어와 행동에 정렬할 수 있다. 적응 데이터에는 원격조작 시연(Teleoperation Demonstration), 로봇 궤적, 시각 관측, 언어 명령, 조작 결과 및 실패 사례가 포함될 수 있다. 이렇게 생성된 모델도 실제 물리 시스템에 배포하기 전에 독립적으로 평가되어야 한다.

컴퓨팅 아키텍처(Computing Architecture)는 서로 다른 모델 크기와 실행 위치를 지원해야 한다. 소형 또는 지연 시간에 민감한 모델은 로봇의 GPU나 AI 가속기(AI Accelerator)에서 지속적으로 실행할 수 있으며, 대형 모델은 필요할 때 엣지 서버(Edge Server) 또는 클라우드 인프라(Cloud Infrastructure)에서 선택적으로 호출할 수 있다. 모델 분할(Model Partitioning), 양자화(Quantization), 캐싱(Caching), 배칭(Batching), 가속 추론(Accelerated Inference)을 통해 메모리와 전력 요구량을 줄일 수 있다. 그러나 로봇의 핵심 기능은 원격 모델의 가용성이나 예측할 수 없는 네트워크 지연에 의존해서는 안 된다.

모델 레지스트리(Model Registry)는 휴머노이드 시스템에 배포되는 AI 구성요소에 대해 통제된 수명주기 관리(Lifecycle Management)를 제공한다. 각 모델 버전은 아키텍처, 파라미터, 학습 데이터 계보(Training Data Lineage), 지원 작업, 하드웨어 요구사항, 평가 결과 및 배포 상태와 연결될 수 있다. 로봇은 승인된 모델 버전만 로드해야 하며, 새로운 모델이 허용할 수 없는 행동을 생성하거나 성능 저하를 일으키는 경우 롤백 메커니즘(Rollback Mechanism)을 통해 검증된 기존 운영 구성으로 복귀할 수 있어야 한다.

안전 경계(Safety Boundary)는 파운데이션 모델의 추론을 안전 필수 제어(Safety-critical Control)와 격리해야 한다. 생성된 행동이나 계획은 작업 공간 한계, 충돌 조건, 사람 근접성(Human Proximity), 관절 한계, 힘 및 토크 제한, 운영 모드 및 자원 제약 조건을 포함하는 결정론적 검사를 통과해야 한다. 파운데이션 모델은 상황을 해석하거나 대응 방안을 제안할 수 있지만 비상 정지(Emergency Stop) 회로, 안전 등급 제어기(Safety-rated Controller), 하드웨어 인터록(Hardware Interlock) 또는 독립적으로 검증된 기타 보호 메커니즘을 무시할 수 없다.

파운데이션 모델은 그럴듯하지만 잘못된 해석을 생성할 수 있기 때문에 신뢰도 및 불확실성 관리(Confidence and Uncertainty Management)가 필요하다. 통합 계층은 입력 품질, 그라운딩 신뢰도, 모델 신뢰도, 실행 이력 및 검증 결과에 관한 정보를 유지해야 한다. 중요한 판단은 결정론적 인식(Deterministic Perception), 중복 센서(Redundant Sensor), 추가 모델 질의 또는 월드 모델 제약(World-model Constraint)을 통해 교차 검증할 수 있다. 신뢰도가 낮은 출력은 재관측(Re-observation), 대안 추론, 사람의 확인 또는 보수적인 행동을 유발할 수 있다.

모델이 외부 서버와 통신하거나 원격 인프라로부터 업데이트를 수신하는 경우 사이버보안(Cybersecurity)은 특히 중요해진다. 인증(Authentication), 권한 부여(Authorization), 암호화 통신(Encrypted Communication), 소프트웨어 서명(Software Signing), 무결성 검증(Integrity Verification), 접근 제어 및 감사 로깅(Audit Logging)을 통해 모델 아티팩트(Model Artifact)와 추론 인터페이스를 보호해야 한다. 프롬프트 인젝션(Prompt Injection), 악의적인 센서 콘텐츠, 손상된 도구 또는 승인되지 않은 모델 업데이트가 궁극적으로 물리적 로봇 행동에 영향을 미칠 수 있다는 점을 고려해야 한다.

모니터링(Monitoring)은 배포 이후 계산 성능과 행동 성능을 모두 평가해야 한다. 추론 지연, GPU 사용률, 메모리 소비, 온도, 네트워크 사용량, 모델 실패, 신뢰도 분포 및 작업 성공률을 로봇 이벤트와 함께 기록할 수 있다. 행동 모니터링(Behavioral Monitoring)은 드리프트(Drift), 반복적인 추론 실패, 비정상적인 도구 사용 또는 예상 결과와 실제 결과 사이의 차이를 식별할 수 있다. 이러한 기록은 진단, 모델 개선, 플릿 학습(Fleet Learning), 통제된 수명주기 관리를 지원한다.

플릿 수준 통합(Fleet-level Integration)을 통해 여러 휴머노이드에서 수집된 경험을 각 로봇이 독립적으로 학습하지 않고도 모델 개선에 활용할 수 있다. 선택된 관측, 작업 결과, 실패 및 사람의 수정 정보는 엣지 또는 클라우드 학습 환경으로 업로드할 수 있으며, 이곳에서 필터링, 라벨링(Labeling), 평가를 거쳐 향후 모델 개발에 반영된다. 업데이트된 모델은 통제된 배포 전에 검증되며, 이를 통해 현장 운영(Field Operation)과 중앙집중식 AI 엔지니어링(Centralized AI Engineering) 사이에 피드백 루프를 형성한다.

파운데이션 모델 통합은 궁극적으로 휴머노이드의 체화 AI 스택(Embodied AI Stack)을 위한 공통 지능 인프라(Common Intelligence Infrastructure)를 제공한다. VLM, VLA, 에이전트 및 멀티 에이전트 구성요소는 서로 격리된 AI 기능으로 동작하는 대신 공유 모델 서비스, 메모리, 도구, 월드 표현(World Representation), 수명주기 관리 메커니즘을 활용할 수 있다. 유연한 사전학습 지능과 구조화된 인터페이스, 검증, 로컬 실시간 제어, 안전 감독 및 관리된 배포를 결합함으로써 이 아키텍처는 파운데이션 모델에서 신뢰할 수 있는 피지컬 AI(Physical AI) 운영으로 이어지는 실용적인 연결 구조를 형성한다.

## 14.06. Physical AI Runtime

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

피지컬 AI 런타임(Physical AI Runtime)은 체화 지능(Embodied Intelligence)을 휴머노이드 로봇의 결정론적 컴퓨팅, 통신, 제어 및 안전 인프라와 연결하는 운영 소프트웨어 계층(Operational Software Layer)이다. VLM, VLA, 에이전트(Agent), 멀티 에이전트(Multi-Agent), 파운데이션 모델(Foundation Model) 서비스가 인식, 계획, 스킬, 진단 및 하드웨어 인터페이스와 상호작용하는 실행 환경을 제공한다. 주요 역할은 확률적 추론이 검증된 실행 경계(Validated Execution Boundary)를 우회하지 않도록 하면서 AI의 의사결정을 관리 가능한 로봇 동작으로 변환하는 것이다.

런타임(Runtime)은 상위 수준 지능 서비스와 하위 수준 로보틱스 소프트웨어 스택(Robotics Software Stack) 사이에 위치한다. 상위에서는 파운데이션 모델과 에이전트가 의미론적 해석, 목표, 계획, 행동 후보 및 도구 요청을 생성한다. 하위에서는 모션 플래너(Motion Planner), 실시간 제어기(Real-time Controller), 장치 드라이버(Device Driver), 통신 네트워크 및 안전 메커니즘이 물리적 하드웨어와 상호작용한다. 런타임은 명시적인 인터페이스를 통해 이러한 계층을 조정하여 AI 기능을 모듈화된 상태로 유지하면서 물리적 실행이 예측 가능하고 시험 가능한 경로를 따르도록 한다.

서비스 지향 아키텍처(Service-oriented Architecture)를 사용하면 런타임 기능을 각각의 책임에 따라 분리할 수 있다. 인식 서비스(Perception Service)는 카메라, 라이다(LiDAR), 오디오, 촉각 센싱(Tactile Sensing), 힘 측정 및 고유수용성 데이터(Proprioceptive Data)를 처리하고, 월드 모델 서비스(World-model Service)는 구조화된 환경 상태를 유지한다. 계획 서비스는 작업 또는 모션 솔루션을 계산하고, 스킬 서비스(Skill Service)는 재사용 가능한 로봇 기능을 제공하며, AI 추론 서비스(AI Inference Service)는 멀티모달 모델을 실행한다. 런타임은 이러한 구성요소 사이의 검색, 통신, 의존 관계, 상태 및 수명주기 상태(Lifecycle State)를 관리한다.

런타임 오케스트레이션(Runtime Orchestration)은 서비스와 모델이 언제 실행되어야 하는지, 그리고 그 결과가 어떻게 연결되어야 하는지를 결정한다. 하나의 작업에는 인식, 객체 그라운딩(Object Grounding), 추론, 스킬 선택, 궤적 생성(Trajectory Generation), 검증 및 실행이 순차적으로 필요할 수 있으며, 다른 기능들은 동시에 동작할 수 있다. 오케스트레이터(Orchestrator)는 의존 관계와 실행 상태를 관리하여 비동기 AI 추론(Asynchronous AI Inference)이 주기적인 로보틱스 프로세스 및 결정론적 실시간 루프와 제어되지 않은 시간적 상호작용을 발생시키지 않고 공존할 수 있도록 한다.

런타임은 상위 수준 지능이 사용할 수 있는 통합 로봇 상태 표현(Unified Robot State Representation)을 유지한다. 관절 위치, 속도, 액추에이터 상태, 배터리 상태, 열 정보(Thermal Information), 위치 추정(Localization), 접촉 상태, 활성 고장(Active Fault), 네트워크 상태 및 현재 실행 중인 스킬을 구조화된 인터페이스를 통해 제공할 수 있다. 이를 통해 파운데이션 모델과 에이전트가 분산된 하드웨어별 데이터에 의존하는 것을 방지하고 추론, 계획, 모니터링 및 복구를 위한 일관된 운영 문맥(Operational Context)을 제공한다.

월드 상태 인터페이스(World-state Interface)는 의미론적 AI 추론과 측정 가능한 물리 정보를 연결한다. 인식 시스템에서 탐지된 객체는 식별자, 자세(Pose), 신뢰도, 타임스탬프(Timestamp), 속성 및 관계와 연결될 수 있다. 사람의 위치, 장애물, 접근 가능한 영역, 조작 대상 및 작업 상태 역시 동일한 운영 프레임워크를 통해 표현할 수 있다. 따라서 VLM과 에이전트는 의미론적 엔티티(Semantic Entity)를 기반으로 추론할 수 있으며, 플래너와 제어기는 물리적 실행에 필요한 기하학적 정보를 획득할 수 있다.

스킬 실행(Skill Execution)은 피지컬 AI 런타임의 핵심 책임이다. 상위 수준 지능은 제한되지 않은 액추에이터 명령을 직접 생성하는 대신 이동(Navigate), 도달(Reach), 파지(Grasp), 배치(Place), 검사(Inspect), 말하기(Speak), 전달(Hand Over), 복구(Recover)와 같이 정의된 기능을 호출해야 한다. 각 스킬은 파라미터, 사전 조건(Precondition), 실행 상태, 완료 기준(Completion Criteria), 타임아웃 조건 및 실패 코드를 제공한다. 런타임은 스킬 활성화를 감독하고 서로 호환되지 않거나 상호 배타적인 물리적 동작이 동시에 실행되지 않도록 한다.

행동 검증(Action Validation)은 AI가 생성한 의도와 로봇 실행 사이에 통제된 경계를 형성한다. 요청된 스킬이나 궤적이 승인되기 전에 런타임은 객체 참조, 운영 모드, 자원 가용성, 작업 공간 제약, 충돌 조건, 관절 한계, 페이로드 가정(Payload Assumption), 사람 근접성(Human Proximity)을 검증할 수 있다. 유효하지 않거나 불완전한 요청은 저수준 제어에 도달하기 전에 거부된다. 이러한 검증 계층은 행동이 확률적 파운데이션 모델이나 동적으로 생성된 에이전트 계획에서 시작될 때 특히 중요하다.

실행 모니터링(Execution Monitoring)은 명령된 행동이 예상한 결과를 생성하는지를 관찰한다. 센서 피드백, 제어기 상태, 궤적 진행 상태, 접촉 측정값, 인식 업데이트 및 스킬 완료 조건을 예상 실행 상태와 비교한다. 예를 들어 파지 명령은 단순히 모션이 완료되었다는 이유만으로 성공한 것으로 판단되지 않으며, 객체 존재 여부, 그리퍼 상태, 힘 정보 또는 후속 인식을 통해 성공 여부를 확인해야 할 수 있다. 검증된 결과는 에이전트와 월드 모델 서비스에 다시 전달된다.

복구 관리(Recovery Management)는 즉각적인 안전 정지가 필요하지 않은 실행 편차를 처리한다. 타임아웃, 도달할 수 없는 목표, 파지 실패, 차단된 경로, 일시적인 통신 장애 또는 사용할 수 없는 자원은 사전에 정의된 복구 절차(Recovery Procedure)를 유발할 수 있다. 런타임은 활성 스킬을 취소하거나, 재관측(Re-observation)을 요청하거나, 구성요소를 재설정하거나, 대체 기능을 선택하거나, 재계획을 위해 구조화된 실패 정보를 에이전트에 반환할 수 있다. 안전 필수 고장(Safety-critical Failure)은 독립적인 안전 메커니즘과 사전에 정의된 안전 상태 전환(Safe-state Transition)이 담당한다.

실시간 분리(Real-time Separation)는 피지컬 AI가 근본적으로 서로 다른 시간 요구사항을 갖는 워크로드를 포함하기 때문에 필수적이다. 파운데이션 모델 추론에는 수십 또는 수백 밀리초 이상이 필요할 수 있지만, 균형 제어, 모터 전류 제어, 접촉 안정화(Contact Stabilization), 액추에이터 통신에는 결정론적인 밀리초 또는 서브밀리초 주기(Deterministic Millisecond or Sub-millisecond Cycle)가 필요할 수 있다. 따라서 런타임은 최선형 AI 실행(Best-effort AI Execution)을 하드 또는 소프트 실시간 영역(Hard or Soft Real-time Domain)과 분리하고, 제어되지 않은 실행 문맥을 공유하는 대신 제한된 인터페이스(Bounded Interface)를 통해 통신하도록 한다.

컴퓨팅 자원 관리(Computing Resource Management)는 CPU, GPU, AI 가속기(AI Accelerator), 메모리, 스토리지 및 네트워크 대역폭을 조정한다. 대규모 VLM 또는 VLA 추론 워크로드가 위치 추정, 제어, 진단 또는 안전 관련 통신에 필요한 자원을 소진해서는 안 된다. 런타임 정책은 프로세스 우선순위, CPU 어피니티(CPU Affinity), GPU 메모리 예산, 추론 대기열(Inference Queue), 대역폭 제한 및 열적 제약(Thermal Constraint)을 설정할 수 있다. 자원 인식 스케줄링(Resource-aware Scheduling)은 계산 비용이 높은 AI 서비스가 필수 로봇 기능을 불안정하게 만드는 대신 점진적으로 성능을 낮추도록 한다.

통신 미들웨어(Communication Middleware)는 런타임 구성요소 사이의 데이터 교환 백본(Data Exchange Backbone)을 제공한다. ROS 2와 DDS는 인식, 의미론적 상태, 작업 및 진단 정보를 분산할 수 있으며, 이더캣(EtherCAT), CAN FD 또는 기타 결정론적 네트워크는 제어기와 액추에이터를 연결할 수 있다. 이더넷(Ethernet)은 고대역폭 센서와 컴퓨팅 노드를 지원한다. 런타임은 네트워크 혼잡이 액추에이터 동작에 예측할 수 없는 형태로 전파되지 않도록 의미론적 미들웨어 트래픽과 시간 결정적 제어 통신 사이에 명확한 경계를 정의해야 한다.

시간 동기화(Time Synchronization)는 센싱, 추론, 월드 모델링(World Modeling), 계획 및 실행 전반에 공통 시간 기준(Common Temporal Reference)을 제공한다. 카메라 프레임, 라이다 측정값, IMU 데이터, 관절 상태, 힘 측정값, AI 결과 및 제어 이벤트는 일관된 타임스탬프를 가져야 한다. PTP 또는 하드웨어 지원 동기화(Hardware-supported Synchronization)를 사용하면 분산 컴퓨팅 노드 사이의 시간 정렬을 향상시킬 수 있다. 신뢰할 수 있는 시간 정보는 런타임이 정보의 최신성을 판단하고, 멀티모달 관측을 연관시키고, 이벤트를 재구성하며, 오래된 명령이나 월드 상태 정보를 거부할 수 있도록 한다.

수명주기 관리(Lifecycle Management)는 런타임 구성요소의 시작, 초기화, 준비, 운영, 성능 저하(Degradation), 재시작, 업데이트 및 종료를 제어한다. 서비스가 운영 상태가 되기 전에 의존 관계를 해결해야 하며, 상태 검사(Health Check)를 통해 필요한 센서, 제어기, 모델 및 통신 인터페이스가 사용 가능한지를 검증해야 한다. 구성요소에 장애가 발생하면 허용되는 범위에서 런타임이 이를 격리하거나 재시작할 수 있다. 명시적인 수명주기 상태는 부분적으로 초기화된 AI 또는 로보틱스 서비스가 너무 이른 시점에 물리적 실행에 참여하는 것을 방지한다.

진단 및 관측 가능성(Diagnostics and Observability)은 전체 피지컬 AI 스택의 동작을 확인할 수 있는 가시성을 제공한다. 로그, 트레이스(Trace), 메트릭(Metric), 모델 추론 시간, 제어기 상태, 네트워크 지연, GPU 사용률, 메모리 소비, 센서 상태, 스킬 전환 및 실패 이벤트를 동기화된 타임스탬프를 사용하여 연관시킬 수 있다. 이러한 정보는 문제 해결과 신뢰성 분석을 지원하는 동시에 모델 평가, 회귀 시험(Regression Testing), 플릿 유지보수(Fleet Maintenance) 및 향후 시스템 개선을 위한 구조화된 운영 근거를 제공한다.

소프트웨어 요청이 궁극적으로 물리적 행동으로 이어질 수 있기 때문에 보안(Security)은 런타임 인터페이스를 보호해야 한다. 인증(Authentication)과 권한 부여(Authorization)는 어떤 프로세스, 모델, 사용자 또는 외부 서비스가 로봇 기능에 접근할 수 있는지를 결정한다. 안전한 소프트웨어 업데이트, 서명된 모델 아티팩트(Signed Model Artifact), 암호화된 외부 통신, 무결성 검사(Integrity Checking), 자격 증명 관리(Credential Management), 감사 로깅(Audit Logging)은 실행 환경을 보호한다. 도구 및 스킬 권한은 최소 권한 원칙(Least-privilege Principle)을 적용하여 하나의 AI 서비스가 침해되더라도 자동으로 제한 없는 로봇 제어 권한을 획득하지 못하도록 해야 한다.

엣지 및 클라우드 서비스(Edge and Cloud Service)는 안전한 로컬 동작의 필수 전제조건이 되지 않으면서 런타임 기능을 확장할 수 있다. 원격 인프라는 대규모 모델 추론, 플릿 분석(Fleet Analytics), 모델 학습, 데이터 관리, 소프트웨어 배포 및 장기 모니터링을 제공할 수 있다. 온보드 런타임(Onboard Runtime)은 연결이 저하되거나 사용할 수 없는 경우에도 필수 인식, 계획, 진단, 안전 감독 및 제어 기능을 유지해야 한다. 원격에서 생성된 결과도 물리적 행동에 영향을 미치기 전에 로컬에서 생성된 AI 출력과 동일한 검증 경계를 통과해야 한다.

피지컬 AI 런타임은 궁극적으로 체화 지능이 신뢰할 수 있는 기계 동작으로 전환되는 통합 경계(Integration Boundary)를 제공한다. VLM은 의미론적 이해(Semantic Understanding)를 제공하고, VLA는 인식과 행동을 연결하며, 에이전트는 목표를 관리하고, 멀티 에이전트 조정(Multi-agent Coordination)은 분산 행동을 조직하며, 파운데이션 모델은 재사용 가능한 지능을 제공한다. 런타임은 이러한 기능을 월드 상태, 스킬, 자원, 통신, 진단, 검증, 복구 및 결정론적 제어와 결합하여 확장 가능하고 신뢰할 수 있는 휴머노이드 피지컬 AI 운영에 필요한 실행 기반을 형성한다.
