# 매스 스터디 · 깃허브 설치 안내

claude.ai에서 만든 매스 스터디와 화면·조작이 똑같은 사이트를, 내 주소(`https://내아이디.github.io/mass-study/`)로 올리는 방법이에요. 전부 무료이고, 카드 등록 없이 아이패드 사파리만으로 할 수 있어요. 처음 한 번만 20~30분 걸려요.

**올릴 파일 5개**

| 파일 | 하는 일 |
|---|---|
| `index.html` | 사이트 본체 |
| `icon.png` | 홈 화면 아이콘 |
| `supabase-setup.sql` | 데이터베이스 설정 (Supabase에 붙여넣기만 해요) |
| `keepalive.yml` | 저장소가 잠들지 않게 3일마다 깨우기 |
| `README.md` | 이 안내 |

> 예전 대화에서 받은 `supabase-setup.sql`과는 내용이 달라요. 이미 Supabase 프로젝트를 만들어 두었다면 **1단계는 건너뛰고 2단계부터** 하면 돼요. 예전 표는 그대로 두어도 괜찮아요.

---

## 1. Supabase 가입 · 데이터베이스 만들기

1. supabase.com → **Start your project** → **Continue with GitHub** (GitHub 계정이 없으면 github.com에서 먼저 가입)
2. **New project**
   - Name: `mass-study`
   - Database Password: **Generate a password** → 메모장에 보관 (사이트에서는 안 써요)
   - Region: **Northeast Asia (Seoul)**
   - Plan: **Free**
3. 1~2분 기다려요.

## 2. 데이터베이스 설정 붙여넣기

1. 왼쪽 메뉴 **SQL Editor** → **New query**
2. `supabase-setup.sql` 내용을 **전부** 복사해 붙여넣고 **Run**
3. `Success. No rows returned`가 나오면 끝이에요. 여러 번 실행해도 괜찮아요.

이 설정이 사이트 규칙을 지켜 줘요.
- 내 작업(나만 봄)은 나만 읽고 고칠 수 있어요.
- 프로젝트에 저장한 작업물·피드백은 만든 사람만 고치거나 지울 수 있어요.
- 표에 직접 쓰는 건 막혀 있고, 규칙을 검사하는 통로로만 저장돼요.

## 3. 연결 정보 두 개 넣기

1. 왼쪽 아래 ⚙️ **Project Settings** → **API Keys** (또는 **Data API**)
2. 두 값을 복사해요.
   - **Project URL**: `https://abcdefgh.supabase.co` 형태
   - **Publishable key** (`sb_publishable_…`), 없으면 **anon public** 키
   - ⚠️ `secret` / `service_role` 키는 **절대 쓰지 마세요.**
3. `index.html` 맨 위쪽 `▼▼▼` 표시 사이를 바꿔요.
   ```js
   window.MS_CONFIG = {
     SUPABASE_URL: "https://abcdefgh.supabase.co",
     SUPABASE_ANON_KEY: "sb_publishable_xxxxxxxx"
   };
   ```
   4단계에서 GitHub에 올린 뒤, GitHub 화면에서 `index.html` → 연필 ✏️ 버튼으로 고쳐도 돼요.

> 이 키는 공개돼도 괜찮은 키예요. 데이터는 2단계의 규칙이 지켜요.

## 4. GitHub에 올려서 주소 만들기

1. github.com → 오른쪽 위 **＋** → **New repository**
   - Repository name: `mass-study` (주소에 들어가요)
   - **Public** (무료 사이트 기능은 공개 저장소에서만 돼요. 코드만 공개되고 조원 데이터는 공개되지 않아요)
   - **Create repository**
2. **uploading an existing file** → `index.html`, `icon.png`, `README.md`를 올리고 **Commit changes**
3. 저장소 **Settings** → **Pages**
   - Source: **Deploy from a branch**
   - Branch: **main** / **(root)** → **Save**
4. 1~2분 뒤 새로고침하면 주소가 떠요: **`https://내아이디.github.io/mass-study/`**

## 5. 잠들지 않게 하기

Supabase 무료 프로젝트는 7일 동안 아무도 안 쓰면 일시정지돼요.

1. 저장소 첫 화면 **Add file** → **Create new file**
2. 파일 이름에 정확히 `.github/workflows/keepalive.yml` 입력 (`/`를 치면 폴더가 생겨요)
3. `keepalive.yml` 내용을 붙여넣고 **Commit changes**
4. **Actions** 탭 → **keepalive** → **Run workflow** → 초록 체크 ✅면 성공

GitHub는 저장소에 60일간 변화가 없으면 이 자동 실행을 멈추고 메일을 보내요. 메일이 오면 **Actions**에서 **Enable workflow**를 누르세요.

---

## 처음 써볼 때

- 처음 들어가면 **닉네임**을 정해요. 조원들에게 이 이름이 보여요.
- 오른쪽 위 **내 이름 버튼 → 열쇠 링크 복사**를 눌러 나와의 채팅 같은 곳에 꼭 저장해 두세요.
  - 로그인이 없는 대신 이 열쇠가 "나"예요. 브라우저 기록을 지우거나 다른 기기에서 열 때 이 링크를 열면 내 작업을 그대로 이어서 고칠 수 있어요.
  - **열쇠 링크는 남에게 보내지 마세요.** 받은 사람이 내 작업을 고칠 수 있어요. 조원에게는 사이트 주소만 보내요.
- **홈 화면에 추가**(사파리 공유 버튼 → 홈 화면에 추가)하면 앱처럼 전체 화면으로 열려요.
  - 홈 화면 앱은 사파리와 저장 공간이 따로라서, 처음 열면 새 사람으로 시작돼요. 이때 **내 이름 버튼 → 다른 기기의 열쇠 링크 붙여넣기**로 저장해 둔 열쇠 링크를 넣으면 원래 나로 바뀌어요.

## claude.ai 판과 다른 점

| | claude.ai 아티팩트 | 깃허브판 |
|---|---|---|
| 주소 | claude.ai/artifact/… | 내아이디.github.io/mass-study |
| 조원 조건 | claude.ai 로그인 + 편집자 초대 | 주소만 있으면 돼요 |
| 나를 구분하는 방법 | claude.ai 계정 | 닉네임 + 열쇠 링크 |
| 위쪽 X·공유 버튼 | 있음 | 없음 (전체 화면) |
| 화면·조작·기능 | 같음 | 같음 |

두 사이트는 데이터가 따로예요. claude.ai에서 만든 작업은 깃허브판에 자동으로 넘어오지 않아요.

## 알아둘 점 (1단계 테스트용)

- 사이트 주소를 아는 사람은 프로젝트와 공유된 작업물을 **볼 수** 있어요. 고치기·지우기는 만든 사람만 할 수 있어요. 주소는 조원끼리만 나눠 주세요.
- 프로젝트 이름 바꾸기, 레퍼런스 폴더 정리처럼 함께 쓰는 부분은 claude.ai판과 같이 참여자 누구나 할 수 있어요.
- 레퍼런스 사진은 지워도 사진 파일 자체는 저장소에 남아요(다른 사람이 지우지 못하게 하려고요). 무료 한도(1GB, 사진 약 1,500장)를 넘기 전까지는 신경 쓰지 않아도 돼요.

## 무료 한도 (Supabase Free)

- 데이터베이스 500MB: 작업물은 아주 작아서 수만 개도 괜찮아요.
- 사진 저장 1GB
- 넘으면 요금이 나가는 게 아니라 기능이 멈춰요. 사용량은 Supabase → **Usage**에서 봐요.

## 안 될 때

| 증상 | 확인할 것 |
|---|---|
| "공유 저장소에 연결되지 않아 이 브라우저에만 저장돼요" | `index.html` 위쪽 두 값이 맞는지, 앞뒤 따옴표가 있는지 |
| 저장할 때 "권한이 없어요" | 2단계 SQL을 끝까지 실행했는지 (다시 Run 해도 괜찮아요) |
| 사진이 안 올라가요 | 2단계 SQL을 다시 Run → Supabase **Storage**에 `ms-img`가 있는지 |
| 조원이 저장한 게 바로 안 보여요 | 최대 1분 안에 따라와요. 급하면 새로고침 |
| 며칠 만에 열었더니 안 돼요 | Supabase에서 프로젝트가 **Paused**면 **Restore** → 5단계 다시 확인 |
