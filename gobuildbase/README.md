# Golang build base
[![Docker Repository on Quay](https://quay.io/repository/honestbee/gobuildbase/status "Docker Repository on Quay")](https://quay.io/repository/honestbee/gobuildbase)

Base docker image for Honestbee's Golang builds

## Contents:

 - [Goose](https://bitbucket.org/liamstask/goose/cmd/goose):
   For database migrations (required for tests)
 - [Ginkgo](https://github.com/onsi/ginkgo/ginkgo):
   For Unit Tests
 - [modocache](https://github.com/modocache/gover):
   To gather all *.coverprofile files to send to coveralls.io
 - [goveralls](github.com/mattn/goveralls):
   Send *.coverprofiles to coveralls.io

## Notes:

Confirm if it is needed to run `go test` as `goveralls` should run this
implicitly
