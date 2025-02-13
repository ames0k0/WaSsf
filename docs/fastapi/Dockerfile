FROM alpine:latest

ARG MKDOCS__DEV_ADDR

WORKDIR /fastapi

RUN apk add --no-cache git
RUN apk add --no-cache python3 py3-pip

RUN git clone \
	--single-branch \
	--no-tags \
	--depth=1 \
	https://github.com/fastapi/fastapi.git \
	.

RUN pip install --break-system-packages -r requirements-docs.txt

WORKDIR /fastapi/docs/en
EXPOSE 8300

CMD ["mkdocs", "serve", "--dev-addr", "0.0.0.0:8300"]
