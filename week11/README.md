# 🔶 1. Wi-Fi
- ■ 구성
```
IEEE 802.11 표준

구성 요소:

AP (Access Point): 유무선 공유기

STA (Station): 스마트폰, 노트북 등
```

- ■ Service Set
```
BSS (Basic Service Set)

Ad hoc 모드: AP 없이 기기 간 직접 통신

Infrastructure 모드: AP를 통해 통신

ESS (Extended Service Set): 여러 BSS가 연결된 형태
```

- ■ MAC 방식
```
PCF (Point Coordination Function): 중앙 집중형 (선택사항)

DCF (Distributed Coordination Function): 분산형, CSMA/CA 사용
```

- ■ CSMA/CA
```
Carrier Sense Multiple Access with Collision Avoidance

충돌을 피하기 위해 백오프(backoff) 적용

RTS/CTS 메커니즘으로 숨겨진 단말 문제 해결

기본 동작 순서:
RTS → CTS → DATA → ACK
```

- ■ CSMA-CD vs CSMA-CA
```
항목	CSMA-CD	CSMA-CA
적용	유선 이더넷	무선 LAN
특징	충돌 후 감지	충돌 전 회피
장점	빠름	저가 구현 가능
단점	무선에 부적합	지연 발생 가능
```

# 🔶 2. ZigBee
- ■ 프로토콜 스택
```
PHY (물리): DSSS 방식, 3밴드 27채널 사용

MAC: 충돌 방지 위한 CSMA-CA

NWK: 네트워크 형성

APS & APL: 응용 계층 연결
```

- ■ PHY 계층
```
DSSS (Direct Sequence Spread Spectrum) 사용

저전력 설계로 수면기기 등 지원
```

- ■ MAC 계층
```
- 기기 유형:
NC (코디네이터)
FFD (Full Function Device)
RFD (Reduced Function Device)

- 통신 방식
비콘 없음 (Non-Beacon):
Non-slotted CSMA-CA, 간단하지만 sleep 기능 어려움

비콘 있음 (Beacon):
Slotted CSMA-CA, 슈퍼프레임 기반, 에너지 절약 가능
```

- ■ 슈퍼프레임 구조
```
슬롯 16개까지 구성 가능

구성:
Beacon → CAP(경쟁 구간) → CFP(예약 구간) → 비활성 구간

GTS (Guaranteed Time Slot): CFP에서 예약 송수신
```

# 🔶 3. 주소 체계
- ■ 주소 유형
```
Extended (64비트): 고유 주소

Short (16비트): 코디네이터 할당
```

- ■ MAC 주소 구성
```
PAN ID (2byte) + 주소 (2/8byte)
```

- ■ 주소 표시 예시
```
유형	구성	총 길이
같은 네트워크	목적지(2) + 근원지(2)	4 byte
다른 네트워크	PAN ID(2) + 주소(2) × 2	8 byte
다른 네트워크 + IEEE 주소	PAN ID(2) + 주소(8) × 2	20 byte
```

# 🔶 4. 분산 주소 할당 기법 (Cskip(d))
## ■ 정의
- ZigBee 네트워크에서 라우터 노드가 자식 노드에게 주소를 분산적으로 할당

## ■ 장점
- 중앙 집중 방식에 비해 트래픽 감소
- 라우팅 효율 향상

## ■ 관련 매개변수
```
Cm: 하나의 부모 노드가 가질 수 있는 최대 자식 수
Rm: 라우터 자식의 최대 수
Lm: 최대 네트워크 깊이 (Depth)
```