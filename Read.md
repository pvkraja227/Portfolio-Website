Docker image can be reduced in 4 stages

1. modifying dependencies
dev: dev + prod dependencies
prod: only prod dependencies
2. smaller base images: alpine (very low size) / slim / distroless (disadv: no package mgr (apt, shell) // adv: very low size, useful for security reasons)
3. multi stage dockerfile (stage 1: build artifact along with dependencies / stage 2: copy artifact from 1 with no dependencies)
4. use nginx:alpine webserver (43 MB) instead of node:alpine (240 MB)

server - t2.med

sudo apt update
install docker - 2 steps
sudo usermod -aG docker ubuntu (adding ubuntu user to docker group)
newgrp docker (apply changes)
git clone https://github.com/pvkraja227/Portfolio-Website.git

1. Dockerfile

From node:latest
WORKDIR /app
COPY package*.json ./
RUN npm install
copy . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "run", "start"]

docker build -t app:1 -f Dockerfile1
