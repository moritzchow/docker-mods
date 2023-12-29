FROM golang:1.20-alpine3.17 as build
COPY root/ /root-layer/

# Install transmission-nat-pmp, cache bust if latest commit changed
ADD https://api.github.com/repos/moritzchow/transmission-nat-pmp/commits?per_page=1 latest_commit
RUN go install github.com/moritzchow/transmission-nat-pmp@latest && \
    mv /go/bin/transmission-nat-pmp /root-layer/transmission-nat-pmp

FROM scratch
COPY --from=build /root-layer/ /
