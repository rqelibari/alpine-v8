# Alpine V8
This Dockerfile builds Google's V8 library and tools on alpine. This project
is meant to be used in other multistage Dockerfiles to copy the V8 library and
include files over. At least that is what I am using it for.

# Usage
Include this image in your multistage Dockerfile and copy the V8 lib and
includes over. E.g.

```Dockerfile
FROM rqelibari/alpine-v8:latest as v8
FROM alpine:3.8
...
COPY --from=v8 /root/v8/include /usr/include
COPY --from=v8 /root/v8/lib /usr/lib
...
```

## Author
I am not the author of this Dockerfile. I found this script on a [gist][2]
of [@tylerchr][1] while I was searching for a v8 lib for an alpine image
in another project of mine. A huge thanks to him for sharing the results of
his efforts.

[1]: https://github.com/tylerchr
[2]: https://gist.github.com/tylerchr/15a74b05944cfb90729db6a51265b6c9
