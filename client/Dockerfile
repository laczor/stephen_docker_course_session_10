# We can tag the phase, everyting will be referenced as "builder"
FROM node:alpine as builder
WORKDIR '/app'
COPY package.json ./
RUN npm install

# Volumes are used only in developement!
COPY . .
RUN npm run build

# This will be only executed after the application has been built!!
FROM nginx
EXPOSE 3000

# Take my file and overwrite the existing one!
COPY ./default.conf /etc/nginx/conf.d/default.conf
# It will be served automatically when it will starts up!
COPY --from=builder /app/build /usr/share/nginx/html