FROM ubuntu

ARG ENABLE_CACHE=1
ARG CACHE_HOST=0
ARG CACHE_PORT=0

RUN if [ "$ENABLE_CACHE" -eq 1 ]; then \
        echo "Acquire::http { proxy \"http://$CACHE_HOST:$CACHE_PORT\"; };" > /etc/apt/apt.conf.d/01proxy; \
    elif [ -e /etc/apt/apt.conf.d/01proxy ]; then \
        rm /etc/apt/apt.conf.d/01proxy; \
    fi

RUN apt-get update && apt-get install -y apache2 vim iputils-ping
RUN ping apt-cacher-ng