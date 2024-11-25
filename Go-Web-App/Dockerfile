FROM golang:1.22.5 AS base

WORKDIR /app

COPY ./go-web-app/go.mod .

RUN go mod download

COPY ./go-web-app/static .

COPY ./go-web-app/. .

RUN go build -o main .

FROM gcr.io/distroless/base

COPY --from=base /app/main .

COPY --from=base /app/static ./static

EXPOSE 8080

CMD [ "./main" ]