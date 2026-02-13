# SimOps Documentation Site

MkDocs + Material theme 기반의 SimOps 문서 사이트입니다.

## 배포 방법 (GitHub Pages)

### 1. GitHub 리포 생성

GitHub에서 `simops` (또는 원하는 이름) 리포를 생성합니다.

### 2. 초기 설정

```bash
# 압축 해제 후
cd simops-site

# site_url 수정 (본인 GitHub 유저네임으로)
# mkdocs.yml → site_url: https://YOUR_USERNAME.github.io/simops/

# Git 초기화 및 push
git init
git add .
git commit -m "Initial SimOps site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/simops.git
git push -u origin main
```

### 3. GitHub Pages 활성화

1. GitHub 리포 → **Settings** → **Pages**
2. Source를 **Deploy from a branch**로 설정
3. Branch를 **gh-pages** / **/ (root)** 로 선택
4. Save

push하면 GitHub Actions가 자동으로 빌드/배포합니다.
`https://YOUR_USERNAME.github.io/simops/` 에서 확인할 수 있습니다.

### 4. 콘텐츠 수정

```bash
# Markdown 파일 수정 후
git add .
git commit -m "Update content"
git push
# → 자동 배포됨
```

## 로컬 미리보기

```bash
pip install mkdocs mkdocs-material
mkdocs serve
# http://127.0.0.1:8000 에서 확인
```

## 프로젝트 구조

```
simops-site/
├── mkdocs.yml              # 사이트 설정
├── docs/
│   ├── index.md            # 랜딩 페이지 (한영 병행)
│   ├── en/                 # English
│   │   ├── overview.md     # SimOps Concept Overview
│   │   ├── architecture.md # Technical Architecture
│   │   └── wfm-era.md     # SimOps in the WFM Era
│   ├── ko/                 # 한국어
│   │   ├── overview.md     # SimOps 컨셉 개요
│   │   ├── architecture.md # 기술 아키텍처
│   │   └── wfm-era.md     # WFM 시대의 SimOps
│   └── assets/             # 이미지, 로고 등
└── README.md
```

## 커스터마이징

- **테마 색상**: `mkdocs.yml` → `theme.palette.primary` / `accent`
- **로고 추가**: `docs/assets/logo.png` 추가 후 `mkdocs.yml`에 설정
- **섹션 추가**: `docs/en/` 및 `docs/ko/`에 `.md` 파일 추가 후 `nav` 업데이트
- **도메인 설정**: `mkdocs.yml` → `site_url` 변경

## 커스텀 도메인 (선택)

커스텀 도메인을 사용하려면:

1. `docs/CNAME` 파일 생성 → 도메인 입력 (예: `simops.dev`)
2. DNS에 CNAME 레코드 추가 → `YOUR_USERNAME.github.io`
3. GitHub 리포 Settings → Pages → Custom domain 설정
