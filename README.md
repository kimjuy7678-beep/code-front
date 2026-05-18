# 🚀 Code-Front: Git에서 AWS로 배포하기

**Git 저장소에서 코드를 수집하고 AWS에 자동 배포하는 CI/CD 프로젝트**

---

## 📋 목차

- [프로젝트 개요](#프로젝트-개요)
- [주요 기능](#주요-기능)
- [아키텍처](#아키텍처)
- [기술 스택](#기술-스택)
- [설치 및 설정](#설치-및-설정)
- [사용 방법](#사용-방법)
- [배포 프로세스](#배포-프로세스)
- [기여하기](#기여하기)

---

## 🎯 프로젝트 개요

**Code-Front**는 Git 저장소에서 코드를 자동으로 수집하고 AWS 클라우드에 배포하는 통합 CI/CD 솔루션입니다.

개발자가 코드를 Push하면 자동으로 빌드, 테스트, 배포가 진행되도록 설계되었습니다.

### 주요 목표
- ✅ 자동화된 코드 배포 파이프라인 구축
- ✅ 빠른 개발 속도 유지
- ✅ 배포 오류 최소화
- ✅ 팀 협업 효율성 증대

---

## ⭐ 주요 기능

| 기능 | 설명 | 상태 |
|------|------|------|
| Git 자동 감지 | 저장소 변경사항 자동 감지 | ✅ 활성 |
| 코드 빌드 | 자동 빌드 및 컴파일 | ✅ 활성 |
| 테스트 실행 | 배포 전 자동 테스트 | ✅ 활성 |
| AWS 배포 | EC2, S3, Lambda 배포 지원 | ✅ 활성 |
| 배포 로그 | 실시간 배포 진행 상황 모니터링 | ✅ 활성 |
| 롤백 기능 | 이전 버전으로 복구 | 🔄 개발중 |
| 슬랙 알림 | 배포 상태 실시간 알림 | 🔄 개발중 |

---

## 🏗️ 아키텍처

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  GitHub/GitLab Repository                               │
│  (코드 저장소)                                           │
│                                                         │
└────────────────┬────────────────────────────────────────┘
                 │
                 │ Push Event
                 ▼
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  Webhook Trigger (GitHub Actions/GitLab CI)            │
│  (변경사항 감지)                                         │
│                                                         │
└────────────────┬────────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  Code-Front CI/CD Pipeline                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │  Build   │→ │  Test    │→ │  Deploy  │              │
│  └──────────┘  └──────────┘  └──────────┘              │
│                                                         │
└────────────────┬────────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  AWS Cloud Services                                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │   EC2    │  │    S3    │  │  Lambda  │              │
│  └──────────┘  └──────────┘  └──────────┘              │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 🛠️ 기술 스택

### Frontend
| 기술 | 버전 | 용도 |
|------|------|------|
| React | 18.x | UI 프레임워크 |
| TypeScript | 5.x | 타입 안정성 |
| Tailwind CSS | 3.x | 스타일링 |
| Vite | 5.x | 빌드 도구 |

### Backend & DevOps
| 기술 | 버전 | 용도 |
|------|------|------|
| Node.js | 18.x | 서버 런타임 |
| Python | 3.10+ | 스크립팅 |
| Docker | 최신 | 컨테이너화 |
| GitHub Actions | - | CI/CD 파이프라인 |
| AWS CodePipeline | - | 배포 파이프라인 |

### AWS Services
| 서비스 | 목적 |
|-------|------|
| EC2 | 애플리케이션 호스팅 |
| S3 | 정적 파일 저장소 |
| CloudFront | CDN 서비스 |
| RDS | 데이터베이스 |
| Lambda | 서버리스 함수 |
| CodePipeline | 배포 파이프라인 |

---

## 📦 설치 및 설정

### 사전 요구사항
```bash
- Git 설치 완료
- AWS 계정 및 IAM 권한 설정
- Node.js 18.x 이상
- Docker 설치 (선택사항)
```

### 저장소 클론
```bash
git clone https://github.com/kimjuy7678-beep/code-front.git
cd code-front
```

### 의존성 설치
```bash
npm install
# 또는
yarn install
```

### 환경 변수 설정
```bash
cp .env.example .env.local
```

`.env.local` 파일 수정:
```env
# AWS 설정
AWS_REGION=ap-northeast-2
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key

# GitHub 설정
GITHUB_TOKEN=your_github_token
GITHUB_REPO=your_repo_url

# 배포 설정
DEPLOYMENT_ENVIRONMENT=production
```

---

## 💻 사용 방법

### 로컬 개발
```bash
# 개발 서버 실행
npm run dev

# 브라우저에서 http://localhost:5173 접속
```

### 빌드
```bash
# 프로덕션 빌드
npm run build

# 빌드 결과물 미리보기
npm run preview
```

### 테스트
```bash
# 전체 테스트 실행
npm run test

# 커버리지 포함 테스트
npm run test:coverage
```

---

## 🚀 배포 프로세스

### 1️⃣ 코드 Push
```bash
git add .
git commit -m "feat: Add new feature"
git push origin main
```

### 2️⃣ 자동 배포 트리거
```
GitHub Push Event
    ↓
Webhook 수신 (GitHub Actions)
    ↓
CI/CD 파이프라인 시작
```

### 3️⃣ 배포 단계

| 단계 | 작업 | 소요 시간 |
|------|------|---------|
| 1. Build | 코드 컴파일 및 번들링 | ~2분 |
| 2. Test | 단위 테스트 및 통합 테스트 | ~3분 |
| 3. Security Scan | 보안 취약점 검사 | ~1분 |
| 4. Deploy to Staging | 스테이징 환경 배포 | ~2분 |
| 5. Deploy to Production | 프로덕션 배포 | ~2분 |
| **총 소요 시간** | | **~10분** |

### 4️⃣ 배포 완료 확인
```bash
# AWS 콘솔에서 확인
https://console.aws.amazon.com/

# 배포된 애플리케이션 접속
https://your-app.example.com
```

---

## 📊 배포 지원 환경

```
┌─────────────────────────────────┐
│                                 │
│  Staging Environment            │
│  - 테스트 환경                   │
│  - 실제 배포 전 검증            │
│  - 팀 테스트 및 QA              │
│                                 │
└─────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────┐
│                                 │
│  Production Environment         │
│  - 실제 배포 환경               │
│  - 고가용성 구성                │
│  - 모니터링 및 로깅             │
│                                 │
└─────────────────────────────────┘
```

---

## 🔧 설정 및 커스터마이징

### GitHub Actions 워크플로우
`.github/workflows/deploy.yml` 파일을 수정하여 배포 프로세스 커스터마이징

### AWS 배포 설정
`aws-config.json` 파일에서 AWS 리소스 설정 변경

```json
{
  "region": "ap-northeast-2",
  "ec2": {
    "instanceType": "t3.medium",
    "keyName": "your-key-pair"
  },
  "s3": {
    "bucketName": "your-bucket-name"
  }
}
```

---

## 📈 모니터링 및 로그

### CloudWatch 로그 확인
```bash
aws logs tail /aws/code-front/deployment --follow
```

### 배포 상태 확인
```bash
aws codepipeline get-pipeline-state --name code-front-pipeline
```

---

## 🤝 기여하기

### 기여 방법
1. Fork 저장소
2. Feature 브랜치 생성: `git checkout -b feature/amazing-feature`
3. 변경사항 Commit: `git commit -m 'Add amazing feature'`
4. 브랜치에 Push: `git push origin feature/amazing-feature`
5. Pull Request 생성

### 코드 컨벤션
- 커밋 메시지: Conventional Commits 따르기
- 코드 스타일: ESLint 및 Prettier 설정 준수
- 테스트: 새 기능마다 테스트 코드 작성

---

## 📝 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 [LICENSE](./LICENSE) 파일을 참조하세요.

---

## 📞 지원 및 문의

- 📧 이메일: [support@example.com](mailto:support@example.com)
- 💬 이슈: [GitHub Issues](https://github.com/kimjuy7678-beep/code-front/issues)
- 📖 문서: [Wiki](https://github.com/kimjuy7678-beep/code-front/wiki)

---

## 🎉 감사의 말

이 프로젝트를 사용해주시고 기여해주시는 모든 분들께 감사드립니다!

**Last Updated**: 2026-05-18
