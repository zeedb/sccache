FROM rust:buster AS builder

COPY . /workspace
WORKDIR /workspace
RUN cargo test --locked --all-targets
RUN cargo build --release

FROM rust:slim-buster

COPY --from=builder /workspace/target/release/sccache /usr/local/bin/sccache

CMD ["sccache"]