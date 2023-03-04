# run docker locally

1. ´´´docker build -t nvidia .´´´

2. ´´´docker run --gpus all --privileged -v /var/run/docker.sock:/var/run/docker.sock -v /local:/local nvidia´´´
