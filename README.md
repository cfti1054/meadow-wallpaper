# 초원 라이브 배경화면 3D

현재 시각에 맞춰 해와 달이 움직이고, 서울 실시간 날씨와 날짜별 계절에 따라 장면이 바뀌며,
마우스가 지나가면 3D 잔디가 헤쳐지는 배경화면입니다. 빌드 과정 없는 정적 사이트(HTML 1개 + three.js)입니다.

## 폴더 구성

```
index.html            배경화면 본체 (모든 코드)
vendor/three.min.js   3D 엔진 three.js r149 (MIT, 외부 CDN 없이 동작)
vendor/three.LICENSE  three.js 라이선스
```

## 1. GitHub에 올리기

```bash
git remote add origin https://github.com/<내 계정>/meadow-wallpaper.git
git push -u origin main
```

## 2. Railway에 배포

1. railway.com → New Project → **Deploy from GitHub repo** → 이 저장소 선택
2. 설정 없이 자동 배포됩니다. 루트에 `index.html`이 있으면 Railway(Railpack)가 정적 사이트로 인식해 Caddy로 띄워 줍니다.
3. 서비스의 **Settings → Networking → Generate Domain** 으로 주소를 만듭니다. 예: `https://meadow-wallpaper.up.railway.app`
4. 이후 `git push` 할 때마다 자동으로 다시 배포됩니다.

## 3. 배경화면으로 지정

배경화면 앱에는 주소 끝에 `#wallpaper` 를 붙여 넣습니다(미리보기 패널 숨김).

```
https://meadow-wallpaper.up.railway.app/#wallpaper
```

| OS | 앱 (무료) | 방법 |
|---|---|---|
| Windows | Lively Wallpaper | `+` (배경화면 추가) → 주소 입력 → 적용 |
| Mac | Plash | 메뉴바 아이콘 → Add Website → 주소 입력 |

## 옵션 (주소 뒤에 붙이기)

| 옵션 | 뜻 |
|---|---|
| `?q=low` / `?q=med` / `?q=high` | 잔디 양 (노트북 내장 그래픽은 `low` 권장) |
| `?fps=30` | 초당 프레임 제한 (전력 절약) |

예: `https://meadow-wallpaper.up.railway.app/?q=low&fps=30#wallpaper`

## 위치 바꾸기

`index.html` 상단의 `const LAT = 37.57, LON = 126.98;` 를 원하는 도시의 위도·경도로 바꾸면
일출·일몰과 날씨가 그 위치 기준으로 바뀝니다.

## 알아둘 점

- 호스팅 주소로 쓰면 PC가 인터넷에 연결돼 있어야 배경화면이 뜹니다. 인터넷 없이 쓰려면 이 폴더를 그대로 PC에 두고 `index.html` 파일을 배경화면 앱에 지정하세요.
- 날씨는 Open-Meteo(개인·비상업 무료, 키 불필요)에서 15분마다 받아옵니다.
- Mac의 Plash에서는 바탕화면 창이 마우스 움직임을 받지 못해 잔디 반응이 제한됩니다.
