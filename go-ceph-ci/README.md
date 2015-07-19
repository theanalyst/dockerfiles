go-ceph-ci
----------

Meant for running ci-tests for [go-ceph](https://github.com/noahdesu/go-ceph)

Assuming current directory holds go-ceph code, run it as:

docker run --rm -it -v $(CURDIR):/go/src/github.com/noahdesu/go-ceph go-ceph-ci:giant
