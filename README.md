# SRTgo Plus: K-Train (KTX, SRT) Reservation Assistant

> [!NOTE]
> 원본 [srtgo](https://github.com/lapis42/srtgo) 프로젝트가 2025년 9월 개발 중단됨에 따라, 본 저장소에서 이어서 유지보수 및 개발을 진행하고 있습니다.
> 코레일(KTX)의 anti-bot 정책 변경에 대응하여 정상 동작하도록 수정하였습니다.

> [!WARNING]
> 본 프로그램의 모든 상업적, 영리적 이용을 엄격히 금지합니다. 개인적인 승차권 예매 용도로만 사용해 주세요. 본 프로그램 사용에 따른 민형사상 책임을 포함한 모든 책임은 사용자에게 있으며, 개발자는 어떠한 책임도 부담하지 않습니다. 본 프로그램을 내려받음으로써 위 사항에 동의하는 것으로 간주됩니다.

---

## 설치

```bash
pip install git+https://github.com/junddao/srtgo_plus.git
```

## 사용법

터미널에서 아래 명령어를 실행하면 됩니다.

```bash
srtgo
```

### 메뉴 구성

```
[?] 메뉴 선택:
  예매 시작
  예매 확인/결제/취소
  로그인 설정
  텔레그램 설정
  카드 설정
  역 설정
  역 직접 수정
  예매 옵션 설정
  나가기
```

### 1. 로그인 설정

처음 사용 시 **로그인 설정**에서 SRT 또는 KTX 계정을 등록합니다.

- 2026년 9월 이후 SRT 노선 예매는 코레일+ 통합회원 계정으로 진행됩니다. 프로그램의 **SRT 노선** 선택은 코레일 API를 사용합니다.

- 멤버십 번호, 이메일, 전화번호 중 하나로 로그인 가능
- 로그인 정보는 시스템 키체인에 안전하게 저장됩니다

### 2. 예매 시작

1. **SRT** 또는 **KTX** 선택
2. 출발역, 도착역, 날짜, 시간, 승객수 선택
3. 검색된 열차 목록에서 원하는 열차 선택 (복수 선택 가능)
4. 좌석 유형 선택 (일반실 우선 / 일반실만 / 특실 우선 / 특실만)
5. 매진 시 자동으로 빈 자리가 날 때까지 재시도

### 3. 텔레그램 알림 (선택)

텔레그램 봇을 연동하면 예매 성공 시 알림을 받을 수 있습니다.

1. [@BotFather](https://t.me/BotFather)에서 봇 생성 후 토큰 발급
2. **텔레그램 설정** 메뉴에서 토큰과 chat_id 입력

### 4. 카드 결제 (선택)

카드 정보를 미리 등록하면 예매와 동시에 자동 결제가 가능합니다.

## 요구사항

- Python 3.10 이상
- 의존 패키지: `click`, `curl_cffi`, `requests`, `inquirer`, `keyring`, `PyCryptodome`, `prompt_toolkit`, `python-telegram-bot`, `termcolor`

## 변경사항 (원본 대비)

- KTX(코레일) anti-bot 대응: `x-dynapath-m-token` 생성 엔진 구현
- KTX MACRO ERROR 에러 핸들링 개선
- 예매 간격 파라미터 안전성 조정

## Credits

- 원본 프로젝트: [srtgo](https://github.com/lapis42/srtgo) by lapis42
- SRT 모듈: [SRT](https://github.com/ryanking13/SRT) by ryanking13 (MIT License)
- KTX 모듈: [korail2](https://github.com/carpedm20/korail2) by carpedm20 (BSD License)
- Anti-bot bypass 참고: [korail2 PR #54](https://github.com/carpedm20/korail2/pull/54) by dhfhfk
