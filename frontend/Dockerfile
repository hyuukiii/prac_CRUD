# Node.js 최신 LTS 버전 사용
FROM node:18-alpine

WORKDIR /app

# 패키지 설치 캐싱을 위해 package.json만 먼저 복사
COPY package*.json ./
RUN npm install

# 소스 코드 복사
COPY . .

# 개발 서버 포트 노출
EXPOSE 3000

# 개발 모드로 실행
CMD ["npm", "start"]