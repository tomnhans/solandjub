# solandjub

둘이 함께 여행 지출을 빠르게 기록하고, 마지막에 누가 누구에게 얼마를 보내야 하는지 확인하는 모바일 우선 웹앱입니다.

## GitHub Pages로 사용

로컬 서버를 켜지 않고 쓰려면 GitHub에 올린 뒤 Pages로 배포하면 됩니다.

1. GitHub에서 새 저장소를 만듭니다.
2. 이 프로젝트 파일을 저장소에 올립니다.
3. 저장소의 `Settings` > `Pages`에서 `Source`를 `GitHub Actions`로 선택합니다.
4. `main` 브랜치에 올라가면 자동으로 배포됩니다.
5. 배포 후 표시되는 Pages 주소로 접속합니다.

주소는 보통 아래 형태입니다.

```txt
https://사용자이름.github.io/solandjub/
```

## 두 사람 공동 입력

앱의 `공유 설정`에 Supabase URL과 anon key를 저장하면 `공유 여행 만들기`로 초대 링크를 만들 수 있습니다.

자세한 설정은 `SUPABASE_SETUP.md`를 참고하세요.

## 로컬 실행

로컬에서 확인할 때만 사용합니다.

```bash
npm install
npm run dev
```

## 검증

```bash
npm run lint
npm run build
npm run test:settlement
```

## 주요 기능

- 지출 추가, 수정, 삭제
- 반반, 내가 전액 부담, 동행인이 전액 부담, 직접 입력 분담
- 총 지출액, 결제 총액, 실제 부담액, 최종 정산 문구 자동 계산
- 날짜별, 카테고리별, 결제자별 필터와 항목명/메모 검색
- localStorage 자동 저장
- JSON 내보내기와 가져오기
- 전체 데이터 초기화
- 다크모드 자동 대응
