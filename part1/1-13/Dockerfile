FROM --platform=linux/amd64 golang:1.16

WORKDIR /usr/src/app
RUN dpkg --add-architecture amd64 \
    && apt-get update \
    && apt-get install -y --no-install-recommends gcc-x86-64-linux-gnu libc6-dev-amd64-cross


COPY . .
RUN CGO_ENABLED=1 GOOS=linux GOARCH=amd64 CC=x86_64-linux-gnu-gcc go build
RUN go test ./...

ENV REQUEST_ORIGIN=http://localhost:8000
RUN chmod u+x ./server
ENTRYPOINT [ "./server" ]