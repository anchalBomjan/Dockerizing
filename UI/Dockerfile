FROM node:20-alpine AS build
WORKDIR /app

COPY Employee.UI/package*.json ./
RUN npm install

COPY Employee.UI/ ./
RUN npm run build -- --configuration production

FROM nginx:alpine AS final
COPY --from=build /app/dist/employee.ui/browser /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80