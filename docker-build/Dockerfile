# From https://github.com/homeport/gonut/tree/master/assets/sample-apps/golang

FROM ghcr.io/shipwright-io/shipwright-samples/golang:1.18 AS build

COPY . .
ENV CGO_ENABLED=0
RUN ls -al .git || echo "Git folder not found"

RUN go build \
    -ldflags "-s -w -extldflags '-static'" \
    -o /tmp/helloworld \
    main.go

FROM scratch
COPY --from=build /tmp/helloworld ./helloworld
ENTRYPOINT [ "./helloworld" ]
EXPOSE 8080
