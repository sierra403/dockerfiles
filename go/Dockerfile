FROM golang:1.25 as build

WORKDIR /go/src/app

COPY . .

RUN go mod download
RUN CGO_ENABLED=0 go build -ldflags="-w -s" -o /go/bin/app


FROM gcr.io/distroless/base-debian12

COPY --from=build /go/bin/app ./app

CMD ["./app"]
