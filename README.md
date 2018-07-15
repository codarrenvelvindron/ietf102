# ietf102

## Build instructions 
- docker build -t mercu_original .

- docker run -dit -v `pwd`/hg-committed:/tmp/mercurial mercu_original

- docker exec -it [container] /bin/bash
