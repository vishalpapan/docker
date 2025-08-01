#BASE IMAGE

FROM ubuntu AS build

RUN apt-get update && apt-get install -y golang-go

ENV GO11MODULE=off
ENV GOPATH=/go

#Create GOPATH structure
WORKDIR /go/src/app

#set working directory
WORKDIR /app

COPY . .

#here we build the application binary using the go files.
RUN CGO_ENABLED=0 go build -o /app .

#from here new stage of build starts where we just copy binary from the build stage and run it, this reduces image size

FROM scratch

#copy the compiled binary from the build stage
COPY --from=build /app /app

#set the entrypoint for the container to run the binary

ENTRYPOINT ["/app"]





