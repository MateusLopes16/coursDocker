FROM golang:latest AS builder
WORKDIR /src
COPY dispatcher.go .
RUN CGO_ENABLED=0 GOOS=linux go build -o dispatcher dispatcher.go

FROM scratch
COPY --from=builder /src/dispatcher /dispatcher
COPY /static /static
EXPOSE 80
CMD ["/dispatcher"]