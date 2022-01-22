FROM golang:1.17 as base


FROM base as dev


RUN curl -fLo install.sh https://raw.githubusercontent.com/cosmtrek/air/master/install.sh \
    && chmod +x install.sh && sh install.sh && cp ./bin/air /bin/air



RUN apt update && apt install -y \
git \
bash \
git \
nano \
htop \
openssh-client

# Add Maintainer Info
LABEL maintainer="selman tunç <selmantunc@gmail.com>"

WORKDIR /app

RUN   mv /bin/air /app/air && rm -rf /bin/air && rm -rf /go/bin/air

EXPOSE 8080

ENTRYPOINT ["./air", "-c", ".air.toml"]

#CMD ["./air"]