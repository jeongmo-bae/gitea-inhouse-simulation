# Gitea In-house Simulation

본 프로젝트는 **사내 Gitea 기반 버전관리 도구 도입을 위한 사전 시뮬레이션**입니다.  
집에서 보유한 두 장비를 다음과 같이 가정하여 Gitea 서버-클라이언트 환경을 구축하고, Git 연동 테스트 및 실습 과정을 기록합니다.

---

## 환경 구성

| 역할 | test 장비 | test 장비 OS | 사내 장비 | 사내 장비 OS |
|-----|----------|-------------|---------|------------|
| Gitea 서버 | 데스크탑 | Ubuntu | 마케팅허브AP 개발서버| RHEL 7 |
| Git 클라이언트 | 노트북 | Windows 10 | 사내 개발자 로컬 PC | Window 10 |
---

## 구축 흐름 요약

1. **네트워크 통신 확인**
   - 노트북 ↔ 데스크탑 간 ping 확인
   - 동일 공유기 환경 또는 동일 네트워크 구성 필요
   - Gitea 기본 포트(3000) 방화벽 개방 필요

2. **Gitea 설치 (데스크탑/RHEL 7)**
   - Gitea 바이너리 다운로드 및 실행
   - SQLite 사용 (간단 실습 목적)
   - systemd 등록으로 자동 시작 설정
   - `firewalld`를 통한 포트 개방 필요

3. **Gitea 초기 설정**
   - 브라우저에서 `http://<데스크탑 IP>:3000` 접속
   - 관리자 계정 생성 및 기본 설정

4. **Git 클라이언트 설정 (노트북/Windows 10)**
   - Git 설치 및 환경변수 설정
   - Gitea에서 원격 리포지토리 생성
   - 로컬에서 `git remote add`, `git push`로 연동 확인

5. **웹 UI로 확인**
   - 브라우저로 커밋 및 Push 이력 확인

6. **이 과정을 GitHub에 문서화**
   - GitHub에 레포 생성
   - 스크립트 및 실습 문서 기록

---

## 📁 프로젝트 구조 예시

```bash
gitea-inhouse-simulation/
├── README.md                # 전체 개요 및 장비 역할
├── docs/   
│   ├── 01_desktop_setup.md        # Gitea 설치 및 설정 (RHEL 7)
│   ├── 02_laptop_setup.md         # Git 클라이언트 설정 (Windows 10)
│   └── 03_test_push.md            # Push 테스트 및 결과 확인
└── scripts/
    └── install_gitea_rhel.sh      # RHEL용 Gitea 설치 스크립트