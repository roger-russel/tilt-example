FROM golang:1.22.2-alpine3.18 as base
ENV LANG en_US.UTF-8
ENV LC_ALL=C
ENV LANGUAGE en_US.UTF-8
WORKDIR /app

FROM base as builder
COPY . .
RUN go mod tidy
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GO111MODULE=on go build -o api ./main.go

# Use distroless as minimal base image to package the api binary
# Refer to https://github.com/GoogleContainerTools/distroless for more details
FROM gcr.io/distroless/static:nonroot as final
WORKDIR /

COPY --from=builder /app/api .
USER nonroot:nonroot

ENTRYPOINT ["/api"]