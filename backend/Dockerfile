FROM golang:alpine

# Instalação de bibliotecas do sistema operacional para funcionamento correto das dependências da aplicação
RUN apk add -U --no-cache build-base \
        gcc \
        abuild \
        binutils \
        binutils-doc \
        gcc-doc \
	&& rm -rf /var/cache/apk/* \
    && rm -rf /tmp/* \
	&& apk update

# Variável de ambiente requisito para uso da dependência go-sqlite3
ENV CGO_ENABLED 1

COPY src/backend/main.go src/

# Instalação do git requisito para funcionamento do comando go get;
# download das dependências;
# build da aplicação
RUN apk add --no-cache git \
    && go get github.com/gorilla/mux \
    && go get github.com/sirupsen/logrus \
	&& go get github.com/mattn/go-sqlite3 \
    && apk del git \
	&& go build src/main.go

ENTRYPOINT [ "/go/main" ]

EXPOSE 8080