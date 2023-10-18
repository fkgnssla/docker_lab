# Node.js의 Alpine Linux 버전을 기본 이미지로 선택하고, 이 단계의 이름을 "build"로 설정
FROM node:alpine as build
# 도커의 작업 디렉터리를 "/app"으로 설정
WORKDIR /app
# 현재 디렉터리의 "package.json" 파일을 도커의 "/app"으로 복사
COPY package.json /app
# 패키지 설치 ("--silent" 플래그는 출력을 최소화한다.)
RUN npm install --silent
# 현재 디렉터리의 모든 파일을 "/app"으로 복사
COPY . /app
# react 실행
RUN npm run build

# Nginx를 기본 이미지로 선택
FROM nginx
# 이전 단계(build 단계)에서 생성된 "/app/build" 디렉터리를 Nginx의 정적 파일을 호스팅하는 기본 디렉터리 "/usr/share/nginx/html"로 복사
COPY --from=build  /app/build /usr/share/nginx/html
# nginx 실행
ENTRYPOINT ["nginx", "-g", "daemon off;"]
