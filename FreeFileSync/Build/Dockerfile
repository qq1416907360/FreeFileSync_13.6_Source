FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        software-properties-common curl gnupg2 && \
    rm -rf /var/lib/apt/lists/*

RUN add-apt-repository universe

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libwxgtk3.2-dev libssh2-1-dev && \
    rm -rf /var/lib/apt/lists/*

RUN DEBIAN_FRONTEND=noninteractive \
    apt-get update \
    && apt-get install -y --no-install-recommends \
        xauth \
        xvfb \
        gtk2-engines-pixbuf \
        libnotify-dev \
        libpulse0 \
        libxtst6 \
        libnss3 \
        x11-apps \
    && rm -rf /var/lib/apt/lists/*


ENV DISPLAY=192.168.1.10:0.0


RUN mkdir -p /app && \
    chmod 755 /app

COPY Bin /app/Bin
COPY Resources /app/Resources

RUN chmod +x /app/Bin/FreeFileSync_x86_64

WORKDIR /app

CMD ["sh", "-c", "Xvfb :99 -screen 0 1024x768x24 & sleep 20 && ./Bin/FreeFileSync_x86_64"]
