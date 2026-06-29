# syntax=docker/dockerfile:1

ARG SWIFT_IMAGE=swift:6.3

FROM ${SWIFT_IMAGE} AS build
WORKDIR /workspace

ARG SWIFT_WEB_REF=main
RUN git clone --depth 1 --branch ${SWIFT_WEB_REF} https://github.com/1amageek/swift-web.git /opt/swift-web

COPY . /workspace/app
RUN swift run --package-path /opt/swift-web sweb prepare --package-path /workspace/app
RUN swift build --package-path /workspace/app/.swiftweb/generated/server -c release --product app-server

FROM ${SWIFT_IMAGE} AS runtime
WORKDIR /app
ENV PORT=8080

COPY --from=build /workspace/app/.swiftweb/generated/server/.build/release/app-server /app/app-server

EXPOSE 8080
CMD ["/app/app-server"]

