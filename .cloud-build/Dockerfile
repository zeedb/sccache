FROM rust:buster AS builder

COPY . /sccache
WORKDIR /sccache
RUN cargo test --locked --all-targets
RUN cargo build --release

FROM rust:buster

RUN rustup toolchain install nightly-2020-05-10 && \
    rustup default nightly-2020-05-10

COPY --from=builder /sccache/target/release/sccache /usr/local/bin/sccache