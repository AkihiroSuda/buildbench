FROM alpine AS buildc
RUN apk add --no-cache build-base
RUN echo -e "#include <stdio.h>\nint main(int ac, char *av[]){printf(\"hello c\\\\n\");return 0;}" | tee /hello.c
COPY . /foo
RUN gcc -o /a.out /hello.c

# the COPY above SHOULD NOT invalidate the cache for the buildgo stage.

FROM alpine AS buildgo
RUN apk add --no-cache build-base
RUN apk add --no-cache go
RUN echo -e "package main\nfunc main(){println(\"hello go\")}" | tee /hello.go
RUN go build -o /a.out /hello.go

FROM alpine
COPY --from=buildc /a.out /hello1
COPY --from=buildgo /a.out /hello2

# Note: as of June 5, 2018, Buildah and Kaniko does not support `FROM anotherstage`
