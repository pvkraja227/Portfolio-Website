Docker image can be reduced in 4 stages

1. modifying dependencies
dev: dev + prod dependencies
prod: only prod dependencies
2. smaller base images: alpine (very low size) / slim / distroless (disadv: no package mgr (apt, shell) // adv: very low size, useful for security reasons)
3. multi stage dockerfile (stage 1: build artifact along with dependencies / stage 2: copy artifact from 1 with no dependencies)
4. use nginx ( 50 MB) instead of node (240 MB)

server - te.med

install docker - 2 steps
