# Jae-Hwan Jhong — Academic Homepage

`https://jaehwan-jhong.github.io/` 에 배포되는 개인 홈페이지입니다.

## 파일 구성

```
homepage/
├── index.html          # Home 페이지
├── cv.html             # CV 페이지
├── research.html       # Publications & Talks
├── members.html        # Lab members
├── styles.css          # 공통 스타일 (4개 페이지 전부 이것 사용)
├── images/
│   └── profile.jpg     # 프로필 사진 (직접 추가 필요)
└── README.md           # 이 문서
```

## 배포 가이드 (초기 세팅, 한 번만)

### 1단계: 기존 repository 비우기

`JaeHwan-Jhong/jaehwan-jhong.github.io` 에 가서 기존 Jekyll 파일들을 삭제합니다. 
웹에서 각 파일 옆 쓰레기통 아이콘을 클릭하거나, 더 간단하게는 repo Settings → Danger Zone → Delete repository 후 같은 이름으로 다시 생성해도 됩니다. (Starred나 issue 없으니 손해 없음)

### 2단계: 새 파일 업로드

repository 메인 페이지 → **Add file → Upload files** → 아래 5개 파일을 드래그앤드롭:

- `index.html`
- `cv.html`
- `research.html`
- `members.html`
- `styles.css`

맨 아래 "Commit changes" 버튼 클릭.

### 3단계: 프로필 사진 추가

1. repository 메인 페이지에서 **Add file → Create new file**
2. 파일명 입력란에 `images/profile.jpg` 라고 입력 (슬래시를 입력하면 images 폴더가 자동으로 만들어짐)
3. 실제로는 이 방식으로 이미지를 올릴 수는 없으니, 다음 방식으로:
   - **Add file → Upload files** 에서 프로필 사진을 `profile.jpg` 이름으로 바꿔 업로드
   - 업로드 후 repo에서 해당 파일을 클릭 → 연필 아이콘 → 경로를 `images/profile.jpg` 로 수정하거나, 별도로 `images/` 폴더를 만들어 이동

가장 쉬운 방법: 터미널에서 다음 명령 실행 (Git 사용 시)
```bash
mkdir images
cp /path/to/your/photo.jpg images/profile.jpg
git add images/profile.jpg
git commit -m "Add profile photo"
git push
```

프로필 사진 권장 사양:
- 세로형 비율 (4:5 정도)
- 최소 400×500px 이상
- 정사각형도 동작하지만 세로형이 더 보기 좋음

### 4단계: GitHub Pages 활성화

repository의 **Settings → Pages** 에서 Source가 "Deploy from a branch"로 되어있고 branch가 `main`, folder가 `/ (root)` 인지 확인. 이미 이전에 Pages를 썼던 repo라면 자동으로 활성화되어 있을 것.

1-2분 대기 후 `https://jaehwan-jhong.github.io/` 접속.

## 이후 수정 방법

### 논문 한 편 추가하는 법

1. GitHub에서 `research.html` 파일 열기
2. 우측 상단 연필 아이콘 클릭
3. 원하는 연도 섹션을 찾아서, 기존 `<li class="pub-item">` 블록 하나를 복사해 붙여넣기
4. 저자, 제목, 저널 정보만 수정
5. 아래 "Commit changes" 클릭 → 1분 뒤 반영

예시 템플릿:
```html
<li class="pub-item">
  <span class="pub-authors"><span class="self">Jhong, J.-H.</span>, Author 2, &amp; Author 3</span>
  <span class="pub-title">논문 제목.</span>
  <span class="pub-venue">Journal Name, 10(2), 100–120.</span>
</li>
```

자신이 저자일 때 `<span class="self">...</span>` 로 감싸면 와인 컬러 + 굵게 하이라이트됩니다.

### 학생 추가

`members.html` 의 **"Graduate Students"** 섹션에 있는 HTML 주석(`<!-- TEMPLATE FOR ADDING A STUDENT: -->`) 을 참고하여 `<div class="member-card">` 블록을 복사해 붙여넣고 정보 수정. `empty-state` div는 첫 학생이 생기면 지우기.

### 색상/폰트 변경

`styles.css` 파일 맨 위 `:root { ... }` 블록에서 색상과 폰트 변수를 바꾸면 사이트 전체에 반영됩니다.

예: 와인 컬러 대신 딥 네이비로 바꾸려면
```css
--accent: #1e3a5f;          /* 기존 #6d1a2b */
--accent-soft: #dde4ed;     /* 기존 #f3e4e6 */
```

## 디자인 컨셉

- **타이포그래피**: Fraunces (세리프 디스플레이) + IBM Plex Sans/Mono (본문/메타)
- **컬러**: 따뜻한 종이 배경 (`#faf6ee`) + 딥 와인 포인트 (`#6d1a2b`)
- **레이아웃**: 최대 720px 본문 너비, 1000px 헤더 너비
- **반응형**: 760px 미만에서 모바일 레이아웃으로 전환
- **폰트**: Google Fonts CDN에서 로드 (오프라인 작동 안함)

## 로컬에서 미리보기

파일을 수정한 뒤 바로 결과를 보고 싶다면:

```bash
cd homepage
python3 -m http.server 8000
```

후 브라우저에서 `http://localhost:8000` 접속.

Python 없이도 `index.html` 파일을 그냥 더블클릭하면 브라우저에서 열립니다 (단, 이 경우 상대경로 링크 일부가 정상 동작 안 할 수 있음).

## 문의

디자인 수정이나 추가 기능이 필요하면 Claude에게 요청하세요.
