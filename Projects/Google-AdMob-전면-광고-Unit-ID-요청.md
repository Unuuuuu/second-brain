작성일: 2026년 1월 7일

---

## 배경

- 해외 사용자(디바이스 지역 설정이 한국이 아닌 사용자)에게 Adrop 전면 광고 대신 Google AdMob 전면 광고를 노출하고자 함
- 현재 6개 위치에서 전면 광고가 노출되며, 해외 사용자 대응을 위한 Google AdMob Unit ID가 필요함

---

## 전면 광고 노출 위치

| #   | 위치            | 트리거 시점                      | 현재 Adrop Unit ID Key | 비고        |
| --- | ------------- | --------------------------- | -------------------- | --------- |
| 1   | 군인 정보 수정 완료   | 군인 정보 수정 후 저장 시             | soldierEditEnd       |           |
| 2   | 프로필 이미지 수정 완료 | 프로필 이미지 수정 후 저장 시           | profileEditEnd       |           |
| 3   | 진급 축하 팝업      | 진급 축하 팝업 닫을 때               | promotionCongratsEnd |           |
| 4   | D-Day 축하 팝업   | D-Day 축하 팝업 닫을 때            | dDayCongratsEnd      |           |
| 5   | 전역 축하 팝업      | 전역 축하 팝업 닫을 때               | dischargeCongratsEnd |           |
| 6   | 안드로이드 앱 종료    | 뒤로가기로 앱 종료 시 (Android Only) | androidBack          | AdMob 미적용 |

---

## 제안: 위치별 별도 Unit ID 생성

각 노출 위치마다 별도의 Unit ID를 생성하는 방식을 제안합니다.

### 제안 이유

- **위치별 성과 분석 가능**: CTR, CPM, 노출수 등을 위치별로 확인 가능
- **문제 발생 시 원인 파악 용이**: 특정 위치의 광고 성과 저하 시 빠른 원인 분석 가능
- **현재 Adrop 구조와 일관성 유지**: 기존 구조를 그대로 활용하여 코드 복잡도 최소화

---

## 결정 사항

- **androidBack(안드로이드 앱 종료) 제외**: 해외 사용자의 Android 앱 종료 시에는 광고를 노출하지 않음
- 나머지 5개 위치에서만 Google AdMob 전면 광고 적용

---

## 요청 Unit ID 목록

총 10개 (iOS 5개 + Android 5개)

| 위치                 | iOS Unit ID | Android Unit ID |
| -------------------- | :---------: | :-------------: |
| soldierEditEnd       |      O      |        O        |
| profileEditEnd       |      O      |        O        |
| promotionCongratsEnd |      O      |        O        |
| dDayCongratsEnd      |      O      |        O        |
| dischargeCongratsEnd |      O      |        O        |

---

## 요청 사항

위 10개 Unit ID 생성을 요청드립니다.
