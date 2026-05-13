FROM alpine:latest AS builder
WORKDIR /app
COPY index.html app.js default.conf ./

FROM nginxinc/nginx-unprivileged:alpine
COPY --from=builder /app/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/index.html /usr/share/nginx/html/
COPY --from=builder /app/app.js /usr/share/nginx/html/
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]