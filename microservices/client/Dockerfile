FROM node:24-alpine AS builder

WORKDIR /app

COPY package.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf 

COPY --from=builder /app/build /usr/share/nginx/html


# 🟢 Builder stage
# FROM node:24-alpine AS builder

# 👉 This stage:

# installs dependencies
# runs:
# npm run build

# 👉 This creates:

# /app/build

# This folder contains:

# index.html
# JS files
# CSS files
# 🔵 Nginx stage
# FROM nginx

# 👉 This stage:

# does NOT have Node
# only serves static files
# 🎯 The key line (your question)
# COPY --from=builder /app/build /usr/share/nginx/html

# ✔ YES — this is exactly what you must write

# 🧠 What it REALLY means

# “Take the build folder from the builder stage
# and copy it into the nginx serving folder”

# 📦 Important detail (many people miss this)

# 👉 You are copying:

# /app/build