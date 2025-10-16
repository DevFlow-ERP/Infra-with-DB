# DevFlow ERP Infrastructure

개발 환경용 인프라 설정

## 사용법

### 1. 환경 변수 설정

```bash
cp .env.example .env
# .env 파일을 편집하여 필요한 비밀번호 설정
```

### 2. PostgreSQL 시작

```bash
docker-compose -f docker-compose.dev.yml up -d
```

### 3. 데이터베이스 상태 확인

```bash
docker-compose -f docker-compose.dev.yml ps
docker-compose -f docker-compose.dev.yml logs postgres
```

### 4. PostgreSQL 접속

```bash
docker exec -it devflow-postgres-dev psql -U devflow -d devflow
```

### 5. 서비스 중지

```bash
docker-compose -f docker-compose.dev.yml down
```

### 6. 데이터 초기화 (주의: 모든 데이터 삭제)

```bash
docker-compose -f docker-compose.dev.yml down -v
```

## 서비스 정보

- **PostgreSQL**: localhost:5432
  - Database: devflow
  - User: devflow
  - Password: .env 파일 참조

- **Redis**: localhost:6379

## 연결 URL

```
# PostgreSQL
DATABASE_URL=postgresql://devflow:devflow_pass_123@localhost:5432/devflow

# Redis
REDIS_URL=redis://localhost:6379/0
```
