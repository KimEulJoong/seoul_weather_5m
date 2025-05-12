
# 🌦️ 서울 기상 데이터 자동 수집 (5분 간격)

> **서울의 실시간 기온 데이터를 5분마다 자동 수집하여 CSV 파일로 저장**하는 GitHub Actions 기반 자동화 시스템입니다.

---

## 📌 프로젝트 개요

이 프로젝트는 OpenWeatherMap API를 이용해 **서울의 기온 데이터를 5분마다 자동 수집**하고,  
`seoul_weather.csv` 파일에 저장한 후 GitHub 저장소에 자동 커밋합니다.

- ⏱️ **5분 간격으로 실행**  
- ☁️ **OpenWeather API 사용**  
- 💾 **CSV 형식으로 누적 저장**  
- 🔁 **GitHub Actions 자동화**

---

## 📂 파일 구성

| 파일명 | 설명 |
|:---|:---|
| `.github/workflows/seoul_weather_5m.yml` | GitHub Actions 자동 실행 스크립트 |
| `seoul_weather_5m.py` | 서울 날씨 데이터를 요청하고 CSV로 저장하는 파이썬 코드 |
| `seoul_weather.csv` | 수집된 기온 데이터가 누적 저장되는 파일 |

---

## ⚙️ 사전 준비

### 1. OpenWeatherMap API 키 발급  
[https://openweathermap.org/api](https://openweathermap.org/api) 에서 회원가입 후 API 키를 발급받습니다.

### 2. GitHub 저장소 Secrets 등록  
GitHub 프로젝트 설정 > **Settings > Secrets and variables > Actions** 메뉴에서 아래 키를 추가합니다:

- `OPENWEATHER_API_KEY` : OpenWeatherMap에서 발급받은 API 키

---

## 🚀 자동화 동작 방식

GitHub Actions에서 5분마다 다음 순서를 반복합니다:

1. 저장소에서 코드를 체크아웃
2. Python 3.9 환경 설정
3. `requests` 패키지 설치
4. `seoul_weather_5m.py` 실행
   - 서울의 현재 기온 데이터를 API로 요청
   - `seoul_weather.csv` 파일에 날짜와 함께 저장
5. 변경된 CSV 파일을 커밋하고 저장소에 푸시

---

## 🧪 수집 예시 (CSV 내용)

```
datetime,temperature
2025-04-28 10:00,16.3
2025-04-28 10:05,16.5
...
```

---

## 📅 자동 실행 설정 (Cron)

```yaml
schedule: 
  - cron: "*/5 * * * *"  # 매 5분마다 실행
```

> ⚠️ GitHub Actions는 UTC 기준으로 동작합니다.

---

## 📜 라이선스

MIT License

---

## 🙋‍♀️ 기여 방법

- 오류 수정 및 기능 개선 PR 환영합니다!
- Issue 등록도 언제든지 가능합니다 😊

---

## 🔗 참고 링크

- [OpenWeatherMap API 문서](https://openweathermap.org/current)
- [GitHub Actions 공식 문서](https://docs.github.com/en/actions)

---
