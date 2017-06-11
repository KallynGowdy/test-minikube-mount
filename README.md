## Reproduction of [#1562](https://github.com/kubernetes/minikube/issues/1562)

- The `test` folder contains a set of files that represent a directory that we're trying to mount to a container via minikube.
- The `master` branch contains a passing set of files, while the `failing` branch contains the opposite.

Note that this error is pretty veiled, so just because it fails on my machine doesn't mean it will fail on your machine.

1. Make sure that minikube has been started and is running.
2. Mount the `./test` folder to Minikube
    - Windows: `> minikube mount .\test:/test`
    - Unix: `$ minikube mount ./test:/test`
3. Attempt to `ls` the directory inside of minikube
    - `> minikube ssh -- ls /test`
4. If you're on the `master` branch, it should pass. If you're on the `failing` branch, it should fail with error code `526`
