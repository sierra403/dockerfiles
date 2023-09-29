FROM golang:1.21 as build

WORKDIR /go/src/app

COPY . .

RUN go mod download
RUN CGO_ENABLED=0 go build -o /go/bin/app


FROM gcr.io/distroless/base-debian11

COPY --from=build /go/bin/app ./app

ENV TZ=America/Edmonton

CMD ["./app"]