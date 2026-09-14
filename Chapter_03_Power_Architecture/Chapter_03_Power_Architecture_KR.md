**Volume 21. Humanoid Electrical Architecture**

# Chapter 03. Power Architecture

## 03.01. 48V System

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

48V 전기 시스템(48 V Electrical System)은 휴머노이드 로봇(Humanoid Robot)에서 액추에이터 출력(Actuator Power), 도체 크기(Conductor Size), 전력 변환 효율(Conversion Efficiency), 전기 안전(Electrical Safety) 사이의 균형을 제공하는 실용적인 전력 백본(Power Backbone)이다. 기존의 12V 또는 24V 아키텍처(Architecture)와 비교하면 높은 배전 전압(Distribution Voltage)은 동일한 기계적 출력에 필요한 전류를 감소시켜 더 가벼운 와이어 하니스(Wire Harness)와 낮은 저항 손실(Resistive Loss)을 구현하면서도 소형 이동형 로봇 플랫폼에 적합한 특성을 유지할 수 있다.

휴머노이드의 전력 수요(Power Demand)는 보행, 물체 들어 올리기, 자세 복구, 동적 조작(Dynamic Manipulation) 과정에서 수십 개의 관절(Joint)이 동시에 가속될 수 있기 때문에 많은 고정형 로봇과 근본적으로 다르다. 고관절(Hip), 무릎(Knee), 발목(Ankle), 어깨(Shoulder), 몸통(Torso) 액추에이터는 평균 소비전력을 크게 초과하는 짧은 고출력 과도상태(High-Power Transient)를 발생시킬 수 있다. 따라서 48V 버스(48 V Bus)는 정격 출력만이 아니라 연속적인 에너지 흐름과 급격한 피크 전류(Peak Current) 공급 능력을 함께 고려하여 설계해야 한다.

배터리 팩(Battery Pack)은 일반적으로 48V 전력 도메인(Power Domain)의 주 에너지원이며 보호 및 스위칭 장치(Protection and Switching Device)를 거쳐 중앙 전력 분배 경로(Central Power Distribution Path)에 에너지를 공급한다. 배터리 전압은 배터리 화학계(Battery Chemistry), 충전 상태(State of Charge), 부하(Load), 온도(Temperature), 운전 조건에 따라 변하기 때문에 48V는 일정하게 유지되는 전압이라기보다 공칭 시스템 등급(Nominal System Class)을 의미한다. 모터 드라이브(Motor Drive)와 하위 컨버터(Downstream Converter)는 규정된 전체 동작 전압 범위와 과도상태 범위를 견딜 수 있어야 한다.

일반적인 아키텍처에서는 배터리 에너지가 메인 퓨즈(Main Fuse), 절연 또는 서비스 차단기(Service Disconnect), 컨택터 단계(Contactor Stage), 프리차지 회로(Precharge Circuit), 전류 센싱(Current Sensing), 전력 분배 장치(Power Distribution Unit)를 통과하도록 구성한다. 이 중앙 경로에서 보호된 분기 회로(Protected Branch)가 액추에이터 그룹, 컴퓨팅 장비(Computing Equipment), 인지 전자장치(Perception Electronics), 냉각 시스템(Cooling System), 보조 컨버터(Auxiliary Converter)에 전력을 공급한다. 이러한 구조는 하나의 분기 회로 고장이 전체 전기 기능을 불필요하게 정지시키는 것을 방지하면서 고장 영역을 선택적으로 격리할 수 있도록 한다.

프리차지(Precharge)는 대용량 직류 링크 커패시터(DC-Link Capacitor)를 포함하는 여러 모터 인버터(Motor Inverter)에 48V 버스가 전력을 공급할 때 특히 중요하다. 직접 연결하면 심각한 돌입전류(Inrush Current), 컨택터 아크(Contactor Arcing), 커넥터 스트레스(Connector Stress), 비정상적인 전압 변동이 발생할 수 있다. 제어된 프리차지 경로는 메인 컨택터가 닫히기 전에 분산된 커패시턴스(Distributed Capacitance)를 점진적으로 충전하며, 전압 모니터링(Voltage Monitoring)을 통해 버스가 허용 가능한 임계값에 도달했는지를 확인한 후 전체 전력 운전을 시작한다.

액추에이터 네트워크(Actuator Network)는 일반적으로 48V 시스템에서 가장 큰 부하를 차지한다. 관절 모터 드라이버(Joint Motor Driver)는 직류 버스 에너지를 브러시리스 모터(Brushless Motor)를 위한 제어된 상전류(Phase Current)로 변환하고, 로컬 제어기(Local Controller)는 위치(Position), 속도(Velocity), 토크(Torque), 임피던스(Impedance)를 제어한다. 고출력 관절에는 독립적인 보호 분기 회로를 적용할 수 있으며 작은 관절들은 지역별 전력 공급 경로(Regional Feed)를 공유할 수 있다. 이러한 구성은 전기 아키텍처가 휴머노이드 신체의 물리적 구조를 따라 배치될 수 있도록 한다.

지역별 전력 분배(Regional Power Distribution)는 로봇을 몸통(Torso), 왼팔(Left Arm), 오른팔(Right Arm), 왼쪽 다리(Left Leg), 오른쪽 다리(Right Leg), 머리(Head), 보조 영역(Auxiliary Zone)으로 구분할 수 있다. 몸통에는 배터리, 주 전력 분배 장치(Main PDU), 안전 스위칭(Safety Switching), 상위 컴퓨팅(High-Level Computing)을 배치하고 각 팔다리에는 로컬 전력 분배 모듈(Local Distribution Module)을 배치할 수 있다. 이러한 구역화(Zoning)는 긴 고전류 케이블을 줄이고 조립, 진단, 모듈 교체, 기계적 공간이 제한된 관절 구조 내부의 하니스 라우팅(Harness Routing)을 단순화한다.

휴머노이드의 하니스는 도체 직경과 굽힘 반경(Bend Radius)이 제한된 좁은 관절과 움직이는 구조를 통과하기 때문에 전압 강하(Voltage Drop)가 매우 중요하다. 설계에서는 피크 전류, 케이블 저항(Cable Resistance), 커넥터 저항(Connector Resistance), 온도 상승(Temperature Rise), 허용 전압 강하(Allowable Voltage Sag), 반복 굽힘(Repetitive Flexing)을 동시에 고려해야 한다. 과도한 전압 강하는 여러 관절이 최대 동적 출력을 요구하는 순간 액추에이터의 토크 성능을 감소시키거나 저전압 보호(Undervoltage Protection)를 작동시킬 수 있다.

48V 전력 도메인은 동일한 배터리에서 에너지를 공급받더라도 저전압 전자장치(Low-Voltage Electronics)와 논리적으로 분리하는 것이 바람직하다. 절연형 또는 비절연형 DC-DC 컨버터(Isolated or Non-Isolated DC-DC Converter)를 이용하여 컴퓨터, 센서, 통신 장치, 엔코더(Encoder), 제어 전자장치가 요구하는 안정화된 24V, 12V, 5V 또는 기타 전원 레일(Power Rail)을 생성할 수 있다. 이를 통해 민감한 전자장치가 고전류 전기기계 부하(Electromechanical Load)에서 발생하는 큰 전기적 교란에 직접 노출되는 것을 방지할 수 있다.

회생 에너지(Regenerative Energy) 역시 고려해야 한다. 휴머노이드 관절은 보행과 균형 제어(Balance Control) 과정에서 빈번하게 부하를 감속하거나 기계적 에너지를 흡수한다. 모터 드라이브는 이러한 에너지를 직류 버스로 반환할 수 있으며, 배터리 또는 다른 부하가 이를 충분히 빠르게 흡수하지 못하면 버스 전압이 상승할 수 있다. 따라서 배터리 충전 수용 능력(Battery Charge Acceptance), 인버터 한계(Inverter Limit), 버스 커패시턴스(Bus Capacitance), 제동 전략(Braking Strategy), 과전압 보호(Overvoltage Protection)를 전체 48V 전력 설계의 일부로 고려해야 한다.

접지(Grounding)와 전자파 적합성(Electromagnetic Compatibility)은 전력 아키텍처와 밀접하게 연계된다. 모터 인버터의 빠른 스위칭은 공통 모드(Common-Mode) 및 차동 모드(Differential-Mode) 노이즈를 발생시켜 엔코더, 카메라, 관성 측정 장치(IMU), 힘 센서(Force Sensor), 이더넷(Ethernet), 실시간 통신 네트워크(Real-Time Communication Network)에 간섭할 수 있다. 따라서 제어된 리턴 경로(Return Path), 적절한 차폐(Shielding), 필터링(Filtering), 섀시 본딩(Chassis Bonding), 커넥터 설계, 노이즈가 큰 전력 회로와 민감한 신호 회로 사이의 물리적 분리가 필수적이다.

보호 시스템(Protection System)은 하나의 메인 퓨즈에만 의존하지 않고 여러 계층에서 협조적으로 구성해야 한다. 배터리 분기(Battery Branch)는 치명적인 전원 고장으로부터 시스템을 보호하고, 전력 분배 장치는 주요 배전 경로를 보호하며, 로컬 보호(Local Protection)는 개별 액추에이터 또는 보조 회로를 격리할 수 있다. 전자식 전류 모니터링(Electronic Current Monitoring)은 추가적인 진단 가시성(Diagnostic Visibility)을 제공하고 보다 빠른 제어 정지를 가능하게 한다. 보호 임계값은 정상적인 가속 피크를 허용하면서 지속적인 고장 에너지가 배선이나 전자장치를 손상시키지 않도록 설정해야 한다.

전력 모니터링(Power Monitoring)은 전기적 보호뿐만 아니라 로봇 수준의 지능에도 필요한 정보를 제공한다. 팩 전압(Pack Voltage), 분기 전류(Branch Current), 컨버터 상태(Converter Status), 온도, 필요한 경우 절연 또는 누설 상태(Insulation or Leakage Condition), 누적 에너지(Accumulated Energy) 등의 측정값을 상위 제어기(Supervisory Controller)와 공유할 수 있다. 이를 통해 로봇은 남은 운용 시간을 추정하고 비정상적인 액추에이터 전력 소비를 식별하며, 열적 스트레스 상황에서 성능을 낮추고 가용성이 저하되기 전에 충전 또는 유지보수를 계획할 수 있다.

기능 안전(Functional Safety)을 위해서는 48V 아키텍처가 인지, 진단 또는 통신 기능을 불필요하게 종료시키지 않으면서 액추에이터 에너지를 제어된 방식으로 제거하거나 제한할 수 있어야 한다. 비상 상황에서는 토크를 발생시키는 전력 분기(Torque-Producing Branch)를 차단하면서 로그 기록과 고장 보고를 위한 보호된 저전력 도메인(Low-Power Domain)은 계속 활성화할 수 있다. 구체적인 분할 방식은 안전 개념(Safety Concept)에 따라 달라지지만 전력 도메인 경계는 제어 및 통신 경계와 함께 정의해야 한다.

기계적 통합(Mechanical Integration)은 전력 시스템이 지속적으로 움직이는 구조 내부에서 작동하기 때문에 전기적 신뢰성(Electrical Reliability)에 큰 영향을 준다. 커넥터와 케이블은 진동(Vibration), 반복 굽힘, 관절 운동, 충격 하중(Shock Load), 유지보수 사이클(Maintenance Cycle)을 견뎌야 한다. 팔다리 인터페이스(Limb Interface)는 관련 없는 하니스 구간을 분해하지 않고도 모듈을 교체할 수 있도록 설계하는 것이 바람직하다. 극성 구분(Polarization), 잠금 장치(Locking Mechanism), 스트레인 릴리프(Strain Relief), 접촉 보호(Touch Protection), 서비스 차단 기능은 조립 오류와 의도하지 않은 전원 인가를 방지하는 데 도움이 된다.

배터리 셀(Battery Cell), 컨택터, 컨버터, 커넥터, 도체, 모터 드라이브는 모두 열을 발생시키기 때문에 열 설계(Thermal Design)도 매우 중요하다. 실험실 조건에서 결정된 정격 전류(Current Rating)는 공기 흐름이 제한된 밀폐형 몸통이나 팔다리 구조 내부에서는 그대로 적용되지 않을 수 있다. 따라서 전기적 디레이팅(Electrical Derating)은 단순히 부품의 명판 정격에 의존하지 않고 주변 온도(Ambient Temperature), 듀티 사이클(Duty Cycle), 인접 열원(Neighboring Heat Source), 냉각 아키텍처(Cooling Architecture), 최악 조건의 동작 프로파일(Worst-Case Motion Profile)을 반영해야 한다.

견고한 48V 휴머노이드 아키텍처는 궁극적으로 단순한 배터리와 배선 시스템이 아니라 에너지 관리 네트워크(Energy-Management Network)로 동작한다. 배터리 관리(Battery Management), 전력 분배(Power Distribution), 관절 드라이브(Joint Drive), DC-DC 변환(DC-DC Conversion), 안전 제어(Safety Control), 진단(Diagnostics), 열 관리(Thermal Supervision), 회생 에너지 처리가 로봇의 전체 신체에 걸쳐 상호 협력해야 한다. 이러한 통합적 접근 방식은 높은 순간 기계 출력(Transient Mechanical Power)을 제공하면서도 효율(Efficiency), 고장 격리(Fault Containment), 정비성(Serviceability), 예측 가능한 시스템 동작(Predictable System Behavior)을 동시에 확보할 수 있도록 한다.

## 03.02. 72V System

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

72V 전기 시스템(72 V Electrical System)은 휴머노이드 로봇(Humanoid Robot)의 전력 공급 능력을 일반적으로 48V 아키텍처(48 V Architecture)가 담당하는 범위보다 높은 수준으로 확장한다. 배전 전압(Distribution Voltage)을 높이면 전류를 비례해서 증가시키지 않고도 더 큰 기계적 출력(Mechanical Power)을 전달할 수 있다. 이는 특히 다리, 고관절(Hip), 몸통(Torso), 팔 액추에이터(Actuator)가 높은 토크(Torque)를 발생시키면서도 적절한 케이블 질량과 열적 성능(Thermal Performance)을 유지해야 하는 대형 휴머노이드에서 중요한 장점이 된다.

72V 배전(72 V Distribution)의 주요 전기적 장점은 동일한 출력 수준에서 필요한 전류를 감소시킬 수 있다는 것이다. 도체 손실(Conductor Loss)은 전류의 제곱에 비례하기 때문에 버스 전압(Bus Voltage)을 높이면 케이블, 커넥터(Connector), 컨택터(Contactor), 전력 분배 장치에서 발생하는 저항성 발열(Resistive Heating)을 크게 줄일 수 있다. 또한 낮은 전류는 더 작은 도체 단면적(Conductor Cross Section)을 사용할 수 있게 하므로 몸통과 여러 관절형 팔다리 전체에 전기 배선이 배치되는 로봇에서 하니스 중량(Harness Weight)을 줄이는 데 도움이 된다.

공칭 72V 배터리(Nominal 72 V Battery)는 사용 가능한 전체 충전 상태(State of Charge)에서 항상 정확히 72V로 동작하지 않는다. 실제 버스 전압은 셀 화학계(Cell Chemistry), 직렬 셀 개수(Series Cell Count), 충전 한계(Charging Limit), 방전 상태(Discharge State), 온도, 순간 부하(Instantaneous Load)에 따라 달라진다. 따라서 주 버스(Primary Bus)에 연결되는 모든 부품은 단순한 공칭 72V 기준이 아니라 발생 가능한 최대 동작 전압(Maximum Operating Voltage)과 과도 전압(Transient Voltage)을 기준으로 선정해야 한다.

배터리 인터페이스(Battery Interface)는 일반적으로 메인 퓨즈(Main Fuse), 서비스 차단기(Service Disconnect), 컨택터, 프리차지 회로(Precharge Circuit), 전류 센싱(Current Sensing), 전력 분배 장치(Power Distribution Unit)를 포함한다. 이러한 요소는 배터리에 저장된 에너지와 로봇의 분산 전기 부하(Distributed Electrical Load) 사이에 제어 가능한 경계를 형성한다. 아키텍처는 안전한 기동(Startup), 정상 운전, 고장 격리(Fault Isolation), 제어된 종료(Controlled Shutdown), 유지보수, 비상 전원 차단을 지원하면서 영향을 받지 않은 서브시스템(Subsystem)의 불필요한 정지를 최소화해야 한다.

버스 전압과 설치된 인버터 용량(Inverter Capacity)이 증가할수록 프리차지(Precharge)의 중요성도 높아진다. 관절 모터 드라이브(Joint Motor Drive)는 초기 방전 상태에서 낮은 임피던스 부하처럼 동작하는 직류 링크 커패시터(DC-Link Capacitor)를 포함한다. 이를 72V 배터리에 직접 연결하면 상당한 돌입전류(Inrush Current)가 발생할 수 있다. 프리차지 저항(Precharge Resistor)과 제어된 스위칭 경로(Controlled Switching Path)는 메인 컨택터가 닫히기 전에 하위 버스 전압을 점진적으로 상승시켜 전력 부품에 가해지는 전기적·기계적 스트레스를 줄인다.

고출력 관절 액추에이터(High-Power Joint Actuator)는 72V 전력 도메인(Power Domain)을 직접 적용하기에 적합한 대상이다. 고관절, 무릎(Knee), 발목(Ankle), 어깨(Shoulder), 몸통 드라이브(Torso Drive)는 높은 전압을 사용함으로써 모터 드라이버(Motor Driver)가 높은 모터 회전속도에서 상전류(Phase Current)를 제어하는 데 필요한 더 큰 전압 여유(Voltage Headroom)를 확보할 수 있다. 이를 통해 활용 가능한 토크-속도 영역(Torque-Speed Envelope)을 향상시키면서 해당 전력을 로봇 내부로 전달하는 데 필요한 직류 측 전류(DC-Side Current)를 줄일 수 있다.

72V 시스템의 장점은 동적인 전신 운동(Dynamic Whole-Body Motion)에서 특히 중요해진다. 보행 가속(Walking Acceleration), 계단 오르기, 물체 들어 올리기, 점프, 외란 복구(Disturbance Recovery), 화물 운반 등의 동작에서는 여러 주요 관절이 동시에 높은 출력을 발생시켜야 할 수 있다. 따라서 배전 아키텍처(Distribution Architecture)는 각 액추에이터가 서로 독립적으로 최대 부하에 도달한다고 가정하거나 평균 배터리 출력(Average Battery Power)이 순간 요구사항을 충분히 나타낸다고 가정하지 않고, 서로 연관된 부하 피크(Correlated Load Peak)를 기준으로 설계해야 한다.

높은 전압의 전력 백본(Power Backbone)을 사용하더라도 지역별 전력 분배(Regional Distribution)는 여전히 유용하다. 중앙 전력 분배 장치(PDU)는 보호된 72V 분기 회로를 몸통, 팔, 다리 방향으로 분배하고, 지역별 전력 분배 모듈(Regional Distribution Module)은 로컬 모터 드라이브까지 더 짧은 전력 연결을 제공할 수 있다. 이러한 구역형 접근 방식(Zonal Approach)은 긴 고전류 경로를 제한하고 하니스 라우팅(Harness Routing)을 단순화하며 고장 위치 식별(Fault Localization)을 개선하고, 휴머노이드의 다른 부분을 광범위하게 분해하지 않고도 팔다리 모듈을 전기적으로 분리하거나 교체할 수 있게 한다.

72V 아키텍처에서는 전압 도메인 분할(Voltage-Domain Partitioning) 역시 신중하게 설계해야 한다. 고출력 액추에이터는 메인 버스(Main Bus)에서 직접 동작할 수 있지만 인지(Perception), 통신(Communication), 컴퓨팅(Computing), 제어(Control), 보조 전자장치(Auxiliary Electronics)는 일반적으로 더 낮고 안정화된 전압을 요구한다. 따라서 DC-DC 컨버터(DC-DC Converter)를 이용하여 48V, 24V, 12V, 5V 또는 기타 필요한 전원 레일(Power Rail)을 생성하고 필터링(Filtering)과 필요한 경우 전력 도메인 사이의 갈바닉 절연(Galvanic Isolation)을 제공할 수 있다.

DC-DC 변환(DC-DC Conversion)은 전체 배터리 전압 범위와 모터 동작에서 발생하는 과도상태 환경(Transient Environment)을 모두 수용해야 한다. 컨버터를 선정할 때는 효율(Efficiency), 연속 및 피크 출력(Continuous and Peak Output Power), 기동 특성(Startup Behavior), 열적 한계(Thermal Limit), 입력 필터링(Input Filtering), 고장 대응(Fault Response), 전자파 적합성(Electromagnetic Compatibility)을 고려해야 한다. 중요한 저전압 전자장치에는 독립적인 보호 기능이나 에너지 유지 기능(Energy Hold-Up)을 적용하여 액추에이터 버스의 짧은 전기적 교란으로 인해 컴퓨팅 장치 또는 안전 제어기(Safety Controller)가 즉시 재설정되는 것을 방지할 수 있다.

회생 운전(Regenerative Operation)은 72V 버스에 상당한 전기적 스트레스를 발생시킬 수 있다. 관절 감속, 하강 동작 또는 균형 제어(Balance Control)를 위한 에너지 흡수 과정에서 모터 드라이브는 에너지를 공통 직류 링크(Common DC Link)로 반환할 수 있다. 배터리가 이러한 회생 전력(Regenerative Power)을 받아들이지 못하면 버스 전압이 빠르게 상승할 수 있다. 따라서 아키텍처에서는 배터리 충전 한계(Battery Charge Limit), 인버터 제어(Inverter Control), 버스 커패시턴스(Bus Capacitance), 회생 토크 제한(Regenerative Torque Limitation), 선택적인 제동 또는 에너지 소산 장치(Energy-Dissipation Mechanism)를 상호 조정해야 한다.

따라서 배터리 관리(Battery Management)는 전신 운동 제어(Whole-Body Motion Control)와 긴밀하게 연계된다. 배터리 관리 시스템(BMS)은 충전 상태(State of Charge), 전류 한계(Current Limit), 온도, 셀 전압 상태(Cell Voltage Condition), 허용 충전 및 방전 출력(Allowable Charging and Discharging Power)과 같은 정보를 제공해야 한다. 상위 제어기(Supervisory Controller)는 이러한 한계를 활용하여 전기적 보호 기능이 작동하기 전에 액추에이터 동작을 제한하고, 로봇이 가속도, 적재 능력(Payload Capability), 회생 제동 강도(Regenerative Braking Intensity)를 제어된 방식으로 감소시킬 수 있도록 한다.

72V 전원(Source)은 상당한 고장 에너지(Fault Energy)를 공급할 수 있기 때문에 보호 협조(Protection Coordination)가 필수적이다. 메인 배터리 보호(Main Battery Protection)는 심각한 전원 측 고장을 처리하고, 전력 분배 장치는 주요 분기 회로를 선택적으로 보호하며, 로컬 보호 장치(Local Protection Device)는 개별 부하를 보호해야 한다. 퓨즈 정격(Fuse Rating), 전자식 회로 보호(Electronic Circuit Protection), 컨택터 차단 용량(Contactor Interrupt Capability), 커넥터 정격, 도체 허용전류(Conductor Ampacity), 고장 전류 특성(Fault-Current Characteristic)은 개별적으로가 아니라 하나의 통합된 보호 시스템으로 평가해야 한다.

높은 전압으로 배전 전류가 감소하더라도 전압 강하(Voltage Drop)는 여전히 중요하다. 동적인 액추에이터 부하는 케이블 임피던스(Cable Impedance), 커넥터 저항, 배터리 임피던스(Battery Impedance), 공유 배전 경로(Shared Distribution Path)를 통해 빠른 버스 전압 변동을 발생시킬 수 있다. 과도한 로컬 전압 강하는 모터 드라이브의 저전압 고장(Undervoltage Fault)을 발생시킬 수 있으며, 회생 동작은 과전압 상태(Overvoltage Condition)를 만들 수 있다. 적절한 도체 크기, 버스 커패시턴스, 배전 토폴로지(Distribution Topology), 제어 협조(Control Coordination)를 통해 허용 가능한 전압 안정성(Voltage Stability)을 유지해야 한다.

전자파 적합성(Electromagnetic Compatibility)은 고전압 버스가 로봇 신체 전체에 분산된 여러 고주파 스위칭 모터 드라이브(High-Frequency Switching Motor Drive)에 전력을 공급하기 때문에 더욱 중요한 설계 요소가 된다. 빠른 인버터 스위칭은 엔코더(Encoder), 힘 및 토크 센서(Force and Torque Sensor), 관성 측정 장치(IMU), 카메라, 이더넷(Ethernet) 링크, 안전 회로(Safety Circuit)에 노이즈를 결합시킬 수 있다. 신호 무결성(Signal Integrity)을 유지하기 위해 하니스 분리, 제어된 접지(Grounding), 차폐(Shielding), 공통 모드 관리(Common-Mode Management), 필터링, 섀시 본딩(Chassis Bonding), 신중하게 설계된 귀환 전류 경로(Return-Current Path)가 필요하다.

열 관리(Thermal Management)는 집중 손실(Concentrated Loss)과 분산 손실(Distributed Loss)을 모두 고려해야 한다. 높은 전압을 사용하면 하니스 손실을 감소시킬 수 있지만 배터리 셀(Battery Cell), 컨버터, 컨택터, 모터 드라이브, 커넥터, 보호 장치는 여전히 열을 발생시킨다. 따라서 부품 정격은 이상적인 실험실 운전 조건을 가정하지 않고 인클로저 온도(Enclosure Temperature), 공기 흐름(Airflow), 냉각 구성(Cooling Configuration), 듀티 사이클(Duty Cycle), 동시 액추에이터 부하(Simultaneous Actuator Loading), 환경 조건(Environmental Condition)을 기준으로 디레이팅(Derating)해야 한다.

48V에서 72V 아키텍처로 전환하면 유지보수 및 정비(Service) 측면에서도 변화가 발생한다. 커넥터 인터페이스(Connector Interface), 노출된 도전부(Exposed Conductive Part), 차단 절차(Disconnect Procedure), 라벨링(Labeling), 절연(Insulation), 인터록(Interlock), 정비 작업자의 접근 방식은 시스템에서 사용할 수 있는 증가된 전기 에너지 수준을 반영해야 한다. 모듈형 팔다리 교체(Modular Limb Replacement)에는 명확한 무전압화(De-Energization) 및 확인 절차(Verification Procedure)를 포함하여 정비 작업이 소프트웨어 명령이나 컨택터 상태에 대한 추정에만 의존하지 않도록 해야 한다.

기능 안전(Functional Safety)은 위험한 액추에이터 에너지(Hazardous Actuator Energy)의 제거와 필수 저전력 기능(Essential Low-Power Function)의 유지를 구분해야 한다. 비상 정지(Emergency Stop)는 선택된 72V 모터 분기 회로를 차단하거나 비활성화하면서 안전 제어기, 인지 시스템, 통신, 진단(Diagnostics), 이벤트 로깅(Event Logging)에 필요한 보호 전원은 유지할 수 있다. 이러한 전력 도메인 분리(Power-Domain Separation)는 로봇이 제어된 안전 상태(Controlled Safe State)로 진입하면서도 정지 원인을 식별하고 외부에 전달할 수 있는 충분한 전기적 기능을 유지하도록 한다.

잘 설계된 72V 휴머노이드 아키텍처는 단순히 48V 시스템의 전압만 높인 구조가 아니다. 배터리, 배터리 관리 시스템(BMS), 컨택터, 프리차지 시스템(Precharge System), 전력 분배 장치(PDU), 지역별 전력 분배, 모터 드라이브, DC-DC 컨버터, 회생 에너지 처리(Regenerative-Energy Handling), 접지, 보호, 진단, 열 관리, 안전 도메인(Safety Domain)을 상호 조정하여 설계해야 한다. 이러한 요소를 하나의 시스템으로 통합하여 엔지니어링하면 72V 배전은 하니스 질량, 전기적 손실(Electrical Loss), 열적 스트레스(Thermal Stress), 시스템 수준 위험(System-Level Risk)을 관리하면서 더 높은 성능의 휴머노이드 로봇을 지원할 수 있다.

## 03.03. HV/LV Distribution

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

휴머노이드 로봇(Humanoid Robot)은 구동계 수준의 관절 액추에이터(Joint Actuator)와 민감한 전자 시스템이 근본적으로 서로 다른 전기적 조건에서 동작하기 때문에 고전압 및 저전압 배전 아키텍처(HV-LV Distribution Architecture)를 체계적으로 구성해야 한다. 고전압 도메인(HV Domain)은 집중적인 기계 출력을 공급하고, 저전압 도메인(LV Domain)은 컴퓨팅(Computing), 인지(Perception), 통신(Communication), 센싱(Sensing), 안전(Safety), 제어(Control)를 지원한다. 두 영역의 통합은 로봇 전체에서 효율, 전기적 절연(Electrical Isolation), 고장 격리(Fault Containment), 예측 가능한 동작을 보장해야 한다.

휴머노이드 플랫폼에서 고전압(High Voltage)이라는 용어는 저전압 전자장치 도메인과 비교하여 48V 또는 72V 아키텍처와 같은 주 구동 또는 액추에이터 버스(Primary Traction or Actuator Bus)를 의미할 수 있다. 정확한 분류는 시스템 요구사항과 적용되는 표준에 따라 달라진다. 용어상의 분류와 관계없이 주 전력 버스(Primary Power Bus)는 논리 수준 전원 레일(Logic-Level Rail)보다 훨씬 큰 전류와 에너지를 전달하므로 전용 스위칭(Switching), 보호(Protection), 배전(Distribution), 정비(Service) 전략이 필요하다.

배터리 에너지는 일반적으로 메인 퓨즈(Main Fuse), 서비스 차단기(Service Disconnect), 컨택터(Contactor), 프리차지 회로(Precharge Circuit), 전류 측정(Current Measurement)을 포함하는 보호된 주 전력 경로를 통해 로봇으로 공급된다. 이렇게 형성된 고전압 전력 버스(HV Power Bus)는 중앙 전력 분배 장치(Power Distribution Unit)를 거쳐 보호된 여러 분기 회로로 나뉜다. 이러한 분기 회로는 휴머노이드의 물리적·기능적 구역화(Zoning)에 따라 몸통 액추에이터, 좌우 팔, 좌우 다리 및 기타 고출력 모듈에 전력을 공급할 수 있다.

저전압 도메인은 일반적으로 하나 이상의 DC-DC 컨버터(DC-DC Converter)를 통해 주 전력 버스로부터 생성된다. 서브시스템(Subsystem)의 요구사항에 따라 로봇은 48V, 24V, 12V, 5V 또는 그보다 낮은 안정화 전원 레일(Regulated Power Rail)을 사용할 수 있다. 이러한 출력은 인공지능 컴퓨터(AI Computer), 실시간 제어기(Real-Time Controller), 카메라, 라이다(LiDAR), 관성 측정 장치(IMU), 엔코더(Encoder), 힘 센서(Force Sensor), 통신 스위치(Communication Switch), 냉각 장치(Cooling Device), 디스플레이(Display), 보조 전자장치(Auxiliary Electronics)에 전력을 공급하면서 액추에이터 버스의 전기적 교란에 직접 노출되는 것을 방지한다.

전력 도메인 분할(Power-Domain Partitioning)은 전기적 기능과 물리적 위치를 모두 고려해야 한다. 중앙 고전압 백본(Central HV Backbone)은 몸통과 팔다리에 위치한 지역별 전력 모듈(Regional Power Module)로 에너지를 분배할 수 있으며, 로컬 저전압 변환(Local LV Conversion)은 해당 부하 가까이에 배치할 수 있다. 이를 통해 긴 저전압·고전류 케이블 경로를 줄이고 도체 질량(Conductor Mass)을 감소시킬 수 있다. 그러나 분산형 전력 변환(Distributed Conversion)은 추가적인 열 관리, 패키징(Packaging), 전자파 적합성(EMC), 진단(Diagnostics), 정비성(Serviceability) 요구사항을 발생시킨다.

몸통(Torso)은 일반적으로 배터리, 메인 전력 분배 장치(Main PDU), 컨택터, 안전 전자장치(Safety Electronics), 중앙 컴퓨팅(Central Computing), 주요 DC-DC 컨버터를 수용할 수 있기 때문에 주 전기 허브(Primary Electrical Hub)의 역할을 수행한다. 이 영역에서 보호된 전력 경로가 팔, 다리, 머리 방향으로 확장된다. 지역별 전력 분배 모듈(Regional Distribution Module)은 이러한 전력 공급 경로를 다시 세분화하여 교체 가능한 기계 모듈과 밀접하게 대응하는 전기적 구역(Electrical Zone)을 형성하고 조립, 유지보수, 고장 위치 식별(Fault Localization)을 단순화할 수 있다.

다리는 고관절(Hip), 무릎(Knee), 발목(Ankle) 액추에이터가 체중 지지, 균형, 보행, 가속, 외란 복구(Disturbance Recovery)를 수행해야 하기 때문에 일반적으로 주요 고전압 소비 영역(HV Consumer)이 된다. 팔과 몸통 액추에이터도 물체를 들어 올리거나 조작하는 과정에서 상당한 순간 전력(Transient Power)을 요구할 수 있다. 반면 머리(Head)는 주로 카메라, 마이크, 인지 전자장치, 디스플레이, 통신 장치와 같은 저전압 부하(LV Load)를 포함하므로 전압 도메인 분할은 신체 부위의 기능과 밀접하게 연관된다.

고전압 및 저전압 배선(HV and LV Wiring)은 서로 동일한 하니스 요소로 취급해서는 안 된다. 고출력 도체(High-Power Conductor)는 허용전류(Current Capacity), 전압 강하(Voltage Drop), 온도 상승(Temperature Rise), 고장 전류(Fault Current), 커넥터 성능(Connector Capability), 기계적 라우팅(Mechanical Routing)을 고려하여 설계해야 한다. 저전압 전력선과 신호 배선은 노이즈 민감도(Noise Susceptibility)와 신호 무결성(Signal Integrity)에 특히 주의해야 한다. 스위칭 전력 경로와 민감한 통신 또는 센서 배선을 물리적으로 분리하면 움직이는 관절과 제한된 하니스 통로 전체에서 전자기 결합(Electromagnetic Coupling)을 줄일 수 있다.

접지 전략(Grounding Strategy)은 두 전압 도메인을 연결하는 중요한 인터페이스이다. 모터 드라이브(Motor Drive)와 DC-DC 컨버터는 전력 도체, 차폐(Shield), 섀시 구조(Chassis Structure), 통신 인터페이스를 통해 전파되는 고주파 공통 모드 전류(High-Frequency Common-Mode Current)를 발생시킬 수 있다. 귀환 경로(Return Path)가 적절하게 제어되지 않으면 엔코더, 관성 측정 장치, 카메라, 이더넷(Ethernet), 이더캣(EtherCAT), CAN FD 및 기타 네트워크에 영향을 줄 수 있다. 따라서 접지 기준(Ground Reference), 섀시 본딩(Chassis Bonding), 차폐(Shielding), 필터링(Filtering), 절연(Isolation)을 개별적으로가 아니라 하나의 시스템으로 설계해야 한다.

전기적 분리가 안전, 노이즈 제어 또는 고장 격리에 의미 있는 이점을 제공하는 영역에는 갈바닉 절연(Galvanic Isolation)을 적용할 수 있다. 절연형 DC-DC 컨버터(Isolated DC-DC Converter)와 절연형 통신 인터페이스(Isolated Communication Interface)는 선택된 도메인 사이에서 원하지 않는 전류 경로가 형성되는 것을 방지할 수 있다. 그러나 절연은 비용, 부피, 변환 손실(Conversion Loss), 설계 복잡성을 증가시키므로 무조건 적용해서는 안 된다. 각각의 절연 경계(Isolation Boundary)는 명확하게 정의된 전기적 또는 안전 요구사항에 대응해야 한다.

배전 아키텍처는 선택적 고장 격리(Selective Fault Isolation)를 지원해야 한다. 하나의 팔다리에서 단락(Short Circuit)이 발생한 경우 전체 로봇의 전원을 불필요하게 차단하지 않고 해당 분기 회로만 분리할 수 있는 것이 바람직하다. 마찬가지로 보조 저전압 장치 하나의 고장이 액추에이터 버스 전체를 정지시켜서는 안 된다. 협조된 퓨즈(Coordinated Fuse), 전자식 보호(Electronic Protection), 스마트 스위치(Smart Switch), 컨택터, 컨버터 보호(Converter Protection), 로컬 모니터링(Local Monitoring)을 통해 고장을 발생 지점 가까이에서 격리하면서 안전한 범위 내에서 정상 기능을 유지할 수 있다.

기능 안전(Functional Safety)은 전력 도메인을 분리해야 하는 또 다른 중요한 이유이다. 비상 정지(Emergency Stop) 상황에서는 토크를 발생시키는 액추에이터 전력을 신속하게 제거해야 하지만 일부 저전압 시스템은 계속 동작해야 할 수 있다. 안전 제어기(Safety Controller), 통신 인터페이스, 이벤트 로거(Event Logger), 인지 시스템, 진단 프로세서(Diagnostic Processor)는 안전 상태(Safe State)로의 전환을 관리하고, 이벤트를 기록하며, 상태를 외부에 전달하고, 제어된 복구 또는 유지보수 절차를 지원하기 위해 일정 시간 동안 계속 전원을 공급받을 필요가 있다.

기동 시퀀싱(Startup Sequencing)은 고전압 및 저전압 도메인의 동작 순서를 조정해야 한다. 일부 저전압 제어기는 메인 액추에이터 버스가 활성화되기 전에 동작하여 배터리 상태, 안전 조건, 통신 무결성(Communication Integrity), 컨택터 제어를 확인해야 할 수 있다. 이후 프리차지(Precharge)를 수행하여 고전압 버스를 형성한 다음 액추에이터를 활성화할 수 있다. 종료 과정에서는 반대 순서를 적용하여 고에너지 회로가 안전하게 비활성화되고 방전될 때까지 진단 및 로그 기록 기능을 유지할 수 있다.

DC-DC 컨버터는 고전압 및 저전압 배전을 연결하는 주요 아키텍처 브리지(Architectural Bridge)이다. 입력 전압 범위는 배터리 전압 변화, 스위칭 과도현상(Switching Transient), 회생 이벤트(Regenerative Event), 비정상 조건을 수용해야 하며 출력은 민감한 전자장치에 충분히 안정적인 전압을 공급해야 한다. 따라서 컨버터 효율, 열적 특성(Thermal Behavior), 출력 리플(Output Ripple), 절연, 기동 시퀀싱, 전류 제한(Current Limiting), 진단, 전자파 방출(Electromagnetic Emission)을 해당 컨버터가 지원하는 부하와 함께 평가해야 한다.

중요한 저전압 기능에는 선택적으로 이중화(Redundancy)를 적용할 수 있다. 휴머노이드는 안전 제어기, 통신 게이트웨이(Communication Gateway), 필수 컴퓨팅 자원(Essential Compute Resource)에 독립적인 컨버터 또는 보호된 전력 공급 경로를 사용하여 하나의 보조 전원 고장이 모든 상위 감독 기능(Supervisory Capability)을 즉시 상실시키지 않도록 할 수 있다. 이러한 이중화는 최종 컨버터만 단순히 복제하는 것이 아니라 관련 배선, 보호, 접지, 배전 경로에서 공통 고장 지점(Common Failure Point)을 제거할 때 가장 효과적이다.

회생 에너지(Regenerative Energy)는 주로 고전압 도메인에 영향을 주지만 저전압 시스템에도 간접적인 영향을 미칠 수 있다. 관절 모터가 감속 또는 하강 동작 중 기계적 에너지를 반환하면 주 버스 전압이 상승할 수 있다. DC-DC 컨버터는 이러한 전압 변화를 견디면서 과도한 전기적 교란을 출력 측으로 전달하지 않아야 한다. 따라서 배터리 충전 수용 능력(Battery Charge Acceptance), 회생 제어(Regenerative Control), 버스 커패시턴스(Bus Capacitance), 과전압 보호(Overvoltage Protection), 컨버터 입력 한계(Converter Input Limit)는 고전압과 저전압의 경계에서 상호 연계된다.

모니터링(Monitoring)은 두 전압 도메인의 상태를 모두 확인할 수 있어야 한다. 로봇은 배터리 전압, 고전압 분기 전류(HV Branch Current), 저전압 레일 전압(LV Rail Voltage), 컨버터 전류, 온도, 컨택터 상태, 보호 상태(Protection Status), 에너지 소비량을 측정할 수 있다. 이러한 측정값을 통합하면 상위 소프트웨어(Supervisory Software)는 배터리 한계, 액추에이터 고장, 컨버터 열화(Converter Degradation), 배선 문제, 비정상적인 서브시스템 부하를 구분할 수 있으며 예지 정비(Predictive Maintenance)와 에너지 인식형 임무 계획(Energy-Aware Mission Planning)을 지원할 수 있다.

열적 거동(Thermal Behavior) 역시 고전압 및 저전압 배전을 서로 연결한다. 고출력 컨택터, 커넥터, 모터 드라이브, 도체는 국부적인 열을 발생시키며, DC-DC 컨버터와 컴퓨팅 시스템은 몸통과 팔다리 내부에 추가적인 열 부하(Thermal Load)를 발생시킨다. 따라서 전기적 구역화(Electrical Zoning)는 냉각 아키텍처(Cooling Architecture)와 함께 설계해야 한다. 온도 센싱(Temperature Sensing)과 디레이팅 정책(Derating Policy)을 적용하면 지속적인 고출력 동작 중 열적으로 제한된 영역이 안전 운전 한계(Safe Operating Limit)를 초과하는 것을 방지할 수 있다.

정비성(Serviceability)은 초기 설계 단계부터 전력 도메인 경계에 반영해야 한다. 팔다리 모듈은 명확하게 정의된 전력 인터페이스(Power Interface), 커넥터 키잉(Connector Keying), 안전 차단 절차(Safe Disconnect Procedure), 방전 요구사항(Discharge Requirement), 진단 접근 기능(Diagnostic Access)을 갖추어야 한다. 정비 작업자는 고전압 에너지가 존재하는지와 저전압 제어 전원이 여전히 활성화되어 있는지를 확인할 수 있어야 한다. 전기적 구역이 기계적으로 교체 가능한 어셈블리(Replaceable Assembly)와 직접 대응하도록 모듈형 인터페이스(Modular Interface)를 설계하면 수리 시간을 크게 줄일 수 있다.

잘 설계된 고전압-저전압 배전 아키텍처(HV-LV Distribution Architecture)는 궁극적으로 휴머노이드 신체 전체에 체계적인 에너지 계층(Energy Hierarchy)을 형성한다. 배터리와 주 전력 버스는 고출력 에너지를 제공하고, 지역별 전력 분배는 이를 액추에이터 구역으로 전달하며, DC-DC 변환은 안정적인 전자장치 전원을 생성하고, 보호 및 모니터링 시스템은 각각의 경계를 감독한다. 이러한 계층을 통합적으로 조정하면 높은 동적 성능을 확보하면서 효율, 전자파 적합성 견고성(EMC Robustness), 고장 격리, 기능 안전, 모듈성(Modularity), 정비성을 동시에 유지할 수 있다.

## 03.04. Battery Modules

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

배터리 모듈(Battery Module)은 휴머노이드 로봇(Humanoid Robot) 전력 아키텍처에서 에너지를 저장하는 기본 구성 단위이다. 배터리를 하나의 일체형 부품(Monolithic Component)으로 취급하는 대신 모듈형 설계(Modular Design)는 필요한 전압, 용량, 기계 구조, 센싱(Sensing), 보호(Protection), 열 관리 기능을 관리 가능한 어셈블리(Assembly) 단위로 분할한다. 이러한 접근 방식은 다양한 크기와 성능 등급의 휴머노이드에서 패키징 유연성(Packaging Flexibility), 제조, 진단(Diagnostics), 정비성(Serviceability), 확장성(Scalability)을 향상시킨다.

각 배터리 모듈은 필요한 모듈 전압과 에너지 용량을 확보하기 위해 직렬 및 병렬로 연결된 전기화학 셀(Electrochemical Cell)의 정해진 배열로 구성된다. 직렬 연결(Series Connection)은 전압을 높이고 병렬 연결(Parallel Connection)은 사용 가능한 용량과 전류 공급 능력을 증가시킨다. 이후 여러 모듈을 조합하여 로봇의 액추에이터(Actuator) 및 컴퓨팅(Computing) 요구사항에 적합한 48V, 72V 또는 기타 시스템 수준 배터리 아키텍처(System-Level Battery Architecture)를 구성할 수 있다.

셀 화학계(Cell Chemistry)는 모듈 설계에 큰 영향을 미친다. 리튬이온(Lithium-Ion) 기술은 높은 에너지 밀도(Energy Density)와 출력 성능을 제공하지만 화학계에 따라 비에너지(Specific Energy), 사이클 수명(Cycle Life), 열적 안정성(Thermal Stability), 방전 성능(Discharge Capability), 충전 속도(Charging Rate), 비용, 동작 온도 사이에서 서로 다른 절충 관계가 존재한다. 선택된 화학계는 장시간 운전의 평균 에너지 소비뿐만 아니라 동적인 휴머노이드 운동에서 발생하는 짧은 고출력 요구도 지원해야 한다.

휴머노이드의 부하 프로파일(Load Profile)은 여러 관절이 가속, 감속 또는 외부 하중을 지지하면서 전력 소비가 빠르게 변화할 수 있기 때문에 배터리 모듈에 독특한 요구사항을 부여한다. 보행, 계단 오르기, 물체 들어 올리기, 균형 복구(Balance Recovery), 전신 조작(Whole-Body Manipulation)은 큰 과도 전류(Transient Current)를 발생시킬 수 있다. 따라서 모듈 설계에서는 정격 에너지 용량만을 기준으로 하지 않고 연속 전류, 피크 전류(Peak Current), 펄스 지속시간(Pulse Duration), 내부 저항(Internal Resistance), 전압 강하(Voltage Sag), 온도 상승, 회복 특성(Recovery Behavior)을 고려해야 한다.

각 모듈의 전기적 구성(Electrical Configuration)은 전체 배터리 팩 아키텍처와 호환되어야 한다. 충전 상태(State of Charge)에 따른 셀 전압 변화는 최소, 공칭, 최대 모듈 전압을 결정하며, 모듈 개수는 시스템 버스 전압 범위(System Bus Range)를 결정한다. 모터 드라이브(Motor Drive), DC-DC 컨버터(DC-DC Converter), 컨택터(Contactor), 보호 장치, 전력 분배 장치(PDU)는 충전, 방전, 회생(Regeneration), 과도 운전 조건에서 발생하는 전체 전압 범위를 견딜 수 있어야 한다.

배터리 모듈에는 안전하고 예측 가능한 동작을 유지하기 위한 통합 전압 및 온도 센싱(Integrated Voltage and Temperature Sensing)이 필요하다. 개별 셀 그룹 전압(Cell-Group Voltage)을 통해 불균형(Imbalance), 과충전(Overcharge), 과도한 방전, 진행 중인 셀 열화(Cell Degradation)를 확인할 수 있다. 대표적인 열적 위치에 배치된 온도 센서(Temperature Sensor)는 비정상적인 발열을 감지하고 전류 디레이팅(Current Derating)을 지원한다. 이러한 측정값은 전체 에너지 저장 시스템의 상태를 감독하는 배터리 관리 시스템(Battery Management System)의 입력으로 사용된다.

배터리 관리 시스템(BMS)은 모듈 수준 정보와 팩 수준 운전 한계(Pack-Level Operating Limit)를 통합하여 관리한다. 충전 상태, 건전 상태(State of Health), 허용 방전 출력(Allowable Discharge Power), 허용 회생 충전 출력(Allowable Regenerative Charging Power), 열적 한계(Thermal Limitation)를 추정할 수 있다. 이러한 값은 휴머노이드 상위 제어기(Supervisory Controller)에 전달되어 고부하 동작 중 보호 장치가 개입하도록 만드는 대신 운동 계획(Motion Planning)과 액추에이터 제어가 배터리의 순간적인 공급 능력 범위 내에서 이루어지도록 할 수 있다.

셀 밸런싱(Cell Balancing) 역시 중요한 모듈 수준 기능이다. 용량, 누설(Leakage), 온도, 노화(Aging)의 작은 차이가 시간이 지나면서 셀 사이에 서로 다른 상태를 만들기 때문이다. 밸런싱이 없으면 가장 약한 셀 그룹이 다른 셀보다 먼저 전압 한계에 도달하여 배터리 팩의 사용 가능한 용량을 감소시킬 수 있다. 수동형 또는 능동형 밸런싱(Passive or Active Balancing)을 통해 이러한 불균형을 줄일 수 있지만 복잡성, 발열, 효율, 밸런싱 속도(Balancing Speed), 제어 요구사항에는 상당한 차이가 있다.

휴머노이드에서는 배터리 공간이 컴퓨터, 전력 전자장치(Power Electronics), 냉각 장비, 구조 부재(Structural Member), 관절 메커니즘(Joint Mechanism)과 경쟁하기 때문에 기계적 패키징(Mechanical Packaging)이 특히 중요하다. 몸통(Torso)은 로봇 중심부 근처에 비교적 크고 보호된 공간을 제공하기 때문에 주요 배터리 모듈을 배치하기에 자연스러운 위치이다. 배터리 위치는 무게 중심(Center of Gravity), 관성(Inertia), 균형 제어(Balance Control), 접근성(Accessibility), 충돌 또는 낙상 보호, 고출력 도체의 배선 길이에도 영향을 미친다.

모듈형 배터리 아키텍처(Modular Battery Architecture)는 패키징 또는 질량 분포(Mass Distribution)가 필요한 경우 여러 물리적 위치에 에너지 저장 장치를 분산할 수 있다. 그러나 분산형 모듈(Distributed Module)은 추가적인 전력 연결, 통신 링크(Communication Link), 보호 장치, 동기화 요구사항(Synchronization Requirement), 서로 다른 열적 환경을 발생시킨다. 따라서 서로 연결된 모듈은 하나의 공통 전기 버스를 공유하는 독립 배터리가 아니라 상호 조정되는 에너지 시스템(Coordinated Energy System)으로 관리해야 한다.

모듈 인클로저(Module Enclosure)는 기계적 보호와 전기적 보호를 동시에 제공한다. 셀은 진동(Vibration), 충격(Shock), 반복적인 휴머노이드 운동, 취급 하중(Handling Load), 낙상이나 충돌에 따른 잠재적인 충격을 견딜 수 있도록 고정되어야 한다. 인클로저는 도전성 물체(Conductive Object)가 통전 부품(Energized Component)에 접근하는 것도 방지해야 하며 전력, 통신, 센싱, 냉각, 정비를 위한 제어된 인터페이스를 제공해야 한다. 구조적 하중(Structural Load)이 취약한 셀 어셈블리에 예측할 수 없는 형태로 전달되지 않도록 해야 한다.

열 관리(Thermal Management)는 배터리 열화를 가속하지 않으면서 얼마나 많은 전기적 성능을 지속적으로 사용할 수 있는지를 결정한다. 높은 방전 전류는 내부 발열을 발생시키며 충전 및 회생 에너지는 추가적인 열적 스트레스(Thermal Stress)를 발생시킬 수 있다. 큰 온도 차이는 불균일한 노화와 전기적 특성을 유발할 수 있으므로 모듈 온도는 충분히 균일하게 유지해야 한다. 냉각은 전도 경로(Conduction Path), 강제 공랭(Forced Air), 액체 냉각 시스템(Liquid Cooling System) 또는 로봇 전체 열 관리 아키텍처와의 통합을 이용할 수 있다.

보호 기능(Protection)은 모듈 수준과 전체 팩 수준에 모두 존재해야 한다. 모듈에는 퓨즈(Fuse), 전류 차단 메커니즘(Current Interruption Mechanism), 온도 모니터링, 전압 감시(Voltage Supervision), 커넥터 인터록(Connector Interlock)을 적용할 수 있으며, 전체 팩에는 메인 컨택터(Main Contactor), 서비스 차단기(Service Disconnect), 프리차지(Precharge), 전류 센싱(Current Sensing), 중앙 보호 기능(Central Protection)이 추가된다. 목적은 국부적인 전기 고장이 전체 에너지 저장 시스템이나 휴머노이드의 배전 하니스(Distribution Harness)로 확산되는 것을 방지하는 것이다.

고전류 모듈 연결(High-Current Module Connection)에는 신중한 커넥터 및 버스바 엔지니어링(Connector and Busbar Engineering)이 필요하다. 접촉 저항(Contact Resistance)은 특히 반복되는 피크 출력 이벤트에서 전압 손실과 발열에 직접적인 영향을 미친다. 인터페이스는 예상 전류, 최대 전압, 진동, 결합 사이클(Mating Cycle), 기계적 공차(Mechanical Tolerance), 오염(Contamination), 열팽창(Thermal Expansion)을 견딜 수 있어야 한다. 키잉(Keying)과 접촉 안전 기능(Touch-Safe Feature)은 생산 또는 현장 유지보수 중 잘못된 조립과 우발적인 접촉을 줄일 수 있다.

배터리 모듈은 액추에이터의 회생 운전(Regenerative Actuator Operation)과 직접적으로 상호작용한다. 휴머노이드 관절이 감속하면 모터 드라이브가 전기 에너지를 배터리 방향으로 반환할 수 있다. 배터리 관리 시스템은 충전 상태, 온도, 전압, 충전 한계(Charging Limit)를 기준으로 셀이 이러한 에너지를 안전하게 받아들일 수 있는지를 판단해야 한다. 회생 에너지 수용 능력(Regenerative Acceptance)이 제한되는 경우 로봇은 회생 토크(Regenerative Torque)를 감소시키거나 초과 버스 에너지를 제어하기 위한 다른 메커니즘을 사용해야 할 수 있다.

사용 가능한 출력(Power Availability)은 고정된 배터리 사양이 아니라 동적으로 변화하는 값으로 취급해야 한다. 정상 온도와 중간 수준의 충전 상태에서 높은 전류를 공급할 수 있는 모듈이라도 저온, 낮은 충전 상태, 과열 또는 노화된 조건에서는 훨씬 적은 출력을 제공할 수 있다. 상위 소프트웨어(Supervisory Software)는 배터리 한계를 실시간으로 이용하여 전기적 또는 열적 한계를 초과하기 전에 가속도, 보행 속도, 페이로드 처리(Payload Handling), 기타 로봇 동작을 조정할 수 있다.

진단(Diagnostics)은 단기 및 장기 시간 범위 모두에서 배터리 동작을 추적해야 한다. 셀 그룹 전압 편차(Cell-Group Voltage Spread), 온도 구배(Temperature Gradient), 내부 저항 지표(Internal Resistance Indicator), 전류 이력(Current History), 에너지 처리량(Energy Throughput), 충전 사이클(Charge Cycle), 보호 이벤트(Protection Event), 비정상적인 전압 강하를 통해 진행 중인 열화를 확인할 수 있다. 이력 데이터(Historical Data)는 건전 상태 추정(State-of-Health Estimation)과 예지 정비(Predictive Maintenance)를 지원하여 운전 시간 감소 또는 예상하지 못한 정지가 발생하기 전에 성능이 저하된 모듈을 식별할 수 있도록 한다.

정비성(Serviceability)은 모듈형 배터리 구조를 채택하는 가장 중요한 이유 중 하나이다. 전기적 호환성(Electrical Compatibility), 충전 상태 정합(State-of-Charge Matching), 기계적 인터페이스, 배터리 관리 시스템 설정을 적절하게 관리한다면 결함이 있거나 성능이 저하된 모듈만 교체하고 전체 배터리 어셈블리를 교체하지 않을 수 있다. 안전한 유지보수를 위해서는 명확하게 정의된 차단(Disconnect), 방전(Discharge), 확인(Verification), 제거(Removal), 설치(Installation), 재가동(Recommissioning) 절차가 필수적이다.

배터리 모듈은 제조 전략(Manufacturing Strategy)에도 영향을 미친다. 표준화된 기계적 외형(Standardized Mechanical Envelope), 전기 커넥터, 통신 인터페이스, 식별 데이터(Identification Data), 시험 절차(Test Procedure)는 자동화 조립(Automated Assembly)과 생산라인 최종 검사(End-of-Line Verification)를 지원할 수 있다. 각 모듈은 통합 전에 전압, 필요한 경우 절연(Insulation), 온도 센싱, 통신, 밸런싱 기능, 전기적 성능을 시험할 수 있으므로 숨겨진 결함이 완성된 휴머노이드 시스템에 포함될 가능성을 줄일 수 있다.

견고한 배터리 모듈 아키텍처(Battery-Module Architecture)는 궁극적으로 전기화학(Electrochemical), 전기(Electrical), 기계(Mechanical), 열(Thermal), 통신(Communication), 진단, 안전 엔지니어링(Safety Engineering)을 하나의 교체 가능한 에너지 서브시스템(Replaceable Energy Subsystem)으로 통합한다. 적절하게 설계된 모듈은 고성능 휴머노이드 액추에이터에 필요한 전압과 과도 출력(Transient Power)을 제공하면서 제어된 충전, 회생, 고장 격리(Fault Isolation), 열 관리, 상태 모니터링(Health Monitoring), 로봇의 전체 운용 수명주기(Operational Lifecycle)에 걸친 유지보수를 지원한다.

## 03.05. Hot Swap

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

핫스왑(Hot Swap)은 휴머노이드 로봇(Humanoid Robot)이 모든 전기 서브시스템(Electrical Subsystem)을 완전히 종료하는 기존 방식의 셧다운(Shutdown)을 수행하지 않고 에너지 저장 모듈(Energy-Storage Module)을 교체하거나 변경할 수 있도록 한다. 목적은 단순히 배터리를 빠르게 교체하는 것이 아니라 하나의 배터리 모듈이 분리되고 새로운 모듈이 장착되는 동안 선택된 컴퓨팅(Computing), 통신(Communication), 진단(Diagnostics), 안전(Safety) 기능을 제어된 상태로 계속 유지하는 것이다. 이러한 기능은 장시간 운용이 요구되는 로봇의 가용성(Availability)을 크게 향상시킬 수 있다.

실용적인 핫스왑 아키텍처(Hot-Swap Architecture)를 구현하려면 단순히 탈착 가능한 배터리 모듈(Removable Battery Module)을 사용하는 것만으로는 충분하지 않다. 전기 시스템은 일시적으로 함께 존재할 수 있는 두 전원(Source)을 관리하고, 제어되지 않은 전류 흐름 없이 두 전원 사이를 전환하며, 필수 부하(Essential Load)의 전원 중단을 방지해야 한다. 따라서 기계적 인터페이스(Mechanical Interface), 커넥터(Connector), 배터리 관리(Battery Management), 전력 분배(Power Distribution), 프리차지(Precharge), 전원 격리(Source Isolation), 전압 정합(Voltage Matching), 통신, 상위 제어 소프트웨어(Supervisory Software)가 하나의 통합된 서브시스템으로 동작해야 한다.

일반적인 방식 중 하나는 두 개 이상의 독립적으로 탈착 가능한 배터리 모듈을 관리형 직류 전력 버스(Managed DC Power Bus)에 연결하는 것이다. 정상 운전 중에는 여러 모듈이 부하를 분담하거나 하나의 모듈을 예비 전원(Reserve Source)으로 유지할 수 있다. 모듈을 제거하기 전에 제어기는 해당 모듈이 담당하던 전력 공급을 남아 있는 전원으로 이전한다. 이후 제거 대상 모듈을 전기적으로 격리할 수 있으며, 필수 로봇 시스템은 활성 상태의 모듈로부터 계속 전력을 공급받는다.

아키텍처는 단자 전압(Terminal Voltage)이 크게 다른 두 배터리 모듈이 직접 연결되는 것을 방지해야 한다. 배터리와 버스의 임피던스(Impedance)가 낮기 때문에 비교적 작은 전압 차이도 큰 균등화 전류(Equalization Current)를 발생시킬 수 있다. 연결 전에 시스템은 새로 장착되는 모듈을 식별하고 전압을 측정하며 호환성을 확인한 다음, 커넥터 자체에서 제어되지 않은 전원 병렬 연결(Source Paralleling)이 발생하도록 하지 않고 제어된 전기적 전환을 수행해야 한다.

프리차지(Precharge)는 이러한 전환을 제어하는 중요한 메커니즘을 제공한다. 새로 장착되는 배터리가 용량성 부하(Capacitive Load)를 포함하는 버스에 연결될 때 프리차지 경로를 이용하여 메인 전력 접점(Main Power Contact)이 닫히기 전에 관련 전압을 점진적으로 균등화할 수 있다. 격리 장치(Isolation Device) 양쪽의 전압을 측정하면 제어기는 전압 차이가 허용 가능한 범위까지 감소했는지를 확인할 수 있다. 이 조건이 만족된 후에만 해당 모듈이 전력 네트워크(Power Network)에 완전히 연결되도록 허용해야 한다.

핫스왑 커넥터(Hot-Swap Connector)는 전력, 통신, 감지 접점(Detection Contact)의 연결 순서를 의도적으로 설계해야 한다. 단계별 접점 길이(Staged Contact Length)를 적용하여 메인 전력 접점보다 먼저 보호 접지(Protective Earth), 섀시 기준(Chassis Reference), 장착 감지(Presence Detection), 통신 또는 인터록(Interlock) 신호가 연결되도록 할 수 있다. 모듈을 제거할 때는 반대 순서를 통해 고전류 접점이 분리되기 전에 사전 경고를 제공할 수 있다. 이를 통해 제어기는 부하를 제거하고 전자식 또는 전기기계식 격리 장치(Electromechanical Isolation Device)를 안전하게 개방할 시간을 확보할 수 있다.

커넥터 설계에서는 반복적인 결합 사이클(Mating Cycle), 고전류, 접촉 저항(Contact Resistance), 진동(Vibration), 오염(Contamination), 기계적 정렬 오차(Mechanical Misalignment), 작업자의 취급 조건도 고려해야 한다. 반복적인 아크(Arcing)는 접촉면을 손상시키고 저항을 증가시킬 수 있으므로 전력 접점을 큰 부하 전류를 직접 차단하는 주요 수단으로 사용해서는 안 된다. 메인 접점이 물리적으로 분리되기 전에 시스템이 모듈 전류를 정의된 안전 수준까지 감소시키고 모듈을 전기적으로 격리해야 한다.

배터리 관리 시스템(Battery Management System)은 모듈을 삽입하거나 제거할 수 있는지를 판단하는 데 핵심적인 역할을 수행한다. 연결 전에 모듈 전압, 충전 상태(State of Charge), 온도, 건전 상태(Health Status), 전류 공급 능력(Current Capability), 고장 이력(Fault History), 식별 정보(Identification Information)를 확인할 수 있다. 안전하지 않은 온도, 호환되지 않는 전압, 내부 고장 또는 허용할 수 없는 상태를 보고하는 모듈은 기계적으로 올바르게 장착되었더라도 전기적으로 격리된 상태를 유지해야 한다.

여러 종류의 배터리가 유사한 기계적 인터페이스를 공유하는 경우 모듈 식별(Module Identification)이 유용하다. 로봇은 모듈을 수용하기 전에 배터리 화학계(Chemistry), 공칭 전압(Nominal Voltage), 용량(Capacity), 펌웨어 호환성(Firmware Compatibility), 제조 데이터(Manufacturing Data), 지원 가능한 전류 한계(Current Limit)를 확인할 수 있다. 이를 통해 기계적으로는 호환되지만 전기적으로 부적절한 배터리가 메인 버스(Main Bus)에 연결되는 것을 방지하고 구성 정보를 상위 에너지 관리 시스템(Supervisory Energy-Management System)에 자동으로 전달할 수 있다.

로봇이 일시적으로 감소된 배터리 용량으로 동작하는 동안에는 부하 관리(Load Management)가 중요해진다. 두 개의 모듈 중 하나가 제거되면 남아 있는 하나의 모듈만으로는 두 모듈이 함께 제공하던 동일한 피크 액추에이터 출력(Peak Actuator Power)을 공급하지 못할 수 있다. 따라서 상위 제어기는 교체 과정에서 보행 가속(Walking Acceleration), 관절 토크(Joint Torque), 물체 인양 능력(Lifting Capacity) 또는 기타 고출력 기능을 제한하면서 컴퓨팅, 통신, 균형 감시(Balance Supervision), 필수 안전 기능을 계속 유지할 수 있다.

핫스왑 이벤트(Hot-Swap Event)는 비공식적인 유지보수 작업이 아니라 명확하게 정의된 운전 상태(Operating State)로 취급해야 한다. 로봇은 정상 운전에서 교체 준비(Swap Preparation) 상태로 전환하고, 비필수 부하(Nonessential Load)를 감소시키며, 남아 있는 전원의 안정적인 공급 상태를 확인하고, 선택된 모듈을 격리한 후 기계적 해제(Mechanical Release)를 허가할 수 있다. 이후 제거를 감지하고 교체 모듈을 검증하며 프리차지를 수행하고 새로운 전력 경로를 연결한 다음 최종적으로 정상 성능 한계를 복원할 수 있다.

기계적 고정(Mechanical Retention)은 전기적 상태와 연동되어야 한다. 배터리 모듈이 상당한 전류를 전달하는 동안 자유롭게 제거할 수 있어서는 안 되며, 교체 모듈이 안전하게 장착되기 전에 완전히 통전되어서도 안 된다. 전기기계식 래치(Electromechanical Latch) 또는 상태 감시형 잠금 장치(Monitored Locking Mechanism)를 사용하여 이러한 관계를 강제할 수 있다. 위치 및 장착 감지 센서(Position and Presence Sensor)는 고전류 연결이 허용되기 전에 모듈이 필요한 기계적 결합 상태에 도달했는지를 확인할 수 있다.

에너지 유지 기능(Energy Hold-Up)은 매우 짧은 전원 전환 과정에서 중요한 저전압 전자장치(Low-Voltage Electronics)를 보호할 수 있다. 로컬 커패시터(Local Capacitor), 전용 백업 전원(Dedicated Backup Supply), 보조 배터리(Auxiliary Battery)를 사용하여 주 버스에서 짧은 전기적 교란이 발생하더라도 안전 제어기(Safety Controller), 통신 게이트웨이(Communication Gateway), 실시간 제어기(Real-Time Controller), 진단 시스템에 전력을 유지할 수 있다. 필요한 유지 시간(Hold-Up Duration)은 전원 전환이 항상 순간적으로 이루어진다고 가정하지 않고 실제 스위칭 및 고장 대응 특성을 기준으로 결정해야 한다.

전력 분배 장치(Power Distribution Unit)는 전원 선택(Source Selection)과 하위 시스템 보호(Downstream Protection)를 조정한다. 스마트 스위치(Smart Switch), 컨택터(Contactor), 전류 센서(Current Sensor), 전압 센서(Voltage Sensor), 분기 보호 장치(Branch Protection Device)를 이용하면 각 배터리 모듈을 독립적으로 연결하거나 격리할 수 있다. 전력 분배 장치는 전원 측 고장(Source-Side Fault)과 부하 측 고장(Load-Side Fault)을 구분하여 결함이 있는 모듈을 제거할 때 정상 모듈이나 중요한 하위 전력 도메인까지 불필요하게 차단하지 않도록 해야 한다.

회생 에너지(Regenerative Energy)는 핫스왑 과정에서 추가적인 과제를 발생시킨다. 하나의 배터리 모듈을 제거하거나 삽입하는 동안에도 관절 모터 드라이브(Joint Motor Drive)는 감속 과정에서 직류 버스로 에너지를 반환할 수 있다. 남아 있는 배터리는 충분한 회생 에너지 수용 능력(Regenerative Acceptance)을 가져야 하며, 그렇지 않은 경우 로봇은 회생 운전(Regenerative Operation)을 일시적으로 제한해야 한다. 따라서 버스 전압 모니터링(Bus Voltage Monitoring), 운동 제어(Motion Control), 배터리 충전 한계(Battery Charge Limit), 선택적인 에너지 소산 메커니즘(Energy-Dissipation Mechanism)은 교체 과정 전체에서 상호 조정되어야 한다.

열적 조건(Thermal Condition) 역시 핫스왑 허용 여부를 결정할 수 있다. 최근까지 사용된 배터리는 높은 온도일 수 있으며 교체 모듈은 활성 배터리 팩보다 훨씬 낮거나 높은 온도일 수 있다. 열적·전기적 특성이 크게 다른 모듈을 연결하면 불균등한 전류 분담(Unequal Current Sharing)과 가속된 스트레스(Accelerated Stress)가 발생할 수 있다. 따라서 제어 시스템은 여러 모듈의 병렬 운전을 허용하기 전에 온도와 전류 공급 능력을 평가해야 한다.

고장 처리(Fault Handling)는 핫스왑이 정상적으로 완료되지 않을 가능성을 고려해야 한다. 새로 장착된 모듈의 식별에 실패하거나, 프리차지가 제한 시간 내에 완료되지 않거나, 전압 차이가 계속 유지되거나, 통신이 끊기거나, 컨택터가 닫히지 않을 수 있다. 이러한 경우 시스템은 문제가 있는 모듈을 격리 상태로 유지하고 가능한 경우 정상 전원을 이용해 운전을 지속하며 고장을 명확하게 보고해야 한다. 또한 안전하지 않은 연결 시퀀스(Connection Sequence)를 반복적으로 시도해서는 안 된다.

진단(Diagnostics)은 전체 핫스왑 시퀀스(Hot-Swap Sequence)를 기록해야 한다. 유용한 정보에는 모듈 식별 정보, 삽입 및 제거 시간, 버스 전압, 모듈 전압, 전류 전환(Current Transfer), 프리차지 시간, 컨택터 상태, 온도, 충전 상태, 통신 상태, 비정상 이벤트(Abnormal Event)가 포함된다. 이러한 기록은 고장 분석(Troubleshooting), 커넥터 수명 평가(Connector-Life Assessment), 배터리 건전성 분석(Battery Health Analysis), 예지 정비(Predictive Maintenance), 현장 교체 절차가 올바르게 수행되고 있는지 검증하는 데 활용할 수 있다.

기능 안전(Functional Safety)은 배터리 교체 과정에서 허용되는 로봇의 동작을 정의해야 한다. 에너지 용량이나 전력 이중화(Power Redundancy)가 감소한 상태에서는 완전한 동적 운동(Full Dynamic Motion)이 적절하지 않을 수 있다. 대신 로봇은 안정된 자세(Stable Posture)를 유지하거나 이동을 제한하고 액추에이터 토크를 감소시키거나 외부 지지(External Support)를 요구하면서 인지 및 통신 기능은 활성 상태로 유지할 수 있다. 따라서 핫스왑은 단순한 전기 기능이 아니라 로봇의 운전 상태 머신(Operational State Machine) 및 안전 아키텍처(Safety Architecture)와 통합되어야 한다.

전체 설계가 적절하게 조정되면 정비성(Serviceability) 측면에서 상당한 이점을 얻을 수 있다. 방전된 배터리를 빠르게 교체하면 로봇 전체가 재충전될 때까지 기다릴 필요가 없어 물류(Logistics), 제조(Manufacturing), 검사(Inspection), 서비스(Service) 분야에서 거의 연속적인 운전이 가능하다. 표준화된 모듈 인터페이스(Standardized Module Interface)는 로봇의 전체 수명주기 동안 플릿 유지보수(Fleet Maintenance), 배터리 순환 운용(Battery Rotation), 충전 인프라(Charging Infrastructure), 예비 부품 관리(Spare Management), 성능이 저하된 모듈의 교체를 단순화할 수 있다.

견고한 핫스왑 아키텍처(Hot-Swap Architecture)는 궁극적으로 모듈형 배터리(Modular Battery), 제어된 전원 스위칭(Controlled Source Switching), 프리차지, 단계형 커넥터(Staged Connector), 배터리 관리 시스템 감독(BMS Supervision), 전력 분배 장치 제어(PDU Control), 기계적 인터록(Mechanical Interlocking), 에너지 유지 기능, 진단, 로봇 수준 전력 관리(Robot-Level Power Management)를 통합한다. 이러한 기능을 올바르게 결합하면 배터리 교체는 필수 운전 기능을 유지하면서 돌입전류(Inrush Current), 아크, 전압 불일치(Voltage Mismatch), 안전하지 않은 전원 인가(Unsafe Energization), 제어되지 않은 액추에이터 전원 상실을 방지하는 제어된 시스템 전환(Controlled System Transition)이 된다.

## 03.06. PDU Architecture

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

전력 분배 장치(Power Distribution Unit)는 휴머노이드 로봇(Humanoid Robot)의 배터리 시스템과 분산 부하(Distributed Load) 사이에서 전력을 중앙 집중적으로 조정하는 핵심 장치이다. 전력 분배 장치(PDU)는 단순한 접속함(Junction Box)이 아니라 전력 라우팅(Power Routing), 회로 보호(Circuit Protection), 스위칭(Switching), 전류 측정(Current Measurement), 전압 모니터링(Voltage Monitoring), 진단(Diagnostics), 안전 제어(Safety Control)를 통합한다. 이를 통해 배터리 에너지를 액추에이터(Actuator), 컴퓨팅(Computing), 인지(Perception), 통신(Communication), 보조 시스템(Auxiliary System)에 공급되는 제어된 분기 전원(Controlled Branch Supply)으로 변환한다.

전력 분배 장치는 일반적으로 배터리 팩(Battery Pack)과 주 보호 장치(Primary Protection Device)의 하위에 배치된다. 배터리 에너지는 메인 퓨즈(Main Fuse), 서비스 차단기(Service Disconnect), 컨택터(Contactor), 프리차지 회로(Precharge Circuit), 전류 센싱(Current Sensing)을 거쳐 메인 배전 버스(Main Distribution Bus)에 도달할 수 있다. 아키텍처에 따라 이러한 기능의 일부를 전력 분배 장치 인클로저(PDU Enclosure)에 직접 통합하여 휴머노이드 몸통(Torso) 내부에 소형 중앙 전력 관리 어셈블리(Central Power-Management Assembly)를 구성할 수도 있다.

메인 버스(Main Bus)는 공칭 48V 또는 72V 시스템과 같이 선택된 전력 아키텍처의 전체 운전 범위를 수용할 수 있어야 한다. 버스바(Busbar), 도체(Conductor), 커넥터(Connector), 스위칭 장치(Switching Device), 보호 부품(Protection Component)은 연속 전류, 액추에이터의 동시 피크 전류, 회생 전류(Regenerative Current), 과도 전압(Voltage Transient), 고장 조건(Fault Condition)을 견뎌야 한다. 따라서 전기적 정격(Electrical Rating)은 로봇의 평균 소비전력이 아니라 최악 조건의 시스템 동작(Worst-Case System Behavior)을 기준으로 결정해야 한다.

중앙 버스에서 전력 분배 장치는 주요 전기적 구역(Electrical Zone)에 대응하는 보호된 분기 회로(Protected Branch)로 전력을 나눈다. 일반적인 공급 대상에는 몸통, 왼팔(Left Arm), 오른팔(Right Arm), 왼쪽 다리(Left Leg), 오른쪽 다리(Right Leg), 머리(Head), 컴퓨팅 시스템, 냉각 장비(Cooling Equipment), 보조 부하(Auxiliary Load)가 포함된다. 이러한 구역형 배전 구조(Zonal Distribution Structure)는 휴머노이드의 물리적 구성을 따르며 각 신체 영역을 보다 독립적으로 보호, 모니터링, 진단 및 격리할 수 있도록 한다.

액추에이터 분기 회로(Actuator Branch)는 일반적으로 가장 크고 동적으로 변화하는 전류를 전달한다. 고관절(Hip), 무릎(Knee), 발목(Ankle), 어깨(Shoulder), 팔꿈치(Elbow), 몸통 드라이브(Torso Drive)는 보행, 물체 들어 올리기, 균형 유지, 외란 복구(Disturbance Recovery) 과정에서 빠르게 변화하는 전력 수요를 발생시킬 수 있다. 전력 분배 장치는 충분한 버스 전압을 유지하면서 여러 관절에서 동시에 발생하는 연관 피크 부하(Correlated Peak Load)를 견뎌야 한다. 따라서 분기 회로 설계에서는 도체 용량, 커넥터 정격, 보호 임계값(Protection Threshold), 열적 거동(Thermal Behavior), 예상 과도상태 지속시간(Transient Duration)을 고려해야 한다.

보호 협조(Protection Coordination)는 전력 분배 장치의 가장 중요한 역할 중 하나이다. 하나의 액추에이터 또는 팔다리에서 고장이 발생한 경우 관련이 없는 전기 도메인(Electrical Domain)을 불필요하게 정지시키지 않고 해당 분기 회로만 차단하는 것이 바람직하다. 메인 보호(Main Protection)는 치명적인 전원 측 고장(Source-Side Fault)을 처리하고, 분기 보호(Branch Protection)는 국부적인 고장을 제한한다. 퓨즈(Fuse), 회로 차단기(Circuit Breaker), 전자식 스위치(Electronic Switch), 지능형 보호 장치(Intelligent Protection Device)는 전류 수준, 응답 시간(Response Time), 안전 요구사항에 따라 조합할 수 있다.

전자식 분기 스위칭(Electronic Branch Switching)은 기존의 수동형 퓨즈 배전(Passive Fuse Distribution)을 넘어서는 기능을 제공한다. 솔리드 스테이트 스위치(Solid-State Switch) 또는 제어형 컨택터(Controlled Contactor)는 각각의 부하를 독립적으로 활성화하거나 비활성화하고, 전류를 측정하며, 단락(Short Circuit)을 감지하고, 과전류 상태(Overcurrent Condition)를 식별하여 상위 소프트웨어(Supervisory Software)에 상태를 보고할 수 있다. 이를 통해 로봇은 기계적 분리에 전적으로 의존하지 않고 제어된 기동(Controlled Startup), 선택적 종료(Selective Shutdown), 부하 차단(Load Shedding), 고장 복구(Fault Recovery), 정비 격리(Maintenance Isolation)를 수행할 수 있다.

전력 분배 장치의 전류 센싱(Current Sensing)은 시스템 운전 상태와 부품 건전성(Component Health)에 대한 중요한 정보를 제공한다. 배터리 입력, 주요 액추에이터 분기, DC-DC 컨버터(DC-DC Converter) 공급 경로, 컴퓨팅 부하 또는 기타 중요 회로에서 전류를 측정할 수 있다. 다양한 운전 모드에서 전류 특성을 비교하면 로봇은 비정상적인 전력 소비, 구속된 액추에이터(Stalled Actuator), 배선 고장(Wiring Fault), 열화된 커넥터(Degraded Connector), 증가하는 서브시스템 손실(Subsystem Loss)을 완전한 고장으로 발전하기 전에 식별할 수 있다.

전압 모니터링(Voltage Monitoring)은 배전 네트워크(Distribution Network)의 각 단계를 통해 에너지가 정상적으로 전달되고 있는지를 확인함으로써 전류 센싱을 보완한다. 배터리 입력, 메인 버스, 컨택터, 프리차지 경로, 선택된 분기 회로의 전압을 측정하면 과도한 전압 강하(Voltage Drop), 개방 회로(Open Circuit), 용착된 컨택터(Welded Contactor), 접속 불량(Weak Connection), 비정상적인 버스 동작을 확인할 수 있다. 전압과 전류 데이터를 결합하면 실시간 전력 및 에너지 추정(Real-Time Power and Energy Estimation)도 지원할 수 있다.

모터 드라이브(Motor Drive)와 DC-DC 컨버터가 상당한 입력 커패시턴스(Input Capacitance)를 가지는 경우 프리차지 제어(Precharge Control)를 전력 분배 장치에 통합할 수 있다. 메인 컨택터가 닫히기 전에 제어된 저항 경로(Controlled Resistor Path)를 이용하여 하위 커패시터(Downstream Capacitor)를 충전하고 돌입전류(Inrush Current)를 제한한다. 전력 분배 장치는 컨택터 양단의 전압 차이를 모니터링하고 버스가 필요한 임계값에 도달한 경우에만 전체 연결을 허용함으로써 커넥터 스트레스, 컨택터 아크(Contactor Arcing), 전기적 교란(Electrical Disturbance)을 감소시킨다.

전력 분배 장치는 고출력 액추에이터 도메인(High-Power Actuator Domain)과 저전압 전자 시스템(Low-Voltage Electronic System)을 연결하는 중요한 브리지(Bridge)이기도 하다. 보호된 전력 공급 경로를 통해 48V, 24V, 12V, 5V 또는 기타 안정화 전원 레일(Regulated Power Rail)을 생성하는 DC-DC 컨버터에 전력을 공급할 수 있다. 이러한 분기 회로를 분리하면 액추에이터 회로에서 발생한 고장이나 스위칭 교란(Switching Disturbance)이 민감한 전자 부하로 직접 전파되는 것을 방지할 수 있다.

기능 안전(Functional Safety) 요구사항은 전력 분배 장치의 분기 회로가 어떻게 분할되고 제어되는지에 영향을 준다. 비상 정지(Emergency Stop) 상황에서는 토크를 발생시키는 액추에이터 분기 회로의 전원을 차단하면서 선택된 컴퓨팅, 통신, 진단, 안전 제어기(Safety Controller)의 전원은 계속 유지해야 할 수 있다. 따라서 전력 분배 장치는 안전 제어형 전력 도메인(Safety-Controlled Power Domain)과 비안전 전력 도메인(Non-Safety Power Domain)을 분리하여 위험한 기계적 에너지를 제거하면서 안전 상태(Safe State)를 관리하고 보고하는 데 필요한 전기 기능을 유지할 수 있다.

안전 제어기는 주 인공지능 컴퓨터(AI Computer) 또는 애플리케이션 컴퓨터(Application Computer)와 독립적으로 중요한 전력 분배 장치의 스위칭을 감독할 수 있다. 비상 정지 입력(Emergency-Stop Input), 컨택터 피드백(Contactor Feedback), 분기 상태(Branch Status), 전압 측정값, 인터록 신호(Interlock Signal)는 전용 안전 로직(Dedicated Safety Logic)을 통해 평가할 수 있다. 이러한 분리는 복잡한 상위 소프트웨어에 대한 의존성을 줄이고 메인 컴퓨팅 환경이 사용할 수 없거나 응답하지 않는 경우에도 중요한 전원 차단 기능(Power-Removal Function)을 수행할 수 있도록 한다.

서로 다른 서브시스템을 항상 동시에 활성화할 수 있는 것은 아니므로 기동 및 종료 시퀀싱(Startup and Shutdown Sequencing)은 전력 분배 장치를 통해 조정된다. 저전압 제어기와 안전 전자장치가 먼저 기동되고, 이후 통신 네트워크, 프리차지, 메인 액추에이터 버스(Main Actuator Bus), 마지막으로 모터 드라이브 활성화(Motor-Drive Enablement)가 순차적으로 이루어질 수 있다. 종료 과정에서는 이 순서를 반대로 적용하여 액추에이터 에너지를 먼저 제거하면서 진단 및 로깅 시스템(Logging System)은 시스템 상태를 기록할 수 있을 만큼 충분한 시간 동안 전원을 유지할 수 있다.

부하 차단(Load Shedding)은 사용 가능한 배터리 출력이 제한될 때 전력 분배 장치가 지능적으로 대응할 수 있도록 한다. 낮은 충전 상태(State of Charge), 과도한 온도, 배터리 열화(Battery Degradation), 핫스왑 운전(Hot-Swap Operation), 모듈 고장(Module Fault)은 사용 가능한 전력을 감소시킬 수 있다. 상위 제어기는 전력 분배 장치에 비필수 부하(Nonessential Load)를 차단하거나 제한하도록 명령하면서 균형 제어(Balance Control), 안전 시스템, 통신 및 휴머노이드를 제어된 운전 상태로 전환하는 데 필요한 기능을 유지할 수 있다.

전력 분배 장치는 여러 모터 드라이브를 하나의 공통 에너지원에 연결하므로 회생 에너지(Regenerative Energy)를 고려해야 한다. 감속 또는 하강 동작 중 액추에이터 드라이브는 메인 버스로 에너지를 반환할 수 있다. 전력 분배 장치의 전압 및 전류 센싱은 회생 상태(Regenerative Condition)를 식별하는 데 도움을 주며, 배터리 관리 시스템(Battery Management System)은 허용 가능한 충전 출력을 결정한다. 회생 에너지가 배터리 수용 능력을 초과하는 경우 과도한 버스 전압을 방지하기 위해 과전압 보호(Overvoltage Protection)와 에너지 관리 전략(Energy-Management Strategy)이 필요하다.

버스바, 스위치, 퓨즈, 컨택터, 커넥터, 전류 센싱 요소(Current-Sensing Element)는 높은 부하에서 열을 발생시키기 때문에 열 관리(Thermal Management)가 필요하다. 전력 분배 장치 인클로저는 배터리, 컴퓨터, 컨버터가 함께 배치된 밀집된 몸통 내부에 위치할 수 있어 까다로운 열적 환경(Thermal Environment)에 노출될 수 있다. 따라서 온도 센서(Temperature Sensor), 도체 크기 선정, 열 확산(Heat Spreading), 공기 흐름(Airflow), 냉각 인터페이스(Cooling Interface), 전류 디레이팅(Current Derating)을 전기 설계의 일부로 고려해야 한다.

전력 분배 장치는 수많은 스위칭 모터 드라이브와 컨버터에 에너지를 공급하므로 전자파 적합성(Electromagnetic Compatibility)도 중요하다. 고주파 전류 성분(High-Frequency Current Component)은 공유 도체와 접지 경로를 통해 전파될 수 있다. 저인덕턴스 버스 구조(Low-Inductance Bus Structure), 적절한 필터링, 제어된 접지(Controlled Grounding), 섀시 본딩(Chassis Bonding), 차폐(Shielding), 전력 및 통신 인터페이스 사이의 물리적 분리는 배전에서 발생하는 노이즈가 센서나 실시간 네트워크(Real-Time Network)의 성능을 저하시키는 것을 방지하는 데 도움이 된다.

통신(Communication)은 지능형 전력 분배 장치(Intelligent PDU)를 네트워크화된 로봇 서브시스템(Networked Robot Subsystem)으로 변화시킨다. CAN FD, 이더넷(Ethernet) 또는 기타 적절한 인터페이스를 통해 분기 전류, 전압, 온도, 스위치 상태, 고장 코드(Fault Code), 에너지 소비량, 진단 정보를 상위 제어기에 전달할 수 있다. 명령을 통해 분기 활성화, 제어된 격리, 리셋(Reset), 정비 모드(Service Mode)를 요청할 수 있으며, 중앙 컴퓨터와의 통신이 중단되더라도 로컬 전력 분배 장치 로직(Local PDU Logic)은 보호 기능을 계속 유지해야 한다.

진단 로깅(Diagnostic Logging)은 과전류 트립(Overcurrent Trip), 저전압(Undervoltage), 과전압(Overvoltage), 컨택터 고장, 과도한 온도, 프리차지 시간 초과(Precharge Timeout), 분기 격리(Branch Isolation), 예상하지 못한 전류 소비와 같은 중요한 전기적 이벤트를 보존해야 한다. 시간 정보가 기록된 이벤트 데이터(Time-Stamped Event Data)는 로봇의 운동 및 액추에이터 동작과 연계하여 분석할 수 있다. 이러한 정보는 고장 분석(Troubleshooting), 예지 정비(Predictive Maintenance), 보호 설정 보정(Protection Calibration), 재현하기 어려운 간헐적 전기 문제(Intermittent Electrical Problem)의 식별을 지원한다.

명확하게 정의되고 표시된 분기 인터페이스(Branch Interface)를 갖춘 전력 분배 장치 아키텍처는 정비성(Serviceability)을 향상시킨다. 모듈형 커넥터(Modular Connector)를 이용하면 관련이 없는 회로를 건드리지 않고 개별 팔다리, 컴퓨팅 모듈, 냉각 시스템 또는 보조 장치를 분리할 수 있다. 커넥터 키잉(Connector Keying), 인터록, 접촉 안전 인터페이스(Touch-Safe Interface), 진단 접근(Diagnostic Access), 명확한 무전압화 절차(De-Energization Procedure)는 유지보수 위험을 줄이고 생산 또는 현장 환경에서 주요 휴머노이드 모듈을 신속하게 교체할 수 있도록 한다.

견고한 휴머노이드 전력 분배 장치 아키텍처(Humanoid PDU Architecture)는 궁극적으로 수동형 배전함(Passive Distribution Box)이 아니라 지능형 에너지 라우팅 및 보호 플랫폼(Intelligent Energy-Routing and Protection Platform)으로 동작한다. 구역형 배전(Zonal Distribution), 스위칭, 센싱, 보호, 프리차지, 안전 제어, 진단, 통신, 열 관리, 정비 인터페이스(Service Interface)를 통합함으로써 전력 분배 장치는 로봇 전체에 걸친 전기 에너지를 체계적으로 조정하면서 높은 동적 성능(High Dynamic Performance), 고장 격리(Fault Containment), 모듈성(Modularity), 신뢰성 높은 운전(Reliable Operation)을 지원한다.
