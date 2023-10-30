FROM registry.access.redhat.com/ubi9/go-toolset:1.19.10-4 AS builder

COPY . .
RUN go mod download

#RUN go build -o ./main
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o main main.go

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
COPY --from=builder /opt/app-root/src/main /

ENV PORT 8081
EXPOSE 8081

CMD [ "/main" ]
