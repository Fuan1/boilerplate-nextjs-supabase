# 프로젝트 폴더 구조 및 설명

## /src (프론트엔드 코드)

- **components/**  
  재사용 가능한 UI 컴포넌트(버튼, 모달, 카드 등). shadcn, lucide 등 외부 UI 라이브러리 기반 컴포넌트도 포함.

- **features/**  
  도메인별 상태/로직(예: user, game, chat 등). 각 도메인별로 zustand store, 비즈니스 로직, hooks 등을 분리.

- **store/**  
  전역 상태관리(zustand 등). 여러 도메인에서 공통으로 쓰는 상태(예: 로그인 상태, 테마 등).

- **services/**  
  **외부 서비스 연동 코드(예: supabase, REST API, GraphQL 등)**. supabase 클라이언트, API 래퍼, DB 쿼리 함수 등.
  **API 호출/응답, 인증, 실시간 등 외부와 통신하는 모든 코드**. (Next.js의 app/api 폴더와는 다름!)

- **icons/**  
  lucide 등 커스텀 아이콘 컴포넌트.

- **hooks/**  
  커스텀 React 훅(예: useDebounce, useModal 등).

- **types/**  
  프론트엔드 전용 타입 정의(컴포넌트 props, UI 상태 등).

- **utils/**  
  프론트엔드 전용 유틸 함수(포맷터, 파서 등).

- **constants/**  
  상수, config, enum 등.

- **styles/**  
  Tailwind, 전역/모듈 CSS, 스타일 관련 파일.

- **lib/**  
  기타 라이브러리, 프론트엔드에서만 쓰는 유틸/헬퍼.

- **app/**  
  Next.js App Router(페이지, 레이아웃, 서버 컴포넌트 등).

---

## /supabase (서버/DB/백엔드 관련)

- **functions/**  
  Supabase Edge Functions(서버리스 함수, 백엔드 API). DB 트리거, 커스텀 API 등.

- **migrations/**  
  DB 스키마 마이그레이션 파일(테이블, 인덱스 등 변경 이력).

- **seeds/**  
  초기 데이터 시드(더미 데이터, 기본값 등).

- **types/**  
  Supabase에서 자동 생성된 DB 타입(테이블, Row, Insert 등). 주로 DB 스키마 기반 타입.

- **storage/**  
  Supabase Storage(파일 업로드 등) 관련 파일.

---

## /shared (프론트-서버 공용 코드)

- **types/**  
  프론트와 서버가 **공유**하는 타입(예: DB 엔티티, API 응답 타입 등). supabase/types에서 자동 생성된 타입을 symlink/copy해서 둘 수도 있음.

- **utils/**  
  프론트-서버 모두에서 쓸 수 있는 범용 유틸 함수.

---

## 🔎 services 폴더에 대해 더 자세히!

- **services/**는 "API 코드"를 넣는 곳이 맞습니다. 단, 여기서 말하는 API란 **외부 서비스와 통신하는 코드**(예: supabase, 외부 REST API, GraphQL 등)를 의미합니다.
- 예시:
  - `services/supabase/client.ts` : supabase 클라이언트 인스턴스 생성
  - `services/supabase/userApi.ts` : 유저 관련 supabase 쿼리 함수
  - `services/api/openai.ts` : 외부 OpenAI API 호출 함수
- **컴포넌트에서 직접 API 호출 금지!** 반드시 services/hook을 통해 호출

---

## 💡 정리

- **services/**: 프론트에서 외부 서비스(서버, DB, 3rd-party API 등)와 통신하는 코드(클라이언트, 래퍼, 쿼리 함수 등)
- **app/api/**: Next.js 서버에서 동작하는 API 라우트(이 프로젝트에서는 별도 사용 X)
- **shared/types/**: 프론트-서버가 공유하는 타입(주로 DB 타입)
- **supabase/types/**: supabase에서 자동 생성된 DB 타입(공유 필요시 shared/types로 symlink/copy)
