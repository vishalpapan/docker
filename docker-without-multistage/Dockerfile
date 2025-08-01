FROM ubuntu AS build

RUN apt-get update && apt-get install -y golang-go

ENV GO111MODULE=off

COPY . .

RUN CG0_ENABLED=0 go build -o /app .

ENTRYPOINT ["/app"]
