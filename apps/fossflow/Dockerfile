FROM alpine:latest

WORKDIR /fossflow

RUN apk add --no-cache git
RUN apk add --no-cache npm
RUN apk add --no-cache nodejs

RUN git clone \
	--single-branch \
	--no-tags \
	--depth=1 \
	https://github.com/stan-smith/FossFLOW.git \
	.


COPY --chown=node:node package*.json ./
RUN npm ci && npm cache clean --force

COPY --chown=node:node . .

EXPOSE 3000

CMD ["npm", "start"]
