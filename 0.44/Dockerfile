FROM swift:5.1.2 as builder

RUN apt-get update && apt-get install -y curl

ENV SWIFTFORMAT_VERSION=0.44.0
ENV SWIFTFORMAT_ARCHIVE="https://github.com/nicklockwood/SwiftFormat/archive/${SWIFTFORMAT_VERSION}.tar.gz"

RUN mkdir -p /build/lib && cp -R /usr/lib/swift/linux/*.so* /build/lib

RUN curl -LSs --fail -o /tmp/swiftformat.tgz -- "${SWIFTFORMAT_ARCHIVE}" \
  && cd /tmp \
  && tar -xzf swiftformat.tgz \
  && mv "./SwiftFormat-${SWIFTFORMAT_VERSION}" ./swiftformat \
  && cd /tmp/swiftformat \
  && swift build -c release \
  && mv `swift build -c release --show-bin-path` /build/bin

FROM swift:5.1.2-slim

LABEL maintainer="Moritz Lang <hi@slashmo.codes>"
LABEL description="Docker Container for SwiftFormat"

WORKDIR /bin

COPY --from=builder /build/bin/swiftformat .

RUN chmod +x swiftformat

WORKDIR /app

ENTRYPOINT [ "/bin/swiftformat", "." ]
