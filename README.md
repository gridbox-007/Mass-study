# 매스 스터디 사이트 · 설치 안내 (1단계: 조원 테스트)

아이패드 사파리만으로 할 수 있어요. 전부 무료이고 카드 등록은 필요 없어요. 처음 한 번만 20~30분 걸려요.

준비할 파일 4개: `index.html`, `supabase-setup.sql`, `keepalive.yml`, `README.md`(이 파일)

---

## 1. Supabase 가입 · 데이터베이스 만들기

1. supabase.com 접속 → **Start your project** → **Continue with GitHub**를 누르세요. GitHub 계정이 없으면 github.com에서 먼저 가입하면 2단계에서도 그대로 써요.
2. **New project**를 누르고 아래처럼 입력하세요.
   - Name: `mass-study`
   - Database Password: **Generate a password**를 누른 뒤 메모장에 보관 (사이트에서는 안 써요)
   - Region: **Northeast Asia (Seoul)**
   - Plan: **Free**
3. 만들어질 때까지 1~2분 기다려요.

## 2. 데이터베이스 설정 붙여넣기

1. 왼쪽 메뉴 **SQL Editor** → **New query**를 누르세요.
2. `supabase-setup.sql` 파일 내용을 **전부** 복사해 붙여넣고 **Run**을 누르세요.
3. `Success. No rows returned`가 나오면 끝이에요. 여러 번 실행해도 괜찮아요.

## 3. 연결 정보 두 개 복사하기

1. 왼쪽 아래 ⚙️ **Project Settings** → **API Keys**(또는 **Data API**)로 가세요.
2. 아래 두 값을 메모하세요.
   - **Project URL**: `https://abcdefgh.supabase.co` 형태
   - **Publishable key** (`sb_publishable_…`로 시작), 없으면 **anon public** 키
   - ⚠️ `secret` 또는 `service_role` 키는 **절대 쓰지 마세요.**
3. `index.html` 위쪽의 이 부분에 붙여넣으세요.
   ```js
   window.MS_CONFIG = {
     SUPABASE_URL: "https://abcdefgh.supabase.co",
     SUPABASE_ANON_KEY: "sb_publishable_xxxxxxxx"
   };
   ```
   (4단계에서 GitHub에 올린 다음 GitHub 화면에서 연필 ✏️ 버튼으로 고쳐도 돼요.)

> 이 키는 공개돼도 괜찮은 키예요. 데이터를 지키는 건 2단계에서 넣은 보안 규칙이 해요.

## 4. GitHub에 올려서 사이트 주소 만들기

1. github.com → 오른쪽 위 **＋** → **New repository**를 누르세요.
   - Repository name: `mass-study` (이게 주소에 들어가요)
   - **Public** 선택 (무료 사이트 기능은 공개 저장소에서만 돼요. 코드가 공개될 뿐이고 조원들 데이터는 공개되지 않아요)
   - **Create repository**를 누르세요.
2. **uploading an existing file** 링크를 누르고 `index.html`, `README.md`를 올린 뒤 **Commit changes**를 누르세요.
3. 저장소 **Settings** → 왼쪽 **Pages**로 가세요.
   - Source: **Deploy from a branch**
   - Branch: **main** / **(root)** → **Save**
4. 1~2분 뒤 새로고침하면 위쪽에 주소가 떠요.
   **`https://내아이디.github.io/mass-study/`** ← 이 주소를 조원들에게 보내면 돼요.

## 5. 잠들지 않게 하기 (7일 미사용 일시정지 방지)

1. 저장소 첫 화면에서 **Add file** → **Create new file**을 누르세요.
2. 파일 이름 칸에 정확히 `.github/workflows/keepalive.yml`을 입력하세요. `/`를 치면 폴더가 자동으로 만들어져요.
3. `keepalive.yml` 내용을 붙여넣고 **Commit changes**를 누르세요.
4. **Actions** 탭 → **keepalive** → **Run workflow**를 눌러 한 번 시험해 보세요. 초록 체크 ✅가 뜨면 성공이에요.

이후로는 3일마다 자동으로 접속해요.
GitHub는 저장소에 60일 동안 변화가 없으면 이 자동 실행을 멈추고 메일을 보내요. 메일이 오면 **Actions** 탭에서 **Enable workflow**를 누르면 다시 켜져요.

---

## 처음 써볼 때

- 처음 들어가면 **닉네임**을 정해요. 조원들에게 이 이름이 보여요.
- 👤 이름 버튼 → **🔑 열쇠 링크 복사**를 눌러 나와의 채팅에 저장해 두세요.
  아이패드 사파리는 오래 안 쓴 사이트의 저장 정보를 지우기도 해요. 그래도 이 링크를 열면 내 프로젝트·플랜·이미지를 다시 수정할 수 있어요. **열쇠 링크는 남에게 보내지 마세요.**
- 홈 화면에 추가하면 앱처럼 쓸 수 있어요: 사파리 공유 버튼 → **홈 화면에 추가**

## 사용법 요약

| 기능 | 방법 |
|---|---|
| 프로젝트 만들기 | 홈 → ＋ 새 프로젝트 (6자리 코드 자동 생성, 예: `K7X-9Q2`) |
| 프로젝트 링크 공유 | 프로젝트 화면 오른쪽 위 🔗 코드 버튼 |
| 새 플랜 | 플랜 탭 → ＋ 새 플랜 (내 초안은 이 기기에만 저장) |
| 조원에게 공유 | 편집기 오른쪽 위 **프로젝트에 저장** |
| 외곽(점선) | 외곽·반원·원 버튼 / 반원은 ↻ 방향 버튼으로 90° 회전 |
| 상자(실선) | 상자 버튼 → 용도 입력, 색 선택, 가로·세로(m) 숫자 입력 |
| 이동·크기 조절 | 도형 끌기 / 모서리·변의 네모 손잡이 끌기 (격자에 딱 맞춰짐) |
| 화면 이동·확대 | 빈 곳 한 손가락 끌기 / 두 손가락 벌리기 / **맞춤** 버튼 |
| 되돌리기 | ↶ ↷ (키보드 연결 시 ⌘Z, ⇧⌘Z) |
| 격자 크기 | 아래 도구 막대 **격자** (0.5 / 1 / 2 / 3 / 5 / 10m) |
| 남의 플랜 발전시키기 | 열기 → **복제해서 내 초안으로** (원본은 작성자만 수정) |
| 레퍼런스 | 레퍼런스 탭 → ＋ 폴더 → ＋ 이미지 (장당 약 300KB로 자동 압축), 편집 중엔 **레퍼런스** 버튼 |

## 무료 한도 (Supabase Free)

- 데이터베이스 500MB: 플랜은 아주 작아서 수만 개도 괜찮아요.
- 이미지 저장 1GB: 300KB × 약 3,000장
- 한도를 넘으면 요금이 나가는 게 아니라 기능이 제한돼요. 이미지를 지워서 한도 아래로 내려가면 다시 쓸 수 있어요.
- 사용량 확인: Supabase 관리 화면 → **Usage**

## 1단계에서 알아둘 점

- 사이트 주소를 아는 사람은 누구나 모든 프로젝트를 **볼 수** 있어요. 수정·삭제는 만든 사람 기기만 할 수 있어요. 주소는 조원들끼리만 공유해 주세요.
- 데이터베이스에는 프로젝트 비밀번호 칸이 이미 만들어져 있어요. 2단계에서 "코드 찾기 + 비밀번호" 화면만 붙이면 돼요.
