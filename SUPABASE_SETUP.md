# solandjub 공유 입력 설정

두 사람이 각자 휴대폰에서 같은 장부를 입력하려면 Supabase 프로젝트 하나가 필요합니다.

## 1. 테이블 만들기

Supabase SQL Editor에서 아래 SQL을 실행합니다.

```sql
create table if not exists expenses (
  id text primary key,
  trip_id text not null,
  date text not null,
  title text not null,
  category text not null,
  payer text not null,
  amount integer not null,
  split_type text not null,
  my_share integer not null,
  companion_share integer not null,
  memo text,
  created_at text not null,
  updated_at text not null
);

alter table expenses enable row level security;

create policy "public trip read" on expenses
for select using (true);

create policy "public trip insert" on expenses
for insert with check (true);

create policy "public trip update" on expenses
for update using (true);

create policy "public trip delete" on expenses
for delete using (true);
```

## 2. Realtime 켜기

Supabase Dashboard에서 `Database` > `Replication`으로 이동해 `expenses` 테이블의 Realtime을 켭니다.

## 3. 앱에 연결

앱의 `공유 설정`에 Supabase URL과 anon key를 저장합니다.

그 뒤 `공유 여행 만들기`를 누르면 `?trip=...`이 붙은 초대 링크가 만들어집니다.

## 보안 참고

이 설정은 로그인 없는 여행용 간편 공유 구조입니다. 초대 링크를 가진 사람이 장부를 볼 수 있다고 가정합니다.
더 강한 보안이 필요하면 로그인, 초대 토큰, Edge Function, 세밀한 RLS 정책을 추가해야 합니다.
