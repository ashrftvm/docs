# Deployment of Angular SSR to Amazon EC2

1. ```npm run build:ssr```
2. Move the dist over to your server
3. install PM2
    - ```npm install pm2 -g```
4. On your server, use PM2 to run the server bundled app
    - pm2 start dist/server.js
5. If you're using Nginx, or other web servers, make sure to redirect requests to the port that the app started with PM2 is listening on.
