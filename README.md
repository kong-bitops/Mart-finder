# Mart Finder

주변 5km 이내 마트 가격을 비교해 최저가 마트를 추천하는 Windows 데스크톱 유틸리티입니다.

## 1) 실행 환경
- OS: Windows 10 / Windows 11
- Python: 3.11 이상 권장
- 주요 라이브러리:
  - FastAPI
  - Uvicorn
  - SQLAlchemy
  - Requests
  - PySide6

## 2) 설치 절차 (소스코드 실행 기준)
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## 3) 실행 방법 (단계별)
### A. Python 소스코드로 실행
1. 더미 데이터 생성
```powershell
python -m backend.seed_data
```

2. 백엔드 서버 실행
```powershell
python -m uvicorn backend.main:app --host 127.0.0.1 --port 8000
```

3. 다른 터미널에서 데스크톱 앱 실행
```powershell
python -m desktop.app
```

### B. exe 파일로 실행 (권장)
`dist/VibeMartFinder.exe` 더블클릭으로 바로 실행 가능합니다.

## 4) 관리자 권한 필요 여부
- 관리자 권한 없이 실행 가능합니다.
- 기본적으로 사용자 쓰기 가능 경로(로컬 앱데이터 또는 프로젝트 `data` 폴더)를 사용합니다.

## 5) 주요 기능
- 현재 위치 기준 반경 5km 마트 검색
- 상품 가격 비교 및 최저가 마트 추천
- 대분류/소분류 기반 상품 검색
- 마트별 할인 상품 조회
- 장바구니 담기 및 총액 계산
- 지도 표시(무료 지도 API 또는 대체 지도 이미지)

## 6) 프로젝트 구조
```text
backend/          # FastAPI 서버, 데이터 모델, 추천 로직
desktop/          # PySide6 UI, API 클라이언트
data/             # SQLite DB 및 로그
dist/             # 빌드된 exe
requirements.txt  # 의존성 목록
run_vibe.py       # 단일 실행 진입점
```

## 7) 선택 설정 (상세 지도)
Mapbox 토큰이 있으면 더 자세한 지도를 사용할 수 있습니다.

```powershell
$env:MAPBOX_ACCESS_TOKEN="YOUR_MAPBOX_TOKEN"
python -m desktop.app
```

토큰이 없어도 기본 지도/대체 지도로 동작합니다.
