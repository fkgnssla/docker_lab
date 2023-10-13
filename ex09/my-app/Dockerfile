FROM nginx

# build 폴더에 있는 index.html을 /usr/share/nginx/html에 복사
COPY build /usr/share/nginx/html

# nginx 실행
ENTRYPOINT ["nginx", "-g", "daemon off;"]

