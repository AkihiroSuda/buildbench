# Buildbench: benchmark tool for Docker, BuildKit, img, Buildah, and Kaniko

[![Build Status](https://travis-ci.org/AkihiroSuda/buildbench.svg)](https://travis-ci.org/AkihiroSuda/buildbench)

## Requirements

* bash
* realpath
* Docker

## Usage

```console
$ ./buildbench ./examples/ex01 out.csv 5
```

* To disable specific builder, please set `DISABLE_DOCKER`, `DISABLE_BUILDKIT`, and so on.
