# Base image nhẹ và tối ưu cho Node.js
FROM node:20-alpine

# Đặt thư mục làm việc bên trong container
WORKDIR /app

# Copy file package.json và package-lock.json để cache layer install
COPY package*.json ./

# Cài dependencies ở chế độ production
RUN npm ci --omit=dev --no-audit --no-fund

# Copy toàn bộ source code
COPY . .

# Mở port 3003 (API Gateway)
EXPOSE 3003

# Lệnh khởi động container
CMD ["npm", "start"]
