# 유채민 포트폴리오 (proj_portfolio)

무선 네트워크의 자원 스케줄링을 연구하는 학부연구생 유채민의 개인 소개 사이트입니다.
2026학년도 초급프로젝트 과제 1로 Hugo 테마를 골라 직접 설정하고, GitHub Actions로 GitHub Pages에 배포합니다.

- 공개 사이트: https://dbchim0418-yu.github.io/proj_portfolio/
- 저장소: https://github.com/dbchim0418-YU/proj_portfolio
- 사용 테마: [Kiyomi Portfolio](https://github.com/mathscantor/hugo-theme-kiyomi-portfolio) (MIT 라이선스)
- 원본 테마의 영문 안내는 [site/themes/template/README.md](site/themes/template/README.md)에 그대로 남겨 두었습니다.

## 사용 도구와 버전

| 도구 | 버전 | 사용 위치 |
| --- | --- | --- |
| Hugo (extended) | 0.167.0 | 사이트 빌드 (`.github/workflows/hugo-pages.yml`에서 지정) |
| Dart Sass | 1.105.0 | 테마 스타일 처리 (워크플로가 자동 설치) |
| Python | 3.12 (Actions), 3.12.10 (작성자 PC) | 수업 제공 준비, 빌드 스크립트 실행 |
| Node.js | 24 | 워크플로의 의존성 준비 단계 (이 테마는 npm 패키지를 쓰지 않음) |
| Git | 2.x | 버전 관리, GitHub에 push |
| 준비 스크립트 | `prepare_github_pages.py` 3.1 | 수업 제공 스크립트. 테마 ZIP을 `site/`로 정리하고 배포 워크플로 생성 |

## 폴더 구조

```text
proj_portfolio/
├─ .github/
│  ├─ workflows/hugo-pages.yml   # main에 push하면 빌드 후 GitHub Pages에 배포
│  └─ pages_build.py             # 워크플로가 실행하는 빌드 스크립트 (준비 스크립트 사본)
├─ site/                         # 실제로 빌드되는 Hugo 사이트
│  ├─ hugo.toml                  # 사이트 설정 (이름, 소개 문구, GitHub 주소 등)
│  ├─ pages.json                 # 배포 주소(baseURL)와 테마 설정 (준비 스크립트가 생성)
│  ├─ content/_index.md          # 소개 섹션 본문
│  ├─ data/                      # 연구 활동, 기술, 학력 내용 (YAML)
│  ├─ layouts/                   # 테마 템플릿을 덮어쓴 파일 (한국어화, 기능 수정)
│  ├─ assets/                    # 사이트 전용 CSS, JS
│  ├─ static/                    # 아바타 이미지, Pretendard 글꼴
│  └─ themes/template/           # Kiyomi Portfolio 테마 원본 (수정하지 않음)
├─ prepare_github_pages.py       # 수업 제공 준비 스크립트
└─ (그 밖의 폴더)                 # 테마 ZIP을 풀었을 때 있던 원본 파일
```

## 설치와 로컬에서 확인하기

1. **Hugo extended 0.167.0 설치**
   - [Hugo 릴리스 페이지](https://github.com/gohugoio/hugo/releases/tag/v0.167.0)에서 `hugo_extended_0.167.0_windows-amd64.zip`을 받아 압축을 풀고, `hugo.exe`가 있는 폴더를 PATH에 추가합니다.
   - 설치 확인: `hugo version` 결과에 `v0.167.0`과 `extended`가 보여야 합니다.
2. **저장소 받기**
   ```bash
   git clone https://github.com/dbchim0418-YU/proj_portfolio.git
   cd proj_portfolio
   ```
3. **미리보기 서버 실행** (저장하면 자동으로 새로고침됩니다)
   ```bash
   hugo server -s site --config hugo.toml,pages.json
   ```
   브라우저에서 http://localhost:1313/proj_portfolio/ 을 엽니다. 종료는 `Ctrl + C`입니다.
4. **배포와 같은 방식으로 빌드하기** (선택)
   ```bash
   python .github/pages_build.py --build
   ```
   결과는 `public/` 폴더에 만들어지며, `.gitignore`에 들어 있어 커밋되지 않습니다.
